---
title: "List all bluetooth devices"
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
[Programm PowerShell - Learn PowerShell's programming paradigms](./programm%20powershell.md)
