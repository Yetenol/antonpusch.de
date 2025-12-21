---
date: "2025-07-17T08:13:58.242+02:00"
title: "Handle errors in Powershell"
description: "-"
dg-publish: true
---

# Set default error handling

Stop execution of a script when any error occurs 
```powershell
$ErrorActionPreference = [Management.Automation.ActionPreference]::Stop
```

Execute only if previous command was successful

```powershell
Invoke-WebRequest 'https://github.com/Yetenol/shortcutFox/releases/latest/download/shortcutFox.exe' -OutFile "$env:Temp/shortcutFox.exe"
if ($?) {Start-Process "$env:Temp/shortcutFox.exe"}
```


---
Sources:
- 2023-03-21: [Everything you wanted to know about exceptions - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/scripting/learn/deep-dives/everything-about-exceptions?view=powershell-7.3)

Related:

Tags:
