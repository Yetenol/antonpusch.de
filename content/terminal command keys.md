---
title: "Terminal Command Keys"
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

![thumbnail](https://cdn.vsassets.io/v/M226_20230814.3/_content/Header/default_icon_128.png) Terminal Command Keys is a [Visual Studio Code](./visual%20studio%20code.md) extension about version control. Assign terminal commands to a keybinding. 

- Install extension via [Extensions](vscode:extension/petekinnecom.terminal-command-keys), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=petekinnecom.terminal-command-keys)
- Download the [latest release](https://github.com/petekinnecom/terminal-command-keys.git/releases/latest) of its source code [repository](https://github.com/petekinnecom/terminal-command-keys.git) on GitHub


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
- [Obsidian as a markdown editor - Switch between Vscode and Obsidian](./obsidian%20as%20a%20markdown%20editor.md)
- [Invoke a shell command in VS Code's integrated terminal using a keybindung](./invoke%20a%20shell%20command%20in%20vs%20code's%20integrated%20terminal%20using%20a%20keybindung.md)


Tags:
[Version Control - Track, commit, push, rebase changes in VS Code](./version%20control.md)