
| t                  | U                   |
| ------------------ | ------------------- |
| $10$               | $0.76$              |
| $25$               | $0.5$               |
| $81$               | $0.29$              |
| $289$              | $0.14$              |
| $1{,}089$          | $4.42\cdot 10^{-2}$ |
| $4{,}225$          | $1.7\cdot 10^{-2}$  |
| $16{,}641$         | $8.2\cdot 10^{-3}$  |
| $66{,}049$         | $3.91\cdot 10^{-3}$ |
| $2.63\cdot 10^{5}$ | $1.95\cdot 10^{-3}$ |
| $1.05\cdot 10^{6}$ | $9.77\cdot 10^{-4}$ |



| $_{x}\diagdown^{y}$   |              0 |              1 |              2 | $\mathbb{P}(X=\cdot)$ |
| --------------------- | -------------: | -------------: | -------------: | --------------------: |
| 0                     | $^1\!/_{\!16}$ | $^1\!/_{\!16}$ |            $0$ |         $^1\!/_{\!8}$ |
| 1                     | $^2\!/_{\!16}$ | $^3\!/_{\!16}$ | $^1\!/_{\!16}$ |         $^3\!/_{\!8}$ |
| 2                     | $^1\!/_{\!16}$ | $^3\!/_{\!16}$ | $^2\!/_{\!16}$ |         $^3\!/_{\!8}$ |
| 3                     |            $0$ | $^1\!/_{\!16}$ | $^1\!/_{\!16}$ |         $^1\!/_{\!8}$ |
| $\mathbb{P}(Y=\cdot)$ |  $^1\!/_{\!4}$ |  $^1\!/_{\!2}$ |  $^1\!/_{\!4}$ |                       |


![minimal 68.svg](./content/attachments/minimal%2068.svg)

![Pasted image 20240822022401.png](./content/attachments/pasted%20image%2020240822022401.png)

Overleaf
```latex
\documentclass{article}
\pagestyle{empty}
\usepackage{amsmath,mathtools,amssymb,amsfonts,color,multicol,tabularray,tabularx,pgfplotstable}
\pgfplotstableset{/pgfplots/compat = 1.17, col sep = &, row sep = \\, string type}
\setlength{\columnseprule}{1pt}
\def\columnseprulecolor{\color{blue}}
\setlength{\parindent}{0pt}
\renewenvironment{tabularx}[0]{\begin{tblr}}{\end{tblr}}
\begin{document}

\begin{tabularx}[caption,tall]{lc}
      Name & Identifier \\
      Peter&3\\
 Io&Hat\\
 Lara&$\triangle$\\
 \end{tabularx}

\begin{align*} \qquad&\hspace{-2em}
\mathbb{P}(X+Y=k) 
= \sum_{\mathclap{x \in X(\Omega)}} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}

\end{document}
```