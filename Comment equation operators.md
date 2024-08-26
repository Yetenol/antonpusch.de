# Describe an operator

$$
f(x) \overset{\text{def}}{=} x^2 + c
$$


```latex
\[
f(x) 
\overset{\text{def}}{=} x^2 + c
\overset{\text{nutze \eqref{eq:innerfunction}}}{=} f(a_0 x^4)
\]
\[
g(x) = a_0 x^4 
\]
```

# Reference a secondary calculation

$$
\begin{gather*}
f(g(x)) \overset{\text{nutze (1)}}{=} f(a_0 x^4) \\
g(x) = a_0 x^4 \tag{1} 
\end{gather*}
$$

```latex
f(g(x)) \overset{\text{nutze \eqref{eq:inner}}}{=} f(a_0 x^4)
g(x) = a_0 x^4 \vphantom{eq:inner}\tag{*} 
```

```latex
f(g(x)) \overset{\text{nutze \eqref{eq:inner}}}{=} f(a_0 x^4)
```
```latex
g(x) = a_0 x^4 \label{eq:innerfunction}\label{eq:inner}\tag{\theequation}\refstepcounter{equation}
```

# Comment stretchable arrows

$$
\begin{align*}
\MoveEqLeft{} 0,99 < 1 - \mathbb{P}(A)^k 
= 1 - p^k 
\xRightarrow{+p^k - 0,99} p^k < 0,01
\xRightarrow{\log_p()} k > \log_p(0,01) \\&
\xRightarrow{p=0,11} k > \log_{0,11}(0,01) \approx 2,086 
\xRightarrow{k \in \mathbb{N}^+} k \ge 3
\end{align*} 
$$


Don't comment after line

- works on a blackboard, looks bad on paper

$$
\begin{align*}
0,99 &< 1 - \mathbb{P}(A)^k \\
0,99 &< 1 - p^k &&|\ +p^k - 0,99 \\
p^k &< 0,01 &&|\ \log_p() \\
k &> \log_p(0,01) &&|\ p=0,11 \\
k &> \log_{0,11}(0,01) \approx 2,086 &&|\ k \in \mathbb{N}^+ \\
\Rightarrow k &\ge 3
\end{align*} 
$$

# Use cases

$$
\begin{align*}\MoveEqLeft{}
f(x) \overset{\text{def}}{=} x^2 + c 
\overset{\text{(1)} }{=} h(x) + c \\&
\overunderset{\text{symmetrisch}}{\text{auf [0,1]}}{=} \int_{\infty }^{-\infty }  \begin{cases} e^{x - z} & \text{für } 0 \le x \le 1 \land z \ge x \\ 0 & \text{sonst}  \end{cases} \, dx \\&
 = \int_0^z e^{x - z} \, dx \ll t
\end{align*}
$$


Don't write long overbraces


$$
f(x) \overset{\text{def}}{=} x^2 + c 
\overset{\text{(1)} }{=} h(x) + c
\overunderset{\text{symmetrisch}}{\text{auf [0,1]}}{=} \underbrace{\int_{-\infty}^0 0\, dx}_\text{für $x < 0$} + \overbrace{\int_0^z e^{x-z}\, dx}^{\mathclap{\text{für $0 \le x \le 1$ und $z \ge x$}}} + 
\underbrace{\int_z^1 0\, dx}_{\mathclap{\text{für $0 \le x \le 1$ und $z < x$}}} + \overbrace{\int_1^\infty 0\, dx}^{\mathclap{\text{$x > 1$}}}
$$

# Comment matrix columns

![minimal 34.svg](./content/attachments/minimal%2034.svg) 

```latex
\documentclass{article}
\usepackage{amsmath,amssymb,mathtools,aligned-overset,array}
\begin{document}
\def\rb#1{\rotatebox{90}{$\xleftarrow{#1}$}}
\begin{tabular}{c}
$\begin{matrix}
\rb{text1}&\rb{text1}&\rb{text1}&\rb{text1}\\
\end{matrix}$\\
$\begin{bmatrix}
X_x & Y_x & Z_x & T_x \\
X_y & Y_y & Z_y & T_y \\
X_z & Y_z & Z_z & T_z \\
0 & 0 & 0 & 1
\end{bmatrix}$
\end{tabular}
\end{document}
```
- https://mirror.physik.tu-berlin.de/pub/CTAN/obsolete/info/math/voss/mathmode/Mathmode.pdf#page=110

# Overlapping braces

![minimal 35.svg](./content/attachments/minimal%2035.svg) 

```latex
\documentclass{article}
\usepackage{amsmath,amssymb,mathtools,aligned-overset,array,xcolor}
\begin{document}
\begin{align}\label{eq:pqFormel}
y &= 2x^2 -3x +5\nonumber\\
& \hphantom{= \ 2\left(x^2-\frac{3}{2}\,x\right. }%
\textcolor{blue}{%
\overbrace{\hphantom{+\left(\frac{3}{4}\right)^2- %
\left(\frac{3}{4}\right)^2}}^{=0}}\nonumber\\[-11pt]
&= 2\left(\textcolor{red}{%
\underbrace{%
x^2-\frac{3}{2}\,x + \left(\frac{3}{4}\right)^2}%
}%
\underbrace{%
- \left(\frac{3}{4}\right)^2 + \frac{5}{2}}%
\right)\\
&= 2\left(\qquad\textcolor{red}{\left(x-\frac{3}{4}\right)^2}
\qquad + \ \frac{31}{16}\qquad\right)\nonumber\\
y\textcolor{blue}{-\frac{31}{8}}
&= 2\left(x\textcolor{cyan}{-\frac{3}{4}}\right)^2\nonumber
\end{align}
\end{document}
```
- https://mirror.physik.tu-berlin.de/pub/CTAN/obsolete/info/math/voss/mathmode/Mathmode.pdf#page=117

# Vertical and horizontal aligned braces

![minimal 36.svg](./content/attachments/minimal%2036.svg) 

```latex
\documentclass{article}
\pagestyle{empty}
\usepackage{amsmath,amssymb,amsfonts,mathtools,aligned-overset,array,xcolor}
\begin{document}
\def\num#1{\hphantom{#1}}
\def\vsp{\vphantom{\rangle_1}}
\begin{equation*}
\frac{300}{5069}%
\underbrace{\longmapsto\vphantom{\frac{1}{1}}}_{%
\mathclap{\substack{%
\Delta a=271\num9\vsp \\[2pt]
\Delta b=4579\vsp\\[2pt]
\text{$1$ iteration}%
}}} \frac{29}{490}%
\underbrace{\longmapsto \frac{19}{321}\longmapsto}_{%
\mathclap{\substack{%
\Delta a=10\num{9}=\langle271\rangle_{29}\num{20}\\[2pt]
\Delta b=169=\langle4579\rangle_{490}\\[2pt]
\text{$2$ iterations}
}}} \frac{9}{152}
\underbrace{\longmapsto \frac{8}{135}\longmapsto\dots\longmapsto}_{%
\substack{%
\Delta a=1\num{7}=\langle10\rangle_{9}\num{119}\\[2pt]
\Delta b=17=\langle169\rangle_{152}\\[2pt]
\text{$8$ iterations}
}} \frac{1}{16}
\underbrace{\longmapsto\dots\longmapsto\vphantom{\frac{8}{135}}}_{%
\substack{%
\Delta a=0=\langle1\rangle_{1}\num{76} \\[2pt]
\Delta b=1=\langle17\rangle_{16} \\[2pt]
\text{$8$ iterations}
}} \frac{1}{1}
\end{equation*}
\end{document}
```
- https://mirror.physik.tu-berlin.de/pub/CTAN/obsolete/info/math/voss/mathmode/Mathmode.pdf#page=118

# More

$$
    \begin{gathered}
        \text{Annahmen:} \\
        (A1): n \equiv 3 \pmod{19} \\
        (A2): n \equiv 1 \pmod{20} \\
        (A3): n \equiv 2 \pmod{21} \\
        (A4): n \equiv 0 \pmod{23} \\
        (A5): n \equiv 1 \pmod{22}
    \end{gathered} 
    \qquad
    \begin{gathered}
        \text{Zu Zeigen:} \\
        (Z1.1): n \equiv 3 \pmod{19} \\
        (Z2.1): n \equiv 1 \pmod{20} \\
        (Z3.1): n \equiv 2 \pmod{21} \\
        (Z4.1): n \equiv 0 \pmod{23} \\
        (Z5.1): n \equiv 1 \pmod{11}
    \end{gathered} 
$$

$$
\begin{align*}\MoveEqLeft{}
\operatorname{L} \big( (a + b)^{*}  \big) 
\overset{ \text{FS 1.2.8 *} }{=} 
\operatorname{L} ( a + b )^{*}
\overset{ \text{FS 1.2.8 +} }{=} 
\big( \operatorname{L} ( a ) \cup \operatorname{L} ( b ) \big)^{*}  
\overset{ \text{FS 1.2.8 } a, b \, \in\,  \Sigma}{=} \big( \{ a \} \cup \{ b \}   \big)^{*}  
\overset{ \text{Def. } \cup}{=} 
\{ a, b \}^{*} \\&
\overset{ \text{Def. } \in}{=} 
\big\{ w \in \{ a, b \}^{*} \big\}
\overset{ \text{Def. } \left| \cdot \right|_{\cdot}  }{=} 
\big\{ w \in \{ a, b, c \}^{*} \mid \left| w \right|_{c} = 0 \big\} 
\overset{ \text{Def. } \Sigma }{=} 
\big\{ w \in \Sigma^{*} \mid \left| w \right|_{c} = 0  \big\}
\end{align*}
$$
$$
X = \sum_{1\le i\le j\le n} X_{ij} \qquad
X = \sum_{\mathclap{1\le i\le j\le n}} X_{ij}
$$