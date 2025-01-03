---
title: "PowerToys"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
microsoft-id: xp89dcgq3k6vld
winget-id: Microsoft.PowerToys
github-repo: microsoft/PowerToys
priority: 3
categories:
  - Personalization
---

PowerToys is a [personalization](install%20personalization%20apps.md.md) app. 

- Open in [Microsoft Store](ms-windows-store://pdp/?ProductId=XP89DCGQ3K6VLD&mode=mini) or invoke:
  ```
  winget install -e XP89DCGQ3K6VLD --accept-package-agreements
  ```
- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e Microsoft.PowerToys
  ```
- Download the [latest release](https://github.com/microsoft/PowerToys/releases/latest) of its source code [repository](https://github.com/microsoft/PowerToys) on GitHub


- Open `PowerToys Settings` by launching the application twice
- Open `File Explorer add-ons`
  - [x] Enable PDF (.pdf) preview _# Preview Pane_
  - [x] Enable PDF (.pdf) thumbnails _# Icon Preview_
- Open `Mouse utilities`
  - `Shake mouse` ← Activation method _# Find My Mouse_
  - [x] Enable Mouse Pointer Crosshairs _# Mouse Pointer Crosshairs_
- Open `FancyZones`
  - Open `Zone behavior` _# Zones_
    - [x] Use a non-primary mouse button to toggle zone activation
    - `Activate the zone whose center is closest to the cursor` ← When multiple zones overlap
  - Open `Zone appearance` _# Zones_
    - [ ] Show zone number
  - Open `Window behavior` _# Windows_
    - [x] Disable round corners when window is snapped
  - [x] Override Windows Snap _# Windows_
- Open `Screen Ruler`
  - [x] Enable Screen Ruler
