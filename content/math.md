---
title: "Math - Typeset, align, wrap, comment, enumerate, space out, scale, and style mathematical expressions, utilizing amsmath"
dg-publish: true
dg-show-toc: true
aliases:
  - Math
---
LaTeX's mathematical notation syntax has gained widespread adoption for formatting equations and formulas. It is now integrated into numerous digital platforms like markdown editors, web pages, word processing software, and online forums. But as with text, uniform, comprehensible formatting is not a matter of course. Good information is often spread across different documentation and organized according to implementation rather than the problem it solves.
Therefore, I created my own documentation to achieve the following objectives:

- Maximum **compatibility**: Use macros supported by KaTeX, MathJax, PdfLaTeX, to edit and preview in Obsidian, VSCode, and Overleaf, and to generate websites and PDFs.
- **Portability**: Emphasis on **established packages** that are better implemented. **No custom macros** - Built-in macros might be longer, but they are universally understood.
- **Direct** representation of **values**: I prefer seeing and editing the output values in place, rather than jumping through variables, dynamic calculations, or macro definitions.
- On-demand **minimal syntax**: Add complexity (like `\left`-`\right` or extra braces) only when needed to keep the expressions shorter, and visually light weight.

My main resources are *Mathematical Typesetting with LaTeX*[^1] and the older LaTeX2 guide *The Not So Short Introduction to LATEX*[^2], as well as the official package documentations.

> The amsmath package is a LATEX package that provides miscellaneous enhancements for improving the information structure and printed output of documents
> that contain mathematical formulas.
- [Introduction p. 5](https://texdoc.org/serve/amsmath/0#page=5) from AMSmath User’s Guide


Let $f = x^2 + \frac{1}{11}$:
$$
\begin{align*} \qquad&\hspace{-2em}
\mathbb{P}(X+Y=k) 
= \sum_{\mathclap{x \in X(\Omega)}} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}
$$
- See source example: [Showcase of math equations](./showcase%20of%20math%20equations.md)

# Math modes

**Inline** mode: `$` … `$`, see example in the paragraph

**Display** mode, see $(\mathrm{1a\text{-}c})$ 
- **Centered** equation(s): **Single** equation $\mathrm{(1a)}$ `\[` …`\]`, Multiple equations `\begin{gather*}`
- Alternating **right/left**-aligned columns: **Separated** pairs $\text{(1b)}$ `\begin{align*}` - $n$ pairs of **touching** columns $\mathrm{(1c)}$ `\begin{alignat*}{2}` - Max. spaced-out to line width `\begin{flalign*}`
- See source examples: [Array-like environments - Align equations and relation symbol relative to each other](./array-like%20environments.md)

