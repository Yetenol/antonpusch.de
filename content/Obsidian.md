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
  
Obsidian is a [office](install%20office%20apps.md.md), [education](install%20education%20apps.md.md) app. Obsidian is a powerful and extensible knowledge base that works on top of your local folder of plain text files.   
- Invoke the installer listed on Windows Package Manager:  
  ```  
  winget install -e Obsidian.Obsidian  
  ```  
- Download the [latest release](https://github.com/obsidianmd/obsidian-releases/releases/latest) from [Github](https://github.com/obsidianmd/obsidian-releases)  
- Download it from the [publisher's website](https://obsidian.md/)  
  
  
# Synchronisation  
  
Server host  
- OneDrive Host vault files  
  
PC  
- [Remotely Save](./Remotely%20Save.md) syncs files while Obsidian is running  
- Symbolic Link sync .obsidian config  
  
Phone  
- [FolderSync](https://play.google.com/store/apps/details?id=dk.tacit.android.foldersync.lite&hl=en) syncs files  
- FolderSync syncs .obsidian config folder separately  
- Starts sync every time obsidian is open (configured through Samsung Routines)  
  
Backup version control  
- PC commits and pushes local changes to GitHub repository every 5min  
  
Publishing  
- [Digital Garden](./Digital%20Garden.md) generates static markdown files, pushes them into separate repository, Netlify deploys from GitHub webhook [Setup my digital garden](./Setup%20my%20digital%20garden.md)  
  
# Extensions  
  
| Name                                                         | Thumbnail | Modportal links                                                                                                                          | Categories                               | Description                                                                                                                                                                                              |  
| ------------------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |  
| **[Text Snippets](./Text%20Snippets.md)**                 |           | [Comminity plugins](obsidian://show-plugin?id=text-snippets-obsidian), [Webstore](https://obsidian.md/plugins?id=text-snippets-obsidian) | Editing                                  | Snippets for faster typing. Allows you to replace text templates, create your own, and expand text shortcuts.                                                                                            |  
| **[Dataview](./Dataview.md)**                           |           | [Comminity plugins](obsidian://show-plugin?id=dataview), [Webstore](https://obsidian.md/plugins?id=dataview)                             | Dynamic content                          | Dataview is a live index and query engine over your knowledge base. You can associate _data_ (like tags, dates, snippets, numbers, and so on) with your markdown pages, and then _query_ (like filter... |  
| **[Remotely Save](./Remotely%20Save.md)**                 |           | [Comminity plugins](obsidian://show-plugin?id=remotely-save), [Webstore](https://obsidian.md/plugins?id=remotely-save)                   | Synchronization                          | Yet another unofficial plugin allowing users to sync notes between local device and the cloud service (S3, Dropbox, webdav, OneDrive).                                                                   |  
| **[Digital Garden](./Digital%20Garden.md)**               |           | [Comminity plugins](obsidian://show-plugin?id=digitalgarden), [Webstore](https://obsidian.md/plugins?id=digitalgarden)                   | Publishing                               | Publish your notes to a digital garden for others to enjoy.                                                                                                                                              |  
| **[Obsidian Git](./Obsidian%20Git.md)**                   |           | [Comminity plugins](obsidian://show-plugin?id=obsidian-git), [Webstore](https://obsidian.md/plugins?id=obsidian-git)                     | Synchronization, Version control, Backup | Plugin that allows you to back up your Obsidian.md vault to a remote Git repository (e.g. private repo on GitHub).                                                                                       |  
| **[Translate](./Translate.md)**                         |           | [Comminity plugins](obsidian://show-plugin?id=translate), [Webstore](https://obsidian.md/plugins?id=translate)                           | Editing, Translation                     | Translate text and notes with Google Translate, DeepL, Azure, and more.                                                                                                                                  |  
| **[deepL](./deepL.md)**                                 |           | [Comminity plugins](obsidian://show-plugin?id=deepl), [Webstore](https://obsidian.md/plugins?id=deepl)                                   | Editing Translation                      | Allows translation of selected texts into more than 25 languages with DeepL.                                                                                                                             |  
| **[Copy as Latex](./Copy%20as%20Latex.md)**                 |           | [Comminity plugins](obsidian://show-plugin?id=obsidian-copy-as-latex), [Webstore](https://obsidian.md/plugins?id=obsidian-copy-as-latex) | \-                                       | Designed for when you want to do most of your writing in a nice Obsidian environment, with lots of citations from a nicely managed set of references etc. Lighterweight than Pandoc, doesn't assume y... |  
| **[Advanced Cursors](./Advanced%20Cursors.md)**           |           | [Comminity plugins](obsidian://show-plugin?id=advanced-cursors), [Webstore](https://obsidian.md/plugins?id=advanced-cursors)             | Editing                                  | Use multiple cursors even more powerfully.                                                                                                                                                               |  
| **[LaTeX Suite](./LaTeX%20Suite.md)**                     |           | [Comminity plugins](obsidian://show-plugin?id=obsidian-latex-suite), [Webstore](https://obsidian.md/plugins?id=obsidian-latex-suite)     | Editing, Math                            | A plugin for Obsidian that aims to make typesetting LaTeX math as fast as handwriting.                                                                                                                   |  
| **[TlDraw](./TlDraw.md)**                               |           | [Comminity plugins](obsidian://show-plugin?id=tldraw), [Webstore](https://obsidian.md/plugins?id=tldraw)                                 | Graphics                                 | This Obsidian plugin allows users to use Tldraw, which is a tiny little drawing app, inside of Obsidian. Users can draw, plan, and use all of Tldraw's tools to augment their Obsidian experience. Th... |  
| **[Advanced URI](./Advanced%20URI.md)**                   |           | [Comminity plugins](obsidian://show-plugin?id=obsidian-advanced-uri), [Webstore](https://obsidian.md/plugins?id=obsidian-advanced-uri)   | Programming                              | Control everything with URI.                                                                                                                                                                             |  
| **[Execute Code](./Execute%20Code.md)**                   |           | [Comminity plugins](obsidian://show-plugin?id=execute-code), [Webstore](https://obsidian.md/plugins?id=execute-code)                     | Programming                              | Execute code snippets within a note.                                                                                                                                                                     |  
| **[Shell commands](./Shell%20commands.md)**               |           | [Comminity plugins](obsidian://show-plugin?id=obsidian-shellcommands), [Webstore](https://obsidian.md/plugins?id=obsidian-shellcommands) | Programming                              | Define system commands that you want to execute via command palette, hotkeys, URI links or automated events. E.g. open external applications or perform automated file modifications.                    |  
| **[Dynamic Embed](./Dynamic%20Embed.md)**                 |           | [Comminity plugins](obsidian://show-plugin?id=obsidian-dynamic-embed), [Webstore](https://obsidian.md/plugins?id=obsidian-dynamic-embed) | Visualisation                            | Embed snippets, templates and any linkable by delegating the current scope to the embedded file, treating it as content instead of a reference.                                                          |  
| **[Diagrams](./Diagrams.md)**                           |           | [Comminity plugins](obsidian://show-plugin?id=drawio-obsidian), [Webstore](https://obsidian.md/plugins?id=drawio-obsidian)               | Visualisation, Graphics                  | Create and edit Draw.io diagrams in Obsidian.                                                                                                                                                            |  
| **[Code Emitter🗑](./Code%20Emitter.md)**                 |           | [Comminity plugins](obsidian://show-plugin?id=code-emitter), [Webstore](https://obsidian.md/plugins?id=code-emitter)                     | Programming                              | Allows code blocks to be executed interactively in a sandbox like Jupyter notebooks. Supported language Rust, Kotlin, Python, JavaScript, TypeScript, etc.                                               |  
| **[Self-hosted LiveSync🗑](./Self-hosted%20LiveSync.md)** |           | [Comminity plugins](obsidian://show-plugin?id=obsidian-livesync), [Webstore](https://obsidian.md/plugins?id=obsidian-livesync)           | Synchronization                          | Community implementation of self-hosted livesync. Reflect your vault changes to some other devices immediately. Please make sure to disable other synchronize solutions to avoid content corruption o... |  
  
  
Take a look at  
Database Folder, Projects, Breadcrumbs, and Metadata Menu (which mimics supertags in Tana) are also solid plugins in Obsidian that complement Dataview and may be worth checking out too  
  
# Motivation  
  
- Don't get lost improving your setup, start writing  
- Obsidian subreddit/YouTube is bad influence  
  
  
![Pasted image 20231204121250.png](./attachments/Pasted%20image%2020231204121250.png)  
  
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
- [Symlinks in Obsidian](Symlinks%20in%20Obsidian.md)  
- [Obsidian as a markdown editor - Switch between Vscode and Obsidian](./Obsidian%20as%20a%20markdown%20editor%20-%20Switch%20between%20Vscode%20and%20Obsidian.md)  
- [How to structure notes - Bottom up, Tags, Top down](How%20to%20structure%20notes%20-%20Bottom%20up,%20Tags,%20Top%20down.md)  
- [Update dataview queries](Update%20dataview%20queries.md)  
- [The graph view in Obsidian shows to which topics a note relates](The%20graph%20view%20in%20Obsidian%20shows%20to%20which%20topics%20a%20note%20relates.md)  
- [Synchronize content between devices](Synchronize%20content%20between%20devices.md)  
- [Pandoc - Convert markup languages context aware with pandoc filters](Pandoc%20-%20Convert%20markup%20languages%20context%20aware%20with%20pandoc%20filters.md)  
- [Other people's obsidian projects](Other%20people's%20obsidian%20projects.md)  
- [Obsidian - Organize, link, and explore their thoughts, ideas, and information through a system of interconnected notes](Obsidian%20-%20Organize,%20link,%20and%20explore%20their%20thoughts,%20ideas,%20and%20information%20through%20a%20system%20of%20interconnected%20notes.md)  
- [Integrate Ai into note taking](Integrate%20Ai%20into%20note%20taking.md)  
- [How to build this garden](How%20to%20build%20this%20garden.md)  
- [Hide the first-level bullet points from results of list queries](./Hide%20the%20first-level%20bullet%20points%20from%20results%20of%20list%20queries.md)  
- [Create diagrams](Create%20diagrams.md)  
- [Convert wikilinks to markdown links](./Convert%20wikilinks%20to%20markdown%20links.md)  
- [Collaborate on synchronized notes in real-time](Collaborate%20on%20synchronized%20notes%20in%20real-time.md)  
  
  
Tags:  
  
https://www.reddit.com/r/ObsidianMD/comments/1872kf5/introducing_obsidian_latex_ocr_generate_latex/