---
title: "Format table headings"
dg-publish: true
---

![figure format table headings.svg](./attachments/figure%20format%20table%20headings.svg)

```latex
\documentclass{standalone}\renewcommand{\thetable}{1\alph{table}}
\usepackage{tabularray,rotating,makecell,mathtools,amsfonts,amssymb}
\UseTblrLibrary{diagbox}
\SetTblrOuter{tall,caption}
\setlength\rotheadsize{1.25cm}
\renewcommand\theadfont{}
% Rotation: \rot[<angle>][<width>]{<stuff>}
\NewDocumentCommand{\rot}{O{45} O{1em} m}{\makebox[#2][l]{\rotatebox{#1}{#3}}}%
\begin{document}
\noindent
\begin{tblr}[caption=Pet Owners]{
  colspec={lrrrr},
  hline{1,Z}={.1em}, hline{3},
  column{1}={halign=l,cmd=\quad},
  row{3-Z}={,rowsep=0pt}, row{3}={abovesep=2pt},
  row{3,6}={font=\bfseries,cmd={},abovesep=6pt,belowsep=2pt},
  cell{1}{2,4}={c=2}{c}, row{1-2}={halign=c},
  cell{1-2}{1}={l,cmd={}},
  column{4}={leftsep+=6pt},
  hline{2} = {2-3}{leftpos = -1, rightpos = -1, endpos},
  hline{2} = {4-5}{leftpos = -1, rightpos = -1, endpos},
}
          & Dogs &    & Cats      \\
Owner     & M    & F  & M    & F  \\
Age                               \\
$< 18$    & 2    & 12 & 7    & 11 \\
$\ge 18$  & 4    & 44 & 5    & 3  \\
Residence                         \\
Urban     & 43   & 46 & 15   & 33 \\
Rural     & 5    & 12 & --   & 14 \\
\end{tblr}
\hspace{1em}
\begin{tblr}[caption=Comparison, 
  note{a}={Collaborate live with team members on the same document}
]{
  colspec={lcc},
  hline{Z}={.1em}, hline{2}, 
  cell{1}{2-Z} = {halign=l,cmd=\rot},
  column{1}={rightsep+=4pt},
  cell{2-Z}{2-Z}={mode=math,cmd=\mathrm}, cell{2}{1}={appto=\TblrNote{a}},
}
Aspect  & Overleaf & Obsidian \\
Collab. & ++       & --       \\
Price   & o        & +        \\
Simple  & -        & ++       \\
\end{tblr}
\hspace{2em}
$\begin{tblr}[caption=Probabilities,
  remark{$x$}={horizontal axis}, remark{$y$}={vertical axis}
]{
  colspec={lccc},
  vline{2}={2-Z}{}, vline{Y}, hline{2}={2-Z}{}, hline{Y},
  cell{1}{1}={preto={\diagbox}}, column{1}={colsep=2pt},
  cell{1}{2-Y}={f}, cell{2-Y}{1}={c},
  cell{1,Z}{1}={font=\boldmath,l}, cell{1}{Z}={m,font=\boldmath},
}
{x}{y} & 0              & 1              & 2              & \Sigma        \\
0      & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & 0              & ^1{\!/\!}_{8} \\
1      & ^2{\!/\!}_{16} & ^3{\!/\!}_{16} & ^1{\!/\!}_{16} & ^3{\!/\!}_{8} \\
2      & ^1{\!/\!}_{16} & ^3{\!/\!}_{16} & ^2{\!/\!}_{16} & ^3{\!/\!}_{8} \\
3      & 0              & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & ^1{\!/\!}_{8} \\
\Sigma & ^1{\!/\!}_{4}  & ^1{\!/\!}_{2}  & ^1{\!/\!}_{4}  & 1             \\
\end{tblr}$
\end{document}
```

# More examples

![figure table headers 2.svg](./attachments/figure%20table%20headers%202.svg)

```latex
\documentclass{article}\pagestyle{empty}\setcounter{table}{3}\renewcommand{\thetable}{1\alph{table}}
\usepackage{tabularray,rotating,makecell}
\UseTblrLibrary{diagbox}
\SetTblrOuter{tall,caption}
\SetTblrInner{}
\setlength\rotheadsize{1.25cm}
\renewcommand\theadfont{}
% Rotation: \rot[<angle>][<width>]{<stuff>}
\NewDocumentCommand{\rot}{O{45} O{1em} m}{\makebox[#2][l]{\rotatebox{#1}{#3}}}%
\begin{document}
\noindent
\begin{tblr}{colspec={ccc},hline{1,Z}={.08em},hline{2},row{1}={font=\bfseries}}
Name & Unicode & Alt code \\
$\alpha$ alpha & U+03B1 & Alt 224 \\
$\gamma$ gamma & U+0393 & Alt 226 \\
$\delta$ delta & U+03B4 & Alt 235 \\
\end{tblr}
\hspace{1em}
\begin{tblr}[note{a}={Synchronous and asynchronous collaboration}]
    {colspec={lcc},vline{2},hline{2}}
 & Word & Docs \\
Collab.\TblrNote{a} & ++ & ++ \\
Price & -- & ++ \\
Simple & $\circ$ & + \\
\end{tblr}
\hspace{1em}
\begin{tblr}[remark{$x$}={horizontal axis},remark{$y$}={vertical axis}]
    {colspec={lccc},vline{2},hline{2},column{1}={colsep=2pt} }
\diagbox{$x$}{$y$} &              0 &              1 &              2 \\
0                  & $^1\!/_{\!16}$ & $^1\!/_{\!16}$ &            $0$ \\
1                  & $^3\!/_{\!16}$ & $^3\!/_{\!16}$ & $^1\!/_{\!16}$ \\
2                  & $0$ & $^4\!/_{\!16}$ & $^3\!/_{\!16}$ \\
\end{tblr}

\vspace{1em}\noindent
\begin{tblr}{
  colspec={lrrrr},
  hline{1,Z}={.08em},hline{3},
  column{1}={halign=l,cmd=\quad}, 
    row{3-Z}={,rowsep=0pt},
    row{3,6}={font=\bfseries,cmd={},abovesep=6pt,belowsep=2pt},
    row{3}={abovesep=2pt},
  cell{1}{2,4}={c=2}{c},
    row{1-2}={halign=c},
    column{4}={leftsep+=6pt},
    hline{2} = {2-3}{leftpos = -1, rightpos = -1, endpos},
    hline{2} = {4-5}{leftpos = -1, rightpos = -1, endpos},
}
& Dogs && Cats \\
& M & F & M & F \\
Age \\
$< 18$   & 2 & 12 & 7 & 11 \\ 
$\ge 18$ & 4 & 44 & 5 & 3 \\
Residence \\
Urban & 43 & 46 & 15 & 33 \\
Rural & 5  & 12 &  - & 14 \\
\end{tblr}
\hspace{1em}
\begin{tblr}{
  row{1} = {halign=l,cmd=\rot},
  colspec={lcc},vline{2},hline{2},
}
& Property 1 & Property 2 & Property 3 \\
System 1        &       &       &  X    \\ 
System 2        & X     & X     &  X    \\
System 3        & X &   &  X    \\
\end{tblr}
\end{document}
```

# Two dimensional table

![figure table headers x-y.svg](./attachments/figure%20table%20headers%20x-y.svg)

