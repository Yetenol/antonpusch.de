---
date: "2025-07-17T08:13:58.825+02:00"
title: "Sudo"
description: "Switch and test elevated execution, Run as Administrator"
dg-publish: true
dg-folder: powershell/filesystem
---

Elevated current process unless executed privileged
```powershell
$is_executed_privileged = ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).
    IsInRole([Security.Principal.WindowsBuiltInRole]::"Administrator")
if (-not $is_executed_privileged) {
    if ((Get-Command wt.exe) -ne $null) {
        Start-Process wt "powershell -File $PSCommandPath -ExecutionPolicy Bypass" -Verb RunAs
    } else {
        Start-Process powershell "-File $PSCommandPath -ExecutionPolicy Bypass" -Verb RunAs
    }
    Start-Sleep 10
    exit
}
"Hello World"
Read-Host
```

The flag _Run as Administrator_ is stored in byte `0x15` (= 21) at bit `0x20` (= 6).

**Enable** elevated execution for a file

```powershell
$bytes = [System.IO.File]::ReadAllBytes((Resolve-Path $file))
$bytes[0x15] = $bytes[0x15] -bor 0x20 
[System.IO.File]::WriteAllBytes((Resolve-Path $file), $bytes)
```

**Disable** elevated execution for a file

```powershell
$bytes = [System.IO.File]::ReadAllBytes((Resolve-Path $file))
$bytes[0x15] = $bytes[0x15] -bxor 0x20
[System.IO.File]::WriteAllBytes((Resolve-Path $file), $bytes)
```

**Test** whether this process is elevated

```powershell
[bool] $isProcessElevated = ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] "Administrator")
```

**Require** elevated execution

```powershell
#Requires -RunAsAdministrator
```

```powershell
if (-not ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] "Administrator")) {
 throw "Administrator privilege required to run this script"
}
```

**Create** a scheduled task

```powershell
$actions = (New-ScheduledTaskAction -Execute 'powershell')
$principal = New-ScheduledTaskPrincipal -GroupId "BUILTIN\Administrators" -RunLevel Highest
$task = New-ScheduledTask -Action $actions -Principal $principal
Register-ScheduledTask 'Diagnostics' -InputObject $task
```

---
Sources:
- 2022-04-25: [windows - How to create a Run As Administrator shortcut using Powershell - Stack Overflow](https://stackoverflow.com/questions/28997799/how-to-create-a-run-as-administrator-shortcut-using-powershell)
- 2023-03-02: [Running a command as Administrator using PowerShell? - Stack Overflow](https://stackoverflow.com/questions/7690994/running-a-command-as-administrator-using-powershell)

Related:

Tags:
[File system operations - Use paths, get meta data, link, download, and encrypt files and folders](./index.md)
