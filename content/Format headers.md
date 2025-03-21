---
publish: true
---

# Pet Owners

![figure pet owners.svg](./attachments/figure%20pet%20owners.svg)

```latex
\documentclass{standalone} \title{pet owners}
\renewcommand{\thetable}{1.1}
\usepackage{tabularray}
\begin{document}
\noindent
\begin{tblr}[tall,caption=Pet Owners]{
  colspec={lrrrr},
  hline{1,Z}={.08em}, hline{3},
  column{1}={halign=l,cmd=\quad},
  row{3-Z}={,rowsep=0pt}, row{3}={abovesep=2pt},
  row{3,6}={font=\bfseries,cmd={},abovesep=6pt,belowsep=2pt},
  cell{1}{2,4}={c=2}{c}, row{1-2}={halign=c},
  cell{1-2}{1}={l,cmd={}},
  column{4}={leftsep+=6pt},
  hline{2} = {2-3}{leftpos = -1, rightpos = -1, endpos},
  hline{2} = {4-5}{leftpos = -1, rightpos = -1, endpos},
}
          & Dogs &    & Cats &    \\
Owner     & M    & F  & M    & F  \\
Age                               \\
$< 18$    & 2    & 12 & 7    & 11 \\
$\ge 18$  & 4    & 44 & 5    & 3  \\
Residence                         \\
Urban     & 43   & 46 & 15   & 33 \\
Rural     & 5    & 12 & --   & 14 \\
\end{tblr}
\end{document}
```

# Comparison

- Beware: Rotated title clips out of table

![figure comparison table 1.svg](./attachments/figure%20comparison%20table%201.svg)

```latex
\documentclass{standalone} \title{comparison table 1}
\renewcommand{\thetable}{1.2}
\usepackage{tabularray,rotating,makecell}
\setlength\rotheadsize{1.25cm}
\renewcommand\theadfont{}
\NewDocumentCommand{\rot}{O{45} O{1em} m}{\makebox[#2][l]{\rotatebox{#1}{#3}}}%
\begin{document}
\begin{tblr}[tall, caption=Comparison, 
    note{a}={Collaborate live with team members on the same document}
]{  colspec={lcc}, hline{1,Z}={.08em}, hline{2}, 
    cell{1}{2-Z} = {halign=l,cmd=\rot[45][1em]},
    column{1}={rightsep+=4pt}, column{Z}={rightsep+=12pt},
    cell{2-Z}{2-Z}={mode=math,cmd=\mathrm}, 
    cell{2}{1}={appto=\TblrNote{a}},
}
Aspect    & Overleaf & Obsidian \\
Collab.   & ++       & --       \\
Price     & o        & +        \\
Feautures & ++       & +        \\
\end{tblr}
\end{document}
```

# Two dimensional table

- To dynamically calculate the sum, see [Calculate statistics for table numbers](./Calculate%20statistics%20for%20table%20numbers.md)

![figure probabilities table 1.svg](./attachments/figure%20probabilities%20table%201.svg)

```latex
\documentclass{standalone} \title{probabilities table 1}
\renewcommand{\thetable}{1.3a}
\usepackage{tabularray}
\UseTblrLibrary{diagbox}
\let\oldfrac\frac
\renewcommand{\frac}[2]{\mathchoice 
    {\oldfrac{#1}{#2}} {{^{#1}\!/_{\!#2}}}
    {\oldfrac{#1}{#2}} {\oldfrac{#1}{#2}}  }
\begin{document}
$\begin{tblr}[tall,caption=Probabilities,
    remark{$x$}={horizontal axis}, remark{$y$}={vertical axis} 
]{  hline{2}={2-Z}{}, vline{2}={2-Z}{}, hline{Y}, vline{Y}, 
    column{1-Z}={c}, column{1}={colsep=2pt},
    cell{1}{1}={preto={\diagbox}}, 
    cell{1,Z}{1,Z}={font=\boldmath},
}
{x}{y} & 0            & 1            & 2            & \Sigma      \\
0      & \frac{1}{16} & \frac{1}{16} & 0            & \frac{1}{8} \\
1      & \frac{2}{16} & \frac{3}{16} & \frac{1}{16} & \frac{3}{8} \\
2      & \frac{1}{16} & \frac{3}{16} & \frac{2}{16} & \frac{3}{8} \\
3      & 0            & \frac{1}{16} & \frac{1}{16} & \frac{1}{8} \\
\Sigma & \frac{1}{4}  & \frac{1}{2}  & \frac{1}{4}  & 1           \\
\end{tblr}$
\end{document}
```

