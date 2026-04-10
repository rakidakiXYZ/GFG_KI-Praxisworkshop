# 04 Auswertungen und Pivots

**Die Brot-und-Butter-Arbeit der Daten­analyse — von Summen und Durch­schnitten bis zu Trends und Korrelationen, mit den Prompts, die wirklich funktionieren.**

---

## Warum dieses Tutorial?

Dies ist das Arbeits­pferd dieses Kapitels. Wenn Sie Teil 02 (Übergabe­wege) und Teil 03 (Qualitäts­check) beherrschen, sind Sie bereit für die eigentliche Auswertung. Sie haben eine saubere Tabelle, Claude kennt sie, und jetzt wollen Sie Antworten auf Ihre Fragen.

Die meisten Fragen, die Sie in Ihrem Arbeits­alltag an eine Daten­tabelle stellen, lassen sich in eine von fünf Klassen einsortieren: **Summen und Aggregate, Pivots, Vergleiche, Trends, Korrelationen.** Für jede Klasse gibt es ein Standard-Muster, das die KI zuverlässig versteht. Wer diese fünf Muster kennt, kann 90 Prozent aller Business-Fragen an Daten selbst beantworten — ohne je eine Formel geschrieben zu haben.

Dieser Teil gibt Ihnen die fünf Muster mit Beispiel-Prompts, echten Ergebnissen und typischen Fall­stricken. Alle Beispiele beziehen sich auf denselben fiktiven Datensatz `verkaeufe_2025.xlsx` aus Teil 02, damit Sie die Muster direkt vergleichen können.

**Was Sie nach diesem Tutorial wissen werden:**

- Die fünf Frage­klassen, in die sich fast jede Daten­auswertung einsortieren lässt.
- Für jede Klasse ein robustes Prompt-Muster, das Sie nur leicht anpassen müssen.
- Worauf Sie bei der Formulierung jeder Frage achten müssen, damit die KI weiß, was genau Sie wissen wollen.
- Typische Fall­stricke und wie Sie sie erkennen, bevor Sie sie weiter­reichen.

## Klasse 1: Summen, Durch­schnitte und andere Aggregate

Die einfachste Klasse: Sie wollen einen einzelnen Wert aus allen Zeilen ableiten. Gesamt­umsatz, durchschnittliche Auftrags­größe, Anzahl der Bestellungen, höchster Einzel­auftrag, Median-Lieferzeit.

**Standard-Prompt:**

```
Bitte berechne aus verkaeufe_2025.xlsx die folgenden Kennzahlen:

1. Gesamt-Umsatz (Summe der Spalte „Umsatz")
2. Anzahl der Bestellungen (Anzahl der Zeilen)
3. Durchschnittlicher Umsatz pro Bestellung (Mittelwert)
4. Median-Umsatz pro Bestellung
5. Höchster und niedrigster Einzel-Umsatz mit dem jeweiligen Kunden.

Gib mir das als kleine Tabelle mit zwei Spalten (Kennzahl und Wert).
Formatiere Euro-Beträge mit Tausender-Trennung und zwei
Nachkommastellen.
```

**Warum es funktioniert:** Sie nennen die Datei, die Spalte und die gewünschte Formatierung explizit. Die KI muss nichts raten.

**Typischer Fall­strick:** „Durchschnitt" kann Mittelwert oder Median sein. Der Mittelwert reagiert stark auf Ausreißer — ein einziger Millionen-Auftrag kann den Durchschnitt über alle Zeilen verzerren. Der Median ist robuster. Als Faustregel: Wenn die Verteilung schief ist, melden Sie lieber den Median. Sagen Sie im Prompt explizit, was Sie meinen, oder lassen Sie sich beide geben.

**Zweiter Fall­strick:** Null-Werte und leere Werte werden unterschiedlich behandelt. Eine leere Zelle in einer Umsatz­spalte ist nicht dasselbe wie eine Null. Wenn Sie einen Mittel­wert berechnen, fragen Sie die KI explizit: „Wie gehst du mit leeren Werten um? Ignoriere sie oder zähle sie als Null?".

## Klasse 2: Pivots und Kreuz­tabellen

Die wichtigste und häufigste Frage­klasse in der Praxis. Sie wollen eine Größe **nach einer Dimension aufschlüsseln**: Umsatz pro Region, Umsatz pro Produkt, Bewerbungen pro Kanal, Support-Tickets pro Woche. Oder Sie wollen eine Größe **nach zwei Dimensionen** sehen: Umsatz pro Region und pro Quartal, Bewerbungen pro Kanal und pro Position.

**Standard-Prompt für eine Dimension:**

```
Bitte erstelle aus verkaeufe_2025.xlsx eine Pivot-Auswertung:
Summe des Umsatzes, gruppiert nach Region.
Sortiert absteigend nach Umsatz.
Gib mir die Tabelle plus eine Zeile mit der Gesamtsumme.
```

**Standard-Prompt für zwei Dimensionen:**

```
Bitte erstelle aus verkaeufe_2025.xlsx eine Kreuztabelle:
Zeilen = Region, Spalten = Quartal (Q1 bis Q4), Werte = Summe Umsatz.
Füge eine Gesamt-Zeile und eine Gesamt-Spalte hinzu.
Formatiere die Zahlen als Euro mit Tausender-Trennung.
```

**Typischer Fall­strick:** Die Anzahl der Gruppen kann überwältigend sein. Wenn Sie „Umsatz pro Kunde" fragen und 800 Kunden haben, bekommen Sie eine unübersichtliche Tabelle. Sagen Sie in solchen Fällen im Prompt: „Gib mir nur die Top 20 nach Umsatz und fasse den Rest in einer Zeile 'Sonstige' zusammen."

**Zweiter Fall­strick:** Quartal aus Datums­spalte ableiten. Wenn Ihre Tabelle eine Datums­spalte hat, aber keine Quartals­spalte, müssen Sie der KI sagen, sie soll das Quartal aus dem Datum ableiten. Der xlsx-Skill kann das, aber Sie müssen es explizit anweisen: „Leite das Quartal aus der Spalte 'Datum' ab."

## Klasse 3: Vergleiche und Veränderungen

Sie wollen zwei Zustände miteinander vergleichen: Dieses Jahr gegen letztes Jahr, dieser Monat gegen den Vormonat, Region A gegen Region B, Produkt X gegen Produkt Y.

**Standard-Prompt:**

```
Bitte vergleiche aus verkaeufe_2025.xlsx den Umsatz zwischen dem ersten
und dem zweiten Halbjahr 2025:

1. Absolute Summe je Halbjahr.
2. Absolute Differenz.
3. Prozentuale Veränderung.
4. Die drei Regionen mit der größten absoluten Steigerung.
5. Die drei Regionen mit dem größten absoluten Rückgang.

Gib mir das als strukturierten Bericht mit klarer Gliederung.
```

**Typischer Fall­strick:** Prozentuale Änderungen auf kleinen Basiswerten. Wenn eine Region im H1 nur 100 Euro Umsatz hatte und im H2 200 Euro, ist das eine Steigerung von 100 Prozent — aber absolut nur 100 Euro, und damit praktisch irrelevant. Fragen Sie deshalb immer nach **absoluten** und **relativen** Werten.

**Zweiter Fall­strick:** Vergleichbarkeit. Wenn ein neues Produkt erst in der zweiten Jahres­hälfte verkauft wurde, ist der „Jahres­vergleich" für dieses Produkt irreführend. Die KI merkt das nicht von selbst. Lassen Sie sich in solchen Fällen immer auch eine Liste der „nur in einem Halb­jahr vorhandenen" Produkte oder Regionen geben.

## Klasse 4: Trends und Zeit­reihen

Sie haben eine Datums­spalte und wollen sehen, wie sich eine Größe über die Zeit entwickelt: Umsatz pro Monat, Anzahl Supports pro Woche, Anmeldungen pro Tag.

**Standard-Prompt:**

```
Bitte erstelle aus verkaeufe_2025.xlsx eine Zeitreihe:
Summe Umsatz pro Monat für das gesamte Jahr 2025.
Gib mir die Tabelle (12 Zeilen) und beschreibe den Verlauf in drei
Sätzen: Gesamttrend, stärkster und schwächster Monat, Besonderheiten.

Erzeuge zusätzlich ein Liniendiagramm mit dem Monatsverlauf und
speichere es als umsatz_2025_monatsverlauf.png im Arbeitsordner.
```

**Typischer Fall­strick:** Saisonalität vs. echter Trend. Ein Rückgang im Sommer kann Saisonalität sein, kein Alarm­zeichen. Die KI kann das erklären, wenn Sie sie darauf ansprechen: „Ist der Rückgang im August ein Hinweis auf einen Trend oder typisch saisonal, wenn man die Vorjahres­daten kennt?". Wenn Sie keine Vorjahres­daten haben, bleibt das eine offene Frage.

**Zweiter Fall­strick:** Zu feine Granularität. Ein Tages­verlauf über ein ganzes Jahr hat 365 Datenpunkte und sieht in einem Diagramm schnell wie Rauschen aus. Monats- oder Wochen­werte sind oft besser lesbar. Lassen Sie die KI bei Bedarf ein **gleitendes Mittel** über sieben Tage berechnen, um Schwankungen zu glätten.

**Dritter Fall­strick:** Leere Perioden. Wenn in einem Monat gar keine Daten vorliegen, zeigt das Diagramm einen abrupten Bruch — oder die KI interpoliert stillschweigend. Fragen Sie explizit: „Wie gehst du mit Monaten ohne Daten um?"

## Klasse 5: Korrelationen und einfache Muster

Sie wollen wissen, ob zwei Größen zusammen­hängen: Je höher X, desto höher Y? Oder desto niedriger? Oder gar kein Zusammen­hang?

**Standard-Prompt:**

