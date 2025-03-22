---
date: "2025-03-22T23:45:55.004+01:00"
title: "KeeWeb"
description: "-"
dg-folder: computer/apps
dg-publish: true
microsoft-id: 
winget-id: KeeWeb.KeeWeb
website: https://keeweb.info/
priority: 1
categories:
  - Storage
synopsis: Free cross-platform password manager compatible with KeePass
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

# Motivation

- moderne UI mit flexiblen Seitenverhältnisses des Fensters
- füge synchron getätigte Änderungen zusammen, ohne mehrere Dateien zu erstellen

- modern interface with flexible window aspects ratios
- native one-time-passwords feature
- native cloud synchronisation with common cloud providers
    - merge syncron

# Open cloud database

- Start the application
- Click `More > OneDrive`
  - If prompted allow access in Windows Defender Firewall for all networks
  - Authenticate using the browser
- Click `OneDrive` again and select the database
- Unlock the database
- Set sorting to Auto (click icon right of the search bar)

# Modify settings

Open **Settings** via `[Ctrl + ,]`

Open **Appearance** within General
- Automatically switch between light and theme when possible
- Colorful custom icons in the list

Open **Function** within General
- Automatically save and sync periodically: **On every change**
- Clear clipboard after copy: **In 10 seconds**
- Minimize the app instead of close: **☒ Yes**
- Minimize on field copy: **☒ Yes**
- Automatically use group icon for new entries: **☒ Yes**

Open **Auto lock** within General
- If the app is inactive: **In 5 minutes**
- When the app is minimized: **☐ No**
- When the computer is locked or put to sleep: **☒ Yes**

Open **Shortcuts**
 - copy OTP: **Ctrl + Alt + O**
 - open KeeWeb: **Ctrl + Alt + K**

Open your database settings, symbolized by a closed lock
 - File format: **KDBX 3** # Advanced

Open **Generate**, symbolized by a flash in the bottom right
- Open the dropdown menu and click `...`
- Click **New preset** and the bottom
- Selected by default: **☒ Yes**
- Name: **QWERTY/QWERTZ with 3 verify characters**
- Default length: **20**
- Additional symbols to include: `!$%.`
- Pattern: `XXXXXXXXXXXXXXXX.aaa`

Open **Browser**
- Select your browser and install its extension via the download icon
- In  your browser, enable KeeWeb Connect during InPrivate
- Navigate to the extension options or visit chrome-extension://pikpfmjfkekaeinceagbebpfkmkdlcjk/pages/options.html
- Click **Connect to KeeWeb**
- Click **Edit keyboard shortcuts** or visit about://extensions/shortcuts
- Choose another field in KeeWeb: **Ctrl + Shift + 2**
- One-time codes: **Ctrl + Shift + 1**
- Submit the form automatically: **Ctrl + Shift + V**

# Run at startup

```powershell
$WshShell = New-Object -comObject WScript.Shell
$Shortcut = $WshShell.CreateShortcut("$env:AppData\Microsoft\Windows\Start Menu\Programs\Startup\KeeWeb.lnk")
$Shortcut.TargetPath = "powershell.exe"
$Shortcut.Arguments = "-Command `"start 'C:\Program Files\KeeWeb\KeeWeb.exe' -WindowStyle Hidden`""
$Shortcut.WindowStyle = 7 # start minimized
$Shortcut.Save()
```


---
Sources:

Related:
```dynamic-embed
[[List related notes]]
```

Tags:
Password manager