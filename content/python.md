---
title: "Python"
dg-publish: true
not-in-use: 
microsoft-id: 
winget-id: Python.Python.3.13
github-repo: 
github-release-filename: 
website: https://www.python.org/downloads/
priority: 
link-modportals:
  - <pre><code class='language-powershell'>pip install ~modportal0-id~</code></pre>
modportal0-id: 
thumbnail: 
categories:
  - Development
synopsis: Python is a high-level, versatile programming language known for its clean syntax and readability, making it popular for everything from web development to data science and artificial intelligence.
extends-app: 
cssclasses:
  - cards
dg-content-classes:
  - cards
---

Python is a [development](install%20development%20apps.md.md) app. Python is a high-level, versatile programming language known for its clean syntax and readability, making it popular for everything from web development to data science and artificial intelligence.

- Invoke the installer listed on Windows Package Manager:
  ```powershell
  winget install -e Python.Python.3.13
  ```
- Download it from the [publisher's website](https://www.python.org/downloads/)


Troubleshoot PATH setup
- [List all apps in PATH locations](./list%20all%20apps%20in%20path%20locations.md)

Find newest version
```powershell
winget search Python.Python
```

Install python in system-wide `%ProgramFiles%`
- Package installation will have to be privileged as well
```powershell
winget install -e Python.Python.3.13 --scope machine
```

| Name                                                 | Thumbnail                                                                    | Modportal links                                                                  | Categories    | Description                                                                     |
| ---------------------------------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ------------- | ------------------------------------------------------------------------------- |
| **[PyX](./pyx.md)**                             | ![](https://pyx-project.org/pyxlogo.png)                                     | <pre><code class='language-powershell'>pip install PyX</code></pre>              | Visualisation | Generate PDF, SVG graphics with LaTeX drawn text and PostScript drawing backend |
| **[MatPlotLib PyPlot](./matplotlib%20pyplot.md)** | ![](https://upload.wikimedia.org/wikipedia/commons/8/84/Matplotlib_icon.svg) | <pre><code class='language-powershell'>pip install matplotlib</code></pre>       | Visualisation | Generate GUI, SVG, PDF figures with an implicit, MATLAB-like interface          |
| **[Plotly Python](./plotly%20python.md)**         | ![](https://avatars.githubusercontent.com/u/5997976?s=280&v=4)               | <pre><code class='language-powershell'>pip install plotly==6.0.0rc0</code></pre> | Visualisation | Generate interactive, publication-quality graphs                                |

