---
date: "2025-03-22T20:50:41.294+01:00"
title: "Convert hexadecimal and decimal numbers in powershell"
description: "-"
dg-publish: true
dg-folder: powershell/data
---
Convert decimal to hexadecimal
```run-powershell
525328 | foreach { '0x{0:X8}' -f $_ }
'0x{0:X8}' -f 525328
```

Convert hexadecimal to decimal
```run-powershell
0x10
```


---
Sources:

Related:

Tags:
[Handle data - Handle, Import, Export, Filter and RegEx query objects in PowerShell](./index.md)