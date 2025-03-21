---
publish: true
priority: 3
---

Example content
```powershell
$c = Get-Command
```

# Visualize

Split output into console-sized **pages**
```powershell
$c | more
```

Launch table **GUI**
```powershell
$c | Out-GridView
```

Show plaintext **table**  
```powershell
$c | Format-Table
```

# Empty file

Set 0 KB or create **empty file**

```powershell
Out-File -FilePath $file
```

- abbreviate `Out-File $file`

# File export

Export **lossless** .NET object
```powershell
$c | Export-Clixml -Path "object.xml"
```

Export **spreadsheet table** separated by commas for programs like Excel.
```powershell
$c | Export-Csv -Delimiter "," -NoTypeInformation -Path ".\text.csv"
```

Export **plaintext table** separated by spaces.
```powershell
$c | Format-Table -AutoSize -Wrap |
	Out-File -FilePath ".\text.txt"
```

Export **plaintext list** with each property on a new line.
```powershell
$c | Format-List |
	Out-File -FilePath ".\text.txt"
```

Export **encrypted standard string**  
```powershell
$c | ConvertTo-SecureString -AsPlainText -Force |
	ConvertFrom-SecureString |
	Out-File -FilePath ".\key.bin"
```


---
Sources:

Related:

Tags:
[Handle PowerShell data - Handle, Import, Export, Filter and RegEx query objects](./Handle%20PowerShell%20data%20-%20Handle,%20Import,%20Export,%20Filter%20and%20RegEx%20query%20objects.md)
Document conversion