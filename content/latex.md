---
title: "LaTeX - Typeset mathematical and scientific notation, handle cross-referencing and citations, and position images according to defined placement rules"
dg-publish: true
dg-permalink: latex
aliases: LaTeX
---
- LaTeX as cli tool
- this is a webpage, obviously not pdf
- figures
- like css
- not just one document
- don't worry about compile time

It's easy to start typesetting in LaTeX, and rely on TeX Stack Exchange's plentiful answers, whenever you don't know how to implement something. However, I encountered many seemingly simple solutions, that caused more trouble afterwards. Sometimes, changes will unknowingly affect other parts of your document; packages are outdated or straight up cause conflicts; or more modern LaTeX3 approaches should be preferred. 
Therefore, I developed guides on the following topics:

[Math - Typeset, align, wrap, comment, enumerate, space out, scale, and style mathematical expressions, utilizing amsmath](./latex-math.md)

$$
\begin{align*} \qquad&\hspace{-2em}
\mathbb{P}(X+Y=k) 
= \sum_{\mathclap{x \in X(\Omega)}} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}
$$

[Tables - Create tables and format by definiting styles in the preamble, utilizing pgfplotstable, tabularray](./latex-tables.md)

![figure format table headings.svg](./attachments/figure%20format%20table%20headings.svg)

[Listings - Print source code with syntax highlighting in latex with listings](./latex-listings.md)

![code block.svg](./attachments/code%20block.svg)

[Follow varying typographic conventions with the same input syntax](./follow%20varying%20typographic%20conventions%20with%20the%20same%20input%20syntax.md)

$$
\begin{gather*}
\left( \left( \left( ( ) \sqrt{2}  \right) \right) \right) \quad
\Bigg( \bigg( \Big( ( ) \sqrt{2}  \Big) \bigg) \Bigg) \tag{6a} \\
\frac{235}{711} \quad \tfrac{235}{711} \quad  {^{235} {\!/\!} _{711}} \quad {^{235} \mathclap{\diagup} _{711}} \tag{6b} \\
2.71828\times 10^{3} \quad 2{,}72\cdot 10^{3} \quad 2\,718{,}28 \tag{6c} \\
1 \, \mathrm{kg\, m / s^2} \quad 1 \, \mathrm{kg\, m s^{-2}} \quad 1 \, \mathrm{\tfrac{kg\, m}{s^2} } \tag{6d} \\
1{,}50 \,\text€ \quad \$\, 1.50 \quad 2 \,¥ \quad 1.50 \,\text{GBP} \tag{6e} \\
\text{March 1, 2024 \quad 1. März '24} \tag{6f}
\end{gather*}
$$

[Plots - Dynamically plot mathematical functions as a vector graphic](./plots.md)

![figure plots.svg](./attachments/figure%20plots.svg)

[Networks, Commutative diagrams - Dynamically draw graph networks as a vector graphic](./networks%20commutative%20diagrams.md)

![figure networks.svg](./attachments/figure%20networks.svg)

[Electrical circuit - Dynamically draw electronic circuit diagrams as a vector graphic](./electrical%20circuit.md)

![figure electrical circuit.svg](./attachments/figure%20electrical%20circuit.svg)

[Molecules - Dynamically draw structural formulas of chemical molecules as a vector graphic](./molecules.md)

![figure molecules.svg](./attachments/figure%20molecules.svg)



- [Values  - Standardize math, numbers, symbols, quantities, money](./values.md)
- [Float - Dynamically place figures, images, tables, and listings at the top, bottom, or single page](./float.md)
- [Graphics, Plots - Generate dynamic professional vector graphics with matching fonts, design](./graphics%20plots.md)
- [LaTeX Symbols - Lookup mathematical symbols, operations, relations, and arrows](./latex-symbols.md)
- [Learn and troubleshoot LaTeX - Read (package) documentation, cheat sheets, tutorials](./learn%20and%20troubleshoot%20latex.md)
- [Project structure - Create folders for setup, resources, bibliographies](./project%20structure.md)
- [Graphical elements - Standardize tables, images, plots](./graphical%20elements.md)
- [Layout the document - Setup margins, hyphenation, table of contents](./layout%20the%20document.md)
- [Develop LaTeX packages](./develop%20latex%20packages.md)

Learn, Troubleshoot, Debugging/Help/Documentation
- keep package number low
- don't create macros
- problem with text, quotes, math, tables, images, floats, listings, layout, development, setup, conversion, compile time, plots, graphics, citations

Basis text elements
Math
Tables
Images
Listings
Formatting, Layout
Development 
My setup
- writing, conversion, lint, debug
- which editor comparison
- Don't spent so much time on your setup, start writing code
- alternative markup systems

---
Sources:
- 2023-06-19: [How I'm able to take notes in mathematics lectures using LaTeX and Vim | Gilles Castel](https://castel.dev/post/lecture-notes-1/)
- [The LaTeX fetish (Or: Don’t write in LaTeX! It’s just for typesetting) – Daniel Allington](http://www.danielallington.net/2016/09/the-latex-fetish/)

Related:
- [Markdown - Write plaintext in a centralized location and generate to PDF, Jupiter notebooks, web pages, social media posts](Markdown%20-%20Write%20plaintext%20in%20a%20centralized%20location%20and%20generate%20to%20PDF,%20Jupiter%20notebooks,%20web%20pages,%20social%20media%20posts.md)
- [latex, pdf to cropped svg - Redraw selection of a pdf as paths in a svg with Inkscape](latex,%20pdf%20to%20cropped%20svg%20-%20Redraw%20selection%20of%20a%20pdf%20as%20paths%20in%20a%20svg%20with%20Inkscape.md)
- [Excel to latex - Embed spreadsheet files as latex tables](Excel%20to%20latex%20-%20Embed%20spreadsheet%20files%20as%20latex%20tables.md)
 

Tags:
[Markup and typesetting systems - Produce printed or digital documents aesthetically pleasing with readable typography](./markup%20and%20typesetting%20systems.md)
