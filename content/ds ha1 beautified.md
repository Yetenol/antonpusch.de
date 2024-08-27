---
title: "DS HA1 beautified"
dg-publish: true
---
\section{Ameisenkolonie}
\hfill \textbf{9 Punkte}

Sei $2\,000\,000 \le n \le 3\,000\,000$ die Anzahl der Ameisen in der Kolonie mit
$$
\begin{align*}
n &\equiv 3 \pmod{19} & \implies n &\in [3]_{\equiv 19} \\
n &\equiv 1 \pmod{20} & \implies n &\in [1]_{\equiv 20} \\
n &\equiv 2 \pmod{21} & \implies n &\in [2]_{\equiv 21} \\
n &\equiv 1 \pmod{22} & \implies n &\in [1]_{\equiv 22} \\
n &\equiv 0 \pmod{23} & \implies n &\in [0]_{\equiv 23}
\end{align*}
$$
Sei $A = [3]_{\equiv 19} \cap [1]_{\equiv 20} \cap [2]_{\equiv 21} \cap [1]_{\equiv 22} \cap [0]_{\equiv 23}$.

Laut Definition, teilt der Divisor $m$ die Differenz zweier Zahlen derselben Äquivalenzklasse $[x]_{\equiv m}$.
Die Elemente von $A$ sind in $5$ Äquivalenzklassen enthalten. Somit teilen jeweils die Divisoren \numlist{19;20;21;22;23} die Differenz zweier Zahlen aus $A$; die kleinstmögliche solche Zahl ist das kleinste gemeinsame Vielfache von \numlist{19;20;21;22;23}:
$$\operatorname{kgV}(19,20,21,22,23) = \operatorname{kgV}(19,2^2 \cdot 5,3 \cdot 7, 2 \cdot 11, 23) = 19 \cdot 2^2 \cdot 5 \cdot 3 \cdot 7 \cdot 11 \cdot 23 = 2018940 = M$$
Also teilt $M$ die Differenz zweier Zahlen aus $A$. Das nächst kleinere und nächst größere Element von $A$ sind:
$n_0 - \operatorname{kgV}(19,20,21,22,23) = 2\,582\,141 - 2\,018\,940 = 563\,201 < 2\,000\,000$ und \\
$n_0 + \operatorname{kgV}(19,20,21,22,23) = 2\,582\,141 + 2\,018\,940 = 4\,601\,081 > 3\,000\,000$.

Somit hat $A$ im Bereich $2\,000\,000 \le n \le 3\,000\,000$ nur ein Element.

Somit sind genau $2\,582\,141$ Ameisen in der Kolonie und keine andere Anzahl ist möglich.

$$
n \equiv 1 \pmod{22} \implies \exists\, k \in \mathbb{Z} \mid n = 22k + 1 \implies \exists\, k \in \mathbb{Z}  \mid n = 11 \cdot \underbrace{ 2k }_{\in\, \mathbb{Z} } + 1 \implies  n \equiv 1 \pmod{11}
$$
Das System $m_{1} = 11$, $m_{2} = 19$, $m_{3} = 20$, $m_{4} = 21$, $m_{5} = 23$ ist paarweise relativ prim, da paarweise kein gemeinsamer Primfaktor existiert $11$, $19$, $2^2 \cdot 5$, $3 \cdot 7$ und $23$. Laut chinesischem Restsatz kann jede natürliche Zahl $< 19 \cdot 20 \cdot 21 \cdot 11 \cdot 23 = M = 2018940$ eindeutig durch ihre Reste modulo \numlist{19; 20; 21; 11; 23} dargestellt werden.

