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
\documentclass{standalone} \renewcommand{\thetable}{5.1}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\ExplSyntaxOn
\clistNew\columnList \clistNew\rowList \fpNew\nAccum \fpNew\nCell
\prgNewFunction\rowRangesToList{ n }{
\__tblr_get_childs:nx{ #1 }{ \therowcount } 
\prgReturn{\l_tblr_childs_clist}  
}
\prgNewFunction\ColumnRangesToList{ n }{ 
\__tblr_get_childs:nx{ #1 }{ \thecolcount }
\prgReturn{\l_tblr_childs_clist}
}
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
\prgReturn{ \fpEval{ round(\nAccum,2) }} 
}
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

- Trip distance: $dist_r \coloneqq \left| marker_{r - 1} - marker_r \right|$ for $r \in \{ 4, \ldots,  6,  9, \ldots,  11 \}$ 
- Total price: $total_r \coloneqq  price_r \cdot  overnights_r$ for $r \in \{ 3, \ldots,  6,  8, \ldots,  11 \}$ 
- Distance on Mecklenburg Lakeland: $meck \coloneqq \sum_{r = 4}^{6} dist_r$ 
- Distance on Havel River: $havel \coloneqq \sum_{r = 9}^{11} dist_r$ 
- Minimum overnight price: $min \coloneqq \min(price_3, \ldots, price_{11} )$ 
- Maximum overnight price: $max \coloneqq \max(price_3, \ldots, price_{11} )$
- Total accommodation cost: $accom \coloneqq \sum_{r = 3}^{11} total_r$
- Daily average: $avg \coloneqq accom \div \operatorname{count-nonnull}(total_3, \ldots, total_{11} )$ 

![table accumulate trip expenses.svg](./attachments/table%20accumulate%20trip%20expenses.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{5.2}
\usepackage{tabularray}
\UseTblrLibrary{functional,siunitx}
\ExplSyntaxOn
\clistNew\columnList \clistNew\rowList \fpNew\nAccum \fpNew\nCell
\prgNewFunction\rowRangesToList{ n }{
\__tblr_get_childs:nx{ #1 }{ \therowcount } 
\prgReturn{\l_tblr_childs_clist}  
}
\prgNewFunction\ColumnRangesToList{ n }{ 
\__tblr_get_childs:nx{ #1 }{ \thecolcount }
\prgReturn{\l_tblr_childs_clist}
}
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
\prgReturn{ \fpEval{ round(\nAccum,2) }} 
}
\prgNewFunction\cellRel{ mm }{
\intSet\lTmpaInt{ \therownum + #1 }
\intSet\lTmpbInt{ \thecolnum + #2 }
\intSet\lTmpcInt{ \cellGetText{\intUse\lTmpaInt}{\intUse\lTmpbInt} }
\prgReturn{\intUse\lTmpcInt}
}
\ExplSyntaxOff
\begin{document}
\begin{tblr}[tall,caption={Calculate non-bold trip expenses, distances},
note{}={We travel \qty{30}{km} on the Mecklenburg Lakeland and \qty{20}{km} on the Havel River. Overnight prices range from \qty{0}{EUR} to \qty{16}{EUR}. In total, accommodation costs \qty{120}{EUR} averaging \qty{14.3}{EUR} per night.},
]{
hline{1,Z}={.08em},hline{2}, column{2-Z}={r}, column{1}={l}, 
cell{1}{2-Z}={c}, row{2,7}={abovesep+=6pt,belowsep+=2pt},
cell{2-Z}{1}={cmd=\quad}, cell{2,7}{1}={c=6}{cmd={},font=\bfseries},
cell{2-Z}{2,4,5}={font=\bfseries},
cell{4-6,9-11}{3}={cmd={\fpEval{
    abs(\cellRel{-1}{-1} - \cellRel{0}{-1})  }}},
cell{3-6,8-11}{6}={cmd={\fpEval{ 
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

# Extract numbers

```latex
\documentclass{standalone}
\usepackage{tabularray}
\ExplSyntaxOn

\ExplSyntaxOff
\begin{document}

\end{document}
```