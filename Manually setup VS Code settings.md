## Or setup manually

Enable auto save, to keep opened files synchronized with the drive.

```json
// AUTO SAVE - Keep opened files synchronized with the drive
"files.autoSave": "afterDelay",
```

Cleanup interface. Hide activity bar, editor tabs, menu bar.

```json
// CLEAN INTERFACE - Hide activity bar, editor tabs, menu bar
"workbench.activityBar.visible": false,
"workbench.editor.showTabs": false,
"window.menuBarVisibility": "compact",
```

Cleanup startup. Always start with an empty editor. Don't restore sessions.

```json
// CLEAN STARTUP - Always start with an empty editor. Don't restore sessions.
"window.restoreWindows": "none",
"workbench.startupEditor": "newUntitledFile",
```

```json
// CUSTOM INTERFACE - Put sidebar on the right, use system color theme, downscale interface, simplify minimap
"workbench.sideBar.location": "right",
"window.autoDetectColorScheme": true,
"window.zoomLevel": -0.5,
"editor.minimap.renderCharacters": false,
```

```json
{
    // AUTO SAVE - Keep opened files synchronized with the drive
    "files.autoSave": "afterDelay",
    // CLEAN INTERFACE - Hide activity bar, editor tabs, menu bar
    "workbench.activityBar.visible": false,
    "workbench.editor.showTabs": false,
    "window.menuBarVisibility": "compact",
    // CLEAN STARTUP - Always start with an empty editor. Don't restore sessions.
    "window.restoreWindows": "none",
    "workbench.startupEditor": "newUntitledFile",
    "workbench.colorTheme": "Default Light Modern",
    // CUSTOM INTERFACE - Put sidebar on the right, use system color theme, downscale interface, simplify minimap
    "workbench.sideBar.location": "right",
    "window.autoDetectColorScheme": true,
    "window.zoomLevel": -0.5,
    "editor.minimap.renderCharacters": false,
    // OTHER CHANGES
}
```

Import [settings.json](configs/VisualStudioCode-settings.json) to
```
%AppData%\Code\User\settings.json
```

Install extensions from a PowerShell
```powershell
code --install-extension cschlosser.doxdocgen
code --install-extension cssho.vscode-svgviewer
code --install-extension GitHub.vscode-pull-request-github
code --install-extension jeff-hykin.better-cpp-syntax
code --install-extension ms-vscode-remote.remote-containers
code --install-extension ms-vscode-remote.remote-ssh
code --install-extension ms-vscode-remote.remote-ssh-edit
code --install-extension ms-vscode-remote.remote-wsl
code --install-extension ms-vscode.cpptools
code --install-extension ms-vscode.cpptools-extension-pack
code --install-extension ms-vscode.cpptools-themes
code --install-extension thqby.vscode-autohotkey2-lsp
code --install-extension yzhang.markdown-all-in-one
```

---
Sources:

Related:

Tags:
[Visual Studio Code](./content/visual%20studio%20code.md)