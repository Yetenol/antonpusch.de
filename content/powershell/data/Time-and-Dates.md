---
date: "2025-07-17T08:13:58.893+02:00"
title: "Time and Dates"
description: "Handle temporal data like day of week, clock time, or first day of month"
dg-publish: true
dg-folder: powershell/data
---

# Overview

- `[DateTime]` Timestamp as date and time   
  `Date`, `Day`, `DayOfWeek`, `DayOfYear`, `Hour`, `Kind`, `Millisecond`, `Minute`, `Month`, `Second`, `Ticks`, `TimeOfDay`, `Year`, `DateTime`

- `[DateTimeOffset]` Time interval contains    
  `Date`, `DateTime`, `Day`, `DayOfWeek`, `DayOfYear`, `Hour`, `LocalDateTime`, `Millisecond`, `Minute`, `Month`, `Offset`, `Second`, `Ticks`, `TimeOfDay`, `UtcDateTime`, `UtcTicks`, `Year`

Get **current** timestamp    
```powershell
[DateTime] $currentTimestamp1 = Get-Date
[DateTime] $currentTimestamp2 = [DateTime]::Now
[DateTime] $currentUtcTimestamp = [DateTime]::UtcNow
[Int64] $unixMillis = [DateTimeOffset]::Now.ToUnixTimeMilliseconds()
[Int64] $unixSeconds = [DateTimeOffset]::Now.ToUnixTimeSeconds()
```

Get **specific** timestamp    
```powershell
[DateTime] $nowNewYearsEve = Get-Date -Year 1999 -Month 12 -Day 31
[DateTime] $midnightNewYearsEve = [DateTime]"1999-12-31" 
[DateTime] $todayQuarterToTwelve = [DateTime]"23:45:33" 
[DateTime] $13ofJanuary2007 = [DateTime]"1.13.07 12:30"
```

Get **relative** timestamp    
```powershell
[DateTime] $lastMidnight = [DateTime]::Now - [DateTime]::Now.TimeOfDay
[DateTime] $yesterday = [DateTime]::Now.AddDays(-1)
[DateTime] $firstThisMonth = Get-Date -Date $lastMidnight -Day 1
```

# Formatted timestamps

Import **Unix Milliseconds** timestamp    
```powershell
[DateTime] $importUnixMillis = 1673978762521 | foreach {
    [DateTimeOffset]::FromUnixTimeSeconds($_).DateTime
}
```

Import **Unix Seconds** timestamp    
```powershell
[DateTime] $importUnixSeconds = 1674064339 | foreach {
    [DateTimeOffset]::FromUnixTimeSeconds($_).DateTime
}
```

Import timestamp using **current culture**
```powershell
[DateTime] $date = "13.04.2022" | foreach { 
    [DateTime]::Parse($_, [CultureInfo]::CurrentCulture)
}
```

Import timestamp using a **specific culture**
```powershell
$germanCulture = [cultureinfo]::GetCultureInfo('de-DE')
[DateTime] $date = "13.04.2022" | foreach { 
    [DateTime]::Parse($_, $germanCulture)
}
```

Import timestamp using a **specific format**    
```powershell
$dateFormat = "yyyyMMdd"
[DateTime] $date = "20220413" | foreach {
    [DateTime]::ParseExact($_, $dateFormat, [CultureInfo]::InvariantCulture)
}
```


---
Sources:
- 2023-01-17: [Get-Date (Microsoft.PowerShell.Utility) - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.3)

Related:

Tags:
[Handle data - Handle, Import, Export, Filter and RegEx query objects in PowerShell](./index.md)
