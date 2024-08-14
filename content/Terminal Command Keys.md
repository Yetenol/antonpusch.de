---  
dg-publish: true  
not-in-use: false  
microsoft-id:   
winget-id:   
github-repo: petekinnecom/terminal-command-keys.git  
github-release-filename:   
website:   
priority:   
link-modportals:   
modportal0-id: petekinnecom.terminal-command-keys  
thumbnail: https://cdn.vsassets.io/v/M226_20230814.3/_content/Header/default_icon_128.png  
categories:  
  - Version control  
synopsis: |  
  Assign terminal commands to a keybinding.  
extends-app: "[[Visual Studio Code]]"  
---  
  
![thumbnail](https://cdn.vsassets.io/v/M226_20230814.3/_content/Header/default_icon_128.png)   
Terminal Command Keys is a [Visual Studio Code](./Visual%20Studio%20Code.md) extension about version control. Assign terminal commands to a keybinding.    
- Install extension via [Extensions](vscode:extension/petekinnecom.terminal-command-keys), [Web Marketplace](https://marketplace.visualstudio.com/items?itemName=petekinnecom.terminal-command-keys)  
- Download the [latest release](https://github.com/petekinnecom/terminal-command-keys.git/releases/latest) from [Github](https://github.com/petekinnecom/terminal-command-keys.git)  
  
  
Open current file in Obsidian using `[F10]`  
  
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
  
  
---  
Sources:  
  
Related:  
- [Obsidian as a markdown editor - Switch between Vscode and Obsidian](./Obsidian%20as%20a%20markdown%20editor%20-%20Switch%20between%20Vscode%20and%20Obsidian.md)  
- [Invoke a shell command in VS Code's integrated terminal using a keybindung](./Invoke%20a%20shell%20command%20in%20VS%20Code's%20integrated%20terminal%20using%20a%20keybindung.md)  
  
  
Tags:  
[Version Control - Track, commit, push, rebase changes in VS Code](./Version%20Control%20-%20Track,%20commit,%20push,%20rebase%20changes%20in%20VS%20Code.md)