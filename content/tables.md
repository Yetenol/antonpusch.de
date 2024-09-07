---
title: "Tables - Separate content in plaintext and styles like alignment, spacing, markup, and calculation, utilizing Tabularray"
dg-publish: true
dg-show-toc: true
aliases:
  - Table
---
Use only one[^1] package for tables, a modern LaTeX3 package with key-value configuration separating the styles and table content. Calculate correct cell dimensions, and spacing. Select rows, columns, cells, and grid lines for flexible designs, following these objectives:

- Keep the table data **portable**, raw, and readable: No macros in table content (except math macros supported by MathJax and KaTeX)
- Row, column **headers**: **Narrow** (down) **titles**; **Group** similar titles; Put more important columns to the left; Prefer **more rows** than columns
- Make layout **light-weight**: Few border lines; Spacing between cells, rows, columns; Few colors; Visually guide horizontal reading (Zebra, dashed lines)
- Horizontal **alignment**: **Left**-align text, row headers; **Right**-align numbers; **Center**-align column headers

My main resources are the official package documentation of Tabularray[^2], and documentation on LaTeX3 functional[^3], and expl3[^4].

> This tabularray package will \[...\] directly use LaTeX3 functions to parse the table, and then typeset the entire table. Under the premise of being compatible with the basic syntax of LaTeX2 tables, this macro package will completely separate the content and style of the table, and the style of the table can be completely set in keyval way.
- from package description of Tabularray[^2]

# Format table without changing the input data

## Format headers (first row, first column)

- **Group** row, column headings, see 1a
- Visually clarify table **boundaries**: Thick horizontal lines 1a
- Visually clarify **column titles** and **row titles**: Thin border line 1b, 1c; Left-aligned first column 1a, 1b
- Apply border **pattern**: Inner **gridlines** $\mathrm{1c}$
- Multicolumn header
- See source examples: [Format headers - Group, align, rotate, separate, and abbreviate the titles for rows and columns](./format%20headers.md)

![table headers.svg](./attachments/table%20headers.svg)

## Format numbers

- Prefix, Suffix, url, numbers right-aligned, text/left center-aligned; Number format, scientific notation, rounding, group every three digits, monospace, evaluate. Stats, also see [more styles](./follow%20varying%20typographic%20conventions%20with%20the%20same%20input%20syntax.md)
- pgfmathparse, dash 3rd line, math, siunit, pgfmathparse, date, money, command, macro, bold, color, fraction styles
- dateformat, fraction format, yes/no symbol, 
- See source examples: [Format numbers - Evaluate, Round to precision, Set decimal and thousands separator, Use scientific notations](./format%20numbers.md)

![table body.svg](./attachments/table%20body.svg)

## Format text

- Url, Monospace, Movie list, regex, detect name, replace LaTeX -> `\LaTeX`, auto truncate to footnote, autoheaders(rotate, group), vgroupdetect, hgroupdetect, auto format, replace empty cells, texttt
- See source examples: [Format text - Style body text in monospace, macros with slash](./format%20text.md)

![table text formatting.svg](./attachments/table%20text%20formatting.svg)

## Reference floating tables

