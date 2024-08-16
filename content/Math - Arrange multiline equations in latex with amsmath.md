---
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
  
## Inline mode  
  
- `$` … `$`  
  
This is an inline math expression $\begin{array}{:c:} \hdashline \scriptstyle \sqrt{2} + \frac{1}{2}a \\ \hdashline \end{array}$ within a sentence.   
  
## Display mode  
  
- **Centered** equation(s): **Single** equation $\text{(1a)}$ `\[` …`\]`, Multiple equations `\begin{gather*}`  
- Alternating **right/left**-aligned columns: **Separated** pairs ${} \text{(1b)} {}$ `\begin{align*}`, $n$ pairs of **touching** columns $\text{(1c)}$ `\begin{alignat*}{2}`, Max. spaced-out to line width `\begin{flalign*}`  
- See source examples [Vertically align equations](./Vertically%20align%20equations.md)  
  
$$  
\gets \begin{array}{:c:} \hdashline xxxxx \\ \hdashline \end{array} \to \tag{1a}  
$$  
$$  
\begin{align*}  
\gets \begin{array}{:r:l:} \hdashline xx \!\!&\!\! = xxx \\ \hdashline x \!\!&\!\! =  x \\ \hdashline \end{array} & \to & \gets   
\begin{array}{:r:l:} \hdashline xxxx \!\!&\!\! =  x \\ \hdashline xx \!\!&\!\! = xxx \\ \hdashline \end{array} \to \tag{1b}  
\end{align*}  
$$  
$$  
\begin{alignat*}{2}  
\gets \begin{array}{:r:l:} \hdashline xx \!\!&\!\! =  xxx \\ \hdashline x \!\!&\!\! = x \\ \hdashline \end{array} &&   
\begin{array}{:r:l:} \hdashline xxxx \!\!&\!\! =  x \\ \hdashline xx \!\!&\!\! = xxx \\ \hdashline \end{array} \to \tag{1c}  
\end{alignat*}  
$$  
  
## Nested tabular mode  
  
- Surround with **delimiters** $\mathrm{(4a)}$ \begin{pmatrix} - \begin{cases}  
- **Split** overlong equations in multiple lines ${} \mathrm{(4b)} {}$  
  
$$  
\begin{align*} \qquad&\kern{-2em}  
x = \begin{pmatrix} \begin{array}{:c:c:} \hdashline xx \!\!&\!\! x \\ \hdashline x \!\!&\!\! xx \\ \hdashline x \!\!&\!\! x \\ \hdashline \end{array} \end{pmatrix}  + \begin{cases} \begin{array}{:l:l:} \hdashline xxx \!\!&\!\! \text{if } x \\ \hdashline x \!\!&\!\! \text{otherwise} \\ \hdashline \end{array} \end{cases} \tag{2a} \\&  
 = xxxxxxx \\&  
\! \begin{split} \begin{array}{:r:} \hdashline = xxxxxxxxxxxxx \\ \hdashline xxxxxxx \\ \hdashline \end{array}\end{split} \tag{2b} \\&  
\end{align*}  
$$  
  
# Symbols  
  
- Operators $\text{(3a)}$, Relations $\text{(3b)}$, Arrows $\text{(3c)}$  
- More: Roots, fraction, matrix, operators, relations, accents, greek letter | Limits, super/subscript | escevt for better vectors #34 | Split delimiter | Math in description heading | Breaking (page/column break) | Fonts #23, styles #30  
- See source examples [LaTeX Symbols - Lookup mathematical symbols, operations, relations, and arrows](./LaTeX%20Symbols%20-%20Lookup%20mathematical%20symbols,%20operations,%20relations,%20and%20arrows.md)  
  
$$  
\begin{gather*}  
+ - \cdot \times / \div : {}^\ \mid\,  \parallel \cup \cap \setminus \neg \land \lor \pm \Join \tag{3a} \\  
=\, \approx\, <\, \ge\, \triangleq\, \coloneqq\, \equiv\, \in\, \subset\, \supseteq\, \gg, \ne\, \nless\, \nsupseteq\,  \nsim  \tag{3b} \\  
\implies \nLeftarrow\!= \!\!\!\mathrlap{\quad\not}\iff \xrightarrow[\text{text}]{\text{long}}\, \nearrow\, \uparrow\, \updownarrow\, \dashleftarrow\, \Leftrightarrow\, \Downarrow\, \Updownarrow\, \circlearrowleft\, \Rsh \tag{3c} \\  
\end{gather*}  
$$  
  
  
# Wrap long equation over multiple lines  
  
