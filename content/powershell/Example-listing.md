---
date: "2025-03-23T11:38:43.991+01:00"
title: "Example listing"
description: "Example code block for note preview"
dg-publish: true
dg-folder: powershell
---

![figure powershell listing.svg](../figure-powershell-listing.svg)

```latex
\documentclass{article} \title{powershell listing}
\usepackage{listings,xcolor}
\input{listings-styles} \input{listings-powershell} 
\begin{document}
\begin{lstlisting}[language=PowerShell,style=colorful]
Read-Host -AsSecureString | ConvertFrom-SecureString > "encrypted.txt"
[RegEx]::Match((Get-Date), '(\d+):(?<name>\d+)') | foreach { [PSCustomObject]@{
    FirstCaptureGroup = $_.Groups[1].value
    NamedCaptureGroup = $_.Groups["name"].value
}}
\end{lstlisting}
\end{document}
```

![figure powershell collection.svg](../figure-powershell-collection.svg)

```latex
\documentclass{standalone} \title{powershell collection}
\usepackage{graphbox}
\begin{document}
\includegraphics[align=c,width=2cm]{powershell logo} \hspace{1em}
\includegraphics[align=c]{figure powershell listing}
\end{document}
```