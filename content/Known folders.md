---
publish: true
priority: 1
---

- [User folders - Locate or redirect the download, desktop, This PC folder](./User%20folders.md)
- [Panels and system folders - Locate the recycle bin, control panels](./panels%20and%20system%20folders.md)
- [Deprecated panels and system folders - Locate deprecated 3D Objects folder](./Deprecated%20panels%20and%20system%20folders.md)

# Import all user folders as environment variables

Define user folder macros

```powershell
@{
    AppData = 'AppData'; IECache = 'Cache'; IECookies = 'Cookies'; Desktop = 'Desktop'; Favorites = 'Favorites'; History = 'History'; LocalAppData = 'Local AppData'; Music = 'My Music'; Pictures = 'My Pictures'; Videos = 'My Video'; Documents = 'Personal'; Downloads = '{374DE290-123F-4565-9164-39C4925E467B}'; NetworkShortcuts = 'NetHood'; PrinterShortcuts = 'PrintHood'; Programs = 'Programs'; Recent = 'Recent'; SendTo = 'SendTo'; StartMenu = 'Start Menu'; Startup = 'Startup'; Templates = 'Templates'; CloudRoot = '{A52BBA46-E9E1-435F-B3D9-28DAA648C0F6}';
    SavedPictures = '{3B193882-D3AD-4EAB-965A-69829D1FB59F}'; CameraRoll = '{AB5FB87B-7CE2-4F83-915D-550846C9537B}'; Screenshots = '{B7BEDE81-DF94-4682-A7D8-57A52620B86F}'; LocalDocuments = '{F42EE2D3-909F-4907-8871-4C22FC0BF756}'; LocalDownloads = '{7D83EE9B-2244-4E70-B1F5-5393042AF1E4}'; LocalMusic = '{A0C69A99-21C8-4671-8703-7934162FCF1D}'; LocalPictures = '{0DDD015D-B06C-45D5-8C4C-F59713854639}'; LocalVideos = '{35286A68-3C57-41A1-BBB1-0EAE73D76C95}';
    CommonDownloads = '{3D644C9B-1FB8-4f30-9B45-F670235F79C0}'; CommonAppData = 'Common AppData'; CommonDesktop = 'Common Desktop'; CommonDocuments = 'Common Documents'; CommonPrograms = 'Common Programs'; CommonStartMenu = 'Common Start Menu'; CommonStartup = 'Common Startup'; CommonTemplates = 'Common Templates'; CommonMusic = 'CommonMusic'; CommonPictures = 'CommonPictures'; CommonVideos = 'CommonVideo';
} | 
% GetEnumerator | 
% { 
    $namespace = if ($_.Value -like '{*}') {"shell:::" + $_.Value} else {"shell:" + $_.Value}
    try { 
        [Environment]::SetEnvironmentVariable($_.Name, (New-Object -ComObject Shell.Application).NameSpace($namespace).Self.Path)
    } catch {}
}
```

Reveal folder in *File Explorer*    

```powershell
Invoke-Item -Path $env:Pictures
```

List available macros

```powershell
Get-ChildItem env:
```

---
Sources:
- 2022-04-24: [Known Folder GUIDs for File Dialog Custom Places - Windows Forms .NET Framework - Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/desktop/winforms/controls/known-folder-guids-for-file-dialog-custom-places?view=netframeworkdesktop-4.8)

Related:
```dynamic-embed
[[List related notes]]
``` 

Tags:
[Windows](./Windows.md)
[Operate on file system - Use paths, get meta data, link, download, and encrypt files and folders](./Operate%20on%20file%20system.md)
