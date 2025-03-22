---
date: "2025-03-22T10:39:37.961+01:00"
title: "Connect via SFTP"
description: "Use WinSCP module to connect via SFTP"
dg-publish: true
dg-folder: powershell/filesystem
---

Install WinSCP PowerShell modul:
```powershell
Install-Module -Name WinSCP -Scope AllUsers
Import-Module WinSCP
```

Store password as encrypted string in a file
- Uses [Windows Data Protection API (DPAPI)](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.5), so that only the same user on the same machine can decrypt it. 
```powershell
$passwordFile = "C:\scripts\encryptedPassword.dat"
$securedPassword = Read-Host "Enter password" -AsSecureString
$securedPassword | ConvertFrom-SecureString | Out-File $passwordFile
```

Test SFTP connection
```powershell
$server = "sftp.example.com"
$port = 22
$username = "dataexport"
$passwordFile = "C:\scripts\encryptedPassword.dat"

$securedPassword = Get-Content $passwordFile | ConvertTo-SecureString
$credential = New-Object System.Management.Automation.PSCredential(
    $username, $securedPassword)
$sessionOptions = New-WinSCPSessionOption -HostName $server -PortNumber $port `
    -Credential $credential -SshHostKeyPolicy GiveUpSecurityAndAcceptAny
New-WinSCPSession -SessionOption $sessionOptions
```

---
Sources:
- [GitHub - tomohulk/WinSCP: WinSCP PowerShell Wrapper Module](https://github.com/tomohulk/WinSCP)

Related:

Tags:
