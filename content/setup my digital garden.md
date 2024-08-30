---
dg-publish: true
---
# Digital Obsidian Garden

All my markdown notes to be published are uploaded on [Github](https://github.com/yetenol/digital-garden/) and automatically built as my [homepage](https://antonpusch.de/) with [Vercel](https://vercel.com/yetenols-projects/digitalgarden).

The [Digital Garden](https://obsidian.md/plugins?id=digitalgarden) plugin for Obsidian exports exactly all notes with property `dg-publish: true` and deletes old ones. Included live queries of the [Dataview](https://obsidian.md/plugins?id=dataview) plugin are converted to static Markdown. Executable code blocks of the [Execute Code](https://obsidian.md/plugins?id=execute-code) plugin are relabeled for correct syntax highlighting.

The note export, the configuration of the website, and the update of this build template by a pull request are set in the [Digital Garden](https://github.com/oleeskild/obsidian-digital-garden) plugin, see [documentation](https://dg-docs.ole.dev/). 

# Static Site Generator

After each commit, the homepage is automatically regenerated with Vercel, see [template](https://github.com/oleeskild/digitalgarden). The static site generator [Eleventy](https://github.com/11ty/eleventy) installed there reads the folder of Markdown files, and applies their metadata object embedded in the frontmatter. Markdown gets pre-processed as Liquid templates, and build to HTML, see [documentation](https://www.11ty.dev/docs/languages/markdown/).

A Github webhook triggers the rebuild after each commit. Netlify provides the name servers and web hosting for my domain, and therefore updates the website directly on the Internet.

# How to publish dataview queries

The Digital Garden plugin automatically prints all [Dataview](obsidian://show-plugin?id=dataview) queries to markdown. Use [Dynamic Embed](obsidian://show-plugin?id=obsidian-dynamic-embed) plugin to use the same dataview query in multiple notes and every time from their own perspective. Digital Garden doesn't support Dynamic Embed natively but you can create a custom replace filter to publish the same output. For each embedded file replace like *List related notes* replace

```
```dynamic-embed(\n)\[\[List related notes\]\]\n```
```

with the content of the file and use `$1` to add a line break.

# Digital Garden plugin settings


Default Note Settings

- [x] Show home link (dg-home-link)
- [x] Show inline title (dg-show-inline-title)
- [x] Enable search (dg-enable-search)

Appearance Settings

- Theme: **Minimal**
- Sitename: **Anton's Digital Garden**
- Favicon: **attachments/favicon.svg**

Path rewrite rules

```
notes:
apps:
movies:
books:
theatrical plays:
```

# Custom Filters

- Change [Execute Code](./execute%20code.md)'s executable codeblocks to their regular language for syntax highlighting
- Replace [Dynamic Embed](./dynamic%20embed.md)'s blocks with the note's content. Use to following regex pattern and replace the note name

```
```dynamic-embed(\n)\[\[Describe this app and list installation sources\]\]\n```
```

Use `$1` to add a line break with pastes the grouped `(\n)` from the pattern
- If you paste text with line breaks, they get replaces with spaces
- Don't put a line break behind the `$1`

```
Setup my digital garden is a note$1- [[01 Introduction - Computer networks, Classification, Multiplexing, Standardization.md|01 Introduction - Computer networks, Classification, Multiplexing, Standardization]]

```

# Alternative publishing ideas

Obsidian Publish
- [c] expensive 
- [p] reliable
- [p] supprts graph view, canvas view 

11ty Vercel
- [p] free
- [p] supports Dataview, Math, regex replacements

Hugo
- [c] Doesn't support wikilinks
- https://quantick.dev/posts/obsidian-hugo
