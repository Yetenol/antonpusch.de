---
title: "Plots - Dynamically plot mathematical functions as a vector graphic"
date: "2024-12-31T00:00:00.000+01:00"
dg-publish: true
---

# Tikzpicture

![figure tikz 2.svg](./attachments/figure-tikz-2.svg)

```latex
\documentclass{standalone}
\usepackage{tikz}
\usetikzlibrary{trees, decorations, arrows, automata, shadows, 
    positioning, plotmarks, calc, matrix}
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

- Example from [Obsidian TikZJax](https://github.com/artisticat1/obsidian-tikzjax) 

# 3D Plot - PgfPlots

![figure 3d plot.svg](./attachments/figure-3d-plot.svg)

```latex
\documentclass{standalone}
\usepackage{pgfplots}
\pgfplotsset{compat=1.16}
\begin{document}
\begin{tikzpicture}
\begin{axis}[colormap/viridis]
\addplot3[ surf, samples=18, domain=-3:3, ]{
    exp(-x^2-y^2)*x  };
\end{axis}
\end{tikzpicture}
\end{document}
```

- Example from [Obsidian TikZJax](https://github.com/artisticat1/obsidian-tikzjax) 

# Figure collection for note preview

![figure plots.svg](./attachments/figure-plots.svg)

```latex
\documentclass{standalone}
\usepackage{graphicx}
\begin{document}
\includegraphics{figure tikz 2.pdf}
\includegraphics{figure 3d plot.pdf}
\end{document}
```

https://pyx-project.org/
https://pyx-project.org/gallery/graph/index.html

https://asymptote.sourceforge.io/
https://gertingold.github.io/pythonnawi/graphics.html
