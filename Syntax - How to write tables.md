# Syntax - How to write tables

```tex
\documentclass{article}
\usepackage{pgfplotstable, ⟨dependencies for styles⟩}
\pgfplotstableset{
    /pgfplots/compat = 1.17,
    mystyle/.style = {⟨define formatting style⟩},
    ⟨apply global styles⟩
}
\begin{document}
\pgfplotstabletypeset[⟨apply individual styles⟩]{
    ⟨file name or inline table⟩
}
\end{document}
```

- **⟨dependencies for styles⟩**: some styles require additional packages
- **⟨define formatting style⟩**: configure how tables with this style get **formatted**
- **⟨apply global styles⟩**: list styles and configurations that are applied to **all** pgfplots tables
- **⟨individual styles⟩**: list styles and configurations that are applied to **this** pgfplots tables
- **⟨file name or inline table⟩**: table **body** or relative **path** of file with table content
- [p] minimal formatting information at the snippet; style **definitions** in the **preamble** preset the formatting globally
- [p] the code is **independent** of the project: no user-defined macros; clearly shows which package draws the table