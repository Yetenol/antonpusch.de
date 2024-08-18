---
title: "Add title numbers, caption, and reference the table elsewhere"
dg-publish: true
---

Table numbers allow cross-referencing and add a entry in *List of Tables*.

Use essential styles and hlines from [Create a simple table with borders](./create%20a%20simple%20table%20with%20borders.md)

Setup styles for referencing
```latex
\pgfplotstableset{
    caption/.style = {tblr outer={tall,caption={#1}}},
    entry/.style = {tblr outer={tall,entry={#1}}},
    label/.style = {tblr outer={tall,label={#1}}},
    center table/.style = {
        begin table/.prefix={ \parskip=0pt\par\nopagebreak\centering{} },
        end table/.append={ \par\noindent\ignorespacesafterend{} }},
}
```

Show just a table **number**, see $\mathrm{2a}$
- Use style **caption** without a value

Add table **caption**, see $\mathrm{2b, 2c}$
- Caption is wrapped to table width
- Use style **caption=People's identifiers** 

Override the **entry** in the *List of Tables*, see $\mathrm{2b}$
- Use style **entry=IDS** and optionally caption

**List** all tables with table numbers
- Write `\listoftables` and the end of the document

**Reference** a table using **label**, see $\mathrm{2c}$
- See [Layout the table](./layout%20the%20table.md) for clickable, colored links
- Write `\ref{tab:identifiers}` to reference the table elsewhere
- Use style **label=tab:identifiers** and optionally caption
```latex
See table \ref{tab:identifiers} for details. \\
\pgfplotstabletypeset[caption=People's identifiers,label=tab:identifiers]{…}
```

Put table in a **floating** environment, see $\mathrm{2d}$
- table reserves the entire line width
- See [Layout the table](./layout%20the%20table.md) to set default placement specifiers
```latex
See table \ref{tab:identifiers} for details.
\begin{table}[hbp]
    \caption{People's identifiers}\label{tab:identifiers}
    \pgfplotstabletypeset[center table]{…}
\end{table}
```

Demos with tex, text cells, and hlines styles from [Create a simple table with borders](./create%20a%20simple%20table%20with%20borders.md) as default:
![minimal 52.svg](./attachments/minimal%2052.svg)

```latex
\documentclass{article}\pagestyle{empty}\renewcommand{\thetable}{2\alph{table}}
\usepackage{pgfplotstable,tabularray,hyperref}
\hypersetup{colorlinks=true, linkcolor=blue}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    text cells/.style = {string type,tblr={ column{1,Z}={c} }},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style={begin table=\begin{#1}{},end table=\end{#1},skip coltypes,environment/.style={}},
    caption/.style = {tblr outer={tall,caption={#1}}},
    entry/.style = {tblr outer={tall,entry={#1}}},
    label/.style = {tblr outer={tall,label={#1}}},
    hlines/.style={tblr={ hline{1,Z}={.08em},hline{2}={.05em} }},
    center table/.style = {
        begin table/.add = {\parskip=0pt\par\nopagebreak\centering{}}{},
        end table/.add = {}{\par\noindent\ignorespacesafterend{}}  },
    tex,tblr,text cells,hlines
}
\begin{document}
Each person gets assigned a number listed in table \ref{tab:identifiers} on page \pageref{tab:identifiers}.

\noindent
\pgfplotstabletypeset[caption]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
}
\hspace{1cm}
\pgfplotstabletypeset[caption=People's identifiers,entry=IDs]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
}
\hspace{1cm}
\pgfplotstabletypeset[caption=Identifiers,label=tab:identifiers]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hata \\
    Lara & $\triangle$ \\
}
\begin{table}[hbp]
    \caption{People's identifiers}\label{tab:identifiers2}
    \pgfplotstabletypeset[center table]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
    }
\end{table}
\listoftables
\end{document}
```