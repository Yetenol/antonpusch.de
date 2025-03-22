---
date: "2025-03-22T23:45:55.004+01:00"
title: "FreeTube"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 
winget-id: PrestonN.FreeTube
github-repo: FreeTubeApp/FreeTube
github-release-filename: 
website: https://freetubeapp.io/
priority: 3
categories:
  - Entertainment
synopsis: An Open Source YouTube app for privacy
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

# Import subscriptions, history

> [!info]- Replace local settings, subscriptions, history with synchronized cloud data
> ```powershell
> Invoke-Command {
> $cloudFolder = "D:\PlutosCloud\Config\Freetube"
> $localFolder = "$env:AppData\FreeTube"
> $syncItems = @(
>     'profiles.db', 'settings.db', 
>     'playlists.db', 'history.db'
> )
> 
> # Replace local files with references to synchronized cloud files
> $syncItems | foreach {
>     New-Item -ItemType SymbolicLink -Path "$localFolder\$_" -Target "$cloudFolder\$_" -Force -ErrorAction Stop
> }
> 
> # Keep all cloud files, that are accessible via symlinks, fully present locally
> Set-Location $cloudFolder -ErrorAction Stop
> @(
>     Get-Item $syncItems | where PSIsContainer | Get-ChildItem -Recurse
>     Get-Item $syncItems
> ) | foreach { 
>     $_.Attributes = $_.Attributes -bor 0x080000 -band (-bnot 0x400000) 
> }
> }
> ```

Or configure manually

Open `Settings > Distraction Free Settings`
- [x] Hide Video Subscriptions
- [x] Hide Recommended Videos
- [x] Hide Trending Videos
- [x] Hide Popular Videos

Open `Settings > Download Settings`
- `Open in web browser` ← Download Behavior

Open `Settings > SponsorBlock Settings`
- [x] Enable SponsorBlock
