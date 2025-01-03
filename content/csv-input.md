---
title: "CSV Input - Dynamically generate table from file"
date: "2024-09-10T00:00:00.000+02:00"
dg-publish: true
---
![table measurements 1.svg](./attachments/table-measurements-1.svg)


# Legend


![table file input legend.svg](./attachments/table-file-input-legend.svg)

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

![table file input stats.svg](./attachments/table-file-input-stats.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{7.1b}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\ExplSyntaxOn
\regexConst\cNumberPattern {([-+]?(?:\d*\.)?\d+(?:e[-+]?\d+)?)} 
\prgNewFunction\tblrRangesToList{ mm }{ 
    \__tblr_get_childs:nx{#1}{#2}  \prgReturn{\tlUse\l_tblr_childs_clist} }
\prgNewConditional\cellExtractNumber{ mmn }{
    \regexVarExtractOnceTF\cNumberPattern{
        \evalWhole{ \cellGetText{#1}{#2} }
    }\lTmpaSeq{
        \fpSet{#3}{\evalWhole{ \seqVarItem\lTmpaSeq{1} }}
        \prgReturn\cTrueBool
    }{
        \prgReturn\cFalseBool
    }
}
\prgNewFunction\cellCopy{ m }{
    \propSetFromKeyval\lTmpbProp{#1}
    \propGet\lTmpbProp{r}\lTmpaClist
    \propGet\lTmpbProp{c}\lTmpbClist 
    \propGet\lTmpbProp{accum}\lTmpaTl 
    \propGetTF\lTmpbProp{initial}\lTmpbTl{ \fpSet\lTmpaFp{ \tlUse\lTmpbTl }}{
        \fpZero\lTmpaFp }
    \clistSet\lTmpaClist{ 
        \tblrRangesToList{\tlUse\lTmpaClist}{\arabic{rowcount}} }
    \clistSet\lTmpbClist{ 
        \tblrRangesToList{\tlUse\lTmpbClist}{\arabic{colcount}} }
    \clistVarMapInline\lTmpaClist{\clistVarMapInline\lTmpbClist{
        \cellExtractNumberT{##1}{####1}\lTmpcFp{
            \fpSet\lTmpaFp{\fpEval{ \lTmpaTl }}
        }
    }}
    \prgReturn{ \fpUse\lTmpaFp } }
\prgNewFunction\printNumber{ m }{
    \tlSet\lTmpaTl{\evalWhole{#1}}
    \regexVarReplaceOnce\cNumberPattern{\c{pgfmathprintnumber}\cB\{\0\cE\}}\lTmpaTl
    \prgReturn{ \tlUse\lTmpaTl }}
\prgNewFunction\cellSum{ m }{
    \prgReturn{\cellCopy{#1,accum={\lTmpaFp + \lTmpcFp}}}
}
\prgNewFunction\cellMean{ m }{
    \fpSet\lTmpaFp{ \cellCopy{#1,accum=\lTmpaFp + \lTmpcFp} }
    \fpSet\lTmpbFp{ \cellCopy{#1,accum=\lTmpaFp + 1} }
    \prgReturn{ \fpEval{ \lTmpaFp / \lTmpbFp } }}
\prgNewFunction\cellStandardDeviation{ m }{
    \fpSet\lTmpbFp{ \cellMean{#1} }
    \fpSet\lTmpdFp{ \cellCopy{#1,accum={\lTmpaFp + (\lTmpcFp - \lTmpbFp)^2}} }
    \fpSet\lTmpeFp{ \cellCopy{#1,accum=\lTmpaFp + 1} }
    \prgReturn{\fpEval{ sqrt(\lTmpdFp / \lTmpeFp) } } }
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption={Statistics\vphantom{g}},evaluate=\fileInput, ]{
hline{5,8,11,14,17}={dashed},
hline{1,Z}={.08em},hline{2,X}, columns={r}, row{1}={c},
cell{2-Z}{2}={cmd=\printNumber},
cell{Y}{2}={preto=\cellMean{r=2-X,c=2} },
cell{Z}{2}={preto=\cellStandardDeviation{r=2-X,c=2} },
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

![table file input.svg](./attachments/table-file-input.svg)

```latex
\documentclass{standalone}
\usepackage{graphbox}
\begin{document}
\includegraphics[align=t]{table file input legend} \hspace{1em}
\includegraphics[align=t]{table file input stats}
\includegraphics[align=t]{table file input verbatim}
\end{document}
```

