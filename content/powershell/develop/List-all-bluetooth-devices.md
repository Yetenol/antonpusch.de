---
date: "2025-07-17T08:13:58.394+02:00"
title: "List all bluetooth devices"
description: "-"
dg-publish: true
dg-folder: powershell/develop
---

```powershell
Get-PnpDevice -Class Bluetooth | where HardwareID -Match "\\DEV_"
```
