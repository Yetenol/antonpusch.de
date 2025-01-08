---
title: "Spines - Place axis spines of plots"
date: "2025-01-08T00:00:00.000+01:00"
dg-publish: true
---

Default spine

![plot spine default.svg](./attachments/plot-spine-default.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'savefig.transparent':True, 'svg.fonttype':'none',
    'figure.constrained_layout.use':True, 'axes.titlesize': 10,
    'axes.grid':True, 'grid.linestyle':':'})
def plot_with_default_spines(axes):
    x = np.linspace(0, 2.5, 100)
    axes.set_title("Figure 1.1: Default spines")
    axes.set_xlabel("x")
    axes.plot(x, np.cos(np.pi*x)*np.exp(-x), 
        label=r"$f(x) = \frac{\cos(\pi x)}{e^x}$")
    axes.legend()

fig, axs = plt.subplots(figsize=(6,2.2))
plot_with_default_spines(axs)
plt.savefig(@vault_path + '/attachments/plot spine default.svg')
plt.show()
```

Left and bottom spine

![plot spine left bottom.svg](./attachments/plot-spine-left-bottom.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'savefig.transparent':True, 'svg.fonttype':'none',
    'figure.constrained_layout.use':True, 'axes.titlesize': 10,
    'axes.grid':True, 'grid.linestyle':':'})
def plot_with_left_and_bottom_spine(axes):
    x = np.linspace(0, 2.5, 100)
    axes.set_title("Figure 1.2: Left, bottom spine")
    axes.set_xlabel("x")
    axes.plot(x, np.cos(np.pi*x)*np.exp(-x), 
        label=r"$f(x) = \frac{\cos(\pi x)}{e^x}$")
    axes.legend()
    axes.spines[['right', 'top']].set_visible(False)

fig, axs = plt.subplots(figsize=(6,2.2))
plot_with_left_and_bottom_spine(axs)
plt.savefig(@vault_path + '/attachments/plot spine left bottom.svg')
plt.show()
```

Spines through origin

![plot spine origin.svg](./attachments/plot-spine-origin.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'savefig.transparent':True, 'svg.fonttype':'none',
    'figure.constrained_layout.use':True, 'axes.titlesize': 10,
    'axes.grid':True, 'grid.linestyle':':'})
def plot_with_spines_at_zero(axes):
    x = np.linspace(0, 2.5, 100)
    axes.set_title("Figure 1.3: Spines through origin")
    axes.set_xlabel("x")
    axes.plot(x, np.cos(np.pi*x)*np.exp(-x), 
        label=r"$f(x) = \frac{\cos(\pi x)}{e^x}$")
    axes.legend()
    axes.spines[['right', 'top']].set_visible(False)
    axes.spines[['left', 'bottom']].set_position('zero')

fig, axs = plt.subplots(figsize=(6,2.2))
plot_with_spines_at_zero(axs)
plt.savefig(@vault_path + '/attachments/plot spine origin.svg')
plt.show()
```

# Figure collection for note preview

See [figures for print documents (PDF)](./attachments/plot-spines.pdf) or figures for displays:

![plot spines.svg](./attachments/plot-spines.svg)

```python
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'savefig.transparent':True, 'svg.fonttype':'none',
    'figure.constrained_layout.use':True, 'axes.titlesize': 10,
    'axes.grid':True, 'grid.linestyle':':'})
def plot_with_default_spines(axes):
    x = np.linspace(0, 2.5, 100)
    axes.set_title("Figure 1.1: Default spines")
    axes.set_xlabel("x")
    axes.plot(x, np.cos(np.pi*x)*np.exp(-x), 
        label=r"$f(x) = \frac{\cos(\pi x)}{e^x}$")
    axes.legend()
def plot_with_left_and_bottom_spine(axes):
    x = np.linspace(0, 2.5, 100)
    axes.set_title("Figure 1.2: Left,\n bottom spine")
    axes.set_xlabel("x")
    axes.plot(x, np.cos(np.pi*x)*np.exp(-x), 
        label=r"$f(x) = \frac{\cos(\pi x)}{e^x}$")
    axes.legend()
    axes.spines[['right', 'top']].set_visible(False)
def plot_with_spines_at_zero(axes):
    x = np.linspace(0, 2.5, 100)
    axes.set_title("Figure 1.3: Spines\n through origin")
    axes.set_xlabel("x")
    axes.plot(x, np.cos(np.pi*x)*np.exp(-x), 
        label=r"$f(x) = \frac{\cos(\pi x)}{e^x}$")
    axes.legend()
    axes.spines[['right', 'top']].set_visible(False)
    axes.spines[['left', 'bottom']].set_position('zero')

fig, axs = plt.subplots(ncols=3, figsize=(6,2.2))
plot_with_default_spines(axs[0])
plot_with_left_and_bottom_spine(axs[1])
plot_with_spines_at_zero(axs[2])
plt.savefig(@vault_path + '/attachments/plot spines.svg')

# Redraw figure for print documents
plt.rcParams.update({'text.usetex':True, 'font.family':'serif'})
plt.clf()
fig, axs = plt.subplots(ncols=3, figsize=(6,2.2))
plot_with_default_spines(axs[0])
plot_with_left_and_bottom_spine(axs[1])
plot_with_spines_at_zero(axs[2])
plt.savefig(@vault_path + '/attachments/plot spines.pdf')
plt.show()
```


[Other spine plots](Other%20spine%20plots.md)
