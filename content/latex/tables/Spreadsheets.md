---
date: "2025-07-17T08:13:58.788+02:00"
title: "Spreadsheets"
description: "Calculate sum, mean, standard deviation, max, and min across selection of cells"
dg-publish: true
dg-folder: latex/tables
---

# Accumulate selection of cells

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

![figure table accumulate sum.svg](../../figure-table-accumulate-sum.svg)

```latex
\documentclass{standalone} \title{table accumulate sum}
\renewcommand{\thetable}{6.1}
\usepackage{tabularray}
\UseTblrLibrary{functional}
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
    }{  \prgReturn\cFalseBool } }
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
            \fpSet\lTmpaFp{\fpEval{ \lTmpaTl }} } }}
    \prgReturn{ \fpUse\lTmpaFp } }
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption=Sum]{
column{1-Z}={r,mode=math}, row{1}={c,mode=text}, 
hline{1,Z}={.08em},hline{2,Y},
cell{Z}{2}={cmd=\cellCopy{r=2-Y,c=2,accum=\lTmpaFp + \lTmpcFp}}
}
t      & U      \\
2      & 78.52  \\  
-5     & -84.4  \\  
-3     & -7.8   \\ 
4      & 68.38  \\  
-2     & -15.40 \\
\Sigma &        \\
\end{tblr}
\end{document}
```

# Add expenses

Calculate the following values, with row number $r$:

