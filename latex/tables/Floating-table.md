---
date: "2025-03-22T11:18:14.381+01:00"
title: "Floating table"
description: "Let table float here, superwide, above, below, next to a page's main text"
dg-publish: true
dg-folder: latex/tables
---

# Sidenotes

![figure rerun sidenotes table.svg](../../attachments/figure-rerun-sidenotes-table.svg)

```latex
\documentclass{article} \title{rerun sidenotes table}
\usepackage{sidenotes,tabularray,lipsum,lastpage}
\begin{document} \SetTblrInner{hlines}
\sidenotetext{This is a marginal note.} \lipsum[1][1-3] 
\begin{table*}
\begin{tblr}[tall, caption={Expand table into page margins}]{X}
    \lipsum[3][1-4]
\end{tblr}
\end{table*}
\end{document}
```

# Float tables

![figure table floats.svg](../../attachments/figure-table-floats.svg)

```latex
\documentclass{article} \title{table floats}
\renewcommand{\thetable}{4.1\alph{table}} \pagestyle{empty}
\usepackage{tabularray,sidenotes,lipsum,graphbox,float,lastpage}
\captionsetup[table]{skip=2pt}
\begin{document}
\lipsum[4]

\begin{table}[H] \centering{}
\begin{minipage}[b]{.4\textwidth} \centering{}
\caption{Pre-compiled table}
\includegraphics{figure table reference nolabel}
\end{minipage}
\hspace{1em}
\begin{minipage}[b]{.4\textwidth} \centering{}
\begin{tblr}[tall,baseline=b,note{}={Drivers ride busses.},
caption={Multiple tables in same float},
]{
hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name          & Job \\
Zaid Knowles  & Teacher \\
Hayley Conner & Doctor  \\
Susan Wood    & Driver \\
\end{tblr}
\end{minipage}
\end{table}

\begin{margintable}
\begin{tblr}[tall, note{}={as of 2014},
entry={No caption, just an entry in list of tables},
]{
colspec={XX[r]}, hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name   & Age \\
Peter  & 7   \\
Io     & 14  \\
Lara   & 10  \\
\end{tblr}
\end{margintable}

\lipsum[2]

\begin{table*}
\begin{tblr}[tall, 
caption={Superwide table spanning into the margins with adjustable width}, 
]{
colspec={lX}, hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
column{1}={wd=15em}, column{2}={font=\ttfamily},
}
Page &
    URI \\
Bluetooth \& other devices & 
    {ms-settings:bluetooth\\ms-settings:connecteddevices} \\
Connect to wireless display or audio device & 
    ms-settings-connectabledevices:devicediscovery \\
Printers \& scanners & 
    ms-settings:printers \\
Mouse & 
    ms-settings:mousetouchpad \\
\end{tblr}
\end{table*}

% \listoftables
\end{document}
```

## Use custom caption styles

![figure table floats 2.svg](../../attachments/figure-table-floats-2.svg)

```latex
\documentclass{article} \title{table floats 2}
\renewcommand{\thetable}{4.2\alph{table}} \pagestyle{empty}
\usepackage{tabularray,sidenotes,float,lipsum,lastpage}
\begin{document}
\lipsum[4]

\begin{table}[H]
\caption{Float here}
\begin{tblr}[tall,label=none,entry=none,note{}={Drivers ride busses.}]{
colspec={XX}, hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name          & Job \\
Zaid Knowles  & Teacher \\
Hayley Conner & Doctor  \\
Susan Wood    & Driver \\
\end{tblr}
\end{table}

\begin{margintable}
\caption{Float right}
\begin{tblr}[tall,label=none,entry=none,note{}={Drivers ride busses.}]{
colspec={XX[r]}, hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name   & Age \\
Peter  & 7   \\
Io     & 14  \\
Lara   & 10  \\
\end{tblr}
\end{margintable}

\lipsum[2]

\begin{table*}
\caption{Float superwide}
\begin{tblr}[tall,label=none,entry=none,note{}={Drivers ride busses.}]{
colspec={XX[r]}, hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name   & Age \\
Peter  & 7   \\
Io     & 14  \\
Lara   & 10  \\
\end{tblr}
\end{table*}

\listoftables
\end{document}
```

# References

Table without label, caption

![figure table reference nolabel.svg](../../attachments/figure-table-reference-nolabel.svg)

```latex
\documentclass{standalone} \title{table reference nolabel}
\usepackage{tabularray}
\begin{document}
\begin{tblr}[tall,label=none,note{}={Drivers ride busses.}]{
hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name          & Job \\
Zaid Knowles  & Teacher \\
Hayley Conner & Doctor  \\
Susan Wood    & Driver \\
\end{tblr}
\end{document}
```

![figure table reference nolabel 2.svg](../../attachments/figure-table-reference-nolabel-2.svg)

```latex
\documentclass{standalone} \title{table reference nolabel 2}
\usepackage{tabularray}
\begin{document}
\begin{tblr}[tall,label=none,note{}={as of 2014}]{
hline{1,Z}={.08em}, hline{2}, colspec={lr}, row{1}={c},
}
Name   & Age \\
Peter  & 7   \\
Io     & 14  \\
Lara   & 10  \\
\end{tblr}
\end{document}
```

