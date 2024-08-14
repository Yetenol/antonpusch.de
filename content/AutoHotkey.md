---  
dg-publish: true  
microsoft-id:   
winget-id: AutoHotkey.AutoHotkey --scope machine  
github-repo:   
github-release-filename:   
website: https://www.autohotkey.com/download/ahk-v2.exe  
priority: 10  
categories:  
  - Development  
synopsis: A scripting language to create hotkeys, interact with applications, manipulate windows, automate repetitive tasks and increase productivity and streamline tasks on Windows computers.  
---  
  
AutoHotkey is a scripting language primarily used for automating repetitive tasks and creating hotkeys (keyboard shortcuts) for Windows operating system. It can be used to automate tasks such as opening and closing programs, manipulating windows, filling out forms, sending keystrokes and mouse clicks, and more. Additionally, it can be used to create simple GUIs and games.  
  
AutoHotkey is a [development](install%20development%20apps.md.md) app. A scripting language to create hotkeys, interact with applications, manipulate windows, automate repetitive tasks and increase productivity and streamline tasks on Windows computers.   
- Invoke the installer listed on Windows Package Manager:  
  ```  
  winget install -e AutoHotkey.AutoHotkey --scope machine  
  ```  
- Download it from the [publisher's website](https://www.autohotkey.com/download/ahk-v2.exe)  
  
  
# Common use cases  
  
1.  Automating repetitive tasks at work or in personal life.  
2.  Creating custom keyboard shortcuts for frequently used commands.  
3.  Modifying or extending the functionality of existing software.  
4.  Creating simple GUI applications or games.  
5.  Making Windows accessibility adjustments for people with disabilities.  
  
## v2 Beta  
  
- setup **v2 Beta** using elevated [script](./attachments/Setup-AutoHotkey-2.ps1)  
  ```powershell  
  $url = 'https://raw.githubusercontent.com/Yetenol/Setup-Computer/main/script/Setup-AutoHotkey-2.ps1'  
  $command = "Invoke-Command -ScriptBlock ([ScriptBlock]::Create((Invoke-WebRequest -Uri $url)))"  
  Start-Process wt -Verb RunAs -ArgumentList "PowerShell.exe -NoExit -Command $command"  
  ```  
  
  
---  
Sources:  
  
Related:  
[Autohotkey - Interact with applications and streamline repetitive tasks](./Autohotkey%20-%20Interact%20with%20applications%20and%20streamline%20repetitive%20tasks.md)  
  
Tags: