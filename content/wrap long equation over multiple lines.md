---
dg-publish: true
---

# Shrink long fractions

```latex
\documentclass{article}\pagestyle{empty}
\usepackage{mathtools,amssymb,amsfonts}
\begin{document}
\[
a = \frac{ \splitfrac{xxxxxxx}{+ xxxx} }{(1)}
+ \frac{ \splitdfrac{xxxxxxx}{+ xxxx} }{(2)}
+ \frac{ \begin{aligned} xxxxxxx \quad\\[-1ex] + xxxx \end{aligned} }{(3)} 
+ \frac{ \begin{split} xxxxxxx \quad\\[-1ex] + xxxx \end{split} }{(4)} 
+ \frac{ \substack{xxxxxxx \\ +xxxx} }{(5)}
\]
\end{document}
```

![minimal 44.svg](./attachments/minimal%2044.svg)

- use (1) in Obsidian
```
a = \frac{ \splitfrac{xxxxxxx}{+ xxxx} }{(1)}
```
- use (2) in Obsidian
```
a = \frac{ \splitdfrac{xxxxxxx}{+ xxxx} }{(2)}
```
- use (3) in Obsidian, VS Code, Quartz !inconsistent `\begin{aligned}[b]`
```
a = \frac{ \begin{aligned} xxxxxxx \quad\\[-1ex] + xxxx \end{aligned} }{(3)}
```
- use (4) in Obsidian, VS Code, Quartz, Overleaf !warning to use aligned instead
```
a = + \frac{ \begin{split} xxxxxxx \quad\\[-1ex] + xxxx \end{split} }{(4)}
```
- use (5) in Obsidian, VS Code, Quartz, Overleaf
```
a = \frac{ \substack{xxxxxxx \\ +xxxx} }{(5)}
```

# Indent subsequent lines

```latex
\documentclass{article}\pagestyle{empty}
\usepackage{mathtools,amssymb,amsfonts}
\begin{document}
\begin{align*} \qquad&\hspace{-2em}
    R_1 =  \frac{\rho_i \,}{a_i \,\pi}\int_{0}^{h}\left(\frac{r_2-r_1}{h}y+r_1\right)^{-2}dy 
    = \frac{\rho_i \,}{a_i \,\pi}\left[-\frac{1}{\frac{r_2-r_1}{h}\left(\frac{r_2-r_1}{h}y+r_1\right)}\right]_0^h \\&
    = \frac{\rho_i \,}{a_i \,\pi}\left(\frac{h}{r_1\left(r_2-r_1\right)}-\frac{h}{r_2\left(r_2-r_1\right)}\right) +  \frac{\rho_i \,}{a_i \,\pi}\cdot\frac{h}{r_2-r_1}\left(\frac{r_2}{r_1r_2}-\frac{r_1}{r_1\ r_2}\right)
\end{align*}
\end{document}
```

$$
\begin{align*} \qquad&\hspace{-2em}
R_1 =  \frac{\rho_i \,}{a_i \,\pi}\int_{0}^{h}\left(\frac{r_2-r_1}{h}y+r_1\right)^{-2}dy 
= \frac{\rho_i \,}{a_i \,\pi}\left[-\frac{1}{\frac{r_2-r_1}{h}\left(\frac{r_2-r_1}{h}y+r_1\right)}\right]_0^h \\&
= \frac{\rho_i \,}{a_i \,\pi}\left(\frac{h}{r_1\left(r_2-r_1\right)}-\frac{h}{r_2\left(r_2-r_1\right)}\right) +  \frac{\rho_i \,}{a_i \,\pi}\cdot\frac{h}{r_2-r_1}\left(\frac{r_2}{r_1r_2}-\frac{r_1}{r_1\ r_2}\right)
\end{align*}
$$

- Move equation left
```latex
\qquad&\hspace{-2em}
\MoveEqLeft{} % Mathjax only
```

- Vertically aligned dots (Mathjax only)
```latex
\vdotswithin{=} \\&
```

$$
\begin{align*}\MoveEqLeft{} 
a + b + c + d \\& 
= a + b + c + d \\& 
= 0 + 1 + 2 + 3 \\&
\vdotswithin{=} \\&
= \text{result} 
\end{align*}
$$

