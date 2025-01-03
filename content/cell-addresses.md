---
title: "Cell addresses - Count rows and columns relative to the entire table, its body, or the current group"
date: "2024-09-10T00:00:00.000+02:00"
dg-publish: true
---

# Add row number relative to table body

![table counter rownum 1.svg](./attachments/table-counter-rownum-1.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{5.1\alph{table}}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\begin{document}
\begin{tblr}[tall,caption=Count rows]{
hline{1,Z}={.08em},hline{2}, column{1}={l}, row{1}={c},
cell{2-Z}{1}={r,cmd=\fpEval{\therownum - 1}}
}
\# & Name             \\
   & Alexia Beasley   \\
   & Lauren Beard     \\
   & Esme Sanford     \\
   & Leyla Smith      \\
   & Shane Fisher     \\
   & Rosie O'Neill    \\
   & Daisy McGonagall \\
\end{tblr}
\end{document}
```

## Align first, last names

![table counter rownum 1, 2.svg](./attachments/table-counter-rownum-1-2.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{5.1b}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\begin{document}
\begin{tblr}[tall,caption=Count rows]{
colspec={rrl},
hline{1,Z}={.08em},hline{2},
cell{1}{2}={c=2}{c}, 
column{2}={rightsep=2pt}, column{3}={leftsep=2pt},
cell{2-Z}{1}={cmd=\fpEval{\therownum - 1}}
}
\# & Name                \\
   & Alexia & Beasley    \\
   & Lauren & Beard      \\
   & Esme   & Sanford    \\
   & Leyla  & Smith      \\
   & Shane  & Fisher     \\
   & Rosie  & O'Neill    \\
   & Daisy  & McGonagall \\   
\end{tblr}
\end{document}
```


```latex
\documentclass{standalone} \usepackage{graphbox}
\begin{document}
\includegraphics[align=c]{table counter rownum 1} \hspace{1em}
\includegraphics[align=c]{table counter rownum 2}
\end{document}
```


# Tabularray's built-in counters relative to the entire table

- counters rownum, colnum, rowcount, colcount are available
Print counter with format
- `\arabic{rownum}`, `\alph{rownum}`, `\Alph{rownum}`, `\roman{rownum}`, `\Roman{rownum}`, `\therownum`

![table counter absolute.svg](./attachments/table-counter-absolute.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{5.2a}
\usepackage{tabularray}
\begin{document}
\begin{tblr}[tall,caption=Absolute counters in different alphabets]{ 
hline{1,Z}={.08em},hline{3}, column{1-Z}={c},
cell{3-Z}{2}={preto=\arabic{colnum}},
cell{3-Z}{3}={preto=\alph{colnum}},
cell{3-Z}{4}={preto=\Alph{colnum}},
cell{3-Z}{5}={preto=\roman{colnum}},
cell{3-Z}{6}={preto=\Roman{colnum}},
cell{3}{2-Z}={appto={,\arabic{rownum}}},
cell{4}{2-Z}={appto={,\alph{rownum}}},
cell{5}{2-Z}={appto={,\Alph{rownum}}},
cell{6}{2-Z}={appto={,\roman{rownum}}},
cell{7}{2-Z}={appto={,\Roman{rownum}}},
cell{1}{1}={r=2}{font=\bfseries}, cell{1}{2}={c=5}{font=\bfseries},
hline{2}={2-Z}{leftpos=-1,rightpos=-1,endpos},
}
{rownum\\counter} & colnum counter \\
& arabic & alph & Alph & roman & Roman \\
arabic \\
alph   \\
Alph   \\
roman  \\
Roman  \\
\end{tblr}
\end{document}
```

# Offset counters relative to table body

![table counter absolute, body.svg](./attachments/table-counter-absolute-body.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{5.2b}
\usepackage{tabularray}
\UseTblrLibrary{counter,functional}
\IgnoreSpacesOn
\newcounter{colindex} \newcounter{rowindex} \intNew\nindex
\prgNewFunction\updatecolindex{ m }{
    \intCompareTF {\thecolnum} > {#1}
        { \intSet\nindex{ \intEval{ \thecolnum - #1 }}}
        { \intZero\nindex }
    \setcounter{colindex}{\nindex}  }
\prgNewFunction\updaterowindex{ m }{
    \intCompareTF {\therownum} > {#1}
        { \intSet\nindex{ \intEval{ \therownum - #1 }}}
        { \intZero\nindex }
    \setcounter{rowindex}{\nindex}  }
\IgnoreSpacesOff
\begin{document}
\begin{tblr}[tall,caption=Relative counters in different alphabets]{ 
hline{1,Z}={.08em},hline{3}, column{1-Z}={c},
cell{3-Z}{2}={preto=\arabic{colindex}},
cell{3-Z}{3}={preto=\alph{colindex}},
cell{3-Z}{4}={preto=\Alph{colindex}},
cell{3-Z}{5}={preto=\roman{colindex}},
cell{3-Z}{6}={preto=\Roman{colindex}},
cell{3}{2-Z}={appto={,\arabic{rowindex}}},
cell{4}{2-Z}={appto={,\alph{rowindex}}},
cell{5}{2-Z}={appto={,\Alph{rowindex}}},
cell{6}{2-Z}={appto={,\roman{rowindex}}},
cell{7}{2-Z}={appto={,\Roman{rowindex}}},
cell{1-Z}{1-Z}={preto={\updatecolindex{1}\updaterowindex{2}}},
cell{1}{1}={r=2}{font=\bfseries}, cell{1}{2}={c=5}{font=\bfseries},
hline{2}={2-Z}{leftpos=-1,rightpos=-1,endpos},
}
{rowindex\\counter} & colindex counter \\
& arabic & alph & Alph & roman & Roman \\
arabic \\
alph   \\
Alph   \\
roman  \\
Roman  \\
\end{tblr}
\end{document}
```

```latex
\documentclass{standalone} \usepackage{graphbox}
\begin{document}
\includegraphics[align=c]{table counter absolute} \hspace{1em}
\includegraphics[align=c]{table counter body}
\end{document}
```

# Skip cells with group names

![table counter skip.svg](./attachments/table-counter-skip.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{5.3a}
\usepackage{tabularray}
\UseTblrLibrary{counter}
\newcounter{rowindex} \newcounter{colindex}
\begin{document}
\begin{tblr}[tall,caption=Continually count grouped headers]{
colspec={lrrrr}, cell{1-2}{2-Z}={c},
cell{1}{2,4}={c=2}{c},
hline{2} = {2-3}{leftpos = -1, rightpos = -1, endpos},
hline{2} = {4-5}{leftpos = -1, rightpos = -1, endpos},
%
hline{1,Z}={.08em}, hline{3},
cell{2}{2-Z}={appto={\stepcounter{colindex}$_{\roman{colindex}}$}},
column{2-Z}={colsep=2pt},
column{2,4}={leftsep+=6pt},
%
cell{3-Z}{1}={cmd={\stepcounter{rowindex}\rlap{\roman{rowindex})}\qquad}},
row{3-Z}={rowsep=0pt},
row{3,6}={font=\bfseries,cmd={},abovesep=6pt,belowsep=2pt},
}
          & Dogs &    & Cats &    \\
Owner     & M    & F  & M    & F  \\
Age                               \\
$< 18$    & 2    & 12 & 7    & 11 \\
$\ge 18$  & 4    & 44 & 5    & 3  \\
Residence                         \\
Urban     & 43   & 46 & 15   & 33 \\
Rural     & 5    & 12 & --   & 14 \\
\end{tblr}
\end{document}
```

# Restart counter for each group

![table counter skip, groups.svg](./attachments/table-counter-skip-groups.svg)

```latex
\documentclass{standalone} \renewcommand{\thetable}{5.3b}
\usepackage{tabularray}
\UseTblrLibrary{counter}
\newcounter{rowindex} \newcounter{colindex}
\begin{document}
\begin{tblr}[tall,caption=Separately count grouped headers]{
colspec={lrrrr}, cell{1-2}{2-Z}={c},
cell{1}{2,4}={c=2}{c},
hline{2} = {2-3}{leftpos = -1, rightpos = -1, endpos},
hline{2} = {4-5}{leftpos = -1, rightpos = -1, endpos},
%
hline{1,Z}={.1em}, hline{3},
cell{2}{2-Z}={appto={\stepcounter{colindex}$_{\roman{colindex}}$}},
column{2-Z}={colsep=2pt},
cell{2}{2,4}={preto=\setcounter{colindex}{0}},
column{2,4}={leftsep+=6pt},
%
cell{3-Z}{1}={cmd={\stepcounter{rowindex}\rlap{\roman{rowindex})}\qquad}},
row{3-Z}={rowsep=0pt},
row{3,6}={font=\bfseries,cmd=\setcounter{rowindex}{0},
    abovesep=6pt,belowsep=2pt},
}
          & Dogs &    & Cats &    \\
Owner     & M    & F  & M    & F  \\
Age                               \\
$< 18$    & 2    & 12 & 7    & 11 \\
$\ge 18$  & 4    & 44 & 5    & 3  \\
Residence                         \\
Urban     & 43   & 46 & 15   & 33 \\
Rural     & 5    & 12 & --   & 14 \\
\end{tblr}
\end{document}
```

```latex
\documentclass{standalone} \usepackage{graphbox}
\begin{document}
\includegraphics[align=c]{table counter skip} \hspace{1em}
\includegraphics[align=c]{table counter groups}
\end{document}
```

# Figure collection for note preview

![table counters.svg](./attachments/table-counters.svg)

```latex
\documentclass{standalone} \usepackage{graphbox}
\begin{document}
\begin{minipage}{\textwidth} \centering{}
\includegraphics{table counter rownum 1} \hspace{1em}
\includegraphics{table counter groups} \\ \vspace{1em}
\includegraphics{table counter body} 
\end{minipage}
\end{document}
```