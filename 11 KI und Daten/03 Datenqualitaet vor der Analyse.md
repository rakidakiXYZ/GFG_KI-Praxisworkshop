# 03 Datenqualität vor der Analyse

**Müll rein, Müll raus — und warum der 30-Sekunden-Qualitäts­check die wichtigste Gewohnheit dieses Kapitels ist.**

---

## Warum dieses Tutorial?

Es gibt in der Daten­analyse einen Satz, den Praktikerinnen seit Jahrzehnten wiederholen: **Garbage in, garbage out.** Wenn Ihre Roh­daten Fehler haben, wird Ihre Auswertung die Fehler übernehmen — oft in einer Form, die die Fehler versteckt, nicht offenbart. Ein Durchschnitt, der 30 Prozent zu niedrig ist, weil ein paar Zeilen Tippfehler haben, sieht völlig normal aus. Sie merken es erst, wenn jemand fragt: „Moment, passt das wirklich?"

Die KI macht diesen Effekt noch schlimmer, weil sie bereitwillig rechnet, was man ihr vorlegt, ohne von sich aus zu fragen: „Ist diese Zahl überhaupt plausibel?". Deswegen ist **die Qualitäts­prüfung vor der Auswertung** die wichtigste Gewohnheit, die Sie sich in diesem Kapitel aneignen sollten. Sie kostet Sie 30 Sekunden, und sie fängt die meisten Fehler ab.

Dieser Teil zeigt Ihnen, wie Sie in zwei bis drei Prompts eine saubere Qualitäts­prüfung durchführen, welche Probleme regelmäßig auftauchen und wie Sie sie mit KI-Hilfe beheben.

**Was Sie nach diesem Tutorial wissen werden:**

- Warum der Qualitäts­check die beste Investition am Anfang jeder Analyse ist.
- Welche sieben typischen Daten­probleme es gibt und wie Sie sie erkennen.
- Welche drei Standard-Prompts Sie für den Qualitäts­check wieder­verwenden können.
- Wann es sinnvoll ist, eine bereinigte Version der Datei zu erzeugen, und wann Sie die Original-Datei unangetastet lassen sollten.

## Die sieben typischen Datenprobleme

**Problem 1: Fehlende Werte.** Leere Zellen in einer Spalte, die eigentlich immer gefüllt sein müsste. Das passiert, wenn jemand vergessen hat, ein Feld auszufüllen, oder wenn ein Import einen Wert nicht übernehmen konnte. Wenn die KI diese Zeilen in einen Durchschnitt einbezieht, wird der Durchschnitt verzerrt — weil leere Werte in manchen Berechnungen als Null gelten, in anderen als „nicht vorhanden".

**Problem 2: Uneinheitliche Schreib­weisen.** „Müller", „müller", „MÜLLER", „Mueller", „Müller GmbH", „Müller Maschinenbau GmbH" — das sind in einer Kunden­tabelle sechs Einträge, aber vermutlich nur ein oder zwei echte Kunden. Jede Auswertung pro Kunde ist falsch, bis Sie das zusammen­geführt haben.

**Problem 3: Falsch formatierte Zahlen.** Zahlen, die als Text gespeichert sind, weil die Spalte in Excel auf „Text" stand. Zahlen mit Tausend­trennzeichen (`1.234,56` oder `1,234.56`), die je nach Lokalisierung unterschiedlich aussehen. Prozent­werte, die mal als `0,15` und mal als `15%` und mal als `15` gespeichert sind. Das sind die Klassiker, die Ihnen den Tag verderben, wenn Sie sie nicht früh entdecken.

**Problem 4: Datums­probleme.** Das Datum in der US-Schreib­weise (MM/DD/YYYY) statt deutsch (DD.MM.YYYY). Oder mal so, mal so, gemischt in derselben Spalte. Oder Texte wie „letzte Woche". Oder Datums­werte, die Excel als Zahl (Seriennummer) gespeichert hat, bei denen Sie nicht sehen, dass es ein Datum sein soll.

**Problem 5: Duplikate.** Dieselbe Zeile mehrfach in der Tabelle — weil der Export zweimal gelaufen ist, weil jemand die Datei zusammen­gefügt hat, weil zwei Systeme dieselben Daten liefern. Duplikate verdoppeln Summen und verzerren Durchschnitte.

**Problem 6: Ausreißer und offensichtlich falsche Werte.** Ein Alters­eintrag mit dem Wert 999. Ein Gehalt von einer Million Euro in einer Reihe, in der alle anderen bei 50.000 liegen. Ein Datum aus dem Jahr 1970 oder 2099. Das sind häufig Ergebnisse von automatisch gesetzten Default-Werten oder Tipp­fehlern, die jede Statistik kaputt machen.

**Problem 7: Struktur­probleme.** Die Tabelle hat verbundene Zellen, mehrere Kopf­zeilen, Zwischen­summen mitten in den Daten, leere Trenn­zeilen, Fußnoten unter der Tabelle, mehrere Tabellen in einem Arbeits­blatt neben­einander. Für menschliche Leserinnen ist das manchmal praktisch, für eine Maschine ist es ein Albtraum.

