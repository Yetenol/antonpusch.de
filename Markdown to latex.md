- only accept environments `\[` and `align*`
- force line breaks in math block
```
$$
asd
$$
```
- lint `\lt` to `<`, `gt` to `>`
- keep line break after before math block for correct page breaking


Update equation numbers and temporarily show equation references

```powershell
explorer "`"obsidian://advanced-uri?commandname=Copy as Latex: Copy as Latex`""
Start-Sleep 1
Get-Clipboard -Raw | foreach {
    $_ -replace 
    '^[\s\n]*\\subsection\{[\s\w-]*:[\s\w-]*\}\s*\n','' -replace # remove possible wrong heading of last frontmatter attribute
    '\n\$\$\s*\n(?=\\begin\{align\*\})', '' -replace # prevent erroneous nesting of equation structures (align* in $$...$$)
    '(?<=\\end\{align\*\})\s*\n\$\$', "`n" -replace # same as above
    '(?<=\\(sub)*)section(?=\{\d)', 'section*' -replace # don't numerate headings twice
    '(?<=\\)vphantom(?=\{eq:)', 'label' -replace # activate equation labels
    '\\tag(\*?)\{((?:\$|\\\().*?(?:\$|\\\)))\}', '\\tag$1{\\ensuremath{$2}}' # prevent overleaf from thinking there is text in a math environment
    '(?<=\$\$|\\\]|\\end\{align\*\})\n(?=\w)', "`n`n" -replace # add empty line after math blocks
    '\$\$((?:[^$].*?\n)*?)\$\$', "\[`$1\]`n" # allow tag placement in default math block (converts $$..$$ to \[..\])
} | foreach {
"\documentclass{article}`n\usepackage{amsmath,amssymb,mathtools}`n\usepackage[colorlinks=true, linkcolor=blue]{hyperref}`n\begin{document}`n`n$_`n`n\end{document}"
} | Set-Clipboard
```

```powershell
Add-Type -AssemblyName System.Windows.Forms

$saveFileDialog = New-Object System.Windows.Forms.SaveFileDialog
$saveFileDialog.Title = "Save generated PDF as"
$saveFileDialog.Filter = "PDF Files (*.pdf)|*.pdf|All Files (*.*)|*.*"
$saveFileDialog.FilterIndex = 1
$saveFileDialog.FileName = ".pdf"

if ($saveFileDialog.ShowDialog() -ne [System.Windows.Forms.DialogResult]::OK) {
    throw "No file path selected."
}
$exportFilePath = $saveFileDialog.FileName
Write-Host "Selected export file path: $exportFilePath"
```

```powershell
"\documentclass{article}`n\usepackage{amsmath,amssymb,mathtools}`n\usepackage[colorlinks=true, linkcolor=blue]{hyperref}`n\begin{document}`n$_`n\end{document}"
```

Copy as LaTeX

- Remove frontmatter

Fix nested equation syntax
- delete following two regex patterns
```regex
\$\$\s*\n(?=\\begin\{align\*\})
```
- and delete
```regex
(?<=\\end\{align\*\})\s*\n\$\$
```


Don't numerate headings twice (detect headings starting with digit)

```regex
(?<=\\(sub)*)section(?=\{\d)
```
- replace with
```
section*
```

Fix labels

```regex
(?<=\\)vphantom(?=\{eq:)
```

```
label
```

Convert `$$` to `equations*` to allow `\tag{1}` placement

```regex
\$\$((?:[^$]*\n)*?)\$\$
```

```
\[$1\]
```


---
Sources:

Related:

Tags:
[Document conversion](Document%20conversion.md)