**Nested Array**: Element inside inline or display mode containing columns aligned to the **r**ight, **c**enter, or **l**eft, see $\mathrm{(1d\text{-}e)}$
- Surround with **delimiters**, see $\mathrm{(1d)}$: $\left( \begin{smallmatrix} c&c\\ c&c \end{smallmatrix} \right)$ `\begin{pmatrix}` - $\left\{ \begin{smallmatrix} l&l\\ l&l \end{smallmatrix} \right.$ `\begin{cases}`
- **Split** overlong equations in multiple lines $\mathrm{(1e)}$: $\;\begin{smallmatrix} r\\ r \end{smallmatrix}$ `\begin{split}`

This is an inline math expression $\begin{array}{:c:} \hdashline \scriptstyle \!\! \sqrt{2} + \frac{1}{2}a + {}^{1} \!/_{2} \!\! \\ \hdashline \end{array}$ within a paragraph, where symbols are smaller to keep the line height consistent within blocks of text. 
$$
\begin{gather*}
\gets\! \begin{array}{:c:} \hdashline xxxxx \\ \hdashline \end{array} \!\to \tag{1a} \\
\gets\! \begin{array}{:r:l:} \hdashline xx \!\!&\!\! = xxx \\ \hdashline x \!\!&\!\! =  x \\ \hdashline \end{array} \!\to \quad \gets\! 
\begin{array}{:r:l:} \hdashline xxxx \!\!&\!\! =  x \\ \hdashline xx \!\!&\!\! = xxx \\ \hdashline \end{array} \!\to \tag{1b} \\
\gets\! \begin{array}{:r:l:r:l:} \hdashline xx \!\!&\!\! =  xxx\!\! & \!\!= \!\!&\!\!  x \\ \hdashline x \!\!&\!\! = x & \!\!= \!\!&\!\! xxx \\ \hdashline \end{array} \!\to \tag{1c}
\end{gather*}
$$

$$
\begin{align*} \qquad&\kern{-2em}
x = \begin{pmatrix} \begin{array}{:c:c:} \hdashline xx \!\!&\!\! x \\ \hdashline x \!\!&\!\! xx \\ \hdashline x \!\!&\!\! x \\ \hdashline \end{array} \end{pmatrix}  + \begin{cases} \begin{array}{:l:l:} \hdashline xxx \!\!&\!\! \text{if } xx \\ \hdashline x \!\!&\!\! \text{otherwise} \\ \hdashline \end{array} \end{cases} \tag{1d} \\&
 = xxxxxxx \\&
\! \begin{split} \begin{array}{:r:} \hdashline = xxxxxxxxxxxxx \\ \hdashline xxxxxxx \\ \hdashline \end{array}\end{split} \tag{1e} \\&
\end{align*}
$$

# Symbols

- Operators $\mathrm{(2a)}$, Relations ${} \mathrm{(2b)}$, Arrows $\mathrm{(2c)}$
- More: Roots, fraction, matrix, operators, relations, accents, greek letter | Limits, super/subscript | escevt for better vectors #34 | Split delimiter | Math in description heading | Breaking (page/column break) | Fonts #23, styles #30
- See source examples: [LaTeX Symbols - Lookup mathematical symbols, operations, relations, and arrows](./latex-symbols.md)

$$
\begin{gather*}
+ - \cdot \times / \div :{} \Sigma \smallint \Im\,  \Re \mid\, \parallel \cap \setminus \neg \land \pm \Join \tag{2a} \\
=\, \approx\, <\, \ge\, \triangleq\, \coloneqq\, \equiv\, \in\, \subset\, \supseteq\, \gg, \ne\, \nless\, \nsupseteq\,  \nsim  \tag{2b} \\
\implies \nLeftarrow\!= \!\!\!\mathrlap{\quad\not}\iff \xrightarrow[\text{text}]{\text{long}}\, \nearrow\, \uparrow\, \updownarrow\, \dashleftarrow\, \Leftrightarrow\, \Downarrow\, \Updownarrow\, \circlearrowleft\, \Rsh \tag{2c} \\
\alpha \beta \varGamma \Delta E, \mathrm{Z H}, \mathit{\Theta I}, \mathcal{K \Lambda}, \mathscr{M N},  \mathfrak{3 O},  \mathbb{1 P} \tag{2d} \\
(\, )\; \Big\lgroup\,\Big\rgroup\; \big[\,\big]\; \left\{ x \;\middle\vert\; x < \sqrt{2}  \right\}\;  \vert\, \rangle \left[ \begin{smallmatrix} a&b\\c&d \end{smallmatrix} \right]\, \lfloor\rceil \tag{2e}
\end{gather*}
$$

# Wrap long equation over multiple lines

- **Split** long **fractions** in two lines $\mathrm{(3a)}$, **Indent subsequent** lines $\mathrm{(3b\text{-}c)}$, **Wrap overlong** equations $\mathrm{(3b)}$
- See source examples: [Wrap long equation over multiple lines](./wrap%20long%20equation%20over%20multiple%20lines.md)

$$
\begin{align*}\qquad&\kern{-2em}
x = xx +  \frac{  \begin{split} xxxxxxx \quad\\[-1ex] + xxxx \end{split} }{x} +  \frac{ \substack{xxxxxxx \\ +xxxx} }{x}\tag{3a} \\&
\begin{split}\; =  xxxxxxxxxx \\ xxx\end{split} \tag{3b} \\&
 =  xxxxx \tag{3c}
\end{align*} 
$$

# Comment, explain your calculations

- Comment **relations**, see $\mathrm{(4a)}$: $\;{}^\text{def}$ Write short text **above**/below - $^i$ Put **longer** text in a separate **paragraph** - $^\text{use (4b)}$ Write **zero-width** overlapping text - $^{+xx}$ Write on a **extensible** arrow
- Span **braces** under/over expressions, with possible overlap, see start of $\mathrm{(4b)}$ 
- Comment nested **array**: Describe a case, see end of $\mathrm{(4b)}$; Name matrix columns and rows
- See source examples: [Comment equation operators](Comment%20equation%20operators.md)

$$
\begin{gather*}
x \overset{\text{def}}{=} x \overset{i}{=} xxx \overset{\mathclap{\text{use (4b)}}}{=} xxx \xRightarrow{+ xx} x \tag{4a} \\
x = \mathrlap{\phantom{(x)}\overbrace{\phantom{x xx}}^{\text{for }x}}  \underbrace{ (x)x }_{\text{for }x}  \underbrace{ \vphantom{(} xx \cdot x }_{ \mathclap{\substack{\text{for }x\\ \text{and relatives}} }  }
= \begin{cases} xx  & \text{for } xx \\[-1ex] & \text{because}\ldots \\ x  & \text{ow.} \end{cases} \tag{4b}
\end{gather*}
$$
$\overset{i}{=}\;:$ Is equal because the function is symmetrical in the interval $[-1, 1]$.

# Reference, highlight equations

- Equation number $\mathrm{(5a)}$: Combine **arabic, roman** alphabet; current **section, part** numbers; and static **delimiters, text** to reference the equation elsewhere
- **Highlight** part of an equation $\mathrm{(5b)}$: **Bold** math `boldsymbol`, Diagonal **strikeout** `\cancel` - `\bcancel` - `\xcancel`, Draw **rectangle** around math `\boxed` - `\begin{array}`
- More: color `\textcolor`, boldmath, titlemath, ctagsplit and righttag [Mathematical Typesetting with Latex 0.34 2024-02-06, page 69](./attachments/mathematical%20typesetting%20with%20latex%200.34%202024-02-06.pdf.md#page=69&selection=174,0,179,0)

$$
\begin{gather*} \\
\text{[1], [2], (I), i, ii, linear, [3a], [3b], (I-3-0)} \tag{5a} \\
x + \boldsymbol{xx^{x}x} + \cancel{xx^{x}x} + \boxed{xx^{x}x} + \begin{array}{:c:} \hdashline\! xx^{x}x \!\\ \hdashline \end{array} \tag{5b} \\
\end{gather*}
$$

# Follow varying typographic conventions with the same input syntax

- [c] usually not supported in Obsidian (MathJax); VSCode, Quartz (KaTeX)
- [c] less readable source
- [c] depend on package, or project
- [p] formatting in separate from the document
- Auto-scale left-right delimiter pairs $\mathrm{(6a)}$: `\delimitershortfall`
- Fraction in textstyle $\mathrm{(6b)}$: `\frac` - `\sfrac` - `\nicefrac`
- European, American number format $\mathrm{(6c)}$: `\num` - `\pgfmathprintnumber`
- Units, quantities $\mathrm{(6d)}$: `\unit` - `\qty`
- Currencies, money $\mathrm{(6e)}$: `\dEUR` - `\cJPY`
- Dates $\mathrm{(6f)}$: pgfcalendar
- See source examples: [Follow varying typographic conventions with the same input syntax](./follow%20varying%20typographic%20conventions%20with%20the%20same%20input%20syntax.md)

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

# Use typographic template for appearance of numbers

- Spread math over multiple display columns $\mathrm{(7a)}$
- Scale, Placement ${} \mathrm{(7b)} {}$: **Scale delimiters** manually/automatically, Scale **repeating operators**, Force **limits**, or exponents and indices `\limit` - `\nolimit`, Scale equations `exscale`
- Spacing $\mathrm{(7c)}$: After line breaks `\\[1ex]` - `\jot`, fraction styles, 1000 separator, Index (icomma german), smash for inline math, `mathrlap`, Matrix spacing #30, styles, Fix delimiter space
- everydisplay, everymath, underline, long text -> parbox, strikethrough, allowlinebreak, delimitershortfal



$$
\begin{gather*}
\hphantom{\cdots\quad} x = x \quad x = x \quad x = x \quad\cdots \tag{7a} \\
\Big(\big(()\big)\Big),\; {\huge\sum_{j = 1}} \sum_{i = 1}^{\infty} i,\; \int_0^1 \int\limits_0^1 \tag{7b} \\
\begin{pmatrix} 0 1 \\[-1ex] 10 \\ 01 \end{pmatrix},\; \tfrac{3}{11} \, {}^{3\!}/_{\!11} \frac{3}{11}\,a,\; 12\,345 \tag{7c} \\ 
\end{gather*}
$$

# Create commutative diagrams

- See source examples: [Simple commutative diagrams supported by KaTeX, MathJaX - Amscd](Simple%20commutative%20diagrams%20supported%20by%20KaTeX,%20MathJaX%20-%20Amscd.md)
- See more complex examples: [Networks, Commutative diagrams - Dynamically draw graph networks as a vector graphic](./networks%20commutative%20diagrams.md)

$$
\begin{align*}
\begin{CD}
A @>a>> B\\
@VVbV @VVcV\\
C @>d>> D
\end{CD}
\end{align*}
$$

# Things to avoid, deprecated, bad syntax

- no `\\` at end of align
- put `[]` after suqenvironments
- [How not to typeset math in latex](How%20not%20to%20typeset%20math%20in%20latex.md)
Deprecated
- eqnarray
- font syntax
- stackrel
- xalignat, xxalignat
- new operator [Mathematical Typesetting with Latex 0.34 2024-02-06, page 41](./attachments/mathematical%20typesetting%20with%20latex%200.34%202024-02-06.pdf.md#page=41&selection=259,7,259,18)

- In markdown put display math delimiters `$$` on a separate line
- Don't leave spaces in front of caret to prevent block reference detection (write `a^2` instead of `a ^2`)

[^1]: [Mathematical Typesetting with LaTeX](https://www.tug.org/~hvoss/PDF/mathmode.pdf) by Herbert Voß in 2024 which is an updated version of his 2014 [Math mode](https://mirror.physik.tu-berlin.de/pub/CTAN/obsolete/info/math/voss/mathmode/Mathmode.pdf) 
[^2]: [The Not So Short Introduction to LATEX](https://tobi.oetiker.ch/lshort/lshort.pdf) - Or LATEX in 280 minutes by Tobias Oetiker, Marcin Serwin Hubert Partl, Irene Hyna, and Elisabeth Schlegl in 2023 which in based on the german [LATEX 2ε-Kurzbeschreibung](https://ftp.gwdg.de/pub/ctan/info/lshort/german/l2kurz.pdf) by Marco Daniel, Patrick Gundlach, Walter Schmidt, Jörg Knappen, Hubert Partl, and Irene Hyna in 2018