$$
\left.
\begin{aligned}
n &\equiv a_{i} \!\!\pmod{m_{i}} \\
n &\equiv 1 \pmod{11} \\
n &\equiv 3 \pmod{19} \\
n &\equiv 1 \pmod{20} \\
n &\equiv 2 \pmod{21} \\
n &\equiv 0 \pmod{23} \\
\end{aligned}
\;\right\}\;
\begin{aligned}
M & = 11 \cdot 19 \cdot 20 \cdot 21 \cdot 23 \\
& = 2\,018\,940
\end{aligned}
\quad
\begin{aligned}
M_{i} & = {^M  {\!/\!}_{m_{i}}} \\
M_{1} &= {^M {\!/\!}_{11}} = 19 \cdot 20 \cdot 21 \cdot 23 = 183\,540 \\ 
M_{2} &= {^M {\!/\!}_{19}} = 11 \cdot 20 \cdot 21 \cdot 23 = 106\,260 \\
M_{3} &= {^M {\!/\!}_{20}} = 11 \cdot 19 \cdot 21 \cdot 23 = 100\,947 \\
M_{4} &= \tfrac{M}{21} = 11 \cdot 19 \cdot 20 \cdot 23 = 96\,140 \\
M_{5} &= \frac{M}{23} = 11 \cdot 19 \cdot 20 \cdot 21 = 87\,780 \\
\end{aligned}
$$
$$
\begin{align*}
{1\,234\,568 \over 2} \\
\frac 1 2 \\
\frac{ab}{cd} \\
\frac{1 + 2}{3}
\end{align*}
$$


$$
\begin{align*}
M_{i} \cdot t_{i} &\equiv 1 \pmod{m_{i}} \\
M_{1} \cdot 9 &\equiv 1 \pmod{11}  \\
M_{2} \cdot 8 &\equiv 1 \pmod{19}  \\
M_{3} \cdot 3 &\equiv 1 \pmod{20}  \\
M_{4} \cdot 11 &\equiv 1 \pmod{21}  \\
M_{5} \cdot 2 &\equiv 1 \pmod{23}  \\
\end{align*}
$$
$$
\begin{multline*}
\implies \text{Lösung: } n_{0}  
:= \sum_{i = 1}^{5} a_{i} \cdot M_{i} \cdot t_{i}  
 = 1 \cdot 183\,540 \cdot 9 
 + 3 \cdot 106\,260 \cdot 8 
 + 1 \cdot 100\,947 \cdot 3 \\
 + 2 \cdot 96\,140 \cdot 11 
 + 0 \cdot 87\,780 \cdot 2 
 = 6\,620\,021
\end{multline*}
$$
$n_{0} \bmod M = 6\,620\,021 \bmod 2\,018\,940 = 563\,201$ ist die kleinste positive Lösung des obigen Systems.

Wir suchen eine weitere eine Lösung $n_{2}$ für das obige System im Bereich $2\,000\,000 \le n_{2} \le 3\,000\,000$:
$$
\begin{gather}
n_{2} = n_{1} + M = 563\,201 + 2\,018\,940 = 2\,582\,141 \\
2\,000\,000 \le 2\,582\,141 \le 3\,000\,000 \\
\begin{aligned}
2\,582\,141 &\equiv 3 \pmod{19} \quad &
2\,582\,141 &\equiv 2 \pmod{21} \quad &
2\,582\,141 &\equiv 0 \pmod{23} \quad \\
2\,582\,141 &\equiv 1 \pmod{20} \quad &
2\,582\,141 &\equiv 1 \pmod{22}
\end{aligned}
\end{gather}
$$
Somit ist $n_2 = 2\,582\,141$ eine mögliche Anzahl von Ameisen ist der Kolonie.

Laut Definition, teilt der Divisor $m_{i}$ die Differenz zweier Zahlen derselben Äquivalenzklasse $[x]_{\equiv m}$.
Die Elemente von $A$ sind in $5$ Äquivalenzklassen enthalten. Somit teilen die Divisoren \numlist{19;20;21;22;23} die Differenz zweier Zahlen aus $A$; die kleinstmögliche solche Zahl ist das kleinste gemeinsame Vielfache von \numlist{19;20;21;22;23}.
$$\operatorname{kgV}(19,20,21,22,23) = \operatorname{kgV}(19,2^2 \cdot 5,3 \cdot 7, 2 \cdot 11, 23) = 19 \cdot 2^2 \cdot 5 \cdot 3 \cdot 7 \cdot 11 \cdot 23 = 2\,018\,940 $$

Also teilt $2\,018\,940$ die Differenz zweier Zahlen aus $A$.

Wir bestimmen einen möglichen Wert $n_0 \in A$ für $2\,000\,000 \le n_0 \le 3\,000\,000$. Die in Algorithmus \ref{alg:Ameisenkolonie} aufgelistete Berechnung hilft uns, einen geeigneten Kandidaten zu finden, für die mathematische Beweisführung ist er jedoch nicht notwendig.

Wir behaupten $n_0 = 2\,582\,141 \in A$, wobei $2\,000\,000 \le 2\,582\,141 \le 3\,000\,000$ gilt.
$$
\begin{align*}
2\,582\,141 &\equiv 3 \pmod{19}, & 2\,582\,141 &\equiv 2 \pmod{21}, & 2\,582\,141 &\equiv 0 \pmod{23} \\
2\,582\,141 &\equiv 1 \pmod{20}, & 2\,582\,141 &\equiv 1 \pmod{22}
\end{align*}
$$
$\Rightarrow n_0 \in [3]_{\equiv 19} \cap [1]_{\equiv 20} \cap [2]_{\equiv 21} \cap [1]_{\equiv 22} \cap [0]_{\equiv 23} \Rightarrow n_0 \in A$

Da $2\,018\,940$ die Differenz zweier Zahlen aus $A$ teilt, sind das nächst kleinere und nächst größere Element von $A$: \\
$n_0 - \operatorname{kgV}(19,20,21,22,23) = 2\,582\,141 - 2\,018\,940 = 563\,201 < 2\,000\,000$ und \\
$n_0 + \operatorname{kgV}(19,20,21,22,23) = 2\,582\,141 + 2\,018\,940 = 4\,601\,081 > 3\,000\,000$.

Somit hat $A$ im Bereich $2\,000\,000 \le n \le 3\,000\,000$ nur ein Element.

Somit sind genau $2\,582\,141$ Ameisen in der Kolonie und keine andere Anzahl ist möglich.

\begin{algorithm}
\KwResult{2582141 ist der kleinste mögliche Wert für $n$}
\For{$n=2000000$ \textbf{to} $3000000$}{
    \If{$n \bmod 19 = 3$ \textbf{and} $n \bmod 20 = 1$ \textbf{and} $n \bmod 21 = 2$ \textbf{and} $n \bmod 22 = 1$ \textbf{and} $n \bmod 23 = 0$}{
        \Return $n$
    }
}
\caption{Ein Algorithmus der einen Wert im Bereich $2\,000\,000 \le n \le 3\,000\,000$ findet, der in den Äquivalenzklassen $[3]_{\equiv 19}$, $[1]_{\equiv 20}$, $[2]_{\equiv 21}$, $[1]_{\equiv 22}$ und $[0]_{\equiv 23}$ enthalten ist.}
\label{alg:Ameisenkolonie}
\end{algorithm}

---

Wir zeigen, dass das linke Konvergenzsystem genau dann gilt, wenn das rechte Konvergenzsystem gilt:

$$
\textit{Zu Zeigen: }
\left(
\begin{aligned}
    n &\equiv 3 \pmod{19} \;\land \\
    n &\equiv 1 \pmod{20} \;\land \\
    n &\equiv 2 \pmod{21} \;\land \\
    n &\equiv 1 \pmod{22} \;\land \\
    n &\equiv 0 \pmod{23}
\end{aligned} 
\right)
\iff 
\left(
\begin{aligned}
    n &\equiv 1 \pmod{11} \;\land \\
    n &\equiv 3 \pmod{19} \;\land \\
    n &\equiv 1 \pmod{20} \;\land \\
    n &\equiv 2 \pmod{21} \;\land \\
    n &\equiv 0 \pmod{23}
\end{aligned} 
\right)
$$

Wir zeigen zunächst die rechte Richtung der Biimplikation. Wir nehmen die 5 Konvergenzen des linken Systems an und zeigen die 5 Konvergenzen des rechten Systems:
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
Offensichtlich folgen aus $(A1)$, $(A2)$, $(A3)$ und $(A4)$ die gleichen Konvergenzen $(Z1.1)$, $(Z2.1)$, $(Z3.1)$ und $(Z4.1)$. Aus $(A5)$ folgen wir nun $(Z5.1)$:

$$
\begin{multline*}
    n \equiv 1 \pmod{22} 
    \implies \exists\, k \in \mathbb{Z} \mid n = 22k + 1 \\
    \implies \exists\, k \in \mathbb{Z}  \mid n = 11 \cdot \underbrace{ 2k }_{\in\, \mathbb{Z} } + 1 
    \implies  n \equiv 1 \pmod{11}
\end{multline*}
$$
Wir haben alle Teilziele gezeigt und somit auch die rechte Richtung der Biimplikation gezeigt.

Jetzt zeigen wir die linke Richtung der Implikation. Wir nehmen die 5 Konvergenzen des rechten Systems an und zeigen die 5 Konvergenzen des linken Systems:
$$
\begin{gathered}
    \text{Annahmen:} \\
    (A11): n \equiv 3 \pmod{19} \\
    (A12): n \equiv 1 \pmod{20} \\
    (A13): n \equiv 2 \pmod{21} \\
    (A14): n \equiv 0 \pmod{23} \\
    (A15): n \equiv 1 \pmod{11}
\end{gathered} 
\qquad
\begin{gathered}
    \text{Zu Zeigen:} \\
    (Z11.1): n \equiv 3 \pmod{19} \\
    (Z12.1): n \equiv 1 \pmod{20} \\
    (Z13.1): n \equiv 2 \pmod{21} \\
    (Z14.1): n \equiv 0 \pmod{23} \\
    (Z15.1): n \equiv 1 \pmod{22}
\end{gathered} 
$$
Offensichtlich folgen aus $(A11)$, $(A12)$, $(A13)$ und $(A14)$ die gleichen Konvergenzen $(Z11.1)$, $(Z12.1)$, $(Z13.1)$ und $(Z14.1)$. 

Aus $(A12)$ folgt:
$$
\begin{multline*}
n \equiv 1 \pmod{20} 
\implies \exists\, l \in \mathbb{Z} \mid n = 20l + 1 \\
\implies \exists\, l \in \mathbb{Z} \mid n = 2 \cdot \underbrace{ 10l }_{\in\, \mathbb{Z}} + 1 
\implies n \equiv 1 \pmod{2}
\end{multline*}
$$
Also folgt die Annahme:
$(A16): n \text{ ist ungerade}$

Wir zeigen mit Kontraposition, dass wenn $(Z15.1)$ nicht erfüllt wäre, dies Annahmen widerspricht. Wir betrachten die Restklasse modulo $22$ in einer Fallunterscheidung:

Fall 1: $n \bmod 22 \in \{ 0,2,3,4,5,6,7,8,9,10 \}$:
Es folgt $n \not\equiv 1 \pmod{11}$, was $(A15)$ widerspricht.

Fall 2: $n \bmod 22 \in \{ 11, 13, 14, 15, 16, 17, 18, 19, 20, 21 \}$:
Bezogen auf die Konvergenz modulo 11, sind diese Werte konvergent zu den Restklassen in Fall 1. Es folgt $n \not\equiv 1 \pmod{11}$, was $(A15)$ widerspricht.

Fall 3: $n \bmod 22 = 12$:
$$
\exists\, m \in \mathbb{Z} \mid n = 22m + 12 
\implies \exists\, m \in \mathbb{Z} \mid n = 2 \underbrace{ (11m + 6) }_{\in\, \mathbb{Z} } \implies n \equiv 0 \pmod{2}
$$
Es folgt, $n$ ist gerade, was $(A16)$ widerspricht.

Wir haben alle Teilziele gezeigt und somit die linke Richtung der Biimplikation gezeigt.

Also ist das rechte Konvergenzsystem äquivalent zum linken Konvergenzsystem. Es genügt also zu Zeigen, dass das linke Konvergenzsystem nur eine Lösung im Bereich $2\,000\,000 \le n \le 3\,000\,000$ hat. 

Fall 1: $n$ ist gerade:

Aus $(A12)$ folgt die Fallunterscheidung:
$$
\begin{multline*}
n \equiv 1 \pmod{20} 
\implies \exists\, l \in \mathbb{Z} \mid n = 20l + 1 \\
\implies \exists\, l \in \mathbb{Z} \mid n = 2 \cdot \underbrace{ 10l }_{\in\, \mathbb{Z}} + 1 
\implies n \equiv 1 \pmod{2}
\end{multline*}
$$
Also ist $n$ Element der Äquivalenzklasse ungerader Zahlen $[1]_{\equiv 2}$, wobei laut Definition $2$ die Differenz zweier ihrer Elemente teilt.

Laut $(A15)$ ist $n$ auch Element der Äquivalenzklasse $[1]_{\equiv 11}$, wobei $11$ die Differenz zweier ihrer Elemente teilt. 

Somit ist $n$ Element der Schnittmenge $[1]_{\equiv 2} \cap [1]_{\equiv 11}$, und die Zahlen $2$ und $11$ teilen die Differenz zweier Elemente dieser Schnittmenge. Da $2$ und $11$ teilerfremd sind, muss die Differenz auch durch $\operatorname{kgV} (2,11) = 22$ teilbar sein.

$n$ muss also ungerade sein.
Aus $(A15)$ folgt:
$$
n \equiv 1 \pmod{11} \implies \exists\, m \in \mathbb{Z} \mid n = 11m + 1
$$

$$
n = 20m + 1 =  11l + 1
$$

Wir zeigen $(Z15.1)$ mit einer Fallunterscheidung:

$n \equiv 1 \pmod{20}$ und $n \equiv 1 \pmod{11}$ folgt $n \equiv \pmod{22}$.

Fall 1 $n \equiv 1 \pmod{22}$:

$$

Aus $(A12)$ folgt $$
\exists\, l \in \mathbb{Z} \mid n = 20l + 1
\implies \exists\, l \in \mathbb{Z} \mid 2 \cdot \underbrace{ 10l }_{\in\, \mathbb{Z}} + 1 \implies n \equiv 1 \pmod{2} 
$$

Offensichtlich folgen aus den angenommenen Konvergenzen modulo $19$, $20$, $21$ und $23$, die Konvergenzen selbst. 

Sei $n \in [3]_{\equiv 19} \cap [1]_{\equiv 20} \cap [2]_{\equiv 21} \cap [1]_{\equiv 22} \cap [0]_{\equiv 23}$.

Offensichtlich gilt:
$$
\left(
\begin{aligned}
    n &\equiv 3 \pmod{19} \;\land \\
    n &\equiv 1 \pmod{20} \;\land \\
    n &\equiv 2 \pmod{21} \;\land \\
    n &\equiv 0 \pmod{23}
\end{aligned} 
\right)
\iff 
\left(
\begin{aligned}
    n &\equiv 3 \pmod{19} \;\land \\
    n &\equiv 1 \pmod{20} \;\land \\
    n &\equiv 2 \pmod{21} \;\land \\
    n &\equiv 0 \pmod{23}
\end{aligned} 
\right)
$$
Wir müssen also zeigen, dass $n \equiv 1 \pmod{22} \iff n \equiv 1 \pmod{11}$ gilt.

$$
\begin{multline*}
    n \equiv 1 \pmod{22} 
    \implies \exists\, k \in \mathbb{Z} \mid n = 22k + 1 \\
    \implies \exists\, k \in \mathbb{Z}  \mid n = 11 \cdot \underbrace{ 2k }_{\in\, \mathbb{Z} } + 1 
    \implies  n \equiv 1 \pmod{11}
\end{multline*}
$$
$$
n \equiv 1 \pmod{11}
\implies \exists\, k \in \mathbb{Z} \mid n = 11k + 1
\implies \exists\,  : 

---

