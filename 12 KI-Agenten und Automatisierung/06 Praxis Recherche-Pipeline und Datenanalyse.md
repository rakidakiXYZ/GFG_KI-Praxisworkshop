# 06 Praxis — Recherche-Pipeline und wiederkehrende Datenanalyse

**Mehrstufige Web-Recherche und automatisierte Monatsreports — in Fortführung von Kapitel 11.**

---

## Warum dieses Tutorial?

Nach den zwei Workflows aus Teil 05 heben wir den Schwierigkeitsgrad. Beide folgenden Use-Cases sind **mehrstufig**, beide kombinieren mehrere Werkzeuge, und bei beiden ist die Verführung groß, die KI einfach „machen zu lassen". Genau hier entscheidet sich, ob Sie mit Agenten Zeit sparen oder am Ende Zeit verlieren, weil Sie das Ergebnis doch wieder von Hand nachprüfen müssen.

Der erste Workflow ist eine **mehrstufige Recherche-Pipeline**: Frage → Web-Recherche → Faktencheck → strukturierter Report. Der zweite ist eine **wiederkehrende Datenanalyse**, die direkt an Kapitel 11 anschließt — ein monatlicher Report, der sich selbst baut. Beide setzen voraus, dass Sie die Teile 01 bis 04 dieses Kapitels kennen und einen Minimalsatz MCPs eingerichtet haben.

**Was Sie nach diesem Tutorial wissen werden:**

- Wie Sie eine dreistufige Recherche-Pipeline (Suche, Faktencheck, Bericht) mit zwei Subagents bauen.
- Wie Sie eine wiederkehrende Datenanalyse als Slash-Command einrichten, der direkt auf Ihren Kapitel-11-Arbeitsordner zugreift.
- Wie Sie den `schedule`-Skill nutzen, damit der Monatsreport ohne Ihr Zutun entsteht.
- Welche Kontrollpunkte beide Workflows zwingend brauchen, damit Halluzinationen (bei Recherche) und Rechenfehler (bei Daten) nicht unbemerkt durchrutschen.
- Wie Sie die beiden Workflows mit einem `zahlen-pruefer`- und einem `fact-checker`-Subagent absichern.

---

## Use-Case 1: Recherche-Pipeline

**Das Problem.** Sie bekommen eine offene Frage — aus einem Kundenprojekt, einer internen Debatte, einer Anfrage der Geschäftsführung. Sie brauchen eine fundierte Antwort, idealerweise heute noch, und Sie wollen nicht in die Falle tappen, ein LLM zu fragen und dessen erste Antwort ungeprüft weiterzugeben. Gleichzeitig wollen Sie auch nicht zwei Stunden selbst googeln.

**Das Ziel.** Ein Workflow, der eine offene Frage annimmt, mehrere Suchen durchführt, die Ergebnisse sichtet, die wichtigsten Aussagen mit einem zweiten Modell gegenprüfen lässt und am Ende einen kurzen, belegten Report liefert. Belegbarkeit ist hier das entscheidende Wort: Jede Aussage im Report muss auf eine konkrete Quelle zeigen.

### Voraussetzungen

- Claude Code (Cowork geht auch, Claude Code ist hier flexibler wegen der Subagents).
- **Web-Suche und Web-Fetch** als eingebaute Tools (bei Claude Code Standard).
- Optional: **Firecrawl-MCP** oder **Apify-MCP** für strukturiertes Scraping, wenn die einfache Web-Suche nicht ausreicht.
- Optional: **Perplexity** parallel als Second-Opinion-Dienst, falls Sie die Möglichkeit haben — wir kommen darauf zurück.

### Die drei Stationen

Die Pipeline hat drei klare Stationen: **Suchen → Prüfen → Berichten**.

**Station 1 — Suchen.** Der Hauptagent formuliert drei bis fünf Teilfragen aus der Hauptfrage, führt pro Teilfrage eine Web-Suche durch, sammelt relevante Quellen und extrahiert die Kernaussagen. Wichtig: Pro Aussage wird die Quellen-URL und das Datum der Quelle mitgeschrieben. Ohne Quelle wird keine Aussage aufgenommen.