# Text mode

Caption on tables in text mode

![figure table reference text mode.svg](../../attachments/figure-table-reference-text-mode.svg)

```latex
\documentclass{article} \title{table reference text mode}
\renewcommand{\thetable}{4.3\alph{table}}
\usepackage{tabularray,graphbox,caption,lastpage}
\captionsetup[table]{skip=2pt}
\begin{document}
\begin{minipage}{.4\textwidth} \centering{}
\captionof{table}{Pre-compiled table}
\includegraphics{table reference nolabel}
\end{minipage}
%
\begin{tblr}[tall,caption={Inline table},note{}={Drivers ride busses.}]{
hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name          & Job \\
Zaid Knowles  & Teacher \\
Hayley Conner & Doctor  \\
Susan Wood    & Driver \\
\end{tblr}
\listoftables
\end{document}
```

# Floating tables

![figure table reference float mode.svg](../../attachments/figure-table-reference-float-mode.svg)

```latex
\documentclass{article} \title{table reference float mode}
\renewcommand{\thetable}{4.4\alph{table}}
\usepackage{tabularray,graphbox,lastpage}
\begin{document}
\begin{table}[h] \centering{}
\caption{Pre-compiled table}
\includegraphics{table reference nolabel}
\end{table}
%
\begin{center}
\begin{tblr}[tall,caption={Inline table},note{}={Drivers ride busses.}]{
hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name          & Job \\
Zaid Knowles  & Teacher \\
Hayley Conner & Doctor  \\
Susan Wood    & Driver \\
\end{tblr}
\end{center}
\listoftables
\end{document}
```

Floating tables in sidebar

![figure table reference float sidebar.svg](../../attachments/figure-table-reference-float-sidebar.svg)

```latex
\documentclass{article} \title{table reference float sidebar}
\renewcommand{\thetable}{4.5\alph{table}}
\usepackage{tabularray,graphbox,sidenotes,lipsum,lastpage}
\begin{document}
See tables in the sidebar.

\begin{margintable}
\caption{Pre-compiled table}
\includegraphics{table reference nolabel}
\end{margintable}
\begin{margintable}
\begin{tblr}[tall,caption={Inline table},note{}={Drivers ride busses.}]{
hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name          & Job \\
Zaid Knowles  & Teacher \\
Hayley Conner & Doctor  \\
Susan Wood    & Driver \\
\end{tblr}
\end{margintable}
\listoftables
\end{document}
```


# Sub-float mode

![figure table reference subfloat mode.svg](../../attachments/figure-table-reference-subfloat-mode.svg)

```latex
\documentclass{article} \title{table reference subfloat mode}
\renewcommand{\thetable}{4.6\alph{table}}
\usepackage{tabularray,graphbox,lastpage}
\begin{document}
\begin{table}
\begin{minipage}[b]{0.35\textwidth} \centering{}
\caption{Pre-compiled} \vspace{3pt}
\includegraphics{table reference nolabel}
\end{minipage}
\hspace{1em}
\begin{minipage}[b]{0.35\textwidth} \centering{}
\begin{tblr}[tall,baseline=b,caption={Inline table},note{}={Drivers ride busses.}]{
hline{1,Z}={.08em}, hline{2}, row{1}={c}, 
}
Name          & Job \\
Zaid Knowles  & Teacher \\
Hayley Conner & Doctor  \\
Susan Wood    & Driver \\
\end{tblr}
\end{minipage}
\end{table}
\listoftables
\end{document}
```

![figure table reference subfloat mode 2.svg](../../attachments/figure-table-reference-subfloat-mode-2.svg)

```latex
\documentclass{article} \title{table reference subfloat mode 2}
\renewcommand{\thetable}{4.7\alph{table}}
\usepackage{tabularray,graphbox}
\begin{document}
\begin{table}
\begin{minipage}[b]{.2\textwidth} \centering{}
\caption{P} \vspace{4pt}
\includegraphics{table reference nolabel 2}
\end{minipage}
\hspace{1em}
\begin{minipage}[b]{.2\textwidth} \centering{}
\begin{tblr}[tall,baseline=b,caption={I},note{}={as of 2014}]{
hline{1,Z}={.08em}, hline{2}, colspec={lr}, row{1}={c},
}
Name   & Age \\
Peter  & 7   \\
Io     & 14  \\
Lara   & 10  \\
\end{tblr}
\end{minipage}
\hspace{1em}
\begin{minipage}[b]{.2\textwidth} \centering{}
\caption{C} \vspace{4pt}
\begin{tblr}[tall,baseline=b,entry=none,label=none,note{}={as of 2014}]{
hline{1,Z}={.08em}, hline{2}, colspec={lr}, row{1}={c},
}
Name   & Age \\
Peter  & 7   \\
Io     & 14  \\
Lara   & 10  \\
\end{tblr}
\end{minipage}
\end{table}
\listoftables
\end{document}
```