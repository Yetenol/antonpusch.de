---
publish: true
aliases:
  - Textsatzsysteme
---
# Content

[Math - Typeset, align, wrap, comment, enumerate, space out, scale, and style mathematical expressions, utilizing AMSmath](./latex/math/Math.md)

$$
\begin{align*} \qquad&\hspace{-2em}
\mathbb{P}(X+Y=k) 
= \sum_{\mathclap{x \in X(\Omega)}} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}
$$

[Tables - Separate content in plaintext and styles like alignment, spacing, markup, and calculation, utilizing Tabularray](./tables.md)

![table headers.svg](./attachments/table%20headers.svg)

[Code Snippets - Print source code with syntax highlighting in latex with listings](./Code%20snippets.md)

![code block.svg](./attachments/code%20block.svg)


[Graphics - Draw vector networks, graphs, images, plots in latex with tikz, pgf](./Graphics.md)

![figure plots.svg](./attachments/figure%20plots.svg)

[PyPlot](./pyplot.md)

![pyplot_features_demo.svg](./attachments/pyplot_features_demo.svg)

[Dataview - Create dynamic tables using data stored in note properties](./Dataview.md)

- Convert dataview to static markdown for publishing




# Tools

```dynamic-embed
[[List related notes]]
``` 
# Typography

- determine good line breaks for whole paragraphs at once
- Kerning: when letters move closer together, e.g. the 'T" and 'e' in Tea'
- Ligatures: when letters merge together, e.g fi"
- prevent widows and orphans: lonely lines at the start or end of a page, respectively

# Structured documents 

- sections, headings, figures, tables, images, a table of contents, cross-references


---
Sources:

Related:

Tags:
[Computer Language](./Computer%20language.md)

https://blog.ppresume.com/posts/on-typesetting-engines
On Typesetting Engines: A Programmer's Perspective https://blog.ppresume.com/posts/on-typesetting-engines