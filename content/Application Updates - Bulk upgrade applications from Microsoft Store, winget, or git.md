---
publish: true
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
[Autohotkey - Interact with applications and streamline repetitive tasks](./Autohotkey%20-%20Interact%20with%20applications%20and%20streamline%20repetitive%20tasks.md)

Tags:
[PowerShell - A command-line shell and scripting language to manage Windows system and automate administrative tasks](./PowerShell%20-%20A%20command-line%20shell%20and%20scripting%20language%20to%20manage%20Windows%20system%20and%20automate%20administrative%20tasks.md)
