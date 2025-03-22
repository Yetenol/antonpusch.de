---
date: "2025-03-22T07:21:25.596+01:00"
title: "AlgTheo HA3 Nachbesprechung"
description: "-"
dg-publish: true
---
Greedybeweis führen

# Lösung HA3.1)


Eingabe: 
- Menge an Items $I = \{ i_1, \ldots, i_n \}$.
- Für jedes Item $i \in I$ ein Originalpreis $s_i$ und einen Discoutpreis $d_i \in \{ 1, 2 \}$.
- Budget $B \in [ 0, 2n ]$ 
Ausgabe:
- Teilmenge $W \le I$, sodass $\sum_{i \in W} d_i \le B$ und $\sum_{i \in W}$ wird maximiert.

# Algorithmus

Netzwerkproblem: n-p schwer

Füge $n$ Elemente mit Kosten $0$ ein.
$I_1$ Menge der "1 Euro" Produkte
$I_2$ Menge der "2 Euro" Produkte
Sortieren beide Mengen nach Originalpreis.
Falls $B$ ungerade. Include teuerstes aus $I_1$.
Vergleichen teuerstes Element aus $I_2$ mit zwei teuersten Elementen aus $I_1$ und kaufen was teurer ist.

## Korrektheit mit Greedy stays ahead 

1. Können annehmen, dass $B$ gerade ist

Nehmen induktiv an, dass wir bereits $2 \cdot b$ Euro ausgegeben haben und dass unsere Lösung optimal für $2 \cdot b$ ist.

Ziel: Zeigen, dass dies auch für $2 \cdot ( b + 1 )$ gilt
Annahme: Haben weitere Lösungen die mehr bringt im Schritt $( 2b + 1 )$. (Muss mindestens ein 2-er Item oder zwei 1-er Items enthalten die teurer sind als unsere zuletzt hinzugefügten WIDERSPRUCH)
$I_1 = i_{11}, i_{12}, i_{13}, i_{14}, i_{15}, i_{16}$
$I_2 = i_{21}, i_{22}, i_{23}, i_{24}$

Laufzeit $O(n \log(n) )$

# Lösung HA3.2

$1, 17, 50, 75, 100, 125$
Schlecht: 1-51, 17-, 100-
Gut: um 25, 100

## Algorithmus

```
WHILE nicht alle Punkte abgedeckt
    g <- kleinstes nicht abgedeckter Punkt
    Füge g+25 zur Lösunug hinzu
```

## Korrektheit mit Greedy stays ahead (Intervall Scheduling)

- Invariante suchen
- Zeigen, dass Invariante immer gilt

Sei $B = \{ b_1, b_2,  \ldots,  b_l \}$ und $B' = \{ b_1, b_2, \ldots b_{l'}  \}$.
Zeigen $b_i \ge b_{i'}$ 

1. Nehmen an dies gilt für alle $i' < i$
2. $b'_{i - 1} \le b_{i - 1}$
3. Wir setzen Intervall auf $b_i \to b_i - 25$ noch nicht abgedeckt.
4. Also $b'_{i - 1} \le b_{i - 25} \implies b'$ deckt Punkt auch nicht ab.
5. $\implies$ Nächstes Intervall aus $b'$ deckt auch $b_{i - 25}$ oder früher ab $\implies b'_i \le b_i$.
6. $\implies$ Auch $b_l$ früher als $b'_l$
7. $\implies B'$ nutzt $l$ Intervalle
8. $\implies$ Andere Lösung mindestens genauso groß

# Tutor kontrollieren strenger

Übungsblätter härter kontrolliert als in Klausur, damit ihr in Klausur besser seid
Durchschnitt der Bewertung geht runter und dann wieder hoch

# Ausblick HA4

- 1-2 Greedy-Algorithmen
Korrektheit in Aufgabe 1): Greedy stays ahead