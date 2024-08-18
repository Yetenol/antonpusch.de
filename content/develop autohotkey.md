---
title: "Develop AutoHotkey - Program, compile, debug in VS Code"
dg-publish: true
cssclasses:
  - cards
dg-content-classes:
  - cards
---

# Build an executable

Install dependency **[AutoHotkey v2](https://www.autohotkey.com/)** by running
```powershell
winget install -e AutoHotkey.AutoHotkey --scope machine
```

Install dependency **[Ahk2Exe Compiler](https://www.autohotkey.com/docs/v2/Scripts.htm#ahk2exe)** by executing
```
%ProgramFiles%\AutoHotkey\UX\install-ahk2exe.ahk
```
- Or open *AutoHotkey Dash* and click `Compile`
- Confirm to download Ahk2Exe

**Build** an executable by pressing `[Ctrl+Shift+B]` to run build task
```powershell
& "$env:ProgramFiles\AutoHotkey\Compiler\Ahk2Exe.exe" /in source\main.ahk /out bin\shortcutFox.exe /icon source\icons\menu.ico /bin "$env:ProgramFiles\AutoHotkey\v2\AutoHotkey.exe"
```
```cmd
"%ProgramFiles%\AutoHotkey\Compiler\Ahk2Exe.exe" /in source\main.ahk /out bin\shortcutFox.exe /icon source\icons\menu.ico /bin "%ProgramFiles%\AutoHotkey\v2\AutoHotkey.exe"
```

**Start** shortcutFox from Windows Start or execute:
  ```powershell
  .\bin\shortcutFox.exe
	```
- Click `Reload` if prompted that the application is still running

# Develop and debug using Visual Studio Code

Add **language support** [AutoHotkey v2 Language Support](vscode:extension/thqby.vscode-autohotkey2-lsp)
- [p] features IntelliSense for AutoHotkey's functions and your's
- [p] features Rename Symbol

Make sure that the debugger always executes the main source file and not the currently opened one. 

- Unbind `ahk2: Debug Script` and `ahk2: Debug Script with Params` from `f5` and `shift+f5`

Add **debugging adapter** [vscode-autohotkey-debug](vscode:extension/zero-plusplus.vscode-autohotkey-debug)
- [p] features Breakpoints

The debug configuration file specifies which source file is the main file to compile from.

All keybinding shortcuts
```json
    {
        "key": "f5",
        "command": "-ahk2.debug",
        "when": "!inDebugMode && editorLangId == 'ahk2' && resourceScheme == 'file'"
    },
    {
        "key": "shift+f5",
        "command": "-ahk2.debug.params",
        "when": "editorLangId == 'ahk2' && resourceScheme == 'file'"
    },
```

---
Sources:

Related:
| Name                                                                           | Thumbnail                                                                                                                                                             | Modportal links                                                                                                                                                                    | Categories | Description                                                                                   |
| ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------------------------------------------------------------------------------------- |
| **[AutoHotkey v2 Language Support](./autohotkey%20v2%20language%20support.md)** | ![](https://thqby.gallerycdn.vsassets.io/extensions/thqby/vscode-autohotkey2-lsp/2.2.2/1698148424549/Microsoft.VisualStudio.Services.Icons.Default)                   | [Extensions](vscode:extension/thqby.vscode-autohotkey2-lsp), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=thqby.vscode-autohotkey2-lsp)                   | AutoHotkey | AutoHotkey v2 Language support for VS Code, features realization based on v2 syntax analysis. |
| **[vscode-autohotkey-debug](./vscode-autohotkey-debug.md)**               | ![](https://zero-plusplus.gallerycdn.vsassets.io/extensions/zero-plusplus/vscode-autohotkey-debug/1.11.0/1644570337107/Microsoft.VisualStudio.Services.Icons.Default) | [Extensions](vscode:extension/zero-plusplus.vscode-autohotkey-debug), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=zero-plusplus.vscode-autohotkey-debug) | AutoHotkey | Advanced debugging support for AutoHotkey(includes H) v1 and v2                               |


Tags:
[Visual Studio Code](./visual%20studio%20code.md)