```latex
\documentclass{article}\pagestyle{empty}\setcounter{table}{8}\renewcommand{\thetable}{1\alph{table}}
\usepackage{tabularray,rotating,makecell,mathtools,amsfonts,amssymb,xcolor}
\UseTblrLibrary{diagbox}
\SetTblrOuter{tall,caption}
\setlength\rotheadsize{1.25cm}
\renewcommand\theadfont{}
% Rotation: \rot[<angle>][<width>]{<stuff>}
\NewDocumentCommand{\rot}{O{45} O{1em} m}{\makebox[#2][l]{\rotatebox{#1}{#3}}}%
\NewDocumentCommand{\rotA}{O{0} O{1em} m}{\makebox[#2][l]{\rotatebox{#1}{#3}}}%
\begin{document}
\noindent
$\begin{tblr}[remark{$x$}={horizontal axis}, remark{$y$}={vertical axis}]{
  colspec={lcccc},
  vline{2}={2-Z}{}, vline{Y}, hline{2}={2-Z}{}, hline{Y},
  cell{1}{1}={preto={\diagbox}}, column{1}={colsep=2pt},
  cell{1}{2-Y}={f}, cell{2-Y}{1}={c}, 
  cell{1,Z}{1}={font=\boldmath,l}, cell{1}{Z}={m,font=\boldmath},
}
{x}{y} & 0              & 1              & 2              & \Sigma        \\
0      & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & 0              & ^1{\!/\!}_{8} \\
1      & ^2{\!/\!}_{16} & ^3{\!/\!}_{16} & ^1{\!/\!}_{16} & ^3{\!/\!}_{8} \\
2      & ^1{\!/\!}_{16} & ^3{\!/\!}_{16} & ^2{\!/\!}_{16} & ^3{\!/\!}_{8} \\
3      & 0              & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & ^1{\!/\!}_{8} \\
\Sigma & ^1{\!/\!}_{4}  & ^1{\!/\!}_{2}  & ^1{\!/\!}_{4}  &  1             \\
\end{tblr}$
\hspace{1em}
$\begin{tblr}[remark{$x$}={horizontal axis}, remark{$y$}={vertical axis}]{
  colspec={lcccc},
  hline{1,Z}={.1em}, hline{2}={leftpos=-7,endpos},
  cell{1}{1}={preto={\diagbox[linewidth=-100pt]}}, column{1}={colsep=2pt},
  cell{1}{2-Y}={f}, cell{2-Y}{1}={c}, 
  cell{1,Z}{1}={font=\boldmath,l}, cell{1}{Z}={h,font=\boldmath},
  row{Z}={abovesep+=6pt}, column{Z}={leftsep+=6pt},
}
{x}{y} & 0              & 1              & 2              & \Sigma        \\
0      & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & 0              & ^1{\!/\!}_{8} \\
1      & ^2{\!/\!}_{16} & ^3{\!/\!}_{16} & ^1{\!/\!}_{16} & ^3{\!/\!}_{8} \\
2      & ^1{\!/\!}_{16} & ^3{\!/\!}_{16} & ^2{\!/\!}_{16} & ^3{\!/\!}_{8} \\
3      & 0              & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & ^1{\!/\!}_{8} \\
\Sigma & ^1{\!/\!}_{4}  & ^1{\!/\!}_{2}  & ^1{\!/\!}_{4}  &  1            \\
\end{tblr}$
\hspace{1em}
$\begin{tblr}[remark{$x$}={horizontal axis}, remark{$y$}={vertical axis}]{
  colspec={lcccc},
  hline{1,Z}={.1em}, hline{2},
  cell{3-6}{1}={cmd=\quad,font={}},
  cell{1}{1}={r}, cell{1}{2-4}={mode=text,cmd={\\}},
  column{1}={font=\boldmath}, row{1}={valign=h,font=\boldmath},
  row{Z}={abovesep+=6pt}, column{Z}={leftsep+=6pt},
}
y=     & 0              & 1              & 2              & \Sigma        \\
x=                                                                        \\
0      & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & 0              & ^1{\!/\!}_{8} \\
1      & ^2{\!/\!}_{16} & ^3{\!/\!}_{16} & ^1{\!/\!}_{16} & ^3{\!/\!}_{8} \\
2      & ^1{\!/\!}_{16} & ^3{\!/\!}_{16} & ^2{\!/\!}_{16} & ^3{\!/\!}_{8} \\
3      & 0              & ^1{\!/\!}_{16} & ^1{\!/\!}_{16} & ^1{\!/\!}_{8} \\
\Sigma & ^1{\!/\!}_{4}  & ^1{\!/\!}_{2}  & ^1{\!/\!}_{4}  & 1             \\
\end{tblr}$
\end{document}
```

