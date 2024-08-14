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
\begin{document}  
  
The well known Pythagorean theorem $x^2 + y^2 = z^2$ was   
proved to be invalid for other exponents.   
Meaning the next equation has no integer solutions:  
  
\[   
\vec{B} = \frac{\mu I}{2 \pi r} \vec{e}_\phi  
\]  
  
\begin{align*}  
\mathbb{P}(X+Y=k) &  
= \sum_{x \in X(\Omega)} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x)   
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}  
\end{align*}  
  
\end{document}  
```  
  
The well known Pythagorean theorem $x^2 + y^2 = z^2$ was   
proved to be invalid for other exponents.   
Meaning the next equation has no integer solutions:  
  
# Math modes  
  
## Inline mode  
  
- `$` … `$`  
  
This is an inline math expression $\bbox[5px, border: 1px dashed gray]{\scriptstyle \sqrt{2} + \frac{1}{2}}$ within a sentence.   
  
## Display mode  
  
- **Centered** equation(s)¹: **Single** equation¹ `\[` …`\]`, Multiple equations `\begin{gather*}`  
- Alternating **right/left**-aligned columns²³⁴: **Separated** pairs¹ `\begin{align*}`, $n$ pairs of **touching** columns³ `\begin{alignat*}{2}`, Max. spaced-out to **line width**⁴ `\begin{flalign*}`  
- See source examples [Vertically align equations](Vertically%20align%20equations.md)  
  
$$  
    \framebox[10em]{x} \tag{1}  
$$  
$$  
\begin{align*}  
\framebox[1.5em]{x} &= \framebox[3em]{x} & \framebox[2em]{x} &= \framebox[2em]{x} \tag{2} \\  
\framebox[3em]{x} &= \framebox[1em]{x}   & \framebox[1em]{x}   &= \framebox[1em]{x}  
\end{align*}  
$$  
$$  
\begin{alignat*}{2}  
\framebox[1.5em]{x} &= \framebox[3em]{x} & \framebox[2em]{x} &= \framebox[2em]{x} \tag{3} \\  
\framebox[3em]{x} &= \framebox[1em]{x}   & \framebox[1em]{x}   &= \framebox[1em]{x}  
\end{alignat*}  
$$  
$$  
\begin{flalign*}  
\framebox[1.5em]{x} &= \framebox[3em]{x} & \framebox[1em]{x} &= \fbox{x} \;(4) \\  
\framebox[3em]{x} &= \framebox[1em]{x} & \framebox[2em]{x} &= \framebox[2em]{x}  
\end{flalign*}  
$$  
¹²³⁴ as seen in the $(n)^\text{th}$ math display above where $\fbox{x}$ represents math  
  
## Nested tabular mode  
  
- Surround with **delimiters** `\begin{pmatrix}`¹ - `\begin{cases}`²  
- **Attach at** the bottom/center/top `\begin{aligned}[b]`³  - `\begin{aligned}[t]`⁴  
  
$$  
\bbox[5px, border: 1px dashed gray]{\begin{pmatrix} \fbox{x} & \fbox{x} \\ \fbox{x} & \fbox{x} \\ \fbox{x} & \fbox{x} \end{pmatrix}}^{\mathrlap{(1)}} + \bbox[5px, border: 1px dashed gray]{\begin{cases} \fbox{x} & \text{for } \fbox{x} \\ \fbox{x} & \text{ow.} \end{cases}}^{\mathrlap{(2)}} \implies  \bbox[5px, border: 1px dashed gray]{\begin{aligned}[b] \framebox[1.2em]{x} & \fbox{x} \\ \fbox{x} &\framebox[1.2em]{x} \end{aligned}}^{(3)}  
$$  
$$  
\begin{align*}\MoveEqLeft{}  
\framebox[1em]{x} = \framebox[10em]{x} \\&  
 = \bbox[5px, border: 1px dashed gray]{\begin{aligned}[t] \framebox[15em]{x} \\ \framebox[7em]{x} \end{aligned}}^{(4)} \\&  
 = \framebox[13em]{x}  
\end{align*}  
$$  
¹²³⁴ as seen in the $(n)^\text{th}$ dashed box above where $\fbox{x}$ represents math  
  
# Symbols  
  
- Roots, fraction, matrix, operators, relations, accents, greek letter  
- [LaTeX Symbols - Lookup mathematical symbols, operations, relations, and arrows](./LaTeX%20Symbols%20-%20Lookup%20mathematical%20symbols,%20operations,%20relations,%20and%20arrows.md)  
- Limits, super/subscript  
- escevt for better vectors #34  
- Split delimiter  
- Math in description heading  
- Breaking (page/column break)  
- Fonts #23, styles #30  
  
![LaTeX Symbols - Lookup mathematical symbols, operations, relations, and arrows](./LaTeX%20Symbols%20-%20Lookup%20mathematical%20symbols,%20operations,%20relations,%20and%20arrows.md#^287de7)  
  
# Wrap long equation over multiple lines  
  
- Split long fractions over two lines¹, Indent subsequent lines²³, Wrap overlong equations³  
- See [Wrap long equation over multiple lines](Wrap%20long%20equation%20over%20multiple%20lines.md)  
  
$$  
\begin{align*}\MoveEqLeft{}  
\framebox[3em]{x} = \framebox[1em]{x} + \frac{\splitfrac{\scriptstyle\framebox[5em]{x}}{\scriptstyle\framebox[5em]{x}}}{\framebox[2em]{x}} \tag{1} \\&  
 = \framebox[7em]{x} \tag{2} \\&  
 = \,\!\begin{aligned}[t] \framebox[10em]{x} \\ \framebox[2em]{x} \end{aligned} \tag{3} \\&  
\end{align*}  
$$  
¹²³ as seen in the $(n)^\text{th}$ equation above where $\fbox{x}$ represents math  
  
# Comment equation operators  
  
- Comment: **Above**/below operators¹, In a **paragraph** between math displays², **Braces** under parts of an expression³, Comment a **case**³, Name matrix columns and rows  
- See [Comment equation operators](Comment%20equation%20operators.md)  
  
$$  
\framebox[1em]{x} \overset{\text{def}}{=} \framebox[2em]{x}\overset{\mathclap{\text{use (3)}}}{=} \framebox[2em]{x} \xRightarrow{+ \,\framebox[1em]{x}} \framebox[2em]{x} \tag{1}  
$$  
$$  
\begin{flalign*}  
\mathrlap{\text{Describe in a paragraph, what you are doing:}} && (2)  
\end{flalign*}  
$$  
$$  
\framebox[1em]{x} = \underbrace{ \framebox[2em]{x} }_{\text{for }\framebox[1em]{x}} \underbrace{ \framebox[3em]{x} }_{\text{for }\framebox[1em]{x}}  
= \begin{cases} \framebox[1em]{x},  & \text{for } \framebox[1em]{x} \\ \framebox[1em]{x},  & \text{because blah}  \\& \text{blab blub} \end{cases} \tag{3}  
$$  
¹²³ used to comment the $(n)^\text{th}$ equation above where $\fbox{x}$ represents math  
  
# Reference equations  
  
- roman style  
- ctagsplit and righttag [Mathematical Typesetting with Latex 0.34 2024-02-06, page 69](./attachments/Mathematical%20Typesetting%20with%20Latex%200.34%202024-02-06.pdf.md#page=69&selection=174,0,179,0)`  
  
