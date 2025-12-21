---
date: "2025-07-17T08:13:58.855+02:00"
title: "Table with Equal Width Columns"
description: "Typeset tables with distributed column width"
dg-publish: true
priority: 5
---

Utilize special column types to distribute the width of different column types

Dependency [LaTeX.table](https://github.com/Yetenol/latex.table)

**Table body** in `resources/children-list.tex`  

```latex
% Child & Mother & Father
Alysha  & Lyra   & Hans \\
Klaus   & Rosy   & Dieter \\
```

**Table columns, design** in `table/auto-stretch.tex`

```latex
\CatchFileDef{\input⟨data title⟩}{src/⟨data title⟩}{}
\begin{table}  % or \begin{table}[⟨placement specifiers⟩]
    %%%%%%%%%% LAYOUT, META DATA %%%%%%%%%%
    \centering
    \caption{⟨caption⟩} % title displayed below the table and in the index
    \label{tab:⟨table name⟩} % handle to cross reference the table
    \begin{tabularx}{\columnwidth} % total table width
    {   %%%%%%%%%% COLUMN FORMATTING %%%%%%%%%%
        p{1.75cm} % fixed-width column
        X         % justify text, sketching column
        C         % centering text, sketching column
        X         % justify text, sketching column
    }
        \toprule     %%%%%%%%%% MULTICOLUMN HEADERS %%%%%%%%%%
        & \multicolumn{2}{c}{⟨multicolumn header⟩} 
        \\ \cmidrule(lr){2-3}   %%%%%%%%%% COLUMN HEADERS %%%%%%%%%%
        {Child} &
        {Mother} &
        {Father}
        \\ \midrule     %%%%%%%%%% TABLE BODY %%%%%%%%%%
        \input⟨data title⟩ % body file defined in first line
        \bottomrule     %%%%%%%%%% END OF BODY %%%%%%%%%%
    \end{tabularx}
\end{table}
```

- `⟨data title⟩`: File where the table's body is stored
- `⟨placement specifiers⟩` := see [Positioning](Table-with-Equal-Width-Columns.md##positioning)
- `⟨caption⟩`: Title displayed below the table and in the index
- `⟨table name⟩`: Filename and handle to cross reference the table
- `⟨multicolumn header⟩` := column title that spans multiple columns

---
Sources:

Related:

Tags:
[Graphical elements - Standardize tables, images, plots](./Graphical-elements.md)
