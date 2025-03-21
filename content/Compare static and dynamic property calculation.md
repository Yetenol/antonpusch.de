---
publish: true
---


Add static values
```powershell
$EXAMPLE_PATH = "$env:TEMP\example.txt"

New-Item -Path $EXAMPLE_PATH -Force | Out-Null
$file = Get-Item -Path $EXAMPLE_PATH
Write-Host "Does file exist after creation:" $file.Exists

Remove-Item -Path $EXAMPLE_PATH
Write-Host "Does file exist after deletion:" $file.Exists

$file.Refresh()
Write-Host "Does file exist after refresh:" $file.Exists
```


Add dynamic values
```powershell
$EXAMPLE_PATH = "$env:TEMP\example.txt"
$TEST_EXISTANCE = { Test-Path -Path $this.FullName }

New-Item -Path $EXAMPLE_PATH -Force | Out-Null
$file = Get-Item -Path $EXAMPLE_PATH
$file | Add-Member -MemberType ScriptProperty -Name TestExistance -Value $TEST_EXISTANCE
Write-Host "Does file exist after creation:" $file.TestExistance

Remove-Item -Path $EXAMPLE_PATH
Write-Host "Does file exist after deletion:" $file.TestExistance

Write-Host "Does file exist after refresh:" $file.TestExistance
```

Compare performance
```powershell
$files = Get-ChildItem -Path $env:SystemRoot
$TEST_EXISTANCE = { Test-Path -Path $this.FullName }
$files | Add-Member -MemberType AliasProperty -Name StaticExistance -Value Exists
$files | Add-Member -MemberType ScriptProperty -Name DynamicExistance -Value $TEST_EXISTANCE

"StaticExistance", "DynamicExistance" | ForEach-Object {
    $executionTime = Measure-Command { $files."$_" }
    [PSCustomObject]@{
        AccessTest = $_
        Ticks = $executionTime.Ticks
        Milliseconds = $executionTime.Milliseconds
    }
}
```

```
AccessTest        Ticks Milliseconds
----------        ----- ------------
StaticExistance   15388            1
DynamicExistance 371345           37
```


---
Sources:

Related:

Tags:
[Properties - Inspect, filter, select, enrich, and sort objects](./Properties%20-%20Inspect,%20filter,%20select,%20enrich,%20and%20sort%20objects.md)