$$  
\begin{flalign*}  
\text{From calculation \textcolor{blue}{(1)} on page \textcolor{blue}{1}, we can derive:} &&  
\end{flalign*}  
$$  
$$  
\begin{flalign*}  
&& \fbox{x} &= \fbox{x} & \mathllap{(1)} &&&& \fbox{x} &= \fbox{x} & \mathllap{\text{II}}  \\  
&& \fbox{x} &\overset{\mathclap{\text{use \textcolor{blue}{(2)}}}}{=} \fbox{x} & \mathllap{(\text{I})} && \mathrlap{(3.1)} && \fbox{x} &= \fbox{x} &  \\  
&& \fbox{x} &= \fbox{x} & \mathllap{(2)} &&&& \fbox{x} &= \fbox{x} & \mathllap{[\text{lin.}]}  \\  
\end{flalign*}  
$$  
  
# Create commutative diagrams  
  
- [[Amscd graphs]]  
  
$$  
\begin{CD}  
A @>a>> B\\  
@VVbV @VVcV\\  
C @>d>> D  
\end{CD}  
$$  
  
# Layout multiple equations  
  
- Scale, Placement¹²: Spread math over multiple display columns¹, Scale delimiters manually/automatically, Scale repeating operators, Place limits surrounding/next to it `\limit` - `\nolimit`, Scale equations `exscale`  
- Spacing³: Between lines `\\[1ex]` - `\jot`, inside matrix, number 1000 sep, Index (icomma german), smash for inline math, `mathrlap`, Matrix spacing #30, styles, Fix delimiter space  
- Formatting⁴: color, boxed, boldmath, titlemath, everydisplay, everymath, underline, long text -> parbox, strikethrough  
- See [[Layout multiple equations]]  
  
$$  
\begin{gather*}  
\fbox{x} = \fbox{x} \quad\fbox{x} = \fbox{x}\quad\fbox{x} = \fbox{x}\mathrlap{\quad\cdots} \tag{1} \\  
\Big(\big(()\big)\Big),\; {\huge\sum_{j = 1}} \sum_{i = 1}^{\infty} i,\; \int_0^1 \int\limits_0^1,\;  \sideset{_{\text{bl}}^{\text{tl}}}{_{\text{br}}^{\text{tr}}}\sum_{B}^{T} \tag{2} \\  
\begin{pmatrix} 0 1 \\[-1ex] 10 \\ 01 \end{pmatrix},\; \tfrac{3}{11} \,^{3}\!/\!_{11} \frac{3}{11}\,a,\; 12\,345 \tag{3} \\   
\textcolor{magenta}{a + b^2},\; \cancel{a + b^2},\; \underline{a + b^2},\; \boxed{a + b^2} \tag{4}  
\end{gather*}  
$$  
¹²³⁴ used to format the $(n)^\text{th}$ equation above where $\fbox{x}$ represents math  
  
# Things to avoid, deprecated, bad syntax  
  
- no `\\` at end of align  
- put `[]` after suqenvironments  
- [[How not to typeset math in latex]]  
Deprecated  
- eqnarray  
- font syntax  
- stackrel  
- xalignat, xxalignat  
- new operator [[Mathematical Typesetting with Latex 0.34 2024-02-06.pdf#page=41&selection=259,7,259,18|Mathematical Typesetting with Latex 0.34 2024-02-06, page 41]]  
  
- In markdown put display math delimiters `$$` on a separate line  
- Don't leave spaces in front of caret to prevent block reference detection (write `a^2` instead of `a ^2`)  