## More variants

![figure probabilities table.svg](./attachments/figure%20probabilities%20table.svg)

Separate the sum row and column with more spacing instead of additional border lines

```latex
\documentclass{standalone}  \title{probabilities table 2}
\renewcommand{\thetable}{1.3b}
\usepackage{tabularray}
\let\oldfrac\frac
\renewcommand{\frac}[2]{\mathchoice 
    {\oldfrac{#1}{#2}} {{^{#1}\!/_{\!#2}}}
    {\oldfrac{#1}{#2}} {\oldfrac{#1}{#2}}  }
\newcommand{\diagtext}[2]{
    {_{\displaystyle{#1}}\,^{\displaystyle{#2}}}  }
\begin{document}
$\begin{tblr}[tall,caption={Combined row,\\ column title cell},
    remark{$x$}={horizontal axis}, remark{$y$}={vertical axis} 
]{  hline{1,Z}={.08em}, hline{2}={leftpos=-7,endpos},
    column{1-Z}={c}, column{1}={colsep=2pt},
    row{Z}={abovesep+=6pt}, column{Z}={leftsep+=6pt},
    cell{1}{1}={preto=\diagtext},
    cell{1}{Z}={h}, cell{Z}{1}={l},
    cell{1,Z}{1,Z}={font=\boldmath},
}
{x}{y} & 0 & 1 & 2 & \Sigma \\
0      & \frac{1}{16} & \frac{1}{16} & 0            & \frac{1}{8} \\
1      & \frac{2}{16} & \frac{3}{16} & \frac{1}{16} & \frac{3}{8} \\
2      & \frac{1}{16} & \frac{3}{16} & \frac{2}{16} & \frac{3}{8} \\
3      & 0            & \frac{1}{16} & \frac{1}{16} & \frac{1}{8} \\
\Sigma & \frac{1}{4}  & \frac{1}{2}  & \frac{1}{4}  & 1           \\
\end{tblr}$
\end{document}
```

Don't combine $x$ and $y$ in the same diagbox cell

```latex
\documentclass{standalone} \title{probabilities table 3}
\renewcommand{\thetable}{1.3c}
\usepackage{tabularray}
\begin{document}
$\begin{tblr}[tall,caption=No diagbox,
    remark{$x$}={horizontal axis}, remark{$y$}={vertical axis} 
]{  hline{1,Z}={.08em}, hline{2},
    column{1-Z}={c}, column{1}={colsep=2pt},
    row{Z}={abovesep+=6pt}, column{Z}={leftsep+=6pt},
    cell{1}{1,Z}={h,font=\boldmath}, cell{2,Z}{1}={l,font=\boldmath},
    row{1}={ht=1.8em}, cell{1}{2-Y}={f}
}
y= & 0 & 1 & 2 & \Sigma \\
x= \\
0  & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & 0              & ^1{\!/\!}_{8} \\
1  & ^2{\!/\!}_{16} & ^3{\!/\!}_{16} & ^1{\!/\!}_{16} & ^3{\!/\!}_{8} \\
2  & ^1{\!/\!}_{16} & ^3{\!/\!}_{16} & ^2{\!/\!}_{16} & ^3{\!/\!}_{8} \\
3  & 0              & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & ^1{\!/\!}_{8} \\
\Sigma & ^1{\!/\!}_{4} & ^1{\!/\!}_{2} & ^1{\!/\!}_{4}  & 1 \\
\end{tblr}$
\end{document}
```

```latex
\documentclass{standalone} \title{probabilities table}
\usepackage{graphbox}
\begin{document}
\includegraphics[align=c]{figure probabilities table 1} \hspace{1em}
\includegraphics[align=c]{figure probabilities table 2} \hspace{1em}
\includegraphics[align=c]{figure probabilities table 3}
\end{document}
```

# Alternatives to tabularray

## Rotated headers without tabularray

![figure table headers rotated.svg](./attachments/figure%20table%20headers%20rotated.svg)

```latex
\documentclass{article} \title{table comparison 2}
\usepackage{adjustbox,array,float}
\renewcommand{\thetable}{1.2\alph{table}}\setcounter{table}{2}
\newcolumntype{R}[2]{%
    >{\adjustbox{angle=#1,lap=\width-(#2)}\bgroup}l<{\egroup}%
}
\newcommand*\rot{\multicolumn{1}{R{45}{1em}}}% no optional argument here, please!
\begin{document}
\begin{minipage}[b]{.3\textwidth}
\begin{table}[H] \caption{}
\begin{tabular}{r|ccc}
         & \rot{Property 1} & \rot{Property 2} & \rot{Property 3} \\ \hline
System 1 &                  &                  & X                \\ 
System 2 & X                & X                & X                \\
System 3 & X                &                  & X                \\ \hline
\end{tabular}
\end{table}
\end{minipage}
\end{document}
```

```latex
\documentclass{standalone} \title{table headers rotated}
\usepackage{graphbox}
\begin{document}
\includegraphics[align=c]{figure table comparison 1} \hspace{1em}
\includegraphics[align=c]{figure table comparison 2}
\end{document}
```

## PgfPlotsTable and tabularray

![figure table headers pgfplotstable.svg](./attachments/figure%20table%20headers%20pgfplotstable.svg)

```latex
\documentclass{standalone} \title{table headers pgfplotstable}
\usepackage{pgfplotstable,tabularray}
\renewcommand{\thetable}{1.5\alph{table}}
\UseTblrLibrary{diagbox}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    text cells/.style = {string type,tblr={ column{1,Z}={c} }},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style={begin table=\begin{#1}{},end table=\end{#1},skip coltypes,environment/.style={}},
    caption/.style = {tblr outer={tall,caption={#1}}},
    hlines/.style={tblr={ hline{1,Z}={.08em},hline{2}={.05em} }},
    hasrowname/.style={every first column/.append style={string type}, tblr={ column{1}={l} }},
    cross/.style={hasrowname, tblr={ vline{2}, hline{2} }},
    frame/.style={tblr={ vline{1,Z}={.08em},hline{1,Z}={.08em} }},
    innergrid/.style={tblr={ vline{2-Y},hline{2-Y} }},
    boldcolname/.style={tblr={ row{1}={font=\bfseries} }},
    boldrowname/.style={hasrowname, tblr={ column{1}={font=\bfseries} }},
    tex,tblr,text cells,caption
}
\begin{document}
\noindent
\pgfplotstabletypeset[hlines, boldcolname]{
Name           & Unicode & Alt code \\
$\alpha$ alpha & U+03B1  & Alt 224  \\
$\gamma$ gamma & U+0393  & Alt 226  \\
$\delta$ delta & U+03B4  & Alt 235  \\
}
\hspace{1em}
\begin{tblr}[tall,caption]{colspec={lcc},vline{2},hline{2}}
        & Word    & Docs \\
Collab. & ++      & ++   \\
Price   & --      & ++   \\
Simple  & $\circ$ & +    \\
\end{tblr}
\hspace{1em}
\begin{tblr}[tall,caption]{colspec={lccc},vline{2},hline{2}}
\diagbox{$x$}{$y$} &              0 &              1 &              2 \\
0                  & $^1\!/_{\!16}$ & $^1\!/_{\!16}$ & $0$            \\
1                  & $^3\!/_{\!16}$ & $^3\!/_{\!16}$ & $^1\!/_{\!16}$ \\
2                  & $0$            & $^4\!/_{\!16}$ & $^3\!/_{\!16}$ \\
\end{tblr}
\end{document}
```

# Figure collection for note preview

![figure table headers.svg](./attachments/figure%20table%20headers.svg)

```latex
\documentclass{standalone} \title{table headers}
\usepackage{graphbox}
\begin{document}
\includegraphics[align=c]{figure pet owners} \hspace{1em}
\includegraphics[align=c]{figure comparison table} \hspace{1em}
\includegraphics[align=c]{figure probabilities table 1}
\end{document}
```
