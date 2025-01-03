---
title: "Executable scripts - Make scripts executable when renamed cmd"
date: "2024-07-24T00:00:00.000+02:00"
dg-publish: true
---

Make a script self-elevating

```powershell
# Ensure script is running elevated
if (-not ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).
    IsInRole([Security.Principal.WindowsBuiltInRole]::"Administrator")) {
    if ((Get-Command wt.exe) -ne $null) {
        Start-Process wt "powershell -File $PSCommandPath -ExecutionPolicy Bypass" -Verb RunAs
    }
    else {
        Start-Process powershell "-File $PSCommandPath -ExecutionPolicy Bypass" -Verb RunAs
    }
    exit
}
```

Make a PowerShell script a standalone executable script by  
pasting the following snippets at the beginning of a script and by  
adding `.bat` to the file extension like `script.ps1.bat`  
Script cannot be started relatively like `modules\script.ps1.bat`  
This bypasses the _Execution Policy_ for PowerShell scripts.

**Make** script executable  

```cmd
# & cls & powershell -Command "Invoke-Command -ScriptBlock ([ScriptBlock]::Create(((Get-Content """%0""") -join [Environment]::NewLine)))" & exit
# Script is executable when renamed *.cmd or *.bat
```

**Make** script executable and **persistent**

```cmd
# & cls & powershell -NoExit -Command "Invoke-Command -ScriptBlock ([ScriptBlock]::Create(((Get-Content """%0""") -join [Environment]::NewLine)))" & exit
# Script is executable and persistent when renamed *.cmd or *.bat
```

**Make** script executable and **self-elevating**  

```cmd
# & cls & powershell -Command Start-Process wt -Verb RunAs -ArgumentList """PowerShell.exe -Command cd "%CD%" `n Invoke-Command -ScriptBlock ([ScriptBlock]::Create(((Get-Content %0) -join [Environment]::NewLine)))""" & exit
# Script is executable and self-elevating when renamed *.cmd or *.bat
```

**Make** script executable, **self-elevating** and **persistent**

```cmd
# & cls & powershell -Command Start-Process wt -Verb RunAs -ArgumentList """PowerShell.exe -NoExit -Command cd "%CD%" `n Invoke-Command -ScriptBlock ([ScriptBlock]::Create(((Get-Content %0) -join [Environment]::NewLine)))""" & exit
# Script is executable, self-elevating and persistent when renamed *.cmd or *.bat
```

---

Sources:

Related:
[Command Prompt](Command%20Prompt)

Tags:
[Programm PowerShell - Learn PowerShell's programming paradigms](./programm-powershell.md)
