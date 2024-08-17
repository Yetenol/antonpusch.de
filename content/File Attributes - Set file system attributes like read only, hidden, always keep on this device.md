---
dg-publish: true
priority: 9
---

# .Net Attribute Flags

Attributes are bitwise combination of the following `[System.IO.FileAttributes]` fields:

| Value                 | Name                     | Targets    | The target…                                                                                                                                                                                                                                                                                                                                                         |
| --------------------- | ------------------------ | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0x000001`  = 1       | ReadOnly                 | file      | …is read-only.                                                                                                                                                                                                                                                                                                                                                      |
| `0x000002`  = 2       | Hidden                   | both      | …is hidden, and thus is not included in an ordinary directory listing.                                                                                                                                                                                                                                                                                              |
| `0x000004`  = 4       | System                   | both      | …is a system file. That is, the file is part of the operating system or is used exclusively by the operating system.                                                                                                                                                                                                                                                |
| `0x000010`  = 16      | Directory                | directory | …is a directory.                                                                                                                                                                                                                                                                                                                                                    |
| `0x000020`  = 32      | Archive                  | both      | …is marked to be included in incremental backup operation. Windows sets this attribute whenever the file is modified, and backup software should clear it when processing the file during incremental backup.                                                                                                                                                       |
| `0x000040`  = 64      | Device                   | reserved  | Reserved for future use.                                                                                                                                                                                                                                                                                                                                            |
| `0x000080`  = 128     | Normal                   | file      | …is a standard file that has no special attributes. This attribute is valid only if it is used alone.                                                                                                                                                                                                                                                               |
| `0x000100`  = 256     | Temporary                | file      | …is temporary. A temporary file contains data that is needed while an application is executing but is not needed after the application is finished. File systems try to keep all the data in memory for quicker access rather than flushing the data back to mass storage. A temporary file should be deleted by the application as soon as it is no longer needed. |
| `0x000200`  = 512     | SparseFile               | file      | …is a sparse file. Sparse files are typically large files whose data consists of mostly zeros.                                                                                                                                                                                                                                                                      |
| `0x000400`  = 1024    | ReparsePoint             | both      | …contains a reparse point, which is a block of user-defined data associated with a file or a directory.                                                                                                                                                                                                                                                             |
| `0x000800`  = 2048    | Compressed               | both      | …is compressed.                                                                                                                                                                                                                                                                                                                                                     |
| `0x001000`  = 4096    | Offline                  | file      | …is offline. The data of the file is not immediately available.                                                                                                                                                                                                                                                                                                     |
| `0x002000`  = 8192    | NotContentIndexed        | both      | …will not be indexed by the operating system's content indexing service.                                                                                                                                                                                                                                                                                            |
| `0x004000`  = 16384   | Encrypted                | both      | …is encrypted. For a file, this means that all data in the file is encrypted. For a directory, this means that encryption is the default for newly created files and directories.                                                                                                                                                                                   |
| `0x008000`  = 32768   | IntegrityStream          | directory | …includes data integrity support. When this value is applied to a file, all data streams in the file have integrity support. When this value is applied to a directory, all new files and subdirectories within that directory, by default, include integrity support.                                                                                              |
| `0x010000`   = 65536  | Virtual ¹⁾               | reserved  |                                                                                                                                                                                                                                                                                                                                                                     |
| `0x020000`  = 131072  | NoScrubData              | both      | …is excluded from the data integrity scan. When this value is applied to a directory, by default, all new files and subdirectories within that directory are excluded from data integrity.                                                                                                                                                                          |
| `0x040000`  = 262144  | EA ¹⁾                    | internal  | …with extended attributes.                                                                                                                                                                                                                                                                                                                                          |
| `0x040000`  = 262144  | Recall On Open ¹⁾        | internal  | …has no physical representation on the local system                                                                                                                                                                                                                                                                                                                 |
| `0x080000`  = 524288  | Pinned ¹⁾                | both      | …should be kept fully present locally even when not being actively accessed. *Always keep on this device* enables this attribute.                                                                                                                                                                                                                                   |
| `0x100000`  = 1048576 | Unpinned ¹⁾              | both      | …should not be kept fully present locally except when being actively accessed. *Free up space* enables this attribute.                                                                                                                                                                                                                                              |
| `0x400000`  = 4194304 | Recall On Data Access ¹⁾ | both      | …is not fully present locally.                                                                                                                                                                                                                                                                                                                                      |

> ¹⁾ Not recognized by Dotnet's `[IO.FileAttributes]` but official Win32 file attribute

Example: combine _read only_ and _temporary_

```powershell
$flags = [IO.FileAttributes]::ReadOnly + [IO.FileAttributes]::Temporary
```

# Modify Attributes

```powershell
$info = Get-Item -Path ".\example.txt"
$info = New-TemporaryFile
```

**Get** attributes of a file

```powershell
foreach ($n in 0..30) {
    [int]$value = [Math]::Pow(2, $n)
    if ([bool]($info.Attributes -band $value)) {
        [Enum]::Parse([IO.FileAttributes], $value) `
            -replace 524288, "Pinned" -replace 1048576, "Unpinned" `
            -replace 4194304, "RecallOnDataAccess"
    }
}
```

**Test** an attribute

```powershell
[bool]($info.Attributes -band [IO.FileAttributes]::ReadOnly) # is read only?
[bool]($info.Attributes -band 0x080000) # is always available on this device?
```

**Pin** a file to keep it fully present locally
- enable *Pinned* and disable *Unpinned*

```powershell
$info.Attributes = $info.Attributes -bor 0x080000 -band (-bnot 0x100000)
```

**Enable** an attribute

```powershell
$info.Attributes = $info.Attributes -bor [IO.FileAttributes]::Hidden
```

Disable an attribute

```powershell
$info.Attributes = $info.Attributes -band (-bnot [IO.FileAttributes]::Hidden)
```

**Toggle** an attribute

```powershell
$info.Attributes = $info.Attributes -bxor [IO.FileAttributes]::Hidden
```

# Examples

**Pin** a folder and all its subfolders recursively to keep them fully present locally

```powershell
$items = ".\mods\", ".\saves\"
@(
    Get-Item $items | where PSIsContainer | Get-ChildItem -Recurse
    Get-Item $items
) | foreach { 
    $info.Attributes = $info.Attributes -bor 0x080000 -band (-bnot 0x100000)
}
```

Display all attributes in a folder:

- `(Get-ChildItem).Attributes` doesn't work with ¹⁾ attributes

```powershell
Get-ChildItem | foreach { 
    $value = [int]$_.Attributes
    [PSCustomObject]@{ Name = $_.Name; Value = $value; Attributes = $(
        0..30 | foreach { [Math]::Pow(2, $_) } | where {
            [bool]($_ -band $value) 
        } | foreach { 
            [Enum]::Parse([IO.FileAttributes], $_) `
                -replace 524288, "Pinned" -replace 1048576, "Unpinned" `
                -replace 4194304, "RecallOnDataAccess"
        }
    )
}}
```

# Other

List all valid attributes:

```powershell
0..30 | foreach { [Math]::Pow(2, $_) } | where {
    $_ -in [Enum]::GetValues([IO.FileAttributes])
} | foreach { [PSCustomObject]@{ 
    Decimal = $_
    Hexadecimal = $("0x" + [String]::Format("{0:X6}",[int]$_))
    Name = [Enum]::Parse([IO.FileAttributes], $_)
}}
```

---
Sources:
- [File Attribute Constants (WinNT.h) - Win32 apps | Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/fileio/file-attribute-constants)
- 2022-04-05 [FileAttributes Enum (System.IO) - Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/api/system.io.fileattributes?view=net-6.0)
- 2022-04-05 [What does Directory and file Attributes - 525328, 525344 ,5248544 mean- - PowerShell](https://www.reddit.com/r/PowerShell/comments/sgsgpr/what_does_directory_and_file_attributes_525328/)
- 2023-01-18: [Types - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/scripting/lang-spec/chapter-04?view=powershell-7.3#4263-file-attributes-type)

Related:

Tags:
[File System - Use paths, get meta data, link, download, and encrypt files and folders](./File%20System%20-%20Use%20paths,%20get%20meta%20data,%20link,%20download,%20and%20encrypt%20files%20and%20folders.md)
