---
date: "2025-07-17T08:13:58.706+02:00"
title: "Robocopy"
description: "Mirror directory with Robust File Copy for Windows"
dg-publish: true
dg-folder: powershell/filesystem
---
```powershell
$robocopyParams = @(
    $CONFIG.SourcePath, $CONFIG.DestinationPath 
    "/MIR", "/XJ", "/R:3", "/W:1", "/MT:8" # Mirror changes, purge orphans, retry thrice on failure, run on 8 threads
    "/BYTES", "/NJH", "/NFL", "/NDL", "/NP", "/NC"  # Show sizes in bytes, minimize logging
    "/TEE", "/UNILOG+:$($CONFIG.LogFile)" # Output to stdout and log file (in utf16)
)
if ($WhatIf) { $robocopyParams += "/L" } # Only list files without performing file operations
robocopy @robocopyParams
```

---
Sources:

Related:
- [Handle data - Handle, Import, Export, Filter and RegEx query objects in PowerShell](../data/index.md)

Tags:
[PowerShell - A command-line shell and scripting language to manage Windows system and automate administrative tasks](../index.md)