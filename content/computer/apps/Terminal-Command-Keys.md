---
date: "2025-03-22T23:45:55.048+01:00"
title: "Terminal Command Keys"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: false
microsoft-id: 
winget-id: 
github-repo: petekinnecom/terminal-command-keys.git
github-release-filename: 
website: 
priority: 
link-modportals: 
modportal0-id: petekinnecom.terminal-command-keys
thumbnail: https://cdn.vsassets.io/v/M226_20230814.3/_content/Header/default_icon_128.png
categories:
  - Version control
synopsis: |
  Assign terminal commands to a keybinding.
extends-app: "[[Visual Studio Code|Visual Studio Code]]"
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

Open current file in Obsidian using `[F10]`

```json
    {
        "key": "f10",
        "command": "terminalCommandKeys.run",
        "args": {
            "cmd": "\u0001if('${file}' -like 'd:\\Notes\\*') {\n explorer \"`\"obsidian://open?vault=Notes&file=${relativeFile}`\"\"\n } else {\n $externalTarget = Get-Item 'd:\\Notes\\external' | select -expand Target;\n $path = '${relativeFile}' -replace '^\\.\\\\', 'external\\';\n if('${file}' -notlike \"$externalTarget\\*\") {\n start powershell -Verb RunAs \"-Command New-Item -Path 'D:/Notes/external' -Target '${workspaceRoot}' -ItemType SymbolicLink -Force\";\n explorer \"`\"obsidian://advanced-uri?commandname=Reload app without saving`\"\";\n Start-Sleep 1;\n }\n explorer \"`\"obsidian://advanced-uri?filepath=$path&line=${line}`\"\"}",
            "showTerminal": false,
        },
    },
```


---
Sources:

Related:
```dynamic-embed
[[List related notes]]
```

Tags:
[Version Control - Track, commit, push, rebase changes in VS Code](../../Version-Control.md)