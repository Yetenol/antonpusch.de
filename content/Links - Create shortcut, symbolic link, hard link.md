---
dg-publish: true
priority: 6
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
[File System - Use paths, get meta data, link, download, and encrypt files and folders](./File%20System%20-%20Use%20paths,%20get%20meta%20data,%20link,%20download,%20and%20encrypt%20files%20and%20folders.md)
