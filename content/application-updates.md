---
title: "Application Updates - Bulk upgrade applications from Microsoft Store, winget, or git"
date: "2024-07-24T00:00:00.000+02:00"
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
[Autohotkey - Interact with applications and streamline repetitive tasks](./autohotkey.md)

Tags:
[PowerShell - A command-line shell and scripting language to manage Windows system and automate administrative tasks](./powershell.md)
