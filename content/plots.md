---
title: "Plots - Dynamically plot mathematical functions as a vector graphic"
date: "2025-01-06T00:00:00.000+01:00"
dg-publish: true
---

# Native calculation using PGF engine

Calculate function values naively with PGF engine

- 👍 adheres document formatting perfectly
- 👍 No shell escape or external tools necessary
- 👎 limited processing power
 

![figure tikz 2.svg](./attachments/figure-tikz-2.svg)

[PgfPlots calculated by pgf engine](./pgfplots-calculated-by-pgf-engine.md)

# External calculation

Calculate function values externally and draw lines and text in document's style

## Calculate with NumPy and draw with MatLabPlot

- 👍 both NumPy and MatLabPlot are well maintained and have great documentation
- 👍 NumPy calculates very fast
- 👎 some tweaking required to adhere LaTeX's style

![figure plt.svg](./attachments/figure-plt.svg)

[MatPlotLib PyPlot](./matplotlib-pyplot.md)

## Calculate with PostScript and draw with PyX

- 👍 simplest to setup
- 👍 uses LaTeX style by default

![pyx 2.svg](./attachments/pyx-2.svg)

- [PyX](./pyx.md)

## Calculate with GnuPlot and draw with PGF

- [22.6 Plotting a Function Using Gnuplot - Plots of Functions - PGF/TikZ Manual](https://tikz.dev/tikz-plots#autosec-3933)

# Calculate with NumPy, generate PGF instructions, and draw with PGF
