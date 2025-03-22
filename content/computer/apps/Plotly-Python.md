---
date: "2025-03-22T23:45:55.022+01:00"
title: "Plotly Python"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: 
microsoft-id: 
winget-id: 
github-repo: plotly/plotly.py
github-release-filename: 
website: https://plotly.com/python/
priority: 
link-modportals: 
modportal0-id: plotly==6.0.0rc0
thumbnail: https://avatars.githubusercontent.com/u/5997976?s=280&v=4
categories:
  - Visualisation
synopsis: Generate interactive, publication-quality graphs
extends-app: "[[Python|Python]]"
---

```dynamic-embed
[[Describe this app and list installation sources]]
```
![plotly 1.svg](plotly%201.svg)

```python
import plotly.graph_objects as go
import numpy as np
np.random.seed(1)

N = 100
x = np.random.rand(N)
y = np.random.rand(N)
colors = np.random.rand(N)
sz = np.random.rand(N) * 30

fig = go.Figure()
fig.add_trace(go.Scatter(    x=x,    y=y,    mode="markers",    marker=go.scatter.Marker(        size=sz,        color=colors,        opacity=0.6,        colorscale="Viridis"    )))

fig.show()
fig.write_image("plotly.svg")
```

[plotly 1.pdf](plotly%201.pdf)

```python
import plotly.express as px
fig = px.bar(x=["a", "b", "c"], y=[1, 3, 2])
fig.show()
```