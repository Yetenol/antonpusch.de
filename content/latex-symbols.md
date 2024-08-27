---
title: "LaTeX Symbols - Lookup mathematical symbols, operations, relations, and arrows"
dg-publish: true
dg-show-toc: true
dg-permalink: latex-symbols
priority: 1
---

# Relations

| Positive relation                                    | negated                     |
| ---------------------------------------------------- | --------------------------- |
| $=$ <code>=</code>                                   | $\ne$ `\ne`, `\neq`         |
| $\approx$ `\approx`                                  | $\not\approx$ `\not\approx` |
| $<$ `<`                                              | $\nless$ `\nless`           |
| $>$ `>`                                              | $\ngtr$ `\ngtr`             |
| $\le$ `\le`, `\leq`                                  | $\nleq$ `\nleq`             |
| $\ge$ `\ge`, `\geq`                                  | $\ngeq$ `\ngeq`             |
| $\triangleq$ `\triangleq`<br>$\coloneqq$ `\coloneqq` |                             |
| $\equiv$ `\equiv`                                    | $\not\equiv$ `\not\equiv`   |
| $\in$ `\in`                                          | $\notin$ `\notin`           |
| $\ni$ `\ni`                                          | $\not\ni$ `\not\ni`[^1]     |
| $\subset$ `\subset`                                  | $\not\subset$ `\not\subset` |
| $\supset$ `\supset`                                  | $\not\supset$ `\not\supset` |
| $\subseteq$ `\subseteq`                              | $\nsubseteq$ `\nsubseteq`   |
| $\supseteq$ `\supseteq`                              | $\nsupseteq$ `\nsupseteq`   |
| $\sim$ `\sim`                                        | $\nsim$ `\nsim`             |
| $\ll$ `\ll`                                          | $\not\ll$ `\not\ll`         |
| $\gg$ `\gg`                                          | $\not\gg$ `\not\gg`         |

| Logic/Extensible Arrow                                                                 | negated                                                                                                                        |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| $\implies$ `\implies`<br>$\;\xRightarrow{xxx}\;$ `\;\xRightarrow{xxx}\;`               | $\;=\!\nRightarrow\;$ `\;=\!\nRightarrow\;`<br>$\!\!\mathrlap{\quad\not}\implies$ `\mathrlap{\quad\not}\implies`               |
| $\impliedby$ `\impliedby`<br>$\;\xLeftarrow{xxx}\;$ `\;\xLeftarrow{xxx}\;`<br>         | $\;\nLeftarrow\!=\;$ `\;\nLeftarrow\!=\;`<br>$\!\!\mathrlap{\quad\not}\impliedby$ `\mathrlap{\quad\not}\impliedby`<br>         |
| $\iff$ `\iff`<br>$\;\xLeftrightarrow{xxx}\;$ `\;\xLeftrightarrow{xxx}\;`<br>           | $\;\Leftarrow\!\nRightarrow\;$ `\;\Leftarrow\!\nRightarrow\;`<br>$\!\!\mathrlap{\quad\not}\iff$ `\mathrlap{\quad\not}\iff`<br> |
| $\to$ `\to`<br>$\xrightarrow[yyy]{xxx}$ `\xrightarrow[yyy]{xxx}`                       | $\nrightarrow$ `\nrightarrow`                                                                                                  |
| $\gets$ `\gets`<br>$\xleftarrow{xxx}$ `\xleftarrow{xxx}`                               | $\nleftarrow$ `\nleftarrow`                                                                                                    |
| $\leftrightarrow$ `\leftrightarrow`<br>$\xleftrightarrow{xxx}$ `\xleftrightarrow{xxx}` | $\nleftrightarrow$ `\nleftrightarrow`                                                                                          |
| $\xlongequal{xxx}$ `\xlongequal{xxx}`                                                  |                                                                                                                                |
| $\xmapsto{xxx}$ `\xmapsto{xxx}`                                                        |                                                                                                                                |

