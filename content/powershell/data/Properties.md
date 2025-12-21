---
date: "2025-07-17T08:13:58.612+02:00"
title: "Properties"
description: "Inspect, filter, select, enrich, and sort objects"
dg-publish: true
dg-folder: powershell/data
---

Everything in PowerShell is already or becomes a .NET object. Therefore, you should be familiar with how to handle and analyze them. Objects are easiest to visualize as text tables, but keep in mind that the entries themselves can also be objects.

- PowerShell modules return objects of a specific type
- external programs return an array of lines `Object[]` (Array von Textzeilen) zurück.

An understanding of [pipelines](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_pipelines)is required. 

```powershell
$drives = Get-PSDrive
$files = Get-ChildItem -File
```

# Inspect result object

See object's [type](../../Data-Types.md) and properties
```powershell
$drives | Get-Member -MemberType Properties
```
- in terminals, you may abbreviate with `$drives | gm`

# Count objects

Count elements or file lines
```powershell
$drives.Count
```

Add **index** the each results
```powershell
$index = 0
$drives | foreach {
    $_ | Add-Member -NotePropertyName "Index" -NotePropertyValue ($index++) -Force
}
$drives | select Index, Name, Root
```

# Narrow down a result

Select **specific indexes**
```powershell
$drives | select -Index 2, 4, 7 
```
```powershell
$drives[2, 4, 7]
$drives[@(2; 4; 7)]
```

Select a **range** at the beginning, end or with specific indexes at the beginning
```powershell
$drives | select -First 2 -Last 3
```
```powershell
$drives[0..1 + -3..-1]
$drives[@(0..1; -3..-1)]
```

Select **duplicates** only once
```powershell
$drives.Provider | select -Unique
```

**Condition** expression(s) to be selected
- Learn operators using: `Get-Help about_Comparison_Operators`
```powershell
$drives | where {$_.Root -match "^HKEY_"}
```
``` powershell
$files | where { `
    ( $_.Extension -eq ".xml" -or $_.Name -like "example*" ) `
    -and 
    $_.LastWriteTime -ge [DateTime]::"2000-12-31" `
}
```
- in terminals, you may abbreviate with `$drives | where Name -match "vpn"`

# Select specific properties of a result

View **all** properties
```powershell
$drives | select -Property *
```

Select **existing** properties
```powershell
$drives | select -Property Verb, Noun
```

Select a **precalculated** property
```powershell
$files | foreach { [PSCustomObject]@{
    Name = $_.Name;
    "Size in MB" = [Math]::Round($_.Length / 1MB, 2);
}}
```

Select a property to be calculated **dynamically** during readout
```powershell
$files | select -Property @(
	"Name",
	@{
    	Label = "Size in MB"
    	Expression = { [Math]::Round($_.Length / 1MB, 2) }
    }
)
```
- in terminals, you may abbreviate with `$files | select Name, @{name="Size in MB"; expr={[Math]::Round($_.Length / 1MB, 2)}}`

# Sort a result

Sort ascending / default direction
```powershell
$drives | sort -Property Version, Name
```

Specify sorting direction
```powershell
$drives | sort -Property Version -Descending
```
```powershell
$drives | sort -Property @(
	@{
    	Expression = "Version"
    	Descending = $True
    },
	"Name"
)
```
- in terminals, you may abbreviate with `$drives | sort @{expr="Version"; desc=$True}, Name`

---
Sources:
- 2023-03-19: [about Calculated Properties - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_calculated_properties)
- 2023-03-19: [Add a calculated property with Select-Object in PowerShell – 4sysops](https://4sysops.com/archives/add-a-calculated-property-with-select-object-in-powershell/)
- 2023-03-10: [Select-Object (Microsoft.PowerShell.Utility) - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.3)
- 2023-03-10: [Add-Member (Microsoft.PowerShell.Utility) - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.3)
- 2023-03-10: [Ultimate Guide to Using PowerShell Add-Member Cmdlet - i Love PowerShell](https://ilovepowershell.com/powershell-modern/ultimate-guide-to-using-powershell-add-member-cmdlet/)
- 2023-03-10: [String.PadRight Methode (System) | Microsoft Learn](https://learn.microsoft.com/de-de/dotnet/api/system.string.padright?view=net-7.0)

Related:
```dynamic-embed
[[List related notes]]
```

Tags:
[Handle data - Handle, Import, Export, Filter and RegEx query objects in PowerShell](./index.md)
