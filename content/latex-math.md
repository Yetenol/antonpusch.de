---
title: "Math - Typeset, align, wrap, comment, enumerate, space out, scale, and style mathematical expressions, utilizing amsmath"
dg-publish: true
dg-permalink: latex-math
dg-show-toc: true
---

# Motivation

Mainly based on [Mathematical Typesetting with LaTeX - Herbert Voß 2023](https://www.tug.org/~hvoss/PDF/mathmode.pdf) (view [TeX code](https://www.tug.org/~hvoss/)) which is an updated version of [Math mode - Herbert Voß 2014](https://mirror.physik.tu-berlin.de/pub/CTAN/obsolete/info/math/voss/mathmode/Mathmode.pdf).
- Packages: amsmath, mathtools, empheq

# Syntax

```latex
\documentclass{article}
\usepackage{mathtools,amssymb,amsfonts}
\begin{document}
Let $f = x^2 + \frac{1}{11}$:
\begin{align*} \qquad&\hspace{-2em}
\mathbb{P}(X+Y=k) 
= \sum_{\mathclap{x \in X(\Omega)}} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}
\end{document}
```

Let $f = x^2 + \frac{1}{11}$:
$$
\begin{align*} \qquad&\hspace{-2em}
\mathbb{P}(X+Y=k) 
= \sum_{\mathclap{x \in X(\Omega)}} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}
$$

# Math modes

**Inline** mode: `$` … `$`, see example in the paragraph

**Display** mode, see $(\mathrm{1a\text{-}c})$ 
- **Centered** equation(s): **Single** equation $\mathrm{(1a)}$ `\[` …`\]`, Multiple equations `\begin{gather*}`
- Alternating **right/left**-aligned columns: **Separated** pairs $\text{(1b)}$ `\begin{align*}` - $n$ pairs of **touching** columns $\mathrm{(1c)}$ `\begin{alignat*}{2}` - Max. spaced-out to line width `\begin{flalign*}`
- See source examples: [Vertically align equations](./vertically%20align%20equations.md)

**Nested** tabular math with **r**ight, **c**enter, and **l**eft aligned columns, see $\mathrm{(1d\text{-}e)}$
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
- See source examples [LaTeX Symbols - Lookup mathematical symbols, operations, relations, and arrows](./latex-symbols.md)

$$
\begin{gather*}
+ - \cdot \times / \div :{} \Sigma \smallint \Im\,  \Re \mid\, \parallel \cap \setminus \neg \land \pm \Join \tag{2a} \\
=\, \approx\, <\, \ge\, \triangleq\, \coloneqq\, \equiv\, \in\, \subset\, \supseteq\, \gg, \ne\, \nless\, \nsupseteq\,  \nsim  \tag{2b} \\
\implies \nLeftarrow\!= \!\!\!\mathrlap{\quad\not}\iff \xrightarrow[\text{text}]{\text{long}}\, \nearrow\, \uparrow\, \updownarrow\, \dashleftarrow\, \Leftrightarrow\, \Downarrow\, \Updownarrow\, \circlearrowleft\, \Rsh \tag{2c} \\
\alpha \beta \varGamma \Delta E, \mathrm{Z H}, \mathit{\Theta I}, \mathcal{K \Lambda}, \mathscr{M N},  \mathfrak{3 O},  \mathbb{1 P} \tag{2d} \\
(\, )\; \Big\lgroup\,\Big\rgroup\; [\,]\; \left\{ x \;\middle\vert\; x < \sqrt{2}  \right\}\;  \vert\, \rangle \left[ \begin{smallmatrix} a&b\\c&d \end{smallmatrix} \right]\, \lfloor\rceil \tag{2e}
\end{gather*}
$$

# Wrap long equation over multiple lines

- **Split** long **fractions** in two lines ${} \mathrm{(3a)} {}$, **Indent subsequent** lines ${} \mathrm{(3b\text{-}c)} {}$, **Wrap overlong** equations $\mathrm{(3b)}$
- See source examples [Wrap long equation over multiple lines](./wrap%20long%20equation%20over%20multiple%20lines.md)