- Trip distance $dist_r \coloneqq \left| marker_{r - 1} - marker_r \right|$ for $r \in \{ 4, 5, 6, 9, 10, 11 \}$ 
- Total price $total_r \coloneqq  price_r \cdot  overnights_r$ for $r \in \{ 3, 4, \ldots, 11 \}$ 
- Distance through Mecklenburg Lakeland $meck \coloneqq \left| marker_3 - marker_6 \right|$ 
- Distance on Havel River $havel \coloneqq \left| marker_8 - marker_{11}  \right|$ 
- Minimum non-zero overnight price $min \coloneqq \min \big( \{ price_r \in Price \mid price_c > 0, r \in \{ 3, 4, \ldots, 11 \} \big)$ 
- Maximum overnight price $max \coloneqq \max(price_3, \ldots, price_{11} )$
- Total accommodation cost $accom \coloneqq \sum_{r = 3}^{11} total_r$
- Daily average $avg \coloneqq accom \div \operatorname{count-nonnull}(total_3, \ldots, total_{11} )$ 

![figure table accumulate trip expenses.svg](../../figure-table-accumulate-trip-expenses.svg)

```latex
\documentclass{standalone} \title{table accumulate trip expenses}
\renewcommand{\thetable}{6.2}
\usepackage{tabularray,eurosym}
\UseTblrLibrary{functional}
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
    }{  \prgReturn\cFalseBool } }
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
            \fpSet\lTmpaFp{\fpEval{ \lTmpaTl }} } }}
    \prgReturn{ \fpUse\lTmpaFp } }
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption={Calculate trip distances, expenses that are \textbf{bold}},note{}={
    We canoe \textbf{%
    \cellCopy{r={3,6},c={2},accum={ abs(\lTmpaFp - \lTmpcFp) }}\,km} 
    through the Mecklenburg Lakeland and \textbf{%
    \cellCopy{r={8,11},c={2},accum={ abs(\lTmpaFp - \lTmpcFp) }}\,km} 
    on the Havel River. Overnight prices range from \textbf{%
    \cellCopy{r={3-Z},c={4},accum={\lTmpcFp != 0 ? min(\lTmpaFp,\lTmpcFp) : \lTmpaFp},initial={999999}}\,\euro} 
    to \textbf{%
    \cellCopy{r={3-Z},c={4},accum={max(\lTmpaFp,\lTmpcFp)}, initial={-999999}}\,\euro}. 
    In total, accommodation costs \textbf{%
    \cellCopy{r={3-Z},c={6},accum={\lTmpaFp + \lTmpcFp}}\,\euro}
    averaging \textbf{%
    \fpEval{ round(
    \cellCopy{r={3-Z},c={6},accum={\lTmpaFp + \lTmpcFp}} /
    \cellCopy{r={3-Z},c={6},accum={\lTmpaFp + 1}}, 2) }\,\euro}
    per night.},
]{
    hline{1,Z}={.08em},hline{2}, column{2-Z}={r}, column{1}={l}, 
    cell{1}{2-Z}={c}, row{2,7}={abovesep+=6pt,belowsep+=2pt},
    cell{2-Z}{1}={cmd=\quad}, cell{2,7}{1}={c=6}{cmd={},font=\bfseries},
    cell{2-Z}{3,6}={font=\bfseries},
    cell{2-Z}{2}={appto={\,km}}, cell{4-6,9-11}{3}={cmd={$\Delta\,$},appto={\,km}},
    cell{2-Z}{5}={l,preto={$\times$ },appto={ $=$}}, cell{2-Z}{4,6}={appto={\,\euro}},
    cell{4}{3}={preto={\cellCopy{r={3,4},c={2},accum={ abs(\lTmpaFp - \lTmpcFp) }}}},
    cell{5}{3}={preto={\cellCopy{r={4,5},c={2},accum={ abs(\lTmpaFp - \lTmpcFp) }}}},
    cell{6}{3}={preto={\cellCopy{r={5,6},c={2},accum={ abs(\lTmpaFp - \lTmpcFp) }}}},
    cell{9}{3}={preto={\cellCopy{r={8,9},c={2},accum={ abs(\lTmpaFp - \lTmpcFp) }}}},
    cell{10}{3}={preto={\cellCopy{r={9,10},c={2},accum={ abs(\lTmpaFp - \lTmpcFp) }}}},
    cell{11}{3}={preto={\cellCopy{r={10,11},c={2},accum={ abs(\lTmpaFp - \lTmpcFp) }}}},
    cell{3}{6}={preto={\cellCopy{r={3},c={4-5},accum={\lTmpaFp * \lTmpcFp}, initial=1}}},
    cell{4}{6}={preto={\cellCopy{r={4},c={4-5},accum={\lTmpaFp * \lTmpcFp}, initial=1}}},
    cell{5}{6}={preto={\cellCopy{r={5},c={4-5},accum={\lTmpaFp * \lTmpcFp}, initial=1}}},
    cell{6}{6}={preto={\cellCopy{r={6},c={4-5},accum={\lTmpaFp * \lTmpcFp}, initial=1}}},
    cell{8}{6}={preto={\cellCopy{r={8},c={4-5},accum={\lTmpaFp * \lTmpcFp}, initial=1}}},
    cell{9}{6}={preto={\cellCopy{r={9},c={4-5},accum={\lTmpaFp * \lTmpcFp}, initial=1}}},
    cell{10}{6}={preto={\cellCopy{r={10},c={4-5},accum={\lTmpaFp * \lTmpcFp}, initial=1}}},
    cell{11}{6}={preto={\cellCopy{r={11},c={4-5},accum={\lTmpaFp * \lTmpcFp}, initial=1}}},
}
{Location along\\the rivers} & {River\\marker} & {Trip\\distance} 
    & {Price\\per night} &
{Overnight\\stays} & {Total\\price} \\
Mecklenburg Lakeland            \\
Wilderness Haven & 62 && 5  & 0 \\
Adventure Oasis  & 48 && 0  & 2 \\
Forest Escape    & 23 && 7  & 1 \\
Lakeview Camp    & 5  && 11 & 1 \\

Havel River                       \\
Whispering Woods  & 25  && 12 & 0 \\
Sunset Pines      & 58  && 5  & 1 \\
Starlight Meadows & 72  && 8  & 1 \\
Evergreen Glade   & 100 && 16 & 1 \\
\end{tblr}
\end{document}
```

# Regex

> This module provides regular expression testing, extraction of submatches, splitting, and replacement, all acting on token lists. The syntax of regular expressions is mostly a subset of the pcre syntax (and very close to posix), with some additions due to the fact that TEX manipulates tokens rather than characters. For performance reasons, only a limited set of features are implemented. Notably, back-references are not supported.

- see [Regular Expressions (Regex) ch. 13 p. 87](http://mirrors.ctan.org/macros/latex/contrib/functional/functional.pdf#page=87) in functional documentation

- Uses pcre syntax
- only a limited set of features are implemented, back-references are not supported

# Extract numbers

```latex
\documentclass{standalone} \title{}

\usepackage{tabularray}
\UseTblrLibrary{functional}
\ExplSyntaxOn
\regexConst\lNumberPattern {(\d+)}
\fpNew\nCell
\prgNewConditional\containsNumber{ m }{
\regexVarExtractOnceTF\lNumberPattern{ #1 }\lTmpaSeq{ 
    \fpSet\nCell{ \seqVarItem\lTmpaSeq{1} }  
    \prgReturn\cTrueBool
}{
    \fpZero\nCell
    \prgReturn\cFalseBool  
}}
\regexConst\gParenthesePattern {\((.+?)\)}
\prgNewFunction\rowRelativeAndAbsoluteRangesToList{ m }{
\tlSet\lTmpaTl{ #1 }
\regexVarReplaceAll\gParenthesePattern{ \c{intEval}\cB\{ \1 - 1 \cE\} }\lTmpaTl
\prgReturn{ \tlUse\lTmpaTl }
}
\ExplSyntaxOff
\begin{document}
\containsNumberT{12 km} {\fpUse\nCell}
,11-\rowRelativeAndAbsoluteRangesToList{(12)-(3)},
\end{document}
```