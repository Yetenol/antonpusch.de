---
title: "LaTeX to SVG - Embed LaTeX figures in markdown. Automate compiling, cropping, and exporting."
dg-publish: true
---
# Dependencies

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

Inject python code

```python {ignore='global'}
import os, contextlib

def new_temporary_folder():
    import tempfile, uuid
    user_temp_directory = tempfile.gettempdir()
    new_subfolder = os.path.join(user_temp_directory, str(uuid.uuid4()))
    os.makedirs(new_subfolder)
    return new_subfolder
    
def save_source_to_file(latex_source, destination):
    import os
    file_path = os.path.join(destination,'figure.tex')
    with open(file_path, 'w') as source_file:
        print(latex_source, file=source_file)
    return file_path

@contextlib.contextmanager
def temporary_working_directory(path):
    current_dir = os.getcwd()
    try:
        os.chdir(path)
        yield
    finally:
        os.chdir(current_dir)

def is_standalone_class(latex_source):
    import re
    return re.search(r'\\documentclass\s*(?:\[[^\]]*\])?\s*\{standalone\}', latex_source)

def compile_and_crop_figure(latex_source, attachments_folder, compiler="pdflatex", escape_shell=False):
    import subprocess, tempfile
    intermediates_folder = tempfile.mkdtemp()
    input_file = save_source_to_file(latex_source, intermediates_folder)
    with temporary_working_directory(attachments_folder):
        subprocess.run(f'texfot pdflatex -output-directory={intermediates_folder} {input_file}', shell=True)
    with temporary_working_directory(intermediates_folder):
        if not is_standalone_class(latex_source):
            os.rename('figure.pdf', 'figure_precrop.pdf')
            subprocess.run('pdfcrop figure_precrop.pdf figure.pdf', shell=True)
        subprocess.run('pdf2svg figure.pdf figure.svg', shell=True)
    return intermediates_folder

def print_figure(filename, folder, vault_temporary_folder):
    import shutil, uuid
    source_file = os.path.join(folder, filename)
    vault_filename = str(uuid.uuid4()) + '.svg'
    vault_relative_file = f'/{vault_temporary_folder}/{vault_filename}'
    shutil.copy2(source_file, @vault_path + vault_relative_file)
    @html('<img src="' + @vault_url + vault_relative_file + '"/>')

def export_figure(filename, new_filename, source_folder, destination_folder):
    import shutil
    _, source_ext = os.path.splitext(filename)
    new_basename, filter_ext = os.path.splitext(new_filename)
    if filter_ext and source_ext != filter_ext:
        return
    copy_from = os.path.join(source_folder, filename)
    copy_to = os.path.join(destination_folder, new_basename + source_ext)
    try:
        shutil.copy2(copy_from, copy_to)
        print(f"Figure exported as: {copy_to}")
    except IOError as e:
        print(f"Error exporting figure: {e}")

def delete_figure(folder_path):
    files_to_delete = ['figure.tex', 'figure.aux', 'figure.log', 'figure_precrop.pdf', 'figure.pdf', 'figure.svg']
    for filename in files_to_delete:
        file_path = os.path.join(folder_path, filename)
        if os.path.exists(file_path):
            os.remove(file_path)
    os.rmdir(folder_path)

def generate_latex_figure(latex_source, compiler="pdflatex", escape_shell=False, outfile=None, keep_intermediates=False):
    assets_folder = os.path.join(@vault_path, 'attachments/')
    figure_folder = compile_and_crop_figure(latex_source, assets_folder)
    if outfile:
        export_figure('figure.svg', outfile, figure_folder, assets_folder)
        export_figure('figure.pdf', outfile, figure_folder, assets_folder)
    print_figure('figure.svg', figure_folder, '.temp')
    if not keep_intermediates:
        delete_figure(figure_folder)

generate_latex_figure(r"""
\documentclass{standalone}
\begin{document}
Hello World!
\end{document}
""", outfile='figure hello world')
```

Minimal example
![](file:///C:\Users\anton\AppData\Local\Temp\tmpw5wyk1ko\figure.svg)

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

![figure hello world.svg](./attachments/figure%20hello%20world.svg)

Regular python code

```python {ignore='all'}
import uuid
print("figure_" + str(uuid.uuid4()))
@show(@vault_url + '/attachments/.temp.svg')
```
