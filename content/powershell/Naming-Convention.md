---
date: "2025-07-17T08:13:58.478+02:00"
title: "Naming Convention"
description: "Name PowerShell functions with one of the predefined verbs"
dg-publish: true
dg-folder: powershell
---

# Command

- scripts that are only available in the Windows PowerShell environment
- are _not_ available in other consoles
- e.g. Get-Help
- naming convention: _PREDEFINED\_VERB_-_COMBINATION\_OF\_SPECIFIC\_SINGULAR\_NOUNS_
    - Use Pascal Case (capitalize the first letter of verb and all terms used in the noun)
    - Use one of the predefined verb names provided by PowerShell `Get-Verb` [MS](https://docs.microsoft.com/en-us/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands?view=powershell-7.2)
    - use _Remove_, never use _~~Delete~~_ or _~~Eliminate~~_

## Cmdlet

- pronounced _command-let_
- written in a compiled .NET language

## Function

- written the PowerShell language
