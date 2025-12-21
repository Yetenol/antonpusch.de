---
date: "2025-07-17T08:13:58.187+02:00"
title: "Format text"
description: "Style body text in monospace, macros with slash"
dg-publish: true
dg-folder: latex/tables
---

# Print macros in table

![figure table body macro column.svg](../../figure-table-body-macro-column.svg)

```latex
\documentclass{standalone} \title{table body macro column}
\renewcommand{\thetable}{3.1a}
\usepackage{tabularray}
\begin{document}
\begin{tblr}[tall,caption=Macro names]{  
    colspec={rlcr}, hline{1,Z}={.08em}, hline{2},
    column{1}={mode=math,rightsep=0pt},
    column{2}={preto=\textbackslash,font=\ttfamily,leftsep=2pt},
    row{1}={c,m,mode=text,font=\bfseries}, cell{1}{1}={c=2}{},
    cell{2-Z}{3}={preto={U+}}, 
}
Name          && Unicode & {Alt\\code} \\
\alpha & alpha & 03B1    & 224         \\
\gamma & gamma & 0393    & 226         \\
\delta & delta & 03B4    & 235         \\
\end{tblr}
\end{document}
```

Compare to cells with inline formatting

![figure table body macros.svg](../../figure-table-body-macros.svg)

```latex
\documentclass{standalone} \title{table body macro verbatim}
\renewcommand{\thetable}{3.1b}
\usepackage{tabularray,codehigh,amsmath}
\begin{document}
\begin{tblr}[tall, caption=Preformatted text]{  
    colspec={ll}, hline{1,Z}={.08em}, hline{2},
    row{1}={c,m,font=\bfseries},
}
{Lower\\case}              & {Upper\\case}                         \\
$\alpha$ \fakeverb{\alpha} & $A$ \fakeverb{A}                      \\
$\beta$  \fakeverb{\beta}  & $B$ \fakeverb{B}                      \\
$\gamma$ \fakeverb{\gamma} & 
    {$\Gamma$ \fakeverb{\Gamma}\\$\varGamma$ \fakeverb{\varGamma}} \\
$\delta$ \fakeverb{\delta} & 
    {$\Delta$ \fakeverb{\Delta}\\$\varDelta$ \fakeverb{\varDelta}} \\
\end{tblr}
\end{document}
```

```latex
\documentclass{standalone} \title{table body macros}
\usepackage{graphicx,graphbox}
\begin{document}
\includegraphics[align=c]{table body macro column} \hspace{1em}
\includegraphics[align=c]{table body macro verbatim}
\end{document}
```

# Glossary of commands in monospace

![figure table body monospace.svg](../../figure-table-body-monospace.svg)

```latex
\documentclass{standalone} \title{table body monospace}
\renewcommand{\thetable}{3.2}
\usepackage{tabularray}
\begin{document}
\begin{tblr}[tall, caption=Monospace]{
    colspec={rl}, hline{1,Z}={.08em},hline{2},
    row{1}={font=\bfseries,halign=c}, 
    cell{2-Z}{1}={font=\ttfamily},  
}
Command     & Description \\
calc        & Calculator \\
cmd         & Command Prompt \\
devmgmt.msc & Device Manager \\
\end{tblr}
\end{document}
```

# Colorful text, frames

![figure table text color.svg](../../figure-table-text-color.svg)

```latex
\documentclass{standalone} \title{table text color}
\renewcommand{\thetable}{3.3}
\usepackage{tabularray,tcolorbox}
\newtcbox{\xmybox}[1][red]{opacityback=0,on line,arc=6pt, 
    standard jigsaw, colframe=#1!50!black,boxrule=1pt,
    boxsep=0pt,left=5pt,right=5pt,top=3pt,bottom=3pt}
\begin{document}
\begin{tblr}[tall]{
    columns={c,m}, hline{1,Z}={.08em},hline{2},
    column{1}={l}, row{1}={c}, rows={ht=1.5em},
    %cell{2-Z}{2}={font=\ttfamily},
    cell{2-3}{3}={cmd=\xmybox[green]},
    cell{4,6}{3}={fg=gray},
    cell{5}{3}={cmd=\xmybox[red]},
}
Name            & ID     & Status  \\
Megan Johnson   & MD1319 & Active  \\
Charlotte Davis & GH1256 & Active  \\
Chloe Jones     & IN$7388$ & Archive \\
Emily Smith     & AU2431 & Blocked \\
Lucy Brown      & JW4939 & Archive \\
\end{tblr}
\end{document}
```

# Hyperlinks

![figure table text hyperlinks.svg](../../figure-table-text-hyperlinks.svg)

```latex
\documentclass{standalone} \title{table text hyperlinks}
\renewcommand{\thetable}{3.4}
\usepackage{tabularray,hyperref}
\hypersetup{colorlinks,linkcolor=blue}
\begin{document}
\begin{tblr}[tall]{
    columns={c,m}, hline{1,Z}={.08em},hline{2},
}
Name            & ID     & Homepage  \\
Megan Johnson   & MD1319 & \href{https://en.wikipedia.org/wiki/Amirhossein_Nikpour}{Amirhossein Nikpour - Wikipedia}  \\
Charlotte Davis & GH1256 & \url{https://en.wikipedia.org/wiki/Diyaluma_Falls}   \\
Hannah Wilson   & EU1173 &   \\
Chloe Jones     & GN7388 &  \\
Lucy Brown      & JW4939 &  \\
Emily Smith     & AU2431 &  \\
Jessica Miller  & MC2798 &  \\
Sophie Williams & WR8993 &  \\
\end{tblr}
\end{document}
```

# Figure collection for note preview

![figure table text formatting.svg](../../figure-table-text-formatting.svg)

```latex
\documentclass{standalone} \title{table text formatting}
\usepackage{graphicx,graphbox}
\begin{document}
\includegraphics[align=c]{figure table body monospace} \hspace{1em}
\includegraphics[align=c]{figure table text color} \hspace{1em}
\includegraphics[align=c]{figure table body macro verbatim}
\end{document}
```
