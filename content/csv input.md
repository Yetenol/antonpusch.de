---
title: "CSV Input - Dynamically generate table from file"
dg-publish: true
---
![table measurements 1.svg](./attachments/table%20measurements%201.svg)


# Legend


![table file input legend.svg](./attachments/table%20file%20input%20legend.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{7.1a}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\begin{document}
\begin{tblr}[tall,caption={Legend},evaluate=\fileInput,
remark{$t$} = {Time when datapoint was meassured},
remark{$U_1$} = {Voltage meassured}, ]{
hline{5,8,11,14,17}={dashed},
hline{1,Z}={.08em},hline{2}, columns={r}, row{1}={c},
cell{2-Z}{2}={cmd=\pgfmathprintnumber},
}
$t$ in ms & $U_1$ in V \\
\fileInput{data.tex}
\end{tblr}
\end{document}
```

# Statistics

- TODO: format numbers in stats consistent
- reliable dash every 3rd line without the stats

![table file input stats.svg](./attachments/table%20file%20input%20stats.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{7.1b}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\ExplSyntaxOn
\clistNew\columnList \clistNew\rowList \fpNew\nAccum \fpNew\nCell 
\intNew\nRow \intNew\nColumn
\regexConst\lNumberPattern {([-+]?(?:\d*\.\d+|\d*)(?:e[-+]?\d+))} \regexConst\gParenthesePattern {\((.+?)\)}
\prgNewFunction\tblrRangesToList{ mm }{ 
    \__tblr_get_childs:nx{#1}{#2}  \prgReturn{\tlUse\l_tblr_childs_clist} }
\prgNewFunction\relativeAndTblrRangesToList{ mmm }{
    \tlIfEmptyTF{#1} { \tlSet\lTmpaTl{ (0) } }{ \tlSet\lTmpaTl{ #1 } }
    \regexVarReplaceAll\gParenthesePattern{ \c{intEval}\cB\{ \1 + \c{arabic}\{#2\} \cE\} }\lTmpaTl
    \tlSet\lTmpaTl{ \evalWhole{ \tlUse\lTmpaTl }}
    \tlSet\lTmpaTl{ \tblrRangesToList{ \tlUse\lTmpaTl }{ \arabic{#3} } }
    \prgReturn{ \tlUse\lTmpaTl }  }
\prgNewConditional\extractNumber{ mm }{
    \tlSet\lTmpaTl{ \evalWhole{ \cellGetText{ \intEval{#1} }{ \intEval{#2} } }}
    \regexVarExtractOnceTF\lNumberPattern{ \tlUse\lTmpaTl }\lTmpaSeq{ 
        \fpSet\nCell{ \seqVarItem\lTmpaSeq{1} }  \prgReturn\cTrueBool 
    }{  \fpZero\nCell \prgReturn\cFalseBool }}
\prgNewFunction\cellAccum{ mmmm }{
    \clistSet\rowList{ \relativeAndTblrRangesToList{#1}{rownum}{rowcount} } 
    \clistSet\columnList{ \relativeAndTblrRangesToList{#2}{colnum}{colcount} }
    \tlIfEmptyTF{#4}{ \fpZero\nAccum }{ \fpSet\nAccum{#4} }
    \clistVarMapVariable \rowList \nRow{
        \clistVarMapVariable \columnList \nColumn{
            \extractNumberT{\nRow}{\nColumn}{
                \fpSet\nAccum{ #3 } } } }
    \prgReturn{ \fpEval{ \nAccum }}}
\prgNewFunction\cellMean{ mm }{
    \fpSet\lTmpaFp{ \cellAccum{#1}{#2}{ \nAccum + \nCell }{} }
    \fpSet\lTmpbFp{ \cellAccum{#1}{#2}{ \nAccum + 1 }{} }
    \prgReturn{\fpEval{ \lTmpaFp / \lTmpbFp  } } }
\prgNewFunction\cellStandardDeviation{ mm }{
    \fpSet\lTmpaFp{ \cellMean{#1}{#2} }
    \fpSet\lTmpbFp{ \cellAccum{#1}{#2}{ \nAccum + (\nCell - \lTmpaFp)^2 }{} }
    \fpSet\lTmpcFp{ \cellAccum{#1}{#2}{ \nAccum + 1 }{} }
    \prgReturn{\fpEval{ sqrt(\lTmpbFp / \lTmpcFp) } } }
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption={Statistics\vphantom{g}},evaluate=\fileInput, ]{
hline{5,8,11,14,17}={dashed},
hline{1,Z}={.08em},hline{2,X}, columns={r}, row{1}={c},
cell{2-X}{2}={cmd={\pgfmathprintnumber}},
cell{Y}{2}={cmd={\fpEval{round( \cellMean{2-X}{} ,4)}}},
cell{Z}{2}={cmd={\fpEval{round( \cellStandardDeviation{2-X}{} ,4) }}},
}
$t$ in ms & $U_1$ in V \\
\fileInput{data.tex}
$\mu$ \\
$\sigma$ \\
\end{tblr}
\end{document}
```

# Verbatim print data file

```latex
\documentclass{standalone} \renewcommand{\thetable}{7.1c}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\prgNewFunction\fileVerbatim{ m }{
    \fileGet{#1}{}\lTmpaTl
    \regexReplaceAll{\s*&\s*}{,}\lTmpaTl
    \prgReturn{ \tlUse\lTmpaTl }
}
\begin{document}
\begin{tblr}[tall,caption={File data.csv\vphantom{g}},evaluate=all]{
hline{1,Z}={.08em}, columns={font=\ttfamily}
}
\\
\fileVerbatim{data.tex}{}
\end{tblr}
\end{document}
```

# Figure collection for note preview

![table file input.svg](./attachments/table%20file%20input.svg)

```latex
\documentclass{standalone}
\usepackage{graphbox}
\begin{document}
\includegraphics[align=t]{table file input legend} \hspace{1em}
\includegraphics[align=t]{table file input stats}
\includegraphics[align=t]{table file input verbatim}
\end{document}
```

