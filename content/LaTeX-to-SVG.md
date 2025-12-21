---
date: "2025-07-17T08:13:58.366+02:00"
title: "LaTeX to SVG"
description: "Embed LaTeX figures in markdown. Automate compiling, cropping, and exporting."
dg-publish: true
---
# Dependencies

[TeX Live](./computer/apps/TeX-Live.md)
- Install from website [Easy install - tug.org](https://www.tug.org/texlive/windows.html) 
- Provides `pdflatex` to compile LaTeX source code to PDF
- Provides `texfot` to filter pdflatex stdout to only relevant messages , see [CTAN: Package texfot](https://ctan.org/pkg/texfot)
- Provides `pdfcrop` to trim PDF of whitespace border, see [CTAN: Package pdfcrop](https://ctan.org/pkg/pdfcrop)

[pdf2svg](./computer/apps/pdf2svg)
- Convert PDF to SVG
- Clone repository [dawbarton/pdf2svg](https://github.com/dawbarton/pdf2svg)
- Add `dist-64bits` subfolder to PATH environment variable

[Execute Code](./computer/apps/Execute-Code.md)
- Install Obsidian extension via Comminity plugins, Webstore
- Generate LaTeX figure from Obsidian code block

Python
- [Python](./computer/apps/Python.md)
- Install from website [Downloads - python.org](https://www.python.org/downloads/)
- Execute tools from Obsidian code blocks

# Setup Execute Code

Open Language-Specific Settings > Python

Inject python code

```python {ignore='global'}
import contextlib
@contextlib.contextmanager
def change_working_directory(path):
    import os
    current_dir = os.getcwd()
    try:
        os.chdir(path)
        yield
    finally:
        os.chdir(current_dir)
def export_figure(filename, new_filename, destination_folder):
    import shutil, os
    if not new_filename:
        return
    _, source_ext = os.path.splitext(filename)
    new_basename, filter_ext = os.path.splitext(new_filename)
    if filter_ext and source_ext != filter_ext:
        return
    copy_to = os.path.join(destination_folder, new_basename + source_ext)
    try:
        shutil.copy2(filename, copy_to)
        print(f"Figure exported as: {copy_to}")
    except IOError as e:
        print(f"Error exporting figure: {e}")
def delete_figure(folder_path):
    import os
    files_to_delete = ['figure.tex', 'figure.aux', 'figure.log', 
        'figure.out', 'figure.lot', 'figure_precrop.pdf', 
        'figure.pdf', 'figure.svg']
    for filename in files_to_delete:
        file_path = os.path.join(folder_path, filename)
        if os.path.exists(file_path):
            os.remove(file_path)
    os.rmdir(folder_path)
def show_svg_figure(filename, folder, vault_temporary_folder):
    import shutil, uuid, os
    source_file = os.path.join(folder, filename)
    vault_filename = str(uuid.uuid4()) + '.svg'
    vault_relative_file = f'/{vault_temporary_folder}/{vault_filename}'
    shutil.copy2(source_file, @vault_path + vault_relative_file)
    @html('<img src="' + @vault_url + vault_relative_file + '"/>')

def save_input_to_tex_file(latex_input):
    with open('figure.tex', 'w') as source_file:
        print(latex_input, file=source_file)
def is_standalone_class(latex_input):
    import re
    return re.search(r'\\documentclass\s*(?:\[[^\]]*\])?\s*' + 
        r'\{standalone\}', latex_input)
def add_default_documentclass(latex_input):
    import re
    has_documentclass = re.search(r'\\documentclass[\s{\[]', latex_input)
    if has_documentclass:
        return latex_input
    return r'\documentclass{article}\pagestyle{empty}' + '\n' + \
        latex_input

def build_figure(attachments_folder, compiler="pdflatex", 
escape_shell=False, rerun=0):
    import subprocess, tempfile, os
    compiler = compiler.lower()
    if compiler not in {'pdflatex', 'xelatex', 'lualatex'}:
        compiler = 'pdflatex'
    build_folder = os.getcwd()
    build_command = ['texfot', compiler, 
        f'-output-directory={build_folder}', 'figure.tex']
    with change_working_directory(attachments_folder):
        for _ in range(1+rerun):
            subprocess.run(build_command)
def crop_pdf_to_content():
    import subprocess, os
    os.rename('figure.pdf', 'figure_precrop.pdf')
    subprocess.run('pdfcrop figure_precrop.pdf figure.pdf', shell=True)
def convert_pdf_to_svg():
    import subprocess
    subprocess.run('pdf2svg figure.pdf figure.svg', shell=True)

def generate_latex_figure(latex_input, compiler="pdflatex", 
escape_shell=False, outfile=None, keep_log=False, rerun=0, to_svg=True):
    import tempfile, os
    assets_folder = os.path.join(@vault_path, 'attachments/')
    build_folder = tempfile.mkdtemp()
    latex_input = add_default_documentclass(latex_input)
    with change_working_directory(build_folder):
        save_input_to_tex_file(latex_input)
        build_figure(assets_folder, compiler, escape_shell, rerun)
        if not is_standalone_class(latex_input):
            crop_pdf_to_content()
        if to_svg:
            convert_pdf_to_svg()
            export_figure('figure.svg', outfile, assets_folder)
        export_figure('figure.pdf', outfile, assets_folder)
    if to_svg:
        show_svg_figure('figure.svg', build_folder, '.temp')
    if not keep_log:
        delete_figure(build_folder)

generate_latex_figure(r"""
\documentclass{standalone}
\begin{document}
Hello World!
\end{document}
""")
```

![figure.pdf](./figure.pdf)

Minimal example

```py
generate_latex_figure(r"""
\documentclass{standalone}
\begin{document}
Hello World!
\end{document}
""")
```

Save figure as `figure hello world.svg`

```py
generate_latex_figure(r"""
\documentclass{standalone}
\begin{document}
Hello World!
\end{document}
""", outfile="figure hello world")
```

![figure hello world.svg](./figure-hello-world.svg)

Rerun to get cross-references right

```py
generate_latex_figure(r"""
\documentclass{article} \pagestyle{empty}
\usepackage{mathtools}
\begin{document}
I use \eqref{eq:einstein} a lot.
\[
    E = mc^2 \tag{1}\label{eq:einstein}
\]
\end{document}
""", rerun=True)
```

Regular python code

```python {ignore='all'}
import uuid
print("figure_" + str(uuid.uuid4()))
@show(@vault_url + '/attachments/.temp.svg')
```


```python {ignore='global'}
def check_file_for_patterns(file_path):
    import re
    patterns = [
        r"Rerun to get cross-references right",
        r"Rerun to get outlines right",
        r"Label\(s\) may have changed\. Rerun"
    ]
    
    with open(file_path, 'r') as file:
        content = file.read()
        
    for pattern in patterns:
        if re.search(pattern, content):
            return True
    
    return False

if check_file_for_patterns(r'C:\Users\anton\AppData\Local\Temp\tmpxnojtw_g\figure.log'):
    print("Rerun needed. Will compile again.")
else:
    print("No rerun needed. Compilation complete.")
```


---
Sources:

Related:

Tags:
[TeX Live](./computer/apps/TeX-Live.md)
[pdf2svg](./computer/apps/pdf2svg)
[Python](./computer/apps/Python.md)
