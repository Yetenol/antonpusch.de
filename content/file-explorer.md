---
title: "File Explorer"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
microsoft-id: 
winget-id: 
github-repo: 
github-release-filename: 
website: 
priority: 1
synopsis: ""
---

File Explorer is a app. 



File Explorer is preinstalled.

# View options

- [x] `View > Show > File name extensions`

# Cleanup navigation pane

- **Hide removable drives** from the top level  
  run elevated:

  ```powershell
  Remove-Item -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\DelegateFolders\{F5FB2C77-0E2F-4A16-A381-3E560C68BC83}"
  ```

  to revert the change:  
  `New-Item -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\DelegateFolders\{F5FB2C77-0E2F-4A16-A381-3E560C68BC83}" -Value "Removable Drives"`

# Setup icon paths

- **Link** the **icon folder** to the system-wide symbolic link `C:\FI\`  
    run elevated:

    ```powershell
    New-Item -Path "C:\FI" -ItemType SymbolicLink -Target "D:\OneDrive\Designᴱ\Folder Iconsᴰ\ico"
    ```

- **Set custom icons** for files or folders if desired  
    - `Right-click > Properties > Customize > Change Icon…`
    - `C:\FI\` ← Type the path and use autocomplete