# Set operators as column divider


```latex
\documentclass{article}
\pagestyle{empty}
\usepackage{amsmath,amssymb,mathtools,aligned-overset,array}
\begin{document}
\[
\begin{array}{l@{\:=\:}*{5}{l@{\:+\:}}l}
y_1 & a_{11}x_1 & a_{12}x_2 & a_{13}x_3 & \dots & a_{1(n-1)}x_{n-1} & a_{1n}x_n \\
y_2 & a_{21}x_1 & a_{22}x_2 & a_{23}x_3 & \dots & a_{2(n-1)}x_{n-1} & a_{2n}x_n \\
\ \vdots &\ \vdots &\ \vdots &\ \vdots &\ \vdots &\ \vdots &\ \vdots\\
y_{n-1} & a_{(n-1)1}x_1 & a_{(n-1)2}x_2 & a_{(n-1)3}x_3 & \dots & a_{(n-1)(n-1)}x_{n-1} &
a_{(n-1)n}x_n\\
y_n & a_{n1}x_1 & a_{n2}x_2 & a_{n3}x_3 & \dots & a_{(n)(n-1)}x_{n-1} & a_{nn}x_n
\end{array}
\]
\end{document}
```
- [mirror.physik.tu-berlin.de/pub/CTAN/obsolete/info/math/voss/mathmode/Mathmode.pdf#page=110](https://mirror.physik.tu-berlin.de/pub/CTAN/obsolete/info/math/voss/mathmode/Mathmode.pdf#page=110)

![minimal 33.svg](./attachments/minimal%2033.svg)

# More


$$
a=\frac{
\splitfrac{xy + xy + xy + xy + xy}
{+ xy + xy + xy + xy}
}
{z}
$$
$$
\begin{align*}\MoveEqLeft{}
\fbox{$f(x + y)$} = \framebox[8cm]{first expression} \tag{1} \\&
 = \begin{aligned}[t] \framebox[10cm]{overlong second} \\ \framebox[4cm]{expression} \end{aligned} \tag{2} \\&
 = \framebox[7cm]{third expression} \tag{3}
\end{align*}
$$

$$
\begin{align*}\MoveEqLeft{}
A = \framebox[8cm]{first expression} \tag{1} \\&
= \framebox[10cm]{second} \tag{2}  \\&\qquad
\framebox[4cm]{expression} \\&
= \framebox[7cm]{third expression} \tag{3}
\end{align*}
$$



$$
\begin{align*}
R_1 &= \frac{\rho_i \,}{a_i \,\pi}\int_{0}^{h}\left(\frac{r_2-r_1}{h}y+r_1\right)^{-2}dy 
= \frac{\rho_i \,}{a_i \,\pi}\left[-\frac{1}{\frac{r_2-r_1}{h}\left(\frac{r_2-r_1}{h}y+r_1\right)}\right]_0^h \\&
\overset{\text{Summanden in der Klammer vertauschen}}{=}  \frac{\rho_i \,}{a_i \,\pi}\left(-\frac{1}{\frac{r_2-r_1}{h}\left(r_2-r_1+r_1\right)}+\frac{1}{\frac{r_2-r_1}{h}r_1}\right) \\&
\overset{\text{nutze $(1)$}}{=}  \frac{\rho_i \,}{a_i \,\pi}\left(\frac{h}{r_1\left(r_2-r_1\right)}-\frac{h}{r_2\left(r_2-r_1\right)}\right)
= \frac{\rho_i \,}{a_i \,\pi}\cdot\frac{h}{r_2-r_1}\left(\frac{r_2}{r_1r_2}-\frac{r_1}{r_1\ r_2}\right) \\&
= a+b+c+d+e+f+g+h+i 
= \frac{\rho_i \, h}{d_i \,\pi\left(r_2-r_1\right)}\,\frac{r_2-r_1}{r_1r_2}=\frac{\rho_i \,}{a_i \,\pi}\,\frac{h}{r_1r_2} 
\end{align*}
$$

$$
\begin{align*}
\vec{H}(z_p) &
\overset{\text{\eqref{eq:wegintegral}}}{=}  \frac{I_1}{4\pi} \underbrace{ \oint \frac{d\vec{s}\times\vec{r}}{r^3} }_{\text{läuft 1 Umdrehung auf $\phi$}} \\&
= \frac{I_1}{4\pi} \int{\frac{\vec{e}_\phi \times\vec{r}}{r^3}a\,d\phi}
= \frac{I_1}{4\pi} \int_0^{2\pi}{\frac{\vec{e}_\phi \times\vec{r}}{r^3}a\,d\phi} \\&
\overset{\text{\eqref{eq:abstandNorm}}}{=}  \frac{I_1 a}{4\pi} \int_0^{2\pi}{\frac{\vec{e}_\phi \times\vec{r}}{r^3}d\phi} \\&
= \frac{I_1 a}{4\pi} \int_0^{2\pi}{\frac{\vec{e}_\phi \times\vec{r}}{\underbrace{ \left(\sqrt{ a^2+ {(z_p-h)}^2 }\right)^3 }_{\text{Nenner unabhängig von $\phi$}}}d\phi} \\&
= \frac{I_1 a}{4\pi} \int_0^{2\pi}{\frac{\vec{e}_\phi \times\vec{r}}{\left( a^2+ {(z_p-h)}^2 \right) ^\frac{3}{2}}d\phi} \\&
\overset{\text{\eqref{eq:kreuzprodukt}}}{=}  \frac{I_1 a}{4\pi \left( a^2+ {(z_p-h)}^2 \right) ^\frac{3}{2}} \int_0^{2\pi}{\vec{e}_\phi \times\vec{r} \,  d\phi} \\&
= \frac{I_1 a}{4\pi \left( a^2+ {(z_p-h)}^2 \right) ^\frac{3}{2}} \int_0^{2\pi}{\begin{pmatrix} -\cos{\phi}\, (z_p-h) \\ -\sin{\phi}\, (z_p-h) \\ a \end{pmatrix} d\phi} \\&
= \frac{I_1 a}{4\pi \left( a^2+ {(z_p-h)}^2 \right) ^\frac{3}{2}} \begin{bmatrix} \cos{\phi}\, (z_p-h) \\ \sin{\phi}\, (z_p-h) \\ a \phi \end{bmatrix} _0^{2\pi} \\&
= \frac{I_1 a}{4\pi \left( a^2+ {(z_p-h)}^2 \right) ^\frac{3}{2}} \cdot \begin{pmatrix}0 &-& 0 \\ 0 &-& 0 \\ 2\pi a &-& 0 \end{pmatrix} \\&
= \frac{I_1 a}{4\pi \left( a^2+ {(z_p-h)}^2 \right) ^\frac{3}{2}}\cdot 2\pi a\,\vec{e}_z  \\&
= \frac{I_1 a^2}{2 \left( a^2+ {(z_p-h)}^2 \right) ^\frac{3}{2}}\,\vec{e}_z 
\end{align*}
$$

$$
\framebox[1em]{x} = \framebox[3em]{x} =  \framebox[4em]{x} =  \ldots
\quad\longrightarrow\quad \begin{aligned}\MoveEqLeft{}
\framebox[1em]{x} = \framebox[3em]{x} \\&
=  \framebox[4em]{x} \\& 
\;\;\vdots
\end{aligned}
$$

$$
\begin{align*}\MoveEqLeft{}
\framebox[3em]{x} = \framebox[16em]{x} \\&
 = \begin{aligned}[t] \framebox[20em]{$\mathrm{x_1}$} \\ \framebox[7em]{$\mathrm{x_2}$} \end{aligned}  \\&
 = \framebox[15em]{x}
\end{align*}
$$
$$
\framebox[1em]{x} + \frac{\framebox[10em]{x}}{\framebox[2em]{x}}  \quad\longrightarrow\quad    \framebox[1em]{x} +  
$$


$$
\begin{align*}\MoveEqLeft{}
\mathbb{P}(X+Y=k) 
= \sum_{x \in X(\Omega)} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}
$$
