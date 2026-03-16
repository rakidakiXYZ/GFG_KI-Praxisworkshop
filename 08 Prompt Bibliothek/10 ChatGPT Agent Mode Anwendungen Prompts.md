# ChatGPT Agent Mode: Vom Chatbot zum virtuellen Mitarbeiter

## Wozu dient Agent Mode?

Normales Chatten mit KI: Sie stellen eine Frage, bekommen eine Antwort. **Agent Mode** dreht das um: Sie geben ChatGPT ein **Ziel** — und der Agent findet selbst heraus, welche Schritte nötig sind, um es zu erreichen.

Der Agent kann:
- **Im Web suchen** und aktuelle Informationen finden
- **Dokumente lesen** und analysieren
- **Dateien erstellen** (Präsentationen, Tabellen, Berichte)
- **Tools verbinden** (Gmail, Google Calendar, und mehr)
- **Wiederkehrend arbeiten** — z.B. jeden Morgen um 7:00 Uhr automatisch loslegen

Denken Sie an einen Agent wie an einen **virtuellen Mitarbeiter**: Sie definieren die Rolle, die Werkzeuge und die Erfolgskriterien. Der Agent erledigt den Rest.

## So verwenden Sie Agent Mode

1. **ChatGPT Plus öffnen:** Agent Mode ist für Plus-, Team- und Enterprise-Nutzer verfügbar.
2. **Aufgabe formulieren:** Beschreiben Sie das Ziel, nicht die einzelnen Schritte. Der Agent plant selbst.
3. **Tools aktivieren:** Verbinden Sie bei Bedarf Gmail, Google Calendar oder andere Dienste unter *Settings → Connected Apps* (im Menü links unten).
4. **Beobachten:** Der Agent zeigt Ihnen, was er tut (Websuche, Dateierstellung etc.). Sie können jederzeit eingreifen.
5. **Automatisieren:** Für wiederkehrende Aufgaben erstellen Sie einen Schedule (z.B. „Jeden Tag um 7:00 Uhr").

### 💡 Tipps

- **Ziel statt Schritte:** Schreiben Sie „Erstelle einen Wochenbericht" statt „Öffne meine E-Mails, dann schau den Kalender an, dann...". Der Agent plant die Schritte selbst.
- **Erfolgskriterien definieren:** Was soll am Ende rauskommen? Ein Dokument? Eine E-Mail? Eine Tabelle? Je klarer das Ziel, desto besser.
- **Tools vorher verbinden:** Wenn der Agent auf Gmail oder Calendar zugreifen soll, verbinden Sie die Dienste vorher unter *Settings → Connected Apps*.
- **Iterieren:** Der erste Durchlauf ist selten perfekt. Geben Sie Feedback: *„Mach den Bericht kürzer"* oder *„Füge eine Kostenübersicht hinzu"*.
- **Aktuelle Limitation:** Agents können noch nicht zuverlässig mehrere Tools verketten (z.B. „Lies E-Mail → erstelle automatisch Kalendertermin daraus"). Für solche Ketten brauchen Sie aktuell noch Automatisierungstools wie Zapier oder Make.

> ⚠️ **Datenschutz-Hinweis:** Wenn der Agent auf Ihre E-Mails oder Ihren Kalender zugreift, werden diese Daten an OpenAI übermittelt. Prüfen Sie die Datenschutzrichtlinien Ihres Unternehmens, bevor Sie geschäftliche Konten verbinden. Im Zweifel: erst mit privaten Accounts testen.

---

## Prompt 1: Täglicher Produktivitäts-Assistent

**Kategorie:** Wiederkehrende Aufgabe (Schedule)
**Benötigte Tools:** Google Calendar, Gmail

```
<agent_rolle>
Du bist mein täglicher Produktivitäts-Assistent.
</agent_rolle>

<schedule>
Jeden Tag um 07:00 Uhr:
</schedule>

<aufgaben>
1. Prüfe meinen Kalender für heute — welche Meetings stehen an?
2. Scanne meinen E-Mail-Posteingang nach wichtigen oder zeitkritischen Nachrichten
3. Identifiziere meine Top-Prioritäten für den Tag

Sende mir ein kompaktes Tages-Briefing:
- Meetings, auf die ich mich vorbereiten sollte
- E-Mails, die eine Reaktion erfordern
- Vorgeschlagene Fokus-Themen für heute
</aufgaben>

<format>
Kurz und übersichtlich. Maximal 200 Wörter.
Emoji-Header für schnelles Scannen:
📅 Termine | 📧 E-Mails | 🎯 Fokus
</format>
```

---

## Prompt 2: Wöchentlicher Management-Report

**Kategorie:** Wiederkehrende Aufgabe (Schedule)
**Benötigte Tools:** Google Calendar, Gmail

```
<agent_rolle>
Du bist mein Assistent für den wöchentlichen Rückblick.
</agent_rolle>

<schedule>
Jeden Freitag um 17:00 Uhr:
</schedule>

<aufgaben>
1. Analysiere meine Kalender-Aktivitäten der Woche
2. Scanne meine E-Mail-Aktivitäten
3. Identifiziere wichtige Ergebnisse, Entscheidungen und Muster

Erstelle einen vollständigen Wochenreport:
- Was ist diese Woche passiert? (Highlights)
- Erfolge und Fortschritte
- Probleme oder Risiken, die ich im Blick behalten sollte
- Was lief gut?
- Was kann ich nächste Woche verbessern?
</aufgaben>

<format>
Strukturiert mit Überschriften. Maximal 1 Seite.
Schließe mit 3 konkreten Empfehlungen für nächste Woche.
</format>
```

---

## Prompt 3: Deep Research — Thema analysieren

**Kategorie:** Einmalige Aufgabe (Recherche)

```
<agent_rolle>
Du bist ein Deep-Research-Analyst.
</agent_rolle>

<aufgabe>
Recherchiere und fasse die wichtigsten Trends zu [THEMA EINFÜGEN]
zusammen.
</aufgabe>

<vorgehen>
1. Durchsuche seriöse Quellen (Fachpublikationen, Studien,
   Branchenberichte)
2. Identifiziere mindestens 5 zentrale Trends oder Entwicklungen
3. Für jeden Trend:
   - Zusammenfassung in einem Satz
   - Ein konkretes Beispiel oder eine aktuelle Statistik
   - Quellenlink
4. Schließe mit einer Einschätzung: Was bedeutet das für
   [BRANCHE / UNTERNEHMEN / ABTEILUNG]?
</vorgehen>

<format>
Strukturierter Recherche-Bericht. Seriöse Quellen mit Links.
Sprache: Deutsch, sachlich, auf den Punkt.
</format>
```

**Beispiel-Einsatz:** *„Recherchiere die wichtigsten Trends im Bereich KI-Regulierung in der EU für 2026. Was bedeutet das für eine Volksbank?"*

---

## Prompt 4: Präsentation erstellen

**Kategorie:** Einmalige Aufgabe (Dateierstellung)

```
<agent_rolle>
Du bist ein Präsentations-Designer mit Erfahrung
in Business-Kommunikation.
</agent_rolle>

<aufgabe>
Erstelle eine Präsentation mit [ANZAHL] Folien zum Thema
"[TITEL EINFÜGEN]".
</aufgabe>

<inhalt>
Schwerpunkte:
- [Schwerpunkt 1]
- [Schwerpunkt 2]
- [Schwerpunkt 3]
</inhalt>

<design>
- Modernes, cleanes Layout
- Farbschema: [z.B. Blau und Weiß, passend zum Corporate Design]
- Wenig Text pro Folie — Kernaussagen + Visualisierung
- Letzte Folie: Zusammenfassung + Call-to-Action
</design>

<output>
Liefere die Präsentation als herunterladbare Datei.
</output>
```

---

## Prompt 5: Wiederkehrende Informationssuche

**Kategorie:** Wiederkehrende Aufgabe (Schedule)

```
<agent_rolle>
Du bist mein wiederkehrender Recherche-Assistent.
</agent_rolle>

<schedule>
Jeden Tag um 08:00 Uhr:
</schedule>

<aufgabe>
Suche online nach [WAS SUCHEN — z.B. neue Stellenangebote,
Marktentwicklungen, Wettbewerber-News, Immobilien].

Kriterien:
- [Kriterium 1 — z.B. "Remote-Stellen im Bereich Marketing"]
- [Kriterium 2 — z.B. "Gehalt ab 60.000 €"]
- [Kriterium 3 — z.B. "Veröffentlicht in den letzten 24 Stunden"]
</aufgabe>

<output>
Erstelle eine Übersicht der Top 5–10 Ergebnisse als Tabelle:
- Titel / Name
- Kurzbeschreibung
- Relevante Details (Preis, Gehalt, Datum etc.)
- Direkter Link

Speichere die Ergebnisse in einem Google Doc.
</output>
```

**Beispiel-Einsätze:**
- Tägliche Suche nach neuen KI-Regulierungen für den Bankensektor
- Wettbewerber-Monitoring: Was veröffentlichen andere Banken zum Thema KI?
- Immobiliensuche: Neue Gewerbeflächen in der Region

---

## Weitere Agent-Ideen

Nicht jede Idee braucht einen ausformulierten Prompt — hier eine Übersicht für Inspiration:

| Kategorie | Agent-Idee | Einmalig / Wiederkehrend |
|-----------|-----------|-------------------------|
| 💰 Finanzen | Monatliche Ausgaben analysieren, Sparpotenziale finden | Einmalig |
| 💰 Finanzen | Geschäftliche GuV analysieren, Handlungsempfehlungen geben | Einmalig |
| 📹 Content | YouTube-Video planen (Recherche, Script, SEO-Titel, Thumbnail-Ideen) | Einmalig |
| 📹 Content | Social-Media-Beiträge aus einem bestehenden Artikel ableiten | Einmalig |
| 🤝 Outreach | Micro-Influencer finden + personalisierte Ansprache schreiben | Einmalig |
| 🏠 Monitoring | Täglich Immobilien-Angebote nach Kriterien filtern | Wiederkehrend |
| 💼 Jobsuche | Täglich neue Remote-Stellen nach Kriterien sammeln | Wiederkehrend |
| ✈️ Reise | Reise planen mit Budget, Vorlieben und Kostenvergleich | Einmalig |
| 📊 Reporting | Wöchentlicher CEO-Report aus Kalender + E-Mails | Wiederkehrend |

---

## Agent Mode vs. normales Chatten

| | Normales Chatten | Agent Mode |
|---|---|---|
| **Sie geben** | Eine Frage | Ein Ziel |
| **KI macht** | Antwortet direkt | Plant Schritte, nutzt Tools, liefert Ergebnis |
| **Web-Zugriff** | Begrenzt | Aktiv (sucht, liest, vergleicht) |
| **Dateien** | Kann lesen | Kann lesen UND erstellen |
| **Tools** | Keine | Gmail, Calendar, und mehr |
| **Wiederkehrend** | Nein | Ja (Schedules) |
| **Wann nutzen** | Schnelle Fragen, Brainstorming | Komplexe Aufgaben, Workflows, Automatisierung |

---

