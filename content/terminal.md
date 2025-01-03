---
title: "Terminal"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
microsoft-id: 9n0dx20hk701
winget-id: Microsoft.WindowsTerminal
priority: 1
categories:
  - Development
synopsis: The Windows Terminal is a modern, fast, efficient, powerful, and productive terminal application for users of command-line tools and shells like Command Prompt, PowerShell, and WSL. Its main features include multiple tabs, panes, Unicode and UTF-8 character support, a GPU accelerated text rendering engine, and custom themes, styles, and configurations.
---

Terminal is a [essential](install%20essential%20apps.md.md), [development](install%20development%20apps.md.md) app. The Windows Terminal is a modern, fast, efficient, powerful, and productive terminal application for users of command-line tools and shells like Command Prompt, PowerShell, and WSL. Its main features include multiple tabs, panes, Unicode and UTF-8 character support, a GPU accelerated text rendering engine, and custom themes, styles, and configurations.

- Open in [Microsoft Store](ms-windows-store://pdp/?ProductId=9N0DX20HK701&mode=mini), show in [webstore](https://microsoft.com/store/apps/9N0DX20HK701) or invoke:
  ```
  winget install -e 9N0DX20HK701 --accept-package-agreements
  ```
- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e Microsoft.WindowsTerminal
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

- [Windows Terminal - A unified interface to access and manage different command-line tools and environments](Windows%20Terminal%20-%20A%20unified%20interface%20to%20access%20and%20manage%20different%20command-line%20tools%20and%20environments.md)
- [Synchronize content between devices](Synchronize%20content%20between%20devices.md)
- [multiline powershell expression](multiline%20powershell%20expression.md)


Tags:
