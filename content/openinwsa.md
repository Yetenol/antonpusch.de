---
title: "OpenInWSA"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
not-in-use: true
microsoft-id: 
github-repo: efraimbart/OpenInWSA
github-release-filename: OpenInWSA.exe
website: https://chrome.google.com/webstore/detail/open-in-wsa/nkfpikoflncblmlajlcagaflndiijhhl
categories:
  - Subsystem
synopsis: Browser URL Handler for WSA apps
---

OpenInWSA is a **discarded** [subsystem](install%20subsystem%20apps.md.md) app. Browser URL Handler for WSA apps

- Invoke the [installer](https://github.com/efraimbart/OpenInWSA/releases/latest/download/OpenInWSA.exe) from the latest release of its source code [repository](https://github.com/efraimbart/OpenInWSA) on GitHub
  ```powershell
  Invoke-WebRequest 'https://github.com/efraimbart/OpenInWSA/releases/latest/download/OpenInWSA.exe' -OutFile "$env:Temp/OpenInWSA.exe"
  if ($?) {Start-Process "$env:Temp/OpenInWSA.exe"}
  ```
- Download it from the [publisher's website](https://chrome.google.com/webstore/detail/open-in-wsa/nkfpikoflncblmlajlcagaflndiijhhl)

