---
title: "Tables - Create tables and format by definiting styles in the preamble, utilizing pgfplotstable, tabularray"
dg-publish: true
dg-show-toc: true
aliases:
  - Table
---
It's easy to start typesetting in LaTeX, and rely on TeX Stack Exchange's plentiful answers, whenever you don't know how to implement something. However, I encountered many seemingly simple solutions, that caused more trouble afterwards. Sometimes, changes will unknowingly affect other parts of your document; packages are outdated or straight up cause conflicts; or more modern LaTeX3 approaches should be preferred. 

- modern LaTeX3 package with key-value configuration
- why not just booktabs

There are dozens[^1] of packages for tables, and built-in environments, so what is the problem. 

# My Design Principles

- Keep the table data **raw**, and readable: No ma cros in table content (except math macros supported by MathJax, KaTeX)
- Row, column **headers**: More rows than columns; **Narrow** (down) **titles**; **Group** similar titles; Put more important columns to the left
- Make layout **light-weight**: Few border lines; Spacing between cells, rows, columns; Few colors; Visually guide horizontal reading (Zebra, dashed lines)
- Horizontal **alignment**: **Left**-align text, row headers; **Right**-align numbers; **Center**-align column headers
- [How to design good tables](How%20to%20design%20good%20tables.md)
- [Syntax - How to write tables](Syntax%20-%20How%20to%20write%20tables.md)

# Format headers (first row, first column)

- **Group** row, column headings, see 1a
- Visually clarify table **boundaries**: Thick horizontal lines 1a
- Visually clarify **column titles** and **row titles**: Thin border line 1b, 1c; Left-aligned first column 1a, 1b
- Apply border **pattern**: Inner **gridlines** $\mathrm{1c}$
- Multicolumn header
- See source examples: [Format table headings](./format%20table%20headings.md)

![table headers.svg](./attachments/table%20headers.svg)

# Process, format cell body

## Format raw cell body

- Prefix, Suffix, numbers right-aligned, text/left center-aligned; Number format, scientific notation, rounding, group every three digits, monospace, evaluate. Stats, also see [more styles](./follow%20varying%20typographic%20conventions%20with%20the%20same%20input%20syntax.md)
- See source examples: [Format raw cell body](./format%20raw%20cell%20body.md)

![table body.svg](./attachments/table%20body.svg)

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

## Add title and reference the table elsewhere

- **Placement, alignment**: center the table horizontally
- Add **references**: caption underneath and in the list of tables, label to cross-reference elsewhere
- More ideas: legende, Multifigure, Split, Longtable, surpress tableoftables entry, table next to text, globally set placement specifiers
- Center, Caption, Reference, Longtable, Caption below/above, Caption number, Figurename
- See source examples: [Add title numbers, caption, and reference the table elsewhere](./add%20title%20numbers,%20caption,%20and%20reference%20the%20table%20elsewhere.md) 

![minimal 50.svg](./attachments/minimal%2050.svg)

# Export formatted table

![table body macro column.svg](./attachments/table%20body%20macro%20column.svg)

$$
\begin{gather*}
\text{Table 2.3a:} \\
\begin{array}{ccr} \hline
\text{Name} & \text{Uniform} &
    \begin{matrix}\text{Alt}\\ \text{code}\end{matrix} \\ \hline
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

# Advanced input processing

- formatted text, multicolumn, code in table, image in content, empty cell, postproc, true/false → tickboxes, postprocess make command, detect backtick for commands
- convert backticks to verbatim
- convert text to textbackslash, texttt
- convert `X \ Y` to diagonal row title and column title
- detect columntitle is first markdown column is left aligned
- detect diagonal splitcell in top-leftmost when is contains `\`
- make all math displaymode, inline, fancyfrac [Nicefrac, sfrac - Nice fractions for inline math](Nicefrac,%20sfrac%20-%20Nice%20fractions%20for%20inline%20math.md)

Image in table

Calculate column sum

[More table examples, mainly pgfplotstable](./more%20table%20examples,%20mainly%20pgfplotstable.md)

---
Sources:

Related:
- [Graphical elements - Standardize tables, images, plots](./graphical%20elements.md)
- [LaTeX - Typeset mathematical and scientific notation, handle cross-referencing and citations, and position images according to defined placement rules](./latex.md)
- [Markup and typesetting systems - Produce printed or digital documents aesthetically pleasing with readable typography](./markup%20and%20typesetting%20systems.md)
- [Style presets - Format your document after you written the content in Word, Latex, Markdown](Style%20presets%20-%20Format%20your%20document%20after%20you%20written%20the%20content%20in%20Word,%20Latex,%20Markdown.md)
- [Excel to latex - Embed spreadsheet files as latex tables](Excel%20to%20latex%20-%20Embed%20spreadsheet%20files%20as%20latex%20tables.md)


Tags:


[^1]: Here are some of the packages for tables, though the descriptions are not good: [tables - Which tabular packages do which tasks and which packages conflict? - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/12672/which-tabular-packages-do-which-tasks-and-which-packages-conflict)
