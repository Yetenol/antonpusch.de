---
title: "Process, and format values from files"
dg-publish: true
---
# Main example

3a: Legende unter Tabelle
3b: Add index with line,
Calculate sum, Standardabweichung, Varianz in footer with line
3c: Csv file

call snippet style raw snippet
call set environment->lock environment

![minimal 67.svg](./attachments/minimal%2067.svg)

Faked second table
```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{3\alph{table}}
\usepackage{pgfplotstable,tabularray,mathtools,amssymb,amsfonts}
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
    numeric cells/.style = {numeric type, tblr={ column{1,Z}={r} }},
    shade 2nd/.style = {tblr={ row{even} = {gray9} }},
    dash 3rd/.style = {every nth row = {3}{before row = \hline[dashed]}},
    german/.style = {dec sep={,\!}, 1000 sep ={\,}},
    rename column/.style 2 args = {assign column name/.append style={
        /pgfplots/table/column name/.add={\ifx##1#1#2\else}{\fi}}},
    column unit/.style 2 args = {tblr={ cell{2-Z}{#1}={appto={\,#2}} }},
    row counter/.style={tblr = {column{2}={r}},
    create on use/id/.style = {create col/expr = {int(\pgfplotstablerow+1)}},
    columns/id/.style={column name={\#}, numeric type},
    columns={id,[index]0,[index]1}, },
    data table/.style={csv, hlines, dash 3rd, numeric cells},
    legende/.style={tblr outer={ remark{$t$} = {Time when datapoint was meassured},
    remark{$U_\mathrm{mess}$} = {Voltage meassured} }},
    rename column/.list={{t}{$t$ in ms},{U}{$U_\mathrm{mess}$ in V}},
    snippet/.style = {col sep={&},verb string type, tblr={vlines={0pt},column{1}={l,cmd=\texttt}}},
    stats/.style={tblr={hline{12}},
        every row 10 column 0/.style={assign cell content/.style={/pgfplots/table/@cell content={$\Sigma$}}},
        every row 11 column 0/.style={assign cell content/.style={/pgfplots/table/@cell content={$\bar{x}$}}} },
    caption, tblr={baseline=T},
}
\begin{document}
\noindent
\pgfplotstabletypeset[data table, legende]{resources/data.csv}
\hspace{1cm}
\pgfplotstableset{csv}
\pgfplotstableread{resources/data.csv}{\output}
\pgfplotstableread[tex]{
t & U \\
 & 1.76483 \\
 & 0.176483 \\
}\statsLines
\pgfplotstablevertcat{\output}{\statsLines}
\pgfplotstabletypeset[csv, numeric cells, stats, row counter, hlines, dash 3rd, 
    int detect, sci subscript, zerofill,
    tblr={cell{2-Z}{1-Z}={r}},  ]\output
\hspace{1cm}
\pgfplotstabletypeset[snippet, caption=Data.csv]{resources/data.csv}
\end{document}
```

```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{3\alph{table}}
\usepackage{pgfplotstable,tabularray,mathtools,amssymb,amsfonts}
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
    rename column/.style 2 args = {assign column name/.append style={
        /pgfplots/table/column name/.add={\ifx##1#1#2\else}{\fi}}},
    column unit/.style 2 args = {tblr={ cell{2-Z}{#1}={appto={\,#2}} }},
    row counter/.style={tblr = {column{2}={r},vline{2}={solid}},
    create on use/id/.style = {create col/expr = {\pgfplotstablerow+1}},
    columns/id/.style={column name={\#}},
    columns={id,[index]0,[index]1}, },
    data table/.style={hlines, dash 3rd},
    legende/.style={tblr outer={ remark{$t$} = {Time when datapoint was meassured},
    remark{$U_\mathrm{mess}$} = {Voltage meassured} }},
    rename column/.list={{t}{$t$ in ms},{U}{$U_\mathrm{mess}$ in V}},
    snippet/.style = {col sep={&},verb string type, tblr={vlines={0pt},column{1}={l,cmd=\texttt}}},
    csv, numberic cells, caption, tblr={baseline=T},
}
\begin{document}
\noindent
\def\x{0}
\pgfplotstabletypeset[data table, legende]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[data table, german, int detect, row counter, columns/U/.style={sci subscript}]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[snippet, caption=Data.csv]{resources/data.csv}
\end{document}
```

