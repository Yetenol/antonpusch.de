---
date: "2025-07-17T08:13:58.640+02:00"
title: "Query, filter, sort and transform frontmatter of your notes"
description: "-"
dg-publish: true
---

# Display a list of page which match the query with one additional information

List of all files in your vault

```
LIST
FROM ""
```

# Display one row per data point with several columns of field data

Tabulate all files in your vault

```
TABLE
FROM ""
```

# Display an interactive list of tasks whose pages match the given query


# Display a calendar view displaying each hit via a dot on its referred date


## General Format

```
TABLE|LIST|TASK
    <field> [AS "Column Name"],
    <field>, 
    ...,
    <field> 
FROM <source>
WHERE <expression>
SORT <expression> [ASC/DESC]
... other data commands
```

---
Sources:
- 2023-03-08: [Query Types - Dataview](https://blacksmithgu.github.io/obsidian-dataview/queries/query-types/)
- 2023-01-23: [Can we make a cleaner Dataview list? - Resolved help - Obsidian Forum](https://forum.obsidian.md/t/can-we-make-a-cleaner-dataview-list/32843/10)
- 2023-01-05: [Structure of a Query - Dataview](https://blacksmithgu.github.io/obsidian-dataview/queries/structure/)
- 2023-01-17: [Embed files - Obsidian-docs](https://jackiegeek.gitee.io/obsidian-docs/fr/How%20to/Embed%20files/)

Related:

Tags:
[Dataview - Create dynamic tables using data stored in note properties](./computer/apps/Dataview.md)