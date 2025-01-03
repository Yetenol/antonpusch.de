---
title: "Git"
date: "2024-09-29T00:00:00.000+02:00"
dg-publish: true
microsoft-id: 
winget-id: Git.Git
website: https://git-scm.com/download/win
priority: 1
categories:
  - Development
synopsis: Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
---

Git is a [essential](install%20essential%20apps.md.md), [development](install%20development%20apps.md.md) app. Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e Git.Git
  ```
- Download it from the [publisher's website](https://git-scm.com/download/win)


Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

# Modify installation

Rerun the installer `64-bit Git for Windows Setup` from the [Web](https://git-scm.com/download/win)
- Only show new options: **☐ No**
- Continue until `Select Components`
    - Windows Explorer integration: **☐ No**
    - (NEW!) Add a GIT Bash Profile to Windows Terminal: **☒ Yes**
- Continue until `Choosing the default editor used by Git`
    - choose **Use Visual Studio Code as Git's default editor**
- Continue until `Adjusting the name of the initial branch in new repositories`
    - Override the default branch name for new repositories: **☒ Yes**
    - Branch name: **main**
- Continue installation

# Setup profile

```powershell
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

## Setup communication

1. Open Git Bash

```powershell
& "$env:ProgramFiles\Git\bin\sh.exe" --login
```

2. **Generate** a new SSH key
    [🛈](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)  
    The public key is saved in the clipboard  

```bash
ssh-keygen -t ed25519 -C `hostname`
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
clip < ~/.ssh/id_ed25519.pub
```

3. **Register** the SSH key in the **GitHub** account
    [🛈](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)  
    - [add a new SSH key](https://github.com/settings/ssh/new)
    - [view already registered keys](https://github.com/settings/keys)

## Use existing repositories

> Fix error when using repositories from previous computers:  
> `fatal: detected dubious ownership in repository at '/media/data/users/jhu3szh/serialize'`

**Take ownership** of the **current** repository

```powershell
takeown /F ".\.git\" /R /SKIPSL
```

**Take ownership** of multiple **paths** and **subfolders**  
- Run elevated

```powershell
[string[]]@(
'D:\DEV\';
'D:\ICEBERG\';
'D:\LATEX\';
'D:\STUDIT\';
'D:\Notes\';
'D:\TUB';
'D:\WIKI\';
;) | foreach {
    takeown /F $_ /R /SKIPSL
}
```

**Pull** all child repositories

```powershell
Get-ChildItem -Path "." -Directory -Recurse | 
foreach { $_.FullName } | foreach {
    if (Test-Path -Path "$_\.git") {
        Write-Host "$_`t" -f Cyan -NoNewline
        git -C $_ pull
    }
}
```

---
Sources:

Related:
[Visual Studio Code](./visual-studio-code.md)

Tags:
