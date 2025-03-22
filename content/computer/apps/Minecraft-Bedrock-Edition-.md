---
date: "2025-03-22T23:45:55.022+01:00"
title: "Minecraft (Bedrock Edition)"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 9NBLGGH2JHXJ
winget-id: 
github-repo: 
github-release-filename: 
website: 
priority: 10
categories:
  - Gaming
---

Synopsis::

- **DON'T LAUNCH MINECRAFT YET**
- setup **cloud synchronization** using elevated [script](../../Sync-MinecraftBedrock.ps1)

  ```powershell
  $url = 'https://raw.githubusercontent.com/Yetenol/Setup-Computer/main/scripts/Sync-MinecraftBedrock.ps1'
  $command = "Invoke-Command -ScriptBlock ([ScriptBlock]::Create((Invoke-WebRequest -Uri $url)))"
  Start-Process wt -Verb RunAs -ArgumentList "PowerShell.exe -NoExit -Command $command"
  ```

- **alternatively** configure **_manually_**:
- Install Resource Packs _manually_
    - [Marketplace Hider](https://mcpedl.com/marketplace-remover-resource-pack/)
    - [Foxy's Resource Pack Bundle](https://foxynotail.com/resource-packs/foxys-resource-pack/)
- Activate packs _manually_
  - Open `Settings > Global Resources > My packs`
  - click on the packs and activate them
- Setup Skin _manually_
  - Download [skin](https://minecraft.tools/download-skin/Yetenol)
  - Open `Dressing Room > Menu > Classic Skins > Owned > Import > Choose new skin`
  - Import downloaded skin

# Modify Settings

Open `Profile`
- `Yetenol` =: Name

Open `Video`
- `100` =: Brightness
- [x] Fullscreen
- [x] Hide Paper Doll
- [ ] Screen Animations
- `70.00°` =: FOV
- [ ] View Bobbing
- [ ] FOV Can Be Altered By Gameplay
- `-1` =: GUI Scale Modifier

Open `Audio`
- `0` =: Music

---
Sources:

Related:

Tags:
[Minecraft](./Minecraft.md)