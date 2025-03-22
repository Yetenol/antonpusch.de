---
date: "2025-03-22T12:30:27.136+01:00"
title: "Customize Windows Settings"
description: "-"
dg-publish: true
dg-show-toc: true
dg-folder: computer
---

# System

## Display 

```
ms-settings:display
```

- Scale in Scale & layout: **125%**

## Display > Night light

```
ms-settings:nightlight
```

- Schedule night light: **true**

## Display > Graphics

```
ms-settings:display-advancedgraphics
```

- Let Minecraft's JRE use an external graphics card 
  - Add an app: **Desktop app**
  - Click **Browse** and open folder `%userprofile%\curseforge\minecraft\Install\runtime\`
  - Set the following applications to **High Performance**
```
java-runtime-alpha\windows-x64\java-runtime-alpha\bin\java.exe
java-runtime-alpha\windows-x64\java-runtime-alpha\bin\javaw.exe
java-runtime-beta\windows-x64\java-runtime-beta\bin\java.exe
java-runtime-beta\windows-x64\java-runtime-beta\bin\javaw.exe
jre-legacy\windows-x64\jre-legacy\bin\java.exe
jre-legacy\windows-x64\jre-legacy\bin\javaw.exe
jre-x64\bin\java.exe
jre-x64\bin\javaw.exe
```

## Notif‌ications & actions

```
ms-settings:notifications
```

- Snipping Tool in Notifications from apps and other senders: **false**

- Expand **Additional settings**
  - Show the Windows welcome experience after updates and when signed in to show what's new: **false**
and suggested
  - Suggest ways to get the most out of Windows and finish setting up this device: **false**
  - Get tips and suggestions when using Windows: **false**

## Power & sleep

```
ms-settings:powersleep
```

- Expand **Screen and sleep**
  - On battery power, turn off after: **10 minutes**
  - When plugged in, turn off after: **20 minutes**
  - On battery power, PC goes to sleep after: **15 minutes**
  - When plugged in, PC goes to sleep after: **Never**

## Storage

```
ms-settings:storagesense
```

- Storage sense: **true**
- Open **Storage sense**
  - Delete files in my Downloads folder if they haven't been opened for more than: **14 days**

## Multitasking

```
ms-settings:multitasking
```

- Pressing Alt + Tab shows: **Don't show tabs**

## Clipboard

```
ms-settings:clipboard
```

- Clipboard history: **true**
- Sync across your devices: **true**
  - Manually sync text that I copy: **true**

## About

```
ms-settings:about
```

- Rename your PC to a suitable name

# Bluetooth & devices

## Mouse > TrackPoint settings

1. Modern touchpad driver
```
ms-settings:mousetouchpad
```

- Setup **modern** touchpad driver
  - Click **TrackPoint settings** in ELAN TrackPoint for Thinkpad
  - Middle Button Action: **Middle click**

- Or setup **old** touchpad driver
  ```
  main.cpl
  ```
  - Open **ThinkPad** tab
  - Middle mouse click: **Use as middle click**

## Touchpad

```
ms-settings:devices-touchpad
```

- Expand **Three-finger gestures** in Gestures & interaction
    - Swipes: **Switch apps and show desktop**
    - Taps: **Middle mouse button**

- Expand **Four-finger gestures** in Gestures & interaction
    - Swipes: **Change audio and volume**
    - Taps: **Play/pause**

## Typing > Hardware keyboard

```
ms-settings:devicestyping-hwkbtextsuggestions
```

- Show text suggestions as I type on the physical keyboard: **true**

# Personalization

## Colors

```
ms-settings:personalization-colors
```

- Accent color: **Orange**

## Themes > Desktop icon settings

```
rundll32 shell32.dll,Control_RunDLL desk.cpl,null,0
```

- Recycle bin: **false**

## Taskbar

```
ms-settings:taskbar
```

- Expand **Taskbar items**
  - Task view: **false**
  - Chat: **false**
- Expand **Taskbar corner icon**
  - Pen Menu: **false**
  - Touch keyboard: **false**
- Expand **Other system tray icons**
  - Microsoft OneDrive: **true**
  - shortcutFox.exe: **true**
  - Disable everything else

Pin apps to taskbar
- Unpin all application
- Pin _Microsoft Edge_
- Pin _Visual Studio Code_
  - Open the following folder in _VS Code_ and trust their parent folder
  - `D:\WIKI\doc`
  - `D:\WIKI\Setup-Computer`
  - `D:\DEV\shortcutFox`
  - `D:\LATEX\LaTeX.equations`
  - `D:\LATEX\LaTeX.cleanSyntax`
  - Right-click _VS Code_ in the taskbar and pin the folders to the list 
- Pin _OneNote for Windows 10_
- Pin _File Explorer_
- Pin _Calendar_
- Pin _Mail_

# Apps

## Video playback

```
ms-settings:videoplayback	
```

- Process video automatically to enhance it (depends on your device hardware): **true**

# Time & language

## Typing > Advanced keyboard settings

```
ms-settings:typing
```

Hide the language swapper icon in the taskbbar
- Open **Advanced keyboard settings**
  - Use desktop language bar when it's available: **true**
  - Right-click the language bar in the upper-left corner of the screen
    - Click **Close the Language bar** and confirm the dialog
  - Open **Language bar options > Advanced Key Settings**
    - Set all sequences to **Not Assigned**

## Region > Additional date, time & regional settings

```
intl.cpl
```

- Format: **English (United States)**
- Click **Additional settings...**  
  - Open **Numbers** tab
    - Decimal symbol: `.`
    - Digit grouping symbol: `,`
    - List separator: `,`
  - Open **Date** tab
    - Short date: **yyyy-MM-dd**
  - Click **Apply** and **OK**
- Open **Administrative** tab
  - Click **Copy settings...** and confirm dialog
  - Welcome screen and system accounts: **true**
  - New user accounts: **true**
  - Click **OK** 

# Privacy & security

## Windows Security > Open Windows Security

```
windowsdefender:
```

- Open **Settings** in the bottom-left corner
- Open **Manage notifications**
- Recent activity and scan results: **false**

## For developers

```
ms-settings:developers
```

- Terminal: **Windows Terminal**


---


Sources:

Related:
[Computer - Setup my computers](./index.md)

Tags:
