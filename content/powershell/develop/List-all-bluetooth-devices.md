---
date: "2025-03-22T18:17:54.774+01:00"
title: "List all bluetooth devices"
description: "-"
dg-publish: true
dg-folder: powershell/develop
---

```powershell
Get-PnpDevice -Class Bluetooth | where HardwareID -Match "\\DEV_"
```
