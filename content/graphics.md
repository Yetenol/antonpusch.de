---
title: "Graphics - Draw vector networks, graphs, images, plots in latex with tikz, pgf"
dg-publish: true
---
- [LaTeX to SVG - Embed LaTeX figures in markdown. Automate compiling, cropping, and exporting.](LaTeX%20to%20SVG%20-%20Embed%20LaTeX%20figures%20in%20markdown.%20Automate%20compiling,%20cropping,%20and%20exporting..md)


Generate LaTeX figures from code blocks marked as python in this file by parsing them as a multiline string parameter.

```python {pre}
generate_latex_figure(r"""
```

```python {post}
""")
```

![figure tikz 1.svg](./attachments/figure%20tikz%201.svg)

```python
\documentclass{article}\pagestyle{empty}\title{tikz 1}
\usepackage{tikz}
\usetikzlibrary{trees, decorations, arrows, automata, shadows, positioning, plotmarks, calc, matrix}
\begin{document}

\begin{figure}[hp]
    \centering
\tikzstyle{alter}=[circle, minimum size=16pt, draw, inner sep=1pt] 
\tikzstyle{majarr}=[draw=black]
\begin{tikzpicture}[auto, >=stealth']
    \tikzstyle{majarr}=[draw=black,->,shorten <=1.5pt, shorten >=1.5pt]
    \node[alter, initial, accepting, initial text=] at (0,0) (e) {$[\varepsilon]$};
    \node[alter, accepting] at (2,0) (0) {$[0]$};
    \node[alter] at (0,-2) (1) {$[1]$};
    \node[alter, accepting] at (4,0) (01) {$[01]$};
    \node[alter] at (2,-2) (00) {$[00]$};
    \node[alter] at (4,-2) (11) {$[11]$};

    \draw[majarr] (e) edge node[midway, anchor=south] {$\scriptstyle 0$} (0);
    \draw[majarr] (e) edge node[midway, anchor=east] {$\scriptstyle 1$} (1);
    \draw[majarr] (0) edge[bend left=10] node[midway, anchor=west] {$\scriptstyle 0$} (00);
    \draw[majarr] (0) edge node[midway, anchor=south] {$\scriptstyle 1$} (01);
    \draw[majarr] (01) edge node[midway, anchor=west] {$\scriptstyle 0$} (00);
    \draw[majarr] (01) edge node[midway, anchor=west] {$\scriptstyle 1$} (11);
    \draw[majarr] (00) edge[bend left=10] node[midway, anchor=east] {$\scriptstyle 0$} (0);
    \draw[majarr] (00) edge node[midway, anchor=south] {$\scriptstyle 1$} (1);
    \draw[majarr] (1) edge node[midway, anchor=east] {$\scriptstyle 0$} (0);
    \draw[majarr] (1) edge[bend right=43] node[midway, anchor=south] {$\scriptstyle 1$} (11);
    \draw[majarr] (11) edge[loop right] node {$\scriptstyle 0,1$} (11);
\end{tikzpicture}
\end{figure}

\end{document}
```

# Plots

![figure tikz 2.svg](./attachments/figure%20tikz%202.svg)

```python
\documentclass{article}\pagestyle{empty}\title{tikz 2}
\usepackage{tikz}
\usetikzlibrary{trees, decorations, arrows, automata, shadows, positioning, plotmarks, calc, matrix}
\begin{document}

\begin{tikzpicture}[domain=0:4]
\draw[very thin,color=gray] (-0.1,-1.1) grid (3.9,3.9);
\draw[->] (-0.2,0) -- (4.2,0) node[right] {$x$};
\draw[->] (0,-1.2) -- (0,4.2) node[above] {$f(x)$};
\draw[color=red]    plot (\x,\x)             node[right] {$f(x) =x$};
\draw[color=blue]   plot (\x,{sin(\x r)})    node[right] {$f(x) = \sin x$};
\draw[color=orange] plot (\x,{0.05*exp(\x)}) node[right] {$f(x) = \frac{1}{20} \mathrm e^x$};
\end{tikzpicture}

\end{document}
```

```tikz
\begin{document}
  \begin{tikzpicture}[domain=0:4]
    \draw[very thin,color=gray] (-0.1,-1.1) grid (3.9,3.9);
    \draw[->] (-0.2,0) -- (4.2,0) node[right] {$x$};
    \draw[->] (0,-1.2) -- (0,4.2) node[above] {$f(x)$};
    \draw[color=red]    plot (\x,\x)             node[right] {$f(x) =x$};
    \draw[color=blue]   plot (\x,{sin(\x r)})    node[right] {$f(x) = \sin x$};
    \draw[color=orange] plot (\x,{0.05*exp(\x)}) node[right] {$f(x) = \frac{1}{20} \mathrm e^x$};
  \end{tikzpicture}
\end{document}
```

# Electrical circuit

![figure Electrical circuit.svg](./attachments/figure%20electrical%20circuit.svg)

```python
\documentclass{article}\pagestyle{empty}\title{Electrical circuit}
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[american, voltage shift=0.5]
\draw (0,0)
to[isource, l=$I_0$, v=$V_0$] (0,3)
to[short, -*, i=$I_0$] (2,3)
to[R=$R_1$, i>_=$i_1$] (2,0) -- (0,0);
\draw (2,3) -- (4,3)
to[R=$R_2$, i>_=$i_2$]
(4,0) to[short, -*] (2,0);
\end{circuitikz}

\end{document}
```

```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[american, voltage shift=0.5]
\draw (0,0)
to[isource, l=$I_0$, v=$V_0$] (0,3)
to[short, -*, i=$I_0$] (2,3)
to[R=$R_1$, i>_=$i_1$] (2,0) -- (0,0);
\draw (2,3) -- (4,3)
to[R=$R_2$, i>_=$i_2$]
(4,0) to[short, -*] (2,0);
\end{circuitikz}

\end{document}
```

# 3D Plot

![figure 3D plot.svg](./attachments/figure%203d%20plot.svg)

```python
\documentclass{article}\pagestyle{empty}\title{3D plot}
\usepackage{pgfplots}
\pgfplotsset{compat=1.16}
\begin{document}

\begin{tikzpicture}
\begin{axis}[colormap/viridis]
\addplot3[
	surf,
	samples=18,
	domain=-3:3
]
{exp(-x^2-y^2)*x};
\end{axis}
\end{tikzpicture}

\end{document}
```

```tikz
\usepackage{pgfplots}
\pgfplotsset{compat=1.16}

\begin{document}

\begin{tikzpicture}
\begin{axis}[colormap/viridis]
\addplot3[
	surf,
	samples=18,
	domain=-3:3
]
{exp(-x^2-y^2)*x};
\end{axis}
\end{tikzpicture}

\end{document}
```

# Networks

![figure Networks.svg](./attachments/figure%20networks.svg)

```python
\documentclass{article}\pagestyle{empty}\title{Networks}
\usepackage{tikz-cd}
\begin{document}

\begin{tikzcd}
T
\arrow[drr, bend left, "x"]
\arrow[ddr, bend right, "y"]
\arrow[dr, dotted, "{(x,y)}" description] & & \\
K & X \times_Z Y \arrow[r, "p"] \arrow[d, "q"]
& X \arrow[d, "f"] \\
& Y \arrow[r, "g"]
& Z
\end{tikzcd}
\quad \quad
\begin{tikzcd}[row sep=2.5em]
A' \arrow[rr,"f'"] \arrow[dr,swap,"a"] \arrow[dd,swap,"g'"] &&
  B' \arrow[dd,swap,"h'" near start] \arrow[dr,"b"] \\
& A \arrow[rr,crossing over,"f" near start] &&
  B \arrow[dd,"h"] \\
C' \arrow[rr,"k'" near end] \arrow[dr,swap,"c"] && D' \arrow[dr,swap,"d"] \\
& C \arrow[rr,"k"] \arrow[uu,<-,crossing over,"g" near end]&& D
\end{tikzcd}

\end{document}
```

```tikz
\usepackage{tikz-cd}

\begin{document}
\begin{tikzcd}

    T
    \arrow[drr, bend left, "x"]
    \arrow[ddr, bend right, "y"]
    \arrow[dr, dotted, "{(x,y)}" description] & & \\
    K & X \times_Z Y \arrow[r, "p"] \arrow[d, "q"]
    & X \arrow[d, "f"] \\
    & Y \arrow[r, "g"]
    & Z

\end{tikzcd}

\quad \quad

\begin{tikzcd}[row sep=2.5em]

A' \arrow[rr,"f'"] \arrow[dr,swap,"a"] \arrow[dd,swap,"g'"] &&
  B' \arrow[dd,swap,"h'" near start] \arrow[dr,"b"] \\
& A \arrow[rr,crossing over,"f" near start] &&
  B \arrow[dd,"h"] \\
C' \arrow[rr,"k'" near end] \arrow[dr,swap,"c"] && D' \arrow[dr,swap,"d"] \\
& C \arrow[rr,"k"] \arrow[uu,<-,crossing over,"g" near end]&& D

\end{tikzcd}

\end{document}
```

# Chemistry

![figure Chemistry.svg](./attachments/figure%20chemistry.svg)

```python
\documentclass{article}\pagestyle{empty}\title{Chemistry}
\usepackage{chemfig}
\begin{document}

\chemfig{[:-90]HN(-[::-45](-[::-45]R)=[::+45]O)>[::+45]*4(-(=O)-N*5(-(<:(=[::-60]O)-[::+60]OH)-(<[::+0])(<:[::-108])-S>)--)}

\end{document}
```


```tikz
\usepackage{chemfig}
\begin{document}

\chemfig{[:-90]HN(-[::-45](-[::-45]R)=[::+45]O)>[::+45]*4(-(=O)-N*5(-(<:(=[::-60]O)-[::+60]OH)-(<[::+0])(<:[::-108])-S>)--)}

\end{document}
```


# Chemistry 2

![figure Chemistry 2.svg](./attachments/figure%20chemistry%202.svg)

```python
\documentclass{article}\pagestyle{empty}\title{Chemistry 2}
\usepackage{chemfig}
\begin{document}

\definesubmol\fragment1{
(-[:#1,0.85,,,draw=none]
-[::126]-[::-54](=_#(2pt,2pt)[::180])
-[::-70](-[::-56.2,1.07]=^#(2pt,2pt)[::180,1.07])
-[::110,0.6](-[::-148,0.60](=^[::180,0.35])-[::-18,1.1])
-[::50,1.1](-[::18,0.60]=_[::180,0.35])
-[::50,0.6]
-[::110])
}

\chemfig{
!\fragment{18}
!\fragment{90}
!\fragment{162}
!\fragment{234}
!\fragment{306}
}

\end{document}
```

```tikz
\usepackage{chemfig}
\begin{document}

\definesubmol\fragment1{
(-[:#1,0.85,,,draw=none]
-[::126]-[::-54](=_#(2pt,2pt)[::180])
-[::-70](-[::-56.2,1.07]=^#(2pt,2pt)[::180,1.07])
-[::110,0.6](-[::-148,0.60](=^[::180,0.35])-[::-18,1.1])
-[::50,1.1](-[::18,0.60]=_[::180,0.35])
-[::50,0.6]
-[::110])
}

\chemfig{
!\fragment{18}
!\fragment{90}
!\fragment{162}
!\fragment{234}
!\fragment{306}
}

\end{document}
```
 
---
Sources:
- [A Tutorial for Beginners (Part 1)—Basic Drawing - Overleaf, Online LaTeX Editor](https://www.overleaf.com/learn/latex/LaTeX_Graphics_using_TikZ%3A_A_Tutorial_for_Beginners_(Part_1)%E2%80%94Basic_Drawing)
- [documentation - Materials for learning TikZ - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/15779/materials-for-learning-tikz)
- [documentation - Online searchable manual for TikZ? - TeX - LaTeX Stack Exchange](http://tex.stackexchange.com/questions/11182/online-searchable-manual-for-tikz)
- [documentation - What is the minimum one needs to know to use TikZ? - TeX - LaTeX Stack Exchange](http://tex.stackexchange.com/questions/9116/what-is-the-minimum-one-needs-to-know-to-use-tikz)
- [TikZ and PGF Manual](http://mirrors.ctan.org/graphics/pgf/base/doc/pgfmanual.pdf)
- [TikZ and PGF examples](http://www.texample.net/tikz/examples/)
- [TikZ and PGF | TeXample.net](http://www.texample.net/tikz/)

Related:
- [Markup and typesetting systems - Produce printed or digital documents aesthetically pleasing with readable typography](./markup%20and%20typesetting%20systems.md)


Tags:
[Graphical elements - Standardize tables, images, plots](./graphical%20elements.md)