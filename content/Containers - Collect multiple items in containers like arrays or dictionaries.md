---
dg-publish: true
---

# Overview

- `[Object[]]`, `[Array]` **List** of values
- `[PSCustomObject]` **Custom entity** of members and properties
- `[Hashtable]` **Dictionary** of key-value pairs
- `[Collections.Specialized.OrderedDictionary]` **Ordered dictionary** of key-value pairs 

Create containers
```powershell
[Int32[]] $numberArray = 0, 1, 2, 4, 7
[String[]] $wordArray = @(
    'I'
    'am'
    "here"
)
```

```powershell
[PSCustomObject] 
$customObject = [PSCustomObject] @{
    Name = "Karl"
    ID = 45
}
```

```powershell
[Hashtable] 
$hashtable = @{
    Name = "Karl"
    ID = 45
}
```

```powershell
[Collections.Specialized.OrderedDictionary] 
$orderedMap = [ordered]@{
    FirstValue = "Karl"
    SecondValue = 45
}
```

# Containers

## Array
- `[Object[]]`, `[Array]` **List** of values

Create an array
```powershell
[Int32[]] $numbers = @(0..2; 4; 7)
[Int32[]] $numbers = 0, 1, 2, 4, 7
[Int32[]] $numbers = 0..2 + 4 + 7
[String[]] $words = @(
    'I'
    'am'
    "here"
)
```

Iterate over it
```powershell
$numbers | foreach {
    $_
}
```

## Custom object
- `[PSCustomObject]` Custom entity of members and properties

Create a custom object
```powershell
[PSCustomObject] $object = [PSCustomObject] @{
    Name = "Karl"
    ID = 45
}
```

Access its properties
```powershell
$object.ID
```

Iterate over it
```powershell
$object.PSObject.Properties | foreach {
    $_.Name + "=" + $_.Value
}
```

## Dictionary
- `[Hashtable]` Dictionary of key-value pairs

Create a hashtable
```powershell
[Hashtable] $hashtable = @{
    Name = "Karl"
    ID = 45
}
```

Access its properties
```powershell
$hashtable.ID
```

Iterate over it
```powershell
$orderedMap.Keys
$orderedMap.Values
$hashtable.GetEnumerator() | foreach {
    $_.Key + "=" + $_.Value
}
```

## Ordered dictionary
- `[Collections.Specialized.OrderedDictionary]` Ordered dictionary of key-value pairs 

Create a ordered dictionary
```powershell
[Collections.Specialized.OrderedDictionary] $orderedMap = [ordered]@{
    FirstValue = 12
    SecondValue = 45
}
```

Access its properties
```powershell
$orderedMap.FirstValue
$orderedMap[0]
```

Iterate over it
```powershell
$orderedMap.Keys
$orderedMap.Values
$hashtable.GetEnumerator() | foreach {
    $_.Key + "=" + $_.Value
}
```

---

Sources:
- 2022-12-17: [PowerShell Hash Table vs. PSCustomObject- Deep Dive & Comparison - Jeff Brown Tech](https://jeffbrown.tech/powershell-hash-table-pscustomobject/)
- 2023-03-03: [dictionary - Looping through a hash, or using an array in PowerShell - Stack Overflow](https://stackoverflow.com/questions/9015138/looping-through-a-hash-or-using-an-array-in-powershell)
- 2023-03-23: [about Arrays - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7.3)
- 2023-03-23: [PowerShell One-Liners: Collections, Hashtables, Arrays and Strings - Simple Talk](https://www.red-gate.com/simple-talk/sysadmin/powershell/powershell-one-liners-collections-hashtables-arrays-and-strings/)

Related:

Tags:
[Objects - Handle, Import, Export, Filter and RegEx query objects](./Objects%20-%20Handle,%20Import,%20Export,%20Filter%20and%20RegEx%20query%20objects.md)
