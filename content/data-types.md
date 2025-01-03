---
title: "Data Types - Ensure correct content and members with strongly type variables like booleans, hashtables, or dictionaries"
date: "2024-12-20T00:00:00.000+01:00"
dg-publish: true
priority: 5
dg-show-toc: true
---

# Analyze an existing object

List **data types** of an object

```powershell
$object | Get-Member | select TypeName -Unique
```

- abbriviate `$object | gm | select Typename -Unique`

List **members** of an object

```powershell
$object | Get-Member
```

# Numbers

## Integers

- Convert automatically to larger types
- `[Int32]`, `[Int]` 32-bit signed integer
- `[Int64]`, `[Long]` 64-bit signed integer

```powershell
[Int] $smallNumber = 2147483647
[Long] $highNumber = 9223372036854775807
```

## Decimal numbers

- `[Single]`, `[Float]` Single-precision 32-bit floating point number    
- `[Double]` Double-precision 64-bit floating point number

```powershell
[Float] $lowPrecision = 15.95459
[Double] $highPrecision = 15.954589770191
```

## Boolean

- `[Boolean]` Logical value

```powershell
[Boolean] $enabled = $True 
[Bool] $disabled = $False
```

# Text

- `[Char]` **Single** Unicode 16-bit **character**    
- `[String]` Fixed-length string of Unicode characters
 Char (A Unicode 16-bit character)

```powershell
[Char] $letter = "a"
[String] $evaluatedString = "Hello $env:Username"
[String] $unevaluatedString = 'Raw <>|$&%\Text'
[String] $combinedString1 = ("Found " + $_.Name + "!")
[String] $combinedString2 = ("Found $($_.Name)!")
[String] $combinedString3 = [String]@(
    "Found ",
    $_.Name,
    "!"
)
[String] $multilineString = @”  
First-line  
Second line  
Third line  
“@
```

# Date and time

![Time and Dates - Handle temporal data like day of week, clock time, or first day of month > Overview](./time-and-dates.md#Overview)

# Collect multiple items in containers like arrays or dictionaries

![Containers - Collect multiple items in containers like arrays or dictionaries > Overview](./containers.md#Overview)


---
Sources:
- 2023-01-18: [Types - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/scripting/lang-spec/chapter-04?view=powershell-7.3)
- 2022-12-17: [Difference between single quote (‘) and double quote (“) in PowerShell](https://www.tutorialspoint.com/difference-between-single-quote-and-double-quote-in-powershell)
- 2022-12-17: [PowerShell Multiline String - Working of multiline string using her string](https://www.educba.com/powershell-multiline-string/)

Related:
[How types make hard problems easy](How%20types%20make%20hard%20problems%20easy.md)

Tags:
