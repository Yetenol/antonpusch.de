


![minimal 72.svg](./content/attachments/minimal%2072.svg)

```latex
\documentclass{article}\pagestyle{empty}\renewcommand{\thetable}{1\alph{table}}
\usepackage{pgfplotstable,tabularray}
\UseTblrLibrary{diagbox}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    text cells/.style = {string type,tblr={ column{1,Z}={c} }},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style={begin table=\begin{#1}{},end table=\end{#1},skip coltypes,environment/.style={}},
    caption/.style = {tblr outer={tall,caption={#1}}},
    hlines/.style={tblr={ hline{1,Z}={.08em},hline{2}={.05em} }},
    hasrowname/.style={every first column/.append style={string type}, tblr={ column{1}={l} }},
    cross/.style={hasrowname, tblr={ vline{2}, hline{2} }},
    frame/.style={tblr={ vline{1,Z}={.08em},hline{1,Z}={.08em} }},
    innergrid/.style={tblr={ vline{2-Y},hline{2-Y} }},
    boldcolname/.style={tblr={ row{1}={font=\bfseries} }},
    boldrowname/.style={hasrowname, tblr={ column{1}={font=\bfseries} }},
    tex,tblr,text cells,caption
}
\begin{document}
\noindent
\pgfplotstabletypeset[hlines, boldcolname]{
Name & Unicode & Alt code \\
$\alpha$ alpha & U+03B1 & Alt 224 \\
$\gamma$ gamma & U+0393 & Alt 226 \\
$\delta$ delta & U+03B4 & Alt 235 \\
}
\hspace{1cm}
\begin{tblr}[tall,caption]{colspec={lcc},vline{2},hline{2}}
 & Word & Docs \\
Collab. & ++ & ++ \\
Price & -- & ++ \\
Simple & $\circ$ & + \\
\end{tblr}
\hspace{1cm}
\begin{tblr}[tall,caption]{colspec={lccc},vline{2},hline{2}}
\diagbox{$x$}{$y$} &              0 &              1 &              2 \\
0                  & $^1\!/_{\!16}$ & $^1\!/_{\!16}$ &            $0$ \\
1                  & $^3\!/_{\!16}$ & $^3\!/_{\!16}$ & $^1\!/_{\!16}$ \\
2                  & $0$ & $^4\!/_{\!16}$ & $^3\!/_{\!16}$ \\
\end{tblr}
\end{document}
```