---
title: "Format numbers - Evaluate, Round to precision, Set decimal and thousands separator, Use scientific notations"
dg-publish: true
---

# Number formattings

![table number formats pgf.svg](./attachments/table%20number%20formats%20pgf.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray,mathtools,tikz}
\renewcommand{\thetable}{2.1}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\ExplSyntaxOn
\regexConst\cNumberPattern {([-+]?(?:\d*\.)?\d+(?:e[-+]?\d+)?)} 
\prgNewFunction\printNumber{ mm }{
    \tlIfBlankF{#1}{ \pgfkeys{/pgf/number~format/.cd,#1} }
    \tlSet\lTmpaTl{\evalWhole{#2}}
    \regexVarReplaceOnce\cNumberPattern{\c{pgfmathprintnumber}\cB\{\0\cE\}}\lTmpaTl
    \prgReturn{ \tlUse\lTmpaTl }}
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption=Pgf number formats]{
    hline{1,Z}={.08em},hline{3},
    hline{6,9,12,15,18,21,24,27,30,33}={dashed},
    column{1}={r,cmd=\printNumber{}},
    column{2}={r,cmd=\printNumber{sci}},
    column{3}={r,cmd=\printNumber{sci,sci subscript}},
    column{4}={r,cmd=\printNumber{frac}},
    row{1,2}={c,m}, cell{1}{2}={c=2}{}, cell{1}{1,4}={r=2}{},
    hline{2}={2-3}{leftpos=-2,rightpos=-2,endpos},
}
{Auto\\format} & Scientific notation && Fraction \\
               & forced   & subscript            \\
0.25           & 0.25     & 0.25      & 0.25     \\
-42            & -42      & -42       & -42      \\
289            & 289      & 289       & 289      \\
4225.31        & 4225.31  & 4225.31   & 4225.31  \\
66049          & 66049    & 66049     & 66049    \\
263169         & 263169   & 263169    & 263169   \\
1.0563e6       & 1.0563e6 & 1.0563e6  & 1.0563e6 \\
\end{tblr}
\end{document}
```

## SiUnitX

![table number formats siunitx.svg](./attachments/table%20number%20formats%20siunitx.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray,mathtools,tikz}
\renewcommand{\thetable}{2.2}
\UseTblrLibrary{functional,siunitx}
\sisetup{exponent-product = \cdot}
\usetikzlibrary{fpu}
\ExplSyntaxOn
\regexConst\cNumberPattern {([-+]?(?:\d*\.)?\d+(?:e[-+]?\d+)?)} 
\prgNewFunction\printNum{ mm }{
    \tlSet\lTmpaTl{\evalWhole{#2}}
    \regexVarReplaceOnce\cNumberPattern{\c{num}\[#1\]\cB\{\0\cE\}}\lTmpaTl
    \prgReturn{ \tlUse\lTmpaTl }}
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption=SiUnitX number formats]{
    hline{1,Z}={.08em},hline{3},
    hline{6,9,12,15,18,21,24,27,30,33}={dashed},
    column{1}={r,cmd=\num},
    column{2}={r,cmd={\num[exponent-mode=scientific]}},
    column{3}={r,cmd={\num[exponent-mode=engineering]}},
    column{4}={r,cmd={\num[uncertainty-mode=separate]}},
    row{1,2}={c,m,cmd={}}, cell{1}{2}={c=2}{}, cell{1}{1,4}={r=2}{},
    hline{2}={2-3}{leftpos=-2,rightpos=-2,endpos},
}
{Auto\\format} & Exponent mode             && uncertainty-mode \\
               & scientific   & engineering            \\
0.25           & 0.25         & 0.25        & 0.25     \\
8(12:34)       & 8(12:34)     & 8(12:34)    & 8(12:34) \\
289            & 289          & 289         & 289      \\
4225.31        & 4225.31      & 4225.31     & 4225.31  \\
66049(1)       & 66049(1)     & 66049(1)    & 66049(1) \\
263169         & 263169       & 263169      & 263169   \\
1.0563e6       & 1.0563e6     & 1.0563e6    & 1.0563e6 \\
\end{tblr}
\end{document}
```

# Evaluate mathematical terms

![table body evaluate math.svg](./attachments/table%20body%20evaluate%20math.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray,tikz}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{2.3}
\begin{document}
$\begin{tblr}[tall,caption=Evaluate]{ hline{1,Z}={.08em},
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

# Complex evaluate, assign cell content with PgfPlotsTable

![table body pgfplotstable.svg](./attachments/table%20body%20pgfplotstable.svg)

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

# Alternative without functional

![table body number format no functional.svg](./attachments/table%20body%20number%20format%20no%20functional.svg)

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


# Figure collection for note preview

![table body.svg](./attachments/table%20body.svg)

```latex
\documentclass{standalone} \usepackage{graphbox}
\begin{document}
\begin{minipage}{\textwidth} \centering{}
\includegraphics{table number formats pgf} \hspace{1em}
\includegraphics{table body evaluate math} \\[1em]
\includegraphics[align=c]{table number formats siunitx}
\end{minipage}
\end{document}
```