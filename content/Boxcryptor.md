---
dg-publish: true
not-in-use: true
microsoft-id: 
winget-id: SecombaGmbH.Boxcryptor
github-repo: 
github-release-filename: 
website: https://www.boxcryptor.com/en/download/
priority: 
---

Boxcryptor is a **discarded** app.  
- Invoke the installer listed on Windows Package Manager:
  ```
  winget install -e SecombaGmbH.Boxcryptor
  ```
- Download it from the [publisher's website](https://www.boxcryptor.com/en/download/)


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
- [Cleanup navigation pane](./File%2520Explorer.md##Cleanup%2520navigation%2520pane)

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

| Folder name  | New location              |
| ------------ | ------------------------- |
| Desktop      | `D:\Desktop`              |
| Documents    | `D:\OneDrive\Documents`   |
| Downloads    | `D:\Download`             |
| Music        | `X:\OneDrive\Musicᴱ`      |
| Videos       | `X:\OneDrive\Videosᴱ`     |
| Pictures¹⁾   | `X:\OneDrive\Picturesᴱ`   |
| _3D Objects_ | `X:\OneDrive\3D-Objectsᴱ` |

> ¹⁾ if redirecting `Pictures` fails, do the following  
> - Open [Registry](Registry.md)(how-to-dos.md#--Edit-registry) 
> ```
> HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders
> ```
> 
> | Value name                               | Value data                               |
> | ---------------------------------------- | ---------------------------------------- |
> | `X:\OneDrive\Picturesᴱ`                  | `My Pictures`                            |
> | `X:\OneDrive\Picturesᴱ`                  | `{0DDD015D-B06C-45D5-8C4C-F59713854639}` |
> | `X:\OneDrive\Picturesᴱ\Eigene Aufnahmen` | `{AB5FB87B-7CE2-4F83-915D-550846C9537B}` |
> | `X:\OneDrive\Picturesᴱ\Screenshots`      | `{B7BEDE81-DF94-4682-A7D8-57A52620B86F}` |
>
> - Restart explorer


---
Sources:

Related:

Tags:
[Install storage apps](./Install%20storage%20apps.md)