- Let table float here, superwide, above, below, next to a page's main text
- Add caption,  and reference the table elsewhere
- **Placement, alignment**: center the table horizontally
- Add **references**: caption above and in the list of tables, label to cross-reference elsewhere
- More ideas: legende, Multifigure, Split, Longtable, surpress tableoftables entry, table next to text, globally set placement specifiers
- Center, Caption, Reference, Longtable, Caption below/above, Caption number, Figurename
- See source examples: [Floating table - Let table float here, superwide, above, below, next to a page's main text](./floating%20table.md)

![table floats.svg](./attachments/table%20floats.svg)

# Dynamically calculate cell text, style

- Dynamic calculation vs external preprocessing
- explain expl3, functional
- compare typst, lualatex, xetex, python, dataview, excel
- why separate formulas? excel copy pasting includes formatting
- Calculations need to be shown somewhere else in the document? => Dynamic calculations

## Row and column numbers

- See source examples: [Cell addresses - Count rows and columns relative to the entire table, its body, or the current group](./cell%20addresses.md)

![table counters.svg](./attachments/table%20counters.svg)

## Spreadsheets

- See source examples: [Spreadsheets - Calculate sum, mean, standard deviation, max, and min across selection of cells](./spreadsheets.md)

![table accumulate trip expenses.svg](./attachments/table%20accumulate%20trip%20expenses.svg)

## Table calculation

- See source examples: [Table calculation](./table%20calculation.md)

![table accumulate.svg](./attachments/table%20accumulate.svg)

# Set cell text, style with functions

- Row, column counter; Statistics (sum, mean, standard deviation), regex replace, conditional formatting, heatmap, negative values, validate values, calculate function, compare ideal function to meassured values
- excels capture values with text
-  See source examples: [Calculate statistics for table numbers](./calculate%20statistics%20for%20table%20numbers.md)

![table functional.svg](./attachments/table%20functional.svg)

## Import data from files

- Keep the data in **raw** and **universal** (csv) form: Update data anytime with external programs like Excel, Python, MATLAB, R, PowerShell
- Render **scientific notation** correctly and **uniform**: Render `4.41941738e-02` as $4.42 \cdot 10^{-2}$ $\mathrm{3a, 3b, 3c}$ 
- **Format numbers**: Set max. decimal places $\mathrm{3a, 3b, 3c}$; When to show exponent $\mathrm{3c}$; Use German commas $\mathrm{3b}$
- Visually **guide horizontal reading**: Shade every other row $\mathrm{3a}$; Add dashed line every third row $\mathrm{3b}$ 
- Process input data: sort with column $\mathrm{3c}$ 
- More ideas: filter, sort, custom column titles, multi column names, Align at decimal or scientific separator
- See source examples: [Process, and format values from files](./process%20and%20format%20values%20from%20files.md)

![table measurements 1.svg](./attachments/table%20measurements%201.svg)

# Layout, reference the table

## Split table in page columns

- Split in equal parts; 4a: Longtable split in half; References
- See source examples: [Layout the table](./layout%20the%20table.md)

![table layout 1.svg](./attachments/table%20layout%201.svg)



# Export formatted table

![table body macro column.svg](./attachments/table%20body%20macro%20column.svg)

$$
\begin{gather*}
\text{Table 2.3a:} \\
\begin{array}{ccr} \hline
\text{Name} & \text{Uniform} &
    \begin{matrix}\text{Alt}\\[-2pt] \text{code}\end{matrix} \\ \hline
\alpha\ \backslash\texttt{alpha} & \text{U+03B1} & 224 \\
\gamma\ \backslash\texttt{gamma} & \text{U+0393} & 226 \\
\delta\ \backslash\texttt{delta} & \text{U+03B4} & 235 \\ \hline
\end{array}
\end{gather*}
$$

|       Name        | Uniform | Alt<br>code |
| :---------------: | :-----: | :---------: |
| $\alpha$ `\alpha` | U+03B1  |     224     |
| $\gamma$ `\gamma` | U+0393  |     226     |
| $\delta$ `\delta` | U+03B4  |     235     |

# Things to avoid - Notes - Other

- [How to design good tables](How%20to%20design%20good%20tables.md)
- [More table examples, mainly pgfplotstable](./more%20table%20examples,%20mainly%20pgfplotstable.md)

- formatted text, multicolumn, code in table, image in content, empty cell, postproc, true/false → tickboxes, postprocess make command, detect backtick for commands
- convert backticks to verbatim
- convert text to textbackslash, texttt
- convert `X \ Y` to diagonal row title and column title
- detect columntitle is first markdown column is left aligned
- detect diagonal splitcell in top-leftmost when is contains `\`
- make all math displaymode, inline, fancyfrac [Nicefrac, sfrac - Nice fractions for inline math](Nicefrac,%20sfrac%20-%20Nice%20fractions%20for%20inline%20math.md)

Image in table

Calculate column sum


---
Sources:

Related:
- [Graphical elements - Standardize tables, images, plots](./graphical%20elements.md)
- [LaTeX - Typeset mathematical and scientific notation, handle cross-referencing and citations, and position images according to defined placement rules](./latex.md)
- [Markup and typesetting systems - Produce printed or digital documents aesthetically pleasing with readable typography](./markup%20and%20typesetting%20systems.md)
- [Style presets - Format your document after you written the content in Word, Latex, Markdown](Style%20presets%20-%20Format%20your%20document%20after%20you%20written%20the%20content%20in%20Word,%20Latex,%20Markdown.md)
- [Excel to latex - Embed spreadsheet files as latex tables](Excel%20to%20latex%20-%20Embed%20spreadsheet%20files%20as%20latex%20tables.md)


Tags:


[^1]: There are dozens of traditional LaTeX2 packages for tables which are inconsistent, and unpleasant to use. Here is a list, through the descriptions are not good: [tables - Which tabular packages do which tasks and which packages conflict? - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/12672/which-tabular-packages-do-which-tasks-and-which-packages-conflict)
[^2]: tabularray – Typeset tabulars and arrays with LaTeX3: [Overview - CTAN](https://ctan.org/pkg/tabularray) ; [Documentation - Mirrors](http://mirrors.ctan.org/macros/latex/contrib/tabularray/tabularray.pdf) ; [Wiki - GitHub](https://github.com/lvjr/tabularray/wiki) 
[^3]: functional – Provide an intuitive functional programming interface for LaTeX2: [Overview - CTAN](https://ctan.org/pkg/functional) ; [Documentation - Mirrors](http://mirrors.ctan.org/macros/latex/contrib/functional/functional.pdf) ; [Wiki - GitHub](https://github.com/lvjr/functional/wiki) 
[^4]: expl3 – Wrapper package for experimental LaTeX3: [Overview - CTAN](https://ctan.org/pkg/expl3) ; [Documentation - Mirrors](http://mirrors.ctan.org/macros/latex/required/l3kernel/expl3.pdf) ; [The LaTeX Project](https://www.latex-project.org/latex3/) 