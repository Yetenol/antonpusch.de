---
dg-publish: true
---

- set baseline

![minimal 61.svg](./attachments/minimal%2061.svg)

```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{4\alph{table}}
\usepackage{pgfplotstable,tabularray,pgffor}
\def\x{0}
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
        display columns/0/.style={select equal part entry of={0}{3}},% first part of `A'
        display columns/1/.style={select equal part entry of={0}{3}},% first part of `B'
        display columns/2/.style={select equal part entry of={0}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{3}},% second part of `A'
        display columns/4/.style={select equal part entry of={1}{3}},% second part of `B'
        display columns/5/.style={select equal part entry of={1}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/6/.style={select equal part entry of={2}{3}},% third part of `A'
        display columns/7/.style={select equal part entry of={2}{3}},% third part of `B'
        tblr={ hline{1-Z}={3,6}{0pt}, column{3,6}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r}  }},
    split/.style 2 args={display columns/#1/.style={select equal part entry of={#2}{2} }},
    rename2/.style={columns={[index]0,[index]1,[index]0,[index]1},split/.list={00,10,21,31}},
    csv, numberic cells, hlines, center table, caption,
}
\begin{document}
\noindent
% \pgfkeys{/my key}
\pgfkeys{/my key/.code/.evaluated/.list={{int(4/3)}},
    /my key=1,
}
\pgfkeys{/my key/.get=\mymacro}
\mymacro

\pgfmathparse{int(2/3)} \pgfmathresult


\noindent
\pgfplotstabletypeset[split2]{resources/data.csv}
\vspace{1em}
\pgfplotstabletypeset[split3]{resources/data.csv}
\end{document}
```


```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{4\alph{table}}
\usepackage{pgfplotstable,tabularray}
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
        display columns/0/.style={select equal part entry of={0}{2}},% first part of `A'
        display columns/1/.style={select equal part entry of={0}{2}},% first part of `B'
        display columns/2/.style={select equal part entry of={0}{2}},% blank column
        columns/blank/.style={column name={},assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{2}},% second part of `A'
        display columns/4/.style={select equal part entry of={1}{2}},% second part of `B'
        tblr={ hline{1-Z}={3}{0pt}, column{3}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r} }},
    split3/.style = {
        create on use/blank/.style = {create col/expr = {0}},
        columns={[index]0,[index]1,blank,[index]0,[index]1,blank,[index]0,[index]1},
        display columns/0/.style={select equal part entry of={0}{3}},% first part of `A'
        display columns/1/.style={select equal part entry of={0}{3}},% first part of `B'
        display columns/2/.style={select equal part entry of={0}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{3}},% second part of `A'
        display columns/4/.style={select equal part entry of={1}{3}},% second part of `B'
        display columns/5/.style={select equal part entry of={1}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/6/.style={select equal part entry of={2}{3}},% third part of `A'
        display columns/7/.style={select equal part entry of={2}{3}},% third part of `B'
        tblr={ hline{1-Z}={3,6}{0pt}, column{3,6}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r}  }},
    csv, numberic cells, hlines, center table, caption,
}
\begin{document}
\noindent
\pgfplotstabletypeset[split2]{resources/data.csv}
\vspace{1em}
\pgfplotstabletypeset[split3]{resources/data.csv}
\end{document}
```


# Main example

![minimal 30.svg](./attachments/minimal%2030.svg)

```latex
\documentclass{article}
\pagestyle{empty}
\usepackage{pgfplotstable,tabularray,float}
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
        display columns/0/.style={select equal part entry of={0}{2}},% first part of `A'
        display columns/1/.style={select equal part entry of={0}{2}},% first part of `B'
        display columns/2/.style={select equal part entry of={0}{2}},% blank column
        columns/blank/.style={column name={},assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{2}},% second part of `A'
        display columns/4/.style={select equal part entry of={1}{2}},% second part of `B'
        every table/.append code=\SetTblrInner{
            hline{1-Z}={3}{0pt}, column{3}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r}  }},
    split3/.style = {
        create on use/blank/.style = {create col/expr = {0}},
        columns={[index]0,[index]1,blank,[index]0,[index]1,blank,[index]0,[index]1},
        display columns/0/.style={select equal part entry of={0}{3}},% first part of `A'
        display columns/1/.style={select equal part entry of={0}{3}},% first part of `B'
        display columns/2/.style={select equal part entry of={0}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/3/.style={select equal part entry of={1}{3}},% second part of `A'
        display columns/4/.style={select equal part entry of={1}{3}},% second part of `B'
        display columns/5/.style={select equal part entry of={1}{3},column name={},
            assign cell content/.style = {/pgfplots/table/@cell content = {}}},
        display columns/6/.style={select equal part entry of={2}{3}},% third part of `A'
        display columns/7/.style={select equal part entry of={2}{3}},% third part of `B'
        every table/.append code=\SetTblrInner{
            hline{1-Z}={3,6}{0pt}, column{3,6}={wd=.5cm}, row{1}={halign=c}, row{2-Z}={halign=r}  }},
}
\begin{document}

\pgfplotstabletypeset[csv,tblr,centering,hlines,split2]{resources/data.csv}
\vspace{1cm}
\begin{table}[H]
\pgfplotstabletypeset[csv,tblr,centering,hlines,split3]{resources/data.csv}
\caption{This table was spread across three columns}
\end{table}

\end{document}
```