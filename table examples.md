

# Border examples

## Comparison along categories - Cross

| Aspekt                    | MarkMD | Word | Docs | Overleaf |
| ------------------------- | ------ | ---- | ---- | -------- |
| Einfach                   | o      | +    | ++   | o        |
| synchrone Zusammenarbeit  | ++     | ++   | ++   | ++       |
| asynchrone Zusammenarbeit | +      | ++   | ++   | +        |
| Korrekturhilfe            | -      | ++   | ++   | +        |
| Überarbeitungsvorschläge  | -      | +    | +    | -        |
| Planung                   | ++     | -    | -    | -        |
| Verfügbarkeit             | +      | ++   | +    | +        |
| Preis                     | +      | +    | ++   | ++       |
| Transparenz               | ++     | ++   | ++   | ++       |
| Export                    | ++     | +    | +    | +        |
| Datenschutz               | -      | -    | -    | -        |

## Assign two dimensions: date, route

| $_\text{Route}\diagdown^\text{Date}$ | So, 30.7. | Mo, 31.7. | Di, 01.8. | Mi, 02.8. |
| ------------------------------------------ | --------: | --------: | --------: | --------: |
| **BER**-TBS                                |   1.012 € |   1.023 € |     880 € |     847 € |
| **BER**-KUT                                |   1.020 € |         - |         - |     760 € |
| **BER**-BUS                                |   1.603 € |   1.119 € |     886 € |   2.243 € |
| FRA-TBS                                    |   1.148 € |   1.146 € |   1.000 € |     991 € |
| FRA-BUS                                    |   2.042 € |   1.303 € |   1.071 € |   1.096 € |
| HAM-TBS                                    |   1.168 € |   1.138 € |     794 € |     794 € |


## List - Hlines

| .   | Name        | Unicode | Alt code |
| --- | ----------- | ------- | -------- |
| `α` | Alpha       | U+03B1  | Alt 224  |
| `Γ` | Gamma       | U+0393  | Alt 226  |
| `δ` | Delta       | U+03B4  | Alt 235  |
| `ε` | Epsilon     | U+03B5  | Alt 238  |
| `Θ` | Theta       | U+0398  | Alt 233  |
| `π` | Pi          | U+03C0  | Alt 227  |
| `Σ` | Sigma upper | U+03A3  | Alt 228  |
| `σ` | Sigma lower | U+03C3  | Alt 229  |
| `τ` | Tau         | U+03C4  | Alt 231  |
| `Φ` | Phi upper   | U+03A6  | Alt 232  |
| `φ` | Phi lower   | U+03C6  | Alt 237  |
| `Ω` | Omega       | U+03A9  | Alt 234  |

## List commands

| Positive relation                                    | negated                     |
| ---------------------------------------------------- | --------------------------- |
| $=$ <code>=</code>                                   | $\ne$ `\ne`, `\neq`         |
| $\approx$ `\approx`                                  | $\not\approx$ `\not\approx` |
| $<$ `<`                                              | $\nless$ `\nless`           |
| $>$ `>`                                              | $\ngtr$ `\ngtr`             |
| $\le$ `\le`, `\leq`                                  | $\nleq$ `\nleq`             |
| $\ge$ `\ge`, `\geq`                                  | $\ngeq$ `\ngeq`             |
| $\triangleq$ `\triangleq`<br>$\coloneqq$ `\coloneqq` |                             |
| $\equiv$ `\equiv`                                    | $\not\equiv$ `\not\equiv`   |
| $\in$ `\in`                                          | $\notin$ `\notin`           |
| $\ni$ `\ni`                                          | $\not\ni$ `\not\ni`[^1]     |
| $\subset$ `\subset`                                  | $\not\subset$ `\not\subset` |
| $\supset$ `\supset`                                  | $\not\supset$ `\not\supset` |
| $\subseteq$ `\subseteq`                              | $\nsubseteq$ `\nsubseteq`   |
| $\supseteq$ `\supseteq`                              | $\nsupseteq$ `\nsupseteq`   |
| $\sim$ `\sim`                                        | $\nsim$ `\nsim`             |
| $\ll$ `\ll`                                          | $\not\ll$ `\not\ll`         |
| $\gg$ `\gg`                                          | $\not\gg$ `\not\gg`         |

# Mathe - Cross, diagonal cell border

| $_{x}\diagdown^{y}$   |              0 |              1 |              2 | $\mathbb{P}(X=\cdot)$ |
| --------------------- | -------------: | -------------: | -------------: | --------------------: |
| 0                     | $^1\!/_{\!16}$ | $^1\!/_{\!16}$ |            $0$ |         $^1\!/_{\!8}$ |
| 1                     | $^2\!/_{\!16}$ | $^3\!/_{\!16}$ | $^1\!/_{\!16}$ |         $^3\!/_{\!8}$ |
| 2                     | $^1\!/_{\!16}$ | $^3\!/_{\!16}$ | $^2\!/_{\!16}$ |         $^3\!/_{\!8}$ |
| 3                     |            $0$ | $^1\!/_{\!16}$ | $^1\!/_{\!16}$ |         $^1\!/_{\!8}$ |
| $\mathbb{P}(Y=\cdot)$ |  $^1\!/_{\!4}$ |  $^1\!/_{\!2}$ |  $^1\!/_{\!4}$ |                       |

