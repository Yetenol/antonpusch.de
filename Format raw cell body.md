
# Number formattings

![table body number format.svg](./content/attachments/table%20body%20number%20format.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray,mathtools,tikz}
\renewcommand{\thetable}{2.1}
\UseTblrLibrary{siunitx}
\sisetup{exponent-product = \cdot}
\usetikzlibrary{fpu}
\begin{document}
\begin{tblr}[tall,caption=Number formats]{colspec={
    Q[r,cmd={\pgfmathprintnumber}]
    Q[r,cmd={\pgfkeys{/pgf/number format/.cd,sci}\pgfmathprintnumber}]
    Q[r,cmd={\pgfkeys{/pgf/number format/.cd,sci,sci subscript}\pgfmathprintnumber}]
    Q[r,cmd={\pgfkeys{/pgf/number format/.cd,frac}\pgfmathprintnumber}]
    Q[r,cmd={\num}]
},  hline{1,Z}={.08em},hline{3},
    rowhead = 2, hline{6,9,12,15,18}={dashed},
    hline{2}={1-Y}{leftpos=-2,rightpos=-2,endpos},
    hline{2}={Z}{leftpos=-1,rightpos=-1,endpos},
    row{1-2}={c,m,cmd={}}, cell{1}{1}={c=4}{},
}
PGF math print number                     &&&& SIunitx  \\
float    & sci      & {sci\\sub.} & frac     & num      \\
0.25     & 0.25     & 0.25        & 0.25     & 0.25     \\
-42      & -42      & -42         & -42      & -42      \\
289      & 289      & 289         & 289      & 289      \\
4225     & 4225     & 4225        & 4225     & 4225     \\
66049    & 66049    & 66049       & 66049    & 66049    \\
263169   & 263169   & 263169      & 263169   & 263169   \\
1.0563e6 & 1.0563e6 & 1.0563e6    & 1.0563e6 & 1.0563e6 \\
\end{tblr}
\end{document}
```
# Evaluate mathematical terms

![table body evaluate math.svg](./content/attachments/table%20body%20evaluate%20math.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray,tikz}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{2.2}
\begin{document}
$\begin{tblr}[tall,caption=Evaluate]{ 
    column{1}={r,rightsep=3pt},
    column{2}={l,cmd=\simeq\pgfmathprint,leftsep=0pt}, }
-1          & -1      \\
\pi         & pi      \\
\frac{2}{6} & 2/6     \\
\sqrt{2}    & sqrt(2) \\
13          & 13      \\
\end{tblr}$
\end{document}
```

# Print macros in table

![table body macro column.svg](./content/attachments/table%20body%20macro%20column.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\renewcommand{\thetable}{2.3\alph{table}}
\begin{document}
\begin{tblr}[ tall,caption, 
]{  colspec={rlcr}, hline{1,Z}={.08em}, hline{2},
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

![table body macro verbatim.svg](./content/attachments/table%20body%20macro%20verbatim.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray,codehigh,amsmath,graphics}
\renewcommand{\thetable}{2.3\alph{table}}\setcounter{table}{1}
\begin{document}
\includegraphics{table body macro column}
\hspace{1em}
\begin{tblr}[ tall, caption, baseline=B ]{  
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

![table body monospace.svg](./content/attachments/table%20body%20monospace.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\renewcommand{\thetable}{2.3\alph{table}}\setcounter{table}{2}
\begin{document}
\hspace{1em}
\begin{tblr}[tall, caption=Monospace ]{
    colspec={rl}, hline{1,Z}={.08em},hline{2},
    row{1}={font=\bfseries,halign=c}, 
    cell{2-Z}{1}={font=\ttfamily},  
}
command     & Description \\
calc        & Calculator \\
cmd         & Command Prompt \\
devmgmt.msc & Device Manager \\
\end{tblr}
\end{document}
```

- pgfmathparse
- texttt for commands
- dash 3rd line
- math, siunit, pgfmathparse, date, money, command, macro, bold, color, fraction styles
- dateformat, fraction format, yes/no symbol, 

# Complex evaluate, assign cell content with PgfPlotsTable

![table body pgfplotstable.svg](./content/attachments/table%20body%20pgfplotstable.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray,pgfplotstable,amsmath,amssymb,graphicx}
\renewcommand{\thetable}{2.4}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    numberic cells/.style = {numeric type, tblr={ column{1,Z}={r} }},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style={begin table=\begin{#1}{},end table=\end{#1},skip coltypes,environment/.style={}},
    caption/.style = {tblr outer={tall,caption={#1}}},
    hlines/.style={tblr={ hline{1,Z}={.08em},hline{2}={.05em} }},
    columns/Term/.style={string type, assign cell content/.style={/pgfplots/table/@cell content={ $##1$ }}},
    columns/Value/.style={assign cell content/.style={/pgfplots/table/@cell content={ \pgfmathprint{##1} }}},
}
\begin{document}
\includegraphics{table body evaluate math}
\hspace{1em}
\pgfplotstabletypeset[tex, numberic cells,hlines,caption,tblr={
    column{1}={r,rightsep=3pt},
    column{2}={l,mode=math,cmd=\simeq,leftsep=0pt},
    row{1}={c,mode=text,font=\bfseries,cmd={}}, baseline=b
}]{
    Term        & Value   \\
    -1          & -1      \\
    \pi         & pi      \\
    \frac{2}{6} & 2/6     \\
    \sqrt{2}    & sqrt(2) \\
    13          & 13      \\
}
\end{document}
```

# Figure collection for note preview

![table body.svg](./content/attachments/table%20body.svg)

```latex
\documentclass{article} \pagestyle{empty}
\usepackage{graphicx}
\begin{document}
\includegraphics{table body number format}
\begin{minipage}[b]{.5\textwidth} \centering{}
\includegraphics{table body evaluate math}

\vspace{1em}
\includegraphics{table body monospace}
\end{minipage}
\end{document}
```