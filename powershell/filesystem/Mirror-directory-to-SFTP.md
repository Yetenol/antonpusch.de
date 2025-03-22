---
date: "2025-03-22T10:39:45.269+01:00"
title: "Mirror directory to SFTP"
description: "Use WinSCP module to mirror a directory to a SFTP remote with PowerShell"
dg-publish: true
dg-folder: powershell/filesystem
---
Connect to a SFTP remote
- [Connect via SFTP - Use WinSCP module to connect via SFTP](./Connect-via-SFTP.md)

```powershell
Sync-WinSCPPath -LocalPath $srcDir -RemotePath $destDir -Mode Remote -Mirror
```

---
Sources:
- [GitHub - tomohulk/WinSCP: WinSCP PowerShell Wrapper Module](https://github.com/tomohulk/WinSCP)

Related:

Tags:
[Operate on file system - Use paths, get meta data, link, download, and encrypt files and folders](./index.md)