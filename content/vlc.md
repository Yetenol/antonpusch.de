---
title: "VLC"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
microsoft-id: 
winget-id: VideoLAN.VLC
website: https://www.videolan.org/vlc/
priority: 10
categories:
  - Entertainment
synopsis: VLC is a free and open source cross-platform multimedia player and framework that plays most multimedia files as well as DVDs, Audio CDs, VCDs, and various streaming protocols.
---

VLC is a [entertainment](install%20entertainment%20apps.md.md) app. VLC is a free and open source cross-platform multimedia player and framework that plays most multimedia files as well as DVDs, Audio CDs, VCDs, and various streaming protocols.

- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e VideoLAN.VLC
  ```
- Download it from the [publisher's website](https://www.videolan.org/vlc/)


If installed through winget and dialog `Privacy and Network Access Policy` appears
- [ ] Regularly check for VLC updates 

Open `Preferences` [Ctrl + P]
- Open `Interface` tab 
- `Always` =: Continue playback? _<[#Playlist and Instances]>_

Open `Subtitles / OSD`
- [ ] Show media title on video start _# On Screen Display_
- click `Save`

Fix **Youtube stream** playback    
```powershell
$url = "https://code.videolan.org/videolan/vlc/-/raw/master/share/lua/playlist/youtube.lua?inline=false"
$path = "C:\Program Files\VideoLAN\VLC\lua\playlist\youtube.luac"
New-Item -Path $path -Force -ErrorAction Stop
Invoke-WebRequest -Uri $url -OutFile $path -ErrorAction Stop
```
