---
title: "LaTeX to SVG - Embed LaTeX figures in markdown. Automate compiling, cropping, and exporting."
dg-publish: true
---
Dependencies

[TeX Live](https://www.tug.org/texlive/)
- `pdflatex`: Compile LaTeX source to PDF
- `texfot`: filter pdflatex stdout to only relevant messages , see [CTAN: Package texdoc](https://ctan.org/pkg/texdoc)
- `pdfcrop`: trim PDF of whitespace border, see [CTAN: Package pdfcrop](https://ctan.org/pkg/pdfcrop)

[pdf2svg](https://github.com/dawbarton/pdf2svg)
- Convert PDF to SVG

[Execute Code](./execute%20code.md)
- Generate LaTeX figure from Obsidian code block

# Setup Execute Code

Open Language-Specific Settings > Python

Disable: **Run Python blocks in Notebook Mode**

Inject python code

```python
def is_standalone_class(latex_source):
    import re
    return re.search(r'\\documentclass\s*(?:\[[^\]]*\])?\s*\{standalone\}', latex_source)

def compile_and_crop_figure(latex_source):
    import subprocess, uuid
    basename = "figure_" + str(uuid.uuid4())
    with open(basename + '.tex', 'w') as source_file:
        print(latex_source, file=source_file)
    subprocess.run(f'texfot pdflatex {basename}.tex', input=latex_source.encode(encoding="utf-8"), shell=True)
    if is_standalone_class(latex_source):
        subprocess.run(f'pdf2svg {basename}.pdf {basename}.svg', shell=True)
    else:
        subprocess.run(f'pdfcrop {basename}.pdf {basename}_cropped.pdf', shell=True)
        subprocess.run(f'pdf2svg {basename}_cropped.pdf {basename}.svg', shell=True)
    subprocess.run(f'del {basename}.tex {basename}.aux {basename}.log {basename}.pdf {basename}_cropped.pdf', shell=True)
    return f'{basename}.svg'

def print_figure(path):
    with open(path) as f:
        svg = f.read()
    @html(svg)

def export_figure(path, filename, directory):
    import shutil, os
    basename, ext = os.path.splitext(filename)
    if not ext:
        ext = '.svg'
    export_to = os.path.join(directory, basename + '.svg')
    try:
        shutil.copy2(path, export_to)
        print(f"Figure exported as: {export_to}")
    except IOError as e:
        print(f"Error exporting figure: {e}")

def delete_figure(path):
    import os
    os.remove(path)

def generate_latex_figure(latex_source, compiler="pdflatex", escape_shell=False, outfile=None):
    figure_file = compile_and_crop_figure(latex_source)
    if outfile:
        export_figure(figure_file, outfile, @vault_path + '/attachments/')
    print_figure(figure_file)
    delete_figure(figure_file)
```

Minimal example

```latex
\documentclass{standalone}
\begin{document}
Hello World!
\end{document}
```

Save figure as `figure hello world.svg`

```latex
\documentclass{standalone}
\begin{document}
Hello World!
\end{document}
```

![figure Hello world.svg](figure%20Hello%20world.svg)

Regular python code

```python {ignore='all'}
import uuid
print("figure_" + str(uuid.uuid4()))
```