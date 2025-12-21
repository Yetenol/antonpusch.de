---
date: "2025-07-17T08:13:58.251+02:00"
title: "Hide the first-level bullet points from results of list queries"
description: "-"
dg-publish: true
---

[Dataview - Create dynamic tables using data stored in note properties](./computer/apps/Dataview.md)'s list type automatically creates bullet points before each entry, which is often undesirable. The following CSS snippets hide these first-level bullet points of and reduce the indentation by one level to start like regular paragraphs.

Add a custom CSS snippet to [Obsidian](./computer/apps/Obsidian.md) to hide first level bullet point in query results.

```css
/* no need the previous padding adjustment if using Minimal */
ul.dataview.list-view-ul {
	list-style: none;
    padding-left: 0;
}

/* reinstate the bullet to "subpoints" but also adjust the position
   for the bullet to be on the inside (for compatibility with Minimal) */
ul.dataview.dataview-ul.dataview-result-list-ul {
	list-style: disc;
	/* margin-left: 1.5rem; */
}
```

The [Digital Garden](./computer/apps/Digital-Garden.md) plugin converts [Dataview queries](./Query-filter-sort-and-transform-frontmatter-of-your-notes.md) to pure Markdown so that it can be rendered by [Eleventy](Eleventy.md). Unfortunately, the CSS classes of the list elements are lost, so  generated list outputs cannot be distinguished from manually created Markdown bullet lists. Therefore the change can only be applied for all lists.

```css
/* no need the previous padding adjustment if using Minimal */
ul {
	list-style: none;
    padding-left: 0;
}

/* reinstate the bullet to "subpoints" but also adjust the position
   for the bullet to be on the inside (for compatibility with Minimal) */
ul ul {
	list-style: disc;
	margin-left: 1.5rem;
}
```

---
Sources:
- 2023-03-08: [Can we make a cleaner Dataview list? - Resolved help - Obsidian Forum](https://forum.obsidian.md/t/can-we-make-a-cleaner-dataview-list/32843/7)
- 2023-03-08: [Markdown Dataviews - Codeblock Reference - Dataview](https://blacksmithgu.github.io/obsidian-dataview/api/code-reference/#markdown-dataviews)

Related:

Tags:
[Dataview - Create dynamic tables using data stored in note properties](./computer/apps/Dataview.md)