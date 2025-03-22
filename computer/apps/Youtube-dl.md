---
date: "2025-03-22T12:13:19.168+01:00"
title: "Youtube-dl"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 
winget-id: youtube-dl.youtube-dl
github-repo: ytdl-org/youtube-dl
github-release-filename: youtube-dl.exe
website: https://youtube-dl.org/
priority: 6
categories:
  - Entertainment
synopsis: youtube-dl is a free and open source download manager for video and audio from YouTube and over 1,000 other video hosting websites.
---

Youtube-dl is a [entertainment](install%20entertainment%20apps.md.md) app. youtube-dl is a free and open source download manager for video and audio from YouTube and over 1,000 other video hosting websites.

- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e youtube-dl.youtube-dl
  ```
- Invoke the [installer](https://github.com/ytdl-org/youtube-dl/releases/latest/download/youtube-dl.exe) from the latest release of its source code [repository](https://github.com/ytdl-org/youtube-dl) on GitHub
  ```powershell
  Invoke-WebRequest 'https://github.com/ytdl-org/youtube-dl/releases/latest/download/youtube-dl.exe' -OutFile "$env:Temp/youtube-dl.exe"
  if ($?) {Start-Process "$env:Temp/youtube-dl.exe"}
  ```
- Download it from the [publisher's website](https://youtube-dl.org/)


> [!info]- Replace local settings with synchronized cloud settings
> ```powershell
> Invoke-Command {
> $cloudFolder = "D:\Nextcloud\Config\Youtube-dl"
> $localFolder = "$env:AppData\youtube-dl"
> $syncItems = @(
>     'config.txt'
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