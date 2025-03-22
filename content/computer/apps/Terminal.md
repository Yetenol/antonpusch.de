---
date: "2025-03-22T23:45:55.048+01:00"
title: "Terminal"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 9n0dx20hk701
winget-id: Microsoft.WindowsTerminal
priority: 1
categories:
  - Development
synopsis: The Windows Terminal is a modern, fast, efficient, powerful, and productive terminal application for users of command-line tools and shells like Command Prompt, PowerShell, and WSL. Its main features include multiple tabs, panes, Unicode and UTF-8 character support, a GPU accelerated text rendering engine, and custom themes, styles, and configurations.
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

# Cloud synchronization

> [!info]- Replace local settings with synchronized cloud settings
> ```powershell
> Invoke-Command {
> $cloudFolder = "D:\PlutosCloud\Config\Terminal"
> $localFolder = "$env:LocalAppData\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState"
> $syncItems = @(
>     'settings.json'
> )
> 
> if (-not ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] "Administrator")) {
>  throw "Administrator privilege required to run this script"
> }
> 
> # Replace local files with references to synchronized cloud files
> $syncItems | foreach {
>     New-Item -ItemType SymbolicLink -Path "$localFolder\$_" -Target "$cloudFolder\$_" -Force
> }
> 
> # Keep all cloud files that can be pointed to always available
> Set-Location $cloudFolder -ErrorAction Stop
> @(
>     Get-Item $syncItems
>     Get-Item $syncItems | where PSIsContainer | Get-ChildItem -Recurse
> ) | foreach { $_.Attributes = $_.Attributes -bor 0x080000 }
> }
> ```

Or setup manually

Open `Settings`

Open `Startup`
- Default terminal application: **Windows Terminal**
- Launch mode: **Maximized focus**
- New instance behavior: **Attach to the most recently used window on this desktop**
- Save changes

Open `Appearance`
- Show acrylic in tab row: **Yes**
- Save changes

Open `Actions`
- Delete **Paste** using `Ctrl + V`
- Add **Toggle focus mode** using `F10`
- Save changes

Open `Profiles > Default > Appearance`
- Font size: **10** # Text
- Background opacity: **70%**
- Enable acrylic: **Yes**
- Save changes

---
Sources:

Related:

```dynamic-embed
[[List related notes]]
```

Tags:
