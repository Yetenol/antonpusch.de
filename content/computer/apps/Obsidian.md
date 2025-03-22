---
date: "2025-03-22T23:22:30.238+01:00"
title: "Obsidian"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 
winget-id: Obsidian.Obsidian
github-repo: obsidianmd/obsidian-releases
github-release-filename: 
website: https://obsidian.md/
priority: 2
link-modportals:
  - "[Comminity plugins](obsidian://show-plugin?id=~modportal0-id~)"
  - "[Webstore](https://obsidian.md/plugins?id=~modportal0-id~)"
modportal0-id: 
thumbnail: 
categories:
  - Office
  - Education
synopsis: Obsidian is a powerful and extensible knowledge base that works on top of your local folder of plain text files.
cssclasses:
  - cards
dg-content-classes:
  - cards
---

Obsidian is a [office](install%20office%20apps.md.md), [education](install%20education%20apps.md.md) app. Obsidian is a powerful and extensible knowledge base that works on top of your local folder of plain text files.

- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e Obsidian.Obsidian
  ```
- Download the [latest release](https://github.com/obsidianmd/obsidian-releases/releases/latest) of its source code [repository](https://github.com/obsidianmd/obsidian-releases) on GitHub
- Download it from the [publisher's website](https://obsidian.md/)


# Synchronisation

Server host
- OneDrive Host vault files

PC
- [Remotely Save](./Remotely-Save.md) syncs files while Obsidian is running
- Symbolic Link sync .obsidian config

Phone
- [FolderSync](https://play.google.com/store/apps/details?id=dk.tacit.android.foldersync.lite&hl=en) syncs files
- FolderSync syncs .obsidian config folder separately
- Starts sync every time obsidian is open (configured through Samsung Routines)

Backup version control
- PC commits and pushes local changes to GitHub repository every 5min

Publishing
- [Digital Garden](./Digital-Garden.md) generates static markdown files, pushes them into separate repository, Netlify deploys from GitHub webhook [Setup my digital garden](../../Setup-my-digital-garden.md)

# Extensions

```dynamic-embed
[[List extensions for this app]]
```

Take a look at
Database Folder, Projects, Breadcrumbs, and Metadata Menu (which mimics supertags in Tana) are also solid plugins in Obsidian that complement Dataview and may be worth checking out too

# Motivation

- Don't get lost improving your setup, start writing
- Obsidian subreddit/YouTube is bad influence


![Pasted image 20231204121250.png](../../Pasted-image-20231204121250.png)

# Configuration and settings

 Replace local settings with synchronized cloud settings

```powershell
New-Item D:\Notes\.obsidian -Target D:\PlutosCloud\Config\.obsidian\ -ItemType SymbolicLink
$filesToKeepAvailable = Get-ChildItem D:\PlutosCloud\Config\.obsidian -Recurse
$filesToKeepAvailable += Get-Item D:\PlutosCloud\Config\.obsidian
$filesToKeepAvailable | foreach {
    $_.Attributes = $_.Attributes -bor 0x080000 -band (-bnot 0x100000)
}
```

```powershell fold
Invoke-Command {
$cloudFolder = "D:\PlutosCloud\Config"
$localFolder = "D:\Notes"
$syncItems = @(
    '.obsidian\'
)

# Replace local files with references to synchronized cloud files
$syncItems | foreach {
    New-Item -ItemType SymbolicLink -Path "$localFolder\$_" -Target "$cloudFolder\$_" -Force -ErrorAction Stop
}

# Keep all cloud files, that are accessible via symlinks, fully present locally
Set-Location $cloudFolder -ErrorAction Stop
@(
    Get-Item $syncItems | where PSIsContainer | Get-ChildItem -Recurse
    Get-Item $syncItems
) | foreach { 
    $_.Attributes = $_.Attributes -bor 0x080000 -band (-bnot 0x100000) 
}
}
```

Or configure manually

Open `Settings > General`
- [x] Strict line breaks _# Editor_
- `In the folder specified below` ← Default location for new attachments
    - `attachments` ← Attachment folder path

Open `Settings > Appearance`
- `Adapt to system` ← Base color scheme

Open `Settings > Hotkeys`
- `Ctrl + Alt + C` ← Obsidian Git: Commit all changes with specific message
- `Ctrl + Shift + G` ← Obsidian Git: Open source control view
- `Ctrl + Alt + P` ← Obsidian Git: Pull
- `Ctrl + Alt + Shift + P` ← Obsidian Git: Push

---
Sources:
- 2023-03-08: [Create static mardown table from dataview querry](https://forum.obsidian.md/t/dataviewjs-snippet-showcase/17847/225)
- 2023-01-22: [GitHub - oleeskild/obsidian-digital-garden](https://github.com/oleeskild/obsidian-digital-garden)
- 2023-01-22: [01 Getting started](https://dg-docs.ole.dev/getting-started/01-getting-started/)
- 2023-01-22: [First deploy fails · Issue 167 · oleeskild/obsidian-digital-garden · GitHub](https://github.com/oleeskild/obsidian-digital-garden/issues/167#issuecomment-1399222123)
- 2022-12-27: [Everything I wish I knew when starting to use Obsidian — Nicholas Seitz Photographer](https://www.nickseitz.com/writing/obsidian-day-one-starterpack)

Related:
```dynamic-embed
[[List related notes]]
```

Tags:

https://www.reddit.com/r/ObsidianMD/comments/1872kf5/introducing_obsidian_latex_ocr_generate_latex/