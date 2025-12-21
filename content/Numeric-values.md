---
date: "2025-07-17T08:13:58.508+02:00"
title: "Numeric values"
description: "Typeset (large) numbers, physical quantities, units, money"
dg-publish: true
---

# Numeric values

Dependency: [siunitx](https://texdoc.org/serve/siunitx/0)

## Numbers

| Example Command    | Rendering             |
| ------------------ | --------------------- |
| `\num{12345.2}`    | $12\ 345.2$           |
| `\num{1\,234 5,2}` | $12\ 345.2$           |
| `\num{3.45e-4}`    | $3.45 \times 10^{-4}$ |

## Angles

| Example Command | Rendering      |
| --------------- | -------------- |
| `\ang{10}`      | $10^\circ$     | 
| `\ang{1;2;3}`   | $1^\circ2'3''$ |

# Physical values

Dependency: [siunitx](https://texdoc.org/serve/siunitx/0)

## Units

| Example Command                                           | Rendering                 |
| --------------------------------------------------------- | ------------------------- |
| `\unit{kg.m/s^2}`                                         | $\mathrm{kg\ m/s^2}$      |
| `\unit{\gram\per\cubic\centi\metre}`                      | $\mathrm{g\ cm^{-3}}$     |
| `\unit[per-mode = symbol]{\gram\per\cubic\centi\metre}`   | $\mathrm{g/cm^3}$         |
| `\unit[per-mode = fraction]{\gram\per\cubic\centi\metre}` | $\mathrm{\frac{g}{cm^3}}$ |

## Quantities

| Example Command     | Rendering              |
| ------------------- | ---------------------- |
| `\qty{3}{\celsius}` | $3\ \mathrm{^\circ C}$ |

# Monetary values

Dependencies: [currency](https://texdoc.org/serve/currency/0) + [Currencies and money -  Standardize monetary values, 3 € vs $ 5](./Currencies-and-money.md)

## Currency

| Command   | Rendering |
| --------- | --------- |
| `\cEUR{}` | €         |
| `\cUSD{}` | $         |
| `\cJPY{}` | ¥         |
| `\cGBP{}` | £         |

## Amount of money

| Command      | Rendering |
| ------------ | --------- |
| `\dEUR{1.5}` | 1.50 €    |
| `\dUSD{1.5}` | $ 1.50    |
| `\dJPY{1.5}` | 2 ¥       |
| `\dGBP{1.5}` | £ 1.50    |


---


Sources:

Related:

Tags:
[Values  - Standardize math, numbers, symbols, quantities, money](./Values-.md)
