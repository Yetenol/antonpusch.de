---
date: "2025-03-22T23:45:55.022+01:00"
title: "Obsidian Git"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 
winget-id: 
github-repo: denolehov/obsidian-git
github-release-filename: 
website: 
priority: 3
modportal0-id: obsidian-git
thumbnail: 
categories:
  - Synchronization
  - Version control
  - Backup
synopsis: |
  Plugin that allows you to back up your Obsidian.md vault to a remote Git repository (e.g. private repo on GitHub).
extends-app: "[[Obsidian|Obsidian]]"
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

# Synchronize vault between different devices

A private GitHub repository is used

- Create a new private GitHub repository

# On Windows

No additional setup required

# On Android

- Generate [a new personal access](https://github.com/settings/tokens/new?scopes=repo) token on GitHub
- Open `Settings > (# Community plugins) Obsidian Git > (# Authentication/Commit Author)`
- *GitHub user name* ← Username on your git server. E.g. your username on GitHub
- *Personal access token* ← Password/Personal access token
- *Real name* ← Author name for commit
- *Email address* ← Author email for commit
