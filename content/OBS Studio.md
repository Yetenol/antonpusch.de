---
dg-publish: true
microsoft-id: XPFFH613W8V6LV
winget-id: OBSProject.OBSStudio
github-repo: obsproject/obs-studio
github-release-filename: 
website: https://obsproject.com/
priority: 10
categories:
  - Entertainment
synopsis: OBS Studio - Free and open source software for live streaming and screen recording
---

OBS Studio is a [entertainment](install%20entertainment%20apps.md.md) app. OBS Studio - Free and open source software for live streaming and screen recording 
- Open in [Microsoft Store](ms-windows-store://pdp/?ProductId=XPFFH613W8V6LV&mode=mini) or invoke:
  ```
  winget install -e XPFFH613W8V6LV --accept-package-agreements
  ```
- Invoke the installer listed on Windows Package Manager:
  ```
  winget install -e OBSProject.OBSStudio
  ```
- Download the [latest release](https://github.com/obsproject/obs-studio/releases/latest) from [Github](https://github.com/obsproject/obs-studio)
- Download it from the [publisher's website](https://obsproject.com/)


# Output in display resolution

Open `File > Settings > Video`
- `1920x1080` =: Base (Canvas) Resolution
- `1920x1080` =: Output (Scaled) Resolution
- `24 NTSC` =: Common FPS Values

Open `Files > Settings > Hotkeys`
- `POS1` =: Start Recording
- `ENDE` =: Stop Recording

# Capture DRM protected video and sound

- Use Firefox to play the video
- Click plus icon in OBS's Source dialog
- Choose `Display Capture`

# Play and pause browser with keyboard

- If there is a function key for playing and pausing media, use it
- Otherwise install [SharpKeys](./SharpKeys.md)
- Rebind `Caos Lock` to `Media: Play/Pause`



---
Sources:

Related:
- [Capture, record DRM protected video with OBS](Capture,%20record%20DRM%20protected%20video%20with%20OBS.md)


Tags:
