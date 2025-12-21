---
date: "2025-07-17T08:13:58.805+02:00"
title: "Stoch HA5 zum 2023-05-26"
description: "-"
dg-publish: true
---

!Hausaufgabengruppe in Stochastik für Informatik

# Aufgabe 1

## a)

$X :$ Anzahl der Atomzerfälle pro Sekunde
$X$ ist Poisson-verteilt mit $\lambda = 2$:
$$
\mathbb{P}(X=n) = \frac{2^n}{n! \, e^2} \qquad X(\Omega) = \mathbb{N} 
$$

$$
\mathbb{P}(X > 2) = \sum_{n=3}^{\infty} \frac{2^n}{n! \, e^2} = 1- \frac{5}{e^2} \approx 0,323 
$$
$$
\mathbb{P}(X < 2) = \sum_{n=0}^{1} \frac{2^n}{n! \, e^2} = \frac{1}{e^2} + \frac{2}{e^2} = \frac{3}{e^2} \approx 0,406 
$$
Es gilt $\mathbb{P}(X > 2) \not> \mathbb{P}(X<2)$

## b)

- $4$ Bewohnerinnen im Dorf
- abzählbar unendlich viele Bewohnerinnen in der Hauptstadt
$Y:$ Anzahl aller Freundinnen
$Y$ ist Zipf-verteilt mit Parameter $a=4$:
$$
\mathbb{P}(Y = y) = \frac{1}{y^4} \cdot \frac{1}{Z(4)} \qquad Z(4)=\sum_{k=1}^\infty \frac{1}{k^4} = \frac{\pi^4}{90} \qquad Y(\Omega) = \mathbb{N} 
$$
$$
\mathbb{P}(Y=y) = \frac{1}{y^4} \cdot \frac{90}{\pi^4} = \frac{90}{y^4 \, \pi^4} 
$$
Erst wenn sie mindestens $4$ Dorffreundinnen hat, kann sie eine Hauptstadtfreundin haben
$$
\mathbb{P}(Y > 4) =  \mathbb{P}(Y \ge 5) = \sum_{n=5}^\infty \frac{90}{n^4 \, \pi^4} = 1 - \frac{111845}{1152 \pi^2} \approx 0.00330 
$$

# Aufgabe 2

Wir betrachten nur die Menge aller Studierenden, die die Sprechstunde besuchen. Jeder Person studiert **nur ein Studienfach**. Um Genderprobleme zu vermeiden, rede ich nur von Studienfächern und nicht von Studierenden. Ein Studienfach bezieht sich immer auf eine:n Studierende:n.

$p \in \, ]0,1[$
$X:$ Anzahl der Sprechstundenbesucher, die Informatik studieren
$Y:$ Anzahl der Sprechstundenbesucher, die sonstiges studieren
$Z:$ Anzahl alle Sprechstundenbesucher
$$
\begin{align}
\mathbb{P}(X = x) &= \frac{(p\lambda)^x}{x! \, e^{p\lambda}} & X(\Omega) = \mathbb{N} \\
\mathbb{P}(Y = y) &= \frac{((1-p)\lambda)^y}{y! \, e^{(1-p)\lambda}} & Y(\Omega)=\mathbb{N} \\
Z:= X+Y \qquad \mathbb{P}(Z=z) &= \frac{p^z}{z! \, e^\lambda} = \sum_{x=0}^z \mathbb{P}(X=x,Y=n-x) & Z(\Omega) = \mathbb{N} \\
\end{align}
$$

$X,Y$ sind unabhängig, falls gilt 
$$
\forall_{x \in X(\Omega),\, y \in Y(\Omega)} \, \mathbb{P}(X=x,Y=y) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y)
$$

## Betrachten wir zunächst die linke Seite

In eine Gruppe studieren $x$ Informatik und $y$ sonstiges.
Ihre belegten Studienfächer sind unabhängig voneinander.
Jede Person studiert mit Wahrscheinlichkeit $p$ Informatik.
Jeder Person studiert mit Wahrscheinlichkeit $1-p$ sonstiges.
$x$ Personen studieren mit Wahrscheinlichkeit $p^x$ nur Informatik.
$y$ Personen studieren mit Wahrscheinlichkeit $(1-p)^y$ nur sonstiges.
Es gibt $\binom{x+y}{x}$ Möglichkeiten, $x$ Informatikstudienfächer auf die Gruppe mit $x+y$ Personen zu verteilen.
Somit beträgt die Wahrscheinlichkeit, dass eine Gruppe $x$-mal Informatik und $y$-mal sonstiges als Studienfach hat:
$$
\mathbb{P}(X=x,Y=y) = p^x \cdot (1-p)^y \cdot \binom{x+y}{x} = p^x \cdot (1-p)^y \cdot \frac{(x+y)!}{x! \, y!} 
$$

## Betrachten wir nun die rechte Seite

$$
\begin{align*}\MoveEqLeft{}
\mathbb{P}(X=x) \cdot \mathbb{P}(Y=y) 
= \frac{(p\lambda)^x}{x! \, e^{p\lambda}} \cdot \frac{((1-p)\lambda)^y}{y! \, e^{(1-p)\lambda}} \\&
= \frac{p^x\, (1-p)^y\, \lambda^x\, \lambda^y}{x!\, y!\, e^{p\lambda}\, e^{(1-p)\lambda} } = \frac{p^x\, (1-p)^y\, \lambda^{x+y}}{x!\, y!\, e^\lambda }
\end{align*}
$$

## Wir setzen die Seiten gleich

$$
\begin{align*}\MoveEqLeft{}
\mathbb{P}(X=x,Y=y) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y) \\&
\iff p^x \cdot (1-p)^y \cdot \frac{(x+y)!}{x! \, y!} = \frac{p^x\, (1-p)^y\, \lambda^{x+y}}{x!\, y!\, e^\lambda } 
\xLeftrightarrow{\cdot \frac{x! \, y!}{p^x \, (1-p)^y}} 
(x+y)! = e^{-\lambda} \, \lambda^{x+y}
\end{align*}
$$
Wir haben es nicht geschafft, die Unabhängigkeit zu zeigen. Grundsätzlich muss man $\mathbb{P}(X=x,Y=y)$ bilden und zeigen, dass dies für alle $x \in X(\Omega),\ y \in Y(\Omega)$ gleich $\mathbb{P}(X=x) \cdot \mathbb{P}(Y=y)$ ist. Wir haben $\mathbb{P}(X=x,Y=y)$ nicht korrekt gebildet und können daher die Unabhängigkeit nicht zeigen.

# Aufgabe 3

$X:$ Anzahl der Köpfe in Würfen **1,2,3**
$Y:$ Anzahl der Köpfe in Würfen **3,4**
$$
X(\Omega) = \{ 0,1,2,3 \} \qquad Y(\Omega)= \{ 0,1,2 \}
$$

# a)

$$
(\Omega, \mathbb{P}) : \Omega = \{ K,Z \}^4, \; \mathbb{P}(\omega) = \frac{1}{|\Omega|} = \frac{1}{2^4} = \frac{1}{16} 
$$

## b)

Wir betrachten $X$.
Es gibt $\binom{3}{k}$ Möglichkeiten, $k$ Köpfe auf die ersten **drei** Würfe zu verteilen.
Der letzte Wurf ist uns egal, ergibt also **zwei** Möglichkeiten.
Somit gibt es $\binom{3}{x} \cdot 2$ Elementarereignisse, die auf $X=x$ abbilden, mit jeweils $\mathbb{P}(\omega) = \frac{1}{16}$.
$$
\mathbb{P}(X=x) = \mathbb{P}(\omega) \cdot \binom{3}{x} \cdot 2 = \frac{1}{8} \cdot \binom{3}{x}
$$

| x                 | 0              | 1              | 2              | 3              |
| ----------------- | -------------- | -------------- | -------------- | -------------- |
| $\mathbb{P}(X=x)$ | $\dfrac{1}{8}$ | $\dfrac{3}{8}$ | $\dfrac{3}{8}$ | $\dfrac{1}{8}$ |

