Dependencies

- [TeX Live](https://www.tug.org/texlive/): pdflatex, texfot, pdfcrop
- [pdf2svg](https://github.com/dawbarton/pdf2svg): pdf2svg
- [Execute Code](./content/execute%20code.md)

# Setup Execute Code

Open Language-Specific Settings > Python

Disable: **Run Python blocks in Notebook Mode**

Inject python code

```python
def compile_and_crop_figure(latex_source):
    import subprocess, uuid
    basename = "figure_" + str(uuid.uuid4())
    with open(basename + '.tex', 'w') as source_file:
        print(latex_source, file=source_file)
    subprocess.run(f'texfot pdflatex {basename}.tex', input=latex_source.encode(encoding="utf-8"), shell=True)
    subprocess.run(f'pdfcrop {basename}.pdf {basename}_cropped.pdf', shell=True)
    subprocess.run(f'pdf2svg {basename}_cropped.pdf {basename}.svg', shell=True)
    subprocess.run(f'del {basename}.tex {basename}.aux {basename}.log {basename}.pdf {basename}_cropped.pdf', shell=True)
    return f'{basename}.svg'

def print_figure(path):
    with open(path) as f:
        svg = f.read()
    @html(svg)

def export_figure_if_titled(path, latex_source):
    import shutil, re
    title_match = re.search(r'\\title\{([^}]+)\}', latex_source)
    if not title_match:
        return
    clean_title = re.sub(r'[^a-zA-Z0-9\-]+', ' ', title_match.group(1))
    export_to = @vault_path + '/attachments/figure ' + clean_title + ".svg"
    try:
        shutil.copy2(path, export_to)
        print(f"Figure exported as: {export_to}")
    except IOError as e:
        print(f"Error exporting figure: {e}")

def delete_figure(path):
    import os
    os.remove(path)

def generate_latex_figure(codeblock):
    figure_file = compile_and_crop_figure(codeblock)
    export_figure_if_titled(figure_file, codeblock)
    print_figure(figure_file)
    delete_figure(figure_file)
```

Generate LaTeX figures from code blocks marked as python in this file by parsing them as a multiline string parameter.

```python {pre}
generate_latex_figure(r"""
```

```python {post}
""")
```

Example latex figure

```python
\documentclass{standalone}
\title{Hello world}
\begin{document}
Hello World
\end{document}
```

![figure Hello world.svg](./content/attachments/figure%20hello%20world.svg)

Regular python code

```python {ignore='all'}
import uuid
print("figure_" + str(uuid.uuid4()))
```