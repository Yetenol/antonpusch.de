---
date: "2025-03-22T23:45:55.003+01:00"
title: "Execute Code"
description: "-"
dg-folder: computer/apps
dg-publish: true
not-in-use: false
microsoft-id: 
winget-id: 
github-repo: twibiral/obsidian-execute-code
github-release-filename: 
website: 
priority: 
link-modportals: 
modportal0-id: execute-code
thumbnail: 
categories:
  - Programming
synopsis: Execute code snippets within a note.
extends-app: "[[Obsidian|Obsidian]]"
---

```dynamic-embed
[[Describe this app and list installation sources]]
```

Open Haskell language-specific settings
- [x] Use Ghci - Run haskell code with ghci instead of runghc


# Combines setup

- [LaTeX to SVG - Embed LaTeX figures in markdown. Automate compiling, cropping, and exporting.](../../LaTeX-to-SVG)
- [PyX](./PyX.md)
- [MatPlotLib PyPlot](./MatPlotLib-PyPlot.md)

```python
import os, contextlib

def save_source_to_file(latex_source, destination):
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

def compile_and_crop_figure(latex_source, attachments_folder, compiler="pdflatex", escape_shell=False, rerun=0):
    import subprocess, tempfile
    intermediates_folder = tempfile.mkdtemp()
    input_file = save_source_to_file(latex_source, intermediates_folder)
    with temporary_working_directory(attachments_folder):
        subprocess.run(['texfot', 'pdflatex', 
            f'-output-directory={intermediates_folder}', input_file])
        for _ in range(rerun):
            subprocess.run(['texfot', 'pdflatex',
                f'-output-directory={intermediates_folder}', input_file])
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
    files_to_delete = ['figure.tex', 'figure.aux', 'figure.log', 'figure.out', 'figure.lot', 'figure_precrop.pdf', 'figure.pdf', 'figure.svg']
    for filename in files_to_delete:
        file_path = os.path.join(folder_path, filename)
        if os.path.exists(file_path):
            os.remove(file_path)
    os.rmdir(folder_path)

def generate_latex_figure(latex_source, compiler="pdflatex", escape_shell=False, outfile=None, keep_intermediates=False, rerun=0):
    assets_folder = os.path.join(@vault_path, 'attachments/')
    figure_folder = compile_and_crop_figure(latex_source, assets_folder, rerun=rerun)
    if outfile:
        export_figure('figure.svg', outfile, figure_folder, assets_folder)
        export_figure('figure.pdf', outfile, figure_folder, assets_folder)
    print_figure('figure.svg', figure_folder, '.temp')
    if not keep_intermediates:
        delete_figure(figure_folder)

def export_and_show_pyx_figure(pyx_graph, outfile=None):
    if (outfile):
        g.writeSVGfile(@vault_path + '/attachments/' + outfile)
        g.writePDFfile(@vault_path + '/attachments/' + outfile)
    g.writeSVGfile(@vault_path + '/attachments/.temp')
    @show(@vault_url + '/attachments/.temp.svg')

def export_plt_figure(plt_graph, outfile=None, crop=False):
    basename = @vault_path + '/attachments/' + outfile
    if (not outfile):
        return
    if (crop):
        plt.savefig(basename + '.svg', transparent=True, \
            bbox_inches='tight', pad_inches=0)
        plt.savefig(basename + '.pdf', transparent=True, \
            bbox_inches='tight', pad_inches=0)
        return
    plt.savefig(basename + '.svg', transparent=True)
    plt.savefig(basename + '.pdf', transparent=True)
```
