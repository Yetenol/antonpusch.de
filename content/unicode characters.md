---
dg-publish: true
---

# Useful characters

| Purpose     | Char | Name                                                 | Alt code    |
| ----------- | ---- | ---------------------------------------------------- | ----------- |
| Invisible   | ` `  | [No-Break Space](https://unicode-table.com/en/00A0/) | 225 or 0160 |
| Sort first  | `!`  | Exclamation Mark                                     |             |
| Sort second | `+`  | Plus Sign                                            |             |
| Sort last   | `Ξ`  | [Capital Xi](https://unicode-table.com/en/039E/)     |             |

# Greek letters

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

# Sorting differences on different platforms

| Windows | Android <br> VS Code | PowerShell <br> Command Prompt | Unix Bash |
| ------- | -------------------- | ------------------------------ | ---------- |
| `␣`     |                      |                                |            |
| `!`     | `_`                  |                                |            |
| `_`     | `!`                  |                                |            |
| `~`     | `+`                  |                                |            |
| `+`     | `~`                  | `!`                            | `!`        |
| `µ`     | `␣`                  | `+`                            | `+`        |
| `0`     | `0`                  | `0`                            | `0`        |
| `9`     | `9`                  | `9`                            | `9`        |
| `A`     | `A`                  | `A`                            | `A`        |
| `ä`     | `ä`                  | `Z`                            | `Z`        |
| `ß`     | `ß`                  | `_`                            | `_`        |
| `Z`     | `Z`                  | `~`                            | `~`        |
| `Ξ`     | `µ`                  | `µ`                            | `µ`        |
| `π`     | `Ξ`                  | `ä`                            | `ß`        |
| `Ω`     | `π`                  | `ß`                            | `ä`        |
|         | `Ω`                  | `Ξ`                            | `Ξ`        |
|         |                      | `π`                            | `Ω`        |
|         |                      | `Ω`                            | `π`        |
|         |                      | `␣`                            | `␣`        |

## Special sorting characters

| .   | Name                    | Unicode | Alt code |
| --- | ----------------------- | ------- | -------- |
| `␣` | Open Box                | U+2423  |
| `µ` | Micro                   | U+00B5  | Alt 230  |
| `Ξ` | Xi (greek uppercase)    | U+039E  |
| `π` | Pi (greek lowercase)    | U+03C0  | Alt 227  |
| `Ω` | Omega (greek uppercase) | U+03A9  | Alt 234  |

---
Sources:
- 2022-01-25 [Unicode Character Table](https://unicode-table.com/en/)

Related:

Tags:
[Computer Language](./computer%20language.md)