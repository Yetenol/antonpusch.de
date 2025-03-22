---
date: "2025-03-22T21:41:29.844+01:00"
title: "CSIDL folders"
description: "-"
dg-publish: true
dg-folder: windows/known-folders
---
```powershell
(New-Object -ComObject Shell.Application).NameSpace(0x7).Self.Path
```

- [KNOWNFOLDERID (Knownfolders.h) - Win32 apps \| Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/shell/knownfolderid)
- [CSIDL (Shlobj.h) - Win32 apps \| Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/shell/csidl)