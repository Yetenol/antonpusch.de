---
title: "Format text - Style body text in monospace, macros with slash"
dg-publish: true
---
# Print macros in table

![table body macro column.svg](./attachments/table%20body%20macro%20column.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\renewcommand{\thetable}{3.1\alph{table}}
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

![table body macros.svg](./attachments/table%20body%20macros.svg)

```latex
\documentclass{standalone} \usepackage{graphicx,graphbox}
\begin{document}
\includegraphics[align=c]{table body macro column} \hspace{1em}
\includegraphics[align=c]{table body macro verbatim}
\end{document}
```

```latex
\documentclass{standalone}
\usepackage{tabularray,codehigh,amsmath}
\renewcommand{\thetable}{3.1\alph{table}}\setcounter{table}{1}
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

# Glossary of commands in monospace

![table body monospace.svg](./attachments/table%20body%20monospace.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\renewcommand{\thetable}{3.2}
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

# Figure collection for note preview

![table text formatting.svg](./attachments/table%20text%20formatting.svg)

```latex
\documentclass{standalone} \usepackage{graphicx,graphbox}
\begin{document}
\includegraphics[align=c]{table body macro verbatim} \hspace{1em}
\includegraphics[align=c]{table body monospace}
\end{document}
```