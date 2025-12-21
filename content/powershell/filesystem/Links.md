---
date: "2025-10-20T09:31:21.691+02:00"
title: "Links"
description: "Create shortcut, symbolic link, hard link"
dg-publish: true
dg-folder: powershell/filesystem
---

# Create a shell link (shortcut)

Enable **run at startup**

```powershell
$target = "C:\Windows\system32\notepad.exe"
$shortcutName = "example.lnk"

$env:Startup = (New-Object -ComObject Shell.Application).NameSpace('shell:Startup').Self.Path
$WshShell = New-Object -comObject WScript.Shell
$Shortcut = $WshShell.CreateShortcut("$env:Startup\$shortcutName")
$Shortcut.TargetPath = $target
$Shortcut.Save()
```

Create a shortcut in **Startup**

```powershell
$env:Startup = (New-Object -ComObject Shell.Application).NameSpace('shell:Startup').Self.Path
$WshShell = New-Object -comObject WScript.Shell
$Shortcut = $WshShell.CreateShortcut("$env:Startup\example.lnk")
$Shortcut.TargetPath = "powershell.exe"
$Shortcut.WorkingDirectory = $env:TEMP
$Shortcut.Arguments = '-NoExit -Command "date"'
$Shortcut.IconLocation = "$env:SystemRoot\System32\notepad.exe"
$Shortcut.WindowStyle = [System.Diagnostics.ProcessWindowStyle]::Maximized
$Shortcut.Hotkey = "ALT+CTRL+F"
$Shortcut.Description = "Hover tooltip"
$Shortcut.Save()
```

# Symbolic links

Create a symbolic link

```powershell
New-Item -ItemType SymbolicLink `
    -Name <# Filename or Foldername #> `
    -Target <# Target Path #>
```

Create a hard link

```powershell
New-Item -ItemType HardLink `
    -Name <# Filename #> `
    -Target <# Target Path #>
```

Create a junction

```powershell
New-Item -ItemType Junction `
    -Name <# Folder name #> `
    -Target <# Target Path #>
```

---
Sources:
- 2022-04-25: [Create a desktop shortcut with Windows Script Host - Windows Client - Microsoft Docs](https://docs.microsoft.com/en-us/troubleshoot/windows-client/admin-development/create-desktop-shortcut-with-wsh)

Related:

Tags:
[File system operations - Use paths, get meta data, link, download, and encrypt files and folders](./index.md)
