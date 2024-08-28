---
title: "Array-like environments - Align equations and relation symbol relative to each other"
dg-publish: true
---

# Centered equation(s)

- **Single** equation¹ `\[` …`\]`, Multiple equations² `\begin{gather*}`

LaTeX supported by Overleaf, VS Code (pdflatex)
```latex
\documentclass{article}\pagestyle{empty}
\usepackage{mathtools,amssymb,amsfonts}
\begin{document}
\[
    x = x
\]
\begin{gather*}
    x = xxx \\
    xxx = x
\end{gather*}
\end{document}
```

$$
x = x
$$
$$
\begin{gather*}
x = xxx \\
xxx = x
\end{gather*}
$$

Markdown math supported by Obsidian (mathjax), VS Code/Quartz (katex)
```
x = x
```
Markdown math supported by Obsidian (mathjax), VS Code/Quartz (katex)
```
\begin{gather*}
x = xxx \\
xxx = x
\end{gather*}
```

# Align long equations

- $n$ pairs of **touching** columns³ `\begin{alignat*}{2}`

LaTeX
```latex
\documentclass{article}\pagestyle{empty}
\usepackage{mathtools,amssymb,amsfonts}
\begin{document}
\begin{alignat*}{2}
    p_{X_3}(1) &= \mathbb{P}(\{ (1,1) \} ) && = 0.13 \\
    p_{X_3}(2) &= \mathbb{P}(\{ (1,2),(2,1) \} ) & = 0.16+0.11 & = 0.27 \\
    p_{X_3}(3) &= \mathbb{P}(\{ (1,3),(3,1) \} ) & = 0.12+0.07 & = 0.19 \\
    p_{X_3}(4) &= \mathbb{P}(\{ (2,2) \} ) && = 0.16 \\
    p_{X_3}(6) &= \mathbb{P}(\{ (2,3),(3,2) \} ) & = 0.12+0.08 & = 0.20
\end{alignat*}
\end{document}
```

$$
\begin{alignat*}{2}
p_{X_3}(1) &= \mathbb{P}(\{ (1,1) \} ) && = 0.13 \\
p_{X_3}(2) &= \mathbb{P}(\{ (1,2),(2,1) \} ) & = 0.16+0.11 & = 0.27 \\
p_{X_3}(3) &= \mathbb{P}(\{ (1,3),(3,1) \} ) & = 0.12+0.07 & = 0.19 \\
p_{X_3}(4) &= \mathbb{P}(\{ (2,2) \} ) && = 0.16 \\
p_{X_3}(6) &= \mathbb{P}(\{ (2,3),(3,2) \} ) & = 0.12+0.08 & = 0.20
\end{alignat*}
$$

Markdown
```
\begin{alignat*}{2}
p_{X_3}(1) &= \mathbb{P}(\{ (1,1) \} ) && = 0.13 \\
p_{X_3}(2) &= \mathbb{P}(\{ (1,2),(2,1) \} ) & = 0.16+0.11 & = 0.27 \\
p_{X_3}(3) &= \mathbb{P}(\{ (1,3),(3,1) \} ) & = 0.12+0.07 & = 0.19 \\
p_{X_3}(4) &= \mathbb{P}(\{ (2,2) \} ) && = 0.16 \\
p_{X_3}(6) &= \mathbb{P}(\{ (2,3),(3,2) \} ) & = 0.12+0.08 & = 0.20
\end{alignat*}
```

# Layout multiple equations

Alternating **right/left**-aligned columns²³⁴
- **Separated** pairs¹ `\begin{align*}`
- Max. spaced-out to **line width**⁴ `\begin{flalign*}`

LaTeX supported by Overleaf, VS Code (pdflatex)
```latex
\documentclass{article}\pagestyle{empty}
\usepackage{mathtools,amssymb,amsfonts,multicol}
\begin{document}
\section{Multicolumn \dotfill}
\begin{multicols}{3}\allowdisplaybreaks\vspace*{-1cm}
    \begin{align*}%
        I_2 &= \frac{U_2}{R_2} \\
        U_2 &= \frac{d\Phi_2}{dt} \\
        \Phi &= MI
    \end{align*}
\end{multicols}

\section{Align}
\begin{align*}
    I_2 &= \frac{U_2}{R_2} &
    U_2 &= \frac{d\Phi_2}{dt} &
    \Phi &= MI
\end{align*}

\section{Flalign}
\begin{flalign*}
    I_2 &= \frac{U_2}{R_2} &
    U_2 &= \frac{d\Phi_2}{dt} &
    \Phi &= MI
\end{flalign*}
\end{document}
```

![minimal 40.svg](./attachments/minimal%2040.svg)

(2) Markdown math supported by Obsidian, VS Code, Quartz
```
\begin{align*}
I_2 &= \frac{U_2}{R_2} &
U_2 &= \frac{d\Phi_2}{dt} &
\Phi &= MI
\end{align*}
```

(3) Markdown math supported by Obsidian, **unsupported** by VS Code, **badly supported** by Quartz
```
\begin{flalign*}
I_2 &= \frac{U_2}{R_2} &
U_2 &= \frac{d\Phi_2}{dt} &
\Phi &= MI
\end{flalign*}
```