## Der 30-Sekunden-Qualitäts­check in drei Prompts

Hier ist die Grund­routine. Sie brauchen exakt drei Prompts, die Sie jedem neuen Datensatz voranstellen, bevor Sie irgend­etwas auswerten. Der Workflow geht davon aus, dass Sie Claude Cowork mit dem xlsx-Skill nutzen — für andere Tools müssen Sie nur die Formulierungen leicht anpassen.

### Prompt 1: Struktur und Grundzahlen

```
Bitte öffne die Datei <DATEINAME> mit dem xlsx-Skill. Gib mir:

1. Die Anzahl der Arbeitsblätter und deren Namen.
2. Für das erste (oder genannte) Arbeitsblatt: die Spaltennamen, die
   Gesamtzeilenzahl und den Datentyp jeder Spalte (Text, Zahl, Datum,
   gemischt).
3. Eine Beispielausgabe der ersten 5 und der letzten 5 Zeilen.

Gib mir das Ergebnis als zwei kleine Tabellen (Spaltenübersicht und
Beispielzeilen). Noch keine Auswertung, nur Struktur.
```

Das ist Ihr Standard-Einstieg. Sie sehen sofort, ob die Kopfzeile richtig erkannt wurde, ob die Spalten­typen sinnvoll sind und ob die letzten Zeilen noch gültige Daten enthalten oder schon in leere Zeilen oder Fußnoten übergehen.

### Prompt 2: Qualitäts­prüfung

```
Bitte prüfe jetzt dieselbe Datei auf typische Datenqualitätsprobleme:

1. Fehlende Werte pro Spalte (absolut und in Prozent).
2. Duplikate: vollständige Zeilen-Duplikate und Duplikate in Schlüssel-
   spalten (z.B. eindeutige IDs, wenn vorhanden).
3. Uneinheitliche Schreibweisen in Text-Spalten: nenne mir die fünf
   Text-Spalten mit der höchsten Varianz und gib jeweils drei
   Beispiele, wo Werte sich wahrscheinlich nur in Groß-/Kleinschreibung
   oder Leerzeichen unterscheiden.
4. Ausreißer in numerischen Spalten: nenne für jede numerische Spalte
   Minimum, Maximum, Median und nenne die drei extremsten Werte.
5. Datumsfelder: prüfe, ob alle Datumswerte einem konsistenten Format
   folgen und ob sie in einem plausiblen Bereich liegen.

Gib das Ergebnis als strukturierten Bericht mit klarer Gliederung.
Hervorheben, was auffällig ist.
```

Das ist Ihr eigentlicher Qualitäts­check. Nach diesem Prompt wissen Sie genau, wo Sie reinigen müssen und wo nicht.

### Prompt 3: Bewertung

```
Fasse die Qualitätsprüfung in drei Abschnitten zusammen:

1. Was ist okay und kann direkt ausgewertet werden?
2. Was ist problematisch, sollte aber für eine erste Auswertung
   ausreichen (und warum)?
3. Was muss zwingend vor einer Auswertung korrigiert werden (und
   wie würdest du es korrigieren)?

Maximal 300 Wörter.
```

Dieser dritte Prompt ist der wichtigste. Er zwingt die KI, aus der reinen Beobachtung eine Empfehlung abzuleiten, und er zwingt Sie, eine bewusste Entscheidung zu treffen, bevor Sie weitermachen. Ohne diesen Schritt passiert es leicht, dass Sie die Warn­signale übersehen und trotzdem blind weiterrechnen.

## Bereinigen — ja oder nein?

Wenn der Qualitäts­check Probleme zeigt, stellt sich die Frage: Bereinigen Sie die Datei, oder leben Sie mit den Schwächen?

**Bereinigen, wenn:**
- Die Probleme die Auswertung verfälschen würden (z.B. uneinheitliche Kunden­namen bei einer Pro-Kunden-Analyse).
- Die Probleme einfach zu beheben sind (Schreib­weisen vereinheitlichen, Zahlen­formate korrigieren).
- Sie die Datei regelmäßig auswerten werden und die Bereinigung einmal für dauerhaft lohnt.

**Nicht bereinigen, wenn:**
- Die Probleme für Ihre konkrete Frage irrelevant sind (fehlende Werte in einer Spalte, die Sie gar nicht nutzen).
- Die Bereinigung Entscheidungen erfordern würde, die Sie nicht sicher treffen können („Sind 'Müller GmbH' und 'Mueller Maschinenbau GmbH' derselbe Kunde?").
- Die Datei im Original unverändert bleiben muss (Audit-Anforderungen, offizielle Quelle).

**Goldene Regel: Bereinigen Sie nie das Original.** Wenn Sie bereinigen, lassen Sie Claude eine neue Datei schreiben — mit einem sprechenden Namen wie `verkaeufe_2025_bereinigt_2026-04-10.xlsx` — und lassen Sie das Original unangetastet. So können Sie jederzeit nachvollziehen, was geändert wurde, und bei Problemen zurück­kehren.

## Ein Beispiel-Bereinigungs-Prompt

Angenommen, Ihre Qualitäts­prüfung hat gezeigt, dass die Spalte „Kunde" uneinheitliche Schreib­weisen enthält. So könnten Sie Claude um eine Bereinigung bitten:

```
Bitte erzeuge eine bereinigte Version der Datei verkaeufe_2025.xlsx mit
folgenden Anpassungen in der Spalte „Kunde":

1. Leerzeichen am Anfang und Ende entfernen.
2. Doppelte Leerzeichen innerhalb durch einzelne ersetzen.
3. „GmbH", „Gmbh", „gmbh" vereinheitlichen zu „GmbH".
4. Wenn zwei Einträge sich nur in Groß-/Kleinschreibung unterscheiden,
   den mit korrekter Groß-/Kleinschreibung bevorzugen (z.B. „Müller
   GmbH" statt „müller gmbh").
5. Wenn du eine Änderung nicht sicher vornehmen kannst, markiere die
   betroffenen Zeilen in einer neuen Spalte „Hinweis" und schreibe
   dort, was du vermutest, aber nicht sicher weißt.

Speichere das Ergebnis als verkaeufe_2025_bereinigt.xlsx im selben
Ordner. Gib mir am Ende einen Bericht, welche Änderungen du vorgenommen
hast und welche Zeilen manuelle Prüfung brauchen.
```

Beachten Sie den vierten und fünften Punkt: Wir nehmen der KI **keine** Entscheidungen ab, bei denen sie sich nicht sicher ist. Die Grenze zwischen „automatisch korrigieren" und „manuell prüfen lassen" ist die wichtigste Stelle der Bereinigung.

## Wenn die Datenqualität hoffnungslos ist

Manchmal ist eine Tabelle so verhunzt, dass es keinen Sinn macht, sie mit KI zu reparieren: komplexe verbundene Zellen, inkonsistente Kopf­zeilen, Fußnoten und Zwischen­summen mitten drin, mehrere Tabellen in einem Blatt. In solchen Fällen ist es oft schneller, die Datei **manuell** in ein sauberes Format zu bringen — eine einzige Kopf­zeile, keine verbundenen Zellen, keine Fußnoten, eine Spalte pro Information. Nennen Sie diese saubere Version `<originalname>_flach.xlsx` und arbeiten Sie ab da mit dieser.

Die KI kann Ihnen in diesem Fall helfen, **manuell** aufzuräumen: Sie kann Ihnen sagen, welche Struktur sinnvoll wäre, welche Spalten in welche Zielspalte gehören und wie Sie eine Pivot-Umwandlung (wide-to-long oder long-to-wide) vornehmen sollten. Aber die eigentliche Aufräum­arbeit machen Sie in diesen Fällen besser selbst, weil jede maschinelle Interpretation weitere Fehler einführen kann.

## Qualitäts­check bei wiederkehrenden Reports

Wenn Sie denselben Report jeden Monat bauen, lohnt es sich, den Qualitäts­check zu **automatisieren**: Sie speichern die drei Prompts oben in einer Text­datei und schicken sie per Copy-Paste an die KI, oder Sie legen sie als Slash-Kommando in Claude Code an (Kapitel 10, Teil 04). Dann läuft der Qualitäts­check jeden Monat nach derselben Regel ab, und Sie merken sofort, wenn sich etwas an den Roh­daten geändert hat — zum Beispiel eine neue Spalte hinzu­gekommen ist oder ein alter Wert verschwunden.

Diese Routine ist auch eine ausgezeichnete Frühwarn­anlage gegen stille Daten­änderungen in Quell­systemen. Es ist nicht selten, dass ein Quellsystem „einfach so" eine Spalte umbenennt oder ein Format ändert. Ohne Qualitäts­check merkt das niemand — und Ihre nächste Auswertung rechnet dann plötzlich mit leeren Spalten.

## Was Sie mitnehmen sollten

Der Qualitäts­check ist nicht optional. Er ist die Versicherung dafür, dass alles, was danach kommt, auf verlässlichem Boden steht. Die Investition ist winzig — drei Prompts, zusammen keine fünf Minuten — und der Nutzen immens: Sie vermeiden damit in den meisten Fällen die häufigste Fehler­klasse der Daten­analyse überhaupt, nämlich **sauber gerechnete Ergebnisse auf kaputten Rohdaten**.

Gewöhnen Sie sich an, diese drei Prompts so automatisch auszuführen wie das Einschalten einer Kaffee­maschine am Morgen. Sobald eine neue Datei auf den Tisch kommt: Struktur, Qualitäts­prüfung, Bewertung. Erst danach kommt die eigentliche Analyse.

---

**Weiter geht es mit:** [04 Auswertungen und Pivots](./04%20Auswertungen%20und%20Pivots.md) — die Brot-und-Butter-Arbeit der Daten­analyse, von Summen und Durch­schnitten über Pivots bis hin zu Trends und Korrelationen.
