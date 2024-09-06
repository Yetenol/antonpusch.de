
![table accumulate 1.svg](./content/attachments/table%20accumulate%201.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{5.1}
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
\end{document}
```