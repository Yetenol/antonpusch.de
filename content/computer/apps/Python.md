---
date: "2025-03-22T23:45:55.022+01:00"
title: "Python"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: 
microsoft-id: 
winget-id: Python.Python.3.13
github-repo: 
github-release-filename: 
website: https://www.python.org/downloads/
priority: 
link-modportals:
  - <pre><code class='language-powershell'>pip install ~modportal0-id~</code></pre>
modportal0-id: 
thumbnail: 
categories:
  - Development
synopsis: Python is a high-level, versatile programming language known for its clean syntax and readability, making it popular for everything from web development to data science and artificial intelligence.
extends-app: 
cssclasses:
  - cards
dg-content-classes:
  - cards
---


```dynamic-embed
[[Describe this app and list installation sources]]
```

Troubleshoot PATH setup
- [List all apps in PATH locations](../../powershell/develop/List-all-apps-in-PATH-locations.md)

Find newest version
```powershell
winget search Python.Python
```

Install python in system-wide `%ProgramFiles%`
- Package installation will have to be privileged as well
```powershell
winget install -e Python.Python.3.13 --scope machine
```

```dynamic-embed
[[List extensions for this app]]
```
