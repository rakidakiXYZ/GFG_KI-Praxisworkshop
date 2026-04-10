# 11 KI und Daten — Tabellen, Analyse, Dashboards

Dieses Kapitel zeigt Ihnen, wie Sie mit künstlicher Intelligenz Tabellen auswerten, Muster erkennen, Diagramme erzeugen und aus einem Zahlenberg eine verständliche Geschichte machen — ohne selbst eine Zeile Python schreiben zu müssen. Das Kapitel ist für Menschen geschrieben, die mit Excel-Dateien, CSV-Exports oder Reportings arbeiten und bisher das Gefühl hatten, dass eine ernsthafte Datenanalyse eine Aufgabe für Spezialistinnen und Spezialisten ist. Nach diesem Kapitel werden Sie anders darüber denken.

Die moderne Generation von KI-Werkzeugen hat die Hürde zur Datenanalyse dramatisch gesenkt. Was früher SQL, Pandas und Matplotlib voraussetzte, beantwortet eine KI heute auf eine präzise gestellte Frage hin in Sekunden — inklusive Diagramm und Kurzinterpretation. Der Haken: Die KI macht Fehler. Und weil sie ihre Fehler mit der gleichen Selbstsicherheit verkündet wie ihre Treffer, brauchen Sie ein paar Routinen, um die Spreu vom Weizen zu trennen. Genau diese Routinen sind das Herzstück dieses Kapitels.

Wir konzentrieren uns auf **Claude Cowork** und den mitgelieferten **xlsx-Skill** als Haupt­werkzeug. Beides haben Sie in Kapitel 10 kennengelernt. Der Grund für diese Wahl: Ihre Tabelle bleibt dabei auf Ihrem Rechner, wird in einem kontrollierten Ordner verarbeitet und nicht in einen anonymen Chat hochgeladen — was vor allem dann wichtig ist, wenn in der Tabelle personenbezogene Daten stehen. An den passenden Stellen zeigen wir aber auch, wann Sie alternativ den einfachen Datei-Upload in claude.ai oder ChatGPTs Advanced Data Analysis nutzen können.

Dieses Kapitel baut direkt auf Kapitel 10 (Claude-Infrastruktur) und Kapitel 14 (Ethik, Sicherheit und Verantwortung) auf. Die dort behandelte **Daten-Ampel** spielt hier eine zentrale Rolle: Nicht jede Tabelle darf in jedes Tool, und genau diese Entscheidung treffen Sie bei Daten­analyse ständig.

## Struktur

| Datei | Inhalt |
|-------|--------|
| [01 Warum KI für Daten](./01%20Warum%20KI%20fuer%20Daten.md) | Motivation, was KI bei Daten gut kann, wo die Grenzen liegen |
| [02 Tabellen an die KI übergeben](./02%20Tabellen%20an%20die%20KI%20uebergeben.md) | Upload-Wege im Vergleich, Cowork-Workflow, der xlsx-Skill, Datenschutz |
| [03 Datenqualität vor der Analyse](./03%20Datenqualitaet%20vor%20der%20Analyse.md) | Müll rein, Müll raus — Prüf-Prompts, typische Fallen, saubere Rohdaten |
| [04 Auswertungen und Pivots](./04%20Auswertungen%20und%20Pivots.md) | Summen, Durchschnitte, Pivots, Trends, Korrelationen — mit Beispielen |
| [05 Visualisierungen und Diagramme](./05%20Visualisierungen%20und%20Diagramme.md) | Welches Diagramm wofür, KI-generierte Charts, Design-Regeln |
| [06 Daten-Storytelling](./06%20Daten-Storytelling.md) | Vom Zahlenberg zur Kernaussage, Struktur, Empfänger­orientierung |
| [07 Sanity-Checks und Praxisleitfaden](./07%20Sanity-Checks%20und%20Praxisleitfaden.md) | Halluzinationen bei Zahlen, Checklisten, Muster-Prompts, Team-Routine |

## Illustrationen

Alle Illustrationen liegen im konsistenten Whiteboard-Stil (wie Kapitel 09, 10 und 14) unter [`illustrations/`](./illustrations/):

- `11-01-daten-pipeline.png` — Rohdaten → KI → Auswertung → Visualisierung → Story
- `11-02-sanity-check-cycle.png` — Sechs-Schritt-Routine, um Halluzinationen bei Zahlen zu finden
- `11-03-daten-zu-story-funnel.png` — Wie aus hunderten Zeilen drei Kernaussagen werden
- `11-04-diagrammtyp-entscheidungsbaum.png` — Welches Diagramm für welche Frage?
- `11-05-tabellen-ampel.png` — Welche Tabelle darf in welches Tool? (Ampel mit DSGVO-Bezug)

