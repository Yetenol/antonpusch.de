---
title: "Molecules - Dynamically draw structural formulas of chemical molecules as a vector graphic"
dg-publish: true
---

Generate LaTeX figures from code blocks marked as python in this file by parsing them as a multiline string parameter.

```python {pre}
generate_latex_figure(r"""
```

```python {post}
""")
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


# Figure collection for note preview

![figure molecules.svg](./attachments/figure%20molecules.svg)

```python
\documentclass{standalone}\title{molecules}
\usepackage{chemfig}
\begin{document}

\begin{minipage}[t]{0.5\textwidth}
\vspace{1cm}
\chemfig{[:-90]HN(-[::-45](-[::-45]R)=[::+45]O)>[::+45]*4(-(=O)-N*5(-(<:(=[::-60]O)-[::+60]OH)-(<[::+0])(<:[::-108])-S>)--)}
\end{minipage}
\hspace{.8cm}
\begin{minipage}[t]{0.5\textwidth}
\vspace{0cm}
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
\end{minipage}

\end{document}
```