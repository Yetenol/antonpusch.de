---
title: "Mengenoperationen"
aliases:
  - Vereinigung
  - Schnitt
  - Komplement
  - symmetrische Differenz
  - kartesisches Produkt
  - Potenzmenge
  - Rechne mit Mengen
---

# Definition

Seien $A$ und $B$ Mengen. Dann ist folgende Operationen wie folgt definiert

| Name                                   |     Operation     | Definition                                                                           |
| -------------------------------------- | :---------------: | ------------------------------------------------------------------------------------ |
| Vereinigung                            |    $A \cup B$     | $\{x:x\in A\lor x \in B\}$                                                           |
| Schnitt                                |     $A\cap B$     | $\{x:x\in A \land x\in B\}$                                                          |
| Komplement <br> Menge $A$ **ohne** $B$ |  $A\setminus B$   | $\{x:x\in A \land x\notin B\}$                                                       |
| symmetrische Differenz                 | $A\,\triangle\,B$ | $\{x:x\in A \leftrightarrow x\notin B \}$ <br> $=(A\setminus B) \cup (B\setminus A)$ |
| kartesisches Produkt                   |    $A\times B$    | $\{(x,y):x\in A \land y \in B\}$                                                     |
| Potenzmenge von $A$                    |       $2^A$       | $\{X:X\subseteq A \}$                                                                |

# Korrespondenz von Mengenoperationen und logischen Verknüpfungen

![Pasted image 20230425145217.png](./content/attachments/pasted%20image%2020230425145217.png)

---
Sources:
- 2023-04-24: [Korrespondenz von Mengenoperationen und logischen Verknüpfungen](./content/attachments/buch.pdf)
- 2023-04-20: [SoSe 2023 - DS: Woche 0: Organisatorisches & Grundlagen I](https://isis.tu-berlin.de/mod/videoservice/view.php/cm/1581922/video/165740/view#@1707)
- 2023-04-20: [Begriffe und Mathematische Objekte](https://isis.tu-berlin.de/pluginfile.php/2819913/mod_resource/content/1/01_mengen.pdf)

Related:
- [Menge](Menge.md)
- [DS Test 2023-06-01](DS%20Test%202023-06-01.md)
 

Tags:
[Aussagen- und Prädikatenlogik](Aussagen-%20und%20Pr%C3%A4dikatenlogik.md)
[Diskrete Strukturen](Diskrete%20Strukturen.md)