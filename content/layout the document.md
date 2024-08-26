---
dg-publish: true
priority: 7
---

Generate Placeholder Text    
```latex
\usepackage{lipsum} % Generate placeholder paragraphs
```

# Document Classes

```latex
\documentclass[twocolumn]{article}
```

# File Template

Global formatting in **`setup/layout.tex`**

```
\title{My Template}
\author{Anton Pusch}
\date{\today}
```

# Table Of Contents

```latex
\usepackage{hyperref}
\hypersetup{colorlinks=true} % optional
```

```latex
\tableofcontents
```

# Page Margins

```latex
\usepackage[margin=1.5cm]{geometry} % Set page margins
\usepackage[top=2cm, bottom=2cm, left=3cm, right=1cm]{geometry} % Set page margins
```

# Math Spacing

| Command  | Space Width          |
| -------- | -------------------- |
| `\!`     | $-\frac{3}{18}$ quad |
| `\,`     | $\frac{3}{18}$ quad  |
| `\:`     | $\frac{4}{18}$ quad  |
| `\;`     | $\frac{5}{18}$ quad  |
| `\quad`  | $1$ quad             |
| `\qquad` |                      |

| Command                                                                                            | Description                                                      |
| -------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| `\\` <br> `\newline`                                                                               | starts a new line without starting a new paragraph               |
| `\\*`                                                                                              | additionally prohibits a page break after the forced line break. |
| `newpage`                                                                                          | starts a new page                                                |
| `\linebreak[`_n_`]` <br> `\nolinebreak[`_n_`]` <br> `\pagebreak[`_n_`]` <br> `\nopagebreak[`_n_`]` | suggest places where a break may (or may not) happen             |

# Hyphenation

Define the hyphenation of a word list
```latex
\hyphenation{FORTRAN Hy-phen-a-tion}
```

| .            | Meaning                                                                                                          |
| ------------ | ---------------------------------------------------------------------------------------------------------------- |
| `\-`         | inserts a discretionary hyphen into a word. This also becomes the only point hyphenation is allowed in this word |
| `mbox{text}` | be kept together under all circumstances (e.g. phone number)                                                     |
| `\fbox`      | is similar to `\mbox`, but in addition there will be a visible box drawn around the content.                     |


---
#obsidian/cleanup

Sources:

Related:

Tags:
[LaTeX - Typeset mathematical and scientific notation, handle cross-referencing and citations, and position images according to defined placement rules](./latex.md)