- Split long fractions over two lines $\text{(4a)}$, Indent subsequent lines $\text{(4b-c)}$, Wrap overlong equations $\text{(4b)}$  
- See source examples [Wrap long equation over multiple lines](./Wrap%20long%20equation%20over%20multiple%20lines.md)  
  
  
$$  
\begin{align*}\qquad&\kern{-2em}  
x = xx +  \frac{  \begin{split} xxxxxxx \quad\\[-1ex] + xxxx \end{split} }{x} +  \frac{ \substack{xxxxxxx \\ +xxxx} }{x}\tag{4a} \\&  
\begin{split}\; =  xxxxxxxxxx \\ xxx\end{split} \tag{4b} \\&  
 =  xxxxx \tag{4c}  
\end{align*}   
$$  
  
# Comment equation operators  
  
- Comment: **Above**/below operators$^{(1)}$, In a **paragraph** between math displays$^{(2)}$, **Braces** under parts of an expression${} ^{(3a)}$, Comment a **case**$^{(3b)}$, Name matrix columns and rows  
- See source examples [Comment equation operators](Comment%20equation%20operators.md)  
  
$$  
x \overset{\text{def}}{=} xxxx\overset{\mathclap{\text{use (3)}}}{=} xxxx \xRightarrow{+ x} xxxx \tag{1}  
$$  
$\text{Write a paragraph between equations:}$  
$$  
\, \tag{2}  
$$  
$$  
x = \underbrace{ xxxxx }_{\text{for }x} \underbrace{ xxxx }_{ \mathclap{\substack{\text{for }x\\ \text{and relatives}} }  }  
= \begin{cases} xx,  & \text{for } x \\ x,  & \text{because blah}  \\& \text{blab blub} \end{cases} \tag{3}  
$$  
  
# Reference equations  
  
- roman style  
- ctagsplit and righttag [Mathematical Typesetting with Latex 0.34 2024-02-06, page 69](./attachments/Mathematical%20Typesetting%20with%20Latex%200.34%202024-02-06.pdf.md#page=69&selection=174,0,179,0)  
  
$\text{From calculation \textcolor{blue}{(1)} on page \textcolor{blue}{1}, we can derive:}$  
$$  
\begin{align*}  
\begin{aligned}  
x &= x & (1) \\  
x &\overset{\mathclap{\text{use \textcolor{blue}{(2)}}}}{=} x & (\text{I}) \\  
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
  
- Scale, Placement: Spread math over multiple display columns$^{(1)}$, Scale delimiters manually/automatically$^{(2)}$, Scale repeating operators$^{(2)}$, Place limits surrounding/next to it$^{(2)}$ `\limit` - `\nolimit`, Scale equations `exscale`  
- Spacing$^{(3)}$: Between lines likes insides a matrix$^{(3)}$ `\\[1ex]` - `\jot`, text fraction styles$^{(3)}$, 1000 separator$^{(3)}$, Index (icomma german), smash for inline math, `mathrlap`, Matrix spacing #30, styles, Fix delimiter space  
- Formatting${} ^{(4)}$: color$^{(4)}$ `\textcolor`, Diagonal strikeout$^{(4)}$ `\cancel` - `\bcancel` - `\xcancel`, Draw rectangle around math$^{(4)}$ `\boxed` - `\begin{array}`, boldmath, titlemath, everydisplay, everymath, underline, long text -> parbox, strikethrough  
- See source examples [Layout multiple equations](Layout%20multiple%20equations.md)  
  
$$  
\begin{gather*}  
\hphantom{\cdots\quad} x = x \quad x = x \quad x = x \quad\cdots \tag{1} \\  
\Big(\big(()\big)\Big),\; {\huge\sum_{j = 1}} \sum_{i = 1}^{\infty} i,\; \int_0^1 \int\limits_0^1 \tag{2} \\  
\begin{pmatrix} 0 1 \\[-1ex] 10 \\ 01 \end{pmatrix},\; \tfrac{3}{11} \, {}^{3\!}/_{\!11} \frac{3}{11}\,a,\; 12\,345 \tag{3} \\   
\textcolor{magenta}{a + b^2},\; \cancel{a + b^2},\; \boxed{a + b^2}\; \begin{array}{:c:} \hdashline a + b^2 \\ \hdashline \end{array} \tag{4}  
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
- new operator [Mathematical Typesetting with Latex 0.34 2024-02-06, page 41](./attachments/Mathematical%20Typesetting%20with%20Latex%200.34%202024-02-06.pdf.md#page=41&selection=259,7,259,18)  
  
- In markdown put display math delimiters `$$` on a separate line  
- Don't leave spaces in front of caret to prevent block reference detection (write `a^2` instead of `a ^2`)  
