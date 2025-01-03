---
title: "Electrical circuit - Dynamically draw electronic circuit diagrams as a vector graphic"
date: "2024-12-16T00:00:00.000+01:00"
dg-publish: true
---

# Electrical circuit

Example from [Obsidian TikZJax](https://github.com/artisticat1/obsidian-tikzjax)
![figure electrical circuit.svg](./attachments/figure-electrical%20circuit.svg)

```latex
\documentclass{standalone}
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

![figure electrical circuit europe.svg](./attachments/figure-electrical%20circuit%20europe.svg)

```latex
\documentclass{standalone}
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz}[american, voltage shift=0.5]
\draw (0,0)
to[isource, l=$I_0$, v=$V_0$] (0,3)
to[short, -*, i=$I_0$] (2,3)
to[european resistor=$R_1$, i>_=$i_1$] (2,0) -- (0,0);
\draw (2,3) -- (4,3)
to[european resistor=$R_2$, i>_=$i_2$]
(4,0) to[short, -*] (2,0);
\end{circuitikz}
\end{document}
```

# Figure collection for note preview

![figure circuits.svg](./attachments/figure-circuits.svg)

```python
generate_latex_figure(r"""
\documentclass{standalone}
\usepackage{graphicx}
\begin{document}
\includegraphics{figure electrical circuit}
\includegraphics{figure electrical circuit europe}
\end{document}
""", outfile="figure circuits")
```