|        |                         $K$ |                         $K^c$ |
| ------ | --------------------------: | ----------------------------: |
| $NK$   | ${} \mathbb{P}(NK \vert K)$ |      $\mathbb{P}(NK \vert K)$ |
| $NK^c$ |  $\mathbb{P}(NK^c \vert K)$ | ${} \mathbb{P}(NK^c\vert NK)$ |

| Name                                   |     Operation     |                                      Definition                                      |
| -------------------------------------- | :---------------: | :----------------------------------------------------------------------------------: |
| Vereinigung                            |    $A \cup B$     |                              $\{x:x\in A\lor x \in B\}$                              |
| Schnitt                                |     $A\cap B$     |                             $\{x:x\in A \land x\in B\}$                              |
| Komplement <br> Menge $A$ **ohne** $B$ |  $A\setminus B$   |                            $\{x:x\in A \land x\notin B\}$                            |
| symmetrische Differenz                 | $A\,\triangle\,B$ | $\{x:x\in A \leftrightarrow x\notin B \}$ <br> $=(A\setminus B) \cup (B\setminus A)$ |
| kartesisches Produkt                   |    $A\times B$    |                           $\{(x,y):x\in A \land y \in B\}$                           |
| Potenzmenge von $A$                    |       $2^A$       |                                $\{X:X\subseteq A \}$                                 |

| Logische Operation                        | Mengentheoretisch Operation                                 |
| ----------------------------------------- | ----------------------------------------------------------- |
| $\not A$ Verneinung von A                 | $A^C = \Omega\notin A = \{\omega\in\Omega:\omega\notin A\}$ |
| $A\land B$ *A und B*                      | $A\cap B=\{\omega\in\Omega:\omega\in A\cap \omega\in B\}$   |
| $A \lor B$ *A oder B*                     | $A \cup B$ Vereinigung                                      |
| $A\ \text{xor}\ B$ *A oder B oder beides* | $A\ \triangle\ B = (A\cup B )\setminus A\cap B$             |
| $A\ \text{nor}\ B=\neg(A\lor B)$          |                                                             |

# Legende, Glossar

| Schreibweise       | Bedeutung                              |
| ------------------ | -------------------------------------- |
| $(1,2,3)$          | [Tupel](Tupel.md) <br> haben Reihenfolge       |
| $\{1,2,3\}$        | [Menge](Menge.md) <br> haben keine Reihenfolge |
| $:=$               | Definition                             |
| $x$ Kleinbuchstabe | Element                                |
| $X$ Grobbuchstabe  | Menge                                  |

| IATA-Code | Stadt des Flughafens           |
| --------- | ------------------------------ |
| BER       | Berlin, Deutschland            |
| FRA       | Frankfurt am Main, Deutschland |
| HAM       | Hamburg, Deutschland           |
| TBS       | Tbilisi, Georgien              |
| KUT       | Kutaisi, Georgien              |
| BUS       | Batumi, Georgien               |

| IATA-Code | Fluggesellschaft |
| --------- | ---------------- |
| W6        | Wizz Air         |
| EW        | Eurowings        |
| BT        | Air Baltic       |
| TK        | Turkish Airlines |
| 5F        | FLYONE           |

| Kürzel          | Bedeutung                                                                          |
| --------------- | ---------------------------------------------------------------------------------- |
| **Fremdpreis**  | Preis für 4 Erwachsene des billigsten Portals                                      |
| **Eigenpreis**  | Preis für 4 Erwachsene des Portals der Fluggesellschaft selbst                     |
| **Gesamtpreis** | geschätzter Gesamtpreis beim Kauf durch das Portal der jeweiligen Fluggesellschaft |
| + €             | Handgepäck nicht im Preis enthalten                                                |
| - €             | 1. Hauptgepäck kostenlos                                                           |


# Muss es eine Tabelle sein?

| Gruppenmitglied  | Matrikelnummer |
| ---------------- | -------------- |
| Anton Pusch      | 457514         |
| Miguel Müller    | 468941         |
| Oguz Efe Sonugür | 411575         |

# Preisvergleich


|                                Flugnummern⁽²⁾                                 |     Datum | Route⁽¹⁾ | Fremdpreis⁽³⁾ | Eigenpreis⁽³⁾ | Umstiege | Dauer      |
| :---------------------------------------------------------------------------: | --------: | :------: | ------------: | ------------: | -------- | ---------- |
|     [W6 6408](https://www.google.com/travel/flights/s/LN3g8zLc2SVg2oJP8)      | Mi, 02.8. | BER-KUT  |         820 € |         840 € | 0        | 3hr 45min  |
|     [W6 6408](https://www.google.com/travel/flights/s/uzuJBfxZkUPi8t7z7)      | So, 30.7. | BER-KUT  |         977 € |       1.120 € | 0        | 3hr 45min  |
| [EW 8040, EW 9150](https://www.google.com/travel/flights/s/GCv5xxYNBazi6vxh9) | Di, 01.8. | BER-TBS  |        835+ € |        880+ € | 1        | 9hr 20min  |
|  [BT 212, BT 720](https://www.google.com/travel/flights/s/dmwQVLsMgaNFf7w26)  | Di, 02.8. | BER-BUS  |         873 € |         943 € | 1        | 18hr       |
| [TK 7729, TK 7722](https://www.google.com/travel/flights/s/gPxvUwSaNgXYbq3D6) | Di, 01.8. | BER-TBS  |         898 € |         993 € | 1        | 11hr 35min |
| [TK 1724, TK 376](https://www.google.com/travel/flights/s/UedyBF6d4yzQP4cS6)  | Di, 01.8. | BER-TBS  |      1.009- € |      1.119- € | 1        | 6hr 55min  |
|  [5F 612, 5F 581](https://www.google.com/travel/flights/s/os6hc2qSeC2VkXcv9)  | So, 30.7. | BER-TBS  |       1.012 € |       1.012 € | 1        | 6hr        |
| [TK 1722, TK 392](https://www.google.com/travel/flights/s/75hWgksVBaL9c8Ly8)  | So, 30.7. | BER-BUS  |       1.552 € |       2.263 € | 1        | 8hr 5min   |

|  Route⁽¹⁾   | Sa, 12.8. | So, 13.8. | Mo, 14.8. | Di, 15.8. |
| :---------: | --------: | --------: | --------: | --------: |
| TBS-**BER** |     911 € |   1.025 € |   1.077 € |   1.050 € |
| BUS-**BER** |     830 € |     830 € |     830 € |     830 € |
| KUT-**BER** |   2.742 € |   1.282 € |   4.105 € |         - |
|   TBS-FRA   |     803 € |     803 € |   1.005 € |     793 € |
|   TBS-HAM   |   1.036 € |   1.000 € |   1.036 € |   1.036 € |
|   BUS-HAM   |     731 € |     731 € |     731 € |     731 € |
|   BUS-FRA   |     768 € |     768 € |     768 € |      768€ |
|   KUT-FRA   |         - |   3.852 € |         - |         - |
|   KUT-HAM   |         - |         - |   1.051 € |         - |

|                                Flugnummern⁽²⁾                                 |     Datum | Route⁽¹⁾ | Fremdpreis⁽³⁾ | Eigenpreis⁽³⁾ | Umstiege | Dauer     |
| :---------------------------------------------------------------------------: | --------: | :------: | ------------: | ------------: | -------- | --------- |
| [TK 391, TK 1723](https://www.google.com/travel/flights/s/9kskukLTqSpwG2HN9)  | Di, 15.8. | BUS-BER  |         744 € |         805 € | 1        | 9hr 35min |
| [TK 391, TK 1723](https://www.google.com/travel/flights/s/XsUNpLfxU79u5ruR7)  | So, 13.8. | BUS-BER  |         744 € |         805 € | 1        | 9hr 35min |
| [TK 7723, TK 7728](https://www.google.com/travel/flights/s/6MnZ1BVRYxyfCZ669) | Sa, 12.8. | TBS-BER  |         972 € |       1.045 € | 1        | 8hr 30min |
| [TK 387, TK 1721](https://www.google.com/travel/flights/s/YBySzPwAJiTt3kvY8)  | Sa, 12.8. | TBS-BER  |       1.025 € |       1.099 € | 1        | 7hr 5min  |
| [TK 7723, TK 7728](https://www.google.com/travel/flights/s/wfXtDnptYCdNauK37) | Di, 15.8. | TBS-BER  |         972 € |       1.045 € | 1        | 8hr 30min |

| Nächte |   Anreise | Hinflug⁽²⁾                                                                    |   Abreise | Rückflug⁽²⁾                                                                   |     Gesamtpreis⁽³⁾ |
| ------ | --------: | ----------------------------------------------------------------------------- | --------: | ----------------------------------------------------------------------------- | -----------------: |
| 13     | So, 30.7. | [W6 6408](https://www.google.com/travel/flights/s/uzuJBfxZkUPi8t7z7)          | So, 13.8. | [TK 391, TK 1723](https://www.google.com/travel/flights/s/XsUNpLfxU79u5ruR7)  | 1120+805 = 1.925 € |
| 13     | Di, 01.8. | [EW 8040, EW 9150](https://www.google.com/travel/flights/s/GCv5xxYNBazi6vxh9) | Di, 15.8. | [TK 7723, TK 7728](https://www.google.com/travel/flights/s/wfXtDnptYCdNauK37) | 880+1045 = 1.925 € |
| 12     | Di, 01.8. | [TK 1724, TK 376](https://www.google.com/travel/flights/s/UedyBF6d4yzQP4cS6)  | Di, 15.8. | [TK 7723, TK 7728](https://www.google.com/travel/flights/s/wfXtDnptYCdNauK37) | 993+1025 = 2.018 € |