**Station 2 — Prüfen.** Ein Subagent `fact-checker` bekommt die gesammelten Aussagen und prüft jede einzeln: Steht sie tatsächlich in der angegebenen Quelle? Gibt es widersprechende Quellen? Ist die Quelle vertrauenswürdig (offizielle Stelle, etablierte Fachpublikation, Forschungspapier)? Jede Aussage bekommt eine Ampel: grün (belegt), gelb (teilweise/eine Quelle), rot (unklar oder widerlegt).

**Station 3 — Berichten.** Der Hauptagent schreibt den Report. Er enthält nur grüne und gelbe Aussagen; rote werden als „nicht belegbar" am Ende aufgeführt. Jede Aussage bekommt eine Fußnote mit Quelle und Datum. Der Report wird in `recherchen/<datum>-<thema>.md` gespeichert.

### Der Subagent `fact-checker`

```markdown
---
name: fact-checker
description: Use this agent to verify a list of statements against their 
  cited sources. Call it once per research job, after the search phase.
tools: WebFetch, WebSearch, Read
model: sonnet
---

Du bist ein praeziser Fact-Checker. Deine Aufgabe ist es, eine Liste 
von Aussagen und ihren angegebenen Quellen zu pruefen. Fuer jede Aussage 
lieferst Du eine Bewertung in einem von drei Status:

- **gruen**: Die Aussage steht eindeutig in der angegebenen Quelle und 
  wird von mindestens einer weiteren unabhaengigen Quelle gestuetzt.
- **gelb**: Die Aussage steht in der angegebenen Quelle, aber es gibt 
  keine zweite bestaetigende Quelle, oder es gibt leichte Abweichungen.
- **rot**: Die Aussage steht nicht (oder nicht so) in der angegebenen 
  Quelle, oder es gibt widersprechende Quellen.

## Arbeitsweise

Fuer jede Aussage tust Du genau das Folgende:

1. Rufe die angegebene Quelle auf (WebFetch oder WebSearch zur Verifikation).
2. Pruefe, ob die Aussage dort tatsaechlich in dieser Form zu finden ist.
3. Suche eine zweite unabhaengige Quelle, die das bestaetigt oder widerlegt.
4. Vergib die Ampel und gib einen zwei-satz-langen Kommentar:
   - Satz 1: Was hast Du gefunden?
   - Satz 2: Welche zweite Quelle (oder das Fehlen einer solchen) begruendet 
     Deine Bewertung?

## Regeln

- Keine Annahmen ueber Inhalte, die Du nicht tatsaechlich gelesen hast.
- Wikipedia ist eine brauchbare zweite Quelle, aber nie die einzige 
  bestaetigende Quelle. Du willst zusaetzlich eine Primaerquelle sehen.
- Wenn eine Quelle hinter einer Bezahlschranke liegt und Du den Abstract 
  lesen kannst, aber nicht den ganzen Artikel, dann sage das ausdruecklich: 
  "Abstract bestaetigt, Volltext nicht einsehbar".
- Gib keine "gelb"-Bewertung nur, weil Du unsicher bist. Gelb bedeutet: 
  Quelle bestaetigt, zweite Quelle fehlt. Wenn Du unsicher bist, ob die 
  Quelle die Aussage stuetzt, ist die Antwort "rot".

## Ausgabeformat

Pro Aussage ein Block in folgendem Format:

```
### Aussage N: [Kurztitel]
- **Original**: [woertliche Aussage]
- **Angegebene Quelle**: [URL oder Referenz]
- **Bewertung**: GRUEN / GELB / ROT
- **Gefunden**: [Satz 1]
- **Zweite Quelle**: [Satz 2]
```
```

Beachten Sie: Der Fact-Checker darf **Web-Tools** und **Read**, aber weder Write noch Edit. Er kann keine Dateien verändern — er berichtet nur. Das ist Absicht: Der Hauptagent kompiliert später den Report aus den Fact-Checker-Meldungen, nicht der Subagent selbst.

