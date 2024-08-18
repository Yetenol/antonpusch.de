---
title: "Convert wikilinks to markdown links"
dg-publish: true
---
- https://github.com/zoni/obsidian-export



```powershell
$pattern = '\[\[(?<target>.*?)\]\]'
Get-ChildItem -Filter "*.md" |
foreach { 
    $file = $_.FullName
    $content = Get-Content -Path $file -Raw   # output as one string

    [RegEx]::Matches($content, $pattern) |   # output all regex matches
    foreach { 
        $Target = $_.Groups["target"].value
        $Match = $_.Groups[0].value
        $Encoded = $Target -replace ' ', '%20'
        $Replace = "[$Target]($Encoded)"
        $content = $content -replace [RegEx]::Escape($Match), $Replace
    }

    Set-Content -Path $file -Value $content
}
```

---
Sources:

Related:

Tags:
[Obsidian](./obsidian.md)
[Markdown - Write content-focused and format with hierarchy, abstract highlighting, and meta-information](./markdown.md)
[Document conversion](Document%20conversion.md)