$$
\begin{align*}\qquad&\kern{-2em}
x = xx +  \frac{  \begin{split} xxxxxxx \quad\\[-1ex] + xxxx \end{split} }{x} +  \frac{ \substack{xxxxxxx \\ +xxxx} }{x}\tag{3a} \\&
\begin{split}\; =  xxxxxxxxxx \\ xxx\end{split} \tag{3b} \\&
 =  xxxxx \tag{3c}
\end{align*} 
$$

# Comment equation operators

- Comment: **Over**/under operators ${} \mathrm{(4a)} {}$, In a **paragraph** between math displays, **Braces** under parts of an expression $\mathrm{(4b)}$, Comment a **case** $\mathrm{(4b)}$, Name matrix columns and rows
- See source examples [Comment equation operators](Comment%20equation%20operators.md)

$$
x \overset{\text{def}}{=} xxxx\overset{\mathclap{\text{use (3)}}}{=} xxxx \xRightarrow{+ x} xxxx \tag{4a}
$$
Write a paragraph between equations.
$$
x = \underbrace{ xxxxx }_{\text{for }x} \underbrace{ xxxx }_{ \mathclap{\substack{\text{for }x\\ \text{and relatives}} }  }
= \begin{cases} xx,  & \text{for } x \\ x,  & \text{because blah}  \\& \text{blab blub} \end{cases} \tag{4b}
$$

# Reference equations

- roman style
- ctagsplit and righttag [Mathematical Typesetting with Latex 0.34 2024-02-06, page 69](./attachments/mathematical%20typesetting%20with%20latex%200.34%202024-02-06.pdf.md#page=69&selection=174,0,179,0)

From calculation $\textcolor{limegreen}{(1)}$ on page $\textcolor{limegreen}{1}$, we can derive:
$$
\begin{align*}
\begin{aligned}
x &= x & (1) \\
x &\overset{\mathclap{\text{use \textcolor{limegreen}{(2)}}}}{=} x & (\text{I}) \\
x &= x & (2) \\
\end{aligned}
\qquad
\begin{aligned}
&&x &= x & \text{II}  \\
(3.1) && x &= x &  \\
&&x &= x & [\text{lin.}]  \\
\end{aligned}
\end{align*}
$$

# Create commutative diagrams

- [Amscd graphs](Amscd%20graphs.md)

$$
\begin{align*}
\begin{CD}
A @>a>> B\\
@VVbV @VVcV\\
C @>d>> D
\end{CD}
\end{align*}
$$

# Layout multiple equations

- Spread math over multiple display columns ${} \mathrm{(5a)} {}$
- Scale, Placement ${} \mathrm{(5b)} {}$: **Scale delimiters** manually/automatically, Scale **repeating operators**, Force **limits**, or exponents and indices `\limit` - `\nolimit`, Scale equations `exscale`
- Spacing ${} \mathrm{(5c)} {}$: After line breaks `\\[1ex]` - `\jot`,  fraction styles, 1000 separator, Index (icomma german), smash for inline math, `mathrlap`, Matrix spacing #30, styles, Fix delimiter space
- Formatting $\mathrm{(5d)}$: color `\textcolor`, Diagonal strikeout `\cancel` - `\bcancel` - `\xcancel`, Draw rectangle around math `\boxed` - `\begin{array}`, boldmath, titlemath, everydisplay, everymath, underline, long text -> parbox, strikethrough
- See source examples [Layout multiple equations](Layout%20multiple%20equations.md)

$$
\begin{gather*}
\hphantom{\cdots\quad} x = x \quad x = x \quad x = x \quad\cdots \tag{5a} \\
\Big(\big(()\big)\Big),\; {\huge\sum_{j = 1}} \sum_{i = 1}^{\infty} i,\; \int_0^1 \int\limits_0^1 \tag{5b} \\
\begin{pmatrix} 0 1 \\[-1ex] 10 \\ 01 \end{pmatrix},\; \tfrac{3}{11} \, {}^{3\!}/_{\!11} \frac{3}{11}\,a,\; 12\,345 \tag{5c} \\ 
\textcolor{magenta}{a + b^2},\; \cancel{a + b^2},\; \boxed{a + b^2}\; \begin{array}{:c:} \hdashline a + b^2 \\ \hdashline \end{array} \tag{5d}
\end{gather*}
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
