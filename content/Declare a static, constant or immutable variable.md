---
dg-publish: true
---

# Constant variables

Declare a **immutable** variable
```powershell
New-Variable TEST -Option ReadOnly -Force -Value 100
```
- `.Option ReadOnly`: Cannot be changed, except by using the Force parameter.
- `-Force`: Override previous definitions including debugging
- Can be deleted using `Remove-Variable TEST -Force`

Declare a **baked** variable
```powershell
New-Variable TEST -Option Constant -Force -Value 100
```
- `-Option Constant`: The variable can neither be edited nor removed forever
- `-Force`: Override previous definitions including debugging
- complicates debugging

# Static function variables

Static variables have a lifetime that lasts until the end of the program, instead of loosing their value when execution leaves their scope. This is useful for sharing information like a counter when repeatedly calling a function.

PowerShell doesn't natively provide a way[^1] to create static variables, but we can store the variable globally and restrict access to only the function that declared it. Since the function is stored globally, the name cannot be used elsewhere.

Variables created within functions or scripts do not effect the parent scope, unless you explicitly specify the scope[^2] using *Scope Modifiers* or a *Scope* parameter. 

Declare and initialize a **static** variable
```powershell
function Get-StaticVariable {
    if (-not (Test-Path variable:staticVariable)) {
        New-Variable -Name staticVariable -Value $initialValue -Scope Script -Visibility Private
    }
    return $script:staticVariable
}
```
- the variable is stored in the script's global scope but cannot be accessed there

Mutate a **static** variable
```powershell
function Get-IncrementedStaticCounter {
    if (-not (Test-Path variable:staticCounter)) {
        New-Variable -Name staticCounter -Value $initialValue -Scope Script -Visibility Private
    }
    $script:staticCounter++
    return $script:staticCounter
}
```

---
Sources:
- 2023-03-21: [Set-Variable (Microsoft.PowerShell.Utility) - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-5.1&WT.mc_id=ps-gethelp#-option)
- 2023-03-21: [Does PowerShell support constants? - Stack Overflow](https://stackoverflow.com/questions/2608215/does-powershell-support-constants)
- 2023-03-21 [PowerShell Variable Scope Guide: Using Scope in Scripts and Modules](https://www.varonis.com/blog/powershell-variable-scope)
- 2023-03-21: [about Scopes - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-5.1#powershell-scopes)

[^1]: 2023-03-21: [Static variables - Variables - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/scripting/lang-spec/chapter-05?view=powershell-7.3#521-static-variables)

[^2]: 2023-03-21: [Parent and Child Scopes - about Scopes - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-5.1#parent-and-child-scopes)

Related:
[Data Types - Ensure correct content and members with strongly type variables like booleans, hashtables, or dictionaries](./Data%20Types%20-%20Ensure%20correct%20content%20and%20members%20with%20strongly%20type%20variables%20like%20booleans,%20hashtables,%20or%20dictionaries.md)

Tags:
[Programm PowerShell - Learn PowerShell's programming paradigms](./Programm%20PowerShell%20-%20Learn%20PowerShell's%20programming%20paradigms.md)