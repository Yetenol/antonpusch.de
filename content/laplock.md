---
title: "LapLock"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
not-in-use: true
microsoft-id: 
github-repo: dechamps/laplock
github-release-filename: laplock.exe
categories:
  - Personalization
---

LapLock is a **discarded** [personalization](install%20personalization%20apps.md.md) app. 

- Invoke the [installer](https://github.com/dechamps/laplock/releases/latest/download/laplock.exe) from the latest release of its source code [repository](https://github.com/dechamps/laplock) on GitHub
  ```powershell
  Invoke-WebRequest 'https://github.com/dechamps/laplock/releases/latest/download/laplock.exe' -OutFile "$env:Temp/laplock.exe"
  if ($?) {Start-Process "$env:Temp/laplock.exe"}
  ```

