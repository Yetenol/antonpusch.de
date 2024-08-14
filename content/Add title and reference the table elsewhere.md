---  
dg-publish: true  
---  
  
# Main example  
  
![minimal 29.svg](./attachments/minimal%2029.svg)  
  
```latex  
\documentclass{article}  
\usepackage{pgfplotstable,tabularray,booktabs,float,hyperref}  
\UseTblrLibrary{booktabs}\SetTblrInner{column{1,Z}={c}}  
\hypersetup{colorlinks=true, linkcolor=blue}  
\pgfplotstableset{  
    /pgfplots/compat = 1.17,  
    tabular/.style = {col sep = &, row sep = \\, string type},  
    tblr/.style = {begin table = \begin{tblr}, end table = \end{tblr}},  
    hlines/.style={every table/.append code=\SetTblrInner{  
        hline{1,Z}={\heavyrulewidth},hline{2}={\lightrulewidth} }},  
    centering/.style = {  
        begin table/.add = {\parskip=0pt\par\nopagebreak\centering{}}{},  
        end table/.add = {}{\par\noindent\ignorespacesafterend{}}  },  
}  
\begin{document}  
Each person gets assigned a number listed in table \ref{tab:identifiers} on page \pageref{tab:identifiers}.  
\begin{table}[H]  
\pgfplotstabletypeset[tabular,tblr,centering,hlines]{  
    Name & Identifier \\  
    Peter & 3 \\  
    Io & Hat \\  
    Lara & $\triangle$ \\  
}\caption{People's identifiers}\label{tab:identifiers}  
\end{table}  
\listoftables  
\end{document}  
```  
