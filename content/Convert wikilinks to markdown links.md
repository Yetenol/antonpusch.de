---
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
[Obsidian](./Obsidian.md)
[Markdown - Write content-focused and format with hierarchy, abstract highlighting, and meta-information](./Markdown%20-%20Write%20content-focused%20and%20format%20with%20hierarchy,%20abstract%20highlighting,%20and%20meta-information.md)
[Document conversion](Document%20conversion.md)