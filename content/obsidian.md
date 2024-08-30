---
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
tags:
  - obsidian/cleanup
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

# Synchronisation

Server host
- OneDrive Host vault files

PC
- [Remotely Save](./remotely%20save.md) syncs files while Obsidian is running
- Symbolic Link sync .obsidian config

Phone
- [FolderSync](https://play.google.com/store/apps/details?id=dk.tacit.android.foldersync.lite&hl=en) syncs files
- FolderSync syncs .obsidian config folder separately
- Starts sync every time obsidian is open (configured through Samsung Routines)

Backup version control
- PC commits and pushes local changes to GitHub repository every 5min

Publishing
- [Digital Garden](./digital%20garden.md) generates static markdown files, pushes them into separate repository, Netlify deploys from GitHub webhook [Setup my digital garden](./setup%20my%20digital%20garden.md)

# Extensions

```dynamic-embed
[[List extensions for this app]]
```

Take a look at
Database Folder, Projects, Breadcrumbs, and Metadata Menu (which mimics supertags in Tana) are also solid plugins in Obsidian that complement Dataview and may be worth checking out too

# Motivation

- Don't get lost improving your setup, start writing
- Obsidian subreddit/YouTube is bad influence


![Pasted image 20231204121250.png](./attachments/pasted%20image%2020231204121250.png)

# Configuration and settings

 Replace local settings with synchronized cloud settings

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