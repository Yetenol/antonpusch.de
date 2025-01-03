---
title: "Visual Studio Code"
dg-publish: true
microsoft-id: XP9KHM4BK9FZ7Q
winget-id: Microsoft.VisualStudioCode --scope machine
github-repo: 
github-release-filename: 
website: https://code.visualstudio.com/#alt-downloads
priority: 1
link-modportals:
  - "[Extensions](vscode:extension/~modportal0-id~)"
  - "[Web Marketplace](https://marketplace.visualstudio.com/items?itemName=~modportal0-id~)"
modportal0-id: 
thumbnail: 
categories:
  - Development
aliases:
  - VS Code
synopsis: Visual Studio Code is a free, lightweight, and extensible code editor for building web, desktop, and mobile applications, using any programming language and framework.
cssclasses:
  - cards
dg-content-classes:
  - cards
---

Visual Studio Code also called VS Code is a [essential](install%20essential%20apps.md.md), [development](install%20development%20apps.md.md) app. Visual Studio Code is a free, lightweight, and extensible code editor for building web, desktop, and mobile applications, using any programming language and framework.

  - Open in [Microsoft Store](ms-windows-store://pdp/?ProductId=XP9KHM4BK9FZ7Q&mode=mini) or invoke:
  ```
  winget install -e XP9KHM4BK9FZ7Q --accept-package-agreements
  ```
- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e Microsoft.VisualStudioCode --scope machine
  ```
- Download it from the [publisher's website](https://code.visualstudio.com/#alt-downloads)


Visual Studio Code has built-in support for Git source control management and powerful integrations with GitHub, an integrated debugger, and smart code completion with IntelliSense and with AI-driven IntelliCode. With over 30,000 extensions and themes in the Visual Studio Code Marketplace, you can customize the features and the look of Visual Studio Code to fit your needs, preferences, and style.

You can use Visual Studio Code to build any kind of app, for web, desktop, and mobile. Visual Studio Code supports JavaScript and TypeScript natively and offers extensions for coding in languages such as Python, Java, C/C++, C#, Go, Rust, PHP, and many more.

# Add Windows Explorer context menu entries

Rerun the installer `System Installer 64-bit` from the [Web](https://code.visualstudio.com/#alt-downloads)
- Continue until `Select Additional Tasks`
- [x] Add "Open with Code" action to Windows file context menu
- [x] Add "Open with Code" action to Windows directory context menu

# Settings synchronization

- Open Command Palette via `[Ctrl + Shift + P]`
- Enter `Settings Sync: Turn On`
    - [ ] UI State
    - Click `Sign in & Turn on`
    - Sign in using Github

- [Manually setup VS Code settings](Manually%20setup%20VS%20Code%20settings.md)
- [Manually setup VS Code keybindings](Manually%20setup%20VS%20Code%20keybindings.md)

# List of referenced extensions

| Name                                                                           | Thumbnail                                                                                                                                                             | Modportal links                                                                                                                                                                    | Categories      | Description                                                                                                                |
| ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **[C, C++](./c%20c++.md)**                                                 |                                                                                                                                                                       | [Extensions](vscode:extension/ms-vscode.cpptools), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)                                       | \-              | C/C++ IntelliSense, debugging, and code browsing.                                                                          |
| **[CMake Tools](./cmake%20tools.md)**                                       |                                                                                                                                                                       | [Extensions](vscode:extension/ms-vscode.cmake-tools), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)                                 | \-              | Compile C projects using cmake                                                                                             |
| **[Change Case](./change%20case.md)**                                       | ![](https://cdn.vsassets.io/v/M226_20230814.3/_content/Header/default_icon_128.png)                                                                                   | [Extensions](vscode:extension/FinnTenzor.change-case), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=FinnTenzor.change-case)                               | \-              | Quickly change the case with one keybinding                                                                                |
| **[SmallOnlineTools](./smallonlinetools.md)**                             | ![](https://harveenatwal.gallerycdn.vsassets.io/extensions/harveenatwal/vscode-webtilities/3.1.1/1721716153159/Microsoft.VisualStudio.Services.Icons.Default)         | [Extensions](vscode:extension/HarveenAtwal.vscode-webtilities), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=HarveenAtwal.vscode-webtilities)             | \-              | Your one-stop shop for a wide range of easy-to-use online tools to simplify your daily tasks.                              |
| **[AutoHotkey v2 Language Support](./autohotkey%20v2%20language%20support.md)** | ![](https://thqby.gallerycdn.vsassets.io/extensions/thqby/vscode-autohotkey2-lsp/2.2.2/1698148424549/Microsoft.VisualStudio.Services.Icons.Default)                   | [Extensions](vscode:extension/thqby.vscode-autohotkey2-lsp), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=thqby.vscode-autohotkey2-lsp)                   | AutoHotkey      | AutoHotkey v2 Language support for VS Code, features realization based on v2 syntax analysis.                              |
| **[vscode-autohotkey-debug](./vscode-autohotkey-debug.md)**               | ![](https://zero-plusplus.gallerycdn.vsassets.io/extensions/zero-plusplus/vscode-autohotkey-debug/1.11.0/1644570337107/Microsoft.VisualStudio.Services.Icons.Default) | [Extensions](vscode:extension/zero-plusplus.vscode-autohotkey-debug), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=zero-plusplus.vscode-autohotkey-debug) | AutoHotkey      | Advanced debugging support for AutoHotkey(includes H) v1 and v2                                                            |
| **[Terminal Command Keys](./terminal%20command%20keys.md)**                   | ![](https://cdn.vsassets.io/v/M226_20230814.3/_content/Header/default_icon_128.png)                                                                                   | [Extensions](vscode:extension/petekinnecom.terminal-command-keys), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=petekinnecom.terminal-command-keys)       | Version control | Assign terminal commands to a keybinding.                                                                                  |
| **[Git Graph](./git%20graph.md)**                                           | ![](https://mhutchie.gallerycdn.vsassets.io/extensions/mhutchie/git-graph/1.30.0/1617594001998/Microsoft.VisualStudio.Services.Icons.Default)                         | [Extensions](vscode:extension/mhutchie.git-graph), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)                                       | Version control | View a Git Graph of your repository, and easily perform Git actions from the graph. Configurable to look the way you want! |
| **[Git rebase shortcut](./git%20rebase%20shortcut.md)**                       | ![](https://trentrand.gallerycdn.vsassets.io/extensions/trentrand/git-rebase-shortcuts/1.1.0/1613430968103/Microsoft.VisualStudio.Services.Icons.Default)             | [Extensions](vscode:extension/trentrand.git-rebase-shortcuts), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=trentrand.git-rebase-shortcuts)               | Version control | Use keyboard shortcuts to quickly edit the actions of an interactive Git rebase.                                           |
| **[Auto Hide](./auto%20hide.md)** ⊘ Discarded                               | ![](https://sirmspencer.gallerycdn.vsassets.io/extensions/sirmspencer/vscode-autohide/1.0.8/1687724162504/Microsoft.VisualStudio.Services.Icons.Default)              | [Extensions](vscode:extension/sirmspencer.vscode-autohide), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=sirmspencer.vscode-autohide)                     | \-              | A tool to autohide the sidebar and terminal panel.                                                                         |


---
Sources:

Related:

- [Git](./git.md)
- [Version Control - Track, commit, push, rebase changes in VS Code](./version%20control.md)
- [Pandoc - Convert markup languages context aware with pandoc filters](Pandoc%20-%20Convert%20markup%20languages%20context%20aware%20with%20pandoc%20filters.md)
- [Develop AutoHotkey - Program, compile, debug in VS Code](./develop%20autohotkey.md)
- [Obsidian as a markdown editor - Switch between Vscode and Obsidian](./obsidian%20as%20a%20markdown%20editor.md)
- [Develop more efficiently in VS Code](Develop%20more%20efficiently%20in%20VS%20Code.md)
- [Settings backup of VS Code](Settings%20backup%20of%20VS%20Code.md)
- [Invoke a shell command in VS Code's integrated terminal using a keybindung](./invoke%20a%20shell%20command%20in%20vs%20code's%20integrated%20terminal%20using%20a%20keybindung.md)


Tags:
