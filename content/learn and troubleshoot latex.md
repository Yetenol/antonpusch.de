---
title: "Learn and troubleshoot LaTeX - Read (package) documentation, cheat sheets, tutorials"
dg-publish: true
priority: 1
---

# View user guide of a specific packages  

Visit the *TeX and LaTeX documentation lookup system*
- add the site as a custom search engine `http://texdoc.org/serve/%s/0`
- lookup documentation on **[texdoc.org](https://texdoc.org/index.html)**

Run a command in a terminal
```
texdoc ⟨package name⟩
```
-  a LaTeX suite like *TeX Live* must be installed

Visit the The Comprehensive TEX Archive Network (CTAN)
- search on **[ctan.org](https://ctan.org/)**

# Highlight overfull conflicts

Enable draft mode in the preamble
```latex
\documentclass[draft]{article}
```

Only **check syntax**  
- by suppressing the PDF creation in the preamble  
- Dependency: syntonly
```latex
\syntaxonly
```

**Throw an error** for a specific package
```latex
\PackageError {⟨package name⟩} {⟨error text⟩} {}
```

# Further cheat sheets and resources

- [Learn LaTeX in 30 minutes - Overleaf](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
- [User's Guide for amsmath Package](https://texdoc.org/serve/asmmath/0)
- [The Not So Short Introduction to LaTeX](https://tobi.oetiker.ch/lshort/lshort.pdf)
- [LATEX quick reference](https://icl.utk.edu/~mgates3/docs/latex.pdf)
- [A quick guide to LaTeX](https://www.overleaf.com/latex/templates/a-quick-guide-to-latex/fghqpfgnxggz.pdf)
- [LaTeX Cheat Sheet](https://wch.github.io/latexsheet/latexsheet-a4.pdf)

---


Sources:

Related:

Tags:
[LaTeX - Typeset mathematical and scientific notation, handle cross-referencing and citations, and position images according to defined placement rules](./latex.md)
