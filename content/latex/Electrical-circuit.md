---
date: "2025-03-22T11:25:28.650+01:00"
title: "Electrical circuit"
description: "Dynamically draw electronic circuit diagrams as a vector graphic"
dg-publish: true
dg-folder: latex
---

# Electrical circuit

Example from [Obsidian TikZJax](https://github.com/artisticat1/obsidian-tikzjax)
![figure electrical circuit.svg](../figure-electrical-circuit.svg)

```py
generate_latex_figure(r"""
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
""", outfile="figure electrical circuit")
```

![figure electrical circuit europe.svg](../figure-electrical-circuit-europe.svg)

```py
generate_latex_figure(r"""
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
""", outfile="figure electrical circuit europe")
```

# Figure collection for note preview

![figure circuits.svg](../figure-circuits.svg)

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