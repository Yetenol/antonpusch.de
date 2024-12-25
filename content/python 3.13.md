---
title: "Python 3.13"
dg-publish: true
not-in-use: 
microsoft-id: 
winget-id: Python.Python.3.13
github-repo: 
github-release-filename: 
website: https://www.python.org/downloads/
priority: 
link-modportals: 
modportal0-id: 
thumbnail: 
categories:
  - Development
synopsis: Python is a high-level, versatile programming language known for its clean syntax and readability, making it popular for everything from web development to data science and artificial intelligence.
extends-app: 
---

Python 3.13 is a [development](install%20development%20apps.md.md) app. Python is a high-level, versatile programming language known for its clean syntax and readability, making it popular for everything from web development to data science and artificial intelligence. 
- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e Python.Python.3.13
  ```
- Download it from the [publisher's website](https://www.python.org/downloads/)


Troubleshoot PATH setup
- [List all apps in PATH locations](./list%20all%20apps%20in%20path%20locations.md)

Find newest version
```powershell
winget search Python.Python
```

Install python in system-wide `%ProgramFiles%`
- Package installation will have to be privileged as well
```powershell
winget install -e Python.Python.3.13 --scope machine
```