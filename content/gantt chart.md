---
title: "Gantt chart"
dg-publish: true
---
- page width chart `expand chart`
- arrows between bars
- month, quartal, year, week
- spacing `y unit title`
- less grid
- today
- multiline text
- custom title, calendar title

Portfolio examination

![gantt portfolio examination.svg](./attachments/gantt%20portfolio%20examination.svg)

```latex
\documentclass{standalone}
\usepackage{pgfgantt}
\begin{document}
\begin{ganttchart}[
    hgrid, vgrid={*{5}{draw=none}, dotted, {draw=none}}, 
    x unit=.7mm, y unit title=6mm,
    title height=1,
    time slot format=isodate,
]{2024-10-01}{2025-03-31}
\gantttitlecalendar{year, month=shortname} \\
\ganttgroup{First attempt}{2024-11-15}{2025-02-25} \\
\ganttbar{Homework 1}{2024-11-15}{2024-12-01} \\
\ganttlinkedbar{Homework 2}{2024-12-10}{2025-01-08} \\ 
\ganttlinkedmilestone{Exam A}{2025-02-25} \\
\ganttmilestone{Exam B}{2025-03-23}
\ganttlink[link mid=.32]{elem2}{elem4} \\[solid]
\ganttgroup{Second attempt}{2025-03-10}{2025-03-23} \\
\ganttbar{Homework 1a}{2025-03-10}{2025-03-14} 
\ganttlink[link/.append style={dashed}]{elem3}{elem6} \\
\ganttlinkedbar[link type=dr]{Homework 2a}{2025-03-15}{2025-03-19} \\
\ganttlinkedmilestone{Exam B}{2025-03-23}
\end{ganttchart}
\end{document}
```




![gantt chart 2.svg](./attachments/gantt%20chart%202.svg)

```latex
\documentclass{standalone}
\usepackage{pgfgantt}
\begin{document}
\begin{ganttchart}[
    hgrid, 
    vgrid={*{6}{draw=none}, dotted}, 
    x unit=2pt,
    time slot format=isodate,
]{2024-10-01}{2025-03-31}
\gantttitlecalendar{year, month=shortname} \\
\ganttgroup{Lecture period}{2024-10-14}{2024-12-23}
\ganttgroup{}{2025-01-05}{2025-02-15} \\
\ganttbar{Homework 1}{2024-11-15}{2024-12-01} \\
\ganttlinkedbar{Homework 2}{2024-12-10}{2025-01-04} \\ 
\ganttlinkedmilestone{Test paper}{2025-01-20} \\
\ganttgroup{Exam period}{2025-02-17}{2025-03-31} \\
\ganttmilestone{Exam A}{2025-02-25} \\
\ganttlinkedmilestone{Exam B}{2025-03-23} \\
\end{ganttchart}
\end{document}
```


First and second attempt

![gantt chart 7.svg](./attachments/gantt%20chart%207.svg)

```latex
\documentclass{standalone}
\usepackage{pgfgantt}
\begin{document}
\begin{ganttchart}[
    vgrid={*{5}{draw=none}, dotted, {draw=none}}, 
    x unit=.7mm, y unit title=6mm,
    title height=1,
    time slot format=isodate,
]{2024-10-01}{2025-03-31}
\gantttitlecalendar{year, month=shortname} \\
\ganttbar{Homework 1}{2024-11-15}{2024-12-01} \\
\ganttlinkedbar{Homework 2}{2024-12-10}{2025-01-08} \\ 
\ganttlinkedmilestone{Exam A}{2025-02-25} \\
\ganttmilestone{Exam B}{2025-03-23} \\
\ganttlink[link mid=.32]{elem1}{elem3}
\end{ganttchart}
\end{document}
```



Time and weight

![gantt chart 3.svg](./attachments/gantt%20chart%203.svg)

```latex
\documentclass{standalone}
\usepackage{pgfgantt}
\begin{document}
\begin{ganttchart}[
    vgrid={*{5}{draw=none}, dotted, {draw=none}}, 
    x unit=.7mm, y unit title=6mm,
    title height=1,
    time slot format=isodate,
]{2024-10-01}{2025-03-31}
\gantttitlecalendar{year, month=shortname} \\
\ganttbar{Homework 1}{2024-11-15}{2024-12-01} \\
\ganttlinkedbar{Homework 2}{2024-12-10}{2025-01-08} \\ 
\ganttlinkedmilestone{Exam A}{2025-02-25} \\
\ganttlinkedmilestone{Exam B}{2025-03-23} \\
\ganttlinkedmilestone{Success}{2025-03-31}
\ganttlink[link mid=.32]{elem1}{elem3}
\ganttlink[link mid=.9]{elem2}{elem4}
\end{ganttchart}
\end{document}
```


Colors

![gantt chart 5.svg](./attachments/gantt%20chart%205.svg)

```latex
\documentclass{standalone}
\usepackage{pgfgantt}
\begin{document}
\begin{ganttchart}[
    vgrid={*{5}{draw=none}, dotted, {draw=none}}, 
    x unit=.7mm, y unit title=6mm,
    title height=1,
    link/.style={green},
    time slot format=isodate,
]{2024-10-01}{2025-03-31}
\gantttitlecalendar{year, month=shortname} \\
\ganttbar{Homework 1}{2024-11-15}{2024-12-01} \\
\ganttlinkedbar{Homework 2}{2024-12-10}{2025-01-08} \\ 
\ganttlinkedmilestone{Exam A}{2025-02-25} \\
\ganttlinkedmilestone[link/.style={red}]{Exam B}{2025-03-23} \\
\ganttlinkedmilestone{Success}{2025-03-31}
\ganttlink[link mid=.32]{elem1}{elem3}
\ganttlink[link mid=.9]{elem2}{elem4}
\end{ganttchart}
\end{document}
```


Exams

![gantt chart 4.svg](./attachments/gantt%20chart%204.svg)

```latex
\documentclass{standalone}
\usepackage{pgfgantt}
\begin{document}
\begin{ganttchart}[
    vgrid={*{5}{draw=none}, dotted, {draw=none}}, 
    x unit=.7mm, y unit title=6mm,
    title height=1,
    time slot format=isodate,
]{2024-10-01}{2025-03-31}
\gantttitlecalendar{year, month=shortname} \\
\ganttbar{Homework 1}{2024-11-15}{2024-12-01} \\
\ganttlinkedbar{Homework 2}{2024-12-10}{2025-01-08} \\ 
\ganttlinkedmilestone{Exams}{2025-02-25}
\ganttlinkedmilestone[link/.append style={dashed}]{}{2025-03-23} \\
\end{ganttchart}
\end{document}
```

```latex
\documentclass{standalone}
\usepackage{pgfgantt}
\begin{document}
\begin{ganttchart}[
vgrid,
hgrid
]{1}{12}
\gantttitle{Title}{12} \\
\ganttbar{Task 1}{1}{4} \\
\ganttlinkedbar{Task 2}{5}{6} \\
\ganttlinkedmilestone{M 1}{6} \\
\ganttlinkedbar{Task 3}{7}{11}
\end{ganttchart}
\end{document}
```


![gantt chart 1.svg](./attachments/gantt%20chart%201.svg)

```latex
\documentclass[tikz, margin=5mm]{standalone}
\usepackage{pgfgantt}
\title{Gantt Charts with the pgfgantt Package}
\begin{document}

\begin{ganttchart}[
   vgrid={*{11}{gray, dotted}, *1{black, dashed}},
   bar label node/.append style={
     align=left,
     text width=width("Aim 2. Software verificationx")}
   ]{1}{24}
\gantttitle{Year 1}{12} \gantttitle{Year 2}{12} \\
\ganttbar{Aim 1. Migration}{1}{8} \\
\ganttbar{Aim 2. Software verification}{6}{12} \\
\ganttbar{Aim 3. Hardware portability}{12}{18} \\
\ganttbar{Aim 4. Documentation}{8}{24}

\end{ganttchart}

\end{document}
```

# Typst

![Pasted image 20241216163619.png](./attachments/pasted%20image%2020241216163619.png)

```typst
#import "@preview/timeliney:0.1.0"

#timeliney.timeline(
  show-grid: true,
  {
    import timeliney: *
      
    headerline(group(([*2023*], 4)), group(([*2024*], 4)))
    headerline(
      group(..range(4).map(n => strong("Q" + str(n + 1)))),
      group(..range(4).map(n => strong("Q" + str(n + 1)))),
    )
  
    taskgroup(title: [*Research*], {
      task("Research the market", (0, 2), style: (stroke: 2pt + gray))
      task("Conduct user surveys", (1, 3), style: (stroke: 2pt + gray))
    })

    taskgroup(title: [*Development*], {
      task("Create mock-ups", (2, 3), style: (stroke: 2pt + gray))
      task("Develop application", (3, 5), style: (stroke: 2pt + gray))
      task("QA", (3.5, 6), style: (stroke: 2pt + gray))
    })

    taskgroup(title: [*Marketing*], {
      task("Press demos", (3.5, 7), style: (stroke: 2pt + gray))
      task("Social media advertising", (6, 7.5), style: (stroke: 2pt + gray))
    })

    milestone(
      at: 3.75,
      style: (stroke: (dash: "dashed")),
      align(center, [
        *Conference demo*\
        Dec 2023
      ])
    )

    milestone(
      at: 6.5,
      style: (stroke: (dash: "dashed")),
      align(center, [
        *App store launch*\
        Aug 2024
      ])
    )
  }
)
```


---
Sources:
- [Gantt chart - Wikipedia](https://en.wikipedia.org/wiki/Gantt_chart)
- [timeliney – Typst Universe](https://typst.app/universe/package/timeliney/)
- [pgfgantt Package documentation](http://mirrors.ctan.org/graphics/pgf/contrib/pgfgantt/pgfgantt-doc.pdf)

Related:

Tags:
[LaTeX](./latex.md)