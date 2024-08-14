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
\gets \boxed{xxxxxx} \to \tag{1}  
$$  
$$  
\begin{align*}  
\gets \boxed{\begin{array}{r|l} xx \!\!&\!\! = xxx \\ \hline x \!\!&\!\! =  x \end{array}} & \to & \gets   
\boxed{\begin{array}{r|l} xxxx \!\!&\!\! =  x \\ \hline xx \!\!&\!\! = xxx \end{array}} \to \tag{2}  
\end{align*}  
$$  
$$  
\begin{alignat*}{2}  
\gets \boxed{\begin{array}{r:l} xx \!\!&\!\! =  xxx \\ \hdashline x \!\!&\!\! = x \end{array}} & &   
\boxed{\begin{array}{r:l} xxxx \!\!&\!\! =  x \\ \hdashline xx \!\!&\!\! = xxx \end{array}} \to \tag{3}  
\end{alignat*}  
$$  
$$  
\begin{flalign*}  
\boxed{\begin{array}{r:l} xx \!\!&\!\! =  xxx \\ \hdashline x \!\!&\!\! = x \end{array}} & \to & \gets   
\boxed{\begin{array}{r:l} xxxx \!\!&\!\! =  x \\ \hdashline xx \!\!&\!\! = xxx \end{array}} \\  
&& (4)  
\end{flalign*}  
$$  
¹²³⁴ as seen in the $(n)^\text{th}$ math display above where $x$ represents math  
  
## Nested tabular mode  
  
- Surround with **delimiters** `\begin{pmatrix}`¹ - `\begin{cases}`²  
- **Attach at** the bottom/center/top `\begin{aligned}[b]`³  - `\begin{aligned}[t]`⁴  
  
$$  
\bbox[4px, border: 1px dashed gray]{\begin{pmatrix} \begin{array}{c|c} xx \!\!&\!\! x \\ \hline x \!\!&\!\! xx \\ \hdashline x \!\!&\!\! x \end{array} \end{pmatrix}}_{\mathrlap{(1)}}  
+ \bbox[4px, border: 1px dashed gray]{\begin{cases} \begin{array}{l|l} xxx \!\!&\!\! \text{if } x \\ \hline x \!\!&\!\! \text{otherwise}   \end{array} \end{cases}}_{\mathrlap{(2)}}  
+ \bbox[4px, border: 1px dashed gray]{\begin{aligned}[b] xxx\rule[-.3em]{0.4pt}{1em} & x \\ \hline x \rule[-.3em]{0.4pt}{1em}& xx  \end{aligned}}_{(3)}   
$$  
$$  
\begin{align*}\MoveEqLeft{}  
xx = xxxxxxxxxxx \\&  
 = \!\bbox[4px, border: 1px dashed gray]{\begin{aligned}[t]  
\!xxxxxxxxxxxxx & \\ \hdashline xxxxxxx&  
\end{aligned}}_{(4)} \\&  
 = xxxxxxx  
\end{align*}  
$$  
¹²³⁴ as seen in the $(n)^\text{th}$ dashed box above where $x$ represents math  
  
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
\begin{align*}  
&x = xx +  \frac{\bbox[4px, border: 1px dashed gray]{\splitfrac{xxxx}{xxxx}}_{\mathrlap{(1)}}}{x} \\  
&\begin{array}{r:l} \qquad \!\!&\!\! = \!\bbox[4px, border: 1px dashed gray]{\begin{aligned}[t] \begin{array}{r} \!xxxxxxxxxxx \end{array} \\ \hdashline \begin{array}{r} xxxx \end{array} \end{aligned}}_{(3)} \\ &\!\! = xxx \end{array} \\&  
\qquad^{\mathclap{(2)}}  
\end{align*}   
$$  
  
$$  
\begin{align*}\MoveEqLeft{}  
\framebox[3em]{x} = \framebox[1em]{x} + \frac{\splitfrac{\scriptstyle\framebox[5em]{x}}{\scriptstyle\framebox[5em]{x}}}{\framebox[2em]{x}} \tag{1} \\&  
 = \framebox[7em]{x} \tag{2} \\&  
 = \,\!\begin{aligned}[t] \framebox[10em]{x} \\ \framebox[2em]{x} \end{aligned} \tag{3} \\&  
\end{align*}  
$$  
¹²³ as seen in the $(n)^\text{th}$ equation above where $x$ represents math  
  
# Comment equation operators  
  
- Comment: **Above**/below operators¹, In a **paragraph** between math displays², **Braces** under parts of an expression³, Comment a **case**³, Name matrix columns and rows  
- See [Comment equation operators](Comment%20equation%20operators.md)  
  
$$  
x \overset{\text{def}}{=} xxxx\overset{\mathclap{\text{use (3)}}}{=} xxxx \xRightarrow{+ x} xxxx \tag{1}  
$$  
$\text{Write a paragraph between equations:}$  
$$  
\tag{2}  
$$  
$$  
x = \underbrace{ xxxxx }_{\text{for }x} \underbrace{ xxxx }_{ \mathclap{\substack{\text{for }x\\ \text{and relatives}} }  }  
= \begin{cases} xx,  & \text{for } x \\ x,  & \text{because blah}  \\& \text{blab blub} \end{cases} \tag{3}  
$$  
¹²³ used to comment the $(n)^\text{th}$ equation above where $x$ represents math  
  
# Reference equations  
  
- roman style  
- ctagsplit and righttag [Mathematical Typesetting with Latex 0.34 2024-02-06, page 69](./attachments/Mathematical%20Typesetting%20with%20Latex%200.34%202024-02-06.pdf.md#page=69&selection=174,0,179,0)`  
  
$\text{From calculation \textcolor{blue}{(1)} on page \textcolor{blue}{1}, we can derive:}$  
$$  
\begin{aligned}  
\fbox{x} &= \fbox{x} & (1) \\  
\fbox{x} &\overset{\mathclap{\text{use \textcolor{blue}{(2)}}}}{=} \fbox{x} & (\text{I}) \\  
\fbox{x} &= \fbox{x} & (2) \\  
\end{aligned}  
\qquad  
\begin{aligned}  
&&\fbox{x} &= \fbox{x} & \text{II}  \\  
(3.1) && \fbox{x} &= \fbox{x} &  \\  
&&\fbox{x} &= \fbox{x} & [\text{lin.}]  \\  
\end{aligned}  
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
\hphantom{\cdots\quad} x = x \quad x = x \quad x = x \quad\cdots \tag{1} \\  
\Big(\big(()\big)\Big),\; {\huge\sum_{j = 1}} \sum_{i = 1}^{\infty} i,\; \int_0^1 \int\limits_0^1,\;  \sideset{_{\text{bl}}^{\text{tl}}}{_{\text{br}}^{\text{tr}}}\sum_{B}^{T} \tag{2} \\  
\begin{pmatrix} 0 1 \\[-1ex] 10 \\ 01 \end{pmatrix},\; \tfrac{3}{11} \,^{3}\!/\!_{11} \frac{3}{11}\,a,\; 12\,345 \tag{3} \\   
\textcolor{magenta}{a + b^2},\; \cancel{a + b^2},\; \underline{a + b^2},\; \boxed{a + b^2} \tag{4}  
\end{gather*}  
$$  
¹²³⁴ used to format the $(n)^\text{th}$ equation above where $x$ represents math  
  
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
