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

![minimal 31.svg](./content/attachments/minimal%2031.svg)
# More

$$
\begin{flalign*}
\boxed{\begin{array}{r:l} xx \!\!&\!\! =  xxx \\ \hdashline x \!\!&\!\! = x \end{array}} & \to & \gets 
\boxed{\begin{array}{r:l} xxxx \!\!&\!\! =  x \\ \hdashline xx \!\!&\!\! = xxx \end{array}} \\
&& (4)
\end{flalign*}
$$

$$
x = \frac{\splitfrac{xxxxxx}{xxxxx}}{x}
$$
$$
\sideset{_{\text{bl}}^{\text{tl}}}{_{\text{br}}^{\text{tr}}}\sum_{B}^{T}
$$
