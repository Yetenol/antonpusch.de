---
title: "Copy GUI - Reveal or copy with File Explorer GUI"
date: "2024-08-26T00:00:00.000+02:00"
dg-publish: true
priority: 7
---

Example content

```powershell
$file = ".\example.txt"
$tool = "$env:SystemRoot\System32\notepad.exe"
```

**Open current folder**

```powershell
Invoke-Item -Path .
```

```powershell
explorer (Resolve-Path .) # can only open one folder
```

- abbreviate `ii .`

**Reveal** one **file** or **folder**

```powershell
explorer "/select,`"$(Resolve-Path $file)`""
```

**Copy** using _Windows Explorer_ UI  
- from `$source` to `$destination` with `$copyFlags`

```powershell
$objShell = New-Object -ComObject 'Shell.Application'    
$objFolder = $objShell.NameSpace((Resolve-Path $destination).Path)
$objFolder.CopyHere((Resolve-Path $source).Path, $copyFlags)
```



The `$copyFlags` are a bitwise combination of the following `vOptions` flags:

- `0x0004` $= [4]_{16}  = [4]_{10}$: **no UI**, Do not display a progress dialog box.
- `0x0008` $= [8]_{16} = [8]_{10}$: **rename duplicates**, Give the file being operated on a new name in a move, copy, or rename operation if a file with the target name already exists.
- `0x0010` $= [10]_{16} = [16]_{10}$: **yes to all**, Respond with "Yes to All" for any dialog box that is displayed.
- `0x0040` $[40]_{16} = [64]_{10}$: **allow undo**, Preserve undo information, if possible.
- `0x0080` $= [80]_{16} = [128]_{10}$: **require wildcard**, Perform the operation on files only if a wildcard file name like `*.*` is specified.
- `0x0100` $= [100]_{16} = [256]_{10}$: **UI without filenames**, Display a progress dialog box but do not show the file names.
- `0x0200` $= [200]_{16} = [512]_{10}$: **create directories**, Do not confirm the creation of a new directory if the operation requires one to be created.
- `0x0400` $= [400]_{16} =  [1024]_{10}$: **no error UI**, Do not display a user interface if an error occurs.
- `0x0800` $= [800]_{16} = [2048]_{10}$: **no security attributes**, Do not copy the security attributes of the file. (Version 4.71.)
- `0x1000` $= [1000]_{16} = [4096]_{10}$: **no recursion**, Only operate in the local directory. Do not operate recursively into subdirectories.
- `0x2000` $= [2000]_{16} = [8192]_{10}$: **no file grouping**, Do not copy connected files as a group. Only copy the specified files. (Version 5.0.)

| Value                | Summary                | Description                                                                                                                    |
| -------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `0x0004` <br> = 4    | no UI                  | Do not display a progress dialog box.                                                                                          |
| `0x0008` <br> = 8    | rename duplicates      | Give the file being operated on a new name in a move, copy, or rename operation if a file with the target name already exists. |
| `0x0010` <br> = 16   | yes to all             | Respond with "Yes to All" for any dialog box that is displayed.                                                                |
| `0x0040` <br> = 64   | allow undo             | Preserve undo information, if possible.                                                                                        |
| `0x0080` <br> = 128  | require wildcard       | Perform the operation on files only if a wildcard file name like `*.*` is specified.                                           |
| `0x0100` <br> = 256  | UI without filenames   | Display a progress dialog box but do not show the file names.                                                                  |
| `0x0200` <br> = 512  | create directories     | Do not confirm the creation of a new directory if the operation requires one to be created.                                    |
| `0x0400` <br> = 1024 | no error UI            | Do not display a user interface if an error occurs.                                                                            |
| `0x0800` <br> = 2048 | no security attributes | Do not copy the security attributes of the file. (Version 4.71.)                                                               |
| `0x1000` <br> = 4096 | no recursion           | Only operate in the local directory. Do not operate recursively into subdirectories.                                           |
| `0x2000` <br> = 8192 | no file grouping       | Do not copy connected files as a group. Only copy the specified files. (Version 5.0.)                                          |

Example: **combine** _create directories_, _no error UI_ and _rename duplicates_

```powershell
$copyFlags = 0x400 + 0x200 + 0x8
```

```powershell
$copyFlags = 0x608
```

---
Sources:
- 2022-09-02: [Copying Files In PowerShell - Using Windows Explorer UI - BackSlasher](https://blog.backslasher.net/copying-files-in-powershell-using-windows-explorer-ui.html)
- 2022-09-02: [Folder.CopyHere method (Shldisp.h) - Win32 apps - Microsoft Docs](https://docs.microsoft.com/en-us/windows/win32/shell/folder-copyhere)

Related:

Tags:
[File System - Use paths, get meta data, link, download, and encrypt files and folders](./file-system.md)
