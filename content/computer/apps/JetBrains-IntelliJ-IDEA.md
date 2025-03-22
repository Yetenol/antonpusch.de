---
date: "2025-03-22T23:45:55.004+01:00"
title: "JetBrains IntelliJ IDEA"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: true
microsoft-id: 
winget-id: JetBrains.IntelliJIDEA.Edu
link-modportals:
  - "[Marketplace](https://plugins.jetbrains.com/plugin/~modportal0-id~)"
website: https://www.jetbrains.com/education/download/#section=idea
categories:
  - Development
cssclasses:
  - cards
dg-content-classes:
  - cards
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

# Plugins

Perform action in command pallete `Shift Shift`
```
/Welcome screen/Plugins
```

```dynamic-embed
[[List extensions for this app]]
```

Or install manually
by performing the action in command pallete `Shift Shift`
```
/Welcome screen/Plugins
```


# Keyboard Shortcuts

Perform action in command palette `Shift Shift`
- Type action and press `Ctrl + .` to assign the keyboard shortcut:

| Keyboard shortcut             | Action                                         | Remove other <br> assignments? |
| ----------------------------- | ---------------------------------------------- | ------------------------------ |
| `Ctrl+Ö`                      | `/View/Tool Windows/Terminal`                  | no                             |
| `Ctrl+B`                      | `/Windows/Active Tool Window/Hide All Windows` | no                             |
| `Ctrl+Alt+G`                  | `/View/Tool Windows/Git`                       | no                             |
| `Ctrl+Shift+C`                | `/Git/ Commit`                                 | yes                            |
| `Ctrl+Alt+P`                  | `/Git/ Pull`                                   | yes                            |
| `Ctrl+ALt+Shift+P`            | `/Git/ Push`                                   | yes                            |
| `Ctrl+Alt+S`                  | `/Git/Uncommitted Changes/Stash Changes`       | yes                            |
| `Ctrl+ALt+Shift+S`            | `/Git/Uncommitted Changes/Unstash Changes`     | yes                            |
| `Ctrl+K, Right`               | `/Window/Editor Tabs/Split and Move Right`     | yes                            |
| `Ctrl+K, Down`                | `/Window/Editor Tabs/Split and Move Down`      | yes                            |
| `Ctrl+K, Ctrl+Number Sign(#)` | `/Code/Folding/Collapse Doc Comments`          |                                |

## Settings synchronization

- Open `Command Palette` via `[Ctrl + Shift + A]`
- Enter `/settings Settings Repository`
    - `https://github.com/Yetenol/IntelliJ-IDEA-Settings.git` =: Upstream URL
    - Click `Overwrite Local`

## Or setup manually

### Global Settings

> Open `Find Actions` via `[Ctrl + Shift + P]`
> - `Off` =: Enter `/View/Appearance Main Menu`

> Open `Settings` via `[Ctrl + Alt + S]`
>> Open `Keymap`
>> - `VSCode` =: Keymap
>
>> Open `Appearance & Behavior > Appearance`
>> - [x] Sync with OS _# Theme_
>> - Click Gear Icon
>>   - `One Dark Vivid` =: Dark
>
>> Open `Editor > General`
>>> Open `Editor Tabs`
>>> - `None` =: Tab placement
>>> - Apply
>>
>>> Open `Code Folding`
>>> - [x] Documentation comments _# General_
>
>> Open `Tools > Shared Indexes`
>> - `Download automatically` =: Download pre-built shared indexes to reduce indexing time
>
> - Apply & Save

### Defaults for Workplace Settings

- Open `Find Actions` via `[Ctrl + Shift + P]`
- Enter `/file Settings for New Projects...`

> Open `Verison Control`
>> Open `Confirmation`
>> - `Add silently` =: When files are created _# Confirmation_
>> - [x] Apply to files created outside IntelliJ IDEA _# Confirmation_
>> - `Remove silently` =: When files are deleted _# Confirmation_
>
>> Open `Git`
>> - [x] Auto-update if push of the current branch was rejected _# Push_
>> - [ ] Show Push dialog for Commit and Push _# Push_
>> - `Rebase` =: Update method _# Update_
>
> - Apply & Save


## Java Development Kit (JDK)

```powershell
winget install microsoft.openjdk.17
```
- JDK will be installed to `$env:JAVA_HOME`
- open any java project
- click on setup SDK
- wait a few seconds
- select detected SDK
