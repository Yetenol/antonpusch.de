---
dg-publish: true
---

# Placement Specifiers

```latex
\begin{⟨float environment⟩}[⟨placement specifiers⟩]
\end{⟨float environment⟩}
```

| Specifier          | Name    | Add placement option                                                              |
| ------------------ | ------- | --------------------------------------------------------------------------------- |
| _empty_ <br> `tbp` | default | Put if at the top, bottom of the _next available_ page or on a floats-only page.  |
| `!`                | force   | Force the following settings, without considerung most of the internal parameter. |
| `h`                | here    | Put it exactly where we say it should go.                                         |
| `t`                | top     | Put it at the top of the _next available_ page.                                   |
| `b`                | bottom  | Put it at the bottom of the _next available_ page.                                |
| `p`                | page    | Put it on a special page containing only floats.                                  |

Example

```latex
\begin{figure}[htbp]
\end{figure}
```

# Images

```latex
\begin{figure}  % or \begin{figure}[⟨placement specifiers⟩]
    \centering
    \caption{⟨caption⟩}  % or \caption[⟨listoftables caption⟩]{⟨caption⟩}
    \label{fig:⟨label⟩}
    \includegraphics[width=0.75\columnwidth]{⟨filename⟩}
\end{figure}
```

- `⟨caption⟩`: displayed name of the figure
- `⟨listoftables caption⟩`: (optional) replaces the entry in the list of figures with a shorter version
- `⟨label⟩`: label to reference the figure using `\ref{fig:⟨label⟩}`
- `⟨filename⟩`: file path (with extension) of the image 

# Source Code Listings

```latex
\begin{figure}  % or \begin{figure}[⟨placement⟩]
    \centering
    \lstset{caption = {⟨caption⟩}}
    \lstset{label = code:⟨label⟩}
    \lstinputlisting[language = matlab]{⟨filename⟩}
\end{figure}
```

# Directories

```latex
\listoftables       % Tabellenverzeichnis
\listoffigures      % Abbildungsverzeichnis
\lstlistoflistings  % Codelistenverzeichnis
```

TODO: Tufte Design  floats in separate columns next to main content

---

Sources:

Related:

Tags:
[Graphical elements - Standardize tables, images, plots](./graphical%20elements.md)
