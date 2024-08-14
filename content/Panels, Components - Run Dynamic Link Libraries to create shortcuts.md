---  
dg-publish: true  
---  
  
## Control Panels and their Tabs  
  
- **Control Panel**    
    `rundll32 Shell32.dll,Control_RunDLL`  
- **Control Panel** reload Applets    
    `rundll32 shell32.dll,Control_FillCache_RunDLL`  
- **Mouse** Properties (TrackPoint, TouchPad) &#127775;    
    `rundll32 Shell32.dll,Control_RunDLL main.cpl,@0`  
- **Keyboard** Properties    
    `rundll32 Shell32.dll,Control_RunDLL main.cpl,@1`  
- **Accessibility**    
    `rundll32 shell32.dll,Control_RunDLL access.cpl`  
- Programs    
    `appwiz.cpl`  
    - **Uninstall** or change a program &#127775;    
        `rundll32 shell32.dll,Control_RunDLL appwiz.cpl,null,0`  
    - **Install** a program from the **network**    
        `rundll32 shell32.dll,Control_RunDLL appwiz.cpl,null,1`  
    - Windows **Features** &#127775;    
        `rundll32 shell32.dll,Control_RunDLL appwiz.cpl,null,2`  
- **Display** (Settings App)    
    `desk.cpl`  
    - Desktop **Icon** Settings &#127775;    
        `rundll32 shell32.dll,Control_RunDLL desk.cpl,null,0`  
    - **Screen Saver** Settings    
        `rundll32 shell32.dll,Control_RunDLL desk.cpl,null,1`  
    - **Background** (Settings App)    
        `rundll32 shell32.dll,Control_RunDLL desk.cpl,null,2`  
- **Region**    
    `intl.cpl`  
    - **Formats** &#127775;    
        `rundll32 shell32.dll,Control_RunDLL intl.cpl,null,0`  
    - **Administrative**    
        `rundll32 shell32.dll,Control_RunDLL intl.cpl,null,1`  
- **Game** Controllers    
    `joy.cpl`  
- **Sound**    
    `mmsys.cpl`  
    - **Playback** &#127775;    
        `rundll32 shell32.dll,Control_RunDLL mmsys.cpl,null,0`  
    - **Recording** &#127775;    
        `rundll32 shell32.dll,Control_RunDLL mmsys.cpl,null,1`  
    - **Sounds**    
        `rundll32 shell32.dll,Control_RunDLL mmsys.cpl,null,2`  
- System **Properties**    
    `sysdm.cpl`  
    - **Computer Name**    
        `rundll32 shell32.dll,Control_RunDLL sysdm.cpl,null,1`  
    - **Hardware**    
        `rundll32 shell32.dll,Control_RunDLL sysdm.cpl,null,2`  
    - **Advanced** &#127775 (Performance, User Profiles, Startup and Recovery, Environment Variables)    
        `rundll32 shell32.dll,Control_RunDLL sysdm.cpl,null,3`  
    - System **Protection** &#127775; (Restore Point)    
        `rundll32 shell32.dll,Control_RunDLL sysdm.cpl,null,4`  
- Date and Time    
    `timedate.cpl`  
    - **Date and Time**    
        `rundll32 shell32.dll,Control_RunDLL timedate.cpl,null,0`  
    - Additional **Clocks**    
        `rundll32 shell32.dll,Control_RunDLL timedate.cpl,null,1`  
- **Security** and **Maintenance**    
    `wscui.cpl`  
    - **Security** Center    
        `rundll32 shell32.dll,Control_RunDLL wscui.cpl,Security Center`  
  
## Other Dynamic Link Libraries  
  
- **Lock** computer &#127775;    
    `rundll32 user32.dll,LockWorkStation`  
- **Hibernate** computer &#127775;    
    `rundll32 powrprof.dll,SetSuspendState`  
- **Safely remove** hardware    
    `rundll32 shell32.dll,Control_RunDLL hotplug.dll`  
- Create **shortcut** &#127775;    
    `rundll32 appwiz.cpl,NewLinkHere $destination`  
- Stored **User Names and Passwords** &#127775;    
    `rundll32 keymgr.dll,KRShowKeyMgr`  
- Open **Telnet** connection    
    `rundll32 url.dll,TelnetProtocolHandler $ipAddress`  
- Open a **URL**    
    `rundll32 url.dll,FileProtocolHandler $url`  
- Create **email**    
    `rundll32 url.dll,MailToProtocolHandler "mailto:$emailAddress`"`  
    - z.B. E-Mail Vorlage, nutze %20 als Leerzeichen    
        `rundll32 url.dll,MailToProtocolHandler "mailto:0?cc=1&?bcc=2&subject=3"`  
- **Folder** options    
    `rundll32 shell32.dll, Options_RunDLL 0`  
- Install from **INF** file    
    `rundll32 advpack.dll,LaunchINFSection $infFile,$section`  
- Install **screen saver**    
    `rundll32 desk.cpl,InstallScreenSaver $scrFile`  
- Run **Diskcopy**    
    `rundll32 diskcopy.dll,DiskCopyRunDLL $zeroOrOne`  
- Install from **INF** file    
    `rundll32 setupapi.dll,InstallHinfSection 132 $infFile`  
- **Open with** dialog    
    `rundll32 shell32.dll,OpenAs_RunDLL`  
- **Open with dialog** for a specific file &#127775;    
    `rundll32 shell32.dll,OpenAs_RunDLL $file`  
- **About** MZ/Windows (Version, OS Build)    
    `rundll32 Shell32.dll,ShellAboutA` or    
    `winver`  
- Add a **printer** dialog &#127775;    
    `rundll32 shell32.dll,SHHelpShortcuts_RunDLL AddPrinter`  
- **Printers Folder**    
    `rundll32 shell32.dll,SHHelpShortcuts_RunDLL PrintersFolder` or    
    `explorer shell:printersfolder`  
- Add **printer** without GUI &#127775; [(Details)](http://www.winfaq.de/faq_html/Content/tip2000/onlinefaq.php?h=tip2028.htm)    
    `rundll32 printui.dll,PrintUIEntry $options @$executable`  
    - i.e. add **network printer**    
        `rundll32 printui.dll,PrintUIEntry /q /in /n \\\\ServerName\Freigabename`  
- Show **fonts**    
    `rundll32 shell32.dll,SHHelpShortcuts_RunDLL FontsFolder`  
- Map network drive    
    `rundll32 shell32.dll,SHHelpShortcuts_RunDLL Connect`  
  
---  
Sources:  
- 2021-09-02: [Funktionen-Befehle der Dateien RUNDLL.EXE und RUNDLL32.EXE](http://www.winfaq.de/faq_html/Content/tip0500/onlinefaq.php?h=tip0564.htm)  
  
Related:  
  
Tags:  
[System components - Access settings panels, wizards, icons, consoles](./System%20components%20-%20Access%20settings%20panels,%20wizards,%20icons,%20consoles.md)  
