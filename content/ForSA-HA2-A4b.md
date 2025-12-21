---
date: "2025-07-17T08:13:58.175+02:00"
title: "ForSA HA2 A4b"
description: "-"
dg-publish: true
---

Sei $​\Sigma =  \{ a,b \} ​$. Gegeben sei die Sprache
$$
A_{2} = \{ a^{q}\, b^{r} \mid q,r \in \mathbb{N}  \land q \bmod 3 = 0 \land q/3 = r   \} 
$$
Beweise nur mit dem Pumping Lemma für reguläre Sprachen, dass $​A_{2} ​$ nicht regulär ist.

# Eigenschaften der Sprache in natürlichem Deutsch

Die Sprache $A_2$ besteht aus Wörtern über dem Alphabet $\Sigma = \{a, b\}$, die folgende Eigenschaften erfüllen:

1. Das Wort besteht aus einer bestimmten Anzahl von $a$'s, gefolgt von einer bestimmten Anzahl von $b$'s.
2. Die Anzahl der $a$'s, die das Wort enthält, ist ein Vielfaches von 3.
3. Die Anzahl der $b$'s im Wort ist das Ergebnis der Division der Anzahl der $a$'s durch 3.

Mit anderen Worten, ein Wort in $A_2$ besteht aus einer Wiederholung der Buchstabe $a$ in einer Anzahl, die ein Vielfaches von 3 ist, gefolgt von einer Wiederholung des Buchstaben $b$ in einer Anzahl, die das Ergebnis der Division der Anzahl der $a$'s durch 3 ist.

# Beispielwörter der Sprache

$$
A_{2} = \{ a^{\textcolor{magenta}{q}}\, b^{\textcolor{limegreen}{r}} \mid \textcolor{magenta}{q},\textcolor{limegreen}{r} \in \mathbb{N}  \land q \bmod 3 = 0 \land q/3 = r   \}
$$

$$
\underset{\textcolor{magenta}{0}\textcolor{limegreen}{0}}{ \varepsilon  },
\underset{\textcolor{magenta}{3}}{ aaa }\underset{\textcolor{limegreen}{1}}{ b },
\underset{\textcolor{magenta}{6}}{ aaaaaa }\underset{\textcolor{limegreen}{2}}{ bb },
\underset{\textcolor{magenta}{9}}{ aaaaaaaaa }\underset{\textcolor{limegreen}{3}}{ bbb }
$$

# Beweis mit Pumping Lemma, dass die Sprache nicht regulär ist

Sei $​p \in \mathbb{N} ​$ (beliebig aber  fest). Wir wählen $​w = a^{3p}\, b^{p} ​$ mit $​w \in A_{1} ​$, denn $​3p,p \in \mathbb{N} ​$, und $​3p \bmod 3 = 0​$, und $​3p/3 =  p​$ . Sei $​w = xyz​$ eine beliebige Zerlegung mit $​y \ne \varepsilon ​$ und $​\lvert xy \rvert \le p​$. Da $​\lvert xy \rvert \le p​$ und $​\lvert a^{3p} \rvert \ge  p ​$ gilt, wissen wir, dass sowohl $​x​$ als auch $​y​$ nur aus Buchstaben $​a​$ bestehen und keinen Buchstaben $​b​$ enthalten. Dann ist $​x = a^{i}, y = a^{j}​$ und $​z = a^{3p - i - j}\, b^{p}  ​$ für ein $​j \ne 0​$ und $​i + j \le p​$. Wir wählen $​k = 0​$. Dann ist $​xy^{0}z = a^{i}a^{3p - i - j}\, b^{p} = a^{3p - j}\, b^{p}​$.
Um zu Überprüfen, ob $​xy^{0}z​$ ein Wort der Sprache $​A_{2}​$ ist, müssen wir alle Möglichkeiten betrachten, das Wort $​xy^{0}z​$ in die Teilworte $​a^{q}​$, und $​b^{r}​$ aufzuteilen. Da das Teilwort $​a^{q}​$ nur aus $​a's​$ bestehen kann und das Teilwort $​b^{r}​$ nur aus $​b​$'s bestehen kann, können wir $​xy^{0}z​$ als $​a^{q}​b^{r}$ mit $​q = 3p - j​$, und $​r = p​$ darstellen. Es gilt $​xy^{0}z \notin A_{2}​$, denn $​q/3 \ne r​$, da $\frac{​3p - j}{3} = p - \frac{j}{3} \ne p​$ für $​j \ne 0​$. Da $​\neg \operatorname{\textbf{PUMP-REG}} ( A_{2}  )​$, ist $​A_{2} ​$ nach dem Pumping-Lemma nicht regulär.


---
Sources:

Related:

Tags:
ForSA HA2 zum 2023-07-13