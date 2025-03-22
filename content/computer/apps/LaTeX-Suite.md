---
date: "2025-03-22T23:45:55.004+01:00"
title: "LaTeX Suite"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: 
microsoft-id: 
winget-id: 
github-repo: artisticat1/obsidian-latex-suite
github-release-filename: 
website: 
priority: 
link-modportals: 
modportal0-id: obsidian-latex-suite
thumbnail: 
categories:
  - Editing
  - Math
synopsis: A plugin for Obsidian that aims to make typesetting LaTeX math as fast as handwriting.
extends-app: "[[Obsidian|Obsidian]]"
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

# Write custom snippets

Snippets are formatted as follows:

```ts
{trigger: string, replacement: string, options: string, description?: string, priority?: number}
```

- `trigger` : The text that triggers this snippet.
- `replacement` : The text to replace the `trigger` with.
- `options` : See below.
- `description` (optional): A description for this snippet.
- `priority` (optional): This snippet's priority. Defaults to 0. Snippets with higher priority are run first. Can be negative.

## Options

- `m` : Math mode. Only run this snippet inside math
- `t` : Text mode. Only run this snippet outside math
- `A` : Auto. Expand this snippet as soon as the trigger is typed. If omitted, the Tab key must be pressed to expand the snippet
- `r` : Regex. The `trigger` will be treated as a regular expression
- `w` : Word boundary. Only run this snippet when the trigger is preceded (and followed by) a word delimiter, such as `.`, `,`, or `-`.

Insert **tabstops** for the cursor to jump to by writing "$0", "$1", etc. in the `replacement`.

- [Snippet documentation](https://github.com/artisticat1/obsidian-latex-suite/blob/main/DOCS.md)
- [Community snippets](https://github.com/artisticat1/obsidian-latex-suite/discussions/50)

$$
\begin{align*}
sd 
\end{align*}
$$

# My snippets

```json
[    
    // Math mode
    {trigger: "mk", replacement: "$​$0​$", options: "tAw"},
    {trigger: "dm", replacement: "$$\n$0\n$$", options: "tAw"},
    {trigger: "beg", replacement: "\\begin{$0}\n$1\n\\end{$0}", options: "mA"},

// Environments
    // Enclose selection in an environment
    {trigger: "e", replacement: "\\begin{$0}\n${VISUAL}\n\\end{$0}", options: "mA"},
    {trigger: "g", replacement: "\\begin{gather*}\n${VISUAL}\n\\end{gather*}", options: "mA"},
    {trigger: "a", replacement: "\\begin{align*}\n${VISUAL}\n\\end{align*}", options: "mA"},
    {trigger: "m", replacement: "\\begin{multline*}\n${VISUAL}\n\\end{multline*}", options: "mA"},
    // Open an environment
    {trigger: "cases", replacement: "\\begin{cases}\n$0\n\\end{cases}", options: "mAw"},
    {trigger: "pmat", replacement: "\\begin{pmatrix}\n$0\n\\end{pmatrix}", options: "mAw"},
    {trigger: "bmat", replacement: "\\begin{bmatrix}\n$0\n\\end{bmatrix}", options: "mAw"},
    {trigger: "Bmat", replacement: "\\begin{Bmatrix}\n$0\n\\end{Bmatrix}", options: "mAw"},
    {trigger: "vmat", replacement: "\\begin{vmatrix}\n$0\n\\end{vmatrix}", options: "mAw"},
    {trigger: "Vmat", replacement: "\\begin{Vmatrix}\n$0\n\\end{Vmatrix}", options: "mAw"},
    {trigger: "array", replacement: "\\begin{array}\n$0\n\\end{array}", options: "mAw"},
    {trigger: "matrix", replacement: "\\begin{matrix}\n$0\n\\end{matrix}", options: "mAw"},

    // Greek letters
    {trigger: "@a", replacement: "\\alpha ", options: "mA"},
    {trigger: "@b", replacement: "\\beta ", options: "mA"},
    {trigger: "@g", replacement: "\\gamma ", options: "mA"},
    {trigger: "@d", replacement: "\\delta ", options: "mA"},
    {trigger: "@ep", replacement: "\\varepsilon ", options: "mA"},
    {trigger: "@z", replacement: "\\zeta ", options: "mA"},
    {trigger: "@et", replacement: "\\eta ", options: "mA"},
    {trigger: "@te", replacement: "\\theta ", options: "mA"},
    {trigger: "@i", replacement: "\\iota ", options: "mA"},
    {trigger: "@k", replacement: "\\kappa ", options: "mA"},
    {trigger: "@l", replacement: "\\lambda ", options: "mA"},
    {trigger: "@m", replacement: "\\mu ", options: "mA"},
    {trigger: "@n", replacement: "\\nu ", options: "mA"},
    {trigger: "@x", replacement: "\\xi ", options: "mA"},
    {trigger: "@p", replacement: "\\pi ", options: "mA"},
    {trigger: "@r", replacement: "\\rho ", options: "mA"},
    {trigger: "@s", replacement: "\\sigma ", options: "mA"},
    {trigger: "@ta", replacement: "\\tau ", options: "mA"},
    {trigger: "@u", replacement: "\\upsilon ", options: "mA"},
    {trigger: "@p", replacement: "\\varphi ", options: "mA"},
    {trigger: "@c", replacement: "\\chi ", options: "mA"},
    {trigger: "@o", replacement: "\\omega ", options: "mA"},
    {trigger: "@G", replacement: "\\Gamma ", options: "mA"},
    {trigger: "@D", replacement: "\\Delta ", options: "mA"},
    {trigger: "@T", replacement: "\\Theta ", options: "mA"},
    {trigger: "@L", replacement: "\\Lambda ", options: "mA"},
    {trigger: "@X", replacement: "\\Xi ", options: "mA"},
    {trigger: "@Pi", replacement: "\\Pi ", options: "mA"},
    {trigger: "@S", replacement: "\\Sigma ", options: "mA"},
    {trigger: "@U", replacement: "\\Upsilon ", options: "mA"},
    {trigger: "@Ph", replacement: "\\Phi ", options: "mA"},
    {trigger: "@Ps", replacement: "\\Psi ", options: "mA"},
    {trigger: "@O", replacement: "\\Omega ", options: "mA"},

    // Add backslash before greek letters and symbols
    {trigger: "(?<!\\\\)(${GREEK})", replacement: "\\[[0]]", options: "wrmA", description: "Add backslash before greek letters and symbols"},

// Text
    // Open a text mode
    {trigger: " *\\\"", replacement: " \\text{$0} $1", options: "mAr"},
    // Enclose selection in text mode
    {trigger: "\"", replacement: "\\text{$0${VISUAL}}", options: "mA"},

// Domains
    {trigger: "NN", replacement: "\\mathbb{N} ", options: "mAw"},
    {trigger: "QQ", replacement: "\\mathbb{Q} ", options: "mAw"},
    {trigger: "ZZ", replacement: "\\mathbb{Z} ", options: "mAw"},
    {trigger: "RR", replacement: "\\mathbb{R} ", options: "mAw"},
    {trigger: "PP", replacement: "\\mathbb{P}($0) ", options: "mAw"},
    {trigger: "EE", replacement: "\\mathbb{E}[$0] ", options: "mAw"},
    {trigger: "VV", replacement: "\\mathbb{V}($0) ", options: "mAw"},

// Operators
    // Add spaces around operators
    {description: "+", trigger: "(?<!\\\{) *\\\+", replacement: " + $0", options: "mAr"},
    {description: "-", trigger: "(?<!\\\{) *\\\-", replacement: " - $0", options: "mAr"},
    {description: "*", trigger: "(?<!\\\{|align|mult|multline|gather|equation|\\\\tag) *\\\*", replacement: " \\cdot $0", options: "mAr"},
    {description: ",", trigger: " *,", replacement: ", $0", options: "mAr"},
    {description: "|", trigger: " *\\\|", replacement: " \\mid $0", options: "mAr"},
    {description: "||", trigger: " *\\\|\\\|", replacement: " \\mid $0", options: "mAr"},
    {description: "||", trigger: " *\\\\mid *\\\|", replacement: " \\parallel $0", options: "mAr"},
    {description: "~", trigger: " *\\\~", replacement: " \\sim $0", options: "mAr"},
    {description: "#", trigger: " *\\\#", replacement: " \\in $0", options: "mAr"},
    {description: "->", trigger: " *- *>", replacement: " \\to $0", options: "mAr"},
    {description: "-->", trigger: " *- *- *>", replacement: " \\implies $0", options: "mAr"},
 
    {description: "!", trigger: " *!", replacement: " \\not $0", options: "mAr"},
    {description: "!=", trigger: " *\\\\not *=", replacement: " \\ne $0", options: "mAr"},
    {description: "!==", trigger: " *\\\\ne *=", replacement: " \\not\\equiv $0", options: "mAr"},
    {description: "!<", trigger: " *\\\\not *<", replacement: " \\nless $0", options: "mAr"},
    {description: "!>", trigger: " *\\\\not *>", replacement: " \\ngtr $0", options: "mAr"},
    {description: "!<=", trigger: " *\\\\nless *=", replacement: " \\nleq $0", options: "mAr"},
    {description: "!<=", trigger: " *\\\\ne *<", replacement: " \\nleq $0", options: "mAr"},
    {description: "!>=", trigger: " *\\\\ngtr *=", replacement: " \\ngeq $0", options: "mAr"},
    {description: "!>=", trigger: " *\\\\ne *>", replacement: " \\ngeq $0", options: "mAr"},
    {description: "! operator", trigger: " *\\\\not *\\\\(mid|parallel|sim|subseteq|supseteq)", replacement: " \\n[[0]] $0", options: "mAr"},
    {description: "! ->", trigger: " *\\\\not *\\\\to", replacement: " \\nrightarrow $0", options: "mAr"},
    {description: "! <-", trigger: " *\\\\not *\\\\gets", replacement: " \\nleftarrow $0", options: "mAr"},
    {description: "! <->", trigger: " *\\\\not *\\\\leftrightarrow", replacement: " \\nleftrightarrow $0", options: "mAr"},
    {description: "!~", trigger: " *\\\\not *~", replacement: " \\nsim $0", options: "mAr"},
    {description: "!#", trigger: " *\\\\not *#", replacement: " \\notin $0", options: "mAr"},
    {description: "!in", trigger: " *\\\\not \\\\in", replacement: " \\notin $0", options: "mAr"},
    {description: "!|", trigger: " *\\\\not *\\\|", replacement: " \\nmid $0", options: "mAr"},
    {description: "!||", trigger: " *\\\\nmid *\\\|", replacement: " \\nparallel $0", options: "mAr"},
 
 
    {description: "c", trigger: " *\\\\sub", replacement: " \\subset $0", options: "mAr"},
    {description: "c", trigger: "\\\\?sub", replacement: "\\subset $0", options: "mArw"},
    {description: "c=", trigger: " *\\\\subset *=", replacement: " \\subseteq $0", options: "mAr"},
    {description: "3", trigger: " *\\\\sup", replacement: " \\supset $0", options: "mAr"},
    {description: "3", trigger: "\\\\?sup", replacement: "\\supset $0", options: "mArw"},
    {description: "3=", trigger: " *\\\\supset *=", replacement: " \\supseteq $0", options: "mAr"},

    {description: ":=", trigger: " *: *=", replacement: " \\triangleq $0", options: "mAr"},
    {description: "<=", trigger: " *< *=", replacement: " \\le $0", options: "mAr"},
    {description: "<=", trigger: " *= *<", replacement: " \\le $0", options: "mAr"},
    {description: "<=", trigger: " *\\\\leq", replacement: " \\le $0", options: "mAr"},
    {description: "<", trigger: " *<", replacement: " < $0", options: "mAr"},
    {description: "<", trigger: " *\\\\lt", replacement: " < $0", options: "mAr"},
    {description: ">=", trigger: " *> *=", replacement: " \\ge $0", options: "mAr"},
    {description: ">=", trigger: " *= *>", replacement: " \\ge $0", options: "mAr"},
    {description: ">=", trigger: " *\\\\geq", replacement: " \\ge $0", options: "mAr"},
    {description: ">", trigger: " *>", replacement: " > $0", options: "mAr"},
    {description: ">", trigger: " *\\\\gt", replacement: " > $0", options: "mAr"},
    {description: "==", trigger: " *= *=", replacement: " \\equiv $0", options: "mAr"},
    {description: "=", trigger: " *=", replacement: " = $0", options: "mAr"},
    
    // Overset relation
    {description: "named =", trigger: "(=|\\\\(equiv|to|gets|implies|iff|le|lt|ge|gt|approx|subset|subseteq|supset|supseteq)) *\\\^", replacement: "\\overset{$0}{[[0]]} $1", options: "mAr"},
    
    // Trim spaces before superscript or subscript
    {description: "_", trigger: " *_", replacement: "_{$0} $1", options: "mAr"},
    {description: "^", trigger: " *\\\^", replacement: "^{$0} $1", options: "mAr"},


// Enclose selection
    {trigger: "d", replacement: "\\left${VISUAL}\\right", options: "mA"},
    {trigger: "u", replacement: "\\underbrace{ ${VISUAL} }_{$0}", options: "mA"},
    {trigger: "o", replacement: "\\overbrace{ ${VISUAL} }^{$0}", options: "mA"},
    // {trigger: "c", replacement: "\\textcolor{$0}{${VISUAL}}", options: "mA"},
    {trigger: "r", replacement: "\\textcolor{magenta}{${VISUAL}}", options: "mA"},
    {trigger: "g", replacement: "\\textcolor{limegreen}{${VISUAL}}", options: "mA"},
    {trigger: "y", replacement: "\\textcolor{orange}{${VISUAL}}", options: "mA"},
    
// Abbreviations
    {trigger: "\\\\?(partial|det|log|ln|sin|cos|tan|arcsin|arccos|arctan|sinh|cosh|tanh)", description: "and \\ and parenthesis", replacement: "\\[[0]] ($0) $1", options: "mArw"},
    {trigger: "\\\\?op", replacement: "\\operatorname{$0} ( $1 )", options: "mArw"},
    {trigger: "\\\\?(max|min)", description: "and \\ and curly brackets", replacement: "\\[[0]] \{$0\} $1", options: "mArw"},
    {trigger: "\\\\?noth", description: "⊘", replacement: "\\varnothing ", options: "mArw"},
    {trigger: "\\\\?empty", description: "⊘", replacement: "\\varnothing ", options: "mArw"},
    {trigger: "\\\\?imp", description: "=>", replacement: "\\implies ", options: "mArw"},
    {trigger: "\\\\?Gets", description: "==>", replacement: "\\;\\Longleftarrow\\; ", options: "mArw"},
    {trigger: "\\\\?os", replacement: "\\overset{$1}{$0} $2", options: "mArw"},
    {trigger: "\\\\?us", replacement: "\\underset{$1}{$0} $2", options: "mArw"},
    {trigger: "\\\\?ub", replacement: "\\underbrace{ $1 }_{$0} $2", options: "mArw"},
    {trigger: "\\\\?ob", replacement: "\\overbrace{ $1 }^{$0} $2", options: "mArw"},
    {trigger: " +/", replacement: " \\frac{$0}{$1} $2", options: "mAr"},
    {trigger: " *\\\\f", replacement: " \\frac{$0}{$1} $2", options: "mAr"},
    {trigger: "\\\\?fo", replacement: "\\forall\\, $0 \\mid $1", options: "mArw"},
    {trigger: "\\\\?ex", replacement: "\\exists\\, $0 \\mid $1", options: "mArw"},
    {trigger: "\\\\?bin", replacement: "\\binom{$0}{$1}", options: "mArw"},
    {trigger: "par", replacement: "\\left( $0 \\right) $1", options: "mAw"},
    {trigger: "Par", replacement: "\\big( $0 \\big) $1", options: "mAw"},
    {trigger: "PAR", replacement: "\\Big( $0 \\Big) $1", options: "mAw"},
    {trigger: "cur", replacement: "\\{ $0 \\} $1", options: "mAw"},
    {trigger: "Cur", replacement: "\\big\\{ $0 \\big\\} $1", options: "mAw"},
    {trigger: "CUR", replacement: "\\Big\\{ $0 \\Big\\} $1", options: "mAw"},
    {trigger: "box", replacement: "[ $0 ] $1", options: "mAw"},
    {trigger: "Box", replacement: "\\big[ $0 \\big] $1", options: "mAw"},
    {trigger: "BOX", replacement: "\\Big[ $0 \\Big] $1", options: "mAw"},
    {trigger: "ang", replacement: "\\langle $0 \\rangle $1", options: "mAw"},
    {trigger: "Ang", replacement: "\\big\\langle $0 \\big\\rangle $1", options: "mAw"},
    {trigger: "ANG", replacement: "\\Big\\langle $0 \\Big\\rangle $1", options: "mAw"},
    {trigger: "floor", replacement: "\\left\\lfloor $0 \\right\\rfloor $1", options: "mAw"},
    {trigger: "Floor", replacement: "\\big\\lfloor $0 \\big\\rfloor $1", options: "mAw"},
    {trigger: "FLOOR", replacement: "\\Big\\lfloor $0 \\Big\\rfloor $1", options: "mAw"},
    {trigger: "ceil", replacement: "\\left\\lceil $0 \\right\\rceil $1", options: "mAw"},
    {trigger: "Ceil", replacement: "\\big\\lceil $0 \\big\\rceil $1", options: "mAw"},
    {trigger: "CEIL", replacement: "\\Big\\lceil $0 \\Big\\rceil $1", options: "mAw"},
    {trigger: "round", replacement: "\\left\\lfloor $0 \\right\\rceil $1", options: "mAw"},
    {trigger: "Round", replacement: "\\big\\lfloor $0 \\big\\rceil $1", options: "mAw"},
    {trigger: "ROUND", replacement: "\\Big\\lfloor $0 \\Big\\rceil $1", options: "mAw"},
    {trigger: "abs", replacement: "\\left| $0 \\right| $1", options: "mAw"},
    {trigger: "Abs", replacement: "\\big| $0 \\big| $1", options: "mAw"},
    {trigger: "ABS", replacement: "\\Big| $0 \\Big| $1", options: "mAw"},
    {trigger: "norm", replacement: "\\left\| $0 \\right\| $1", options: "mAw"},
    {trigger: "Norm", replacement: "\\big\| $0 \\big\| $1", options: "mAw"},
    {trigger: "NORM", replacement: "\\Big\| $0 \\Big\| $1", options: "mAw"},
    // {trigger: "box", replacement: "\\left[\\!\\!\\left[ $0 \\right]\\!\\!\\right] $1", options: "mAw"},
    // {trigger: "Box", replacement: "\\big[\\!\\!\\big[ $0 \\big]\\!\\!\\big] $1", options: "mAw"},
    // {trigger: "BOX", replacement: "\\Big[\\!\\!\\Big[ $0 \\Big]\\!\\!\\Big] $1", options: "mAw"},


    // Misc
    {trigger: "tayl", replacement: "${0:f}(${1:x} + ${2:h}) = ${0:f}(${1:x}) + ${0:f}'(${1:x})${2:h} + ${0:f}''(${1:x}) \\frac{${2:h}^{2}}{2!} + \\dots$3", options: "mA"},
]
```

---
Sources:
- [How Obsidian saved me 100s of hours throughout my uni course ft. Latex Suite : r/ObsidianMD](https://www.reddit.com/r/ObsidianMD/comments/184ae2n/how_obsidian_saved_me_100s_of_hours_throughout_my/)

Related:

Tags:
