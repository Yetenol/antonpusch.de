

# Split Equations to equal part to Multi column

- [p] easy to move equations up and down
- [p] allows tab placement in every line

![minimal 37.svg](./content/attachments/minimal%2037.svg) ^a638e9

```latex
\documentclass{article}
\usepackage{amsmath,amssymb,amsfonts,multicol}
\begin{document}
\begin{multicols}{6}\allowdisplaybreaks\vspace*{-1cm}
\begin{align*}%
    a &= b+c \\
    0 &= t+d \\
    0 &= t+d \\
    0 &= t+d \\
    0 &= t+d \\
    0 &= t+d \\
    0 &= t+d \\
    0 &= t+d \\
    0 &= t+d \\
    0 &= t+d \\
    0 &= t+d
\end{align*}
\end{multicols}
\end{document}
```

# Aligned overset

$$
\begin{align*}\MoveEqLeft{}
\Big( \exists\, y \operatorname{.} \neg \big( P_1(y) \lor P_2(y) \big) \Big) \lor \neg \big( \forall\, z \operatorname{.} \neg P_2(z) \lor P_1(z) \big) \to \big( \exists\, x \operatorname{.} \neg P_1(x) \big) \\&
\overset{\mathclap{\text{Proposition 0.5.6}}}{\equiv}\hspace{2em} \neg\big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \lor \neg\big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \to \big(\exists\, x \operatorname{.} \neg P_1(x)\big) \\&
\overset{\mathclap{\text{Proposition 0.5.6}}}{\equiv}\hspace{2em} \neg\big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \lor \neg\big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \to \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \\&
\overset{\mathclap{\text{Implikation}}}{\equiv}\hspace{1.3em} \neg \Big( \neg\big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \lor \neg\big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \Big) \lor \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \\&
\overset{\mathclap{\text{De Morgan II}}}{\equiv}\hspace{1.5em} \Big( \neg\neg\big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \land \neg\neg\big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \Big) \lor \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \\&
\overset{\mathclap{\text{Doppelte Negation}}}{\equiv}\hspace{2.3em} \Big( \big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \land \big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \Big) \lor \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \\&
\overset{\mathclap{\text{Kommutativität von $\lor$}}}{\equiv}\hspace{2.9em} \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \lor \Big( \big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \land \big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \Big)
\end{align*}
$$

```latex
\begin{align*}\MoveEqLeft{}
\Big( \exists\, y \operatorname{.} \neg \big( P_1(y) \lor P_2(y) \big) \Big) \lor \neg \big( \forall\, z \operatorname{.} \neg P_2(z) \lor P_1(z) \big) \to \big( \exists\, x \operatorname{.} \neg P_1(x) \big) \\
\mathrlap{\xLongrightarrow{\hspace{5.5em}}}
\overset{\text{Proposition 0.5.6}}&{=} 
\neg\big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \lor \neg\big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \to \big(\exists\, x \operatorname{.} \neg P_1(x)\big) \\
\overset{\text{Proposition 0.5.6}}&{\equiv} 
\neg\big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \lor \neg\big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \to \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \\
\overset{\text{Implikation}}&{\equiv} 
\neg \Big( \neg\big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \lor \neg\big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \Big) \lor \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \\
\overset{\text{De Morgan II}}&{\equiv} 
\Big( \neg\neg\big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \land \neg\neg\big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \Big) \lor \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \\
\overset{\text{Doppelte Negation}}&{\equiv} 
\Big( \big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \land \big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \Big) \lor \neg\big(\forall\, x \operatorname{.} P_1(x)\big) \\
\overset{\text{Kommutativität von $\lor$}}&{\equiv} 
\neg\big(\forall\, x \operatorname{.} P_1(x)\big) \lor \Big( \big(\forall\, y \operatorname{.} P_1(y) \lor P_2(y)\big) \land \big(\forall\, z \operatorname{.} \neg P_2(z) \lor  P_1(z)\big) \Big)
\end{align*}
```

# More


$$
\begin{align*}
[ \varepsilon  ]_{ \equiv A} & = \{ \varepsilon \} \\
[ 0 ]_{ \equiv_{A} } & = \{ x0 \mid x \in \Sigma^{*} \land \left| x \right|_{0} \bmod 2 = 1  \} \\
[ 01 ]_{ \equiv_{A} } & = \{ x1 \mid x \in \Sigma^{*} \land \left| x \right|_{0} \bmod 2 = 1  \} \\
[ 00 ]_{ \equiv_{A} } & = \{ x0 \mid x \in \Sigma^{*} \land \left| x \right|_{0} \bmod 2 = 0   \} \\
[ 1 ]_{ \equiv_{A} } & = \{ x1 \mid x \in \Sigma^{*} \land \left| x \right|_{0} \bmod 2 = 0  \} \\
[ 11 ]_{ \equiv_{A} } & = \{ x11y \mid x,y \in \Sigma^{*} \} 
\end{align*}
$$

$$
\begin{align*}
[ \varepsilon ]_{ \equiv_{A} } & = \{ b^{n} \mid n \in \mathbb{N} \} \\
[ a^{k} ]_{ \equiv_{A} } & = \{ w \in \{ a, b \}^{*} \mid \left| w \right|_{a} = k \} \text{ für } k \in \mathbb{N}^{+} \\
[ c ]_{ \equiv_{A} } &= \{ xcy \mid x,y \in \{ a, b \}^{*} \land \left| x \right|_{a} - \left| y \right|_{a}  = 0 \} \\
[ a^{l} c ]_{ \equiv_{A} } &= \{ xcy \mid x,y \in \{ a, b \}^{*} \land \left| x \right|_{a} - \left| y \right|_{a}  = l \} \text{ für } l \in \mathbb{N}^{+}  \\
[ cc ]_{ \equiv_{A} } &= \{ w, xcy \mid w \in \{a,b,c\}^{*} \land \left| w \right|_{c} \ge 2 \land x,y \in \{a,b\}^{*} \land \left| y \right|_{a} > \left| x \right|_{a} + 2 \}
\end{align*}
$$
$$
\begin{align*}
P_{1}: \quad S &\to b \mid abbb \mid acbbb \mid aAbbbbb \mid aACbbbbb \mid aACCbbbbb \\
A &\to AACbb \mid AAbb \\
bC &\to Cb \\
aA &\to aa \\
aC &\to ac \\
cC &\to cc
\end{align*}
$$

$$
X = \sum_{1\le i\le j\le n} X_{ij} \qquad
X = \sum_{\mathclap{1\le i\le j\le n}} X_{ij}
$$