---
dg-publish: true
aliases:
  - Textsatzsysteme
---
# Content

[Math - Typeset, align, wrap, comment, enumerate, space out, scale, and style mathematical expressions, utilizing amsmath](./latex-math.md)
$$
\begin{align*} \qquad&\hspace{-2em}
\mathbb{P}(X+Y=k) 
= \sum_{\mathclap{x \in X(\Omega)}} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}
$$
[Tables - Create tables and format by definiting styles in the preamble, utilizing pgfplotstable, tabularray](./latex-tables.md)
![minimal 45.svg](./attachments/minimal%2045.svg)
[Listings - Print source code with syntax highlighting in latex with listings](./latex-listings.md)
![code block.svg](./attachments/code%20block.svg)

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
[Computer Language](./computer%20language.md)