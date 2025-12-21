---
date: "2025-07-17T08:13:58.241+02:00"
title: "Handle data"
description: "Handle, Import, Export, Filter and RegEx query objects in PowerShell"
dg-publish: true
dg-folder: powershell/data
dg-filename: index
---

# Bundle variables

Bundle configuration variables as the start of a script
```powershell
$CONFIG = [PSCustomObject]@{
    SourcePath       = "E:\Data\Analytics\SourceData"
    LogFile          = "C:\scripts\DataExport.log"
    MaxLogLines      = 1000
}
```

Create strongly typed variables
```powershell
class Metrics {
    [bool] $Success
    [DateTime] $Timestamp
    [int] $Count
}
$metrics = [Metrics]::new()
$metrics.Timestamp = [DateTime]::Now
```

# RegEx - Extract data from stdout string

For example, capture cell values from robocopy

```
------------------------------------------------------------------------------

                Total     Copied   Skipped  Mismatch    FAILED    Extras
    Dirs :         50         50         9         0         1         0
   Files :       4263       4258         5         0         0         0
   Bytes : 1290292538 1290018965    273573         0         0         0
   Times :    0:06:50    0:00:40                       0:00:00   0:00:05
```

```powershell
$summaryPattern = @(
    '^\s*Dirs\s*:\s*(?<dirs_total>\d+)\s+(?<dirs_copied>\d+)\s+(?<dirs_skipped>\d+)\s+(?<dirs_mismatch>\d+)\s+(?<dirs_failed>\d+)\s+(?<dirs_extras>\d+)\s*$'
    '^\s*Files\s*:\s*(?<files_total>\d+)\s+(?<files_copied>\d+)\s+(?<files_skipped>\d+)\s+(?<files_mismatch>\d+)\s+(?<files_failed>\d+)\s+(?<files_extras>\d+)\s*$'
    '^\s*Bytes\s*:\s*(?<bytes_total>\d+)\s+(?<bytes_copied>\d+)\s+(?<bytes_skipped>\d+)\s+(?<bytes_mismatch>\d+)\s+(?<bytes_failed>\d+)\s+(?<bytes_extras>\d+)\s*$'
) -join '\n'
$stats = [RegEx]::Match($robocopyOutput -join "`n", $summaryPattern, [System.Text.RegularExpressions.RegexOptions]::Multiline).Groups
[PSCustomObject]@{
    FilesCopied     = $stats["files_copied"].Value
    BytesTransfered = $stats["bytes_copied"].Value
    NumFailures     = [int]::Parse($stats["dirs_failed"].Value) + [int]::Parse($stats["files_failed"].Value)
}
```

- [RegEx Input Parsing - Import data out of plaintext using regular expressions](../../RegEx-Input-Parsing.md)

# CSV, XML - Export structured data

Export **lossless** .NET object
```powershell
h | Export-Clixml -Path "lossless.xml"
```

Export to Excel spreadsheet
```powershell
h | Export-Csv -Delimiter "," -NoTypeInformation -Path "spreadsheet.csv"
```

- [Export to files like plaintext, CSV tables, JSON object, or encrypted binaries](../../Export-to-files-like-plaintext-CSV-tables-JSON-object-or-encrypted-binaries.md)

# DPAPI - Encrypt passwords for same user on same machine

Store password as encrypted string in a file
- Uses [Windows Data Protection API (DPAPI)](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.5), so that only the same user on the same machine can decrypt it. 
```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
$passwordFile = "C:\scripts\encryptedPassword.dat"
$securedPassword = Read-Host "Enter password" -AsSecureString
$securedPassword | ConvertFrom-SecureString > $passwordFile
```

Decrypt password file and use it in a credential
```powershell
$username = "dataexport"
$passwordFile = "C:\scripts\encryptedPassword.dat"
$securedPassword = Get-Content $passwordFile | ConvertTo-SecureString
$credential = New-Object System.Management.Automation.PSCredential(
    $username, $securedPassword)
```

# Other topics

- [Import information out of files](./Import-information-out-of-files.md)
- [Properties - Inspect, filter, select, enrich, and sort objects](./Properties.md)
- [Encryption - Handle sensitive input](./Encryption.md)
- [Time and Dates - Handle temporal data like day of week, clock time, or first day of month](./Time-and-Dates.md)
- [Containers - Collect multiple items in containers like arrays or dictionaries](./Containers.md)
- [Convert hexadecimal and decimal numbers in powershell](./Convert-hexadecimal-and-decimal-numbers-in-powershell.md)
