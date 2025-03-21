---
publish: true
dg-permalink: latex
aliases:
  - LaTeX
---
The powerful typesetting system LaTeX is well known in the world of academia, scientific publishing, and technical documentation. While LaTeX mainly gets used to produce pages of PDF, it integrates well as a pre-processing tool to create vector graphics in notes, websites, and documents, too. Guides show how to improve, or generate the following content elements:

[Math - Typeset, align, wrap, comment, enumerate, space out, scale, and style mathematical expressions, utilizing AMSmath](./Math%20-%20Typeset,%20align,%20wrap,%20comment,%20enumerate,%20space%20out,%20scale,%20and%20style%20mathematical%20expressions,%20utilizing%20AMSmath.md)

$$
\begin{align*} \qquad&\hspace{-2em}
\mathbb{P}(X+Y=k) 
= \sum_{\mathclap{x \in X(\Omega)}} \mathbb{P}(X = x) \cdot \mathbb{P}(Y=k-x) \\&
= \sum_{x = 0}^n \binom{n}{x}\, p^x\, (1-p)^{n-x} \cdot \binom{m}{k-x}\, q^{k-x}\, (1-q)^{m-(k-x)}
\end{align*}
$$

[Tables - Separate content in plaintext and styles like alignment, spacing, markup, and calculation, utilizing Tabularray](./Tables%20-%20Separate%20content%20in%20plaintext%20and%20styles%20like%20alignment,%20spacing,%20markup,%20and%20calculation,%20utilizing%20Tabularray.md)

![figure table headers.svg](./attachments/figure%20table%20headers.svg)

[Code Snippets - Print source code with syntax highlighting in latex with listings](./Code%20Snippets%20-%20Print%20source%20code%20with%20syntax%20highlighting%20in%20latex%20with%20listings.md)

![figure code listing.svg](./attachments/figure%20code%20listing.svg)

[Follow varying typographic conventions with the same input syntax](./Follow%20varying%20typographic%20conventions%20with%20the%20same%20input%20syntax.md)

