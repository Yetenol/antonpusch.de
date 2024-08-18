---
title: "Create a simple table with borders"
dg-publish: true
---
# Essential styles

Setup **essential styles** for demos
```latex
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    text cells/.style = {string type,tblr={ column{1,Z}={c} }},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style = {begin table = \begin{#1}{}, end table = \end{#1}, skip coltypes },
    caption/.style = {tblr outer={tall,caption={#1}}},
}
```

- **tex**: Use LaTeX's default tabular separators for columns `&` and rows `\\`
- **text cells**: Don't parse cells as numbers, center align cells
- **tblr**: use the tabularray environment
- **tblr=⟨key-value pairs⟩**: add inner tabularray configuration
- **tblr outer=⟨key-value pairs⟩**: add outer tabularray configuration
- **environment**: set environment to be used by pgfplotstable, and don't generate column types
- **caption**: Add table number to identify the demo tables

Setup demo projects
```latex
\documentclass{article} \pagestyle{empty}
\renewcommand{\thetable}{⟨chapter⟩\alph{table}} \setcounter{table}{⟨skip n letters⟩}
```
- Use article class without page numbers for easier pdf cropping
- **chapter**: set number at the start of table numbers
- **skip n letters**: start the table numbers with the $n+1^\text{th}$ letter of the lowercase alphabet, default 0

# Add table borders

Use essential styles from above

Setup styles for border lines
```latex
\pgfplotstableset{
    hlines/.style={tblr={ hline{1,Z}={.08em},hline{2}={.05em} }},
    hasrowname/.style={every first column/.append style={string type}, tblr={ column{1}={l} }},
    cross/.style={hasrowname, tblr={ vline{2}, hline{2} }},
    frame/.style={tblr={ vline{1,Z}={.08em},hline{1,Z}={.08em} }},
    innergrid/.style={tblr={ vline{2-Y},hline{2-Y} }},
    boldcolname/.style={tblr={ row{1}={font=\bfseries} }},
    boldrowname/.style={hasrowname, tblr={ column{1}={font=\bfseries} }},
}
```

Rule widths equals booktabs' defaults for toprule, midrule, and bottomrule

Add thick **horizontal** lines around the table and a regular line below the **first row**, see $\mathrm{1a}$
- Use style **hlines**

Add two **crossing** lines separating the **first row** and **first column** from the rest, see $\mathrm{1b}$
- Visually clarify **column titles** and **row titles**
- **Left aligns** the first column
- Use style **cross** requiring hasrowname

Add **inner gridlines**, see $\mathrm{1c, 1d}$
- Vertical and horizontal lines everywhere except the outside border
- Use style **innergrid**

Box the table with a thick **frame** line, see $\mathrm{1c, 1f}$
- Use style **frame**

Format the **first row bold**, see $\mathrm{1c, 1e}$
-  Use style **boldcolname**

Format the **first column bold**, see $\mathrm{1c, 1f}$
- **Left aligns** the first column
- Use style **boldrowname** requiring hasrowname

Demos with essential styles tex, text cells, and caption from [ > Essential styles](create%20a%20simple%20table%20with%20borders.md#Essential%20styles) as default:
![minimal 54.svg](./attachments/minimal%2054.svg)

Complete source code for $\mathrm{1a - 1f}$
```latex
\documentclass{article}\pagestyle{empty}\renewcommand{\thetable}{1\alph{table}}
\usepackage{pgfplotstable,tabularray}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    tex/.style = {col sep = &, row sep = \\},
    text cells/.style = {string type,tblr={ column{1,Z}={c} }},
    tblr/.style = {environment=tblr, every table/.append code={\SetTblrInner[tblr,talltblr,longtblr]{#1}}},
    tblr outer/.style = {tblr, every table/.append code={\SetTblrOuter[tblr,talltblr,longtblr]{#1}}},
    environment/.style = {begin table = \begin{#1}{}, end table = \end{#1}, skip coltypes },
    caption/.style = {tblr outer={tall,caption={#1}}},
    hlines/.style={tblr={ hline{1,Z}={.08em},hline{2}={.05em} }},
    hasrowname/.style={every first column/.append style={string type}, tblr={ column{1}={l} }},
    cross/.style={hasrowname, tblr={ vline{2}, hline{2} }},
    frame/.style={tblr={ vline{1,Z}={.08em},hline{1,Z}={.08em} }},
    innergrid/.style={tblr={ vline{2-Y},hline{2-Y} }},
    boldcolname/.style={tblr={ row{1}={font=\bfseries} }},
    boldrowname/.style={hasrowname, tblr={ column{1}={font=\bfseries} }},
    tex,tblr,text cells,caption
}
\begin{document}
\noindent
\pgfplotstabletypeset[hlines]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
}
\hspace{1cm}
\pgfplotstabletypeset[cross]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
}
\hspace{1cm}
\pgfplotstabletypeset[frame,innergrid,boldcolname,boldrowname]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
}

\vspace{1em}\noindent
\pgfplotstabletypeset[innergrid]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
}
\hspace{1cm}
\pgfplotstabletypeset[boldcolname]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
}
\hspace{1cm}
\pgfplotstabletypeset[frame,boldrowname]{
    Name & Identifier \\
    Peter & 3 \\
    Io & Hat \\
    Lara & $\triangle$ \\
}
\end{document}
```

# Make booktabs compatible with tabularray

Replace hlines and frame styles
```latex
\UseTblrLibrary{booktabs}
\pgfplotstableset{
    hlines/.style={tblr={ hline{1,Z}={\heavyrulewidth},hline{2}={\lightrulewidth} }},
    frame/.style={tblr={ vline{1,Z}={\heavyrulewidth},hline{1,Z}={\heavyrulewidth} }},
}
```

Change heavy rule width, see modified $\mathrm{1a', 1b', 1c'}$
```latex
\heavyrulewidth=1.5pt
```

![minimal 57.svg](./attachments/minimal%2057.svg)

# Create borders without tabularray

**Problem**: Booktabs creates gaps within vertical lines and next to colored rows:

![minimal 22.svg](./attachments/minimal%2022.svg)

**Workaround**: Remove booktabs' vertical spacing
- Remove vertical separation from `\toprule`, `\midrule`, `\bottomrule`
- Create custom width vertical lines with `!{\vrule width .08em}` in the column type

```latex
\setlength{\abovetopsep}{0em}
\setlength{\aboverulesep}{0em}
\setlength{\belowrulesep}{0em}
\setlength{\belowbottomsep}{0em}
!{\vrule width .08em}
```

![minimal 58.svg](./attachments/minimal%2058.svg)

**Ugly example**: Remove booktabs vertical space for conflicts
- boldcolname* or boldrowname* must be applied before any line styles
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
