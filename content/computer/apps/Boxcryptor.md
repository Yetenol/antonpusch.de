---
date: "2025-03-22T23:45:54.987+01:00"
title: "Boxcryptor"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: true
microsoft-id: 
winget-id: SecombaGmbH.Boxcryptor
github-repo: 
github-release-filename: 
website: https://www.boxcryptor.com/en/download/
priority: 
categories:
  - Storage
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

## Enable recycle bin

- Open `System Tray > Boxcryptor > Settings > Advanced`
  - [x] Start with Windows
  - [x] Check for updates
  - Click `Show more settigns`
  - [x] Enable recycle bin
  - [ ] Auto detect removable drives
  - [ ] Auto detect network drives
- **Hide** Boxcryptor **drive** from Windows Explorer's **navigation pane**  
  Enabling recycling bin, mounts Boxcryptor as a fixed drive which makes it a _removable_ drive, 
  thus by default Windows shows it in the top level of the navigation pane. To disable:
- [Cleanup navigation pane](./File-Explorer.md##Cleanup%2520navigation%2520pane)

## Remove desktop drive shortcut

- run elevated:
    ```powershell
    Remove-Item -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\{CA9A9348-B9BC-455E-80DC-8E803145F80B}"
    ```
  to revert this change:  
  `New-Item -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\{CA9A9348-B9BC-455E-80DC-8E803145F80B}" -Value "Boxcryptor"`

## Redirect This PC folders

> How to redirect a `Folder` in `This PC`:
> - Open `Properties > Location > Move`
> - Enter the new path and click `OK`
> - If asked wether to move the files click `Yes`

- Redirect the following folders

- Desktop = `D:\Desktop`
- Documents = `D:\OneDrive\Documents`
- Downloads = `D:\Download`
- Music = `X:\OneDrive\Musicᴱ`
- Videos = `X:\OneDrive\Videosᴱ`
- Pictures = `X:\OneDrive\Picturesᴱ`
- _3D Objects_ = `X:\OneDrive\3D-Objectsᴱ`

# Manually set Pictures folder

if redirecting `Pictures` fails, do the following  

Open Registry at `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders`
- My Pictures = `X:\OneDrive\Picturesᴱ` 
- {0DDD015D-B06C-45D5-8C4C-F59713854639} = `X:\OneDrive\Picturesᴱ`
- {AB5FB87B-7CE2-4F83-915D-550846C9537B} =  `X:\OneDrive\Picturesᴱ\Eigene Aufnahmen`
- {B7BEDE81-DF94-4682-A7D8-57A52620B86F} = `X:\OneDrive\Picturesᴱ\Screenshots`

- Restart explorer
