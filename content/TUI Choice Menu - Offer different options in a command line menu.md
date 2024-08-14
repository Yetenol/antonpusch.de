---  
dg-publish: true  
---  
  
# Ask a question once / until answered  
  
```powershell  
do {  
  $Choice = Read-Host -Prompt "=== Select from: ===`n0 blue`ny yellow`n"  
  switch ($Choice) {  
    0 {  
      Write-Host -Object "Painting in blue"  
      break  
    }   
    "y" {  
      Write-Host -Object "Painting in yellow"  
      return  
    }  
    default {  
      $Choice = $null  
      Write-Host -Object "=== Invalid choice! ==="  
      break  
    }  
  }  
} while ($Choice -eq $null)  
```  
  
# Ask a question repeatedly until canceled  
  
```powershell  
while ($true) {  
  $Choice = Read-Host -Prompt "=== Select from: ===`n0  Sleep`n9+ Shutdown in _s`nq  Quit`n"  
  $n = -1 # Choice parsed to number  
  switch ($Choice) {  
    0 {  
      Write-Host -Object "Falling asleep"  
      break  
    }   
    {<#isNumber#>[double]::TryParse($_,[ref]$n) -and <# >8 #>($n -gt 8)} {  
      Write-Host -Object @("Shutdown in", [math]::floor($_), "seconds")  
      break  
    }  
    "q" {  
      Write-Host -Object "=== Quit ==="  
      return  
    }  
    default {  
      $Choice = $null  
      Write-Host -Object "=== Invalid choice! ==="  
      break  
    }  
  }  
}  
```  
  
  
---  
  
Sources:  
  
Related:  
  
Tags:  
[Programm PowerShell - Learn PowerShell's programming paradigms](./Programm%20PowerShell%20-%20Learn%20PowerShell's%20programming%20paradigms.md)  
