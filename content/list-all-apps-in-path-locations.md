---
title: "List all apps in PATH locations"
date: "2024-07-24T13:25:20.451+02:00"
dg-publish: true
priority: 
---

```powershell
$paths = [String[]] @($env:path -split ";") 
$paths = $paths[0..($paths.Length-2)]
$paths = $paths.ForEach({"$_\*"})
Get-ChildItem -Path $paths -Include *.exe, *.msc `
    | Select -Property `
    @{Label="Type"; Expression={($_.Extension.toUpper() -replace "\`.","")}}, `
    @{Label="Command"; Expression={($_.Name -replace ".exe", "")}}, `
    @{Label="Description"; Expression={[System.Diagnostics.FileVersionInfo]::GetVersionInfo($_).FileDescription}}, `
    @{Label="Version"; Expression={[System.Diagnostics.FileVersionInfo]::GetVersionInfo($_).FileVersion}}, `
    @{Label="Size|KB"; Expression={[math]::Round($_.Length / 1KB)}}, `
    @{Label="Location"; Expression={$_.Directory}} `
    | Sort-Object -Property `
    @{Expression="Location"; Descending=$False}, `
    @{Expression="Extension"; Descending=$True}, `
    @{Expression="Description"; Descending=$False} `
    | Export-Csv -Path "$env:temp\path-apps.csv" -NoType -Delimiter ";"
start "$env:temp\path-apps.csv"
```


---
Sources:

Related:

Tags:
[Programm PowerShell - Learn PowerShell's programming paradigms](./programm-powershell.md)
