---
title: "List all bluetooth devices"
date: "2024-07-24T00:00:00.000+02:00"
dg-publish: true
priority: 
---

```powershell
Get-PnpDevice -Class Bluetooth | where HardwareID -Match "\\DEV_"
```


---
Sources:

Related:

Tags:
[Programm PowerShell - Learn PowerShell's programming paradigms](./programm-powershell.md)
