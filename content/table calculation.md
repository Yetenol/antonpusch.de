---
title: "Table calculation"
dg-publish: true
---

# Accumulate sum, mean, standard deviation, max, min across ranges of the table

```tex
\cellAccum{⟨rows⟩}{⟨columns⟩}{⟨accumulative calculation⟩}
```

- **⟨rows⟩**: comma separated list of (ranges of) desired columns, e.g.: `1-3,Z`
- **⟨columns⟩**: comma separated list of (ranges of) desired columns, e.g.: `even,X-Y`
- **⟨accumulative calculation⟩**: update the value of `\nAccum` for each touched cell, in the order left to right and top to bottom, e.g.: `\nAccum+1` to count cells

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

![table accumulate.svg](./attachments/table%20accumulate.svg)

```latex
\documentclass{standalone}
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