### Der Slash-Command `/recherche`

```markdown
---
description: Fuehrt eine dreistufige Recherche durch: Suche, Faktencheck, 
  Bericht. Braucht ein Thema als Argument. Speichert das Ergebnis unter 
  ./recherchen/.
---

Du bist der Recherche-Assistent. Du bekommst eine offene Frage als Thema. 
Fuehre die folgenden drei Stationen aus:

## Station 1: Suchen

1. Zerlege die Frage in 3 bis 5 konkrete Teilfragen. Zeige sie mir, bevor 
   Du suchst. Wenn ich nichts sage, arbeite weiter. Wenn ich Teilfragen 
   streiche oder ergaenze, passe an.
2. Fuehre pro Teilfrage eine oder zwei Web-Suchen durch.
3. Oeffne die vielversprechendsten Quellen pro Teilfrage mit WebFetch.
4. Extrahiere pro Teilfrage drei bis fuenf Kernaussagen. 
   Jede Kernaussage erhaelt:
   - den Wortlaut der Aussage
   - die URL der Quelle
   - das Veroeffentlichungsdatum der Quelle (wenn verfuegbar)
   - den Autor oder die Organisation

## Station 2: Faktencheck

Uebergib die Liste der Kernaussagen an den `fact-checker`-Subagent. 
Warte auf das Ergebnis. Sortiere die Aussagen anschliessend in drei 
Gruppen (gruen, gelb, rot).

## Station 3: Bericht

Schreibe einen Report mit folgender Struktur nach 
`./recherchen/<YYYY-MM-DD>-<kurztitel>.md`:

### Ueberschrift
Das Thema als Frage formuliert.

### Kurzfassung
Drei bis fuenf Saetze, die die Antwort zusammenfassen. Nur belegte 
Aussagen (gruen und gelb).

### Detailabschnitt
Ein Unterabschnitt pro Teilfrage. In jedem Unterabschnitt die belegten 
Aussagen als Fliesstext mit Fussnoten auf die Quellen. Keine Aufzaehlungen.

### Quellenverzeichnis
Alle Quellen nummeriert, mit URL, Autor, Datum und einer Zeile Kontext 
("Was ist das fuer eine Quelle?").

### Nicht belegbare Behauptungen
Die "rot"-Aussagen als Liste, mit einer Zeile, warum sie nicht belegt 
werden konnten. Das ist ein Pflichtabschnitt — auch wenn er leer ist.

## Bericht an mich

Zeige mir am Ende:
- den Pfad der Datei
- die Anzahl gruener, gelber und roter Aussagen
- die Teilfragen, die kaum belegbare Quellen lieferten (falls vorhanden)
```

### Der Ablauf in der Praxis

Sie haben die Frage „Wie ist der aktuelle Stand der KoKIVO-Behörde BNetzA bei der Umsetzung des EU AI Act in Deutschland?" — eine typische Recherche-Anfrage, wie sie in einem Beratungskontext vorkommt. Sie tippen:

```
/recherche KoKIVO-Umsetzung durch BNetzA in Deutschland, Stand April 2026
```

Der Agent zerlegt die Frage in vier Teilfragen:

1. Welche Rolle hat die BNetzA als KoKIVO (nationale zuständige Behörde)?
2. Welche Fristen gelten laut EU AI Act für die nationale Umsetzung?
3. Welche Hinweise und Verlautbarungen hat die BNetzA zur KI-Aufsicht veröffentlicht?
4. Welche Abgrenzung besteht zu Datenschutzaufsichtsbehörden der Länder?

Er sucht pro Teilfrage, öffnet zwei bis drei Quellen, extrahiert Aussagen. Nach etwa drei Minuten hat er 14 Kernaussagen mit Quellen gesammelt. Er übergibt die Liste an den `fact-checker`. Der prüft jede Aussage, ruft Quellen auf, sucht zweite Belege. Nach weiteren fünf Minuten kommt das Ergebnis: 9 grün, 3 gelb, 2 rot.

Der Hauptagent schreibt den Report, legt ihn unter `recherchen/2026-04-10-kokivo-bnetza.md` ab und meldet: „Datei gespeichert. 9 grüne, 3 gelbe, 2 rote Aussagen. Rot betraf: (1) Behauptung, die BNetzA habe bereits ein Sanktionsverfahren eröffnet — konnte in keiner offiziellen Quelle gefunden werden, (2) Aussage zu einer Mitarbeiterzahl — widerspruechliche Angaben in verschiedenen Medien."

Sie öffnen den Report, lesen die Kurzfassung, prüfen die zwei roten Punkte nach. Insgesamt haben Sie jetzt in knapp 15 Minuten eine Fundierung, an der Sie sich zwei Stunden selbst abgearbeitet hätten. Und Sie wissen genau, was belegt ist und was nicht.

### Sicherungsmechanismen

**Erstens — rote Aussagen sind Pflicht im Report, nicht optional.** Nur wer sieht, was nicht belegt ist, weiß, wo er vorsichtig sein muss. Schummeln Sie das nicht aus dem Ausgabeformat weg.

**Zweitens — Quellen werden nicht zusammengefasst, sondern zitiert.** Der Fact-Checker liest die Quellen tatsächlich an; er verlässt sich nicht auf Claude Googles Vorschau-Snippets. Wenn der Fact-Checker eine Quelle nicht laden kann (Paywall, 404), muss er das im Kommentar sagen.

**Drittens — Second-Opinion mit Perplexity (optional aber empfohlen).** Wenn das Thema kritisch ist, öffnen Sie parallel Perplexity und stellen die gleiche Frage dort. Die Überlappung der Quellen ist ein guter Indikator: Was in beiden Systemen mit gleichen Quellen beantwortet wird, ist robust. Was nur bei einem System auftaucht, braucht eine extra Runde.

### Grenzen und sinnvolle Erweiterungen

- **Grenze:** Stark meinungsgeladene Themen (politisch, ethisch) liefern oft viele „gelbe" Aussagen. Das ist nicht schlimm, aber es heißt, dass die Pipeline kein Ersatz für Ihr eigenes Urteil ist.
- **Grenze:** Bei ganz frischen Themen (das letzte Ereignis war vor 24 Stunden) sind Quellen oft noch nicht ausreichend vernetzt. Rechnen Sie mit mehr Rot.
- **Erweiterung:** Ein zweiter Subagent `quellen-pruefer`, der die Herkunft jeder Quelle bewertet (Primärquelle, Sekundärquelle, Blog, anonym). Das schärft die Grünen weiter.
- **Erweiterung:** Statt einer freien Frage eine **Recherche-Vorlage** für wiederkehrende Themen — z. B. monatliches Marktupdate zu einem Thema, bei dem die Teilfragen schon festgelegt sind.

---

## Use-Case 2: Wiederkehrende Datenanalyse

**Das Problem.** Einmal im Monat liegt ein neuer CSV-Export Ihrer Verkaufsdaten, Ihrer Supportanfragen oder Ihrer Website-Kennzahlen im Drive. Jedes Mal wiederholen Sie den gleichen Ablauf: Datei öffnen, Qualität prüfen, die fünf Standard-Auswertungen rechnen, ein Diagramm bauen, die Kurzinterpretation schreiben, als Word-Dokument speichern, per Mail verschicken. Dreißig Minuten Routine, jeden Monat.

**Das Ziel.** Ein Slash-Command `/monatsreport`, der den gesamten Ablauf in einem Rutsch erledigt, sich an den stabilen Prozess aus Kapitel 11 hält und die wichtigste Sicherung — den **Sanity-Check** — nicht überspringt.

### Voraussetzungen

- **Cowork** (dieses Mal sinnvoller als Claude Code, weil der xlsx-Skill besser integriert ist).
- Die Kapitel-11-Konventionen: Rohdaten unter `daten/roh/`, aufbereitete Daten unter `daten/sauber/`, Reports unter `reports/`.
- Den **xlsx-Skill** aktiv (mitgeliefert).
- Den **docx-Skill** aktiv (mitgeliefert).
- Optional: **Google Drive MCP** verbunden, falls die Rohdaten aus Drive kommen.

### Der Subagent `zahlen-pruefer`

Dieser Subagent ist der Sanity-Check aus Kapitel 11 Teil 07 — aber in Subagent-Form, damit er automatisch nach jeder Analyse läuft.

```markdown
---
name: zahlen-pruefer
description: Use this agent proactively after generating any data report 
  with calculated figures. The agent checks each headline number against 
  the raw source data and flags discrepancies.
tools: Read, Grep, Bash
model: sonnet
---

Du bist der Zahlen-Pruefer. Deine Aufgabe ist es, die Kennzahlen eines 
frisch erstellten Reports stichprobenhaft gegen die Rohdaten zu 
verifizieren.

## Arbeitsweise

1. Du bekommst:
   - den Pfad zur Rohdatendatei (CSV oder XLSX)
   - den Pfad zum fertigen Report (docx oder md)
   - eine Liste der zu pruefenden Kennzahlen (z. B. "Gesamtumsatz Maerz", 
     "Top-5-Produkte nach Umsatz", "Umsatz-Veraenderung gegenueber Vormonat")

2. Fuer jede Kennzahl fuehrst Du eine eigene, minimale Verifikationsrechnung 
   aus, ganz unabhaengig vom urspruenglichen Analyseweg:
   - Fuer Summen: `awk`-Rechnung auf der CSV, pandas-Summe auf dem XLSX, 
     oder eine direkte Nachrechnung ueber Read-Tool.
   - Fuer Rangfolgen: kontrolliere die Top-Liste, indem Du die Rohdaten 
     sortierst und die ersten Eintraege pruefst.
   - Fuer prozentuale Veraenderungen: rechne die Basiswerte nach und 
     berechne die Prozentzahl selbst.

3. Pro Kennzahl meldest Du:
   - **OK**: Dein Ergebnis stimmt mit dem Report-Wert ueberein (Toleranz 
     bei Rundungen erlaubt, aber erklaert).
   - **ABWEICHEND**: Dein Ergebnis weicht ab. Nenne Deinen Wert, den 
     Report-Wert, und eine plausible Ursache (Filterung, Zeitraum, Einheit).
   - **NICHT PRUEFBAR**: Du konntest die Berechnung nicht nachvollziehen 
     (z. B. weil die Rohdaten eine andere Struktur haben als angenommen).

4. Am Ende schreibst Du einen Zwei-Zeilen-Bericht:
   - Zeile 1: Anzahl OK / ABWEICHEND / NICHT PRUEFBAR
   - Zeile 2: Die kritischste gefundene Abweichung (wenn es eine gibt)

## Regeln

- Du rechnest jede Kennzahl tatsaechlich selbst nach. Du schaust nicht 
  nur, ob die Zahl im Report plausibel aussieht.
- Wenn Du eine Abweichung findest, erlaeuterst Du sie, aber Du 
  korrigierst den Report nicht. Das entscheidet der Hauptagent.
- Wenn Du ueberhaupt keine Abweichungen findest, ist das nicht unbedingt 
  ein gutes Zeichen — pruefe dann stichprobenhaft eine zweite Kennzahl 
  mit einer anderen Methode, damit Du nicht nur Deinen eigenen Weg 
  bestaetigst.
```

### Der Slash-Command `/monatsreport`

```markdown
---
description: Erstellt den monatlichen Datenreport aus der neuesten Rohdatei 
  in daten/roh/. Prueft Datenqualitaet, rechnet die Standard-Kennzahlen, 
  erzeugt Diagramme, schreibt die Kurzinterpretation, exportiert als 
  Word-Dokument und laesst den Zahlen-Pruefer gegenpruefen.
---

Du bist der Monatsreport-Assistent. Fuehre die folgenden Schritte aus.

## Schritt 1: Datei finden

Suche in `./daten/roh/` die neueste Datei (nach Aenderungsdatum). 
Erwartetes Format: CSV oder XLSX mit den Spalten 
[Datum, Kunde, Produkt, Menge, Umsatz]. Wenn das Format abweicht, 
brich ab und frag mich, ob das absichtlich ist.

## Schritt 2: Qualitaetscheck

Fuehre den 30-Sekunden-Qualitaetscheck aus Kapitel 11 durch:
- Struktur: Spalten wie erwartet?
- Lücken: Wie viele Zeilen haben Null-Werte?
- Duplikate: Wie viele? 
- Datumsbereich: Umfasst den erwarteten Monat?

Wenn es schwerwiegende Probleme gibt (mehr als 5% fehlende Werte, 
massive Duplikate, falscher Zeitraum), brich ab und melde die Probleme 
detailliert. Frag mich, ob Du trotzdem fortfahren sollst.

## Schritt 3: Kennzahlen

Rechne mit dem xlsx-Skill (oder pandas unter der Haube) die folgenden 
Standard-Kennzahlen:

1. Gesamtumsatz im Monat
2. Anzahl einzigartiger Kunden
3. Top 5 Produkte nach Umsatz
4. Top 5 Kunden nach Umsatz
5. Umsatz im Vergleich zum Vormonat (wenn der Vormonatsexport 
   in `./daten/roh/` vorhanden ist)

Speichere alle Zwischenergebnisse in `./daten/sauber/zwischen-<YYYY-MM>.xlsx`.

## Schritt 4: Diagramme

Baue drei Diagramme:
1. Umsatz pro Tag im Monat (Linie)
2. Top 5 Produkte nach Umsatz (Balken)
3. Umsatz-Verteilung nach Kunden-Dezilen (Balken)

Speichere sie als PNG unter `./reports/<YYYY-MM>/grafiken/`.

## Schritt 5: Kurzinterpretation

Schreibe eine drei-Absatz-lange Interpretation:
- Absatz 1: Zustand des Monats (Umsatz, Kundenanzahl, grosse Bewegungen).
- Absatz 2: Die zwei interessantesten Befunde (z. B. neuer Top-Kunde, 
  ausgefallenes Produkt).
- Absatz 3: Eine Empfehlung oder ein Punkt, der naeher angeschaut 
  werden sollte.

Keine Spekulationen ueber Ursachen, die Du nicht belegen kannst.

## Schritt 6: Word-Dokument

Nutze den docx-Skill, um das Gesamtergebnis als Word-Dokument zu 
erstellen unter `./reports/<YYYY-MM>/monatsreport-<YYYY-MM>.docx`. 
Das Dokument enthaelt:
- Titelseite mit Monat und Erstellungsdatum
- Kurzinterpretation aus Schritt 5
- Die drei Diagramme aus Schritt 4
- Eine Tabelle mit den Kennzahlen aus Schritt 3

## Schritt 7: Zahlen-Pruefung

Rufe den `zahlen-pruefer`-Subagent auf. Uebergib:
- Pfad zur Rohdatei aus Schritt 1
- Pfad zum fertigen Report aus Schritt 6
- Liste der zu pruefenden Kennzahlen (die 5 aus Schritt 3)

Warte auf den Zwei-Zeilen-Bericht. Wenn es ABWEICHUNGEN gibt, zeige sie 
mir ausdruecklich und frage nach, bevor Du den Report als fertig meldest.

## Schritt 8: Abschlussbericht

Zeige mir am Ende:
- Pfad der Word-Datei
- Zahlen-Pruefer-Ergebnis (OK/ABWEICHEND/NICHT PRUEFBAR)
- die drei wichtigsten Kennzahlen aus dem Report

Versende nichts, schick keine Mails. Nur speichern und mir berichten.
```

### Der Ablauf in der Praxis

Am ersten Werktag jedes Monats öffnen Sie Cowork, und der neue CSV-Export liegt schon in `daten/roh/`. Sie tippen `/monatsreport` im Chat.

Der Agent arbeitet die acht Schritte ab. Dauer: je nach Dateigröße drei bis sechs Minuten. Sie sehen die Zwischenmeldungen:

```
Schritt 1: Neueste Datei: daten/roh/verkaeufe-2026-03.csv. 14.812 Zeilen. OK.
Schritt 2: Qualitaet: 12 fehlende Umsatz-Werte (0.08%), 0 Duplikate, 
           Zeitraum 1.-31. Maerz korrekt. Weiter.
Schritt 3: Kennzahlen berechnet. Gesamtumsatz: 2.148.334 EUR.
Schritt 4: Diagramme erstellt.
Schritt 5: Interpretation geschrieben.
Schritt 6: Word-Dokument unter reports/2026-03/monatsreport-2026-03.docx.
Schritt 7: Zahlen-Pruefer laeuft...
           Zahlen-Pruefer: 5 OK, 0 ABWEICHEND, 0 NICHT PRUEFBAR. 
           Alle Kennzahlen unabhaengig nachgerechnet, Werte stimmen.
Schritt 8: Fertig. 
           Datei: reports/2026-03/monatsreport-2026-03.docx
           Gesamtumsatz Maerz: 2.148.334 EUR (+8.4% ggue. Februar)
           Top-Produkt: XYZ mit 412.100 EUR
           Top-Kunde: Kunde ABC mit 287.450 EUR
```

Sie öffnen die Word-Datei, prüfen die Interpretation, passen gegebenenfalls einen Satz an, und verschicken sie selbst. Dauer insgesamt: 10 Minuten, statt 30.

### Mit dem `schedule`-Skill automatisch laufen lassen

Wenn Sie diesen Report jeden Monat manuell starten, sparen Sie schon Zeit. Wenn Sie ihn vom `schedule`-Skill am ersten Werktag jedes Monats automatisch auslösen lassen, läuft er, während Sie Kaffee holen. Der dafür nötige Prompt an Cowork:

```
Nutze den schedule-Skill und lege eine wiederkehrende Aufgabe an:

- Name: "monatsreport-auto"
- Zeitplan: am ersten Werktag jedes Monats um 07:30 Uhr
- Aktion: Fuehre den Slash-Command /monatsreport aus. 
  Wenn der Zahlen-Pruefer ABWEICHUNGEN meldet, sende mir eine Desktop-
  Benachrichtigung. Ansonsten keine Benachrichtigung — ich schaue 
  sowieso in den Ordner.
- Arbeitsordner: /pfad/zum/report-ordner
```

Der `schedule`-Skill legt die Aufgabe an, Cowork merkt sich den Zeitplan, und ab dem nächsten Monatswechsel läuft der Report von selbst. Sie sehen ihn am Morgen fertig im Ordner liegen — oder bekommen eine Benachrichtigung, wenn etwas nicht passt.

### Sicherungsmechanismen

**Erstens — der Zahlen-Prüfer ist nicht optional.** Er ist der wichtigste Teil des Workflows. Ein Monatsreport ohne Sanity-Check ist ein schöner Schein. Der Subagent rechnet unabhängig nach — wenn er das nicht tun würde, würde er nur die eigene Annahme bestätigen.

**Zweitens — Abbruchpunkte bei Datenqualität.** Wenn die Rohdaten auffällig schlecht sind (mehr als 5% Lücken, falscher Zeitraum, unerwartete Spalten), fragt der Agent nach, statt blind fortzufahren. Sie entscheiden bewusst.

**Drittens — kein automatisches Senden.** Der Report wird erstellt, nicht verschickt. Die Entscheidung, ob er an Kunden, die Geschäftsführung oder einen Verteiler geht, liegt bei Ihnen. Automatisiertes Senden an kritische Empfänger ist eine der häufigsten Ursachen für peinliche Vorfälle — vermeiden Sie das.

### Grenzen und sinnvolle Erweiterungen

- **Grenze:** Der Workflow geht davon aus, dass die Rohdaten-Spalten sich nicht ändern. Wenn Ihre IT das Export-Format umstellt, scheitert der Qualitäts-Check — das ist gut, aber Sie müssen dann die Definition anpassen.
- **Grenze:** Der Zahlen-Prüfer kann nur prüfen, was Sie ihm an Kennzahlen übergeben. Spezifische Feinheiten (Sonderpreise, Rabatte, Stornierungen) sieht er nur, wenn sie explizit in der Kennzahlen-Liste stehen.
- **Erweiterung:** Ein `abweichungs-kommentator`-Subagent, der bei Monaten mit grösseren Veränderungen (±15% gegenüber Vormonat) eine zusätzliche Analyse der möglichen Gründe schreibt.
- **Erweiterung:** Ein `dashboard-aktualisierer`-Subagent, der die Kennzahlen parallel in ein vorhandenes Dashboard (Notion, Google Sheet, Looker) schreibt — aber nur in einen **Staging-Bereich**, nicht direkt ins Produktions-Dashboard. Dann entscheiden Sie wieder selbst, ob Sie „Live" klicken.

---

## Was die beiden Use-Cases verbindet

Die Recherche-Pipeline und die Datenanalyse teilen sich drei Muster, die den Unterschied zwischen „funktioniert" und „ist verlässlich" ausmachen:

**Erstens — jeder Subagent prüft, was der Hauptagent produziert.** Der `fact-checker` prüft die Aussagen. Der `zahlen-pruefer` prüft die Kennzahlen. In beiden Fällen ist der Prüfer ein eigener kleiner Claude, kein „Selbstkontrolle-Modus" des Hauptagenten. Das ist wichtig, weil Selbstkontrolle notorisch schlecht funktioniert — ein getrenntes Paar Augen findet, was die eigenen übersehen.

**Zweitens — nichts geht ohne Quellen.** Aussagen ohne Quelle werden rot. Kennzahlen ohne Nachrechnung werden „nicht prüfbar". Der Agent ist nicht berechtigt, unbelegbare Dinge als wahr zu verkaufen, und sein Report bildet das ab.

**Drittens — Menschen treffen die Entscheidungen mit Außenwirkung.** Der Recherche-Report wird nicht ungeprüft an Kunden verschickt. Der Monatsreport wird nicht automatisch an die Geschäftsführung gemailt. Der Agent bereitet vor, der Mensch entscheidet. Je automatisierter die Vorbereitung, desto wichtiger die bewusste Freigabe am Ende.

---

## Kernbotschaft

Die **Recherche-Pipeline** läuft in drei Stationen (Suchen, Prüfen, Berichten) mit einem `fact-checker`-Subagent, der jede Aussage per Ampel bewertet — rote Aussagen bleiben sichtbar. Die **wiederkehrende Datenanalyse** wird zum `/monatsreport`-Slash-Command mit einem `zahlen-pruefer`-Subagent, der jede Kennzahl unabhängig nachrechnet. Der `schedule`-Skill lässt beide wiederkehrend ohne manuellen Anstoß laufen. Drei Prinzipien halten die Workflows verlässlich: getrennte Prüfung durch einen zweiten Agenten, keine Aussagen ohne Quelle oder Nachrechnung, Außenwirkung immer durch den Menschen.

---

## Nächste Schritte

- **[07 Praxisleitfaden Grenzen und Sicherheit](./07%20Praxisleitfaden%20Grenzen%20und%20Sicherheit.md)** — der Abschluss: wann Automatisierung lohnt, welche Guardrails unverzichtbar sind, wie Sie Kosten im Blick behalten.
- Zurück zur Übersicht: **[README](./README.md)**.
- Querverweis: **Kapitel 11 Teil 07 (Sanity-Checks und Praxisleitfaden)** — dort ist der Zahlen-Prüfer als manuelle Routine beschrieben, dieses Tutorial übersetzt ihn in eine Subagent-Form.
