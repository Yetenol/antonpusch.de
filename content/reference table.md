---
title: "Reference table - Add caption, label, and cross-references"
dg-publish: true
---
Table without label, caption

![table reference nolabel.svg](./attachments/table%20reference%20nolabel.svg)

```latex
\documentclass{standalone} 
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

# Text mode

Caption on tables in text mode

![table reference text mode.svg](./attachments/table%20reference%20text%20mode.svg)

```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{4.1\alph{table}}
\usepackage{tabularray,graphbox,caption}
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

# Float mode

![table reference float mode.svg](./attachments/table%20reference%20float%20mode.svg)

```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{4.2\alph{table}}
\usepackage{tabularray,graphbox}
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


![Pasted image 20221230110738.png](./attachments/pasted%20image%2020221230110738.png)