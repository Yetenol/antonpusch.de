---
date: "2025-03-22T23:45:54.998+01:00"
title: "CurseForge"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 
winget-id: Overwolf.CurseForge
github-repo: 
github-release-filename: 
website: https://download.curseforge.com/
link-modportals:
  - "[Modrinth](https://modrinth.com/mod/~modportal0-id~)"
  - "[CurseForge](https://www.curseforge.com/minecraft/mc-mods/~modportal1-id~)"
  - "[Add to modpack](https://www.curseforge.com/minecraft/mc-mods/~modportal1-id~/download?client=y)"
priority: 10
categories:
  - Gaming
not-in-use: true
inherit-extensions: "[Minecraft](./Minecraft.md)"
cssclasses:
  - cards
dg-content-classes:
  - cards
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

- launch CurseForge and skip intro
- install Minecraft with *Standard* modding folder
- link remote config using elevated [script](https://raw.githubusercontent.com/Yetenol/Setup-Computer/main/scripts/Sync-MinecraftJava.ps1)

  ```powershell
  $url = 'https://raw.githubusercontent.com/Yetenol/Setup-Computer/main/scripts/Sync-MinecraftJava.ps1'
  $command = "Invoke-Command -ScriptBlock ([ScriptBlock]::Create((Invoke-WebRequest -Uri $url)))"
  Start-Process wt -Verb RunAs -ArgumentList "PowerShell.exe -NoExit -Command $command"
  ```

    ```powershell
    Link-RemoteConfig `
    -cloudPath "D:\OneDrive\Gaming\Minecraft Java" `
    -localPath "$env:UserProfile\curseforge\minecraft\Install" `
    -syncItems @( '.\saves'; '.\resourcepacks'; '.\screenshots'; '.\config'; '.\shaderpacks'; '.\hotbar.nbt'; '.\options.txt'; '.\servers.dat' )
    ```

- add Minecraft shortcut to StartMenu

    ```powershell
    $installPath = "$env:UserProfile\curseforge\minecraft\Install"
    $installBin = "$installPath\minecraft.exe"
    $shortcutName = "Minecraft.lnk"
    
    $env:Startup = (New-Object -ComObject Shell.Application).NameSpace('shell:Startup').Self.Path
    $WshShell = New-Object -comObject WScript.Shell
    $Shortcut = $WshShell.CreateShortcut("$env:Startup\$shortcutName")
    $Shortcut.TargetPath = $installBin
    $Shortcut.WorkingDirectory = $installPath
    $Shortcut.Arguments = "--workDir=`"$installPath`""
    $Shortcut.Save()
    ```

- open Minecraft from Start Menu
- sign in and launch lastest release
- close Minecraft

## Usage

- to **play** vanilla or modded Minecraft launch `Minecraft Launcher`  
- to **manage modpacks** launch `CurseForge`  

# Modpacks

## Setup Vanilla Modpack

# CurseForge

CurseForge is a modding platform for Minecraft, among others. Both vanilla and modded instances are launched via the official launcher, which is installed with CurseForge to be more compatible. CurseForge is primarily used to download and update mods.

```dynamic-embed
[[List extensions for this app]]
```

Add **profile to vanilla launcher** using elevated [script](../../Link-MinecraftFabric.ps1)

```powershell
$url = 'https://raw.githubusercontent.com/Yetenol/Setup-Computer/main/scripts/Link-MinecraftFabric.ps1'
$command = "Invoke-Command -ScriptBlock ([ScriptBlock]::Create((Invoke-WebRequest -Uri $url)))"
Start-Process wt -Verb RunAs -ArgumentList "PowerShell.exe -NoExit -Command $command"
```

Add the Vanilla profile to the launcher

```json
"Vanilla" : {
      "created" : "1970-01-01T00:00:00.0000000Z",
      "gameDir" : "C:\\Users\\anton\\curseforge\\minecraft\\Instances\\Vanilla\\",
      "javaArgs" : "-Xmx4096m -Xms256m -Dminecraft.applet.TargetDirectory=\"C:\\Users\\anton\\curseforge\\minecraft\\Instances\\Vanilla\" -Dfml.ignorePatchDiscrepancies=true -Dfml.ignoreInvalidMinecraftCertificates=true -Duser.language=en -Duser.country=US",
      "lastUsed" : "2023-05-18T21:41:04.8418337Z",
      "lastVersionId" : "fabric-loader-0.14.19-1.19.4",
      "name" : "Vanilla",
      "resolution" : {
        "height" : 480,
        "width" : 854
      },
      "type" : "custom"
    }
```

## Custom Modpacks

- **Import** a custom modpack (_optional_)  
  using a CurseForge export file
  - Click `Create Custom Profile`
  - Click `Import a previously created profile`
- **Add** a custom modpack (_optional_)  
  - Click `Create Custom Profile`
  - Enter a name and the version configuration
  - Right click profile and click `Open Folder`
  - Import and override all modpack files

## External editors

```dynamic-embed
[[List related notes]]
```

---
Sources:

Related:

Tags:
[Minecraft](./Minecraft.md)