```
Bitte prüfe aus verkaeufe_2025.xlsx, ob es einen Zusammenhang gibt
zwischen der Spalte „Rabatt-Prozent" und der Spalte „Umsatz pro
Bestellung".

1. Berechne den Pearson-Korrelationskoeffizienten.
2. Erzeuge ein Streudiagramm mit Rabatt-Prozent auf der X-Achse und
   Umsatz auf der Y-Achse.
3. Beschreibe den Zusammenhang in zwei Sätzen, angemessen vorsichtig:
   nenne die Richtung (positiv/negativ/keiner), die Stärke (schwach/
   mittel/stark) und weise explizit darauf hin, dass Korrelation nicht
   Kausalität bedeutet.

Speichere das Diagramm als rabatt_vs_umsatz.png im Arbeitsordner.
```

**Typischer Fall­strick:** Die Scheinkorrelation. Zwei Werte können stark korrelieren, weil beide von einer dritten, nicht gemessenen Größe abhängen. Ein Beispiel: Umsatz und Mit­arbeiterzahl korrelieren positiv, aber nicht, weil die eine die andere verursacht, sondern weil beide mit der Firmen­größe wachsen. Die KI erkennt solche Effekte nicht von selbst. Fragen Sie sich bei jedem Zusammen­hang: Gibt es eine andere Erklärung?

**Zweiter Fall­strick:** Lineare Korrelation misst nur lineare Zusammen­hänge. Wenn die Beziehung U-förmig ist (erst steigt, dann fällt), zeigt der Pearson-Wert null, obwohl ein Zusammen­hang da ist. Schauen Sie deshalb immer auch aufs Streu­diagramm, nicht nur auf die Zahl.

**Dritter Fall­strick:** Statistische Signifikanz. Bei kleinen Daten­mengen ist ein gemessener Korrelations­wert womöglich Zufall. Die KI kann Ihnen einen p-Wert nennen, aber ob der aussage­kräftig ist, hängt vom Kontext ab. Wenn Ihre Entscheidungen wirklich auf einer Korrelation beruhen sollen, bitten Sie eine Statistikerin um Rat.

## Ein vollständiges Mini-Projekt als Vorlage

Damit Sie sehen, wie die Klassen ineinander­greifen, hier ein typisches Mini-Projekt: Sie wollen aus der Verkaufs­tabelle einen Mini-Report mit fünf Kern­zahlen bauen.

**Prompt:**

```
Ich baue einen Quartals-Report aus verkaeufe_2025.xlsx für das
erste Quartal 2025. Bitte liefere mir:

1. KENNZAHLEN: Gesamtumsatz Q1, Anzahl Bestellungen Q1, durchschnittlicher
   Bestell-Umsatz Q1 (Median), Anzahl aktive Kunden Q1.

2. PIVOT: Umsatz pro Region für Q1, absteigend sortiert, mit Anteil
   am Gesamt-Q1-Umsatz in Prozent.

3. VERGLEICH: Umsatz Q1 2025 gegen Q4 2024 (absolut und prozentual).
   Falls Q4 2024 nicht in der Datei ist, sag mir das und liefere
   stattdessen den Vergleich zu Q2 2025 oder lass diesen Punkt weg.

4. TREND: Umsatz pro Woche in Q1, als kleine Tabelle (13 Zeilen)
   und als Liniendiagramm, gespeichert als q1_wochenverlauf.png.

5. AUFFÄLLIGKEITEN: Wenn dir beim Durchgehen etwas ins Auge sticht —
   ungewöhnlich hohe oder niedrige Woche, einmaliger Großauftrag,
   Ausreißer — nenne es in einem kurzen Abschnitt „Besonderheiten".

Gib mir alles als strukturierten Bericht mit klaren Überschriften.
Maximal 600 Wörter insgesamt. Rechnungen mit dem xlsx-Skill, nicht
im Kopf.
```

Beachten Sie die letzten zwei Sätze: Die **Wort­grenze** zwingt die KI zur Verdichtung, und der Hinweis auf den Skill ist Ihre Versicherung gegen die Kopf­rechnen-Falle.

## Was Sie mitnehmen sollten

Die fünf Klassen — Aggregate, Pivots, Vergleiche, Trends, Korrelationen — decken 90 Prozent der Daten­auswertungen in der Praxis ab. Mit den fünf Prompt-Mustern, die Sie in diesem Teil gesehen haben, können Sie die meisten Reports bauen, die ein Wissens­arbeiter in einem normalen Unternehmen braucht.

Zwei Dinge sollten Sie aus diesem Teil immer im Kopf behalten: **Erstens**, jede Auswertung muss mit einem expliziten Hinweis auf ein echtes Rechen­werkzeug verbunden sein — sonst rechnet die KI im Kopf. **Zweitens**, jede Prozent­zahl, jeder Durchschnitt, jeder Trend sollte kontextualisiert werden: Absoluten Wert dazu, Ausgangs­basis nennen, Ausreißer erwähnen. Erst dann ist die Zahl verwertbar.

Der nächste Teil wechselt von den Zahlen zu den Bildern: Wie visualisieren Sie die Ergebnisse so, dass sie auch andere verstehen?

---

**Weiter geht es mit:** [05 Visualisierungen und Diagramme](./05%20Visualisierungen%20und%20Diagramme.md) — welches Diagramm für welche Frage, wie Sie KI-generierte Charts lesen und wie Sie verhindern, dass die KI eine hübsche, aber unpassende Visualisierung baut.
