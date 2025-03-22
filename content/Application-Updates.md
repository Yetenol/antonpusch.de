---
date: "2025-03-22T22:19:37.813+01:00"
title: "Application Updates"
description: "Bulk upgrade applications from Microsoft Store, winget, or git"
dg-publish: true
---

# Update all Microsoft Store apps

```powershell
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_EnterpriseModernAppManagement_AppManagement01"
$wmiObj = Get-WmiObject -Namespace $namespaceName -Class $className
$result = $wmiObj.UpdateScanMethod()
```

# Upgrade all winget apps

```powershell
winget upgrade --all
```

# Update all git repositories

- [shortcutFox-gitUpdateAll.ps1](https://github.com/Yetenol/shortcutFox/blob/main/source/scripts/gitUpdateAll.ps1)


---
Sources:

Related:
[AutoHotkey - Interact with applications and streamline repetitive tasks](./AutoHotkey.md)

Tags:
[PowerShell - A command-line shell and scripting language to manage Windows system and automate administrative tasks](./powershell/index.md)