| Regular Arrow                                                                                       | another                                                                                     |
| --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| $\circlearrowright$ `\circlearrowright`                                                             | $\circlearrowleft$ `\circlearrowleft`                                                       |
| $\curvearrowright$ `\curvearrowright`                                                               | $\curvearrowleft$ `\curvearrowleft`                                                         |
| $\Rsh$ `\Rsh`                                                                                       | $\Lsh$ `\Lsh`                                                                               |
| $\to$ `\to`<br>$\longrightarrow$ `\longrightarrow`<br>$\dashrightarrow$ `\dashrightarrow`           | $\gets$ `\gets`<br>$\longleftarrow$ `\longleftarrow`<br>$\dashleftarrow$ `\dashleftarrow`   |
| $\leftrightarrow$ `\leftrightarrow`<br>$\longleftrightarrow$ `\longleftrightarrow`                  | $\updownarrow$ `\updownarrow`<br>                                                           |
| $\nearrow$ `\nearrow`                                                                               | $\searrow$ `\searrow`                                                                       |
| $\downarrow$ `\downarrow`                                                                           | $\uparrow$ `\uparrow`                                                                       |
| $\nwarrow$ `\nwarrow`                                                                               | $\swarrow$ `\swarrow`                                                                       |
| $\Rightarrow$ `\Rightarrow`<br>$\Longrightarrow$ `\Longrightarrow`<br>$\implies$ `\implies`         | $\Leftarrow$ `\Leftarrow`<br>$\Longleftarrow$ `\Longleftarrow`<br>$\impliedby$ `\impliedby` |
| $\Downarrow$ `\Downarrow`                                                                           | $\Uparrow$ `\Uparrow`                                                                       |
| $\Leftrightarrow$ `\Leftrightarrow`<br>$\Longleftrightarrow$ `\Longleftrightarrow`<br>$\iff$ `\iff` | $\Updownarrow$ `\Updownarrow`                                                               |