## Empfohlene Lesereihenfolge

**Wenn Sie wenig Zeit haben:** 01 (Einstieg) → 02 (Upload-Wege) → 07 (Sanity-Checks und Checklisten). Damit sind Sie arbeitsfähig und vermeiden die häufigsten Fehler.

**Wenn Sie mit großen oder sensiblen Tabellen arbeiten:** 01 → 02 (mit Schwerpunkt auf dem Cowork-Abschnitt und der Ampel) → 03 (Datenqualität) → 07 (Praxis). Die Teile 04 bis 06 können Sie später nachlesen.

**Wenn Sie regelmäßig Reportings bauen:** Der Reihe nach, 01 bis 07. Teil 04 ist Ihr Arbeits­tag, Teil 05 und 06 bringen die entscheidende Aufwertung für Empfängerinnen und Empfänger Ihrer Reports.

**Wenn Sie ein bestimmtes Problem akut haben:** Springen Sie direkt in den passenden Teil — jeder Teil ist für sich lesbar und hat am Ende Verweise auf die relevanten Nachbar­kapitel.

## Querverweise zu anderen Kapiteln

- **Kapitel 00 (Grundlagen LLMs)** — Wie Sprachmodelle Text verarbeiten. Hilft zu verstehen, warum LLMs bei Zahlen anfälliger sind als bei Text (Teil 07).
- **Kapitel 01 (Prompt Engineering Text)** — Die Sechs-Bausteine-Struktur funktioniert auch für Daten­prompts. In diesem Kapitel wenden wir sie auf Tabellen an.
- **Kapitel 02 (Strukturierte Prompts)** — Markdown-Tabellen und JSON als Austausch­format. Wenn Sie kleine Daten direkt in den Prompt schreiben wollen, lohnt ein Blick dorthin.
- **Kapitel 03 (GPTs und Projekte)** — Die Persona „Daten-Analyst" aus Kapitel 03 ergänzt dieses Kapitel um einen wiederverwendbaren Sparrings­partner.
- **Kapitel 08 (Prompt Bibliothek)** — Mehrere Template-Prompts dort lassen sich direkt für Daten­analyse wiederverwenden.
- **Kapitel 09 (KI-Tool-Landschaft 2026)** — Vergleich der Anbieter. Relevant, wenn Sie entscheiden, ob Claude, ChatGPT oder Gemini die richtige Wahl für Ihre Daten­analyse ist.
- **Kapitel 10 (Claude-Infrastruktur)** — Cowork, Skills, der xlsx-Skill. Die technische Grundlage, auf der Teil 02 aufbaut.
- **Kapitel 14 (Ethik, Sicherheit und Verantwortung)** — DSGVO, die Daten-Ampel, Halluzinationen. Teil 02 und 07 bauen direkt darauf auf.

## Stand der Fakten

Dieses Kapitel bezieht sich auf **Stand April 2026**. Werkzeuge in diesem Bereich entwickeln sich schnell — speziell die Rechen­leistung, die Anzahl der Zeilen, die ein Modell pro Anfrage verarbeiten kann, und der Funktions­umfang der Skills verändern sich ständig. Die **Prinzipien** in diesem Kapitel (Prompt-Muster, Sanity-Checks, Story­logik) bleiben stabil, die **genannten Tool-Versionen** prüfen Sie im Zweifel auf den Hersteller­seiten nach.

Aktuelle Modell­bezeichnungen zum Zeitpunkt des Schreibens: Claude Opus 4.6, Claude Sonnet 4.6, Claude Haiku 4.5. Für Daten­analyse-Aufgaben empfehlen wir in diesem Kapitel durchgehend Sonnet 4.6 oder Opus 4.6 — Haiku 4.5 ist zu schnell für die Sorgfalt, die bei Zahlen gefragt ist.

## Wichtiger Hinweis zu Genauigkeit

KI-Systeme sind bei Text enorm beeindruckend, bei Zahlen aber weiterhin fehler­anfällig — gerade bei aggregierten Werten, die sie ohne Tool-Unterstützung im Kopf berechnen. Der große Vorteil von Claude Cowork mit dem xlsx-Skill und von ChatGPT Advanced Data Analysis ist, dass diese Werkzeuge nicht „im Kopf rechnen", sondern echten Code ausführen (Pandas unter der Haube). Das reduziert Rechen­fehler dramatisch, eliminiert sie aber nicht: Die KI kann die **falsche Formel** anwenden oder die **falsche Spalte** zusammen­zählen, auch wenn die Arithmetik stimmt. Teil 07 zeigt Ihnen, wie Sie solche Fehler systematisch finden.

