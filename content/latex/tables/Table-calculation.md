---
date: "2025-07-17T08:13:58.852+02:00"
title: "Table calculation"
description: "-"
dg-publish: true
dg-folder: latex/tables
---

# Accumulate sum, mean, standard deviation, max, min across ranges of the table

```tex
\cellAccum{⟨rows⟩}{⟨columns⟩}{⟨accumulative calculation⟩}{⟨neutral value⟩}
```

- **⟨rows⟩**: comma separated list of (ranges of) desired columns, e.g.: `1-3,Z`
- **⟨columns⟩**: comma separated list of (ranges of) desired columns, e.g.: `even,X-Y`
- **⟨accumulative calculation⟩**: update the value of `\nAccum` for each touched cell, in the order left to right and top to bottom, e.g.: `\nAccum+1` to count cells
- **⟨neutral value⟩**: initial value of `\nAccum`. Leave empty for default 0. Product, minimun, and maximun required different initial values

Available dynamic values for calculation:
- `\nAccum`: value assigned after last update
- `\nCell`: value of the current cell
- `\therownum`: current row number
- `\thecolnum`: current column number

Available function:
- Basic arithmetic: `x+y, x-y, x*y, x/y, sqrt(x)`
- Comparison operators: `x<y, x<=<, y>?y, x!=y`
- Boolean logic: `sign(x), !x, x&&y, x||y, x?y:z`
- Exponentials: `exp x, ln x, x^y, logb x`
- Integer factorial: `fact x`
- See more [functional p. 51](https://texdoc.org/serve/functional/0#page=51) - CTAN documentation

![figure table accumulate.svg](../../figure-table-accumulate.svg)


# Minimal examples: Calculate sum of second column

![figure table calculation 1.svg](../../figure-table-calculation-1.svg)

```latex
\documentclass{standalone} \title{table calculation 1}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\ExplSyntaxOn
\clistNew\columnList \clistNew\rowList \fpNew\nAccum \fpNew\nCell
\prgNewFunction\rowRangesToList{ n }{
    \__tblr_get_childs:nx{ #1 }{ \therowcount }
    \prgReturn{\l_tblr_childs_clist}  }
\prgNewFunction\ColumnRangesToList{ n }{
    \__tblr_get_childs:nx{ #1 }{ \thecolcount }
    \prgReturn{\l_tblr_childs_clist}  }
\prgNewFunction\cellAccum{ mmmm }{
    \clistSet\rowList{ \tlIfEmptyTF{#1}{
        \tlUse{\therownum}  }{  \tlUse{\rowRangesToList{#1}}}  }
    \clistSet\columnList{ \tlIfEmptyTF{#2}{
        \tlUse{\thecolnum}  }{  \tlUse{\ColumnRangesToList{#2}}}  }
    \tlIfEmptyTF{#4}{ \fpZero\nAccum }{ \fpSet\nAccum{#4} }
    \clistVarMapVariable \rowList \lTmpaInt{
        \clistVarMapVariable \columnList \lTmpbInt{
            \fpSet\nCell{ \cellGetText{\lTmpaInt}{\lTmpbInt} }
            \fpSet\nAccum{ #3 }  }  }
    \prgReturn{ \fpEval{ round(\nAccum,2) }} }
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption=Sum]{
    column{1-Z}={r,mode=math}, row{1}={c,mode=text}, 
    hline{1,Z}={.08em},hline{2,Y},
    cell{Z}{2}={cmd=\cellAccum{2-Y}{}{\nAccum + \nCell}{}}
}
t      & U      \\
2      & 78.52  \\  
-5     & -84.4  \\  
-3     & -7.8   \\ 
4      & 68.38  \\  
-2     & -15.40 \\
\Sigma &        \\
\end{tblr}
\hspace{1em}
\begin{tblr}[tall,caption=Row index]{
    column{1-Z}={r,mode=math}, row{1}={c,mode=text}, 
    hline{1,Z}={.08em},hline{2},
    cell{2-Z}{1}={cmd=\intEval{\therownum-1}}
}
\# & t  & U      \\
   & 2  & 78.52  \\  
   & -5 & -84.4  \\  
   & -3 & -7.8   \\ 
   & 4  & 68.38  \\  
   & -2 & -15.40 \\
\end{tblr}
\end{document}
```

- Use regex to test if it is a number

![figure table accumulate.svg](../../figure-table-accumulate.svg)

```latex
\documentclass{standalone} \title{table accumulate}

\usepackage{tabularray}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{3.2}
\ExplSyntaxOn
\clistNew\columnList \clistNew\rowList \fpNew\nAccum \fpNew\nCell
\prgNewFunction\rowRangesToList{ n }{
    \__tblr_get_childs:nx{ #1 }{ \therowcount }
    \prgReturn{\l_tblr_childs_clist}  }
\prgNewFunction\ColumnRangesToList{ n }{
    \__tblr_get_childs:nx{ #1 }{ \thecolcount }
    \prgReturn{\l_tblr_childs_clist}  }
\prgNewFunction\cellAccum{ mmm }{
    \clistSet\rowList{ \tlIfEmptyTF{#1}{
        \tlUse{\therownum}  }{  \tlUse{\rowRangesToList{#1}}}  }
    \clistSet\columnList{ \tlIfEmptyTF{#2}{
        \tlUse{\thecolnum}  }{  \tlUse{\ColumnRangesToList{#2}}}  }
    \fpZero\nAccum
    \clistVarMapVariable \rowList \lTmpaInt{
        \clistVarMapVariable \columnList \lTmpbInt{
            \fpSet\nCell{ \cellGetText{\lTmpaInt}{\lTmpbInt} }
            \fpSet\nAccum{ #3 }  }  }
    \prgReturn{ \fpEval{ round(\nAccum,2) }}  }
\prgNewFunction\cellSum{ mm }{
    \prgReturn{ \cellAccum{#1}{#2}{\nAccum + \nCell} }  }
\prgNewFunction\cellCount{ mm }{
    \prgReturn{ \cellAccum{#1}{#2}{\nAccum + 1} }  }
\prgNewFunction\cellMean{ mm }{
    \fpSet\lTmpaFp{ \cellSum{#1}{#2} / \cellCount{#1}{#2} }
    \prgReturn{ \fpEval{ round(\lTmpaFp,2) }}  }
\prgNewFunction\cellStandardDeviation{ mm }{
    \fpSet\lTmpaFp{ \cellMean{#1}{#2} }
    \fpSet\lTmpbFp{ \cellAccum{#1}{#2}{\nAccum + (\nCell - \lTmpaFp)^2} }
    \fpSet\lTmpcFp{ sqrt(\lTmpbFp / \cellCount{#1}{#2})  }
    \prgReturn{ \fpEval{ round(\lTmpcFp,2) }}  }
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption]{
    colspec={rrr}, hline{1,Z}={.08em},hline{2,V},
    column{2-Z}={r,mode=math,cmd=\pgfmathprintnumber}, 
    column{1}={mode=math},
    cell{2-4}{1}={cmd=\intEval{\therownum}},
    row{1}={c,mode=text,cmd={}}, 
    cell{W}{2-Z}={cmd=\cellSum{2-V}{}},
    cell{X}{2-Z}={cmd=\cellMean{2-V}{}},
    cell{Y}{2-Z}={cmd=\cellStandardDeviation{2-V}{}},
    cell{Z}{2-Z}={cmd=\cellAccum{2-V}{}{max(\nAccum,\nCell)}},
}
\#     & a & b    & c              \\
       & 1 & 2.3  & 1.43587294e-01 \\
       & 4 & 5.2  & 4.41941738e-02 \\
       & 7 & 8.44 & 8.20091159e-03 \\
\Sigma                             \\
\mu                                \\
\sigma                             \\
\max                               \\
\end{tblr}
\end{document}
```

# Add statistics to data table

![figure table accumulate 2.svg](../../figure-table-accumulate-2.svg)

```latex
\documentclass{standalone} \title{table accumulate 2}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{3.2}
\ExplSyntaxOn
\clistNew\columnList \clistNew\rowList \fpNew\nAccum \fpNew\nCell
\prgNewFunction\rowRangesToList{ n }{
    \__tblr_get_childs:nx{ #1 }{ \therowcount }
    \prgReturn{\l_tblr_childs_clist}  }
\prgNewFunction\ColumnRangesToList{ n }{
    \__tblr_get_childs:nx{ #1 }{ \thecolcount }
    \prgReturn{\l_tblr_childs_clist}  }
\prgNewFunction\cellAccum{ mmmm }{
    \clistSet\rowList{ \tlIfEmptyTF{#1}{
        \tlUse{\therownum}  }{  \tlUse{\rowRangesToList{#1}}}  }
    \clistSet\columnList{ \tlIfEmptyTF{#2}{
        \tlUse{\thecolnum}  }{  \tlUse{\ColumnRangesToList{#2}}}  }
    \fpSet\nAccum{ \tlIfEmpty{#4} ? 0 : {#4}  }
    \clistVarMapVariable \rowList \lTmpaInt{
        \clistVarMapVariable \columnList \lTmpbInt{
            \fpSet\nCell{ \cellGetText{\lTmpaInt}{\lTmpbInt} }
            \fpSet\nAccum{ #3 }  }  }
    \prgReturn{ \fpEval{ round(\nAccum,2) }}  }
\prgNewFunction\cellSum{ mm }{
    \prgReturn{ \cellAccum{#1}{#2}{\nAccum + \nCell}{0} }  }
\prgNewFunction\cellCount{ mm }{
    \prgReturn{ \cellAccum{#1}{#2}{\nAccum + 1}{0} }  }
\prgNewFunction\cellMean{ mm }{
    \fpSet\lTmpaFp{ \cellSum{#1}{#2} / \cellCount{#1}{#2} }
    \prgReturn{ \fpEval{ round(\lTmpaFp,2) }}  }
\prgSetEqFunction\cellAverage\cellMean
\prgNewFunction\cellStandardDeviation{ mm }{
    \fpSet\lTmpaFp{ \cellMean{#1}{#2} }
    \fpSet\lTmpbFp{ \cellAccum{#1}{#2}{\nAccum + (\nCell - \lTmpaFp)^2}{0} }
    \fpSet\lTmpcFp{ sqrt(\lTmpbFp / \cellCount{#1}{#2})  }
    \prgReturn{ \fpEval{ round(\lTmpcFp,2) }}  }
\prgNewFunction\cellProd{ mm }{
    \prgReturn{ \cellAccum{#1}{#2}{\nAccum * \nCell}{1} }  }
\prgNewFunction\cellMin{ mm }{
    \prgReturn{ \cellAccum{#1}{#2}{min(\nAccum, \nCell)}{\cInfFp} }  }
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption={Calculate over rows, columns}]{
    column{1-Z}={r,mode=math}, row{1}={c}, 
    hline{1,Z}={.08em},hline{2,5}={1-3}{}, 
    cell{2-4}{1-3}={cmd=\pgfmathprintnumber},
    row{X}={abovesep+=6pt}, cell{X-Z}{X}={l}, cell{X-Z}{Y-Z}={c},
    cell{5}{1-3}={cmd=\cellSum{2-W}{}}, cell{X}{X}={cmd={_\Sigma{\;}^N}},
    cell{6}{1-3}={cmd=\cellMean{2-W}{}}, cell{Y}{X}={cmd=\mu},
    cell{7}{1-3}={cmd=\cellStandardDeviation{2-W}{}}, cell{Z}{X}={cmd=\sigma},
    cell{2-4}{X}={cmd=\cellCount{}{1-W}}, 
    cell{2-4}{Y}={cmd=\cellProd{}{1-W}}, cell{X}{Y}={cmd=\Pi},
    cell{2-4}{Z}={cmd=\cellMin{}{1-W}}, cell{X}{Z}={cmd=\min},
    cell{Y}{Y}={r=2,c=2}{l,cmd=Statistics,mode=text,font=\bfseries},
}
a & b    & c    &&& \\
1 & 2.3  & 1.43e-01 \\
4 & 5.2  & 4.41e-02 \\
7 & 8.44 & 8.20e-03 \\
\\ \\ \\
\end{tblr}
\end{document}
```


```latex
\documentclass{standalone}
\usepackage{xfp,functional}
\newcommand{\isnumber}[1]{%
  \ifnum\ifnum\pdfstrcmp{\detokenize{#1}}{\stripws{#1}}=0 0\else
    \ifnum\fpeval{isinf(#1) | isnan(#1)}=0 1\else 0\fi
  \fi=1 1\else 0\fi
}
\newcommand{\stripws}[1]{\romannumeral-`X\romannumeral-`X#1}
\begin{document}
\isnumber{123}        % Returns 1
\isnumber{3.14}       % Returns 1
\isnumber{-2.5e-3}    % Returns 1
\isnumber{abc}        % Returns 0
\isnumber{ 123 }      % Returns 0 (due to whitespace)
\end{document}
```