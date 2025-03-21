---
publish: true
priority: 2
---

# Group variables

Group configuration
```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
$CONFIG = [PSCustomObject]@{
    SourcePath       = "E:\Data\Analytics\SourceData"
    PrometheusOutput = "$env:ProgramFiles\windows_exporter\textfile_inputs\DataExport.prom"
    MetricsBaseName  = "windows_scheduled_task_data_export"
    LogFile          = "C:\scripts\DataExport.log"
    MaxLogLines      = 1000
}
"Hello World!" >> $CONFIG.LogFile
```

Define typed variables
```powershell
class Metrics {
    [bool] $ConnectionSuccess
    [bool] $SyncSuccess
    [DateTime] $Timestamp
    [int] $UploadsCount
    [int] $RemovalsCount
    [int] $FailuresCount
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

- [RegEx Input Parsing - Import data out of plaintext using regular expressions](./RegEx%20Input%20Parsing%20-%20Import%20data%20out%20of%20plaintext%20using%20regular%20expressions.md)

# CSV, XML - Export structured data

Export **lossless** .NET object
```powershell
$c | Export-Clixml -Path "object.xml"
```

Export to Excel spreadsheet
```powershell
Export-Csv -Delimiter "," -NoTypeInformation -Path ".\text.csv"
```

- [Export to files like plaintext, CSV tables, JSON object, or encrypted binaries](./Export%20to%20files%20like%20plaintext,%20CSV%20tables,%20JSON%20object,%20or%20encrypted%20binaries.md)

# DPAPI - Encrypt passwords for same user on same machine

Store password as encrypted string in a file
- Uses [Windows Data Protection API (DPAPI)](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.5), so that only the same user on the same machine can decrypt it. 
```powershell
$passwordFile = "C:\scripts\encryptedPassword.dat"
$securedPassword = Read-Host "Enter password" -AsSecureString
$securedPassword | ConvertFrom-SecureString | Out-File $passwordFile
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

- [Import information out of files](./Import%20information%20out%20of%20files.md)
- [Properties - Inspect, filter, select, enrich, and sort objects](./Properties%20-%20Inspect,%20filter,%20select,%20enrich,%20and%20sort%20objects.md)
- [Encryption - Handle sensitive input](./Encryption%20-%20Handle%20sensitive%20input.md)
- [Time and Dates - Handle temporal data like day of week, clock time, or first day of month](./Time%20and%20Dates%20-%20Handle%20temporal%20data%20like%20day%20of%20week,%20clock%20time,%20or%20first%20day%20of%20month.md)
- [Containers - Collect multiple items in containers like arrays or dictionaries](./Containers%20-%20Collect%20multiple%20items%20in%20containers%20like%20arrays%20or%20dictionaries.md)
- Convert hexadecimal and decimal numbers in powershell

---
Sources:

Related:
```dynamic-embed
[[List related notes]]
``` 

Tags:
[PowerShell - A command-line shell and scripting language to manage Windows system and automate administrative tasks](./PowerShell%20-%20A%20command-line%20shell%20and%20scripting%20language%20to%20manage%20Windows%20system%20and%20automate%20administrative%20tasks.md)
