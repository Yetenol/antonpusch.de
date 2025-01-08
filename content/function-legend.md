---
title: "Function legend - Show formulas for multiple functions"
date: "2025-01-08T00:00:00.000+01:00"
dg-publish: true
---

# Default best placement

Inside overlay legend
Auto placed

![plot legend auto.svg](./attachments/plot-legend-auto.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'savefig.transparent':True, 'svg.fonttype':'none',
    'figure.constrained_layout.use':True, 'axes.titlesize': 10,
    'axes.grid':True, 'grid.linestyle':':'})
def plot_example_functions(axes):
    x = np.linspace(0, 4, 100)
    axes.set_xlabel("x")
    axes.plot(x, x, label=r"$f(x) = x$")
    axes.plot(x, np.exp(x)/20, label=r"$g(x) = \frac{1}{20}\, e^x$")
    axes.plot(x, np.sin(x), label=r"$h(x) = \sin(x)$")
def show_legend_auto(axes):
    axes.set_title("Figure 2.1: Automatic placement at best location")
    axes.legend()

fig, ax = plt.subplots(figsize=(6,2.2))
plot_example_functions(ax)
show_legend_auto(ax)
plt.savefig(@vault_path + '/attachments/plot legend auto.svg')
plt.show()
```

# Locations inside data

- Available locations: `best`, `upper right`, `upper left`, `lower left`, `lower right`, `right`, `center left`, `center right`, `lower center`, `upper center`, `center`


![plot legend inside.svg](./attachments/plot-legend-inside.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'savefig.transparent':True, 'svg.fonttype':'none',
    'figure.constrained_layout.use':True, 'axes.titlesize': 10,
    'axes.grid':True, 'grid.linestyle':':'})
def plot_example_functions(axes):
    x = np.linspace(0, 4, 100)
    axes.set_xlabel("x")
    axes.plot(x, x, label=r"$f(x) = x$")
    axes.plot(x, np.exp(x)/20, label=r"$g(x) = \frac{1}{20}\, e^x$")
    axes.plot(x, np.sin(x), label=r"$h(x) = \sin(x)$")
def show_legend_top_right(axes):
    axes.set_title("Figure 2.2: Show legend inside data")
    axes.legend(loc="upper right")

fig, ax = plt.subplots(figsize=(6,2.2))
plot_example_functions(ax)
show_legend_top_right(ax)
plt.savefig(@vault_path + '/attachments/plot legend inside.svg')
plt.show()
```

# Custom location

- [Legend guide — Matplotlib 3.10.0 documentation](https://matplotlib.org/stable/users/explain/axes/legend_guide.html)


# Figure legends

![plot legend figure.svg](./attachments/plot-legend-figure.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'savefig.transparent':True, 'svg.fonttype':'none',
    'figure.constrained_layout.use':True, 'axes.titlesize': 10,
    'axes.grid':True, 'grid.linestyle':':'})
def plot_example_functions(axes_list):
    x = np.linspace(0, 4, 100)
    for axes in axes_list:
        axes.set_xlabel("x")
    axes_list[0].plot(x, x, label=r"$f(x) = x$")
    axes_list[1].plot(x, np.exp(x)/20, color='orange',
        label=r"$g(x) = \frac{1}{20}\, e^x$")
    axes_list[2].plot(x, np.sin(x), color='green', 
        label=r"$h(x) = \sin(x)$")
def show_legend_alongside_subplots(figure):
    figure.suptitle("Figure 2.4: Combined figure legend for all axes",
        fontsize=10)
    figure.legend(loc="outside center right")

fig, axs = plt.subplots(ncols=3, figsize=(6,2.2))
plot_example_functions(axs)
show_legend_alongside_subplots(fig)
plt.savefig(@vault_path + '/attachments/plot legend figure.svg')
plt.show()
```


[Other plot legends](Other%20plot%20legends.md)