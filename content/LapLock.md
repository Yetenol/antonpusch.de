---
dg-publish: true
not-in-use: true
microsoft-id: 
github-repo: dechamps/laplock
github-release-filename: laplock.exe
categories:
  - Personalization
---

LapLock is a **discarded** [personalization](install%20personalization%20apps.md.md) app.  
- Invoke the [installer of the latest release](https://github.com/dechamps/laplock/releases/latest/download/laplock.exe) from [Github](https://github.com/dechamps/laplock)
  ```powershell
  Invoke-WebRequest 'https://github.com/dechamps/laplock/releases/latest/download/laplock.exe' -OutFile "$env:Temp/laplock.exe"
  if ($?) {Start-Process "$env:Temp/laplock.exe"}
  ```

