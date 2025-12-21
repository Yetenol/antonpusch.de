---
date: "2025-07-17T08:13:58.811+02:00"
title: "Stoch HA8 zum 2023-06-16"
description: "-"
dg-publish: true
---

!Hausaufgabengruppe in Stochastik für Informatik

# Aufgabe 1)

## a)

$$
f:\mathbb{R} \to [0,\infty) \qquad f(x) = \frac{C}{1+x^2} 
$$
Wir wählen $C=\dfrac{1}{\pi}$.

$$
f(x) = \frac{1}{\underbrace{\pi}_\text{$>0$}} \cdot \frac{1}{\underbrace{1+x^2}_\text{$>0$}} 
$$
Also ist $f(x) \ge 0 \text{ für alle } t \in \mathbb{R}$.

$$
\begin{align*}\MoveEqLeft{}
\int_{-\infty}^\infty f(x)\, dx
= \int_{-\infty}^\infty \frac{1}{\pi} \cdot \frac{1}{1+x^2}\, dx \overset{\text{Konstante}}{=} \frac{1}{\pi} \int_{-\infty}^\infty \frac{1}{1+x^2}\, dx \\&
\overunderset{\text{Symmetrisch um 0}}{\text{auf $(-\infty, \infty)$}}{=} \frac{2}{\pi} \int_0^\infty \frac{1}{1+x^2}\, dx \\&
\overunderset{\text{Bekannte}}{\text{Stammfunktion}}{=} \frac{2}{\pi} \lim_{a \to \infty} \Big( \arctan(x) \big|_0^a  \Big) \\&
= \frac{2}{\pi} \cdot\left( \lim_{a \to \infty}  \arctan(a) -0 \right) 
= \frac{2}{\pi} \cdot \frac{\pi}{2} = 1 
\end{align*}
$$
Also ist $\int_{-\infty}^\infty f(x)\, dx =1$.

Es gilt $f(x) \ge 0 \text{ für alle } t \in \mathbb{R}$ und $\int_{-\infty}^\infty f(x)\, dx =1$. Also ist $f$ eine Dichte.

## b)

$$
F(x) = \begin{cases} 1 - \dfrac{1}{x^3} & x \ge 1 \\ 0 & x < 1  \end{cases} 
$$

$$
\begin{align*}\MoveEqLeft{}
\mathbb{P}(X \in [2,4]) 
= \mathbb{P}(X \le 4) - \mathbb{P}(X \le 2) + \underbrace{\mathbb{P}(X=2)}_\text{$=0$} 
= F(4) - F(2) \\&
= \left( 1 - \frac{1}{4^3} \right) - \left( 1 - \frac{1}{2^3} \right) = \frac{63}{64} - \frac{7}{8} 
= \frac{7}{64} \approx 0,101
\end{align*}
$$

Da $a = 3 > 1$ gilt, folgt für die Pareto-verteilte Zufallsvariable $X$:
$$
\begin{align*}
\mathbb{E}\left[ X \right] &
= \int_1^\infty t \cdot \frac{3 \cdot 1^3}{t^4}\, dt 
= 3 \int_1^\infty t^{-3}\, dt \\&
= 3 \cdot \lim_{a \to \infty} \left( \left. - \frac{1}{2t^2} \right|_1^a \right) 
= 3 \cdot \left( 0 + \frac{1}{2} \right) = \frac{3}{2} = 1,5 
\end{align*}
$$

# Aufgabe 2)

Die stetig gleichverteilte Zufallsvariable $X$ mit $\Omega = [0,1]$ hat die Dichte:
$$
f_X(x) = \begin{cases} 1 & 0 \le x \le 1 \\ 0 & \text{sonst.}  \end{cases} 
$$
Die exponentialverteilte Zufallsvariable $Y$ mit $\lambda = 1$ hat die Dichte:
$$
f_Y(y) = \begin{cases} 0 & y < 0 \\ e^{-y} & y \ge 0 \end{cases} 
$$
Da $X$ und $Y$ unabhängig sind, gilt für ihre gemeinsame Dichte:
$$
f_{(X,Y)}(x,y) = f_X(x) \cdot f_Y(y) = \begin{cases} e^{-y} & 0 \le x \le 1 \land y \ge 0 \\ 0 & \text{sonst.}  \end{cases}  
$$
Da $X$ und $Y$ unabhängig sind, ist die Wahrscheinlichkeitsdichte der Summe für alle $z \in \mathbb{R}$ gegeben durch das Faltungsintegral:
$$
\begin{align*}
f_Z(z)  &
= \int_{-\infty}^{\infty} f_X(x) \cdot f_Y(z-x) \, dx \\&
= \int_{-\infty}^{\infty} f_{(X,Y)}(x,z-x)\, dx  \\&
= \int_{-\infty}^{\infty} \begin{cases} e^{x-z} & 0 \le x \le 1 \land z \ge x \\ 0 & \text{sonst.}  \end{cases}\, dx
\end{align*}
$$
Fall 1: $z < 0$
$$
\begin{align*}\MoveEqLeft{}
\int_{-\infty}^{\infty} \begin{cases} e^{x-z} & 0 \le x \le 1 \land z \ge x \\ 0 & \text{sonst.}  \end{cases}\, dx \\&
= \underbrace{\int_{-\infty}^0 0\, dx}_\text{$x < 0$} +
\underbrace{\int_0^1 0\, dx}_\text{$0 \le x \le 1,\ z < x$} + \underbrace{\int_1^\infty 0\, dx}_\text{$x > 1$} = 0
\end{align*}
$$

Fall 2: $0 \le z \le 1$
$$
\begin{align*}\MoveEqLeft{}
\int_{-\infty}^{\infty} \begin{cases} e^{x-z} & 0 \le x \le 1 \land z \ge x \\ 0 & \text{sonst.}  \end{cases}\, dx \\&
= \underbrace{\int_{-\infty}^0 0\, dx}_\text{$x < 0$} + \overbrace{\int_0^z e^{x-z}\, dx}^{\mathclap{\text{$0 \le x \le 1,\ z \ge x$}}} + 
\underbrace{\int_z^1 0\, dx}_{\mathclap{\text{$0 \le x \le 1,\ z < x$}}} + \underbrace{\int_1^\infty 0\, dx}_\text{$x > 1$} \\&
= \int_0^z e^{x-z}\, dx 
= e^{-z} \int_0^z e^x\, dx \\&
= e^{-z} \cdot \Big( e^x \big|_0^z \Big) = e^{-z} (e^z-1) = 1 -e^{-z}
\end{align*}
$$

Fall 2: $z>1$
$$
\begin{align*}\MoveEqLeft{}
\int_{-\infty}^{\infty} \begin{cases} e^{x-z} & 0 \le x \le 1 \land z \ge x \\ 0 & \text{sonst.}  \end{cases}\, dx \\&
= \underbrace{\int_{-\infty}^0 0\, dx}_\text{$x < 0$} + \underbrace{\int_0^1 e^{x-z}\, dx}_\text{$0 \le x \le 1,\ z \ge x$} + \underbrace{\int_1^\infty 0\, dx}_\text{$x > 1$} 
= \int_0^1 e^{x-z}\, dx \\&
= e^{-z} \int_0^1 e^x\, dx 
= e^{-z} \cdot \Big( e^x \big|_0^1 \Big) = e^{-z} (e-1)a
\end{align*}
$$
Die Zufallsvariable $Z = X+Y$ hat somit die Dichte:
$$
f_Z(z) = \begin{cases} e^{-z}(e-1) & z > 1 \\ 1 - e^{-z} & 0 \le z \le 1 \\ 0 & z < 0 \end{cases} 
$$

# Aufgabe 3)

Sei $X \sim \operatorname{Bin}(n; 0,82)$ die Anzahl der erschienenen von den $n$ angemeldeten Studienanfängern.
Sei $n \in \mathbb{N}^+$ die Anzahl der angemeldeten Studienanfängern.

Wir stellen die Zufallsvariable als Summe von unabhängig, identisch verteilten Zufallsvariablen $Y_i \sim \operatorname{Ber}(0,82),\ i=1, \ldots, 240$, die jeweils das Erscheinen eines angemeldeten Studienanfängern beschreibt, dar:
$$
X = \sum_{i=1}^{n} Y_i
$$

Laut dem zentralen Grenzwertsatz gilt
$$
X \approx n \cdot \mathbb{E}\left[ Y_1 \right] + \sqrt{n} \cdot \sigma \cdot Y 
$$
wobei $\mathbb{E}\left[ Y_1 \right] = 0,82$ und $\sigma = \sqrt{\mathbb{V}(Y_1)} = \sqrt{0,82 \cdot 0,18} = \sqrt{0,1476}$ und $Y$ standardnormalverteilte Zufallsvariable ist.
$$
X \approx n \cdot 0,82 + \sqrt{n} \cdot \sqrt{0,1476} \cdot Y = 0,82\,n + \sqrt{0,1476\,n} \cdot Y
$$
$$
Y \approx \frac{X - 0,82\,n}{\sqrt{0,1476\,n}} 
$$

## a)

Sei $n = 240$.
$$
\mathbb{P}(X \le 220) \approx \mathbb{P} \left( Y \le \frac{220 - 0,82 \cdot 240}{\sqrt{0,1476 \cdot 240}} \right) \approx \mathbb{P}\left(Y \le 3.89798 \right) = \Phi_{0,1} \left( 3,89798 \right) \approx 0,999515 
$$

## b)

Sei $n \in \mathbb{N} ^+$.
$$
0,99 \le \mathbb{P}(X \le 220) \approx \mathbb{P} \left( Y \le \frac{220 - 0,82\,n}{\sqrt{0,1476\,n}} \right) = \Phi_{0,1} \left( \frac{220 - 0,82\,n}{\sqrt{0,1476\,n}} \right)
$$
Laut Normalverteilungstabelle gilt $\Phi_{0,1}(2,32) \approx 0,9898 \approx 0,99$.
$$
\Phi_{0,1}(2,32) \le 0,99 \le \Phi_{0,1} \left( \frac{220 - 0,82\,n}{\sqrt{0,1476\,n}} \right) 
$$
Da die Standardnormalverteilung monoton steigend ist, folgt:
$$
2,32 \le \frac{220 - 0,82\,n}{\sqrt{0,1476\,n}} \quad\Rightarrow\quad 0 < n \le 251,069 \quad\overset{\text{$n \in \mathbb{N}^+$}}{\Rightarrow}\quad n \le 251 
$$

Die Probe für $n'= 251$ ergibt $\mathbb{P} \left( Y \le\frac{220 - 0,82 \cdot 251}{\sqrt{0,1476 \cdot 251}} \right) \approx \Phi_{0,1}(2,32968) \approx 0,9901 \ge 0,99$.
Die Probe für $n''= 252$ ergibt $\mathbb{P} \left( Y \le \frac{220 - 0,82 \cdot 252}{\sqrt{0,1476 \cdot 252}} \right) \approx \Phi_{0,1}(2,19060) \approx 0,9858 \not\ge 0,99$.

Es dürfen höchstens 251 Anmeldungen angenommen werden.
