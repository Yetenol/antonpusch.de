---
date: "2025-07-17T08:13:58.321+02:00"
title: "Invoke a shell command in VS Code's integrated terminal using a keybindung"
description: "-"
dg-publish: true
---

Add a custom key binding to invoke a certain shell command in Visual Studio's integrated terminal. 

# Implement natively

Clear the terminal's draft, paste a shell command and invoke it. Requires at least one integrated terminal to exist.

```json
{
    "key": "⟨keys⟩",
    "command": "workbench.action.terminal.sendSequence",
    "args": {
        "text": "\u0001⟨shell command⟩\u000D"
    },
    "when": "terminal.active"
},
```

- `⟨keys⟩`: key to trigger the keybinding like `ctrl+alt+r`
- `⟨shell command⟩`: command to execute like `git commit --amend`
- `\u0001` sends *Start of Heading* character to delete what is already draft in the terminal but not yet executed
- `\u000D` sends *Carriage Return* character to execute the inserted command.

# Implement using an extension

Add a custom key binding to invoke a certain shell command. Requires the extension [Terminal Command Keys](./computer/apps/Terminal-Command-Keys.md)

```json
{
    "key": "⟨keys⟩",
    "command": "terminalCommandKeys.run",
    "args": {
        "cmd": "⟨shell command⟩",
        "newTerminal": false,
        "saveAllFiles": true,
        "showTerminal": true,
        "focus": true,
    },
    // "when": "terminal.active"
},
```

- `⟨keys⟩`: key to trigger the keybinding like `ctrl+alt+r`
- `⟨shell command⟩`: command to execute like `git commit --amend`

---
Sources:

Related:

Tags:
[Visual Studio Code](./computer/apps/Visual-Studio-Code.md)
[Workflows - Improve workflow in applications](./Workflows.md)
[Terminal Command Keys](./computer/apps/Terminal-Command-Keys.md)