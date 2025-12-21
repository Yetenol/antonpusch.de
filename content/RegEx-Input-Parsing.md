---
date: "2025-07-17T08:13:58.674+02:00"
title: "RegEx Input Parsing"
description: "Import data out of plaintext using regular expressions"
dg-publish: true
---

# Overview

```powershell
$linesWithPattern = $lines | where {$_ -match "block"}
$occurrences = [RegEx]::Matches($multiline, $PATTERN).value
$data = [RegEx]::Matches($multiline, $PATTERN) | foreach { 
    [PSCustomObject]@{
        FirstCaptureGroup = $_.Groups[1].value
        NamedCaptureGroup = $_.Groups[$groupName].value
    }
}
```

# Filter lines than contain a pattern

single line mode
```powershell
$linesWithBlock = $lines | where {$_ -like "*block*"}
$linesWithBlock = $lines | where {$_ -match "block"}
$linesWithStandaloneWordBlock = $text | where {
    $_ -match '(?<!\w)' + 'block' + '(?!\w)'
}
```

- see Examples

# Find occurrences of a pattern

single line mode
```powershell
$occurrences = $lines | foreach {
    [RegEx]::Match($_, $PATTERN) 
} | where Success | foreach {
    $_.Value
}
```

multi line mode
```powershell
$occurrences = [RegEx]::Matches($multiline, $PATTERN).value
```

- see Examples

# Capture multiple optionally named **data points**

single line mode
```powershell
$data = $lines | foreach {
    [RegEx]::Match($_, $PATTERN) 
} | where Success | foreach { 
    [PSCustomObject]@{
        FirstCaptureGroup = $_.Groups[1].value
        NamedCaptureGroup = $_.Groups[$groupName].value
    }
}
```

multi line mode
```powershell
$data = [RegEx]::Matches($multiline, $PATTERN) | foreach { 
    [PSCustomObject]@{
        FirstCaptureGroup = $_.Groups[1].value
        NamedCaptureGroup = $_.Groups[$groupName].value
    }
}
```

# Performance

- Speed up data extraction of plain text

# Examples

![RegEx - Use Regular Expressions to search, extract and manipulate text in a specified pattern > Quick Reference](./RegEx.md#Quick%20Reference)

Read example file
```powershell
$helpFile = "$env:SystemRoot\System32\WindowsPowerShell\v1.0\en-US\about_Calculated_Properties.help.txt"
$lines = Get-Content -Path $helpFile
$multiline = (Get-Content -Path $helpFile) -join "`n"
$multiline = (Get-Content -Path $helpFile -Raw) -replace [Environment]::NewLine, "`n"
```

Example: Get paragraph after a standalone Short or long description "heading"
```powershell
# line example          Short·description`n`nCAPTURE
$PATTERN = '(?m)' + '(?<=^\w+ description\n\n)' + '(.+\n)+'
[RegEx]::Matches($multiline, $PATTERN).value
```

Example: Get table column with name, definition, and parameter count of aliases
```powershell
# line example        ···clear···Clear-Host··0··
$PATTERN = '(?m)' + '^\s*(\w+)\s+' + '(?<Definition>\w+-\w+)' + '\s+(?<ParameterCount>\d+)' + '\s*$'
[RegEx]::Matches($multiline, $PATTERN) | foreach { 
    [PSCustomObject]@{
        Name = $_.Groups[1].value
        Definition = $_.Groups["Definition"].value
        ParameterCount = $_.Groups["ParameterCount"].value
    }
}
```

---
Sources:
- 2023-03-23: [about Calculated Properties - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-5.1)
- 2023-03-23: [Where-Object (Microsoft.PowerShell.Core) - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-5.1)

Related:
[RegEx - Use Regular Expressions to search, extract and manipulate text in a specified pattern](./RegEx.md)

Tags:
[Handle data - Handle, Import, Export, Filter and RegEx query objects in PowerShell](./powershell/data/index.md)
Document conversion