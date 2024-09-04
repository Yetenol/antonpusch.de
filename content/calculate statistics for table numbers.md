---
title: "Calculate statistics for table numbers"
dg-publish: true
---
- Keep the data in **raw** and **universal** (csv) form: Update data anytime with external programs like Excel, Python, MATLAB, R, PowerShell
- Render **scientific notation** correctly and **uniform**: Render `4.41941738e-02` as $4.42 \cdot 10^{-2}$ $\mathrm{3a, 3b, 3c}$ 
- **Format numbers**: Set max. decimal places $\mathrm{3a, 3b, 3c}$; When to show exponent $\mathrm{3c}$; Use German commas $\mathrm{3b}$
- Visually **guide horizontal reading**: Shade every other row $\mathrm{3a}$; Add dashed line every third row $\mathrm{3b}$ 
- Process input data: sort with column $\mathrm{3c}$ 
- More ideas: filter, sort, custom column titles, multi column names, Align at decimal or scientific separator
- See source examples: [Layout the table](./layout%20the%20table.md)

![table measurements 1.svg](./attachments/table%20measurements%201.svg)

calculate sum, mean, standard deviation under table
- [Add rows for sum/mean/std at end of pgfplotstable - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/179177/add-rows-for-sum-mean-std-at-end-of-pgfplotstable)
- [\[Pgfplots-features\] Simple calculations on columns of data](https://pgfplots-features.narkive.com/tu1Qxhx5/simple-calculations-on-columns-of-data)


# Sum up integers

![table stats integer sum.svg](./attachments/table%20stats%20integer%20sum.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\UseTblrLibrary{functional}
\renewcommand{\thetable}{3.1}
\IgnoreSpacesOn
\prgNewFunction \funcSum {} {
 \intStepOneInline {2} {\arabic{colcount}} {
 \intZero \lTmpaInt
 \intStepOneInline {2} {\arabic{rowcount}-1} {
 \intAdd \lTmpaInt {\cellGetText {####1} {##1}}
 }
 \cellSetText {\expWhole{\arabic{rowcount}}} {##1} {\intUse\lTmpaInt}
 }
}
\IgnoreSpacesOff
\begin{document}
\begin{tblr}[tall,caption]{
    colspec={rrr},process=\funcSum,
    column{1-Z}={r, mode=math}, column{1}={rightsep=0pt},
    row{1}={c,mode=text}, hline{1,Z}={.08em},hline{2,Y},
}
       & a & b & c \\
       & 1 & 2 & 3 \\
       & 4 & 5 & 6 \\
       & 7 & 8 & 9 \\
\Sigma &   &   &   \\
\end{tblr}
\end{document}
```

# Sum up floats

![table stats integer sum.svg](./attachments/table%20stats%20integer%20sum.svg)

```latex
\documentclass{standalone}
\usepackage{tabularray}
\usepackage{tabularray,tikz}
\UseTblrLibrary{functional}
\usetikzlibrary{fpu}
\renewcommand{\thetable}{3.2}
\IgnoreSpacesOn
\prgNewFunction \funcSum {} {
    \intStepOneInline {2} {\arabic{colcount}} { % for columns 2-Z
        \fpZero \sum % sum = 0.0
        \intStepOneInline {2} {\arabic{rowcount}-1} { % for rows 2-Y
            \fpAdd \sum {\cellGetText {####1} {##1}} % sum += cell
        }
        \cellSetText {\expWhole{\arabic{rowcount}}} {##1} {\fpUse\sum} % cell = sum
    }
}
\IgnoreSpacesOff
\begin{document}
\begin{tblr}[tall,caption]{
    colspec={rrr}, process=\funcSum, hline{1,Z}={.08em},hline{2,Y},
    column{1-Z}={r,mode=math,cmd=\pgfmathprintnumber}, 
    column{1}={rightsep=0pt,cmd={}},
    row{1}={c,mode=text,cmd={}}, 
}
       & a & b & c \\
       & 1 & 2.3 & 1.43587294e-01 \\
       & 4 & 5.2 & 4.41941738e-02 \\
       & 7 & 8.44 & 8.20091159e-03 \\
\Sigma &   &   &   \\
\end{tblr}
\end{document}
```

