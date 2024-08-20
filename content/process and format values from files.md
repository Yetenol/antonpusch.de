---
title: "Process, and format values from files"
dg-publish: true
---

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
    csv, numberic cells, hlines, caption, tblr={baseline=T}
}
\begin{document}
\noindent
\pgfplotstabletypeset[shade 2nd]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[dash 3rd, german]{resources/data.csv}
\hspace{1cm}
\pgfplotstabletypeset[int detect, sort=true, sort key={[index]1}]{resources/data.csv}

\vspace{1em}\noindent
\pgfplotstabletypeset[rename column/.list={{t}{$t$ in ms},{U}{$U_\mathrm{mess}$ in V}},
    tblr outer={ remark{$t$} = {Time when datapoint was meassured},
    remark{$U_\mathrm{mess}$} = {Voltage meassured}  }
    ]{resources/data.csv}
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