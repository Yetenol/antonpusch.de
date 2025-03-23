---
date: "2025-03-23T11:38:32.829+01:00"
title: "PowerShell"
description: "A command-line shell and scripting language to manage Windows system and automate administrative tasks"
dg-publish: true
permalink: powershell
dg-folder: powershell
dg-filename: index
---
PowerShell is a command-line shell and scripting language developed by Microsoft for Windows, designed to provide a powerful and flexible interface for managing Windows systems and automating administrative tasks.


 [Essentials - Access documentation, log data, handle errors in PowerShell](./Essentials.md)

```powershell
Get-Command -Noun Process*
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
$PSDefaultParameterValues['Set-Content:Encoding'] = 'utf8'
$CONFIG = [PSCustomObject]@{
    LogFile          = "C:\scripts\DataExport.log"
    MaxLogLines      = 1000
}
```

[Handle data - Handle, Import, Export, Filter and RegEx query objects in PowerShell](./data/index.md)

```powershell
Export-Csv -Delimiter "," -NoTypeInformation -Path "spreadsheet.csv"
Export-Clixml -Path "lossless.xml"
Read-Host -AsSecureString | ConvertFrom-SecureString > "encrypted.txt"
[RegEx]::Match((Get-Date), '(\d+):(?<name>\d+)') | foreach { [PSCustomObject]@{
    FirstCaptureGroup = $_.Groups[1].value
    NamedCaptureGroup = $_.Groups["name"].value
}}
```

 [File system operations - Use paths, get meta data, link, download, and encrypt files and folders](./filesystem/index.md)

```powershell
$ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath("fake.txt")
New-WinSCPSession -SessionOption $sessionOptions
$item.Attributes = $item.Attributes -bxor [IO.FileAttributes]::Hidden }
[Environment]::SetEnvironmentVariable('PATH', "$env:Path$folder;", 'User')
```

[Known folders - Access the recycle bin, desktop, downloads folder](../windows/known-folders/index.md)

```powershell
[Environment]::GetFolderPath("MyPictures")
$env:Downloads = (New-Object -ComObject Shell.Application).NameSpace('shell:::{374DE290-123F-4565-9164-39C4925E467B}').Self.Path
```

Other topics

- [Learn and Troubleshoot Powershell  - Discover commands, and access documentation](./Learn-and-Troubleshoot-Powershell-.md)
- [Programm PowerShell - Learn PowerShell's programming paradigms](./develop/index.md)
- [Naming Convention - Name PowerShell functions with one of the predefined verbs](./Naming-Convention.md)
- [Manage schedules tasks](./Manage-schedules-tasks.md)
- Command Prompt Comparison - PowerShell vs CMD
- [Bash Equivalents - Replace code from Linux Bash with PowerShell equivalents](./Bash-Equivalents.md)
- Bash Comparison - Powershell Core vs Bash

Note preview

![figure powershell collection.svg](../figure-powershell-collection.svg)


[Example listing - Example code block for note preview](./Example-listing.md)