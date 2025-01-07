---
title: "Spines - Place axis spines of plots"
date: "2025-01-07T00:00:00.000+01:00"
dg-publish: true
---

Normal spines

![plot spine 1.svg](./attachments/plot-spine-1.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams['text.usetex'] = True
plt.rcParams['font.family'] = 'serif'
x = np.linspace(0, np.pi*2, 100)
plt.figure(figsize=(2.7, 2), layout='constrained')
plt.plot(x, np.sin(x), label=r"$f(x) = \sin(x)$")
plt.grid(True)
plt.title("Figure 1.1: Normal spines", fontsize=10)
export_plt_figure(plt, outfile="plot spine 1")
plt.show()
```

Hide spines

![plot spine 2.svg](./attachments/plot-spine-2.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams['text.usetex'] = True
plt.rcParams['font.family'] = 'serif'
x = np.linspace(0, np.pi*2, 100)
plt.figure(figsize=(2.7, 2), layout='constrained')
plt.plot(x, np.sin(x), label=r"$f(x) = \sin(x)$")
plt.title("Figure 1.2: Left, bottom spines", fontsize=10)
plt.grid(True)
ax = plt.subplot()
ax.spines[['right', 'top']].set_visible(False)
export_plt_figure(plt, outfile="plot spine 2")
plt.show()
```

Spines through $(0,0)$ and with arrows

![plot spine 3.svg](./attachments/plot-spine-3.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.axisartist.axislines import AxesZero
plt.rcParams['text.usetex'] = True
plt.rcParams['font.family'] = 'serif'
x = np.linspace(0, np.pi*2, 100)
plt.figure(figsize=(3, 2.5), layout='constrained')
ax = plt.subplot(axes_class=AxesZero)
ax.plot(x, np.sin(x), label=r"$f(x) = \sin(x)$")
plt.title("Figure 1.3: Spines with arrow tips,\n through origin $(0,0)$, \n", fontsize=10)
plt.grid(True)
for direction in ["xzero", "yzero"]:
    ax.axis[direction].set_axisline_style("-|>")
    ax.axis[direction].set_visible(True)
for direction in ["left", "right", "bottom", "top"]:
    ax.axis[direction].set_visible(False)
export_plt_figure(plt, outfile="plot spine 3")
plt.show()
```

# Collection for note preview

![plot spines.svg](./attachments/plot-spines.svg)

```latex
\documentclass{standalone} \usepackage{graphbox}
\begin{document}
\includegraphics[align=c]{plot spine 1}
\includegraphics[align=c]{plot spine 2}
\includegraphics[align=c]{plot spine 3}
\end{document}
```


# Modify spines

- [Spines — Matplotlib 3.10.0 documentation](https://matplotlib.org/stable/gallery/spines/spines.html#sphx-glr-gallery-spines-spines-py)
- [Spine placement — Matplotlib 3.10.0 documentation](https://matplotlib.org/stable/gallery/spines/spine_placement_demo.html#sphx-glr-gallery-spines-spine-placement-demo-py)
- [Axis line styles — Matplotlib 3.10.0 documentation](https://matplotlib.org/stable/gallery/axisartist/demo_axisline_style.html)

![plot spines 2.svg](./attachments/plot-spines-2.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams['text.usetex'] = True
plt.rcParams['font.family'] = 'serif'
x = np.linspace(0, 4, 100)
plt.figure(figsize=(3, 2.5))
plt.plot(x, x, label=r"$f(x) = x$")
plt.plot(x, np.exp(x)/20, label=r"$g(x) = \frac{1}{20}\, e^x$")
plt.plot(x, np.sin(x), label=r"$h(x) = \sin(x)$")
plt.title("Figure 1.1: Normal spines", fontsize=10)
plt.legend()
plt.grid(True)
plt.savefig(@vault_path + '/attachments/plot spine normal.pdf', transparent=True)
plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams['text.usetex'] = True
plt.rcParams['font.family'] = 'serif'
x = np.linspace(0, 4, 100)
plt.figure(figsize=(3, 2.5))
ax = plt.subplot()
ax.plot(x, x, label=r"$f(x) = x$")
ax.plot(x, np.exp(x)/20, label=r"$g(x) = \frac{1}{20}\, e^x$")
ax.plot(x, np.sin(x), label=r"$h(x) = \sin(x)$")
plt.title("Figure 1.2: Left and bottom spine", fontsize=10)
ax.spines[['right', 'top']].set_visible(False)
ax.legend()
ax.grid(True)
plt.savefig(@vault_path + '/attachments/plot spine bottom-left.pdf', transparent=True)
plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams['text.usetex'] = True
plt.rcParams['font.family'] = 'serif'
x = np.linspace(0, 4, 100)
plt.figure(figsize=(3, 2.5))
ax = plt.subplot()
ax.plot(x, x, label=r"$f(x) = x$")
ax.plot(x, np.exp(x)/20, label=r"$g(x) = \frac{1}{20}\, e^x$")
ax.plot(x, np.sin(x), label=r"$h(x) = \sin(x)$")
plt.title("Figure 1.3: Spines through $(0,0)$", fontsize=10)
ax.spines[['left', 'bottom']].set_position('zero')
ax.spines[['top', 'right']].set_visible(False)
ax.legend()
ax.grid(True)
plt.savefig(@vault_path + '/attachments/plot spine zero.pdf', transparent=True)
plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.axisartist.axislines import AxesZero
plt.rcParams['text.usetex'] = True
plt.rcParams['font.family'] = 'serif'
x = np.linspace(0, 4, 100)
plt.figure(figsize=(3, 2.5))
ax = plt.subplot(axes_class=AxesZero)
ax.plot(x, x, label=r"$f(x) = x$")
ax.plot(x, np.exp(x)/20, label=r"$g(x) = \frac{1}{20}\, e^x$")
ax.plot(x, np.sin(x), label=r"$h(x) = \sin(x)$")
plt.title("Figure 1.4: Spines with arrows", fontsize=10)
for direction in ["xzero", "yzero"]:
    ax.axis[direction].set_axisline_style("-|>")
    ax.axis[direction].set_visible(True)
for direction in ["left", "right", "bottom", "top"]:
    ax.axis[direction].set_visible(False)
ax.legend()
ax.grid(True)
plt.savefig(@vault_path + '/attachments/plot spine arrows.pdf', transparent=True)
plt.show()
```

```latex
\documentclass{standalone} \usepackage{graphicx,tabularray}
\begin{document}
\begin{tblr}{}
\includegraphics{plot spine normal} 
\includegraphics{plot spine bottom-left} \\
\includegraphics{plot spine zero}
\includegraphics{plot spine arrows}
\end{tblr}
\end{document}
```


