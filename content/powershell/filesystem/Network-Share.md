---
date: "2025-07-17T08:13:58.487+02:00"
title: "Network Share"
description: "Mount a Windows network share as file system drive to sync files via SMB in PowerShell"
dg-publish: true
dg-folder: powershell/filesystem
---
Store password as encrypted string in a file
- Uses [Windows Data Protection API (DPAPI)](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.5), so that only the same user on the same machine can decrypt it. 
```powershell
$passwordFile = "C:\scripts\encryptedPassword.dat"
$securedPassword = Read-Host "Enter password" -AsSecureString
$securedPassword | ConvertFrom-SecureString | Out-File $passwordFile
```

Mount network share as **network drive**
```powershell
$networkShare = "\\my-server\data"
$username = "my-server\utility-user"
$passwordFile = "C:\scripts\encryptedPassword.dat"
$securedPassword = Get-Content $passwordFile | ConvertTo-SecureString
$credential = New-Object System.Management.Automation.PSCredential(
    $username, $securedPassword)
New-PSDrive -Name "Q" -PSProvider FileSystem -Root $CONFIG.DestinationShare -Credential $credential -Persist
Test-Path "Q:\"
```
