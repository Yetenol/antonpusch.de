---
publish: true
priority: 7
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
[Operate on file system - Use paths, get meta data, link, download, and encrypt files and folders](./Operate%20on%20file%20system%20-%20Use%20paths,%20get%20meta%20data,%20link,%20download,%20and%20encrypt%20files%20and%20folders.md)
