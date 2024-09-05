---
title: "Calculate statistics for table numbers"
dg-publish: true
---
- Keep the data in **raw** and **universal** (csv) form: Update data anytime with external programs like Excel, Python, MATLAB, R, PowerShell
- Render **scientific notation** correctly and **uniform**: Render `4.41941738e-02` as $4.42 \cdot 10^{-2}$ $\mathrm{3a, 3b, 3c}$ 
- **Format numbers**: Set max. decimal places $\mathrm{3a, 3b, 3c}$; When to show exponent $\mathrm{3c}$; Use German commas $\mathrm{3b}$
- Visually **guide horizontal reading**: Shade every other row $\mathrm{3a}$; Add dashed line every third row $\mathrm{3b}$ 
- Process input data: sort with column $\mathrm{3c}$ 
- More ideas: filter, sort, custom column titles, multi column names, Align at decimal or scientific separator
- See source examples: [Layout the table](./layout%20the%20table.md)

![table measurements 1.svg](./attachments/table%20measurements%201.svg)

calculate sum, mean, standard deviation under table
- [Add rows for sum/mean/std at end of pgfplotstable - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/179177/add-rows-for-sum-mean-std-at-end-of-pgfplotstable)
- [\[Pgfplots-features\] Simple calculations on columns of data](https://pgfplots-features.narkive.com/tu1Qxhx5/simple-calculations-on-columns-of-data)



# Counters

- counters rownum, colnum, rowcount, colcount are available
Print counter with format
- `\arabic{rownum}`, `\alph{rownum}`, `\Alph{rownum}`, `\roman{rownum}`, `\Roman{rownum}`, `\therownum`

![table counters.svg](./attachments/table%20counters.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\renewcommand{\thetable}{1.2\alph{table}}
\begin{document}
\begin{tblr}[tall,caption]{ 
    hline{1,Z}={.08em},hline{3}, column{1-Z}={c},
    cell{3-Z}{2}={preto=\arabic{colnum}},
    cell{3-Z}{3}={preto=\alph{colnum}},
    cell{3-Z}{4}={preto=\Alph{colnum}},
    cell{3-Z}{5}={preto=\roman{colnum}},
    cell{3-Z}{6}={preto=\Roman{colnum}},
    cell{3}{2-Z}={appto={,\arabic{rownum}}},
    cell{4}{2-Z}={appto={,\alph{rownum}}},
    cell{5}{2-Z}={appto={,\Alph{rownum}}},
    cell{6}{2-Z}={appto={,\roman{rownum}}},
    cell{7}{2-Z}={appto={,\Roman{rownum}}},
    cell{1}{1}={r=2}{font=\bfseries}, cell{1}{2}={c=5}{font=\bfseries},
    hline{2}={2-Z}{leftpos=-1,rightpos=-1,endpos},
}
{rownum\\counter} & colnum counter \\
& arabic & alph & Alph & roman & Roman \\
arabic \\
alph   \\
Alph   \\
roman  \\
Roman  \\
\end{tblr}
\end{document}
```

# Shift column, row index to main content

![table counters 2.svg](./attachments/table%20counters%202.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\UseTblrLibrary{counter}
\UseTblrLibrary{functional}
\renewcommand{\thetable}{1.2\alph{table}}
\IgnoreSpacesOn
\newcounter{colindex}
\newcounter{rowindex}
\intNew\nindex
\prgNewFunction\updatecolindex{ m }{
    \intCompareTF {\thecolnum} > {#1}
        { \intSet\nindex{ \intEval{ \thecolnum - #1 }}}
        { \intZero\nindex }
    \setcounter{colindex}{\nindex}
}
\prgNewFunction\updaterowindex{ m }{
    \intCompareTF {\therownum} > {#1}
        { \intSet\nindex{ \intEval{ \therownum - #1 }}}
        { \intZero\nindex }
    \setcounter{rowindex}{\nindex}
}
\IgnoreSpacesOff
\begin{document}
\begin{tblr}[tall,caption]{ 
    hline{1,Z}={.08em},hline{3}, column{1-Z}={c},
    cell{3-Z}{2}={preto=\arabic{colindex}},
    cell{3-Z}{3}={preto=\alph{colindex}},
    cell{3-Z}{4}={preto=\Alph{colindex}},
    cell{3-Z}{5}={preto=\roman{colindex}},
    cell{3-Z}{6}={preto=\Roman{colindex}},
    cell{3}{2-Z}={appto={,\arabic{rowindex}}},
    cell{4}{2-Z}={appto={,\alph{rowindex}}},
    cell{5}{2-Z}={appto={,\Alph{rowindex}}},
    cell{6}{2-Z}={appto={,\roman{rowindex}}},
    cell{7}{2-Z}={appto={,\Roman{rowindex}}},
    cell{1-Z}{1-Z}={preto={\updatecolindex{1}\updaterowindex{2}}},
    cell{1}{1}={r=2}{font=\bfseries}, cell{1}{2}={c=5}{font=\bfseries},
    hline{2}={2-Z}{leftpos=-1,rightpos=-1,endpos},
}
{rowindex\\counter} & colindex counter \\
& arabic & alph & Alph & roman & Roman \\
arabic \\
alph   \\
Alph   \\
roman  \\
Roman  \\
\end{tblr}
\end{document}
```

# Only index valid columns, rows

![table counters 3.svg](./attachments/table%20counters%203.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\UseTblrLibrary{counter}
\renewcommand{\thetable}{1.1}
\newcounter{rowindex}
\newcounter{colindex}
\begin{document}
\begin{tblr}[tall,caption=Pet Owners]{
  colspec={lrrrr},
  hline{1,Z}={.1em}, hline{3},
  row{3-Z}={,rowsep=0pt}, row{3}={abovesep=2pt},
  column{1}={halign=l,cmd={\stepcounter{rowindex}\rlap{\roman{rowindex}}\qquad}},
  row{3}={cmd={\stepcounter{colindex}\roman{colindex}}},
  cell{1}{1}={preto=\setcounter{rowindex}{0}\setcounter{colindex}{0}},
      cell{3,6}{1}={font=\bfseries,cmd={}},
      row{3,6}={abovesep=6pt,belowsep=2pt},
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

# Count per group

![table counters 4.svg](./attachments/table%20counters%204.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\UseTblrLibrary{counter}
\renewcommand{\thetable}{1.1}
\newcounter{rowindex}
\newcounter{colindex}
\begin{document}
\begin{tblr}[tall,caption=Pet Owners]{
  colspec={lrrrr},
  hline{1,Z}={.1em}, hline{3},
  row{3-Z}={,rowsep=0pt}, row{3}={abovesep=2pt},
  column{1}={halign=l,cmd={\stepcounter{rowindex}\rlap{\roman{rowindex}}\qquad}},
  cell{3}{2-Z}={preto={\stepcounter{colindex}\roman{colindex}}},
      cell{3,6}{1}={font=\bfseries,cmd=\setcounter{rowindex}{0}},
      row{3,6}={abovesep=6pt,belowsep=2pt},
  cell{1}{2,4}={c=2}{c}, row{1-2}={halign=c},
  cell{3}{2,4}={preto=\setcounter{colindex}{0}},
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



# Statistics

# Calculate sum, mean, or standard deviation for each column

![table stats.svg](./attachments/table%20stats.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{3.2}
\IgnoreSpacesOn
\fpNew\nsum \fpNew\nmean \intNew\nlast
\prgNewFunction\resolveUVWXYZ{ mm }{
    \strCaseTF {#1} {
         U{\tlSet\nlast{5}}  V{\tlSet\nlast{4}}
         W{\tlSet\nlast{3}}  X{\tlSet\nlast{2}}
         Y{\tlSet\nlast{1}}  Z{\tlSet\nlast{0}}
    }{  \prgReturn{ \intEval{ #2 - \nlast }}
    }{  \prgReturn{#1} }
}
\prgNewFunction\colnum{ m }{
    \prgReturn{ \resolveUVWXYZ{#1}{\therowcount} }
}
\prgNewFunction\vsum{ mm }{
    \fpZero\nsum
    \intStepOneInline{ \colnum{#1} }{ \colnum{#2} }{
        \fpAdd\nsum{ \cellGetText{##1}{\thecolnum} }
    }
    \prgReturn{ \fpEval{ round(\nsum,2) } }
}
\prgNewFunction\vmean{ mm }{
    \prgReturn{ \fpEval{ 
        \vsum{ \colnum{#1} }{ \colnum{#2} } 
        / ( \colnum{#2} - \colnum{#1} ) 
    }}
}
\prgNewFunction\vstandarddeviation{ mm }{
    \fpSet\nmean{ \vmean{#1}{#2} }
    \fpZero\nsum
    \intStepOneInline{ \colnum{#1} }{ \colnum{#2} }{
        \fpAdd\nsum{ 
            ( \cellGetText{##1}{\thecolnum} - \nmean )^2 }
    }
    \prgReturn{ \fpEval{ round(\nsum,2) }}
}
\IgnoreSpacesOff
\begin{document}
\begin{tblr}[tall,caption]{
    colspec={rrr}, hline{1,Z}={.08em},hline{2,W},
    column{2-Z}={r,mode=math,cmd=\pgfmathprintnumber}, 
    column{1}={mode=math},
    cell{2-4}{1}={cmd=\intEval{\therownum-1}},
    row{1}={c,mode=text,cmd={}}, 
    cell{X}{2-Z}={cmd=\vsum{2}{W}},
    cell{Y}{2-Z}={cmd=\vmean{2}{W}},
    cell{Z}{2-Z}={cmd=\vstandarddeviation{2}{W}},
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

# Sum up integers

![table stats integer sum.svg](./attachments/table%20stats%20integer%20sum.svg)

```latex
\documentclass{standalone}
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

![table stats float sum.svg](./attachments/table%20stats%20float%20sum.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
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
\documentclass{standalone}
\usepackage{tabularray}
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
\documentclass{standalone}
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



# Figure collection for note preview

![table functional.svg](./attachments/table%20functional.svg)

```latex
\documentclass{standalone}
\usepackage{graphics}
\begin{document}
\includegraphics{table counters}
\hspace{1em}
\includegraphics{table stats}
\end{document}
```