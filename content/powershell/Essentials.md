---
date: "2025-03-22T21:55:55.934+01:00"
title: "Essentials"
description: "Access documentation, log data, handle errors in PowerShell"
dg-publish: true
dg-folder: powershell
---
# Access documentation

Open browser with help page about a command
```powershell
Get-Help Get-Process -Online
```
- abbreviate as `help Get-Process -Online`
- opens [Get-Process - Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-process?view=powershell-7.5&viewFallbackFrom=powershell-6)


Find commands related to a topic
```powershell
Get-Command -Noun Process*
```
- abbreviate as `gcm -Noun Process*`
- outputs Debug-Process, Get-Process, Get-ProcessMitigation, Start-Process, …

- [Learn and Troubleshoot Powershell  - Discover commands, and access documentation](./Learn-and-Troubleshoot-Powershell-.md)

# Get object properties

List available properties, methods for an object or command
```powershell
h | Get-Member -MemberType Properties
```
- abbreviate as `h | gm`
- outputs Attributes, CreationTime, CreationTimeUtc, Exists, Extension, FullName, …

Output a property
```powershell
$o = Get-Item .
$o.Attributes
```
- one-liner: `Get-Item . | select -expand Attributes`

## Configuration and Variables

Log to file
```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
$PSDefaultParameterValues['Set-Content:Encoding'] = 'utf8'
"Hallo und Tschüss!" >> "test.log"
```
- Set encoding, as PowerShell 5 uses different ones by default

Bundle configuration variables as the start of a script
```powershell
$CONFIG = [PSCustomObject]@{
    SourcePath       = "E:\Data\Analytics\SourceData"
    LogFile          = "C:\scripts\DataExport.log"
    MaxLogLines      = 1000
}
```

- [Handle data - Handle, Import, Export, Filter and RegEx query objects in PowerShell](./data/index.md)

## Error Handling

Stop on any error
```powershell
$ErrorActionPreference = [Management.Automation.ActionPreference]::Stop
```

Detect errors
```powershell
try {
    Get-Content "file-that-might-not-exist.txt" -ErrorAction Stop
} catch {
    Write-Output "Error: $_"
} finally {
    Write-Output "Operation complete"
}
```

## Comparison Operators

```powershell
# String comparisons
"Text" -eq "text"   # Case-insensitive equal (True)
"Text" -ceq "text"  # Case-sensitive equal (False)
"Hello" -like "H*"  # Wildcard match (True)
"abc" -match "^a"   # RegEx match (True)

# Numeric comparisons
5 -gt 2     # Greater than (True)
5 -ge 5     # Greater than or equal (True)
5 -lt 10    # Less than (True)

# Logical operators
$true -and $false  # Logical AND (False)
$true -or $false   # Logical OR (True)
-not $true         # Logical NOT (False)
```
