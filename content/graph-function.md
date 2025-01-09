---
title: "Graph function - Dynamically plot mathematical functions as a vector graphic"
date: "2025-01-09T00:00:00.000+01:00"
dg-publish: true
---


# Native and external processing tools 

![plot engine comparison.svg](./attachments/plot-engine-comparison.svg)

- Compare: [Graphing tool comparison - Compare native and external calculation and drawing engines like PGF, MatPlotLib, PyX for visualising data](Graphing%20tool%20comparison%20-%20Compare%20native%20and%20external%20calculation%20and%20drawing%20engines%20like%20PGF,%20MatPlotLib,%20PyX%20for%20visualising%20data.md)

# Terminology

Explicit Axes through Figure `fig` , Axes `ax`

Implicit Axes through PyPlot `plt`

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'savefig.transparent':True, 'savefig.bbox':'tight', 
    'figure.constrained_layout.use':True, 'svg.fonttype':'none',
    'axes.titlesize': 10, 'axes.grid':True, 'grid.linestyle':':'})
def plot_example_function(axes):
    x = np.linspace(0, 2.5, 100)
    axes.set_xlabel("x")
    axes.plot(x, np.cos(np.pi*x)*np.exp(-x), 
        label=r"$f(x) = \dfrac{\cos(\pi x)}{e^x}$")
    axes.legend()

fig, ax = plt.subplots(figsize=(6,2.2))
plot_example_function(ax)
# plt.savefig(@vault_path + '/attachments/plot .svg')
plt.show()
```

# Modify spines of the x or y axis

- Hide unwanted spines, see 1.2, 1.3
- Move spines to origin $(0,0)$, see 1.3
- Add arrow tips to the top and right end of the spines
- See source code examples: [Spines - Place axis spines of plots](./spines.md)

![plot spines.svg](./attachments/plot-spines.svg)

# Add legend

- Show legend at best determined location inside data, see 2.1
- Position legend outside data, see 2.2
- Position legend entries horizontally or in a grid, see 2.2
- Annotate the lines directly within the data, see 2.3
- See source code examples: [Function legend - Show formulas for multiple functions](./function-legend.md)

![plot legend.svg](./attachments/plot-legend.svg)

# Differentiate functions with color or line style

See source code examples: [Cycles - Differentiate data set with colors or line style](./cycles.md)

![plot cycles.svg](./attachments/plot-cycles.svg)

# Size

- [Size of plots](Size%20of%20plots.md)

# Legend

- [Function legend - Show formulas for multiple functions](./function-legend.md)


Color gradients

- [CMasher: Scientific colormaps for making accessible, informative and cmashing plots — CMasher documentation](https://cmasher.readthedocs.io/)

## Layout multiple subfigures

- [Quick start guide — Matplotlib 3.10.0 documentation](https://matplotlib.org/stable/users/explain/quick_start.html#working-with-multiple-figures-and-axes)



---
Sources:
- [Plot (graphics) - Wikipedia](https://en.wikipedia.org/wiki/Plot_(graphics))
- [Graph Terminology | Axis, Range & Scale](https://study.com/academy/lesson/graph-terminology-axis-range-scale.html)

Related:

Tags:
