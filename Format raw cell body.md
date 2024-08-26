$$
\begin{align*}
2.5 \cdot 10^{-1}, 0.25, \tfrac{1}{4}, \dfrac{1}{4}, {}^1\!/_{\!4} \\
1{,}20\, \text{€}, 
\end{align*}
$$

- pgfmathparse
- texttt for commands
- dash 3rd line
- math, siunit, pgfmathparse, date, money, command, macro, bold, color, fraction styles
- dateformat, fraction format, yes/no symbol, 

![minimal 75.svg](./content/attachments/minimal%2075.svg)

```latex
\documentclass{article}\pagestyle{empty}\renewcommand{\thetable}{1\alph{table}}
\usepackage{tabularray,mathtools,codehigh,pgfplotstable}
\newcolumntype{L}[1]{>{\begin{pgfplotstablecoltype}[#1]}r<{\end{pgfplotstablecoltype}}}
\UseTblrLibrary{diagbox}
\UseTblrLibrary{siunitx}
\SetTblrOuter{tall,caption}
\SetTblrInner{baseline=T}
\pgfplotsset{compat=1.18}
\begin{document}
\noindent
\begin{tblr}[caption=Inline formatting]{colspec={l},hline{1,Z}={.08em},hline{2},row{1}={font=\bfseries},  }
Lower & Upper \\
$\alpha$ \fakeverb{\alpha} & $A$ \fakeverb{A} \\
$\beta$  \fakeverb{\beta} & $B$ \fakeverb{B} \\
$\gamma$ \fakeverb{\gamma} & {$\Gamma$ \fakeverb{\Gamma} \\ $\varGamma$ \fakeverb{\varGamma}} \\
$\delta$ \fakeverb{\delta} & {$\Delta$ \fakeverb{\Delta} \\ $\varDelta$ \fakeverb{\varDelta}} \\
\end{tblr}
\hspace{1em}
\begin{tblr}[caption=Number formatting]{colspec={rrrr},hline{1,Z}={.08em},hline{2},row{1}={font=\bfseries,halign=c}, 
    cell{2-Z}{2}={mode=math}, 
    cell{2-Z}{3}={cmd=\pgfmathprintnumber}, 
    cell{2-Z}{4}={cmd=\num} }
String     & Math       & PgfMath     & SiUnitX     \\
4225       & \alpha     & 4225       & 4225       \\
16641      & 16641      & 16641      & 16641      \\
66049      & 66049      & 66049      & 66049      \\
1.050625e6 & 1.050625e6 & 1.050625e6 & 1.050625e6 \\
\end{tblr}

\vspace{1em}\noindent
\begin{tblr}{colspec={rl}, hline{1,Z}={.08em},hline{2},row{1}={font=\bfseries,halign=c}, 
    cell{2-Z}{1}={font=\ttfamily}  }
command & Description \\
calc & Calculator \\
cmd & Command Prompt \\
control & Control Panel \\
\end{tblr}
\hspace{1em}
\begin{tblr}{hline{1,Z}={.08em},hline{2},row{1}={font=\bfseries,halign=c},}
Float1 & Float2 \\
$2.5 \cdot 10^{-1}$ & 
$0.25$ &
$\frac{1}{4}$ &
$^1\!/_{\!4}$ \\
\end{tblr}
\end{document}
```

# Format numbers

![minimal 76.svg](./content/attachments/minimal%2076.svg)

```latex
\documentclass{article}\pagestyle{empty}\renewcommand{\thetable}{1\alph{table}}
\usepackage{tabularray,mathtools,codehigh,tikz}
\UseTblrLibrary{siunitx}
\sisetup{exponent-product = \cdot}
\SetTblrOuter{tall,caption}
\SetTblrInner{baseline=T}
\usetikzlibrary{fpu}
\begin{document}
\noindent
\begin{tblr}[caption=Inline formatting]{
    colspec={},
    column{2}={font=\ttfamily},
    hline{1,Z}={.08em},hline{2},row{1}={font=\bfseries} }
Raw Input & Monospace &  \\
calc.exe & calc.exe & \\
cmd.exe & cmd.exe & \\
\end{tblr}

\vspace{1em}\noindent
\begin{tblr}[caption=Inline formatting]{
    colspec={r
    Q[r,cmd={\pgfmathprintnumber}]
    Q[r,cmd={\pgfkeys{/pgf/number format/.cd,sci,sci subscript}\pgfmathprintnumber}]
    Q[r,cmd={\pgfkeys{/pgf/number format/.cd,frac}\pgfmathprintnumber}]
    Q[r,cmd={\num}]
    },
    hline{5,8,11,14,17}={dashed},hline{1,Z}={.08em},hline{2},row{1}={halign=c,font=\bfseries,cmd={}} }
Raw Input & float & sci & frac & num  \\
0.25     & 0.25     & 0.25     & 0.25     & 0.25     \\
42       & 42       & 42       & 42       & 42       \\
289      & 289      & 289      & 289      & 289      \\
4225     & 4225     & 4225     & 4225     & 4225     \\
66049    & 66049    & 66049    & 66049    & 66049    \\
263169   & 263169   & 263169   & 263169   & 263169   \\
1.0563e6 & 1.0563e6 & 1.0563e6 & 1.0563e6 & 1.0563e6 \\
\end{tblr}
\end{document}
```