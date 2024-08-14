---  
dg-publish: true  
---  
# Main examples  
  
![minimal 28.svg](./attachments/minimal%2028.svg)  
  
```latex  
\documentclass{article}  
\usepackage{pgfplotstable,tabularray}  
\UseTblrLibrary{booktabs}\SetTblrInner{column{1,Z}={c}}  
\pgfplotstableset{  
    /pgfplots/compat = 1.17,  
    tblr/.style = {begin table = \begin{tblr}{}, end table = \end{tblr}, skip coltypes},  
    tabular/.style = {col sep = &, row sep = \\, string type},  
    hlines/.style={every table/.append code=\SetTblrInner{  
        hline{1,Z}={\heavyrulewidth},hline{2}={\lightrulewidth} }},  
    hasrowname/.style={every first column/.append style = {string type},   
        every table/.append code=\SetTblrInner{column{1}={l} }},  
    cross/.style={hasrowname, every table/.append code=\SetTblrInner{  
        vline{2}, hline{2} }},  
    frame/.style={every table/.append code=\SetTblrInner{  
        vline{1,Z}={\heavyrulewidth},hline{1,Z}={\heavyrulewidth} }},  
    innergrid/.style={every table/.append code=\SetTblrInner{  
        vline{2-Y},hline{2-Y} }},  
    boldcolname/.style={every table/.append code=\SetTblrInner{  
        row{1}={font=\bfseries} }},  
    boldrowname/.style={hasrowname, every table/.append code=\SetTblrInner{  
        column{1}={font=\bfseries} }},  
    stylespack/.style={tabular,tblr,frame,innergrid,boldcolname,boldrowname},  
}  
\begin{document}  
\pgfplotstabletypeset[tabular,tblr,hlines]{  
    Name & Identifier \\  
    Peter & 3 \\  
    Io & Hat \\  
    Lara & $\triangle$ \\  
}  
\hspace{1cm}  
\pgfplotstabletypeset[tabular,tblr,cross]{  
    Name & Identifier \\  
    Peter & 3 \\  
    Io & Hat \\  
    Lara & $\triangle$ \\  
}  
\hspace{1cm}  
\pgfplotstabletypeset[stylespack]{  
    Name & Identifier \\  
    Peter & 3 \\  
    Io & Hat \\  
    Lara & $\triangle$ \\  
}  
\end{document}  
```  
  
  
# Create borders without tabularray  
  
Problem: Booktabs creates gaps with row colors or vertical lines:  
  
![minimal 22.svg](./attachments/minimal%2022.svg)  
  
Solution  
  
- Remove vertical separation from `\toprule`, `\midrule`, `\bottomrule`  
- Create custom width vertical lines with `!{\vrule width .08em}` in the column type  
  
```latex  
\setlength{\abovetopsep}{0em}  
\setlength{\aboverulesep}{0em}  
\setlength{\belowrulesep}{0em}  
\setlength{\belowbottomsep}{0em}  
!{\vrule width .08em}  
```  
  
![minimal 25.svg](./attachments/minimal%2025.svg)  
  
Remove booktabs vertical space for conflicts  
  
```latex  
\documentclass{article}  
\pagestyle{empty}  
\usepackage{pgfplotstable,booktabs}  
\pgfplotstableset{  
    /pgfplots/compat = 1.17,  
    tabular/.style = {col sep = &, row sep = \\, string type},  
    hlines/.style = {  
        every head row/.style = {before row = \toprule, after row = \midrule},  
        every last row/.style = {after row = \bottomrule},  
    },  
    vline+/.style = {clearbooktabssep,every first column/.style = {column type=l|,string type}},  
    cross+/.style = {  
        clearbooktabssep,  
        every first column/.style = {column type=l|,string type},  
        every head row/.append style = {after row = \midrule}  
    },  
    clearbooktabssep/.style = {  
        every table/.code = {  
            \setlength{\abovetopsep}{0em}  
            \setlength{\aboverulesep}{0em}  
            \setlength{\belowrulesep}{0em}  
            \setlength{\belowbottomsep}{0em}  
        },  
    },  
    frame+/.style = {  
        every head row/.append style = {before row = \toprule },  
        every last row/.append style = {after row = \bottomrule },  
        every first column/.style = {column type/.add={!{\vrule width .08em}}{}},  
        every last column/.style = {column type/.add={}{!{\vrule width .08em}}},  
        clearbooktabssep  
    },  
    innergrid+/.style = {  
        every column/.code={\ifnum\pgfplotstablecol>0 \pgfkeysalso{column type/.add={|}{}} \fi},  
        every even row/.style={before row/.add=\hline},  
        every odd row/.style={before row/.add=\hline},  
    },  
    boldcolname+/.style = {assign column name/.style={/pgfplots/table/column name={\textbf{##1}}}},  
    boldrowname+/.style = {before row=\bfseries},  
}  
\begin{document}  
\pgfplotstabletypeset[tabular,hlines]{  
    Name & Identifier \\  
    Peter & 3 \\  
    Io & 7 \\  
    Lara & $\cap$ \\  
}  
\hspace{1cm}  
\pgfplotstabletypeset[tabular,cross+]{  
    Name & Identifier \\  
    Peter & 3 \\  
    Io & 7 \\  
    Lara & $\cap$ \\  
}  
\hspace{1cm}  
\pgfplotstabletypeset[tabular,frame+,innergrid+,boldcolname+,boldrowname+]{  
    Name & Identifier \\  
    Peter & 3 \\  
    Io & 7 \\  
    Lara & $\cap$ \\  
}  
\end{document}  
```  
  
