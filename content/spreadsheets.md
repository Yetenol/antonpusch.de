---
title: "Spreadsheets - Calculate sum, mean, standard deviation, max, and min across selection of cells"
dg-publish: true
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

![table accumulate sum.svg](./attachments/table%20accumulate%20sum.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{6.1}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\ExplSyntaxOn
\clistNew\columnList \clistNew\rowList \fpNew\nAccum \fpNew\nCell 
\regexConst\lNumberPattern {([-+]?(?:\d*\.\d+|\d*))} \regexConst\gParenthesePattern {\((.+?)\)}
\prgNewFunction\tblrRangesToList{ mm }{ 
    \__tblr_get_childs:nx{#1}{#2}  \prgReturn{\tlUse\l_tblr_childs_clist} }
\prgNewFunction\relativeAndTblrRangesToList{ mmm }{
    \tlIfEmptyTF{#1} { \tlSet\lTmpaTl{ (0) } }{ \tlSet\lTmpaTl{ #1 } }
    \regexVarReplaceAll\gParenthesePattern{ \c{intEval}\cB\{ \1 + \c{arabic}\{#2\} \cE\} }\lTmpaTl
    \tlSet\lTmpaTl{ \evalWhole{ \tlUse\lTmpaTl }}
    \tlSet\lTmpaTl{ \tblrRangesToList{ \tlUse\lTmpaTl }{ \arabic{#3} } }
    \prgReturn{ \tlUse\lTmpaTl }  }
\prgNewConditional\containsNumber{ m }{
    \regexVarExtractOnceTF\lNumberPattern{ #1 }\lTmpaSeq{ 
        \fpSet\nCell{ \seqVarItem\lTmpaSeq{1} }  \prgReturn\cTrueBool 
    }{  \fpZero\nCell \prgReturn\cFalseBool }}
\prgNewFunction\cellAccum{ mmmm }{
    \clistSet\rowList{ \relativeAndTblrRangesToList{#1}{rownum}{rowcount} } 
    \clistSet\columnList{ \relativeAndTblrRangesToList{#2}{colnum}{colcount} }
    \tlIfEmptyTF{#4}{ \fpZero\nAccum }{ \fpSet\nAccum{#4} }
    \clistVarMapVariable \rowList \lTmpaInt{
        \clistVarMapVariable \columnList \lTmpbInt{
            \containsNumberT{ \cellGetText{\lTmpaInt}{\lTmpbInt} }{
                \fpSet\nAccum{ #3 } } } }
    \prgReturn{ \fpEval{ \nAccum }}}
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
\end{document}
```

# Add expenses

Calculate the following values, with row number $r$:

- Trip distance: $dist_r \coloneqq \left| marker_{r - 1} - marker_r \right|$ for $r \in \{ 4, 5, 6, 9, 10, 11 \}$ 
- Total price: $total_r \coloneqq  price_r \cdot  overnights_r$ for $r \in \{ 3, 4, \ldots, 11 \}$ 
- Distance on Mecklenburg Lakeland: $meck \coloneqq \left| marker_3 - marker_6 \right|$ 
- Distance on Havel River: $havel \coloneqq \left| marker_8 - marker_{11}  \right|$ 
- Minimum non-zero overnight price: $min \coloneqq \min \big( \{ price_r \in Price \mid price_c > 0, r \in \{ 3, 4, \ldots, 11 \} \big)$ 
- Maximum overnight price: $max \coloneqq \max(price_3, \ldots, price_{11} )$
- Total accommodation cost: $accom \coloneqq \sum_{r = 3}^{11} total_r$
- Daily average: $avg \coloneqq accom \div \operatorname{count-nonnull}(total_3, \ldots, total_{11} )$ 

![table accumulate trip expenses.svg](./attachments/table%20accumulate%20trip%20expenses.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{6.2}
\usepackage{tabularray}
\UseTblrLibrary{functional,siunitx}
\ExplSyntaxOn
\clistNew\columnList \clistNew\rowList \fpNew\nAccum \fpNew\nCell 
\intNew\nRow \intNew\nColumn
\regexConst\lNumberPattern {(\d+)} \regexConst\gParenthesePattern {\((.+?)\)}
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
    \prgReturn{ \fpEval{ round(\nAccum,2) }}}
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption={Calculate non-bold trip expenses, distances},note{}={
We travel 
\cellAccum{3,6}{2}{abs(\nCell-\nAccum)}{}~km 
on the Mecklenburg Lakeland and 
\cellAccum{8,11}{2}{abs(\nCell-\nAccum)}{}~km 
on the Havel River. Overnight prices range from 
\cellAccum{3-11}{4}{\nCell != 0 ? min(\nAccum,\nCell) : \nAccum}{\cInfFp}~EUR 
to 
\cellAccum{3-11}{4}{max(\nAccum,\nCell)}{\cMinusInfFp}~EUR. 
In total, accommodation costs 
\cellAccum{3-11}{6}{\nAccum+\nCell}{}~EUR
averaging 
\cellAccum{3-11}{6}{\nAccum+1}{0}~EUR
per night.},
]{
hline{1,Z}={.08em},hline{2}, column{2-Z}={r}, column{1}={l}, 
cell{1}{2-Z}={c}, row{2,7}={abovesep+=6pt,belowsep+=2pt},
cell{2-Z}{1}={cmd=\quad}, cell{2,7}{1}={c=6}{cmd={},font=\bfseries},
cell{2-Z}{2,4,5}={font=\bfseries},
cell{4-6,9-11}{3}={cmd={\fpEval{
    \cellAccum{(-1)-(0)}{2}{abs(\nCell-\nAccum)}{}  }}},
cell{3-11}{6}={cmd={\fpEval{ 
    \cellAccum{}{4-5}{\nAccum * \nCell}{1}  }}},
}
{Location along\\the rivers} & {River\\marker} & {Trip\\distance} & {Price\\per night} &
{Overnight\\stays} & {Total\\price} \\
Mecklenburg Lakeland \\
Wilderness Haven & 62 && 5  & 0 \\
Adventure Oasis  & 48 && 0  & 2 \\
Forest Escape    & 23 && 7  & 1 \\
Lakeview Camp    & 5  && 11 & 1 \\

Havel River \\
Whispering Woods  & 25  && 12 & 0 \\
Sunset Pines      & 66  && 5  & 1 \\
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
\documentclass{standalone}
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