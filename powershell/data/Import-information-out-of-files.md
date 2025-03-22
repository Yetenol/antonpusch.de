---
date: "2025-03-22T18:11:29.580+01:00"
title: "Import information out of files"
description: "-"
dg-publish: true
dg-folder: powershell/data
---

# .NET formatted file

CLI aka Common Language Infrastructure is an _XML_-based representation of an object or objects and stored in a file. When importing, the .Net object structure is preserved 
```powershell
$object = Import-Clixml -Path ".\example.xml"
```

List the **data types** of an object
```powershell
$object | Get-Member | select -ExpandProperty TypeName -Unique
```

List the **members** of an object
```powershell
$object | Get-Member
```

**Count** the elements of the object
```powershell
$object.Count
```

# Plain text file

Import **all** lines from a plaintext file
```powershell
$lines = Get-Content -Path ".\example.txt"
```

Import only a specific line or **range of lines** from a plaintext file: 
```powershell
$line26      = (Get-Content -Path ".\example.txt")[25]
$line23til26 = (Get-Content -Path ".\example.txt")[22..25]
```

- `-TotalCount` speeds up the commands by only loading the first 26 lines.
```powershell
$line26      = (Get-Content -Path ".\example.txt" -TotalCount 26)[25]
$line23til26 = (Get-Content -Path ".\example.txt" -TotalCount 26)[22..25]
```

Count the number of lines:
```powershell
$lines.Count
```

# Import data out of plaintext files

![RegEx Input Parsing - Import data out of plaintext using regular expressions > Overview](../../content/RegEx-Input-Parsing.md#Overview)


---
Sources:

Related:

Tags:
[Handle PowerShell data - Handle, Import, Export, Filter and RegEx query objects](./index.md)