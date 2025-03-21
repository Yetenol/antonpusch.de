---
publish: true
priority: 2
---

Example input

```powershell
$Path = ".\README.md"
$Path = $env:UserProfile
```

Require all paths to exist, by stopping at every error

```powershell
$ErrorActionPreference = [Management.Automation.ActionPreference]::Stop
```

# String

**Get** path of **existing** file or folder    

```powershell
[String] $fileOrFolder = $Path -replace '[\\/]$', '' | Convert-Path
```

**Fake** path of file or folder   

```powershell
[String] $file = $Path | foreach {
    $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath($_)
}
```

```powershell
[String] $folder = $Path -replace '[\\/]$', '' | foreach {
    $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath($_)
}
```

# Filesystem Information Object

Files and folders contain `FullName`, `Extension`, `Name`, `Exists`, `CreationTime`, `CreationTimeUtc`, `LastAccessTime`, `LastAccessTimeUtc`, `LastWriteTime`, `LastWriteTimeUtc`, `Attributes`.

Files also contain `Length`, `DirectoryName`, `Directory`, `IsReadOnly`.

Folders also contain `Parent`, `Root`.

**Retrieve** information of **existing** file or folder

```powershell
[IO.FileInfo] $visibleFile = $Path | Get-Item
```

```powershell
[IO.DirectoryInfo] $visibleFolder = $Path -replace '[\\/]$', '' | Get-Item
```

```powershell
[IO.FileSystemInfo] $visibleFileOrFolder = $Path -replace '[\\/]$', '' | Get-Item
```

```powershell
[IO.FileInfo] $anyFile = $Path | Get-Item -Force
```

```powershell
[IO.DirectoryInfo] $anyFolder = $Path -replace '[\\/]$', '' | Get-Item -Force
```

```powershell
[IO.FileSystemInfo] $anyFileOrFolder = $Path -replace '[\\/]$', '' | Get-Item -Force
```

**Retrieve** information of **existing** file or folder      
or **fake** information of **non-existing** file or folder    

```powershell
[IO.FileInfo] $file = $Path | foreach {
    $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath($_)
} | foreach { 
    [IO.FileInfo]::new($_)
}
```

```powershell
[IO.DirectoryInfo] $folder = $Path -replace '[\\/]$', '' | foreach {
    $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath($_)
} | foreach { 
    [IO.DirectoryInfo]::new($_)
}
```

---

Sources:

Related:

Tags:
[Operate on file system - Use paths, get meta data, link, download, and encrypt files and folders](./Operate%20on%20file%20system.md)
