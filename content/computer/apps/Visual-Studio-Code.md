---
date: "2025-03-22T23:47:56.269+01:00"
title: "Visual Studio Code"
description: "-"
dg-folder: computer/apps
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
  ```powershell
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

- Manually setup VS Code settings
- Manually setup VS Code keybindings

# List of referenced extensions

```dynamic-embed
[[List extensions for this app]]
```

---
Sources:

Related:

```dynamic-embed
[[List related notes]]
```

Tags:
