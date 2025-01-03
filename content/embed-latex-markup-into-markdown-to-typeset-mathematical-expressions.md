---
title: "Embed LaTeX markup into Markdown to typeset mathematical expressions"
date: "2025-01-03T00:00:00.000+01:00"
dg-publish: true
---

Some Markdown variants natively support the implementation of LaTeX markup. Alternatively, an externally generated pictorial rendering using Github can be embedded.

# Example Renderings

| Markup                                                                                                                                                                            | Native Rendering                                                                                                                             | Image Rendering                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `$\int_0^1{\pi^2} \geq 0$`                                                                                                                                                        | $\int_0^1{\pi^2} \geq 0$                                                                                                                     | ![equation](https://render.githubusercontent.com/render/math?math=\int_0^1{\pi^2}\geq{}0)                                                                                                                                            |
| `$\begin{bmatrix}` <br> `1 & 2 & \ldots & n \\` <br> `10 & 20 & \ldots & 10n \\` <br> `\vdots & \vdots & \ddots & \vdots \\` <br> `m & 2m & \ldots & 10^nm` <br> `\end{bmatrix}$` | $\begin{bmatrix} 1 & 2 & \ldots & n \\ 10 & 20 & \ldots & 10n \\ \vdots & \vdots & \ddots & \vdots \\ m & 2m & \ldots & 10^nm \end{bmatrix}$ | <img src="https://render.githubusercontent.com/render/math?math=\begin{bmatrix} 1 %26 2 %26 \ldots %26 n \\ 10 %26 20 %26 \ldots %26 10n \\ \vdots %26 \vdots %26 \ddots %26 \vdots \\ m %26 2m %26 \ldots %26 10^nm \end{bmatrix}"> |

Current markdown flavor
```
$\int_0^1{\pi^2} \geq 0$
```
- $\int_0^1{\pi^2} \geq 0$

Embedded GitHub-generated image
```
![equation](https://render.githubusercontent.com/render/math?math=\int_0^1{\pi^2}\geq{}0)
```
- ![equation](https://render.githubusercontent.com/render/math?math=\int_0^1{\pi^2}\geq{}0)

HTML GitHub-generated image
```
<img src="https://render.githubusercontent.com/render/math?math=\int_0^1{\pi^2} \geq 0">
```
- <img src="https://render.githubusercontent.com/render/math?math=\int_0^1{\pi^2} \geq 0">


---
Sources:
- 2022-04-04: [A hack for showing LaTeX formulas in GitHub markdown.md · GitHub](https://gist.github.com/a-rodin/fef3f543412d6e1ec5b6cf55bf197d7b)

Related:

Tags:
[Markdown - Write content-focused and format with hierarchy, abstract highlighting, and meta-information](./markdown.md)