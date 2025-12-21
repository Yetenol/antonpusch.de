---
date: "2025-07-17T08:13:58.979+02:00"
title: "User folders"
description: "Locate or redirect the download, desktop, This PC folder"
dg-publish: true
priority: 1
dg-folder: windows/known-folders
---

## User-Specific Folders

**List all locations**
```powershell
Get-ItemProperty -Path "HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders" | select * -Exclude "PS*"
```

**Resolve one location**  
- return the location as a string
```powershell
${env:ProgramFiles(x86)}
[Environment]::GetFolderPath("MyPictures")
$env:Pictures = (New-Object -ComObject Shell.Application).NameSpace('shell:My Pictures').Self.Path
$env:Downloads = (New-Object -ComObject Shell.Application).NameSpace('shell:::{374DE290-123F-4565-9164-39C4925E467B}').Self.Path
```
- `$env:Pictures = (Get-ItemProperty -Path "HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders")."My Pictures"`


**Default locations**  
- Value type: REG_EXPAND_SZ

| Shell Folder Name - _Description_                         | Default location                                                              |
| --------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `AppData`                                                 | `%USERPROFILE%\AppData\Roaming`                                               |
| `Cache` <br> _Internet Explorer Cache_                    | `%USERPROFILE%\AppData\Local\Microsoft\Windows\INetCache`                     |
| `Cookies` <br> _Internet Explorer Cookies_                | `%USERPROFILE%\AppData\Local\Microsoft\Windows\INetCookies`                   |
| `Desktop`                                                 | `%USERPROFILE%\Desktop`                                                       |
| `Favorites`                                               | `%USERPROFILE%\Favorites`                                                     |
| `History`                                                 | `%USERPROFILE%\AppData\Local\Microsoft\Windows\History`                       |
| `Local AppData`                                           | `%USERPROFILE%\AppData\Local`                                                 |
| `My Music`                                                | `%USERPROFILE%\Music`                                                         |
| `My Pictures`                                             | `%USERPROFILE%\Pictures`                                                      |
| `My Video`                                                | `%USERPROFILE%\Videos`                                                        |
| `NetHood` <br> _Network Shortcuts_                        | `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Network Shortcuts`           |
| `Personal` <br> _Documents_                               | `%USERPROFILE%\Documents`                                                     |
| `PrintHood`                                               | `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Printer Shortcuts`           |
| `Programs`                                                | `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`         |
| `Recent`                                                  | `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Recent`                      |
| `SendTo`                                                  | `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\SendTo`                      |
| `Start Menu`                                              | `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu`                  |
| `Startup`                                                 | `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup` |
| `Templates`                                               | `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Templates`                   |
| `{374DE290-123F-4565-9164-39C4925E467B}` <br> _Downloads_ | `%USERPROFILE%\Downloads`                                                     |

## If cloud synchronization enabled

The following items do not exist in a clean install of Windows 10 and Windows 11. They’re created only if you redirect those folders to Microsoft OneDrive or DropBox. If the following values exist, the location defined in the following values takes precedence. In case of any conflict, the following values can be deleted so that the defaults (above) are used.

| Shell Folder Name                        | Description       |
| ---------------------------------------- | ----------------- |
| `{A52BBA46-E9E1-435F-B3D9-28DAA648C0F6}` | _Cloud Root_      |
| `{3B193882-D3AD-4EAB-965A-69829D1FB59F}` | _Saved Pictures_  |
| `{AB5FB87B-7CE2-4F83-915D-550846C9537B}` | _Camera Roll_     |
| `{B7BEDE81-DF94-4682-A7D8-57A52620B86F}` | _Screenshots_     |
| `{F42EE2D3-909F-4907-8871-4C22FC0BF756}` | _Local Documents_ |
| `{7D83EE9B-2244-4E70-B1F5-5393042AF1E4}` | _Local Downloads_ |
| `{A0C69A99-21C8-4671-8703-7934162FCF1D}` | _Local Music_     |
| `{0DDD015D-B06C-45D5-8C4C-F59713854639}` | _Local Pictures_  |
| `{35286A68-3C57-41A1-BBB1-0EAE73D76C95}` | _Local Videos_    |

## Common-User Folders

**List all locations**  
```powershell
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders" | select * -Exclude "PS*"
```

**Resolve one location**  
- return the location as a string:
```powershell
$env:CommonStartMenu = (New-Object -ComObject Shell.Application).NameSpace('shell:Common Start Menu').Self.Path
$env:CommonDownloads = (New-Object -ComObject Shell.Application).NameSpace('shell:::{3D644C9B-1FB8-4f30-9B45-F670235F79C0}').Self.Path
```
- `$env:CommonStartMenu = (Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders")."Common Start Menu"`


**Default locations**
- Value type: REG_EXPAND_SZ

| Shell Folder Name - _Description_                                | Default location                                              |
| ---------------------------------------------------------------- | ------------------------------------------------------------- |
| `{3D644C9B-1FB8-4f30-9B45-F670235F79C0}` <br> _Common Downloads_ | `%PUBLIC%\Downloads`                                          |
| `Common AppData`                                                 | `%ProgramData%`                                               |
| `Common Desktop`                                                 | `%PUBLIC%\Desktop`                                            |
| `Common Documents`                                               | `%PUBLIC%\Documents`                                          |
| `Common Programs`                                                | `%ProgramData%\Microsoft\Windows\Start Menu\Programs`         |
| `Common Start Menu`                                              | `%ProgramData%\Microsoft\Windows\Start Menu`                  |
| `Common Startup`                                                 | `%ProgramData%\Microsoft\Windows\Start Menu\Programs\Startup` |
| `Common Templates`                                               | `%ProgramData%\Microsoft\Windows\Templates`                   |
| `CommonMusic`                                                    | `%PUBLIC%\Music`                                              |
| `CommonPictures`                                                 | `%PUBLIC%\Pictures`                                           |
| `CommonVideo`                                                    | `%PUBLIC%\Videos`                                             |



---
Sources:
- 2022-04-23: [Windows 10-11 User Shell Folders Restore Default Paths » Winhelponline](https://www.winhelponline.com/blog/windows-10-shell-folders-paths-defaults-restore/)

Related:

Tags:
[Known folders - Access the recycle bin, desktop, downloads folder](./index.md)
