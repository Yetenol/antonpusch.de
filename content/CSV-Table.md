---
date: "2025-03-22T23:27:49.881+01:00"
title: "CSV Table"
description: "Generate table from raw data in a CSV file, automatically detect and format column headers, and values"
dg-publish: true
dg-show-toc: true
priority: 3
---

Dependency: [pgfplotstable](https://texdoc.org/serve/pgfplotstable/0)

# Usage

Generate a table as a **floating object** from a file

```latex
\begin{table}
    \pgfplotstabletypeset{resources/⟨table name⟩.csv}
    \centering
    \caption{⟨caption⟩}
    \label{tab:⟨table name⟩}
\end{table}
```

- `⟨caption⟩`: Title displayed below the table and in the index
- `⟨table name⟩`: Filename and handle to cross reference the table

Generate a table **in line with text** from a file

```latex
\begin{center}
\pgfplotstabletypeset{resources/⟨table name⟩.csv}
\end{center}
```

Generate a table **in line with text** from given data    

```latex
\begin{center}
\pgfplotstabletypeset{
    a, b 
    5000, 1.234e5
    6000, 1.631e5
    7000, 2.1013e5
    9000, 1000000
}
\end{center}
```

Use an **existing** tabular environment    

```latex
\pgfplotstabletypeset[
    col sep=&,row sep=\\,sci zerofill
]{
    level & dof & error \\
    1 & 4 & 2.50000000e-01 \\ 
    2 & 16 & 6.25000000e-02 \\ 
    3 & 64 & 1.56250000e-02 \\ 
    4 & 256 & 3.90625000e-03 \\ 
    5 & 1024 & 9.76562500e-04 \\ 
    6 & 4096 & 2.44140625e-04 \\ 
    7 & 16384 & 6.10351562e-05 \\ 
    8 & 65536 & 1.52587891e-05 \\ 
    9 & 262144 & 3.81469727e-06 \\ 
    10 & 1048576 &9.53674316e-07 \\
}
```

# Setup

Dependency: [pgfplotstable](https://texdoc.org/serve/pgfplotstable/0), [booktabs](https://texdoc.org/serve/booktabs/0)

## Format all tables

Setup header layout in `setup/layout.tex`

```latex
\pgfplotstableset{
    col sep = comma,
}
```

Put **horizontal lines** around the **header**     

```latex
\pgfplotstableset{
    every head row/.style = {
        before row=\toprule, 
        after row=\midrule
    },
    every last row/.style = {
        after row = \bottomrule
    },
    header = true,
}
```

## Format

**Comment** lines using `%` or `#`

Example file:

```
# Convergence results 
# fictional source, generated 2008 
level dof error1 error2 info grad(log(dof),log(error2)) quot(error1) 
1 4 2.50000000e-01 7.57858283e-01 48 0 0 
2 16 6.25000000e-02 5.00000000e-01 25 -3.00000000e-01 4 
3 64 1.56250000e-02 2.87174589e-01 41 -3.99999999e-01 4 
4 256 3.90625000e-03 1.43587294e-01 8 -5.00000003e-01 4 
5 1024 9.76562500e-04 4.41941738e-02 22 -8.49999999e-01 4 
6 4096 2.44140625e-04 1.69802322e-02 46 -6.90000001e-01 4 
7 16384 6.10351562e-05 8.20091159e-03 40 -5.24999999e-01 4 
8 65536 1.52587891e-05 3.90625000e-03 48 -5.35000000e-01 3.99999999e+00 
9 262144 3.81469727e-06 1.95312500e-03 33 -5.00000000e-01 4.00000001e+00 
10 1048576 9.53674316e-07 9.76562500e-04 2 -5.00000000e-01 4.00000001e+00
```

## Format specific table

Format **specific column** by its name    

```latex
\pgfplotstabletypeset[
    columns/{error1}/.style={
        column name = {$\nabla e_1$},
        string replace = {0}{},
        dec sep align,
        precision = 1,
    }]
    {resources/RAW-DATA.CSV}
```

Create an **empty cell**  

```latex
{}
```

Create a **multicolumn cell**    

```
a,b
{multicolumn cell}
12,4
```


Escape *column separator* by enclosing the cell in braces `{}`

```latex
{grad(log(dof),log(error2)}
```

Escape a brace using backslash    

```latex
column\{withbrace
```

# Pgf keys

## Text table input format

All pgfkeys are stored in `pgfplots/table/`

Specify **column separation character** (default: *space*) 

```latex
col sep = space|tab|comma|semicolon|colon|braces|&|ampersand
```

- *braces* supports **multicolumn and multiline** cells using `{` and `}`
- *space* means whitespace characters
- *≠space* doesn't trim whitespaces behind separator
- *&* trims cells automatically
- combines multiple successive spaces and tabs to single whitespace (as usual in TeX)

**Trim** leading and trailing **white space** of cell entries (default: *true*)

```latex
trim cells = true|false
```

- `col sep = &` enables it

Identify **column names** automatically during input (default: *true*)

```latex
header = true|false|has colnames
```

- *true*: first line **might** be header (auto detect non-numeric entries)
- *false*: first line **isn't** a header
- *has colnames*: first line **must** be a header

**Input data from** external file or inline braces (default: *auto*)

```latex
format = auto|inline|file
```

**Separate rows** with specific character    

```latex
row sep = newline|\\
```

**Ignore list of characters** (default: *empty*)

```latex
ignore chars = {⟨comma separated list⟩}
```

Write **cells with spaces** (default: *empty*)

```latex
text indicator = {⟨char⟩}
```

- escape text indicators by doubling them like `"A long ""cell""" normalcell`

Skip first # lines of input file (default: 0)

```latex
skip first n = {⟨integer⟩}
```

## Selecting Columns and their Appearance Styles

**Select** columns to be displayed

```latex
/columns = {⟨comma separated list⟩}
```

- *empty*: show all columns
- with header: use column name or index
- without header: use `index[#]`

**Alias** a column name

```latex
alias/⟨col name⟩/.initial = {⟨real col name⟩}
```

**Style** a specific **input column**

```latex
columns/⟨column name⟩/.style = {
    ⟨key value list⟩
}
```

**Style** a specific **displayed column**

```latex
display columns/⟨index⟩/.style = {
    ⟨key value list⟩
}
```

or

```latex
every col no ⟨index⟩/.style = {
    ⟨key value list⟩
}
```

Use **LaTeX columntype** (default: *c*)

```latex
column type = {⟨tabular column type⟩}
```

**Rename column name** in output (default: *`\pgfkeysnovalue`*)

```latex
column name = {⟨TEX display column name⟩}
```

**Format column name** in output

General format

```latex
assign column name/.code = {
    /pgfplots/table/column name = {
        ⟨formatting macros⟩ #1
    }
}
```

- align header cells centered using 

    ```
    \multicolumn{1}{c}{ #1 }
    ```

- format header cells bold using 

    ```
    \textbf{ #1 }
    ```

---
Sources:
- 2023-01-07: [https://texdoc.org/serve/pgfplotstable/0](https://texdoc.org/serve/pgfplotstable/0)

Related:
[Floating Table - Add caption, cross reference a table](./Floating-Table.md)

Tags:
[Graphical elements - Standardize tables, images, plots](./Graphical-elements.md)
