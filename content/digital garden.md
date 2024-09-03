---
title: "Digital Garden"
dg-publish: true
not-in-use: 
microsoft-id: 
winget-id: 
github-repo: oleeskild/obsidian-digital-garden
github-release-filename: 
website: 
priority: 3
link-modportals: 
modportal0-id: digitalgarden
thumbnail: 
categories:
  - Publishing
synopsis: |
  Publish your notes to a digital garden for others to enjoy.
modportal1-id: digitalgarden
extends-app: "[[Obsidian|Obsidian]]"
---

Digital Garden is a [Obsidian](./obsidian.md) extension about publishing. Publish your notes to a digital garden for others to enjoy.  
- Install extension via [Comminity plugins](obsidian://show-plugin?id=digitalgarden), [Webstore](https://obsidian.md/plugins?id=digitalgarden)
- Install extension via 
- Download the [latest release](https://github.com/oleeskild/obsidian-digital-garden/releases/latest) from [Github](https://github.com/oleeskild/obsidian-digital-garden)


# Setup note publishing

- Follow [these instructions](https://github.com/oleeskild/obsidian-digital-garden)
- If Netlify cannot deploy the page, try this fix [First deploy fails · Issue #167 · oleeskild/obsidian-digital-garden · GitHub](https://github.com/oleeskild/obsidian-digital-garden/issues/167#issuecomment-1399222123)

# Troubleshooting

Some notes are not reachable via links or didn't apply frontmatter modifications
- Bug: [Frontmatter isn't parsed for files edited in external programs · Issue #176 · oleeskild/obsidian-digital-garden · GitHub](https://github.com/oleeskild/obsidian-digital-garden/issues/176)
- Search for `"dg-publish: true"` and open all files
- Run `Digital Garden: Publish Multiple Notes` again

Open all corrupt notes in Obsidian to repair their cache
```powershell
Set-Location "D:\DEV\digitalgarden\"
git pull
Set-Location "D:\DEV\digitalgarden\src\site\notes"
Get-ChildItem -Filter "*.md" -Recurse | where {
    Select-String -Path $_ -Pattern "dg-publish: true" 
} | foreach {
    $corruptNote = Resolve-Path $_.FullName -Relative
    explorer "`"obsidian:///D:\Notes\$corruptNote`""
    Start-Sleep 1
}
explorer "`"obsidian://advanced-uri?commandname=Reload app without saving`""
```

Open all published notes in Obsidian to repair their cache
```run-powershell
Get-ChildItem -Path "D:\Notes" -Filter "*.md" -Recurse | where {
    Select-String -Path $_ -Pattern "dg-publish: true" 
} | foreach {
    explorer "obsidian:///$($_.FullName)"
    Start-Sleep 1
}
```


# What is a digital garden

- [GitHub - MaggieAppleton/digital-gardeners: Resources, links, projects, and ideas for gardeners tending their digital notes on the public interwebs](https://github.com/MaggieAppleton/digital-gardeners)
- [What are digital gardens? – Chuck Grimmett](https://cagrimmett.com/notes/2020/11/08/what-are-digital-gardens/)
- [Digital Garden | Aaron Young](https://ajy.co/01-personal/digital-garden/)
- [What are digital gardens? – Chuck Grimmett](https://cagrimmett.com/notes/2020/11/08/what-are-digital-gardens/)
- [How to set up your own digital garden - Ness Labs](https://nesslabs.com/digital-garden-set-up)
- [Maggie Appleton](https://maggieappleton.com/)
---

Sources:
- 2023-01-22: [A Brief History and Ethos of the Digital Garden - Obsidian Hub - Obsidian Publish](https://publish.obsidian.md/hub/05+-+Concepts/A+Brief+History+and+Ethos+of+the+Digital+Garden)
- 2023-01-22: [Digital garden - Obsidian Hub - Obsidian Publish](https://publish.obsidian.md/hub/05+-+Concepts/Digital+garden)

Related:

Tags: