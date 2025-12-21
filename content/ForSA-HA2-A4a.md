---
date: "2025-07-17T08:13:58.175+02:00"
title: "ForSA HA2 A4a"
description: "-"
dg-publish: true
---

Sei $​\Sigma = \{ a,b \} ​$. Gegeben sei die Sprache
$$
A_{1} = \left\{  xyx^{R} \mid x \in \Sigma^{*} \land y \in \{ a \}^{*} \land \lvert x \rvert_{a} \ge 1 \land \lvert x \rvert_{a} = \lvert y \rvert      \right\} 
$$
Beweise nur mit dem Pumping Lemma für reguläre Sprachen, dass $​A_{1} ​$ nicht regulär ist.

$$
\mathscr{xyz}
$$

# Eigenschaften der Sprache in natürlichem Deutsch

Die Sprache $A_1$ besteht aus Wörtern über dem Alphabet $\Sigma = \{a, b\}$, die folgende Eigenschaften erfüllen:

1. Das Wort hat die Form $xyx^R$, wobei $x$ ein beliebiges Wort über $\Sigma$ ist und $y$ ein Wort über $\Sigma$, das nur aus dem Buchstaben $a$ besteht.
2. Das Wort $x$ enthält mindestens einmal den Buchstaben $a$.
3. Die Anzahl der Vorkommen des Buchstabens $a$ in $x$ ist gleich der Länge des Wortes $y$.

Mit anderen Worten, ein Wort in $A_1$ besteht aus einer beliebigen Kombination von Buchstaben aus $\Sigma$, gefolgt von einem Wort, das nur aus dem Buchstaben $a$ besteht und die gleiche Länge hat wie die Anzahl der $a$'s in der vorherigen Kombination von Buchstaben. Schließlich wird das Wort durch die Rückwärtsdarstellung der vorherigen Kombination von Buchstaben abgeschlossen.

# Beispielwörter der Sprache

$$
A_{1} = \left\{  \textcolor{magenta}{x}\textcolor{limegreen}{y}\textcolor{orange}{x^{R}} \mid x \in \Sigma^{*} \land y \in \{ a \}^{*} \land \lvert x \rvert_{a} \ge 1 \land \lvert x \rvert_{a} = \lvert y \rvert      \right\},
\qquad \Sigma = \{ a,b \} 
$$
$$
\textcolor{magenta}{a}\textcolor{limegreen}{a}\textcolor{orange}{a},
\textcolor{magenta}{aa}\textcolor{limegreen}{aa}\textcolor{orange}{aa},
\textcolor{magenta}{ab}\textcolor{limegreen}{a}\textcolor{orange}{ba},
\textcolor{magenta}{aab}\textcolor{limegreen}{aa}\textcolor{orange}{baa},
\textcolor{magenta}{bababa}\textcolor{limegreen}{aaa}\textcolor{orange}{ababab}
$$


$$
\textcolor{magenta}{abaaaa}\textcolor{limegreen}{a}\textcolor{orange}{ba} \not \in  A
$$


# Beweis mit Pumping Lemma, dass die Sprache nicht regulär ist

Sei $p \in \mathbb{N} $ (beliebig aber fest). Wir wählen das Wort $w = a^{p + 1}b \cdot  a^{p + 1}  \cdot ba^{p + 1}$ mit $w \in A_{1} $, denn $(ba^{p + 1} )^{R} = a^{p + 1}b$, und $a^{p + 1}b \in \Sigma^{*}$, und $a^{p + 1}  \in \{ a \}^{*}$, und $\lvert a^{p + 1}b \rvert_{a} = p + 1 \ge 1$ da $p \in \mathbb{N}$, und $\lvert a^{p + 1}b \rvert_{a} = p + 1 = \lvert a^{p + 1}  \rvert$. Sei $w = \mathbb{xyz}$ eine beliebige Zerlegung mit $\mathbb{y} \ne \varepsilon$ und $\lvert \mathbb{xy} \rvert \le p$. Dann ist $\mathbb{x} = a^{i}$, $\mathbb{y} = a^{j}$ und $\mathbb{z} = a^{p + 1 - i - j}ba^{p + 1}ba^{p + 1}$ für ein $j \ne 0$ und $i + j \le p + 1$.

Wir wählen $k = 0$. Dann ergibt
$$
    \mathbb{xy}^{0} \mathbb{z} = a^{i} \cdot a^{p + 1 - i - j}ba^{p + 1}ba^{p + 1} = a^{p + 1 - j}ba^{p + 1}ba^{p + 1}
$$
Um zu Überprüfen, ob $\mathbb{xy}^{0} \mathbb{z}$ ein Wort der Sprache $A_{1}$ ist, prüfen wir, ob wir $\mathbb{xy}^{0} \mathbb{z}$ so in die drei Teilworte $x$, $y$, und $x^{R}$ aufteilen können, dass die Bedingungen $\left( x^{R} \right)^{R} = x \land x \in \Sigma^{*} \land y \in \{ a \}^{*} \land \left| x \right|_{a} \ge 1 \land \left| x \right|_{a} = \left| y \right|​$ erfüllt sind. $b$'s können nur im Teilwort $x \in \Sigma^{*}$ oder $x^{R} \in \Sigma^{*}$ vorkommen, jedoch nicht in $y \in \{ a \}^{*}$. Das Wort $\mathbb{xy}^{0} \mathbb{z}$ enthält den Buchstaben $b$ zweimal: $\lvert a^{p + 1 - j}ba^{p + 1}ba^{p + 1} \rvert_{b} = 2$. Da $x^{R}$ eine Rückwärtsdarstellung von $x$ ist, müssen beide Teilworte gleich viele, also genau eines der beiden $b$'s enthalten, also gilt $\lvert x \rvert_{b} = \left\lvert  x^{R} \right\rvert_{b} = 1$. Dann ist $x = a^{p + 1 - j}ba^{l}$, $y = a^{p + 1 - 2l}$, und $x^{R} = a^{l} b a^{p + 1}$ für ein $2l \le p + 1$ mit $l \in \mathbb{N}$.
$$
    \mathbb{xy}^{0} \mathbb{z} = a^{p + 1 - j}ba^{p + 1}ba^{p + 1} 
    = a^{p + 1 - j} b a^{l} \cdot a^{p + 1 - 2l} \cdot a^{l} b a^{p + 1}
$$
$\mathbb{xy}^{0} \mathbb{z} \notin A_{1}$, denn $\left( x^{R} \right)^{R} \ne x$, da $(a^{l} b a^{p + 1})^{R} = a^{p + 1} b a^{l}$ ungleich $a^{p + 1 - j}ba^{l}$ für $j \ne 0$ ist. Da $\neg \operatorname{\textbf{PUMP-REG}} ( A_{1}  )$, ist $A_{1} $ nach dem Pumping-Lemma nicht regulär.

---

Sei $p \in \mathbb{N}$ (beliebig aber fest). Wir wählen das Wort $w = a^{p + 1}b \cdot  a^{p + 1}  \cdot ba^{p + 1}$ mit $w \in A_{1} $, denn $(ba^{p + 1} )^{R} = a^{p + 1}b$, und $a^{p + 1}b \in \Sigma^{*}$, und $a^{p + 1}  \in \{ a \}^{*}$, und $\lvert a^{p + 1}b \rvert_{a} = p + 1 \ge 1$ da $p \in \mathbb{N}$, und $\lvert a^{p + 1}b \rvert_{a} = p + 1 = \lvert a^{p + 1}  \rvert$. Sei $w = \mathbb{xyz}$ eine beliebige Zerlegung mit $\mathbb{y} \ne \varepsilon$ und $\lvert \mathbb{xy} \rvert \le p$. 
Das Wort $w$ beginnt mit dem Präfix $a^{p+1}$, wobei $​\left| a^{p + 1}  \right| = p + 1 > p​$.
Da $\lvert \mathbb{xy} \rvert \le p$ und $\lvert a^{p + 1} \rvert >  p$ gilt, wissen wir, dass sowohl $x$ als auch $y$ nur aus Buchstaben $a$ bestehen. Dann ist $\mathbb{x} = a^{i}$, $\mathbb{y} = a^{j}$ und $\mathbb{z} = a^{p + 1 - i - j}ba^{p + 1}ba^{p + 1}$ für ein $j \ne 0$ und $i + j \le p$:

Sei $​p \in \mathbb{N} ​$ (beliebig aber fest). Wir wählen das Wort $​w = \textcolor{magenta}{a^{p + 1}b} \cdot  \textcolor{limegreen}{a^{p + 1}}  \cdot \textcolor{orange}{ba^{p + 1}}​$ mit $​w \in A_{1} ​$, denn $​(ba^{p + 1} )^{R} = a^{p + 1}b​$, und $​a^{p + 1}b \in \Sigma^{*}​$, und $​a^{p + 1}  \in \{ a \}^{*}​$, und $​\lvert a^{p + 1}b \rvert_{a} = p + 1 \ge 1​$ da $​p \in \mathbb{N}​$, und $​\lvert a^{p + 1}b \rvert_{a} = p + 1 = p + 1 = \lvert a^{p + 1}  \rvert​$. Sei $​w = \mathbb{xyz}​$ eine beliebige Zerlegung mit $\mathbb{​y} \ne \varepsilon​$ und $​\lvert \mathbb{xy} \rvert \le p​$. Da $​\lvert \mathbb{xy} \rvert \le p​$ und $​\lvert a^{p + 1} \rvert >  p ​$ gilt, wissen wir, dass sowohl $​x​$ als auch $​y​$ nur aus Buchstaben $​a​$ bestehen. Dann ist $​\mathbb{x} = a^{i}​$, $​\mathbb{y} = a^{j}​$ und $​\mathbb{z} = a^{p + 1 - i - j}ba^{p + 1}ba^{p + 1}​$ für ein $​j \ne 0​$ und $​i + j \le p$:

$$
\begin{align*}
w = a^{p + 1}b \cdot  a^{p + 1}  \cdot ba^{p + 1} 
&= \overbrace{ \underbrace{ a \ldots a }_{i}\,  \underbrace{ a \ldots a }_{j}\, \underbrace{ a \ldots a }_{p + 1 - i - j} }^{p + 1}\, b\, \overbrace{ a \ldots a }^{p + 1}\, b\, \overbrace{ a \ldots a }^{p + 1} \\
&= \underbrace{ \overbrace{ a \ldots a } }_{\mathbb{x}}\; \underbrace{ \overbrace{ a \ldots a } }_{\mathbb{y}}\; \underbrace{ \overbrace{ a \ldots a }\; b\; a \ldots a\; b\; a \ldots a }_{\mathbb{z}} \\
&= a^{i} \cdot a^{j} \cdot a^{p + 1 - i - j} b a^{p + 1} b a^{p + 1}     
= \mathbb{xyz} 
\end{align*}
$$
$$
\begin{align*}
w = \textcolor{magenta}{a^{p + 1}b} \cdot  \textcolor{limegreen}{a^{p + 1}}  \cdot \textcolor{orange}{ba^{p + 1}} 
&= \overbrace{ \underbrace{ a \ldots a }_{i}\,  \underbrace{ a \ldots a }_{j}\, \underbrace{ a \ldots a }_{p + 1 - i - j} }^{p + 1}\, b\, \overbrace{ a \ldots a }^{p + 1}\, b\, \overbrace{ a \ldots a }^{p + 1} \\
&= \underbrace{ \overbrace{ a \ldots a } }_{\mathbb{x}}\, \underbrace{ \overbrace{ a \ldots a } }_{\mathbb{y}}\, \underbrace{ \overbrace{ a \ldots a }\, b\, a \ldots a\, b\, a \ldots a }_{\mathbb{z}} \\
&= a^{i} \cdot a^{j} \cdot a^{p + 1 - i - j} b a^{p + 1} b a^{p + 1}     
= \mathbb{xyz} 
\end{align*}
$$

Wir wählen $​k = 0$. Dann ergibt
$$
\mathbb{xy}^{0} \mathbb{z} = a^{i} \cdot a^{p + 1 - i - j}ba^{p + 1}ba^{p + 1} = a^{p + 1 - j}ba^{p + 1}ba^{p + 1}​
$$

Um zu Überprüfen, ob $\mathbb{xy}^{0} \mathbb{z}$ ein Wort der Sprache $A_{1}$ ist, prüfen wir, ob wir $\mathbb{xy}^{0} \mathbb{z}$ so in die drei Teilworte $x$, $y$, und $x^{R}$ aufteilen können, dass die Bedingungen $\left( x^{R} \right)^{R} = x \land x \in \Sigma^{*} \land y \in \{ a \}^{*} \land \left| x \right|_{a} \ge 1 \land \left| x \right|_{a} = \left| y \right|​$ erfüllt sind. $b$'s können nur im Teilwort $x \in \Sigma^{*}$ oder $x^{R} \in \Sigma^{*}$ vorkommen, jedoch nicht in $y \in \{ a \}^{*}$. Das Wort $\mathbb{xy}^{0} \mathbb{z}$ enthält den Buchstaben $b$ zweimal: $\lvert a^{p + 1 - j}ba^{p + 1}ba^{p + 1} \rvert_{b} = 2$. Da $x^{R}$ eine Rückwärtsdarstellung von $x$ ist, müssen beide Teilworte gleich viele, also genau eines der beiden $b$'s enthalten, also gilt $\lvert x \rvert_{b} = \left\lvert  x^{R} \right\rvert_{b} = 1$. Dann ist $x = a^{p + 1 - j}ba^{l}$, $y = a^{p + 1 - 2l}$, und $x^{R} = a^{l} b a^{p + 1}$ für ein $2l \le p + 1$ mit $l \in \mathbb{N}$.

$$
\begin{align*}
\mathbb{xy}^{0} \mathbb{z} = a^{p + 1 - j}ba^{p + 1}ba^{p + 1} 
&= \overbrace{ a \ldots a }^{p + 1 - j}\, b\, \overbrace{ \underbrace{ a \ldots a }_{l}\, \underbrace{ a \ldots a }_{p + 1 - 2l}\, \underbrace{ a \ldots a }_{l} }^{p + 1}\, b\, \overbrace{ a \ldots a }^{p + 1} \\
&= \underbrace{ a \ldots a\, b \overbrace{ a \ldots a } }_{x}\, \underbrace{ \overbrace{ a \ldots a } }_{y}\, \underbrace{ \overbrace{ a \ldots a } b\, a \ldots a }_{x^{R}} \\
&= a^{p + 1 - j} b a^{l} \cdot a^{p + 1 - 2l} \cdot a^{l} b a^{p + 1}
\end{align*}
$$

$​\mathbb{xy}^{0} \mathbb{z} \notin A_{1}​$, denn $​\left( x^{R} \right)^{R} \ne x​$, da $​(a^{l} b a^{p + 1})^{R} = a^{p + 1} b a^{l}  \ne a^{p + 1 - j}b​$ für $​j \ne 0​$. Da $​\neg \operatorname{\textbf{PUMP-REG}} ( A_{1}  )​$, ist $​A_{1} ​$ nach dem Pumping-Lemma nicht regulär.


---
Sources:

Related:

Tags:
ForSA HA2 zum 2023-07-13