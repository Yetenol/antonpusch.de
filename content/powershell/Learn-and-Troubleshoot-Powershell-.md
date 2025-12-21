---
date: "2025-07-17T08:13:58.379+02:00"
title: "Learn and Troubleshoot Powershell"
description: "Discover commands, and access documentation"
dg-publish: true
dg-folder: powershell
---

**Update help files** using elevated command
```powershell
Update-Help
```

# Discover commands

Discover **all nouns** of PowerShell modules    
```powershell
Get-Command -Module Microsoft.PowerShell* | group Noun | Format-Wide -AutoSize
```

Discover **all commands** about a noun    
```powershell
Get-Command -Noun Web* | foreach { Get-Help $_ } | Format-Table Name, Synopsis
```

Discover **all modules**    
```powershell
Get-Module
```
```powershell
Get-Module -ListAvailable
```

# Access documentation

Example command:
```powershell
$help = Get-Help -Name Invoke-WebRequest
```

Show help **online**    
```powershell
Get-Help -Name Invoke-WebRequest -Online
```
- abbreviate `help Invoke-WebRequest -Online`

Learn **syntax**    
```powershell
$help.syntax
```
- abbreviate `(help Invoke-WebRequest).syntax` or `(Invoke-WebRequest -?).syntax`

Learn **purpose**    
```powershell
$help.Synopsis
```
- abbreviate `(help Invoke-WebRequest).Synopsis` or `(Invoke-WebRequest -?).Synopsis`

Read **description**    
```powershell
$help.description
```
- abbreviate `(help Invoke-WebRequest).description` or `(Invoke-WebRequest -?).description`  

See **examples**    
```powershell
$help.examples
```
- abbreviate `help Invoke-WebRequest -Examples` or `(Invoke-WebRequest -?).examples`  


---
Sources:

Related:
```dynamic-embed
[[List related notes]]
``` 

Tags:
[PowerShell - A command-line shell and scripting language to manage Windows system and automate administrative tasks](./index.md)