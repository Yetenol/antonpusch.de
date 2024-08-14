---  
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
- Invoke the [installer of the latest release](https://github.com/efraimbart/OpenInWSA/releases/latest/download/OpenInWSA.exe) from [Github](https://github.com/efraimbart/OpenInWSA)  
  ```powershell  
  Invoke-WebRequest 'https://github.com/efraimbart/OpenInWSA/releases/latest/download/OpenInWSA.exe' -OutFile "$env:Temp/OpenInWSA.exe"  
  if ($?) {Start-Process "$env:Temp/OpenInWSA.exe"}  
  ```  
- Download it from the [publisher's website](https://chrome.google.com/webstore/detail/open-in-wsa/nkfpikoflncblmlajlcagaflndiijhhl)  
  
