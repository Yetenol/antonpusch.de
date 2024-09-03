- Keep the data in **raw**, readable and **universal** (csv) form: Update data anytime with external programs like Obsidian, PowerShell, Excel, Python, MATLAB, R
- compatible with Overleaf's pdflatex, Obsidian's Visual editor, Obsidian, Quartz, Powershell (gridview, csv, html, terminal), Excel, Python
- no macros in table content
- latex: format, layout table
- table content must work in tabular
- no pgfmathparse of texttt in every cell, easy to edit values

> This package reads tab-separated numerical tables from input and generates code for pretty-printed
> LATEX-tabulars. It rounds to the desired precision and prints it in different number formatting styles.
- [Abstract p. 1](https://texdoc.org/serve/pgfplotstable/0) from PgfplotsTable Manual

## How to do it right

- project independent
- formatting shouldn't touch data
- export from markdown
- future proof
- pgf great for calculation
- why not calculate before hand?
- tabularray great for formatting: better margin, auto fit cell content, easier cell formatting
- [Table interoperable designs](Table%20interoperable%20designs.md)

# Examples

- [table examples](table%20examples.md)
- [Dos & don't of table design - Guide what to consider when creating tables](./content/dos%20don't%20of%20table%20design.md)
- [Data Tables Design. Basics | by Taras Bakusevych | Medium](https://taras-bakusevych.medium.com/data-tables-design-3c705b106a64)
- [Design better data tables](Design%20better%20data%20tables.md)
- [getinthepicture.org/sites/default/files/resources/8. Good tables.pdf](https://getinthepicture.org/sites/default/files/resources/8.%20Good%20tables.pdf)
- [What to consider when creating tables](https://blog.datawrapper.de/guide-what-to-consider-when-creating-tables/)
- [Table vs Graph - The Visual Battle — storytelling with data](https://www.storytellingwithdata.com/blog/2011/11/visual-battle-table-vs-graph)
- [How to design complex web tables | Slava Shestopalov | Design Bridges](https://medium.com/design-bridges/complex-tables-356826d11861)
- [Interactive diagram](Interactive%20diagram.md)