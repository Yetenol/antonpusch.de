---
date: "2025-07-17T08:13:58.511+02:00"
title: "Obsidian as a markdown editor"
description: "Switch between Vscode and Obsidian"
dg-publish: true
---
# Implement hotkeys in Obsidian and VS Code

## Open Obsidian's current file in VS Code

- [p] opens current file, jumps to same line
- [p] uses vault root as workspace folder
- [p] works with spaces in filename
- requires [Shell commands](./computer/apps/Shell-commands.md)
- Uses vault's root folder as workspace

```cmd
code . --goto \"{{file_path:absolute}}":{{caret_position}}
```

## Open VS Code's current file in Obsidian's **main** vault

- [p] opens current file, jump to same line
- [p] works with spaces in filename
- [p] opens from predefined vault or symbolic links workspace folder as `D:\Notes\external`
- requires [Terminal Command Keys](./computer/apps/Terminal-Command-Keys.md) and [Advanced URI](./computer/apps/Advanced-URI.md)
- replace `D:/Notes/` which occurs 3 times with your vault path (use `/` instead of `\`)
- first character `\u0001` clears drafted prompt in the terminal
- if the file is in your main vault, open it
- otherwise update the `external/` symbolic link if necessary (requires admin privileges)
- then opens the file in the main vault

> [!warning] Ignore the folder `external/` in git and in [Remotely Save](./computer/apps/Remotely-Save.md)


Add VS Code keyboard shortcut:
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

# Alternatives

Open VS Code file **from** main vault in Obsidian
- [p] opens current file, jump to same line
- [p] works with spaces in filename
- [c] file must be in the one predefined vault
- requires [Terminal Command Keys](./computer/apps/Terminal-Command-Keys.md) and [Advanced URI](./computer/apps/Advanced-URI.md)
- default integrated terminal must be PowerShell
- first character `\u0001` clears drafted prompt in the terminal
- replace the vault name with yours
- vault must be specified because Terminal Command Keys's `${file}` variable starts lowercase and therefore isn't recognized by obsidian as a vault

Add VS Code keyboard shortcut:
```json
    {
        "key": "f10",
        "command": "terminalCommandKeys.run",
        "args": {
            "cmd": "\u0001explorer \"`\"obsidian://advanced-uri?filepath=${relativeFile}&line=${line}`\"\"",
            "showTerminal": false,
        },
    },
```

Open VS Code file **at the top** **from** main vault in Obsidian
- requires [Terminal Command Keys](./computer/apps/Terminal-Command-Keys.md)
- [p] opens current file
- [p] works with spaces in filename
- [c] file must be in the one predefined vault

```json
    {
        "key": "f10",
        "command": "terminalCommandKeys.run",
        "args": {
            "cmd": "\u0001explorer \"`\"obsidian://open?vault=Notes&file=${relativeFile}`\"\"",
            "showTerminal": false,
        },
    },
```

Open terminal file in Obsidian
- [p] works with every markdown file
- [c] requires admin privileges for new vaults
- [GitHub - Yetenol/Obsidian-CLI](https://github.com/yetenol/obsidian-cli)

# Goal

- Open the current file in the other editor
- Use the same workplace folder / vault

# Technical difficulties

- Obsidian settings and plugins are stored in the workplace folder
- Obsidian is not designed for multiple vaults
- Obsidian's known vaults are stored in `$env:AppData\obsidian\obsidian.json`
- Create a new obsidian vault `obsidian://new?vault=my%20vault&path=path%2Fto%2Fmy%20note`



---
Sources:
- [Obsidian URI - Obsidian Help](https://help.obsidian.md/Extending+Obsidian/Obsidian+URI)

Related:
```dynamic-embed
[[List related notes]]
```

Tags:
[Obsidian](./computer/apps/Obsidian.md)
[Visual Studio Code](./computer/apps/Visual-Studio-Code.md)
[Markdown - Write content-focused and format with hierarchy, abstract highlighting, and meta-information](./Markdown.md)