calculate sum, mean, standard deviation under table
- [Add rows for sum/mean/std at end of pgfplotstable - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/179177/add-rows-for-sum-mean-std-at-end-of-pgfplotstable)
- [\[Pgfplots-features\] Simple calculations on columns of data](https://pgfplots-features.narkive.com/tu1Qxhx5/simple-calculations-on-columns-of-data)

combine files
```latex
\pgfplotstableread{resources/data.csv}\output
\pgfplotstablevertcat{\output}{resources/stats.csv}
\pgfplotstabletypeset[csv]\outp
```

```latex
\pgfplotstabletypeset[
    calc/.style 2 args={create col/assign/.code={%
    \getthisrow{#1}\entry
    \ifnum\pgfplotstablerow>0
    \pgfmathsetmacro{\entry}{#2(\entry,\pgfmathaccuma)}%
    \fi
    \edef\pgfmathaccuma{\entry}
    \xdef\MAXVAL{\pgfmathaccuma}
    \pgfkeyslet{/pgfplots/table/create col/next content}\entry
    }},
    create max column/.style={create on use/max(#1)/.style={calc={#1}{max}}},
    create min column/.style={create on use/min(#1)/.style={calc={#1}{min}}},
    create sum column/.style={create on use/sum(#1)/.style={calc={#1}{add}}},
    create max column=Val, create min column=Val, create sum column=Val,
    columns={Val,max(Val),min(Val),sum(Val)},
]{testdata.table}
```


```latex
\documentclass{article}
\usepackage{tikz}
\usepackage{pgfplots}
\usepackage{pgfplotstable}
\pgfplotsset{compat=newest}
\usepackage{filecontents}

\begin{filecontents*}{testdata.table}
Val
2
1
3
\end{filecontents*}

\begin{document}


\pgfplotstableread{testdata.table}{\testdata}
\pgfplotstablecreatecol[%
create col/assign/.code={%
\getthisrow{Val}\entry
\ifnum\pgfplotstablerow>0
\pgfmathsetmacro{\entry}{max(\entry,\pgfmathaccuma)}%
\fi
\edef\pgfmathaccuma{\entry}%<--- CF : ATTENTION: do not forget
'%' after lines otherwise TeX introduces spurious spaces
\xdef\MAXVAL{\pgfmathaccuma}%<-- CF: this is a "dirty hack":
% simply write the result to some global variable - which can be used at
% any place in the file.
\pgfkeyslet{/pgfplots/table/create col/next content}\entry
}]{max(Val)}\testdata

\pgfplotstablecreatecol[%
create col/assign/.code={%
\getthisrow{Val}\entry
\ifnum\pgfplotstablerow>0
\pgfmathsetmacro{\entry}{min(\entry,\pgfmathaccuma)}%
\fi
\edef\pgfmathaccuma{\entry}
\pgfkeyslet{/pgfplots/table/create col/next content}\entry
}]{min(Val)}\testdata

\pgfplotstablecreatecol[%
create col/assign/.code={%
\getthisrow{Val}\entry
\ifnum\pgfplotstablerow>0
\pgfmathsetmacro{\entry}{add(\entry,\pgfmathaccuma)}%
\fi
\edef\pgfmathaccuma{\entry}
\pgfkeyslet{/pgfplots/table/create col/next content}\entry
}]{sum(Val)}\testdata

\pgfplotstablecreatecol[%
create col/assign/.code={%
\getthisrow{sum(Val)}\entry
\pgfmathsetmacro{\entry}{divide(\entry,\pgfplotstablerows)}%
\pgfkeyslet{/pgfplots/table/create col/next content}\entry
}]{avg(Val)}\testdata


\pgfplotstabletypeset[%
every head row/.style={before row=\hline,after row=\hline},
every last row/.style={after row=\hline},
columns/Val/.style={fixed,fixed zerofill,precision=2},
columns/min(Val)/.style={fixed,fixed zerofill,precision=2},
columns/max(Val)/.style={fixed,fixed zerofill,precision=2},
columns/avg(Val)/.style={fixed,fixed zerofill,precision=2},
columns/sum(Val)/.style={fixed,fixed zerofill,precision=2},
]{\testdata}


\pgfplotstabletypeset[
    calc/.style 2 args={create col/assign/.code={%
    \getthisrow{#1}\entry
    \ifnum\pgfplotstablerow>0
    \pgfmathsetmacro{\entry}{#2(\entry,\pgfmathaccuma)}%
    \fi
    \edef\pgfmathaccuma{\entry}
    \xdef\MAXVAL{\pgfmathaccuma}
    \pgfkeyslet{/pgfplots/table/create col/next content}\entry
    }},
    create max column/.style={create on use/max(#1)/.style={calc={#1}{max}}},
    create min column/.style={create on use/min(#1)/.style={calc={#1}{min}}},
    create sum column/.style={create on use/sum(#1)/.style={calc={#1}{add}}},
    create max column=Val, create min column=Val, create sum column=Val,
    columns={Val,max(Val),min(Val),sum(Val)},
]{testdata.table}

% CF: dirty hack result: simply dereference global variable:
The max value is \pgfmathprintnumber{\MAXVAL}.

% CF: clean solution: get a single value of the table.
\pgfplotstablegetelem{2}{avg(Val)}\of\testdata
The average value is \pgfmathprintnumber{\pgfplotsretval}.

% CF: get number of rows, subtract by 1, and use that value:
{%
\pgfplotstablegetrowsof{\testdata}%
\count0=\pgfplotsretval % means: store \pgfplotsretval into artihmetic
TeX register
\advance\count0 by-1 % subtract 1 from that register
\edef\pgfplotsretval{\the\count0}% store result into \pgfplotsretval (as
string)
\pgfplotstablegetelem{\pgfplotsretval}{sum(Val)}\of\testdata
The sum is \pgfmathprintnumber{\pgfplotsretval}.
}% this here restores \count0 to its previous value
\end{document}
```




Use essential styles and hlines from [Create a simple table with borders](./create%20a%20simple%20table%20with%20borders.md)

Setup styles for data importing
```latex
\pgfplotstableset{
    csv/.style = {col sep = comma, row sep = newline, column type = {r}, },
    numberic cells/.style = {numeric type, tblr={ column{1,Z}={r} }},
    shade 2nd/.style = {tblr={ row{even} = {gray9} }},
    dash 3rd/.style = {every nth row = {3}{before row = \hline[dashed]}},
    german/.style = {dec sep={,\!}, 1000 sep ={\,}},
}
```

- center header, detect if number => right align, rowhead = 2, multicolumn cell

1 Rename columns, right align, explain column in legende, show fraction, different 10er potenz

decimal align

3
- show how columns can be renames with index `1{new title}` or name `{Umess}{$U_\mathrm{mess}$}`

3a
- default import

3b
- german comma, (e) scientific notation, sort data, index column




![minimal 62.svg](./attachments/minimal%2062.svg)

```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{3\alph{table}}
\usepackage{pgfplotstable,tabularray,mathtools,amssymb,amsfonts}
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
    rename column/.style 2 args = {columns/#1/.style = {column name = {#2}}},
    column unit/.style 2 args = {tblr={ cell{2-Z}{#1}={appto={\,#2}} }},
    rename column/.list={{t}{$t$ in ms},{U}{$U_\mathrm{mess}$ in V}},
    row counter/.style={tblr = {column{2}={r},vline{2}={solid}},
        create on use/id/.style = {create col/expr = {\pgfplotstablerow+1}},
        columns/id/.style={column name={\#}},
        columns={id,[index]0,[index]1}, },
    tblr outer={remark{$t$} = {Time when datapoint was meassured},
        remark{$U_\mathrm{mess}$} = {Voltage meassured}},
    csv, numberic cells, hlines, caption, dash 3rd, tblr={baseline=T},
}
\begin{document}
\noindent
\pgfplotstabletypeset[dash 3rd]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[german, int detect, row counter, columns/U/.style={sci subscript}]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[int detect, sort=true, sort key={[index]1}]{resources/data.csv}

\vspace{1em}\noindent
\pgfplotstabletypeset[]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[column unit/.list={1{m},2{V}}]{resources/data.csv}
\end{document}
```


```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{3\alph{table}}
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
    csv, numberic cells, hlines, caption
}
\begin{document}
\noindent
\pgfplotstabletypeset[shade 2nd]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[dash 3rd, german]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[int detect, sort=true, sort key={[index]1}]{resources/data.csv}
\end{document}
```

# Main example

![minimal 18.svg](./attachments/minimal%2018.svg)

```latex
\documentclass{article}
\usepackage{pgfplotstable,tabularray}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    csv/.style = {col sep = comma, row sep = newline, column type = {r}, numeric type},
    tblr/.style = {begin table = \begin{tblr}, end table = \end{tblr}},
    hlines/.style = {
        every head row/.style = {before row = \hline[0.08em], after row = \hline[0.05em]},
        every last row/.style = {after row = \hline[0.08em]},
    },
    shade2nd/.style = {every even row/.style = {before row = {\SetRow{gray9}}}},
    dash3rd/.style = {every nth row = {3}{before row = \hline[dashed]}},
    german/.style = {dec sep={,\!}, 1000 sep ={\,}},
}
\begin{document}
\pgfplotstabletypeset[csv,tblr,hlines,shade2nd]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[csv,tblr,hlines,dash3rd,german]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[csv,tblr,hlines,int detect,sort=true,sort key={[index]1}]{resources/data.csv}
\end{document}
```

Example file `resources/data.csv`:
```
# Convergence results
# fictional source generated 2008
$t$ in ms, $U_{mess}$ in V
9,7.57858283e-01
25,5.00000000e-01
81,2.87174589e-01
289,1.43587294e-01
1089,4.41941738e-02
4225,1.69802322e-02
16641,8.20091159e-03
66049,3.90625000e-03
263169,1.95312500e-03
1050625,9.76562500e-04
```

# Align at decimal or scientific separator

- [p] supports `dec sep align` and `sci sep align`
- [c] conflicts with tabularray/tblr by using `\multicol` for alignment, thus no improved cell margins, gap between hlines and row color
- color rows with `\rowcolor[gray]{0.9}` from `colortbl`
- create dashed horizontal lines with `\hdashline` from `arydshln`

![minimal 24.svg](./attachments/minimal%2024.svg)

```latex
\documentclass{article}
\usepackage{pgfplotstable,booktabs,colortbl,arydshln}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    csv/.style = {col sep = comma, row sep = newline, column type = {r}, numeric type},
    hlines+/.style = {
        every head row/.style = {before row = \toprule, after row = \midrule},
        every last row/.style = {after row = \bottomrule},
    },
    shade2nd+/.style = {every even row/.style = {before row = {\rowcolor[gray]{0.9}}}},
    dash3rd+/.style = {every nth row = {3}{before row = \hdashline}},
    german/.style = {dec sep={,\!}, 1000 sep ={\,}},
}
\begin{document}
\pgfplotstabletypeset[csv,hlines+,shade2nd+,dec sep align]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[csv,hlines+,dash3rd+,german,sci sep align]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[csv,hlines+,int detect,sort=true,sort key={[index]1}]{resources/data.csv}
\end{document}
```


---
Sources:
- [\[Pgfplots-features\] Simple calculations on columns of data](https://pgfplots-features.narkive.com/tu1Qxhx5/simple-calculations-on-columns-of-data)

Related:

Tags:
