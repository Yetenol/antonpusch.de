---
date: "2025-07-17T08:13:58.544+02:00"
title: "Parameters"
description: "Autocomplete or validate parameters for functions and scripts"
dg-publish: true
dg-folder: powershell/develop
---

Erhalte den nächsten Index als dreistellige Zahl

Get the next index as a three-digit number

Parameters are defined at the first non-comment line within a script of function.
```powershell
param (
    $Noun,
    $Verb
)
```

# Specify data types of parameters

Identify **flag**
- Boolean is _true_ or _false_.
```powershell
param(
    [Switch] $Force
)
```

Identify **specific type**  
```powershell
param (
    [DateTime] $Date
)
```

**Validate** out of predefined options  
- Enables AutoComplete.
```powershell
param (
    [ValidateSet("World", "Galaxy", "Universe")] $Noun
)
```

# Provide default values

Set **default value**  
```powershell
param (
    $Noun = "none"
)
```

Set **default** via command  
```powershell
param (
    $Date = $(Get-Date)
)
```

# Identify optional public properties of parameters

**Require** parameter  
```powershell
param (
    [Parameter(Mandatory,HelpMessage="Enter your name")] $Name
)
```

| Attribute                         | Default | Description                                                                     |
| --------------------------------- | ------- | ------------------------------------------------------------------------------- |
| `Mandatory`                       | false   | Make parameter mandatory and prompt for value when the user does not supply one |
| `ParameterSetName`                |         | Define mutually exclusive parameters                                            |
| `Position`                        |         | Assign positions to parameters and use arguments without parameter names        |
| `ValueFromPipeline`               | false   | Assign pipeline input to a parameter                                            |
| `ValueFromPipelineByPropertyName` |         | Assign a specific property of pipeline input to a parameter                     |
| `ValueFromRemainingArguments`     | false   | Create a ParamArray and assign any unbound argument to a parameter              |
| `DontShow`                        | false   | Hide parameter in IntelliSense and tab completion                               |
| `HelpMessage`                     |         | Provide a help message for mandatory parameters                                 |
| `HelpMessageBaseName`             |         | Name of resource assembly that contains compiled help messages                  |
| `HelpMessageResourceId`           |         | Resource identifier for help message                                            |


---


Sources:
- 2022-11-14: [Designing Professional Parameters - powershell.one](https://powershell.one/powershell-internals/attributes/parameters)
- 2023-03-03: [Parameter Attribute Declaration - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/scripting/developer/cmdlet/parameter-attribute-declaration?view=powershell-7.3)
- 2023-03-23: [function to accept array from pipe](https://social.technet.microsoft.com/Forums/lync/en-US/1327be63-2093-439d-8475-cf571e322efe/function-to-accept-array-from-pipe?forum=winserverpowershell)
- 2023-03-27: [PowerShell Advanced Functions | ScriptRunner](https://www.scriptrunner.com/en/blog/powershell-advanced-functions/)

Related:
[Naming Convention - Name PowerShell functions with one of the predefined verbs](../Naming-Convention.md)

Tags:
[Programm PowerShell - Learn PowerShell's programming paradigms](./index.md)
