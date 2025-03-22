---
date: "2025-03-22T19:35:52.560+01:00"
title: "PowerShell"
description: "A command-line shell and scripting language to manage Windows system and automate administrative tasks"
dg-publish: true
permalink: powershell
dg-folder: powershell
dg-filename: index
---
PowerShell is a command-line shell and scripting language developed by Microsoft for Windows, designed to provide a powerful and flexible interface for managing Windows systems and automating administrative tasks.


 PowerShell Essentials

```powershell
Get-Command -Noun Process*
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
$PSDefaultParameterValues['Set-Content:Encoding'] = 'utf8'
$CONFIG = [PSCustomObject]@{
    SourcePath       = "E:\Data\Analytics\SourceData"
    LogFile          = "C:\scripts\DataExport.log"
    MaxLogLines      = 1000
}
```

[Handle PowerShell data - Handle, Import, Export, Filter and RegEx query objects](./data/index.md)

```powershell
Export-Csv -Delimiter "," -NoTypeInformation -Path "spreadsheet.csv"
Export-Clixml -Path "lossless.xml"
Read-Host -AsSecureString | ConvertFrom-SecureString > "encrypted.txt"
[RegEx]::Match((Get-Date), '(\d+):(?<name>\d+)') | foreach { [PSCustomObject]@{
    FirstCaptureGroup = $_.Groups[1].value
    NamedCaptureGroup = $_.Groups["name"].value
}}
```

 [Operate on file system - Use paths, get meta data, link, download, and encrypt files and folders](./filesystem/index.md)




- [Known folders - Access the recycle bin, desktop, downloads folder](../windows/known-folders/index.md)
- [Learn and Troubleshoot Powershell  - Discover commands, and access documentation](./Learn-and-Troubleshoot-Powershell-.md)
- [Programm PowerShell - Learn PowerShell's programming paradigms](./develop/index.md)
- [Naming Convention - Name PowerShell functions with one of the predefined verbs](./Naming-Convention.md)
- [Manage schedules tasks](./Manage-schedules-tasks.md)
- Command Prompt Comparison - PowerShell vs CMD
- [Bash Equivalents - Replace code from Linux Bash with PowerShell equivalents](./Bash-Equivalents.md)
- Bash Comparison - Powershell Core vs Bash

[Programming Languages - Communicate instructions between humans and computers](../Programming-Languages.md)