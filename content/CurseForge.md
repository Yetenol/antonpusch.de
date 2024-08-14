---  
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
  
CurseForge is a **discarded** [gaming](install%20gaming%20apps.md.md) app.    
- Invoke the installer listed on Windows Package Manager:  
  ```  
  winget install -e Overwolf.CurseForge  
  ```  
- Download it from the [publisher's website](https://download.curseforge.com/)  
  
  
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
  
| Name                                                               | Thumbnail                                                                                | Modportal links                                                                                                                                  | Categories | Description                                                                                                                                                                                              |  
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |  
| **[Lithium](./Lithium.md)**                                   | ![](https://cdn.modrinth.com/data/gvQqBUqZ/icon.png)                                     | [Modrinth](https://modrinth.com/mod/lithium), [CurseForge](https://www.curseforge.com/minecraft/mc-mods/lithium)                                 | \-         | No-compromises game logic/server optimization mod                                                                                                                                                        |  
| **[Sodium](./Sodium.md)**                                     | ![](https://media.forgecdn.net/avatars/284/773/637298471098686391.png)                   | [Modrinth](https://modrinth.com/mod/sodium), [CurseForge](https://www.curseforge.com/minecraft/mc-mods/sodium)                                   | \-         | Modern rendering engine and client-side optimization mod                                                                                                                                                 |  
| **[Freecam](./Freecam.md)**                                   | ![](https://media.forgecdn.net/avatars/467/941/637750574586450724.png)                   | [CurseForge](https://www.curseforge.com/minecraft/mc-mods/free-cam)                                                                              | \-         |  This mod allows you to control your camera separately from your player. While it is enabled, you can fly around and travel through blocks within your render distance. Disabling it will restore you... |  
| **[ItemSwapper](./ItemSwapper.md)**                           | ![](https://cdn.modrinth.com/data/RPOSBQgq/2ab4614cc4288baa911be0365cd22203e75b9233.png) | [Modrinth](https://modrinth.com/mod/itemswapper), [CurseForge](https://www.curseforge.com/minecraft/mc-mods/itemswapper)                         | \-         | Adds an item switch interface triggered by pressing a hotkey                                                                                                                                             |  
| **[Mouse Wheelie](./Mouse%20Wheelie.md)**                       | ![](https://cdn.modrinth.com/data/u5Ic2U1u/icon.png)                                     | [Modrinth](https://modrinth.com/mod/mouse-wheelie), [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mouse-wheelie)                     | \-         | A small clientside mod to enable various mouse wheel related actions. Features item scrolling, inventory sorting, item refilling and much more!                                                          |  
| **[InventoryTabs🗑](./InventoryTabs.md)**                     | ![](https://cdn.modrinth.com/data/F1AqcMCK/icon.png)                                     | [Modrinth](https://modrinth.com/mod/inventory-tabs-updated)                                                                                      | \-         | Client side mod to access nearby blocks without leaving your inventory.                                                                                                                                  |  
| **[Mouse Tweaks🗑](./Mouse%20Tweaks.md)**                       | ![](https://cdn.modrinth.com/data/aC3cM3Vq/icon.jpg)                                     | [Modrinth](https://modrinth.com/mod/mouse-tweaks), [CurseForge](https://www.curseforge.com/minecraft/mc-mods/mouse-tweaks)                       | \-         | Enhances inventory management by adding various functions to the mouse buttons.                                                                                                                          |  
| **[Inventory Essentials🗑](./Inventory%20Essentials.md)**       | ![](https://cdn.modrinth.com/data/Boon8xwi/469cace78935b118f2c713b44ca9e85efcb42c39.png) | [Modrinth](https://modrinth.com/mod/inventory-essentials)                                                                                        | \-         | This mod adds a few inventory control enhancements that have initially been introduced in mods like Inventory Tweaks and Mouse Tweaks, but keeps it limited to only the most essential functionality.... |  
| **[Inventory Profiles Next🗑](./Inventory%20Profiles%20Next.md)** | ![](https://cdn.modrinth.com/data/O7RBXm3n/icon.png)                                     | [Modrinth](https://modrinth.com/mod/inventory-profiles-next), [CurseForge](https://www.curseforge.com/minecraft/mc-mods/inventory-profiles-next) | \-         | Help you keep your inventory sorted. Replace your quasi-broken tool. Dump everything in that chest with one click. Move the items you have that are also already in the chest. Lock item slots in pla... |  
  
  
Add **profile to vanilla launcher** using elevated [script](./attachments/Link-MinecraftFabric.ps1)  
  
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
  
- [NBT Editor](./NBT%20Editor.md)  
- [Chunk Editor](./Chunk%20Editor.md)  
- [Use design inspirations to build creative things in Minecraft](Use%20design%20inspirations%20to%20build%20creative%20things%20in%20Minecraft.md)  
  
  
---  
Sources:  
  
Related:  
  
Tags:  
[Minecraft](./Minecraft.md)  
