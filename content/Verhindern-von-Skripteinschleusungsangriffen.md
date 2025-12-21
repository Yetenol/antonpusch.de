---
date: "2025-07-17T08:13:58.992+02:00"
title: "Verhindern von Skripteinschleusungsangriffen"
description: "-"
dg-publish: true
dg-show-toc: true
---

# Was ist dein Ziel?

Du hast drei Funktionen, die Tests durchführen und einen Wahrheitswert zurückgeben. Du möchtest den Rückgabewert aller drei Funktionen auf die gleiche Weise verarbeiten, und diese Verarbeitung gerne in eine Funktion generalisieren, `starte_Test` genannt.

Soweit bin ich komplett damit einverstanden.

# Wie hast du dieses Ziel erreicht?

Um in der Verarbeitungsfunktion den Test auszuwählen, übergibst du ihr einen Zeichenfolgenwert (engl. String) `$TestID`. Mit dem Befehl `$erg = & $TestID` nutzt du den [Anrufoperator &](https://learn.microsoft.com/de-de/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7.3#call-operator-) und führst einen Scriptblock (Menge an Anweisungen) aus. Deine Variable `$TestID` enthält einen Zeichenfolgenwert und keinen Scriptblock, weshalb er mit [Konvertierungen](https://learn.microsoft.com/de-de/powershell/scripting/lang-spec/chapter-06?view=powershell-7.3#612-conversion-to-scriptblock) in einen Scriptblock umgewandelt wird. Danach wird dieser Scriptblock ausgeführt.

In der Dokumentation heißt es dazu:

> **Aufrufoperator `&`**
> Führt einen Befehl, ein Skript oder einen Skriptblock aus. Mit dem Aufrufoperator, der auch als "Aufrufoperator" bezeichnet wird, können Sie Befehle ausführen, die in Variablen gespeichert und durch Zeichenfolgen oder Skriptblöcke dargestellt werden. Der Aufrufoperator wird in einem untergeordneten Bereich ausgeführt. Weitere Informationen zu Bereichen finden Sie unter about_Scopes.
- Quelle: [Informationen zu Operatoren - PowerShell | Microsoft Learn](https://learn.microsoft.com/de-de/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7.3#call-operator-)

> **6.12 Konvertierung in scriptblock**
> Die Regeln zum Konvertieren eines beliebigen Werts in den Typ `scriptblock` lauten wie folgt:
> - Ein Zeichenfolgenwert wird als Name eines Befehls behandelt, dem optional Argumente für einen Aufruf dieses Befehls folgen.
- Quelle: [Konvertierungen - PowerShell | Microsoft Learn](https://learn.microsoft.com/de-de/powershell/scripting/lang-spec/chapter-06?view=powershell-7.3#612-conversion-to-scriptblock)

# Welche Schwachstellen und Probleme ergeben sich dabei

## Skripteinschleusungsangriffe (engl. script injection attacks)

In der Dokumentation heißt es dazu:

> PowerShell-Skripts können wie andere Programmiersprachen anfällig für Einschleusungsangriffe sein. Ein Einschleusungsangriff tritt auf, wenn ein Benutzer Eingaben für eine anfällige Funktion bereitstellt, die zusätzliche Befehle enthalten. Die anfällige Funktion führt die zusätzlichen Befehle aus, was ein schwerwiegendes Sicherheitsrisiko darstellen kann. Beispielsweise könnte ein böswilliger Benutzer die anfällige Funktion missbrauchen, um beliebigen Code auf einem Remotecomputer auszuführen, wodurch dieser Computer möglicherweise kompromittiert wird und Zugriff auf andere Computer im Netzwerk erhält.
- Quelle: [Verhindern von Skripteinschleusungsangriffen - PowerShell | Microsoft Learn](https://learn.microsoft.com/de-de/powershell/scripting/dev-cross-plat/security/preventing-script-injection?view=powershell-7.3)

Das Problem besteht darin, dass du mit dem Aufrufoperator die Trennung in deinem Programm zwischen Anweisungen und Daten verlierst. Du wandelst blind den datenhaften Zeichenfolgenwert `$TestID` in einen anweisungshaften Scriptblock um und führst diese in vollständigen Vertrauen aus. Insbesondere führst du nicht ein fest definierten Scriptblock aus, sondern übergibt diesen als Eingabewert. Hier ein Beispiel für das böswillige Ausnutzen dieser Schwachstelle:

Wir konstruieren einen Skripteinschleusungsangriff. Dafür müssen wir nicht die Programmdatei beeinflussen, sondern nur die Daten. Wir überschreiben die Variable `$TestID` schreibgeschützt mit einen Scriptblock, der unsere Schadsoftware `notepad` ausführen wird. Scriptblocks erzeugt man mit geschweiften Klammern.

Anschließend rufen wir dein Script auf. Das Überschreiben in Zeile 9 schlägt fehl, da die Variable schreibgeschützt ist. Somit führen wir in Zeile 10 unseren böswilligen Scriptblock aus und die Schadsoftware `notepad` öffnet sich.

Teste das gerne einmal aus:
```powershell
New-Variable -Name TestID -Value { notepad } -Option ReadOnly -Force

# Wir rufen dein Program auf:

function starte_Test($TestID) {
    & $TestID
}

$TestID = { echo "harmloser Code" }
starte_Test -TestID $TestID
```

## Funktionen werden mit Zeichenfolgenwert identifiziert

```powershell
starte_Test "Verbindung_mit_eigenem_Host"
```

Ich finde es schwer lesbar, in deinem Funktionsaufruf zu erkennen, dass die Function, die so heißt wie dein Eingabetext, ausgeführt wird. Wenn du oder ein Kollege die Funktion umbenennst, musst du dich daran erinnern, dass dieser Zeichenfolgenwert eigentlich für den Funktionnamen steht.

# Wie löst man die Probleme?

```powershell
function Verbindung_mit_eigenem_Host {
    return $true
}

function starte_Test([Scriptblock]$Test) {
    $Testergebnis = $Test.Invoke() # führe den Scriptblock aus
    $TestName = $Test.Ast.Name # extrahiere den Funktionnamen aus dem Scriptblock
    if ($Testergebnis) {
        echo "Test: $TestName : OK"
    } else {
        echo "Test: $TestName : failed"
    }
}

starte_Test -Test $function:Verbindung_mit_eigenem_Host
```

Jetzt ist sehr gut lesbar, dass nicht irgendein beliebiger Zeichenfolgenwert übergeben wird, sondern eine Funktion referenziert wird. Und der Scriptblock `$Test` wird auf der Anweisungsebene und nicht auf der Datenebene gesetzt.

---
Sources:

Related:

Tags:
Frank Pusch