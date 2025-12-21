---
date: "2025-07-17T08:13:58.697+02:00"
title: "Reliable reference neighboring Excel cells"
description: "-"
dg-publish: true
synopsis: |
  Calculate with data from other cells, retrieve cell contents using absolute or relative addresses, and freeze rows or columns to prevent them from changing. Reduce the risk of errors when referencing other cells in formulas by using the same formula in all cells and expressing relative queries explicitly.
---

Excel is a spreadsheet program. Functions can be used to perform mathematical and logical operations on data from other cells.

In Excel, the address of a cell, consisting of a letter for the column and a number for the row, can be used to retrieve its contents (for instance `A1`). For example, we want to use another cell value in cell C1. In absolute terms, we query the fixed address A1. Relatively speaking, we are querying the cell of the same row in column A.

When applying the formula to adjacent cells, the relative cell address is used. If this is undesirable, we can freeze the row or column by placing a dollar sign in front of it (for instance `$A$1`).

Excel tries its best to maintain links to the correct cell when, for example, new columns or rows are created between them or the calculating cells are moved. Since after applying the formula to adjacent cell, each cell calls a different address, it is very difficult to check the correctness of the links. Especially when other people touch the spreadsheet, errors can quickly creep in unnoticed and are not obvious.

Therefore, it is more reliable and error resistant to use the same formula in all cells and to express relative queries explicitly. In the following, we will learn this alternative way to query other cells absolutely or relatively.

# Set common names

- **SELECT** `A1`
- open Name Manager (`Ctrl + F3`)
- click `New...`
- add the following entries

| Name:                | Scope:          | Refers to:                                                        |
| -------------------- | --------------- | ----------------------------------------------------------------- |
| `THIS_CELL`          | _current sheet_ | `A1`                                                              |
| `THIS_ROW`           | _current sheet_ | `ROW(THIS_CELL)`                                                  |
| `THIS_COLUMN_NUMBER` | _current sheet_ | `COLUMN(THIS_CELL)`                                               |
| `THIS_COLUMN`        | _current sheet_ | `SUBSTITUTE(ADDRESS(THIS_ROW, THIS_COLUMN_NUMBER,4),THIS_ROW,"")` |

- repeat for every sheet

# Get cell information

- requires [ > Set common names](Reliable-reference-neighboring-Excel-cells.md#Set%20common%20names)

| Description               | Command                                  | Example                                  |
| ------------------------- | ---------------------------------------- | ---------------------------------------- |
| Get current cell          | `THIS_CELL`                              | C2 => `0` <br> throws circular reference |
| Get current row           | `THIS_ROW`                               | C2 => `2`                                |
| Get current column        | `THIS_COLUMN`                            | C2 => `C`                                |
| Get current column number | `THIS_COLUMN_NUMBER`                     | C2 => `3`                                |
| Get current address       | `ADDRESS(THIS_ROW,THIS_COLUMN_NUMBER)`   | C2 => `$C$2`                             |
| Get current address       | `ADDRESS(THIS_ROW,THIS_COLUMN_NUMBER,4)` | C2 => `C2`                               |

# Get neighboring cells

- requires [ > Set common names](Reliable-reference-neighboring-Excel-cells.md#Set%20common%20names)

| Description                   | Command                                                                                    | Example                                    |
| ----------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------ |
| Get current cell              | `INDIRECT(THIS_COLUMN & THIS_ROW)` <br> `INDIRECT(ADDRESS(THIS_ROW,THIS_COLUMN_NUMBER))` | C2 => `C2` <br> throws circular reference |
| Get E column in current row   | `INDIRECT("E" & THIS_ROW)`                                                                | C2 => `E2`                                |
| Get 5th row in current column | `INDIRECT(THIS_COLUMN & 5)`                                                               | C2 => `C5`                                |
| Get right neighbor            | `INDIRECT(ADDRESS(THIS_ROW,THIS_COLUMN_NUMBER+1))`                                        | C2 => `C3`                                |
| Get left neighbor             | `INDIRECT(ADDRESS(THIS_ROW,THIS_COLUMN_NUMBER-1))`                                        | C2 => `C1`                                |
| Get upper neighbor            | `INDIRECT(ADDRESS(THIS_ROW-1,THIS_COLUMN_NUMBER))`                                        | C2 => `B2`                                |
| Get lower neighbor            | `INDIRECT(ADDRESS(THIS_ROW+1,THIS_COLUMN_NUMBER))`                                        | C2 => `D2`                                |


Is a range of cells empty
```
=IF(SUMPRODUCT(--(D16:G16<>""))<>0,"not empty","empty")
```

Get last non-empty cell in a given range
```
=SUM(A4:INDEX(A4:A10,MATCH(TRUE,(A4:A10=""),0)))
```

Sum column values until next blank cell?
```
=SUM(A4:INDEX(A4:A10,MATCH(TRUE,(A4:A10=""),0)))
```


---


Sources:
- 2023-03-16: [How to Reference a Cell from Another Cell in Microsoft Excel](https://www.computerhope.com/issues/ch002007.htm)
- 2023-03-16: [Fill a formula down into adjacent cells - Microsoft Support](https://support.microsoft.com/en-us/office/fill-a-formula-down-into-adjacent-cells-041edfe2-05bc-40e6-b933-ef48c3f308c6)

Related:

Tags:
[Microsoft Excel](./computer/apps/Microsoft-Excel.md)
[Workflows - Improve workflow in applications](./Workflows.md)