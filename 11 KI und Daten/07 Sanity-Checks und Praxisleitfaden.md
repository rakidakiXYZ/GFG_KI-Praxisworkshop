# 07 Sanity-Checks und Praxisleitfaden

**Die letzte Verteidigungs­linie gegen Halluzinationen bei Zahlen — plus Checklisten und Team-Routinen für den Arbeits­alltag.**

---

## Warum dieses Tutorial?

Sie haben in den Teilen 01 bis 06 gelernt, wie Sie saubere Daten analysieren, Pivots bauen, Diagramme erzeugen und aus Zahlen eine Geschichte machen. Der letzte Schritt, der über Erfolg oder Peinlichkeit entscheidet, ist die Prüfung: Stimmt das eigentlich alles? Ist die Zahl, die Sie in den Bericht übernehmen wollen, wirklich richtig — oder hat die KI sie sich plausibel ausgedacht?

Dieser Teil ist die Sammlung der Werkzeuge, die Ihnen helfen, diese Frage verlässlich zu beantworten. Er knüpft direkt an Kapitel 14, Teil 04 (Halluzinationen erkennen) an und spitzt die dort vorgestellten Methoden auf den besonderen Fall von **Zahlen** zu — weil Zahlen eine eigene Art von Halluzination haben. Eine erfundene Zahl sieht nicht anders aus als eine richtige. Sie lügt nicht mit Worten, sie lügt mit Ziffern. Und genau deswegen braucht sie eigene Prüf­methoden.

**Was Sie nach diesem Tutorial wissen werden:**

- Warum KI bei Zahlen besonders anfällig für Halluzinationen ist, auch wenn sie Rechen­werkzeuge nutzt.
- Den Sechs-Schritt-Sanity-Check für jede Kernzahl, die in einen Bericht soll.
- Drei Checklisten für typische Daten-Workflows, die Sie sofort übernehmen können.
- Einen Vorschlag für eine Team-Routine, die Fehler im Reporting systematisch reduziert.

![Sanity-Check-Cycle in sechs Schritten](./illustrations/11-02-sanity-check-cycle.png)

## Warum Zahlen-Halluzinationen so heimtückisch sind

Die KI halluziniert bei Zahlen auf mehreren Ebenen. Die offen­sichtliche ist das **falsche Kopf­rechnen**: Sie fragen nach einer Summe, die KI rechnet im Kopf und liefert eine plausible, aber falsche Zahl. Das lässt sich vermeiden, indem Sie immer ein echtes Rechen­werkzeug nutzen (Cowork mit xlsx-Skill oder ChatGPT Advanced Data Analysis). Soweit, so klar.

Aber es gibt tückischere Formen. Die KI kann **die richtige Rechnung auf die falschen Daten** anwenden — zum Beispiel die Summe über den falschen Monat bilden, weil die Datums­spalte in Wahrheit anders heißt als sie glaubt. Die Rechnung stimmt, das Ergebnis ist falsch. Sie merken es nur, wenn Sie prüfen.

Die KI kann **eine Zahl aus einer früheren Antwort halluzinieren**, die inzwischen nicht mehr gilt. Wenn Sie den Daten­satz zwischen­zeitlich geändert haben, aber die KI sich auf die alte Version „erinnert", bekommt die neue Zahl die alten Eigenschaften. Das passiert häufig bei langen Chats.

Die KI kann **Rundungen verschlucken**. Eine Aggregation über viele Werte mit vielen Nach­kommastellen kann durch Rundungs­fehler leichte Abweichungen zeigen. Normaler­weise harm­los, manchmal aber relevant — bei Euro-Beträgen mit Milliarden summen bedeutet eine winzige relative Abweichung eine große absolute Abweichung.

Und die KI kann **Einheiten verwechseln**. Gehalt in Monats- vs. Jahres­brutto. Umsatz in Tausend vs. Millionen. Zeit in Sekunden vs. Minuten. Wenn die Spalten­beschriftung die Einheit nicht explizit nennt, rät die KI, und manchmal rät sie falsch.

All diese Fehler­klassen haben eines gemeinsam: Sie fallen beim Lesen nicht auf. Die Zahl sieht richtig aus, der Satz klingt plausibel. Nur ein aktiver Prüf­prozess findet sie.

## Der Sechs-Schritt-Sanity-Check

Diese Routine wenden Sie auf jede Kernzahl an, die in einem Bericht, einer Präsentation oder einem Export landet. Sie kostet etwa zwei Minuten pro Zahl und fängt die meisten Fehler ab.

**Schritt 1: Ist die Zahl plausibel in der Größen­ordnung?** Das ist der einfachste Test. Wenn die KI Ihnen einen Gesamt­umsatz von 18 Millionen nennt, Sie aber grob wissen, dass Ihr Unter­nehmen bei etwa 15 Millionen liegt — dann passt das. Wenn die KI 180 Millionen nennt, stimmt etwas nicht. Diesen ersten Test machen Sie im Kopf, in drei Sekunden.

**Schritt 2: Ist die Rechnung nach­vollziehbar?** Fragen Sie die KI: „Zeige mir genau, welche Zeilen und welche Spalte du für diese Zahl verwendet hast." Wenn die Rechnung `Summe der Spalte 'Umsatz' über alle Zeilen, bei denen 'Datum' zwischen 2025-01-01 und 2025-03-31 liegt` lautet, ist das eindeutig und prüf­bar. Wenn die Antwort schwammig ist, ist das ein Warn­signal.

**Schritt 3: Stimmt die Kontroll­rechnung?** Lassen Sie sich eine zweite, unab­hängige Rechnung ausgeben, die dieselbe Zahl ergeben muss. Beispiel: Wenn die KI sagt, der Q1-Umsatz sei 4,2 Millionen, lassen Sie sie gegen­rechnen: „Summiere den Monats­umsatz für Januar, Februar und März einzeln, und gib dann die Summe. Passt das zu den 4,2 Millionen von vorhin?". Wenn ja: Zahl bestätigt. Wenn nein: Zahl neu berechnen.

**Schritt 4: Stichproben­prüfung.** Bei Pivots und Kreuz­tabellen lassen Sie sich eine Zelle erklären: „Für die Zelle Region=Nord, Quartal=Q2 hast du 820.000 genannt. Gib mir die ersten fünf Zeilen dieser Kategorie und die Summe dieser fünf Zeilen. Passt das?". Mit dieser Mikro-Rechnung können Sie sehr schnell prüfen, ob die Aggregation die richtigen Zeilen erwischt hat.

**Schritt 5: Einheit und Definition.** „Welche Einheit hat diese Zahl? Ist das brutto oder netto? Ist das pro Monat oder pro Quartal? Welche Definition von 'aktiver Kunde' hast du verwendet?". Wenn die Antwort nicht mit der Einheit der Spalten über­einstimmt, ist das ein Fehler — oder zumindest eine Unklarheit, die Sie vor der Weiter­gabe ausräumen müssen.

**Schritt 6: Externer Abgleich.** Wenn möglich, vergleichen Sie mit einer zweiten Quelle: Einer alten Excel-Datei, einem Report aus dem ERP, einer Angabe der Buch­haltung. Zwei unab­hängige Quellen, die dieselbe Zahl zeigen, sind die beste Absicherung, die Sie bekommen können. Gerade bei wichtigen Zahlen — Jahres­umsatz, Gehalts­durchschnitt, Mitarbeiter­zahl — ist dieser externe Abgleich Pflicht.

## Die drei Checklisten für den Arbeits­alltag

Diese drei Checklisten decken die meisten Situationen ab, in denen Sie mit KI und Daten arbeiten. Drucken Sie sie aus, legen Sie sie neben den Bildschirm, oder speichern Sie sie als Slash-Kommando in Claude Code.

### Checkliste A: Neue Datei, erste Auswertung

- [ ] Ist die Datei im richtigen Arbeits­ordner und für Cowork sichtbar?
- [ ] Habe ich die Daten-Ampel geprüft — darf die Datei in dieses Tool? (siehe Kapitel 14, Teil 02 und Kapitel 11, Teil 02)
- [ ] Habe ich Prompt 1 aus Teil 03 ausgeführt (Struktur und Grund­zahlen)?
- [ ] Habe ich Prompt 2 aus Teil 03 ausgeführt (Qualitäts­prüfung)?
- [ ] Habe ich entschieden, ob die Datei bereinigt werden muss?
- [ ] Wenn bereinigt: Liegt die neue Datei unter einem klaren Namen im Arbeits­ordner, und ist das Original unverändert?
- [ ] Ist das Modell auf Sonnet 4.6 oder Opus 4.6 gesetzt, nicht auf Haiku? (Haiku ist schnell, aber bei Zahlen zu flüchtig.)

### Checkliste B: Auswertung und Bericht

- [ ] Ist meine Frage so klar formuliert, dass die KI weiß, welche Spalte und welche Gruppierung gemeint ist?
- [ ] Habe ich explizit darauf hingewiesen, dass mit dem xlsx-Skill gerechnet wird und nicht im Kopf?
- [ ] Habe ich nach absoluten **und** relativen Werten gefragt, wenn Prozent­angaben im Spiel sind?
- [ ] Habe ich nach Median **und** Mittelwert gefragt, wenn Verteilungs­effekte relevant sein könnten?
- [ ] Habe ich für jede wichtige Zahl den Sechs-Schritt-Sanity-Check durchgeführt?
- [ ] Habe ich für jedes Diagramm die Sieben-Punkte-Prüfung aus Teil 05 durchgeführt?
- [ ] Ist die Geschichte verdichtet auf höchstens drei Kern­aussagen?
- [ ] Stimmt die erste Zeile so, dass jemand nur beim Überfliegen schon versteht, worum es geht?

### Checkliste C: Vor der Weitergabe

- [ ] Sind alle Zahlen gegen­gerechnet, mindestens per Stichprobe?
- [ ] Stimmen die Einheiten (Euro/kEuro, netto/brutto, pro Monat/pro Jahr)?
- [ ] Sind Daten­beschränkungen (fehlende Zeiträume, nicht erfasste Kategorien) transparent benannt?
- [ ] Ist klar, welche Aussagen **aus den Daten folgen** und welche **Interpretation** sind?
- [ ] Ist der Bericht datenschutz­konform — keine personen­bezogenen Daten, die nicht durften?
- [ ] Hat jemand anderes ihn kurz gegen­gelesen? (Vier-Augen-Prinzip bei wichtigen Reports.)

## Fünf Muster-Prompts zum sofortigen Verwenden

**Muster-Prompt 1: Zahlen-Plausibilitäts­check**

```
Ich habe aus verkaeufe_2025.xlsx berechnet, dass der Q1-Umsatz
4,23 Millionen Euro beträgt. Bitte gib mir drei Wege, um diese
Zahl zu überprüfen: eine Kontrollrechnung auf anderem Weg, eine
Plausibilitätsprüfung über externe Kennzahlen und eine
Stichprobenprüfung auf Zeilenebene.
```

**Muster-Prompt 2: Einheiten und Definitionen klären**

```
Bevor wir weitermachen: Für die folgenden fünf Kennzahlen bitte
jeweils die Einheit, die genaue Definition und die Herkunftsspalte
aus verkaeufe_2025.xlsx nennen:

1. Gesamtumsatz
2. Durchschnittsumsatz pro Bestellung
3. Aktive Kunden
4. Wachstum gegenüber Vorperiode
5. Rabattquote

Wenn eine Definition mehrdeutig ist, nenne alle möglichen
Definitionen und frag, welche ich meine.
```

**Muster-Prompt 3: Critic-Review eines fertigen Berichts**

```
Hier ist ein Entwurf für einen Quartals-Bericht basierend auf
verkaeufe_2025.xlsx.

[Bericht hier einfügen oder Dateiname nennen]

Prüfe ihn kritisch:

1. Gibt es Zahlen, die unbelegt behauptet werden?
2. Gibt es Sätze, die über das hinausgehen, was die Daten
   hergeben?
3. Gibt es Widersprüche zwischen verschiedenen Teilen des
   Berichts?
4. Gibt es Einheiten, die nicht eindeutig sind?
5. Ist die Verdichtung auf drei Kernaussagen gelungen oder
   schwimmt der Bericht?

Sei direkt. Lob gibst du nur, wenn es verdient ist.
```

**Muster-Prompt 4: Halluzinations­falle entschärfen**

```
Für die Aussage „Der Umsatz im Segment A ist im März um 18 Prozent
gestiegen" zeige mir bitte:

1. Welche genaue Rechnung du verwendet hast (Formel, Spalten,
   Zeitraum).
2. Die Absolutwerte für Februar und März im Segment A.
3. Die Differenz und die prozentuale Veränderung, separat
   berechnet.
4. Ob die Zahl 18 Prozent exakt mit der Prozent-Berechnung
   übereinstimmt oder gerundet ist.
```

**Muster-Prompt 5: Eine Tabelle für Nicht-Kenner erklären**

```
Erkläre die folgende Auswertung in einfacher Sprache, für jemanden,
der die Daten nicht kennt und keine Excel-Expertin ist:

[Tabelle oder Dateiname]

Die Erklärung soll:
- Maximal 150 Wörter haben.
- Die drei wichtigsten Aussagen nennen.
- Alle Fachbegriffe vermeiden oder im Vorbeigehen erklären.
- Am Ende einen Satz haben, der die Aussage der Daten in einer
  Kernbotschaft zusammenfasst.

Siezen.
```

## Eine Team-Routine für wiederkehrende Reports

Wenn Sie regelmäßig denselben Report bauen — zum Beispiel einen monatlichen Verkaufs­bericht —, lohnt es sich, die Routine zu formalisieren. Vier Bausteine helfen.

**Baustein 1: Ein Prompt-Pack.** Legen Sie alle Prompts, die Sie für den Report brauchen, in einer Text­datei ab. Strukturieren Sie sie als 1) Qualitäts­check, 2) Auswertung pro Kennzahl, 3) Diagramm­erzeugung, 4) Bericht-Entwurf, 5) Critic-Review. Beim nächsten Monats­report kopieren Sie die Prompts in derselben Reihen­folge und bekommen einen konsistenten Output.

**Baustein 2: Eine Abbruch­liste.** Notieren Sie sich die Fehler, die Sie in früheren Reports gefunden haben. „Im Februar hatte die Region-Spalte plötzlich zwei Schreib­weisen für 'Ost' und 'Osten', die wir vereinheitlichen mussten." „Im März hat die KI das Quartal falsch zugeordnet, weil die Datums­spalte im US-Format kam." Jeder Fehler, den Sie dokumentieren, wird beim nächsten Lauf zu einem Früh­warn­punkt.

**Baustein 3: Das Vier-Augen-Prinzip.** Wichtige Reports bekommen einen zweiten Gegen­leser, bevor sie raus­gehen. Die zweite Person muss nicht die Rohdaten prüfen, aber sie muss die Geschichte gegen­lesen und jede unplausible Zahl hinter­fragen. Bei kritischen Zahlen (öffentlicher Geschäfts­bericht, Präsentation vor Investoren) sollte die Prüfung auch gegen die Rohdaten laufen.

**Baustein 4: Die Change-Liste pro Lauf.** Wenn sich etwas in den Rohdaten oder im Prozess geändert hat (neue Spalte, neue Definition, veränderte Zählweise), notieren Sie es explizit im Report. So verhindern Sie, dass Monats­vergleiche später unbemerkt Äpfel mit Birnen vergleichen.

## Vorsicht bei drei Sonder­situationen

**Sonder­situation 1: Externe Veröffentlichung.** Wenn Zahlen außerhalb des Unter­nehmens landen — im Geschäfts­bericht, in einer Presse­mitteilung, in einem Angebot an Kunden — gilt eine höhere Sorgfalts­stufe. Jede Zahl muss nicht nur gegen­gerechnet, sondern auch **auditiert** sein: Wer hat sie wann wie berechnet, und ist die Quelle dokumentiert? Dies ist vor allem bei börsen­notierten Unter­nehmen rechtlich relevant. Ziehen Sie in solchen Fällen Ihre Buch­haltung oder Ihre Finanz­abteilung hinzu — KI-Auswertungen reichen als alleinige Quelle nicht.

**Sonder­situation 2: Personelle Entscheidungen.** Wenn Daten­auswertungen über Beförderungen, Gehälter, Bewerber­auswahl oder Kündigungen mitentscheiden, greifen DSGVO Art. 22 und der EU AI Act. Kapitel 14, Teil 03, hat die Details. Kurz: Personelle Entscheidungen dürfen in den meisten Fällen nicht **ausschließlich** auf Basis einer KI-Auswertung getroffen werden, und die betroffene Person hat ein Recht darauf, die Entscheidung zu hinter­fragen. Dokumentieren Sie deshalb immer, welche Rolle die Daten­analyse in der Entscheidung gespielt hat und welche menschliche Prüfung stattgefunden hat.

**Sonder­situation 3: Finanz- oder Gesundheits­daten.** Diese beiden Daten­kategorien sind recht­lich besonders geschützt. Finanz­daten von Dritten (zum Beispiel aus Bank­auszügen) und Gesundheits­daten gehören in die rote Kategorie der Daten-Ampel. Nutzen Sie dafür ausschließlich Cowork lokal mit xlsx-Skill — **niemals** den Browser-Upload, auch nicht mit Business-Account, außer Ihre Rechts­abteilung hat es explizit freigegeben.

## Was Sie mitnehmen sollten

Die Sanity-Check-Routine ist das, was einen Amateur von einer Profi-Analystin unter­scheidet. Die Rechenarbeit macht heute die KI. Die Prüfung macht der Mensch — und diese Prüfung ist keine Fußnote, sondern der Kern der Verantwortung, die bei Ihnen bleibt.

Drei Sätze fürs Gedächtnis: **Erstens**, jede Zahl im Bericht ist ein Ver­sprechen, und ein unge­prüftes Versprechen ist leicht­sinnig. **Zweitens**, zwei Minuten Sanity-Check pro Zahl sind die beste Zeit­investition, die Sie in der Daten­analyse machen können. **Drittens**, wer seine Fehler ehrlich benennt und dokumentiert, wird mit jedem Lauf besser — und verliert kein Vertrauen, sondern gewinnt welches.

Damit endet Kapitel 11. Sie haben jetzt das Hand­werk, sichere Tabellen-Analyse mit KI zu machen, die Ergebnisse in Geschichten zu verwandeln und sich gegen die häufigen Fallen zu wappnen. Der nächste logische Schritt, wenn Sie wollen, ist Kapitel 12 (Agenten und Automatisierung) — dort lernen Sie, wiederkehrende Analyse-Workflows ganz aus der Hand zu geben.

---

**Zurück zur Übersicht:** [README](./README.md) — Struktur, Lesereihen­folgen und Querverweise von Kapitel 11.

**Querverweis Kapitel 14:** [04 Halluzinationen erkennen](../14%20Ethik%20Sicherheit%20und%20Verantwortung/04%20Halluzinationen%20erkennen.md) — die allgemeine Form des Themas, aus der die hier gezeigten Zahlen-Sanity-Checks abgeleitet sind.