See more relations in external resources
- [Relation Symbols](https://www.cmor-faculty.rice.edu/~heinken/latex/symbols.pdf#page=2) from LaTeX math symbols
- Packages for [Relations p. 67](https://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf#page=69) or [Arrows p. 94](https://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf#page=96) from Comprehensive LaTeX Symbol List
- [Arrows](https://katex.org/docs/supported#arrows) from KaTeX docs; [Arrows](https://www.cmor-faculty.rice.edu/~heinken/latex/symbols.pdf#page=3) from LaTeX math symbols

Generically negate/comment any relation
- negate $\not\equiv$ `\not\equiv`
- comment $\overset{\text{def}}{=}$ `\overset{\text{def}}{=}`, and see [Comment equation operators](Comment%20equation%20operators.md)

# Operators

| Operator                                                                 | another                                                        |
| ------------------------------------------------------------------------ | -------------------------------------------------------------- |
| $+$ `+`                                                                  | $-$ `-`                                                        |
| $\cdot$ `\cdot`<br>$\times$ `\times`                                     | $/$ `/`<br>$\div$ `\div`                                       |
| $:$ `:`                                                                  | $^\circ$ `^\circ`                                           |
| $\mid$ `\mid`                                                            | $\parallel$ `\parallel`                                        |
| $\cup$ `\cup`                                                            | $\cap$ `\cap`                                                  |
| $\setminus$ `\setminus`                                                  | $\neg$ `\neq`, `lnot`                                          |
| $\land$ `\land`, `\wedge`                                                | $\lor$ `\lor`, `\vee`                                          |
| $\pm$ `\pm`<br>$\mp$ `\mp`                                               | $\Join$ `\Join` [^2]                                           |
| $\Im$ `\Im` imaginary                                                    | $\Re$ `\Re` real                                               |
| $\displaystyle\sum$ `sum`                                                | $\displaystyle\prod$ `\prod`                                   |
| $\displaystyle\int$ `\int`<br>$\displaystyle\oint$ `\oint`               | $\displaystyle\iint$ `\iint`<br>$\displaystyle\iiint$ `\iiint` |
| $\displaystyle\bigcup$ `\bigcup`<br>$\displaystyle\biguplus$ `\biguplus` | $\displaystyle\bigcap$ `\bigcap`                               |
| $\displaystyle\bigwedge$ `\bigwedge`                                     | $\displaystyle\bigvee$ `\bigvee`                               |

$$
\begin{gather*}
\min\, \max\, \log  \ln  \det  \lim \tag{1a} \\
\sin\, \cos\, \tan\, \arcsin\, \arccos\, \arctan \tag{1b} \\
x \sin \alpha,\, x \sin(\alpha),\, \sin^2\alpha, \cancel{x\mathrm{sin}x,\,  x sin() x} \tag{1c} \\
\lim_{a \to \infty}\, \lim\nolimits_{a \to \infty};\; 
{\textstyle \sum_0^\infty \sum\limits_0^\infty};\; 
\operatorname{pre-norm}()\, \mathop{\mathbb{P}_0}_a^b()  \tag{1d}
\end{gather*}
$$

See more operators in external resources
- [Operators](https://katex.org/docs/supported#operators) or [Big operators](https://katex.org/docs/supported.html#big-operators) from KaTeX docs
- Packages for [Operators p. 37](https://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf#page=39) from Comprehensive LaTeX Symbol List
- [Operator names ch. 2.12 p. 66](https://www.tug.org/~hvoss/PDF/mathmode.pdf#page=72) or create custom big operator [mathchar ch. 3.2.7 p. 79](https://www.tug.org/~hvoss/PDF/mathmode.pdf#page=85) from Mathematical Typsetting with LaTeX by H. Voß

Operators with **function name**
- Use predefined operators `\min` - `\sin` - etc., see $\mathrm{(1a\text{-}b)}$ 
- [p] Proper operators get **correct** right and left **spacing** compared to last two examples, see $\mathrm{(1c)}$
- Create custom operator with text name `\operatorname{pre-norm}()` or math name `\mathop{\mathbb{P}_0}_a^b()`, see end of $\mathrm{(1d)}$

Use **limits**, or exponents and indices $\mathrm{(1d)}$
- **Display mode** defaults to **limits**; to force exponents and indices `\lim\nolimits_0^1`
- **Text mode** defaults to **exponents** and **indices**; to force limits `\sum\limits_0^1`
- See [Layout multiple equations](./layout%20multiple%20equations.md)

# Greek Letters

| Lower Case                                            | Upper Case                                           |
| ----------------------------------------------------- | ---------------------------------------------------- |
| $\alpha$ `\alpha`                                     | $\mathrm{A}$ `A`                                     |
| $\beta$ `\beta`                                       | $\mathrm{B}$ `B`                                     |
| $\gamma$ `\gamma`                                     | $\Gamma$ `\Gamma`<br>$\varGamma$ `\varGamma`         |
| $\delta$ `\delta`                                     | $\Delta$ `\Delta`<br>$\varDelta$ `\varDelta`         |
| $\varepsilon$ `\varepsilon` <br>$\epsilon$ `\epsilon` | $\mathrm{E}$ `E`                                     |
| $\zeta$ `\zeta`                                       | $\mathrm{Z}$ `Z`                                     |
| $\eta$ `\eta`                                         | $\mathrm{H}$ `H`                                     |
| $\theta$ `\theta` <br>$\vartheta$ `\vartheta`         | $\Theta$ `\Theta`<br>$\varTheta$ `\varTheta`         |
| $\iota$ `\iota`                                       | $\mathrm{I}$ `I`                                     |
| $\kappa$ `\kappa` <br>$\varkappa^1$ `\varkappa`       | $\mathrm{K}$ `K`                                     |
| $\lambda$ `\lambda`                                   | $\Lambda$ `\Lambda`<br>$\varLambda$ `\varLambda`     |
| $\mu$ `\mu`                                           | $\mathrm{M}$ `M`                                     |
| $\nu$ `\nu`                                           | $\mathrm{N}$ `N`                                     |
| $\xi$ `\xi`                                           | $\Xi$ `\Xi`<br>$\varXi$ `\varXi`                     |
| $o$ `o`                                               | $\mathrm{O}$ `O`                                     |
| $\pi$ `\pi`<br>$\varpi$ `\varpi`                      | $\Pi$ `\Pi`<br>$\varPi$ `\varPi`                     |
| $\rho$ `\rho`<br>$\varrho$ `\varrho`                  | $\mathrm{P}$ `P`                                     |
| $\sigma$ `\sigma`<br>$\varsigma$ `\varsigma`          | $\Sigma$ `\Sigma`<br>$\varSigma$ `\varSigma`         |
| $\tau$ `\tau`                                         | $\mathrm{T}$ `T`                                     |
| $\upsilon$ `\upsilon`                                 | $\Upsilon$ `\Upsilon`<br>$\varUpsilon$ `\varUpsilon` |
| $\varphi$ `\varphi`<br>$\phi$ `\phi`                  | $\Phi$ `\Phi`<br>$\varPhi$ `\varPhi`                 |
| $\chi$ `\chi`                                         | $\mathrm{X}$ `X`                                     |
| $\psi$ `\psi`                                         | $\Psi$ `\Psi`<br>$\varPsi$ `\varPsi`                 |
| $\omega$ `\omega`                                     | $\Omega$ `\Omega`<br>$\varOmega$ `\varOmega`         |
| $\digamma$ `\digamma` [^3]                            |                                                      |

# Delimiters

$$
\begin{gather*}
(x)  \left( \sqrt{2} \right) &
\left. e^{x^2}  \right\uparrow \vphantom{\Bigg)} &
\left\{ x \;\middle|\; x > \frac{1}{2} \right\} \tag{2a,\,2b,\,2c} \\
( \big( \Big( \bigg( \Bigg( &
\begin{bmatrix} a&b\\c&d \end{bmatrix} \vphantom{\Bigg)} &
\left[ \begin{smallmatrix} a&b\\c&d \end{smallmatrix} \right] \tag{2d,\,2e,\,2f}
\end{gather*}
$$

- Use **default** size `(`…`)` or **auto** scale to enclosed content `\left(`…`\right)`, see $\mathrm{(2a)}$ 
- Enclose with a **blank** delimiter `\left.`…`\right\uparrow`, see $\mathrm{(2b)}$ 
- Enclose with a **middle** delimiter `\left\{`…`\;\middle\vert\;`…`\right\}`, see $\mathrm{(2c)}$ 
- **Manually** set size `\big(` -  `\Big(` - `\bigg(` - `\Bigg(`, see $\mathrm{(2d)}$ 
- Use matrix with auto scaled delimiters: `\begin{matrix} a&b\\c&d \end{matrix}`, see $\mathrm{(2e)}$ 
  $(\,)$ pmatrix - $[\, ]$ bmatrix - $\{\,\}$ Bmatrix - $\vert\,\vert$ vmatrix - $\Vert\,\Vert$ Vmatrix
- Use smaller matrix variant, see $\mathrm{(2f)}$:
```
\left[ \begin{smallmatrix} a&b\\c&d \end{smallmatrix} \right]
```

$$
(\, )\; \lgroup\,\rgroup\; [\,]\; \{\,\}\;  \vert\,\vert\; \Vert\, \Vert\; \lfloor\,\rfloor\; \lceil\,\rceil\; \langle\,\rangle\; \ulcorner\,\urcorner\; \llcorner\,\lrcorner\; \uparrow\,\downarrow\; \updownarrow\,\Updownarrow\; \Uparrow\,\Downarrow
$$

| Math                                                  | Markup                                         |
| ----------------------------------------------------- | ---------------------------------------------- |
| $(x), \binom{n}{k},{n \choose k}$                     | `(`…`)` - <br>`\binom{n}{k}` - `{n \choose k}` |
| $\lgroup x\rgroup$                                    | `\lgroup`…`\rgroup`                            |
| $[x],  {n \brack k}$                                  | `[`…`]` - <br>`{n \brack k}`                   |
| $\{x\}, {n \brace k}$                                 | `\{`…`\}` - <br>`{n \brace k}`                 |
| $\vert x\vert$                                        | `\vert`…`\vert`                                |
| $x \mid  x \in \mathbb{N}$                            | …`\mid`…                                       |
| $\left\{ x \;\middle\vert\; x > \frac{1}{2} \right\}$ | `\left\{`…`\;\middle\vert\;`…`\right\}`        |
| $\Vert \vec{x} \Vert$                                 | `\Vert`…`\Vert`                                |
| $AB \parallel CD$                                     | …`\parallel`…                                  |
| $\lfloor x \rfloor$                                   | `\lfloor`…`\rfloor`                            |
| $\lceil x \rceil$                                     | `\lceil`…`\rceil`                              |
| $\langle x \rangle$                                   | `\langle`…`\rangle`                            |

See more delimiters in external resources
- [Delimiters](https://katex.org/docs/supported#delimiters) from KaTeX docs

---

# Non-Mathematical Symbols

These symbols can also be used in text mode.

| Command                                 | Rendering      | Name or _Function_                   | Usage Example                                                 |
| --------------------------------------- | -------------- | ------------------------------------ | ------------------------------------------------------------- |
| `-`                                     | -              | hyphen                               | daughter-in-law, X-rated                                      |
| `--`                                    | –              | en-dash                              | pages 13–67                                                   |
| `---`                                   | —              | em-dash                              | yes—or no?                                                    |
| `$-1$`                                  | −              | minus-sign                           | 0, 1 and −1                                                   |
| `/`                                     | /              | _prevents hyphenation_               | 5 MB/s                                                        |
| `\slash{}`                              | /              | _supports hyphenation_               | read/write                                                    |
| `\ldots{}`                              | …              | ellipsis                             | a, b, c, …                                                    |
| `Mr.~Smith`                             | Mr.&#160;Smith | _suppresses bigger sentence spacing_ | Did ⠀Mr.&#160;Smith ⠀win ⠀today?                              |
| `\dag{}`                                | †              | Dagger                               |                                                               |
| `\ddag{}`                               | ‡              | Double Dagger                        |                                                               |
| `\S{}`                                  | §              | Section Sign                         |                                                               |
| `\P{}`                                  | ¶              | Pilcrow Sign                         |                                                               |
| `\%{}`                                  | %              | Percent Sign                         |                                                               |
| `\textsuperscript{\textcopyright}`      | ©              | Copyright Sign                       |                                                               |
| `\textsuperscript{\textregistered}`     | ®              | Registered Trade Mark Sign           |                                                               |
| `\texttrademark{}`                      | ™              | Trade Mark Sign                      |                                                               |
| `\unit{\degree}` <br> `\textdegree{}`   | °              | Degree Sign                          | [siunitx](https://texdoc.org/serve/siunitx/0) <br> _built in_ |
| `\ang{5}`                               | 5°             | Angle                                | [siunitx](https://texdoc.org/serve/siunitx/0)                 |
| `\unit{\celsius}` <br> `\textcelsius{}` | ℃              | Degree Celsius                       | [siunitx](https://texdoc.org/serve/siunitx/0) <br> _built in_ |
| `\qty{5}{\celsius}`                     | 5 ℃            |                                      | [siunitx](https://texdoc.org/serve/siunitx/0)                 |

# Money and currencies

`€`, `\$`, `pounds` and `\yen` are not recommended

| Command      | Rendering | Dependency                                                                                       |         |
| ------------ | --------- | ------------------------------------------------------------------------------------------------ | ------- |
| `\cEUR{}`    | €         | [currency](https://texdoc.org/serve/currency/0) + [ setup](Standardize%20currencies%20and%20monetary%20values%20-.md) |
| `\cUSD{}`    | $         | [currency](https://texdoc.org/serve/currency/0) + [ setup](Standardize%20currencies%20and%20monetary%20values%20-.md) |
| `\cJPY{}`    | ¥         | [currency](https://texdoc.org/serve/currency/0) + [ setup](Standardize%20currencies%20and%20monetary%20values%20-.md) |
| `\cGBP{}`    | £         | [currency](https://texdoc.org/serve/currency/0) + [ setup](Standardize%20currencies%20and%20monetary%20values%20-.md) |
| `\dEUR{1.5}` | 1.50 €    | [currency](https://texdoc.org/serve/currency/0) + [ setup](Standardize%20currencies%20and%20monetary%20values%20-.md) |
| `\dUSD{1.5}` | $ 1.50    | [currency](https://texdoc.org/serve/currency/0) + [ setup](Standardize%20currencies%20and%20monetary%20values%20-.md) |
| `\dJPY{1.5}` | 2 ¥       | [currency](https://texdoc.org/serve/currency/0) + [ setup](Standardize%20currencies%20and%20monetary%20values%20-.md) |
| `\dGBP{1.5}` | £ 1.50    | [currency](https://texdoc.org/serve/currency/0) + [ setup](Standardize%20currencies%20and%20monetary%20values%20-.md) |

# Degree Symbols

| Command           | Rendering        | Dependency         |
| ----------------- | ---------------- | ------------------ |
| `^\circ`          | $^\circ$         |                    |
| `\unit{\degree}`  | $^\circ$         | [siunitx](https://texdoc.org/serve/siunitx/0) |
| `\unit{\celsius}` | $^\circ\text{C}$ | [siunitx](https://texdoc.org/serve/siunitx/0) |

# Math Mode Accents

| Command           | Rendering         |
| ----------------- | ----------------- |
| `\acute{a}`       | $\acute{a}$       |
| `\bar{a}`         | $\bar{a}$         |
| `\breve{a}`       | $\breve{a}$       |
| `\check{a}`       | $\check{a}$       |
| `\ddot{a}`        | $\ddot{a}$        |
| `\dot{a}`         | $\dot{a}$         |
| `\grave{a}`       | $\grave{a}$       |
| `\hat{a}`         | $\hat{a}$         |
| `\mathring{a}`    | $\mathring{a}$    |
| `\tilde{a}`       | $\tilde{a}$       |
| `\vec{a}`         | $\vec{a}$         |
| `\widehat{AAA}`   | $\widehat{AAA}$   |
| `\widetilde{AAA}` | $\widetilde{AAA}$ |

Set the **style** of the letter in the preamble

| Preamble Command                       | Rendering     | Original   | Dependency                                    |
| -------------------------------------- | ------------- | ---------- | --------------------------------------------- |
| `\renewcommand{\epsilon}{\varepsilon}` | $\varepsilon$ | $\epsilon$ |                                               |
| `\renewcommand{\theta}{\vartheta}`     | $\vartheta$   | $\theta$   |                                               |
| `\renewcommand{\kappa}{\varkappa}`     | $\varkappa$   | $\kappa$   | [amssymb](https://texdoc.org/serve/amssymb/0) |
| `\renewcommand{\pi}{\varpi}`           | $\varpi$      | $\pi$      |                                               |
| `\renewcommand{\rho}{\varrho}`         | $\varrho$     | $\rho$     |                                               |
| `\renewcommand{\sigma}{\varsigma}`     | $\varsigma$   | $\sigma$   |                                               |
| `\renewcommand{\phi}{\varphi}`         | $\varphi$     | $\phi$     |                                               |

# Hebrew Letters

| Command   | Rendering | Dependency         |
| --------- | --------- | ------------------ |
| `\beth`   | $\beth$   | [amssymb](https://texdoc.org/serve/amssymb/0) |
| `\gimel`  | $\gimel$  | [amssymb](https://texdoc.org/serve/amssymb/0) |
| `\daleth` | $\daleth$ | [amssymb](https://texdoc.org/serve/amssymb/0) |

# Number sets

| Command      | Rendering    |
| ------------ | ------------ |
| `\mathbb{A}` | $\mathbb{A}$ |
| `\mathbb{C}` | $\mathbb{C}$ |
| `\mathbb{H}` | $\mathbb{H}$ |
| `\mathbb{N}` | $\mathbb{N}$ |
| `\mathbb{O}` | $\mathbb{O}$ |
| `\mathbb{Q}` | $\mathbb{Q}$ |
| `\mathbb{R}` | $\mathbb{R}$ |
| `\mathbb{S}` | $\mathbb{S}$ |
| `\mathbb{Z}` | $\mathbb{Z}$ |
|              |              |

# Favorites

| Command      | Rendering    |
| ------------ | ------------ |
| `\lnot`      | $\lnot$      |
| `\land`      | $\land$      |
| `\lor`       | $\lor$       |
| `\to`        | $\to$        |
| `\gets`      | $\gets$      |
| `\iff`       | $\iff$       |
| `\implies`   | $\implies$   |
| `\impliedby` | $\impliedby$ |
| `\mathbb{R}` | $\mathbb{R}$ |
| `\approx`    | $\approx$    |
| `\subseteq`  | $\subseteq$  |
| `\supseteq`  | $\supseteq$  |
| `\setminus`  | $\setminus$  |
| `\times`     | $\times$     |
| `\leq`       | $\leq$       |
| `\geq`       | $\geq$       |
| `\cap`       | $\cap$       |
| `\cup`       | $\cup$       |

# Arrows as Accents

| Command                    | Rendering                  |
| -------------------------- | -------------------------- |
| `\overrightarrow{AB}`      | $\overrightarrow{AB}$      |
| `\underrightarrow{AB}`     | $\underrightarrow{AB}$     |
| `\overleftarrow{AB}`       | $\overleftarrow{AB}$       |
| `\underleftarrow{AB}`      | $\underleftarrow{AB}$      |
| `\overleftrightarrow{AB}`  | $\overleftrightarrow{AB}$  |
| `\underleftrightarrow{AB}` | $\underleftrightarrow{AB}$ |

# Delimiters

# Large Delimiters

| Command       | Rendering     |
| ------------- | ------------- |
| `\lgroup`     | $\lgroup$     |
| `\rgroup`     | $\rgroup$     |
| `\lmoustache` | $\lmoustache$ |
| `\arrowvert`  | $\arrowvert$  |
| `\Arrowvert`  | $\Arrowvert$  |
| `\bracevert`  | $\bracevert$  |
| `\rmoustache` | $\rmoustache$ |

# Miscellaneous Symbols

| Command              | Rendering            | Variants       | Dependency                                      |
| -------------------- | -------------------- | -------------- | ----------------------------------------------- |
| `\dots`              | $\dots$              |                |                                                 |
| `\cdots`             | $\cdots$             |                |                                                 |
| `\vdots`             | $\vdots$             |                |                                                 |
| `\ddots`             | $\ddots$             |                |                                                 |
| `\hbar`              | $\hbar$              |                |                                                 |
| `\imath`             | $\imath$             |                |                                                 |
| `\jmath`             | $\jmath$             |                |                                                 |
| `\ell`               | $\ell$               |                |                                                 |
| `\Re`                | $\Re$                |                |                                                 |
| `\Im`                | $\Im$                |                |                                                 |
| `\aleph`             | $\aleph$             |                |                                                 |
| `\wp`                | $\wp$                |                |                                                 |
| `\forall`            | $\forall$            |                |                                                 |
| `\exists`            | $\exists$            |                |                                                 |
| `\mho`               | $\mho$               |                | [latexsym](https://texdoc.org/serve/latexsym/0) |
| `\partial`           | $\partial$           |                |                                                 |
| `'`                  | $'$                  |                |                                                 |
| `\prime`             | $\prime$             |                |                                                 |
| `\emptyset`          | $\emptyset$          |                |                                                 |
| `\infty`             | $\infty$             |                |                                                 |
| `\nabla`             | $\nabla$             |                |                                                 |
| `\triangle`          | $\triangle$          | $\vartriangle$ | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\Box`               | $\Box$               |                | [latexsym](https://texdoc.org/serve/latexsym/0) |
| `\Diamond`           | $\Diamond$           |                | [latexsym](https://texdoc.org/serve/latexsym/0) |
| `\bot`               | $\bot$               |                |                                                 |
| `\top`               | $\top$               |                |                                                 |
| `\angle`             | $\angle$             |                |                                                 |
| `\surd`              | $\surd$              |                |                                                 |
| `\diamondsuit`       | $\diamondsuit$       |                |                                                 |
| `\heartsuit`         | $\heartsuit$         |                |                                                 |
| `\clubsuit`          | $\clubsuit$          |                |                                                 |
| `\spadesuit`         | $\spadesuit$         |                |                                                 |
| `\neg` <br> `\lnot`  | $\neg$ <br> $\lnot$  |                |                                                 |
| `\flat`              | $\flat$              |                |                                                 |
| `\natural`           | $\natural$           |                |                                                 |
| `\sharp`             | $\sharp$             |                |                                                 |
| `\square`            | $\square$            |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\vartriangle`       | $\vartriangle$       |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\triangledown`      | $\triangledown$      |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\lozenge`           | $\lozenge$           |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\diagup`            | $\diagup$            |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\hslash`            | $\hslash$            |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\blacksquare`       | $\blacksquare$       |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\blacktriangle`     | $\blacktriangle$     |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\blacktriangledown` | $\blacktriangledown$ |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\blacklozenge`      | $\blacklozenge$      |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\measuredangle`     | $\measuredangle$     |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\diagdown`          | $\diagdown$          |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\nexists`           | $\nexists$           |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\Finv`              | $\Finv$              |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\eth`               | $\eth$               |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\sphericalangle`    | $\sphericalangle$    |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\Bbbk`              | $\Bbbk$              |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\circledS`          | $\circledS$          |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\complement`        | $\complement$        |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\Game`              | $\Game$              |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\bigstar`           | $\bigstar$           |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\backprime`         | $\backprime$         |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\varnothing`        | $\varnothing$        |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |
| `\mho`               | $\mho$               |                | [amssymb](https://texdoc.org/serve/amssymb/0)   |

Set the **style** of the symbols in the preamble

| Preamble Command                         | Rendering      | Original    | Dependency         |
| ---------------------------------------- | -------------- | ----------- | ------------------ |
| `\renewcommand{\triangle}{\vartriangle}` | $\vartriangle$ | $\triangle$ | [amssymb](https://texdoc.org/serve/amssymb/0) |

# Math Alphabets

example TEXT: `ABCDEabcde1234`

| Command             | Rendering                     | Dependency                                                                                       |
| ------------------- | ----------------------------- | ------------------------------------------------------------------------------------------------ |
| `\mathrm{TEXT}`     | $\mathrm{ABCDEabcde1234}$     |                                                                                                  |
| `\mathit{TEXT}`     | $\mathit{ABCDEabcde1234}$     |                                                                                                  |
| `\mathnormal{TEXT}` | $\mathnormal{ABCDEabcde1234}$ |                                                                                                  |
| `\mathcal{TEXT}`    | $\mathcal{ABCDE}$             |                                                                                                  |
| `\mathscr{TEXT}`    | $\mathscr{ABCDE}$             | [mathrsfs](https://texdoc.org/serve/mathrsfs/0)                                                  |
| `\mathfrak{TEXT}`   | $\mathfrak{ABCDEabcde1234}$   | [amsfonts](https://texdoc.org/serve/amsfonts/0) or [amssymb](https://texdoc.org/serve/amssymb/0) |
| `\mathbb{TEXT}`     | $\mathbb{ABCDE}$              | [amsfonts](https://texdoc.org/serve/amsfonts/0) or [amssymb](https://texdoc.org/serve/amssymb/0) |

---
Sources:
- 2022-06-10: [The Not So Short Introduction to LaTeX2e](https://tobi.oetiker.ch/lshort/lshort.pdf)
- 2022-06-10: [LaTeX Math Symbols Cheat Sheet - Kapeli](https://kapeli.com/cheat_sheets/LaTeX_Math_Symbols.docset/Contents/Resources/Documents/index)
- 2022-06-10: [LaTeX Math for Undergrads](http://tug.ctan.org/info/undergradmath/undergradmath.pdf)
- 2022-06-10: [List of mathematical symbols by subject - Wikipedia](https://en.wikipedia.org/wiki/List_of_mathematical_symbols_by_subject)

Related:
[Vary the style of mathematical symbols - ϖ vs π](Vary%20the%20style%20of%20mathematical%20symbols%20-%20%CF%96%20vs%20%CF%80.md)

Tags:
[Values  - Standardize math, numbers, symbols, quantities, money](./values.md)
[Graphical elements - Standardize tables, images, plots](./graphical%20elements.md)
[LaTeX](./latex.md)

[^1]: the macros `\notni` isn't supported by MathJax
[^2]: improved by [latexsym](https://texdoc.org/serve/latexsym/0)
[^3]: requires [amssymb](https://texdoc.org/serve/amssymb/0)