|                       | y=<br>0        | <br>1          | <br>2            | $\mathbb{P}(X=\cdot)$ |
| --------------------- | -------------- | -------------- | ---------------- | --------------------- |
| $\boldsymbol{x=}$     |                |                |                  |                       |
| $\quad$ 0             | $^1\!/_{\!16}$ | $^1\!/_{\!16}$ | 0                | $^1\!/_{\!8}$         |
| $\;$ 1                | $^2\!/_{\!16}$ | $^3\!/_{\!16}$ | $^1\!/_{\!16}$   | $^3\!/_{\!8}$         |
| 2                     | $^1\!/_{\!16}$ | $^3\!/_{\!16}$ | $^2\!/_{\!16}$   | $^3\!/_{\!8}$         |
| 3                     | 0              | $^1\!/_{\!16}$ | $^1\!/_{\!16}$   | $^1\!/_{\!8}$         |
| $\mathbb{P}(Y=\cdot)$ | $^1\!/_{\!4}$  | $^1\!/_{\!2}$  | $^1\!/_{\!4}$  & |                       |

| $\boldsymbol{y=}$     | 0              | 1              | 2                | $\mathbb{P}(X=\cdot)$ |
| --------------------- | -------------- | -------------- | ---------------- | --------------------- |
| $\boldsymbol{x=}$     |                |                |                  |                       |
| 0                     | $^1\!/_{\!16}$ | $^1\!/_{\!16}$ | 0                | $^1\!/_{\!8}$         |
| 1                     | $^2\!/_{\!16}$ | $^3\!/_{\!16}$ | $^1\!/_{\!16}$   | $^3\!/_{\!8}$         |
| 2                     | $^1\!/_{\!16}$ | $^3\!/_{\!16}$ | $^2\!/_{\!16}$   | $^3\!/_{\!8}$         |
| 3                     | 0              | $^1\!/_{\!16}$ | $^1\!/_{\!16}$   | $^1\!/_{\!8}$         |
| $\mathbb{P}(Y=\cdot)$ | $^1\!/_{\!4}$  | $^1\!/_{\!2}$  | $^1\!/_{\!4}$  & |                       |

# Alternative rotated column headers

![figure table headers rotated.svg](./attachments/figure%20table%20headers%20rotated.svg)

```latex
\documentclass{standalone}
\usepackage{adjustbox,array}
\newcolumntype{R}[2]{%
    >{\adjustbox{angle=#1,lap=\width-(#2)}\bgroup}%
    l%
    <{\egroup}%
}
\newcommand*\rot{\multicolumn{1}{R{45}{1em}}}% no optional argument here, please!
\begin{document}
\begin{tabular}{r|ccc}
&
\rot{Property 1} &
\rot{Property 2} &
\rot{Property 3}
    \\ \hline
System 1        &       &       &  X    \\ 
System 2        & X     & X     &  X    \\
System 3        & X &   &  X    \\ \hline
\end{tabular}
\end{document}
```

# Old pgfplotstable version

![figure table headers pgfplotstable.svg](./attachments/figure%20table%20headers%20pgfplotstable.svg)

```latex
\documentclass{standalone}\setcounter{table}{13}\renewcommand{\thetable}{1\alph{table}}
\title{Table headers pgfplotstable}
\usepackage{pgfplotstable,tabularray}
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
Name & Unicode & Alt code \\
$\alpha$ alpha & U+03B1 & Alt 224 \\
$\gamma$ gamma & U+0393 & Alt 226 \\
$\delta$ delta & U+03B4 & Alt 235 \\
}
\hspace{1cm}
\begin{tblr}[tall,caption]{colspec={lcc},vline{2},hline{2}}
 & Word & Docs \\
Collab. & ++ & ++ \\
Price & -- & ++ \\
Simple & $\circ$ & + \\
\end{tblr}
\hspace{1cm}
\begin{tblr}[tall,caption]{colspec={lccc},vline{2},hline{2}}
\diagbox{$x$}{$y$} &              0 &              1 &              2 \\
0                  & $^1\!/_{\!16}$ & $^1\!/_{\!16}$ &            $0$ \\
1                  & $^3\!/_{\!16}$ & $^3\!/_{\!16}$ & $^1\!/_{\!16}$ \\
2                  & $0$ & $^4\!/_{\!16}$ & $^3\!/_{\!16}$ \\
\end{tblr}
\end{document}
```
