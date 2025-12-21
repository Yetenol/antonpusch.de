---
date: "2025-07-17T08:13:58.378+02:00"
title: "Layout the table"
description: "-"
dg-publish: true
dg-folder: latex/tables
---

![figure table layout 4.svg](../../figure-table-layout-4.svg)

```latex
\documentclass{standalone} \title{table layout 4}
\usepackage{pgfplotstable,tabularray,pgffor}
\renewcommand{\thetable}{3.1\alph{table}}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style={begin table=\begin{#1}{},end table=\end{#1},skip coltypes,environment/.style={}},
    csv/.style = {col sep = comma, row sep = newline, column type = {r}, },
    split2/.style = {
        create on use/blank/.style = {},
        columns/blank/.style={column name={}},
        columns={[index]0,[index]1,blank,[index]0,[index]1},
        split/.list={00,10,20,31,41},
        tblr={ hline{1-Z}={3}{0pt}, column{3}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r} }},
    split/.style 2 args={display columns/#1/.style={select equal part entry of={#2}{2} }},
    rename2/.style={columns={[index]0,[index]1,[index]0,[index]1},split/.list={00,10,21,31}},
}
\SetTblrInner{ hline{1,Z}={.08em},hline{3}, }
\SetTblrOuter{ tall, caption }
\begin{document}
\pgfplotstabletypeset[csv,split2,tblr={}]{data.csv}
\end{document}
```

```latex
\documentclass{standalone} \title{}
\usepackage{tabularray,tikz}
\begin{document}
\begin{tblr}[tall, caption]{
    column{1-Z}={r,cmd=\pgfmathprintnumber},
    row{1}={c,cmd={}}, hline{1,Z}={.08em},hline{2},
}
t       & U              \\ 
10      & 7.57858283e-01 \\              
25      & 5.00000000e-01 \\              
81      & 2.87174589e-01 \\              
289     & 1.43587294e-01 \\              
1089    & 4.41941738e-02 \\              
4225    & 1.69802322e-02 \\              
16641   & 8.20091159e-03 \\              
66049   & 3.90625000e-03 \\              
263169  & 1.95312500e-03 \\              
1050625 & 9.76562500e-04 \\              
\end{tblr}
\end{document}
```


- set baseline

![figure table layout 1.svg](../../figure-table-layout-1.svg)

```latex
\documentclass{article} \title{table layout 1} 
\usepackage{pgfplotstable,tabularray,pgffor}
\renewcommand{\thetable}{3.1\alph{table}} \pagestyle{empty}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    text cells/.style = {string type,tblr={ column{1,Z}={c} }},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style={begin table=\begin{#1}{},end table=\end{#1},skip coltypes,environment/.style={}},
    caption/.style = {tblr outer={tall,caption={#1}}},
    hlines/.style={tblr={ hline{1,Z}={.08em},hline{2}={.05em} }},
    csv/.style = {col sep = comma, row sep = newline, column type = {r}, },
    numberic cells/.style = {numeric type, tblr={ column{1,Z}={r} }},
    shade 2nd/.style = {tblr={ row{even} = {gray9} }},
    dash 3rd/.style = {every nth row = {3}{before row = \hline[dashed]}},
    german/.style = {dec sep={,\!}, 1000 sep ={\,}},
    center table/.style = {
        begin table/.add = {\parskip=0pt\par\nopagebreak\centering{}}{},
        end table/.add = {}{\par\noindent\ignorespacesafterend{}}  },
    split2/.style = {
        create on use/blank/.style = {},
        columns/blank/.style={column name={}},
        columns={[index]0,[index]1,blank,[index]0,[index]1},
        split/.list={00,10,20,31,41},
        tblr={ hline{1-Z}={3}{0pt}, column{3}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r} }},
    split3/.style = {
        create on use/blank/.style = {create col/expr = {0}},
        columns={[index]0,[index]1,blank,[index]0,[index]1,blank,[index]0,[index]1},
        display columns/0/.style={select equal part entry of={0}{3}},% first part of 'A'
        display columns/1/.style={select equal part entry of={0}{3}},% first part of 'B'
        display columns/2/.style={select equal part entry of={0}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{3}},% second part of 'A'
        display columns/4/.style={select equal part entry of={1}{3}},% second part of 'B'
        display columns/5/.style={select equal part entry of={1}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/6/.style={select equal part entry of={2}{3}},% third part of 'A'
        display columns/7/.style={select equal part entry of={2}{3}},% third part of 'B'
        tblr={ hline{1-Z}={3,6}{0pt}, column{3,6}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r}  }},
    split/.style 2 args={display columns/#1/.style={select equal part entry of={#2}{2} }},
    rename2/.style={columns={[index]0,[index]1,[index]0,[index]1},split/.list={00,10,21,31}},
    csv, numberic cells, hlines, center table, caption,
}
\begin{document}
\noindent
\pgfplotstabletypeset[split2]{data.csv}
\vspace{1em}
\pgfplotstabletypeset[split3]{data.csv}
\end{document}
```

![figure table layout 2.svg](../../figure-table-layout-2.svg)

