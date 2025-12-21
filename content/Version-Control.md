---
date: "2025-07-17T08:13:58.993+02:00"
title: "Version Control"
description: "Track, commit, push, rebase changes in VS Code"
dg-publish: true
cssclasses:
  - cards
dg-content-classes:
  - cards
---

**Commit all** changed with specific message using `[ctrl+alt+c]`
- very quick
- enter commit message in a prompt instead of a file with setting `"git.useEditorAsCommitInput": false,` 
- Bind `ctrl+alt+c` to `Git: Commit All`

**See changes** in source control side bar using `[ctrl+shift+g]` 
- see changed files
- stage and unstage files

Rebase and **publish** all local commit to the remote main branch using `[ctrl+shift+p]`
- Install script [git-publish.ps1](https://github.com/Yetenol/alias)
- Install extension [Terminal Command Keys](./computer/apps/Terminal-Command-Keys.md)
- Bind `ctrl+shift+p` to execute `git-publish.ps1` in the terminal


All keyboard shortcuts

```json
    {
        "key": "ctrl+alt+c",
        "command": "git.commitAll"
    },
    {
        "key": "ctrl+shift+p",
        "command": "terminalCommandKeys.run",
        "args": {
            "cmd": "\u0001git-publish.ps1"
        },
    },
```

All settings

```json
"git.useEditorAsCommitInput": false,
```


---
Sources:

Related:
```dynamic-embed
[[List extensions for this app]]
```

Tags:
[Visual Studio Code](./computer/apps/Visual-Studio-Code.md)

