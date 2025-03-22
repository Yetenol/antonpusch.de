---
date: "2025-03-22T11:19:04.060+01:00"
title: "Calculate statistics for table numbers"
description: "-"
dg-publish: true
dg-folder: latex/tables
---
- Keep the data in **raw** and **universal** (csv) form: Update data anytime with external programs like Excel, Python, MATLAB, R, PowerShell
- Render **scientific notation** correctly and **uniform**: Render `4.41941738e-02` as $4.42 \cdot 10^{-2}$ $\mathrm{3a, 3b, 3c}$ 
- **Format numbers**: Set max. decimal places $\mathrm{3a, 3b, 3c}$; When to show exponent $\mathrm{3c}$; Use German commas $\mathrm{3b}$
- Visually **guide horizontal reading**: Shade every other row $\mathrm{3a}$; Add dashed line every third row $\mathrm{3b}$ 
- Process input data: sort with column $\mathrm{3c}$ 
- More ideas: filter, sort, custom column titles, multi column names, Align at decimal or scientific separator
- See source examples: [Layout the table](./Layout-the-table.md)

![figure table measurements 1.svg](../../figure-table-measurements-1.svg)

calculate sum, mean, standard deviation under table
- [Add rows for sum/mean/std at end of pgfplotstable - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/179177/add-rows-for-sum-mean-std-at-end-of-pgfplotstable)
- [\[Pgfplots-features\] Simple calculations on columns of data](https://pgfplots-features.narkive.com/tu1Qxhx5/simple-calculations-on-columns-of-data)




# Statistics

# Calculate sum, mean, or standard deviation for each column

![figure table stats.svg](../../figure-table-stats.svg)

```latex
\documentclass{standalone} \title{table stats}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{3.2}
\ExplSyntaxOn
\clistNew\vchilds 
\fpNew\naccum \fpNew\nmean \intNew\nlast \fpNew\ncell
\prgNewFunction\vclist{ n }{
    \__tblr_get_childs:nx{ #1 }{ \therowcount }
    \prgReturn{\l_tblr_childs_clist}%
}
\prgNewFunction\vMapInline{ mm }{
    \fpZero\naccum
    \clistVarMapInline{ \vclist{#1} }{
        \fpSet\ncell{ \cellGetText{##1}{\thecolnum} }
        \fpSet\naccum{ #2 }
    }
    \prgReturn{ \fpEval{ round(\naccum,2) }}
}
\prgNewFunction\vsum{ m }{
    \prgReturn{ \vMapInline{#1}{\naccum + \ncell}  }}
\prgNewFunction\vcount{ m }{
    \prgReturn{ \clistVarCount{\vclist{#1}} }
}
\prgNewFunction\vmean{ m }{
    \prgReturn{ \fpEval{ round( \vsum{#1} / \vcount{#1} ,2) }}}
\prgNewFunction\vstandarddeviation{ m }{
    \fpSet\nmean{ \vmean{#1} }
    \prgReturn{ \vMapInline{#1}{\naccum + (\ncell - \nmean)^2 }  }}
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption]{
    colspec={rrr}, hline{1,Z}={.08em},hline{2,W},
    column{2-Z}={r,mode=math,cmd=\pgfmathprintnumber}, 
    column{1}={mode=math},
    cell{2-4}{1}={cmd=\intEval{\therownum-1}},
    row{1}={c,mode=text,cmd={}}, 
    cell{X}{2-Z}={cmd=\vsum{2-W}},
    cell{Y}{2-Z}={cmd=\vmean{2-W}},
    cell{Z}{2-Z}={cmd=\vstandarddeviation{2-W}},
}
\#     & a & b    & c              \\
       & 1 & 2.3  & 1.43587294e-01 \\
       & 4 & 5.2  & 4.41941738e-02 \\
       & 7 & 8.44 & 8.20091159e-03 \\
\Sigma                             \\
\mu                                \\
\sigma                             \\
\end{tblr}
\end{document}
```
[Table calculation](./Table-calculation.md)
# Sum up integers

![figure table stats integer sum.svg](../../figure-table-stats-integer-sum.svg)

```latex
\documentclass{standalone} \title{table stats integer sum}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\renewcommand{\thetable}{3.1}
\IgnoreSpacesOn
\prgNewFunction \funcSum {} {
 \intStepOneInline {2} {\arabic{colcount}} {
 \intZero \lTmpaInt
 \intStepOneInline {2} {\arabic{rowcount}-1} {
 \intAdd \lTmpaInt {\cellGetText {####1} {##1}}
 }
 \cellSetText {\expWhole{\arabic{rowcount}}} {##1} {\intUse\lTmpaInt}
 }
}
\IgnoreSpacesOff
\begin{document}
\begin{tblr}[tall,caption]{
    colspec={rrr},process=\funcSum,
    column{1-Z}={r, mode=math}, column{1}={rightsep=0pt},
    row{1}={c,mode=text}, hline{1,Z}={.08em},hline{2,Y},
}
       & a & b & c \\
       & 1 & 2 & 3 \\
       & 4 & 5 & 6 \\
       & 7 & 8 & 9 \\
\Sigma &   &   &   \\
\end{tblr}
\end{document}
```

# Sum up floats

![figure table stats float sum.svg](../../figure-table-stats-float-sum.svg)

```latex
\documentclass{standalone} \title{table stats float sum}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{3.2}
\IgnoreSpacesOn
\prgNewFunction \funcSum {} {
    \intStepOneInline {2} {\arabic{colcount}} { % for columns 2-Z
        \fpZero \sum % sum = 0.0
        \intStepOneInline {2} {\arabic{rowcount}-1} { % for rows 2-Y
            \fpAdd \sum {\cellGetText {####1} {##1}} % sum += cell
        }
        \cellSetText {\expWhole{\arabic{rowcount}}} {##1} {\fpUse\sum} % cell = sum
    }
}
\IgnoreSpacesOff
\begin{document}
\begin{tblr}[tall,caption]{
    colspec={rrr}, process=\funcSum, hline{1,Z}={.08em},hline{2,Y},
    column{1-Z}={r,mode=math,cmd=\pgfmathprintnumber}, 
    column{1}={rightsep=0pt,cmd=\intEval{\therownum-1}},
    row{1}={c,mode=text,cmd={}}, 
    row{Z}={cmd={}}
}
\#     & a & b & c \\
       & 1 & 2.3 & 1.43587294e-01 \\
       & 4 & 5.2 & 4.41941738e-02 \\
       & 7 & 8.44 & 8.20091159e-03 \\
\Sigma &   &   &   \\
\end{tblr}
\end{document}
```


```latex
\documentclass{standalone} \title{}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{3.2}
\IgnoreSpacesOn
\prgNewFunction \sumRowRange {mm} {
    \fpZero \sum % sum = 0.0
    \intStepOneInline {#1} {#2} { % for rows 2-Y
        \fpAdd \sum {\cellGetText {##1} {\thecolnum}} % sum += cell
    }
    \prgReturn {\fpEval {round(\sum,2)}}
}
\prgNewFunction \meanRowRange {mm} {
    \prgReturn {\fpEval{\sumRowRange{#1}{#2}/(#2-#1)}}
}
\prgNewFunction \standardDeviationRowRange {mm} {
    \fpSet \mean {\meanRowRange{#1}{#2}}
    \fpZero \sum % sum = 0.0
    \intStepOneInline {#1} {#2} { % for rows 2-Y
        \fpAdd \sum {(\cellGetText {##1} {\thecolnum} - \mean)^2}
    }
    \prgReturn {\fpEval {round(\sum,2)}}
}
\IgnoreSpacesOff
\begin{document}
\begin{tblr}[tall,caption]{
    colspec={rrr}, hline{1,Z}={.08em},hline{2,W},
    column{2-Z}={r,mode=math,cmd=\pgfmathprintnumber}, 
    column{1}={mode=math},
    cell{2-4}{1}={cmd=\intEval{\therownum-1}},
    row{1}={c,mode=text,cmd={}}, 
    cell{X}{2-Z}={cmd=\sumRowRange{2}{4}},
    cell{Y}{2-Z}={cmd=\meanRowRange{2}{4}},
    cell{Z}{2-Z}={cmd=\standardDeviationRowRange{2}{4}},
}
\#     & a & b    & c              \\
       & 1 & 2.3  & 1.43587294e-01 \\
       & 4 & 5.2  & 4.41941738e-02 \\
       & 7 & 8.44 & 8.20091159e-03 \\
\Sigma                             \\
\mu                                \\
\sigma                             \\
\end{tblr}
\end{document}
```

```latex
\documentclass{standalone} \title{}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\begin{document}
\IgnoreSpacesOn
\prgNewFunction \charToNum{mm} {
    \strCaseTF {#1} {
         {U} {\tlSet\lTmpkTl{5}}  {V} {\tlSet\lTmpkTl{4}}
         {W} {\tlSet\lTmpkTl{3}}  {X} {\tlSet\lTmpkTl{2}}
         {Y} {\tlSet\lTmpkTl{1}}  {Z} {\tlSet\lTmpkTl{0}}
    }{  \prgReturn{\intEval{#2-\lTmpkTl}}  }
    {  \prgReturn{#1}  }}
\IgnoreSpacesOff
\charToNum{X}{5} \charToNum{Y}{5} \charToNum{Z}{5} \charToNum{3}{5}
\end{document}
```

```latex
\documentclass{standalone} \title{}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\ExplSyntaxOn
\prgNewFunction\getVChilds{ m }{
    \__tblr_get_childs:nx{ #1 }{ \therowcount }
    \prgReturn \l_tblr_childs_clist
}
\prgNewFunction\getHChilds{ m }{
    \__tblr_get_childs:nx{ #1 }{ \thecolcount }
    \prgReturn \l_tblr_childs_clist
}
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall, caption]{}
a & b & c & d \\
1 & 2 & 3 & 4 \\
5 & \getVChilds{1-Z} & 7 & 8 \\
9 & 9 & 9 & 9 \\
\end{tblr}
\end{document}
```

# Figure collection for note preview

![figure table functional.svg](../../figure-table-functional.svg)

```latex
\documentclass{standalone} \title{table functional}
\usepackage{graphics}
\begin{document}
\includegraphics{figure table counter body}
\hspace{1em}
\includegraphics{figure table stats}
\end{document}
```