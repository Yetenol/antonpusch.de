---
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
  ```
  winget install -e da2x.edgedeflector
  ```
- Invoke the [installer of the latest release](https://github.com/da2x/EdgeDeflector/releases/latest/download/EdgeDeflector_install.exe) from [Github](https://github.com/da2x/EdgeDeflector)
  ```powershell
  Invoke-WebRequest 'https://github.com/da2x/EdgeDeflector/releases/latest/download/EdgeDeflector_install.exe' -OutFile "$env:Temp/EdgeDeflector_install.exe"
  if ($?) {Start-Process "$env:Temp/EdgeDeflector_install.exe"}
  ```

