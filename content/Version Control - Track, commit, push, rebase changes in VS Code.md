---  
dg-publish: true  
cssclasses:  
  - cards  
dg-content-classes:  
  - cards  
---  
  
**Commit all** changed with specific message using `[ctrl+alt+c]`  
- very quick  
- enter commit message in a prompt instead of a file with setting `"git.useEditorAsCommitInput": false,`   
- Bind `ctrl+alt+c` to `Git: Commit All`  
  
**See changes** in source control side bar using `[ctrl+shift+g]`   
- see changed files  
- stage and unstage files  
  
Rebase and **publish** all local commit to the remote main branch using `[ctrl+shift+p]`  
- Install script [git-publish.ps1](https://github.com/Yetenol/alias)  
- Install extension [Terminal Command Keys](./Terminal%20Command%20Keys.md)  
- Bind `ctrl+shift+p` to execute `git-publish.ps1` in the terminal  
  
  
All keyboard shortcuts  
  
```json  
    {  
        "key": "ctrl+alt+c",  
        "command": "git.commitAll"  
    },  
    {  
        "key": "ctrl+shift+p",  
        "command": "terminalCommandKeys.run",  
        "args": {  
            "cmd": "\u0001git-publish.ps1"  
        },  
    },  
```  
  
All settings  
  
```json  
"git.useEditorAsCommitInput": false,  
```  
  
  
---  
Sources:  
  
Related:  
| Name                                                         | Thumbnail                                                                                                                                                 | Modportal links                                                                                                                                                              | Categories      | Description                                                                                                                |  
| ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------- |  
| **[Terminal Command Keys](./Terminal%20Command%20Keys.md)** | ![](https://cdn.vsassets.io/v/M226_20230814.3/_content/Header/default_icon_128.png)                                                                       | [Extensions](vscode:extension/petekinnecom.terminal-command-keys), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=petekinnecom.terminal-command-keys) | Version control | Assign terminal commands to a keybinding.                                                                                  |  
| **[Git rebase shortcut](./Git%20rebase%20shortcut.md)**     | ![](https://trentrand.gallerycdn.vsassets.io/extensions/trentrand/git-rebase-shortcuts/1.1.0/1613430968103/Microsoft.VisualStudio.Services.Icons.Default) | [Extensions](vscode:extension/trentrand.git-rebase-shortcuts), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=trentrand.git-rebase-shortcuts)         | Version control | Use keyboard shortcuts to quickly edit the actions of an interactive Git rebase.                                           |  
| **[Git Graph](./Git%20Graph.md)**                         | ![](https://mhutchie.gallerycdn.vsassets.io/extensions/mhutchie/git-graph/1.30.0/1617594001998/Microsoft.VisualStudio.Services.Icons.Default)             | [Extensions](vscode:extension/mhutchie.git-graph), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)                                 | Version control | View a Git Graph of your repository, and easily perform Git actions from the graph. Configurable to look the way you want! |  
  
  
Tags:  
[Visual Studio Code](./Visual%20Studio%20Code.md)  
  
