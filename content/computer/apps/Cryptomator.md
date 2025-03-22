---
date: "2025-03-22T23:45:54.987+01:00"
title: "Cryptomator"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: 
microsoft-id: 
winget-id: Cryptomator.Cryptomator
github-repo: cryptomator/cryptomator
github-release-filename: 
website: https://cryptomator.org/downloads/win/thanks/
priority: 
link-modportals: 
modportal0-id: 
thumbnail: 
categories:
  - Storage
synopsis: With Cryptomator, the key to your data is in your hands. Cryptomator encrypts your data quickly and easily. Afterwards you upload them protected to your favorite cloud service.
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

## Redirect This PC folders

Redirect the main folders in *This PC* as following:
- Open `Properties > Location > Move`
- Enter the new path and click `OK`
- If asked wether to move the files click `Yes`

| Folder name  | New location            |
| ------------ | ----------------------- |
| Desktop      | `D:\Desktop`            |
| Documents    | `D:\OneDrive\Documents` |
| Downloads    | `D:\Download`           |
| Music        | `E:\Musicᴱ`             |
| Videos       | `E:\Videosᴱ`            |
| Pictures¹⁾   | `E:\Picturesᴱ`          |
| _3D Objects_ | `E:\3D-Objectsᴱ`        |

¹⁾ if redirecting `Pictures` fails, edit the Registry at
```
HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders
```

| Value name                      | Value data                               |
| ------------------------------- | ---------------------------------------- |
| `E:\Picturesᴱ`                  | `My Pictures`                            |
| `E:\Picturesᴱ`                  | `{0DDD015D-B06C-45D5-8C4C-F59713854639}` |
| `E:\Picturesᴱ\Eigene Aufnahmen` | `{AB5FB87B-7CE2-4F83-915D-550846C9537B}` |
| `E:\Picturesᴱ\Screenshots`      | `{B7BEDE81-DF94-4682-A7D8-57A52620B86F}` |

- Restart explorer
