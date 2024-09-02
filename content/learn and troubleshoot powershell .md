---
title: "Learn and Troubleshoot Powershell  - Discover commands, and access documentation"
dg-publish: true
priority: 1
---

**Update help files** using elevated command
```powershell
Update-Help
```

# Discover commands

Discover **all nouns** of PowerShell modules    
```powershell
Get-Command -Module Microsoft.PowerShell* | group Noun | Format-Wide -AutoSize
```

Discover **all commands** about a noun    
```powershell
Get-Command -Noun Web* | foreach { Get-Help $_ } | Format-Table Name, Synopsis
```

Discover **all modules**    
```powershell
Get-Module
```
```powershell
Get-Module -ListAvailable
```

# Access documentation

Example command:
```powershell
$help = Get-Help -Name Invoke-WebRequest
```

Show help **online**    
```powershell
Get-Help -Name Invoke-WebRequest -Online
```
- abbreviate `help Invoke-WebRequest -Online`

Learn **syntax**    
```powershell
$help.syntax
```
- abbreviate `(help Invoke-WebRequest).syntax` or `(Invoke-WebRequest -?).syntax`

Learn **purpose**    
```powershell
$help.Synopsis
```
- abbreviate `(help Invoke-WebRequest).Synopsis` or `(Invoke-WebRequest -?).Synopsis`

Read **description**    
```powershell
$help.description
```
- abbreviate `(help Invoke-WebRequest).description` or `(Invoke-WebRequest -?).description`  

See **examples**    
```powershell
$help.examples
```
- abbreviate `help Invoke-WebRequest -Examples` or `(Invoke-WebRequest -?).examples`  


---
Sources:

Related:
- [Learn about Character Encoding in PowerShell](Learn%20about%20Character%20Encoding%20in%20PowerShell.md)
- [Learn about WMI Cmdlets in PowerShell](Learn%20about%20WMI%20Cmdlets%20in%20PowerShell.md)
- [Learn about WMI in PowerShell](Learn%20about%20WMI%20in%20PowerShell.md)
- [Learn about WSMan Provider in PowerShell](Learn%20about%20WSMan%20Provider%20in%20PowerShell.md)
- [Learn about WS-Management Cmdlets in PowerShell](Learn%20about%20WS-Management%20Cmdlets%20in%20PowerShell.md)
- [Learn about WQL in PowerShell](Learn%20about%20WQL%20in%20PowerShell.md)
- [Learn about Windows RT in PowerShell](Learn%20about%20Windows%20RT%20in%20PowerShell.md)
- [Learn about Wildcards in PowerShell](Learn%20about%20Wildcards%20in%20PowerShell.md)
- [Learn about Windows PowerShell ISE in PowerShell](Learn%20about%20Windows%20PowerShell%20ISE%20in%20PowerShell.md)
- [Learn about Windows Powershell 5.1 in PowerShell](Learn%20about%20Windows%20Powershell%205.1%20in%20PowerShell.md)
- [Learn about While in PowerShell](Learn%20about%20While%20in%20PowerShell.md)
- [Learn about Variable Provider in PowerShell](Learn%20about%20Variable%20Provider%20in%20PowerShell.md)
- [Learn about Using in PowerShell](Learn%20about%20Using%20in%20PowerShell.md)
- [Learn about Variables in PowerShell](Learn%20about%20Variables%20in%20PowerShell.md)
- [Learn about Updatable Help in PowerShell](Learn%20about%20Updatable%20Help%20in%20PowerShell.md)
- [Learn about Try Catch Finally in PowerShell](Learn%20about%20Try%20Catch%20Finally%20in%20PowerShell.md)
- [Learn about Type Operators in PowerShell](Learn%20about%20Type%20Operators%20in%20PowerShell.md)
- [Learn about Types.ps1xml in PowerShell](Learn%20about%20Types.ps1xml%20in%20PowerShell.md)
- [Learn about Type Accelerators in PowerShell](Learn%20about%20Type%20Accelerators%20in%20PowerShell.md)
- [Learn about Trap in PowerShell](Learn%20about%20Trap%20in%20PowerShell.md)
- [Learn about Transactions in PowerShell](Learn%20about%20Transactions%20in%20PowerShell.md)
- [Learn about Throw in PowerShell](Learn%20about%20Throw%20in%20PowerShell.md)
- [Learn about Splatting in PowerShell](Learn%20about%20Splatting%20in%20PowerShell.md)
- [Learn about Tab Expansion in PowerShell](Learn%20about%20Tab%20Expansion%20in%20PowerShell.md)
- [Learn about Signing in PowerShell](Learn%20about%20Signing%20in%20PowerShell.md)
- [Learn about Split in PowerShell](Learn%20about%20Split%20in%20PowerShell.md)
- [Learn about Switch in PowerShell](Learn%20about%20Switch%20in%20PowerShell.md)
- [Learn about Special Characters in PowerShell](Learn%20about%20Special%20Characters%20in%20PowerShell.md)
- [Learn about Simplified Syntax in PowerShell](Learn%20about%20Simplified%20Syntax%20in%20PowerShell.md)
- [Learn about Session Configurations in PowerShell](Learn%20about%20Session%20Configurations%20in%20PowerShell.md)
- [Learn about Session Configuration Files in PowerShell](Learn%20about%20Session%20Configuration%20Files%20in%20PowerShell.md)
- [Learn about Scopes in PowerShell](Learn%20about%20Scopes%20in%20PowerShell.md)
- [Learn about Script Internationalization in PowerShell](Learn%20about%20Script%20Internationalization%20in%20PowerShell.md)
- [Learn about Scripts in PowerShell](Learn%20about%20Scripts%20in%20PowerShell.md)
- [Learn about Script Blocks in PowerShell](Learn%20about%20Script%20Blocks%20in%20PowerShell.md)
- [Learn about Run With PowerShell in PowerShell](Learn%20about%20Run%20With%20PowerShell%20in%20PowerShell.md)
- [Learn about Requires in PowerShell](Learn%20about%20Requires%20in%20PowerShell.md)
- [Learn about Return in PowerShell](Learn%20about%20Return%20in%20PowerShell.md)
- [Learn about Reserved Words in PowerShell](Learn%20about%20Reserved%20Words%20in%20PowerShell.md)
- [Learn about Remote Troubleshooting in PowerShell](Learn%20about%20Remote%20Troubleshooting%20in%20PowerShell.md)
- [Learn about Remote Requirements in PowerShell](Learn%20about%20Remote%20Requirements%20in%20PowerShell.md)
- [Learn about Remote Variables in PowerShell](Learn%20about%20Remote%20Variables%20in%20PowerShell.md)
- [Learn about Remote Jobs in PowerShell](Learn%20about%20Remote%20Jobs%20in%20PowerShell.md)
- [Learn about Remote Output in PowerShell](Learn%20about%20Remote%20Output%20in%20PowerShell.md)
- [Learn about Remote in PowerShell](Learn%20about%20Remote%20in%20PowerShell.md)
- [Learn about Regular Expressions in PowerShell](Learn%20about%20Regular%20Expressions%20in%20PowerShell.md)
- [Learn about Remote Disconnected Sessions in PowerShell](Learn%20about%20Remote%20Disconnected%20Sessions%20in%20PowerShell.md)
- [Learn about Ref in PowerShell](Learn%20about%20Ref%20in%20PowerShell.md)
- [Learn about Redirection in PowerShell](Learn%20about%20Redirection%20in%20PowerShell.md)
- [Learn about Registry Provider in PowerShell](Learn%20about%20Registry%20Provider%20in%20PowerShell.md)
- [Learn about Quoting Rules in PowerShell](Learn%20about%20Quoting%20Rules%20in%20PowerShell.md)
- [Learn about PSSnapins in PowerShell](Learn%20about%20PSSnapins%20in%20PowerShell.md)
- [Learn about PSSession Details in PowerShell](Learn%20about%20PSSession%20Details%20in%20PowerShell.md)
- [Learn about PSModulePath in PowerShell](Learn%20about%20PSModulePath%20in%20PowerShell.md)
- [Learn about PSSessions in PowerShell](Learn%20about%20PSSessions%20in%20PowerShell.md)
- [Learn about PSConsoleHostReadLine in PowerShell](Learn%20about%20PSConsoleHostReadLine%20in%20PowerShell.md)
- [Learn about PSCustomObject in PowerShell](Learn%20about%20PSCustomObject%20in%20PowerShell.md)
- [Learn about Providers in PowerShell](Learn%20about%20Providers%20in%20PowerShell.md)
- [Learn about Properties in PowerShell](Learn%20about%20Properties%20in%20PowerShell.md)
- [Learn about Prompts in PowerShell](Learn%20about%20Prompts%20in%20PowerShell.md)
- [Learn about Profiles in PowerShell](Learn%20about%20Profiles%20in%20PowerShell.md)
- [Learn about Preference Variables in PowerShell](Learn%20about%20Preference%20Variables%20in%20PowerShell.md)
- [Learn about PowerShell Ise exe in PowerShell](Learn%20about%20PowerShell%20Ise%20exe%20in%20PowerShell.md)
- [Learn about Pipelines in PowerShell](Learn%20about%20Pipelines%20in%20PowerShell.md)
- [Learn about PowerShell exe in PowerShell](Learn%20about%20PowerShell%20exe%20in%20PowerShell.md)
- [Learn about Parameters in PowerShell](Learn%20about%20Parameters%20in%20PowerShell.md)
- [Learn about Path Syntax in PowerShell](Learn%20about%20Path%20Syntax%20in%20PowerShell.md)
- [Learn about Parsing in PowerShell](Learn%20about%20Parsing%20in%20PowerShell.md)
- [Learn about Parameter Sets in PowerShell](Learn%20about%20Parameter%20Sets%20in%20PowerShell.md)
- [Learn about Parameters Default Values in PowerShell](Learn%20about%20Parameters%20Default%20Values%20in%20PowerShell.md)
- [Learn about PackageManagement in PowerShell](Learn%20about%20PackageManagement%20in%20PowerShell.md)
- [Learn about Output Streams in PowerShell](Learn%20about%20Output%20Streams%20in%20PowerShell.md)
- [Learn about Operators in PowerShell](Learn%20about%20Operators%20in%20PowerShell.md)
- [Learn about Operator Precedence in PowerShell](Learn%20about%20Operator%20Precedence%20in%20PowerShell.md)
- [Learn about Objects in PowerShell](Learn%20about%20Objects%20in%20PowerShell.md)
- [Learn about Numeric Literals in PowerShell](Learn%20about%20Numeric%20Literals%20in%20PowerShell.md)
- [Learn about Object Creation in PowerShell](Learn%20about%20Object%20Creation%20in%20PowerShell.md)
- [Learn about Modules in PowerShell](Learn%20about%20Modules%20in%20PowerShell.md)
- [Learn about Module Manifests in PowerShell](Learn%20about%20Module%20Manifests%20in%20PowerShell.md)
- [Learn about Methods in PowerShell](Learn%20about%20Methods%20in%20PowerShell.md)
- [Learn about Logical Operators in PowerShell](Learn%20about%20Logical%20Operators%20in%20PowerShell.md)
- [Learn about Member-Access Enumeration in PowerShell](Learn%20about%20Member-Access%20Enumeration%20in%20PowerShell.md)
- [Learn about Logging in PowerShell](Learn%20about%20Logging%20in%20PowerShell.md)
- [Learn about Line Editing in PowerShell](Learn%20about%20Line%20Editing%20in%20PowerShell.md)
- [Learn about Language Keywords in PowerShell](Learn%20about%20Language%20Keywords%20in%20PowerShell.md)
- [Learn about Language Modes in PowerShell](Learn%20about%20Language%20Modes%20in%20PowerShell.md)
- [Learn about Locations in PowerShell](Learn%20about%20Locations%20in%20PowerShell.md)
- [Learn about Join in PowerShell](Learn%20about%20Join%20in%20PowerShell.md)
- [Learn about Job Details in PowerShell](Learn%20about%20Job%20Details%20in%20PowerShell.md)
- [Learn about Intrinsic Members in PowerShell](Learn%20about%20Intrinsic%20Members%20in%20PowerShell.md)
- [Learn about Jobs in PowerShell](Learn%20about%20Jobs%20in%20PowerShell.md)
- [Learn about If in PowerShell](Learn%20about%20If%20in%20PowerShell.md)
- [Learn about History in PowerShell](Learn%20about%20History%20in%20PowerShell.md)
- [Learn about Hidden in PowerShell](Learn%20about%20Hidden%20in%20PowerShell.md)
- [Learn about Help System in PowerShell](Learn%20about%20Help%20System%20in%20PowerShell.md)
- [Learn about Functions in PowerShell](Learn%20about%20Functions%20in%20PowerShell.md)
- [Learn about Hash Tables in PowerShell](Learn%20about%20Hash%20Tables%20in%20PowerShell.md)
- [Learn about Group Policy Settings in PowerShell](Learn%20about%20Group%20Policy%20Settings%20in%20PowerShell.md)
- [Learn about Functions OutputTypeAttribute in PowerShell](Learn%20about%20Functions%20OutputTypeAttribute%20in%20PowerShell.md)
- [Learn about Functions CmdletBindingAttribute in PowerShell](Learn%20about%20Functions%20CmdletBindingAttribute%20in%20PowerShell.md)
- [Learn about Functions Argument Completion in PowerShell](Learn%20about%20Functions%20Argument%20Completion%20in%20PowerShell.md)
- [Learn about Functions Advanced Parameters in PowerShell](Learn%20about%20Functions%20Advanced%20Parameters%20in%20PowerShell.md)
- [Learn about Functions Advanced in PowerShell](Learn%20about%20Functions%20Advanced%20in%20PowerShell.md)
- [Learn about Functions Advanced Methods in PowerShell](Learn%20about%20Functions%20Advanced%20Methods%20in%20PowerShell.md)
- [Learn about Foreach in PowerShell](Learn%20about%20Foreach%20in%20PowerShell.md)
- [Learn about Format.ps1xml in PowerShell](Learn%20about%20Format.ps1xml%20in%20PowerShell.md)
- [Learn about Function Provider in PowerShell](Learn%20about%20Function%20Provider%20in%20PowerShell.md)
- [Learn about FileSystem Provider in PowerShell](Learn%20about%20FileSystem%20Provider%20in%20PowerShell.md)
- [Learn about For in PowerShell](Learn%20about%20For%20in%20PowerShell.md)
- [Learn about Execution Policies in PowerShell](Learn%20about%20Execution%20Policies%20in%20PowerShell.md)
- [Learn about Eventlogs in PowerShell](Learn%20about%20Eventlogs%20in%20PowerShell.md)
- [Learn about Environment Variables in PowerShell](Learn%20about%20Environment%20Variables%20in%20PowerShell.md)
- [Learn about Do in PowerShell](Learn%20about%20Do%20in%20PowerShell.md)
- [Learn about DesiredStateConfiguration in PowerShell](Learn%20about%20DesiredStateConfiguration%20in%20PowerShell.md)
- [Learn about Enum in PowerShell](Learn%20about%20Enum%20in%20PowerShell.md)
- [Learn about Environment Provider in PowerShell](Learn%20about%20Environment%20Provider%20in%20PowerShell.md)
- [Learn about Debuggers in PowerShell](Learn%20about%20Debuggers%20in%20PowerShell.md)
- [Learn about Data Sections in PowerShell](Learn%20about%20Data%20Sections%20in%20PowerShell.md)
- [Learn about Continue in PowerShell](Learn%20about%20Continue%20in%20PowerShell.md)
- [Learn about Core Commands in PowerShell](Learn%20about%20Core%20Commands%20in%20PowerShell.md)
- [Learn about Comparison Operators in PowerShell](Learn%20about%20Comparison%20Operators%20in%20PowerShell.md)
- [Learn about CommonParameters in PowerShell](Learn%20about%20CommonParameters%20in%20PowerShell.md)
- [Learn about Comment Based Help in PowerShell](Learn%20about%20Comment%20Based%20Help%20in%20PowerShell.md)
- [Learn about Certificate Provider in PowerShell](Learn%20about%20Certificate%20Provider%20in%20PowerShell.md)
- [Learn about Command Syntax in PowerShell](Learn%20about%20Command%20Syntax%20in%20PowerShell.md)
- [Learn about Classes in PowerShell](Learn%20about%20Classes%20in%20PowerShell.md)
- [Learn about Command Precedence in PowerShell](Learn%20about%20Command%20Precedence%20in%20PowerShell.md)
- [Learn about CimSession in PowerShell](Learn%20about%20CimSession%20in%20PowerShell.md)
- [Learn about Case-Sensitivity in PowerShell](Learn%20about%20Case-Sensitivity%20in%20PowerShell.md)
- [Learn about Calculated Properties in PowerShell](Learn%20about%20Calculated%20Properties%20in%20PowerShell.md)
- [Learn about Built-in Functions in PowerShell](Learn%20about%20Built-in%20Functions%20in%20PowerShell.md)
- [Learn about Break in PowerShell](Learn%20about%20Break%20in%20PowerShell.md)
- [Learn about Booleans in PowerShell](Learn%20about%20Booleans%20in%20PowerShell.md)
- [Learn about Assignment Operators in PowerShell](Learn%20about%20Assignment%20Operators%20in%20PowerShell.md)
- [Learn about Arithmetic Operators in PowerShell](Learn%20about%20Arithmetic%20Operators%20in%20PowerShell.md)
- [Learn about Arrays in PowerShell](Learn%20about%20Arrays%20in%20PowerShell.md)
- [Learn about Aliases in PowerShell](Learn%20about%20Aliases%20in%20PowerShell.md)
- [Learn about Alias Provider in PowerShell](Learn%20about%20Alias%20Provider%20in%20PowerShell.md)
 

Tags:
[PowerShell - A command-line shell and scripting language to manage Windows system and automate administrative tasks](./powershell.md)