---
date: "2025-03-22T12:13:19.151+01:00"
title: "shortcutFox"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 
github-repo: Yetenol/shortcutFox
github-release-filename: shortcutFox.exe
priority: 1
categories:
  - Personalization
synopsis: ShortcutFox lists shortcuts, which can be easily customized with a json-like file, in the context menu of a system tray icon. Additionally, a few personalization tweaks are applied.
---

shortcutFox is a [essential](install%20essential%20apps.md.md), [personalization](install%20personalization%20apps.md.md) app. ShortcutFox lists shortcuts, which can be easily customized with a json-like file, in the context menu of a system tray icon. Additionally, a few personalization tweaks are applied.

- Invoke the [installer](https://github.com/Yetenol/shortcutFox/releases/latest/download/shortcutFox.exe) from the latest release of its source code [repository](https://github.com/Yetenol/shortcutFox) on GitHub
  ```powershell
  Invoke-WebRequest 'https://github.com/Yetenol/shortcutFox/releases/latest/download/shortcutFox.exe' -OutFile "$env:Temp/shortcutFox.exe"
  if ($?) {Start-Process "$env:Temp/shortcutFox.exe"}
  ```


# Select personalization tweaks

- Enable `Tray icon > Manage script... > Run at startup`
- Select favorite action via `Tray icon > Set left click action`
- Select favorite hotkeys via `Tray icon > Manage keyboard shortcuts`