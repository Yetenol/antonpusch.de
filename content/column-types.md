---
title: "Column Types - Lookup column types aligned left, right, or center, with fixed, or evenly distributed width"
date: "2024-07-24T00:00:00.000+02:00"
dg-publish: true
priority: 9
---

|                       | Content            | Width               | Alignment       | Dependency                                            |
| --------------------- | ------------------ | ------------------- | --------------- | ----------------------------------------------------- |
| `L`                   | paragraph          | evenly distributed  | left            | [LaTeX.table](https://github.com/Yetenol/latex.table) |
| `R`                   | paragraph          | evenly distributed  | right           | [LaTeX.table](https://github.com/Yetenol/latex.table) |
| `C`                   | paragraph          | evenly distributed  | center          | [LaTeX.table](https://github.com/Yetenol/latex.table) |
| `X`                   | paragraph          | evenly distributed  | justify         | [tabularx](https://texdoc.org/serve/tabularx/0)       |
| `p{1cm}`              | paragraph          | fixed               | left            | built-in                                              |
| `p`                   | single line        | auto-fit to content | left            | built-in                                              |
| `m{}`                 | paragraph          | fixed               | vertical center | built-in                                              |
| `S[table-format=3.1]` | number/single line | fixed               | decimal point   | [siunitx](https://texdoc.org/serve/siunitx/0)         |
| `S`                   | number/single line | auto-fit to content | decimal point   | [siunitx](https://texdoc.org/serve/siunitx/0)         |


---
Sources:

Related:

Tags:
[Graphical elements - Standardize tables, images, plots](./graphical-elements.md)