```latex
\documentclass{article} \title{table layout 2} 
\usepackage{pgfplotstable,tabularray}
\renewcommand{\thetable}{3.2\alph{table}} \pagestyle{empty}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    text cells/.style = {string type,tblr={ column{1,Z}={c} }},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style={begin table=\begin{#1}{},end table=\end{#1},skip coltypes,environment/.style={}},
    caption/.style = {tblr outer={tall,caption={#1}}},
    hlines/.style={tblr={ hline{1,Z}={.08em},hline{2}={.05em} }},
    csv/.style = {col sep = comma, row sep = newline, column type = {r}, },
    numberic cells/.style = {numeric type, tblr={ column{1,Z}={r} }},
    shade 2nd/.style = {tblr={ row{even} = {gray9} }},
    dash 3rd/.style = {every nth row = {3}{before row = \hline[dashed]}},
    german/.style = {dec sep={,\!}, 1000 sep ={\,}},
    center table/.style = {
        begin table/.add = {\parskip=0pt\par\nopagebreak\centering{}}{},
        end table/.add = {}{\par\noindent\ignorespacesafterend{}}  },
    split2/.style = {
        create on use/blank/.style = {create col/expr = {0}},
        columns={[index]0,[index]1,blank,[index]0,[index]1},
        display columns/0/.style={select equal part entry of={0}{2}},% first part of 'A'
        display columns/1/.style={select equal part entry of={0}{2}},% first part of 'B'
        display columns/2/.style={select equal part entry of={0}{2}},% blank column
        columns/blank/.style={column name={},assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{2}},% second part of 'A'
        display columns/4/.style={select equal part entry of={1}{2}},% second part of 'B'
        tblr={ hline{1-Z}={3}{0pt}, column{3}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r} }},
    split3/.style = {
        create on use/blank/.style = {create col/expr = {0}},
        columns={[index]0,[index]1,blank,[index]0,[index]1,blank,[index]0,[index]1},
        display columns/0/.style={select equal part entry of={0}{3}},% first part of 'A'
        display columns/1/.style={select equal part entry of={0}{3}},% first part of 'B'
        display columns/2/.style={select equal part entry of={0}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{3}},% second part of 'A'
        display columns/4/.style={select equal part entry of={1}{3}},% second part of 'B'
        display columns/5/.style={select equal part entry of={1}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/6/.style={select equal part entry of={2}{3}},% third part of 'A'
        display columns/7/.style={select equal part entry of={2}{3}},% third part of 'B'
        tblr={ hline{1-Z}={3,6}{0pt}, column{3,6}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r}  }},
    csv, numberic cells, hlines, center table, caption,
}
\begin{document}
\noindent
\pgfplotstabletypeset[split2]{data.csv}
\vspace{1em}
\pgfplotstabletypeset[split3]{data.csv}
\end{document}
```


# Main example

![figure table layout 3.svg](../../figure-table-layout-3.svg)

```latex
\documentclass{article} \title{table layout 3}
\usepackage{pgfplotstable,tabularray,float} \pagestyle{empty}
\UseTblrLibrary{booktabs}
\UseTblrLibrary{booktabs}\SetTblrInner{column{1,Z}={c}}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    csv/.style = {col sep = comma, row sep = newline, column type = {r}, numeric type},
    tblr/.style = {begin table = \begin{tblr}{}, end table = \end{tblr}, skip coltypes},
    hlines/.style={every table/.append code=\SetTblrInner{
        hline{1,Z}={\heavyrulewidth},hline{2}={\lightrulewidth} }},
    dash3rd/.style = {every nth row = {3}{before row = \hline[dashed]}},
    centering/.style = {
        begin table/.add = {\parskip=0pt\par\nopagebreak\centering{}}{},
        end table/.add = {}{\par\noindent\ignorespacesafterend{}}  },
    split2/.style = {
        create on use/blank/.style = {create col/expr = {0}},
        columns={[index]0,[index]1,blank,[index]0,[index]1},
        display columns/0/.style={select equal part entry of={0}{2}},% first part of 'A'
        display columns/1/.style={select equal part entry of={0}{2}},% first part of 'B'
        display columns/2/.style={select equal part entry of={0}{2}},% blank column
        columns/blank/.style={column name={},assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{2}},% second part of 'A'
        display columns/4/.style={select equal part entry of={1}{2}},% second part of 'B'
        every table/.append code=\SetTblrInner{
            hline{1-Z}={3}{0pt}, column{3}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r}  }},
    split3/.style = {
        create on use/blank/.style = {create col/expr = {0}},
        columns={[index]0,[index]1,blank,[index]0,[index]1,blank,[index]0,[index]1},
        display columns/0/.style={select equal part entry of={0}{3}},% first part of 'A'
        display columns/1/.style={select equal part entry of={0}{3}},% first part of 'B'
        display columns/2/.style={select equal part entry of={0}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{3}},% second part of 'A'
        display columns/4/.style={select equal part entry of={1}{3}},% second part of 'B'
        display columns/5/.style={select equal part entry of={1}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/6/.style={select equal part entry of={2}{3}},% third part of 'A'
        display columns/7/.style={select equal part entry of={2}{3}},% third part of 'B'
        every table/.append code=\SetTblrInner{
            hline{1-Z}={3,6}{0pt}, column{3,6}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r}  }},
}
\begin{document}

\pgfplotstabletypeset[csv,tblr,centering,hlines,split2]{data.csv}
\vspace{1cm}
\begin{table}[H]
\pgfplotstabletypeset[csv,tblr,centering,hlines,split3]{data.csv}
\caption{This table was spread across three columns}
\end{table}

\end{document}
```