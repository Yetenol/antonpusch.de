---
date: "2025-03-22T07:21:26.336+01:00"
title: "Define custom mathematical expressions"
description: "-"
dg-publish: true
---

# Custom symbols

Dependency: siunitx

Custom **symbol**
```latex
\newmathsymbol{\fE}{f_\mathrm{E}}
```

# Custom functions

Norm
```latex
\newcommand{\norm}[1]{\left\lVert{}#1\right\rVert}
```

Absolute value
```latex
\newcommand{\abs}[1]{\left\lvert{}#1\right\rvert}
```

# Better vectors

**Stretch vector arrow** as wide as the elements it spans
```latex
\renewcommand{\vec}{\vv}
```


---
Sources:

Related:

Tags:
[Values  - Standardize math, numbers, symbols, quantities, money](./Values-.md)
