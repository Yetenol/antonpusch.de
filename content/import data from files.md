---
title: "Import data from files"
dg-publish: true
---
# Main example

![minimal 18.svg](./attachments/minimal%2018.svg)

```latex
\documentclass{article}
\usepackage{pgfplotstable,tabularray,amsmath,amssymb,xcolor}
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