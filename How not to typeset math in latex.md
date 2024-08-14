# Why not use showonlyrefs from mathtools?

Problem1: tags overlap with long equations, only eqref and not ref cause tag to be shown, tag still needs to be in an numbered (non-starred) math environment which looks very different without the option (not very portable)

```latex
\documentclass{article}
\pagestyle{empty}
\usepackage{amsmath}
\begin{document}
\begin{align*}
    E=mc^2  \label{anton}\tag{\theequation}\refstepcounter{equation} \\
    E=mc^2  \\
    E=mc^2  \\
    E=mc^2  \tag{\theequation} \refstepcounter{equation} \\
\end{align*}
\begin{equation}
    a
\end{equation}
\[
    E=mc^2  \tag{\theequation}\refstepcounter{equation} \\
\]
\eqref{anton}
\end{document}
```

![[./content/minimal 31.svg|minimal 31.svg]]
# More