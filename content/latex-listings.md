---
title: "Listings - Print source code with syntax highlighting in latex with listings"
dg-publish: true
dg-permalink: latex-listings
---
# Syntax

```latex
\documentclass{article}
\usepackage{yetenol-styles}
\lstset{style=⟨global style⟩}
\begin{document}

\verb`⟨inline source code⟩`

\begin{lstlisting}[language=⟨code language⟩]
⟨block source code⟩
\end{lstlisting}

\begin{lstinputlisting}[language=⟨code language⟩]{⟨file with source code⟩}
\end{lstinputlisting}

\end{document}
```

- **⟨global style⟩**: configure **all** code snippets
- **⟨code language⟩**: configure language for code **highlighting**
- **⟨inline source code⟩**: verbatim code to be printed within **text**
- **⟨block source code⟩**: verbatim code to be printed as a **tile**
- **⟨file with source code⟩**: relative path of the **file** to be printed
- [p] minimal formatting information when creating the snippet; style **definitions** are moved to the **preamble**
- [p] the code is **independent** of the project: no user-defined macros; clearly shows which package highlights the code

Input code from file, block, or inline

Layouts
dots, colorful
Longcode split
Documentation
Latex code
code in table
Supported languages
Create custom language
Multiple languages

# Examples

- import the file [yetenol-styles.sty](latex-listings.md#Styling%20setup) for the required style definitions

Add **inline** code within a paragraph.

```latex
\documentclass{article}
\usepackage{yetenol-styles}
\lstset{style=block}
\begin{document}

Refer to the manual in \verb`README.md` for further information.

\end{document}
```

![inline code.svg](./attachments/inline%20code.svg)

Create a code **block**

```latex
\documentclass{article}
\usepackage{yetenol-styles}
\lstset{style=block}
\begin{document}

\begin{lstlisting}[language=python]
# Mauris viverra massa id lorem pretium gravida.

if num == 1:
  print(num, "is not a prime.")
elif num > 1:
  for i in range(2, num):
    if (num % i) == 0:
      print(num, "is a prime.")
      break
\end{lstlisting}

\end{document}
```

![code block.svg](./attachments/code%20block.svg)

Print a source **file**'s content

```latex
\documentclass{article}
\usepackage{yetenol-styles}
\lstset{style=colorful}
\begin{document}

\begin{lstinputlisting}[language=python]{resources/script.py}
\end{lstinputlisting}

\end{document}
```

![code file colorful.svg](./attachments/code%20file%20colorful.svg)

Add a snippet **caption** and a **label** for cross references

```latex
\documentclass{article}
\usepackage{yetenol-styles}
\lstset{style=block}
\begin{document}

A python script file listed in snippet \ref{code:is-prime} tests if the given number is prime.

\begin{figure}\begin{lstlisting}[language=python]
# Mauris viverra massa id lorem pretium gravida.

if num == 1:
  print(num, "is not a prime.")
elif num > 1:
  for i in range(2, num):
    if (num % i) == 0:
      print(num, "is a prime.")
      break
\end{lstlisting}\caption{Test for prime number}\label{code:is-prime}
\end{figure}

\end{document}
```

![caption label code.svg](./attachments/caption%20label%20code.svg)

# Add custom styling

Use key-value pairs to configure code snippets of the listings package

- `alsolanguage`
- [2.3 The key=value interface | Listings Package](https://texdoc.org/serve/listings/0#page=12)
- [keyval package](https://texdoc.org/serve/keyval/0)
- [Example of key-value list | 1.3 Figure out the appearance | Listings Package](https://texdoc.org/serve/listings/0#page=6)
- [2.4 Predefined languages | Listings Package](https://texdoc.org/serve/listings/0#page=13)

# Styling setup

Manually add the file `yetenol-styles.sty`

```latex
\NeedsTeXFormat{LaTeX2e}
\ProvidesPackage{yetenol-styles}[]
\RequirePackage{listings} %%%%%%%%%% STYLE CODE LISTINGS %%%%%%%%%%
\RequirePackage{float}  %%%%% By default place tables at precisely their location in the code
\floatplacement{figure}{H}
\RequirePackage{etoolbox} %%%%% if style=yetenol, apply inline and block styles
\AtBeginEnvironment{lstlisting}{\noindent{\tiny\dotfill}}
\AfterEndEnvironment{lstlisting}{\tiny\dotfill\renewcommand{\figurename}{Snippet}}
\AtBeginEnvironment{lstinputlisting}{\noindent{\tiny\dotfill}}
\AfterEndEnvironment{lstinputlisting}{\tiny\dotfill\renewcommand{\figurename}{Snippet}}
\RequirePackage{xcolor} %%%%% Code block default style
\lstdefinestyle{dots}{
    basicstyle=\ttfamily\scriptsize,
    commentstyle=\color[rgb]{0.5,0.5,0.5},
    breaklines=true,
    numbers=left,
    numberstyle=\tiny,
    numbersep=7pt,
    aboveskip=0.5em,
    belowskip=0em,
    showstringspaces=false,
    xleftmargin=14pt,
    postbreak=\mbox{\hspace{-2.5em}\textcolor{gray}{$\hookrightarrow$}\space\space},
}
\definecolor{codegreen}{rgb}{0,0.6,0}
\definecolor{codegray}{rgb}{0.5,0.5,0.5}
\definecolor{codepurple}{rgb}{0.58,0,0.82}
\definecolor{backcolour}{rgb}{0.95,0.95,0.92}
\lstdefinestyle{colorful}{
  backgroundcolor=\color{backcolour},   
  commentstyle=\color{codegreen},
  keywordstyle=\color{magenta},
  numberstyle=\tiny\color{codegray},
  stringstyle=\color{codepurple},
  basicstyle=\ttfamily\footnotesize,
  breakatwhitespace=false,         
  breaklines=true,                 
  captionpos=b,                    
  keepspaces=true,                 
  numbers=left,                    
  numbersep=5pt,                  
  showspaces=false,                
  showstringspaces=false,
  showtabs=false,                  
  tabsize=2
}
\lstdefinestyle{lines}{
  belowcaptionskip=1\baselineskip,
  breaklines=true,
  frame=L,
  xleftmargin=\parindent,
  language=C,
  showstringspaces=false,
  basicstyle=\footnotesize\ttfamily,
  keywordstyle=\bfseries\color{green!40!black},
  commentstyle=\itshape\color{purple!40!black},
  identifierstyle=\color{blue},
  stringstyle=\color{orange},
}
```

# Alternatives

Create an abbreviation macro for `\lstinline`

```latex
\documentclass{article}
\RequirePackage{listings}
\lstMakeShortInline`
\begin{document}

Try the package `\usepackage{amsmath}` instead.

\end{document}
```

[Deprecated latex listings](Deprecated%20latex%20listings.md)

---
Sources:

Related:
- [LaTeX - Typeset mathematical and scientific notation, handle cross-referencing and citations, and position images according to defined placement rules](./latex.md)
- [Markup and typesetting systems - Produce printed or digital documents aesthetically pleasing with readable typography](./markup%20and%20typesetting%20systems.md)
- [Style presets - Format your document after you written the content in Word, Latex, Markdown](Style%20presets%20-%20Format%20your%20document%20after%20you%20written%20the%20content%20in%20Word,%20Latex,%20Markdown.md)


Tags:
[Graphical elements - Standardize tables, images, plots](./graphical%20elements.md)