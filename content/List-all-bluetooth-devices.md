---
date: "2025-03-22T07:21:28.111+01:00"
title: "List all bluetooth devices"
description: "-"
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
[Programm PowerShell - Learn PowerShell's programming paradigms](./Programm-PowerShell.md)