$$
\begin{gather*}
\left( \left( \left( ( ) \sqrt{2}  \right) \right) \right) \quad
\Bigg( \bigg( \Big( ( ) \sqrt{2}  \Big) \bigg) \Bigg) \tag{6a} \\
\frac{235}{711} \quad \tfrac{235}{711} \quad  {^{235} {\!/\!} _{711}} \quad {^{235} \mathclap{\diagup} _{711}} \tag{6b} \\
2.71828\times 10^{3} \quad 2{,}72\cdot 10^{3} \quad 2\,718{,}28 \tag{6c} \\
1 \, \mathrm{kg\, m / s^2} \quad 1 \, \mathrm{kg\, m s^{-2}} \quad 1 \, \mathrm{\tfrac{kg\, m}{s^2} } \tag{6d} \\
1{,}50 \,\text€ \quad \$\, 1.50 \quad 2 \,¥ \quad 1.50 \,\text{GBP} \tag{6e} \\
\text{March 1, 2024 \quad 1. März '24} \tag{6f}
\end{gather*}
$$

[Plots - Dynamically plot mathematical functions, values as a vector graphic](./Plots%20-%20Dynamically%20plot%20mathematical%20functions,%20values%20as%20a%20vector%20graphic.md)

![figure plot tikz collection.svg](./attachments/figure%20plot%20tikz%20collection.svg)

[Networks, Commutative diagrams - Dynamically draw graph networks as a vector graphic](./Networks,%20Commutative%20diagrams%20-%20Dynamically%20draw%20graph%20networks%20as%20a%20vector%20graphic.md)

![figure networks.svg](./attachments/figure%20networks.svg)

[Electrical circuit - Dynamically draw electronic circuit diagrams as a vector graphic](./Electrical%20circuit%20-%20Dynamically%20draw%20electronic%20circuit%20diagrams%20as%20a%20vector%20graphic.md)

![figure circuits.svg](./attachments/figure%20circuits.svg)

[Molecules - Dynamically draw structural formulas of chemical molecules as a vector graphic](./Molecules%20-%20Dynamically%20draw%20structural%20formulas%20of%20chemical%20molecules%20as%20a%20vector%20graphic.md)

![figure molecules.svg](./attachments/figure%20molecules.svg)

Heatmaps

![figure heatmap.svg](./attachments/figure%20heatmap.svg)

[Gantt chart](./Gantt%20chart.md)

![figure gantt portfolio examination 2.svg](./attachments/figure%20gantt%20portfolio%20examination%202.svg)

Roadmap for further data visualizations

- spiderweb diagram
- Fractals
- Public transport map
- (trail) Maps
- orbital paths
- engineering blueprint
- Minecraft blueprint
- Factorio blueprint
- music notes
- timeline
- geographic maps with transparent circles
- low-poly art

Roadmap for setup comparisons

- writing, conversion, lint, debug
- which editor comparison
- Don't spent so much time on your setup, start writing code
- alternative markup systems

Learn, Troubleshoot, Debugging/Help/Documentation
- keep package number low
- don't create macros
- problem with text, quotes, math, tables, images, floats, listings, layout, development, setup, conversion, compile time, plots, graphics, citations
- [Learn and troubleshoot LaTeX - Read (package) documentation, cheat sheets, tutorials](./Learn%20and%20troubleshoot%20LaTeX%20-%20Read%20(package)%20documentation,%20cheat%20sheets,%20tutorials.md)
- [Develop LaTeX packages](./Develop%20LaTeX%20packages.md)

Other topics

- [Values  - Standardize math, numbers, symbols, quantities, money](./Values%20%20-%20Standardize%20math,%20numbers,%20symbols,%20quantities,%20money.md)
- [Float - Dynamically place figures, images, tables, and listings at the top, bottom, or single page](./Float%20-%20Dynamically%20place%20figures,%20images,%20tables,%20and%20listings%20at%20the%20top,%20bottom,%20or%20single%20page.md)
- [Graphics, Plots, Visualization - Generate dynamic professional vector graphics with matching fonts, design](./Graphics,%20Plots,%20Visualization%20-%20Generate%20dynamic%20professional%20vector%20graphics%20with%20matching%20fonts,%20design.md)
- [Project structure - Create folders for setup, resources, bibliographies](./Project%20structure%20-%20Create%20folders%20for%20setup,%20resources,%20bibliographies.md)
- [Graphical elements - Standardize tables, images, plots](./Graphical%20elements%20-%20Standardize%20tables,%20images,%20plots.md)
- [Layout the document - Setup margins, hyphenation, table of contents](./Layout%20the%20document%20-%20Setup%20margins,%20hyphenation,%20table%20of%20contents.md)

Color gradients
- [Color gradients and my gradual descent into madness – Typst Blog](https://typst.app/blog/2023/color-gradients/)

Animation
- [GitHub - ManimCommunity/manim: A community-maintained Python framework for creating mathematical animations.](https://github.com/ManimCommunity/manim/)

Motivation and use cases for LaTeX

---
Sources:
- 2023-06-19: [How I'm able to take notes in mathematics lectures using LaTeX and Vim | Gilles Castel](https://castel.dev/post/lecture-notes-1/)
- [The LaTeX fetish (Or: Don’t write in LaTeX! It’s just for typesetting) – Daniel Allington](http://www.danielallington.net/2016/09/the-latex-fetish/)

Related:
```dynamic-embed
[[List related notes]]
``` 

Tags:
[Markup and typesetting systems - Produce printed or digital documents aesthetically pleasing with readable typography](./Markup%20and%20typesetting%20systems%20-%20Produce%20printed%20or%20digital%20documents%20aesthetically%20pleasing%20with%20readable%20typography.md)
