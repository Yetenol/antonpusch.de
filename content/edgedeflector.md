---
title: "EdgeDeflector"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
not-in-use: true
microsoft-id: 
winget-id: da2x.edgedeflector
github-repo: da2x/EdgeDeflector
github-release-filename: EdgeDeflector_install.exe
website: 
priority: 
categories:
  - Personalization
---
---

EdgeDeflector is a **discarded** [personalization](install%20personalization%20apps.md.md) app. 

- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e da2x.edgedeflector
  ```
- Invoke the [installer](https://github.com/da2x/EdgeDeflector/releases/latest/download/EdgeDeflector_install.exe) from the latest release of its source code [repository](https://github.com/da2x/EdgeDeflector) on GitHub
  ```powershell
  Invoke-WebRequest 'https://github.com/da2x/EdgeDeflector/releases/latest/download/EdgeDeflector_install.exe' -OutFile "$env:Temp/EdgeDeflector_install.exe"
  if ($?) {Start-Process "$env:Temp/EdgeDeflector_install.exe"}
  ```

