---
date: "2025-03-22T23:45:55.054+01:00"
title: "Visual Studio"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: 
microsoft-id: 
winget-id: Microsoft.VisualStudio.2022.Community --override "--quiet --add Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions"
github-repo: 
github-release-filename: 
website: https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=learn.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2022
priority: 
link-modportals:
  - "[View in marketplace](https://marketplace.visualstudio.com/items?itemName=~modportal0-id~)"
modportal0-id: 
thumbnail: 
categories:
  - Development
synopsis: 
extends-app: 
cssclasses:
  - cards
dg-content-classes:
  - cards
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

# Languages

- Create a new Blazor project

# Configure IDE

Change the following settings through Feature Search (Ctrl + Q) or though the menu.

Enable hot reload on file save:
- Open *Debugging > .NET / C++ Hot Reload*
- Apply Hot Reload on File Save: **true**

Enable format on save:
- *Text Editor > Code Cleanup >* Run Code Cleanup profile on Save: **true**

Auto save on focus change:
- *Environment > Documents* > Automatically save files when Visual Studio is in the background: **true**

Use VS Code key bindings:
- Open *Environment > Keyboard >* Change hotkeys and keyboard shortcuts
- Apply the following additional keyboard mapping scheme: **Visual Studio Code**


Skip start window and directly open solution:
- *Environment > General >* On startup, open: **Most recent solution**

Hide number of references above classes, properties
- Open *Text Editor > All Languages CodeLens >* Turn CodeLens on or off
- Enable CodeLens: **false**


Keep opening braces on the same line:
- Open *Text Editor > C# > Code Style > Formatting > New Lines >* New line formatting option for braces
- New line options for braces: *Set all to* **false**
- New line options for keywords: *Set all to* **false**

Don't automatically close HTML tags
- Open *Text Editor > HTML > Advanced*
- Auto insert closing tag: **false**
- Use legacy Razor editor for ASP.NET Core (requires restart): **true**
- Restart

Open *Environment > Keyboard >* Change hotkeys and **keyboard shortcuts**


Adopt system color theme:
- Install [Auto Theme Switcher - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=NickJohn.AutoThemeSwitcherForWin10DarkMode) 
- Open *Auto Theme Switcher for Win 10 > General*
- Light Theme: **Light**
- Dark Theme: **Dark**
- Open *Environment > General >* Change environment color themes
- Color Theme: *anything but system*

| Name                                                                           | Thumbnail                                                                                                                                                                                      | Modportal links                                                                                                                  | Categories | Description |
| ------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ---------- | ----------- |
| **[Roslynator 2022](./Roslynator-2022.md)**                               | ![](https://josefpihrt.gallerycdn.vsassets.io/extensions/josefpihrt/roslynator2022/4.13.0/1739135512551/Microsoft.VisualStudio.Services.Icons.Default)                                         | [View in marketplace](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2022)                             | \-         | \-          |
| **[Shrink Empty Lines 2022](./Shrink-Empty-Lines-2022.md)**               | ![](https://visualstudioplatformteam.gallerycdn.vsassets.io/extensions/visualstudioplatformteam/syntacticlinecompression2022/17.0/1630426367563/Microsoft.VisualStudio.Services.Icons.Default) | [View in marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.SyntacticLineCompression2022) | \-         | \-          |
| **[Solution Error Visualizer 2022](./Solution-Error-Visualizer-2022.md)** | ![](https://visualstudioplatformteam.gallerycdn.vsassets.io/extensions/visualstudioplatformteam/solutionerrorvisualizer2022/17.0/1649440970139/Microsoft.VisualStudio.Services.Icons.Default)  | [View in marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.SolutionErrorVisualizer2022)  | \-         | \-          |


---
Sources:

Related:

Tags:
ASP.NET Core Blazor