Wir betrachten $Y$.
Die ersten beiden Würfe sind uns egal, ergeben also $2^2=4$ Möglichkeiten.
Es gibt $\binom{2}{k}$ Möglichkeiten, $k$ Köpfe auf die letzten **beiden** Würfe zu verteilen.
Somit gibt es $4 \cdot \binom{2}{y}$ Elementarereignisse, die auf $Y=y$ abbilden, mit jeweils $\mathbb{P}(\omega) = \frac{1}{16}$.
$$
\mathbb{P}(Y=y) = \mathbb{P}(\omega) \cdot 4 \cdot \binom{2}{y} = \frac{1}{4} \cdot \binom{2}{y} 
$$

| y                 | 0              | 1              | 2   |
| ----------------- | -------------- | -------------- | --- |
| $\mathbb{P}(Y=y)$ | $\dfrac{1}{4}$ | $\dfrac{1}{2}$ | $\dfrac{1}{4}$    |

## c)

Da der Wahrscheinlichkeitsraum ein La-Place Raum ist, reicht es aus, die Elementarereignisse der Schnittmenge von $\{X=x\}$ und $\{ Y=y \}$ zu zählen und mit $|\Omega| = 16$ zu dividieren. Ich bilde nun die gültigen Elementarereignisse mathematisch informell, da es nur um deren Anzahl geht:

| "$X^{-1}$" \ "$Y^{-1}$" | ??ZZ       | ??KZ, ??ZK       | ??ZZ       |
| ----------------------- | ---------- | ---------------- | ---------- |
| ZZZ?                    | ZZZZ       | ZZZK             | -          |
| ZZK?, ZKZ?, KZZ?        | ZKZZ, KZZZ | ZZKZ, ZKZK, KZZK | ZZKK       |
| ZKK?, KZK?, KKZ?        | KKZZ       | ZKKZ, KZKZ, KKZK | ZKKK, KZKK |
| KKK?                    | -          | KKKZ              | KKKK       |

Somit ergibt sich für die gemeinsame Verteilung von $X$ und $Y$ folgendes. Als Probe habe ich noch die Randverteilungen $\mathbb{P}(X=x)$ und $\mathbb{P}(Y=y)$ als Zeilenund Spaltensumme ergänzt, was aus genau unseren in b) berechneten Verteilungen entspricht 🙂

| $x$ \ $y$             | 0               | 1               | 2               | $\mathbb{P}(X=\cdot)$ |
| --------------------- | --------------- | --------------- | --------------- | --------------------- |
| 0                     | $\dfrac{1}{16}$ | $\dfrac{1}{16}$ | $0$             | $\dfrac{1}{8}$        |
| 1                     | $\dfrac{2}{16}$ | $\dfrac{3}{16}$ | $\dfrac{1}{16}$ | $\dfrac{3}{8}$        |
| 2                     | $\dfrac{1}{16}$ | $\dfrac{3}{16}$ | $\dfrac{2}{16}$ | $\dfrac{3}{8}$        |
| 3                     | $0$             | $\dfrac{1}{16}$ | $\dfrac{1}{16}$ | $\dfrac{1}{8}$        |
| $\mathbb{P}(Y=\cdot)$ | $\dfrac{1}{4}$  | $\dfrac{1}{2}$  | $\dfrac{1}{4}$  |                       |

## d)

$$
X,Y \text{ sind unabhängig} \iff \forall_{x \in X(\Omega), y \in Y(\Omega)} \, \mathbb{P}(X=x,Y=y) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y=y) 
$$
Ich widerlege mit dem Gegenbeispiel $X=0, Y=0$:
$$
\begin{align*}
\mathbb{P}(X=0,Y=0) = \mathbb{P}(X=0) \cdot \mathbb{P}(Y=0) 
\iff \frac{1}{16} = \frac{1}{8} \cdot \frac{1}{4} = \frac{1}{32}
\iff \text{falsche Aussage} 
\end{align*} $$
$\implies X,Y$ sind nicht unabhängig

## e)

$Z:$ Anzahl Köpfe in den Würfel **2,3,4**
$W:$ Anzahl Köpfe in den Würfen **2,3**

Nein, die gemeinsame Verteilung ist verschieden. Beispielhaft bildet nur das Elementarereignis $\{ (Z,Z,Z,Z) \}$ auf $X=0$ und $Y=0$ ab, während die beiden Elementarereignisse $\{ (K,Z,Z,Z),(Z,Z,Z,Z) \}$ auf $Z=0$ und $W=0$ abbilden.
