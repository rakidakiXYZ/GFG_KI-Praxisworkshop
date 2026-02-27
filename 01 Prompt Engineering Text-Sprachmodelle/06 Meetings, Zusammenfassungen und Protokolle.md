# Prompt-Vorlagen: Zusammenfassungen & Protokolle

**Meeting-Protokolle, Dokumentanalysen und Management-Summaries — die Prompts, die Ihnen Stunden an Nacharbeit ersparen**

---

## Warum dieses Tutorial?

In Tutorial 01-05 haben Sie gelernt, wie KI Ihre schriftliche Kommunikation verbessert — E-Mails, Beschwerdeantworten, Telefonleitfäden. Jetzt geht es um die andere Seite: Nicht Texte *schreiben*, sondern Texte *verdichten*. Aus lang mach kurz. Aus Chaos mach Struktur. Aus einem 90-Minuten-Meeting mach eine halbe Seite mit den drei Dingen, die wirklich zählen.

Das klingt banal. Ist es nicht.

Bankmitarbeiter verbringen geschätzt 15-20% ihrer Arbeitszeit mit Dokumentation. Meeting-Protokolle schreiben, Rundschreiben lesen und zusammenfassen, BaFin-Mitteilungen für den Vorstand aufbereiten, Beratungsgespräche nachbereiten. Das sind bei einer 40-Stunden-Woche 6 bis 8 Stunden — fast ein ganzer Arbeitstag, nur für Zusammenfassungen.

KI kann diese Zeit auf einen Bruchteil reduzieren. Aber nur, wenn Sie wissen, wie Sie die richtigen Prompts formulieren. Denn „Fasse das zusammen" ist wie „Mach mal ein Protokoll" — das Ergebnis ist Zufall. Was Sie brauchen, sind *Prompt-Vorlagen*, die der KI genau sagen, *was* sie extrahieren soll, *für wen* und *in welchem Format*.

> **Volksbank-Analogie:** Stellen Sie sich vor, Ihre Auszubildende kommt aus einem 2-Stunden-Vorstandsmeeting und Sie fragen: „Was wurde besprochen?" Wenn sie gut ist, sagt sie: „Drei Entscheidungen, zwei offene Punkte, und Herr Müller muss bis Freitag die Zahlen liefern." Wenn sie nicht gut ist, erzählt sie Ihnen 20 Minuten lang, wer was gesagt hat. Dieses Tutorial bringt Ihrer KI bei, wie die gute Auszubildende zu antworten.

**Was Sie nach diesem Tutorial können:**

- Meeting-Transkripte in strukturierte Protokolle umwandeln — mit Entscheidungen, Aufgaben und Deadlines
- Management-Summaries erstellen, die auf eine halbe Seite passen und trotzdem alles Wichtige enthalten
- Lange Dokumente (Rundschreiben, BaFin-Texte, Verbandsinformationen) in lesbare Zusammenfassungen verdichten
- Dokumentanalysen im McKinsey-Stil erstellen — für Vorstandsvorlagen und Aufsichtsratssitzungen
- Prompt-Templates für wiederkehrende Meeting-Typen aufbauen und wiederverwenden
- Datenschutz- und Compliance-Regeln bei der KI-gestützten Protokollierung einhalten

---

## Schritt 1: Vom Meeting zum Protokoll — Was Sie brauchen, bevor die KI anfängt

Bevor wir Prompts bauen, klären wir die Grundlage: Woher kommt der Text, den die KI zusammenfassen soll?

### Was ist ein Meeting-Transkript?

Ein **Transkript** ist die verschriftlichte Version eines Meetings — wie Untertitel, nur für das gesamte Gespräch. Es enthält alles, was gesagt wurde, inklusive der „Ähms", Wiederholungen und Themenwechsel.

**Wie bekomme ich ein Transkript?**

| Methode | Tool | So geht's |
|---|---|---|
| **Automatische Aufzeichnung** | Microsoft Teams | „Aufzeichnung & Transkription" starten (Drei-Punkte-Menü → Aufzeichnung starten) |
| | Zoom | „Aufzeichnen" aktivieren (mit Transkriptionsoption) |
| | Google Meet | „Transkription starten" im Menü |
| **Eigene Notizen** | Stift + Papier / OneNote | Während des Meetings mitschreiben. Muss nicht perfekt sein — die KI kann auch Stichpunkte verarbeiten |
| **Nachträgliche Umwandlung** | Whisper, Otter.ai, tl;dv | Audio-Aufzeichnung hochladen → Text zurückbekommen |

> **Wichtig zu verstehen:** Die KI kann nur verarbeiten, was im Transkript steht. Sie erfindet nichts dazu — außer Sie bitten sie darum (was Sie bei Protokollen nie tun sollten). Deshalb gilt: Je besser das Transkript, desto besser das Protokoll.

### Drei Quellen, drei Ansätze

```
┌─────────────────────────────────────────────────────────────────┐
│          📝 Was habe ich? → Welchen Prompt brauche ich?         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  📎 TRANSKRIPT (vollständig, automatisch erstellt)              │
│     → Prompt-Vorlage 1: Detailliertes Protokoll (Schritt 3)   │
│     → Prompt-Vorlage 2: Management-Summary (Schritt 4)        │
│                                                                 │
│  📋 EIGENE NOTIZEN (Stichpunkte, handschriftlich oder digital)  │
│     → Prompt-Vorlage 3: Notizen → Protokoll (Schritt 3)       │
│     Tipp: Geben Sie Kontext mit (Meeting-Typ, Teilnehmer)     │
│                                                                 │
│  📄 DOKUMENT (Rundschreiben, BaFin-Text, Bericht)              │
│     → Prompt-Vorlage 4: Dokumentanalyse (Schritt 5)           │
│     → Prompt-Vorlage 5: McKinsey-Stil Summary (Schritt 5)     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** Stellen Sie sich drei verschiedene Situationen vor: (1) Sie haben eine Teams-Aufzeichnung vom Kreditausschuss — da nutzen Sie das detaillierte Protokoll. (2) Sie haben sich während einer Filialleiter-Runde schnell Notizen gemacht — da reicht die Notizen-Vorlage. (3) Ein 40-seitiges BVR-Rundschreiben zur neuen Kreditrichtlinie liegt auf Ihrem Schreibtisch — da brauchen Sie die Dokumentanalyse.

---

## Schritt 2: Datenschutz und Compliance — Was niemals in die KI darf

**Lesen Sie diesen Abschnitt, bevor Sie den ersten Prompt ausprobieren.** Er ist kurz, aber entscheidend.

Als Bank unterliegen Sie dem Bankgeheimnis (§ 383 HGB), der DSGVO und den MaRisk-Anforderungen der BaFin. Das bedeutet: Nicht alles, was in einem Meeting besprochen wird, darf in ein KI-Tool eingegeben werden.

> **Seit Dezember 2025** hat die BaFin eine „Orientierungshilfe zu IKT-Risiken beim Einsatz von KI" veröffentlicht. Kernaussage: KI ist kein Innovationsthema mehr, sondern ein IKT-Risiko, das unter DORA (Digital Operational Resilience Act) fällt. Das heißt: Ihre Bank braucht klare Regeln, welche Daten in welche KI-Tools dürfen.

### Was Sie NIEMALS in ein externes KI-Tool eingeben dürfen

| Kategorie | Beispiele | Warum nicht |
|---|---|---|
| **Kundendaten** | Namen, Kontonummern, Adressen, Geburtsdaten | Bankgeheimnis, DSGVO |
| **Finanzielle Details** | Kontostände, Kreditbeträge, Konditionen einzelner Kunden | Bankgeheimnis |
| **Interne Strategien** | Fusionspläne, Übernahmen, vertrauliche Vorstandsbeschlüsse | Geschäftsgeheimnis |
| **Personaldaten** | Gehälter, Beurteilungen, Abmahnungen | DSGVO, Arbeitsrecht |
| **Zugangsdaten** | Passwörter, System-Zugänge, Bankleitzahlen mit Kontexten | IT-Sicherheit |

### Was Sie stattdessen tun

```
┌─────────────────────────────────────────────────────────────────┐
│              🛡️ Anonymisieren vor dem Prompten                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ❌ „Herr Schmidt, Konto 4711, hat 50.000€ Dispo beantragt"    │
│  ✅ „Kunde A hat einen Dispositionskredit im mittleren          │
│     fünfstelligen Bereich beantragt"                           │
│                                                                 │
│  ❌ „Filiale Soest macht 2,3 Mio Verlust im Kreditgeschäft"    │
│  ✅ „Eine unserer Filialen hat Verluste im Kreditgeschäft       │
│     verzeichnet"                                                │
│                                                                 │
│  ❌ „Vorstandsmitglied Müller will Filiale Werl schließen"      │
│  ✅ „Es wurde über eine mögliche Filialkonsolidierung           │
│     gesprochen"                                                 │
│                                                                 │
│  Faustregel: Wenn ein Journalist mit dem Text etwas             │
│  anfangen könnte → anonymisieren.                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Das Vier-Augen-Prinzip

KI-generierte Protokolle sind **Entwürfe**, keine fertigen Dokumente. Bevor Sie ein Protokoll weiterleiten:

1. **Fakten prüfen:** Stimmen Namen, Daten, Zahlen?
2. **Datenschutz prüfen:** Sind sensible Informationen geschwärzt?
3. **Vollständigkeit prüfen:** Fehlt eine wichtige Entscheidung?
4. **Ton prüfen:** Passt die Formulierung zum Anlass?

> **Das „Human-in-the-Loop-Prinzip":** Die KI fasst zusammen. Sie verantworten das Ergebnis. Immer. Keine Ausnahmen.

---

## Schritt 3: Meeting-Protokolle — Vom Transkript zum strukturierten Dokument

Jetzt wird es praktisch. Sie haben ein Meeting-Transkript (oder Notizen) und wollen daraus ein Protokoll. Hier sind zwei Varianten — wählen Sie je nach Bedarf.

### Prompt-Vorlage 1: Detailliertes Protokoll (für interne Dokumentation)

Diese Vorlage eignet sich für alle Meeting-Typen, bei denen Sie eine vollständige Dokumentation brauchen — Kreditausschuss, Filialleiter-Runde, Projektmeeting, Teammeeting.

**Wo tippe ich das ein?** Öffnen Sie Ihr KI-Tool (ChatGPT, Claude, Gemini), kopieren Sie den Prompt ins Eingabefeld, und fügen Sie das Transkript darunter ein. Bei langen Transkripten (mehr als 5 Seiten): Kein Problem — aktuelle KI-Modelle können auch 20-Seiten-Transkripte verarbeiten.

```
Du bist ein professioneller Meeting-Analyst für eine 
deutsche Genossenschaftsbank. Du erstellst aus Meeting-
Transkripten klare, strukturierte und umsetzbare Protokolle. 
Schreibe auf Deutsch, professionell aber verständlich.

KONTEXT:
Du erhältst ein Meeting-Transkript der Volksbank Hellweg eG. 
Das Transkript kann mehrere Sprecher enthalten, informell 
sein und verschiedene Themen behandeln.

AUFGABEN — Schritt für Schritt:

1. Lies das gesamte Transkript sorgfältig durch.

2. Erfasse die MEETING-GRUNDDATEN:
   - Titel/Thema des Meetings
   - Datum und Uhrzeit (falls erwähnt, sonst „nicht angegeben")
   - Dauer (falls erwähnt)
   - Teilnehmer mit Rollen (z.B. „Sarah Schmidt, 
     Teamleiterin Kundenservice")
   - Abwesende (falls erwähnt)
   - Vertraulichkeit: „Intern — Volksbank Hellweg eG"

3. Liste die HAUPTTHEMEN auf, die besprochen wurden.

4. Erstelle für jedes Thema eine ZUSAMMENFASSUNG 
   (3–5 Stichpunkte) und dokumentiere alle ENTSCHEIDUNGEN.

5. Sammle die KEY TAKEAWAYS — die 3-5 wichtigsten Punkte, 
   die man sich merken sollte.

6. Extrahiere alle AUFGABEN (Action Items) als Tabelle:
   - Was muss getan werden?
   - Wer ist verantwortlich?
   - Bis wann?
   - Priorität (Hoch/Mittel/Niedrig)

7. Liste FOLLOW-UPS — Themen fürs nächste Meeting.

8. Dokumentiere OFFENE FRAGEN — was muss noch geklärt werden?

9. Erfasse RISIKEN oder ABHÄNGIGKEITEN, falls erwähnt.

10. Notiere UNKLARHEITEN: Wenn etwas im Transkript unklar 
    war, markiere es mit Zeitstempel.

11. Falls ein nächstes Meeting erwähnt wurde: Datum und 
    vorgeschlagene Agenda notieren.

12. DATENSCHUTZ: Schwärze alle sensiblen Daten:
    - Kundennamen → „[Kunde A]"
    - Kontonummern → „[anonymisiert]"
    - Konkrete Beträge einzelner Kunden → „[Betrag]"
    - Erfinde NICHTS dazu — nur Informationen aus dem 
      Transkript verwenden

FORMATIERUNG:
- Datum: YYYY-MM-DD (oder „tbd")
- Namen: „Vorname Nachname (Rolle)"
- Bei fehlenden Infos: „unbekannt" oder „tbd"

AUSGABEFORMAT (Markdown):

### Meeting-Grunddaten
- Titel: …
- Datum/Uhrzeit: … – … (Dauer: …)
- Teilnehmer: …
- Abwesend: …
- Vertraulichkeit: Intern — Volksbank Hellweg eG

### Hauptthemen
- …

### Zusammenfassungen & Entscheidungen

**Thema 1: [Name]**
- Zusammenfassung: …
- **Entscheidungen:**

| Nr. | Entscheidung | Entscheider | Gilt ab | Betroffene |
|-----|-------------|-------------|---------|------------|
| 1   | …           | …           | …       | …          |

### Key Takeaways
- …

### Aufgaben (Action Items)

| Nr. | Aufgabe | Verantwortlich | Fällig | Priorität | Status |
|-----|---------|---------------|--------|-----------|--------|
| 1   | …       | …             | …      | …         | Neu    |

### Follow-ups (nächstes Meeting)
- …

### Offene Fragen
- …

### Risiken & Abhängigkeiten
- …

### Unklarheiten im Transkript
- [Zeitstempel] — unverständlich — möglicher Sprecher: …

### Nächstes Meeting
- Datum/Ziel: …
- Vorgeschlagene Agenda: …

---

Füge jetzt bitte das Meeting-Transkript hier ein:
```

### So wenden Sie den Prompt an — Schritt für Schritt

**Beispiel-Szenario:** Sie hatten ein 60-minütiges Kreditausschuss-Meeting in Teams. Die Aufzeichnung ist fertig.

**Schritt 1: Transkript exportieren**
- In Teams: Aufzeichnung öffnen → „Transkript herunterladen" → Textdatei speichern
- In Zoom: „Aufzeichnungen" → Meeting auswählen → „Transkript" herunterladen

**Schritt 2: Transkript anonymisieren** (WICHTIG!)
- Kundennamen ersetzen: „Herr Schneider" → „Kunde A"
- Kontonummern entfernen
- Konkrete Kreditbeträge einzelner Kunden verallgemeinern: „350.000€ Baufinanzierung" → „Baufinanzierung im mittleren sechsstelligen Bereich"

**Schritt 3: Prompt + Transkript in KI einfügen**
- Prompt kopieren → in ChatGPT/Claude/Gemini einfügen
- Transkript darunter einfügen
- Enter drücken — die KI generiert das Protokoll (10-30 Sekunden)

**Schritt 4: Ergebnis prüfen** (IMMER!)
- Stimmen die Namen und Rollen?
- Sind alle Entscheidungen erfasst?
- Sind die Action Items korrekt zugeordnet?
- Wurden alle sensiblen Daten geschwärzt?
- Hat die KI etwas *hinzugefügt*, das nicht im Transkript stand?

**Schritt 5: Finalisieren und verteilen**
- Letzte Korrekturen vornehmen
- Als PDF oder Word speichern
- An alle Teilnehmer senden

> **Praxis-Tipp:** Beim ersten Mal dauert der gesamte Prozess vielleicht 15-20 Minuten. Nach ein paar Durchläufen sind es 5-8 Minuten — statt 30-45 Minuten für ein manuelles Protokoll.

### Prompt-Vorlage für Notizen statt Transkript

Wenn Sie kein automatisches Transkript haben, sondern nur Ihre eigenen Stichpunkte:

```
Du bist ein professioneller Meeting-Analyst. Ich gebe dir 
meine handschriftlichen Notizen aus einem Meeting. 
Erstelle daraus ein strukturiertes Protokoll.

KONTEXT:
- Meeting-Typ: [z.B. Wöchentliches Teammeeting Privatkundenberatung]
- Datum: [z.B. 2026-02-26]
- Teilnehmer: [z.B. Thomas Bergmann (Teamleiter), 
  Sarah Weber, Klaus Richter, Sonja Bergmann]

WICHTIG:
- Ergänze NICHTS, was nicht in meinen Notizen steht
- Wenn etwas unklar ist, markiere es mit [PRÜFEN]
- Formuliere meine Stichpunkte in vollständige Sätze um,
  aber ändere nicht die Bedeutung

Meine Notizen:
[HIER NOTIZEN EINFÜGEN]
```

---

## Schritt 4: Management-Summary — Eine halbe Seite für die Chefetage

Nicht jeder braucht alle Details. Ihr Vorstand will wissen: Was wurde entschieden? Was muss ich tun? Was sind die Risiken? Fertig.

### Prompt-Vorlage 2: Kompakte Management-Summary

```
Du bist ein erfahrener Kommunikationsberater für den 
Vorstand einer Genossenschaftsbank.

AUFGABE: Erstelle eine kompakte Management-Summary aus 
dem folgenden Meeting-Transkript.

MEETING-TYP: [z.B. Kreditausschuss, Filialleiter-Runde, 
Projekt-Review, Strategiemeeting]

ZIELGRUPPE: [z.B. Vorstand, Bereichsleitung, Aufsichtsrat]

STRUKTUR:

**1. Executive Summary (2-3 Sätze)**
Was ist das wichtigste Ergebnis dieses Meetings?

**2. Entscheidungen & Beschlüsse**
- Format: „Entscheidung: [Was] | Begründung: [Warum] | 
  Entscheider: [Wer]"

**3. Aufgaben & Verantwortlichkeiten**

| Aufgabe | Verantwortlich | Deadline | Priorität |
|---------|---------------|----------|-----------|
| …       | …             | …        | …         |

**4. Risiken & Herausforderungen**
- Liste mit Dringlichkeit (Hoch/Mittel/Niedrig)

**5. Nächste Schritte**
- Was passiert als Nächstes?
- Wann ist das nächste Meeting?

FORMAT: Maximal 1 Seite (ca. 300-400 Wörter). 
Professionell, sachlich, auf den Punkt.

DATENSCHUTZ: 
- Kundendaten → „[anonymisiert]"
- Konkrete Beträge einzelner Kunden → allgemeine Kategorien
- Keine verbindlichen Rechtsaussagen

TRANSKRIPT:
[HIER EINFÜGEN]
```

### Wann welche Variante?

| Situation | Variante 1 (Detail) | Variante 2 (Summary) |
|---|---|---|
| Protokoll für alle Teilnehmer | ✅ | |
| Bericht an den Vorstand | | ✅ |
| Audit-relevante Dokumentation | ✅ | |
| Schneller Überblick für Kollegen, die nicht dabei waren | | ✅ |
| Grundlage für Follow-up-Meeting | ✅ | |
| Entscheidungsvorlage für Aufsichtsrat | | ✅ |

> **Volksbank-Analogie:** Variante 1 ist das vollständige Sitzungsprotokoll, das im Ordner landet. Variante 2 ist die gelbe Haftnotiz, die Ihr Vorstand auf dem Schreibtisch findet: „Drei Dinge, die Sie wissen müssen."

### Aus einem Meeting mehrere Versionen erstellen

Ein besonders wirkungsvoller Trick: Erstellen Sie zuerst das detaillierte Protokoll (Variante 1), und lassen Sie die KI daraus verschiedene Versionen ableiten.

```
Erstelle aus dem folgenden Protokoll eine kompakte 
1-Seiten-Version für den Vorstand.

Fokus: Entscheidungen, Budget-Auswirkungen, Risiken.
Weglassen: Detaillierte Diskussionen, technische Details.
Ton: Sachlich, entscheidungsorientiert.

Protokoll:
[HIER DAS DETAILLIERTE PROTOKOLL EINFÜGEN]
```

```
Erstelle aus dem folgenden Protokoll eine kurze E-Mail 
an alle Teilnehmer mit:
- Den 3 wichtigsten Ergebnissen
- Allen Action Items als Checkliste
- Dem Datum des nächsten Meetings

Ton: Freundlich, motivierend, kurz.
Max. 150 Wörter.

Protokoll:
[HIER EINFÜGEN]
```

---

## Schritt 5: Dokumente zusammenfassen — Rundschreiben, BaFin-Texte, Verbandsberichte

Neben Meetings gibt es eine zweite große Zusammenfassungs-Aufgabe im Bankalltag: lange Dokumente lesen und verdichten. BVR-Rundschreiben, BaFin-Mitteilungen, Prüfungsberichte, Verbandsinformationen — Texte, die gelesen werden *müssen*, aber selten gelesen werden *wollen*.

### Prompt-Vorlage 3: Dokument-Zusammenfassung (Zwei-Stufen-Format)

Diese Vorlage liefert Ihnen zwei Versionen: eine ausführliche und einen One-Pager. So können Sie selbst die Details lesen und dem Vorstand den One-Pager weiterleiten.

```
Du bist ein erfahrener Fachanalyst für die Verdichtung 
regulatorischer und fachlicher Dokumente im Bankwesen.

AUFGABE: Fasse das folgende Dokument in zwei Versionen 
zusammen.

BRANCHE: Genossenschaftliches Bankwesen
ZIELGRUPPE: [z.B. Vorstand, Compliance, Fachbereich Kredit]
SPRACHE: Professionell, sachlich, allgemeinverständlich

VERSION 1 — AUSFÜHRLICHE ZUSAMMENFASSUNG:
- Klar strukturiert, logisch gegliedert
- Hauptaussagen, Argumente, Entscheidungen herausarbeiten
- Fachbegriffe und Abkürzungen erklären
- To-Dos und Handlungsbedarfe hervorheben
- Auswirkungen auf die Volksbank Hellweg benennen

VERSION 2 — ONE-PAGER (max. 1 DIN-A4-Seite):
- Überschrift + Datum + Quelle
- 3-5 Kernpunkte in kurzen Sätzen
- To-Dos mit Frist und Verantwortlichkeit
- Max. 250 Wörter

BESONDERER FOKUS:
- [z.B. „rechtliche Implikationen für unser Kreditgeschäft"]
- [z.B. „Was müssen wir bis wann umsetzen?"]

FORMAT:

## 📑 AUSFÜHRLICHE ZUSAMMENFASSUNG

📌 **Titel:** [Originaltitel]
📅 **Datum:** [Falls relevant]
📁 **Quelle:** [z.B. BVR, BaFin, Prüfungsverband]

### Kerninhalte
- …

### Wichtige Details & Erläuterungen
- …

### Auswirkungen auf die Volksbank Hellweg
- …

### To-Dos & Handlungsbedarf

| Nr. | Aufgabe | Frist | Verantwortlich |
|-----|---------|-------|---------------|
| 1   | …       | …     | …             |

---

## 📋 ONE-PAGER

📌 **[Kurztitel]**
📅 **[Datum]**

**Kurz & Knapp:**
- …

**✅ To-Dos:**
- [Aufgabe 1] — [Frist] — [Verantwortlich]
- [Aufgabe 2] — [Frist] — [Verantwortlich]

---

DOKUMENT:
[HIER TEXT ODER DATEI EINFÜGEN]
```

### Prompt-Vorlage 4: Vorstandsvorlage im McKinsey-Stil

Wenn ein Dokument direkt für den Vorstand oder Aufsichtsrat aufbereitet werden soll — knapp, faktenbasiert, entscheidungsorientiert:

```
Du bist ein Strategieberater, der Dokumente für die 
Vorstandsebene einer Genossenschaftsbank aufbereitet.

AUFGABE: Erstelle eine Management-Zusammenfassung im 
McKinsey-Stil aus dem folgenden Dokument.

STRUKTUR:

### 1️⃣ Executive Takeaway
2-3 Sätze mit der zentralen Kernaussage und strategischen 
Empfehlung.

### 2️⃣ Kontext
Kurzbeschreibung: Thema, Ziel, Zweck des Dokuments.

### 3️⃣ Zentrale Erkenntnisse
Maximal 5 Stichpunkte — nur Fakten, Analysen und Zahlen.

### 4️⃣ Strategische und operative Implikationen
Was ist für Vorstand und Geschäftsleitung 
entscheidungsrelevant? Was bedeutet das konkret für 
die Volksbank Hellweg?

### 5️⃣ Empfohlene nächste Schritte
3-5 priorisierte Maßnahmen.

STILREGELN:
- Keine Füllwörter, keine Floskeln
- Jeder Satz muss Information transportieren
- Zahlen und Fakten statt Meinungen
- Klare Handlungsempfehlungen
- Max. 400 Wörter gesamt

DOKUMENT:
[HIER EINFÜGEN]
```

### Praxis-Beispiel: BaFin-Orientierungshilfe zusammenfassen

**Szenario:** Die BaFin hat im Dezember 2025 eine neue „Orientierungshilfe zu IKT-Risiken beim Einsatz von KI" veröffentlicht. 30 Seiten. Ihr Compliance-Beauftragter bittet Sie, eine Zusammenfassung für den Vorstand zu erstellen.

**Sie nutzen Prompt-Vorlage 4 mit dem Zusatz:**
```
BESONDERER FOKUS:
- Was müssen Genossenschaftsbanken konkret tun?
- Welche Fristen gibt es?
- Welche Risiken drohen bei Nicht-Einhaltung?
- Bezug zu DORA (Digital Operational Resilience Act)
```

**Die KI liefert z.B.:**

> ### 1️⃣ Executive Takeaway
> Die BaFin stuft KI-Systeme ab sofort als IKT-Assets unter DORA ein. Jede Bank, die KI nutzt — auch „nur" ChatGPT für E-Mails — muss dies in ihr IKT-Risikomanagement aufnehmen und dokumentieren. Handlungsbedarf besteht sofort.
>
> ### 2️⃣ Kontext
> Die Orientierungshilfe vom 18.12.2025 konkretisiert, wie Finanzunternehmen die DORA-Anforderungen auf KI-Anwendungen übertragen sollen. Sie ersetzt keine bestehenden Rundschreiben, sondern ergänzt sie um den KI-Aspekt.
>
> [...]

> **Volksbank-Analogie:** Stellen Sie sich vor, Ihr Compliance-Beauftragter müsste diese 30 Seiten selbst lesen, zusammenfassen und eine Vorstandsvorlage schreiben. Das dauert einen halben Tag. Mit dem richtigen Prompt sind es 20 Minuten — inklusive Qualitätskontrolle.

---

## Schritt 6: Prompt-Templates für wiederkehrende Meeting-Typen

Wenn Sie regelmäßig ähnliche Meetings haben — und das haben Sie als Bankmitarbeiter definitiv —, lohnt es sich, **eigene Prompt-Templates** zu erstellen. Einmal aufsetzen, immer wiederverwenden.

### Template: Kreditausschuss

```
Du erstellst ein Protokoll für den Kreditausschuss der 
Volksbank Hellweg eG.

FESTE STRUKTUR:
1. Kreditentscheidungen (Genehmigung/Ablehnung/Vertagung)
   - Kreditart, Volumen (anonymisiert als Kategorie), 
     Laufzeit, Sicherheiten
   - Abstimmungsergebnis
2. Risikobetrachtung
   - Auffällige Engagements (anonymisiert)
   - Risikoklassen-Veränderungen
3. Regulatorische Updates
   - MaRisk-relevante Änderungen
   - BaFin-Hinweise
4. Offene Punkte und Nachträge
5. Action Items mit Verantwortlichen und Fristen

DATENSCHUTZ (KRITISCH):
- KEINE Kundennamen — nur „Engagement A", „Kreditnehmer B"
- KEINE konkreten Beträge — nur Kategorien 
  (z.B. „kleiner sechsstelliger Bereich")
- KEINE Sicherheiten-Details, die Rückschlüsse auf 
  den Kunden erlauben

Transkript:
[HIER EINFÜGEN]
```

### Template: Filialleiter-Runde

```
Du erstellst ein Protokoll für die monatliche 
Filialleiter-Runde der Volksbank Hellweg eG.

FESTE STRUKTUR:
1. Geschäftsentwicklung (Trends, keine absoluten Zahlen)
2. Personalthemen (anonymisiert)
3. Vertriebsthemen (Kampagnen, Aktionen, Cross-Selling)
4. Kundenrückmeldungen (anonymisiert, Muster statt Einzelfälle)
5. Organisatorisches (IT, Umbau, Öffnungszeiten)
6. Best Practices (was funktioniert in welcher Filiale?)
7. Action Items

DATENSCHUTZ:
- Kundennamen → entfernen
- Mitarbeiternamen in Feedbacks → anonymisieren
- Filialkennzahlen → nur Trends und Richtungen

Transkript:
[HIER EINFÜGEN]
```

### Template: Wöchentliches Teammeeting

```
Du erstellst ein Protokoll für das wöchentliche Teammeeting 
im Bereich [z.B. Privatkundenberatung] der Volksbank 
Hellweg eG.

FESTE STRUKTUR:
1. Rückblick letzte Woche (Highlights, Herausforderungen)
2. Kundenfeedback (anonymisiert, Muster und Trends)
3. Prozessverbesserungen und Best Practices
4. Schulungsbedarfe
5. Ausblick nächste Woche
6. Action Items (mit Owner und Deadline)

STILREGELN:
- Kurz und knapp (max. 1,5 Seiten)
- Positiv-konstruktiver Ton
- Kundenfeedback nur in anonymisierter, aggregierter Form

Transkript:
[HIER EINFÜGEN]
```

> **Praxis-Tipp:** Speichern Sie diese Templates in OneNote, einer Textdatei oder als „Custom Instructions" in ChatGPT. In Tutorial 01-08 lernen Sie, wie Sie daraus einen eigenen Custom GPT bauen, der automatisch das richtige Template wählt.

---

## Schritt 7: Erweiterte Techniken — Follow-up-Aktionen aus Protokollen ableiten

Das Protokoll ist fertig. Aber die eigentliche Arbeit beginnt jetzt: Aufgaben verteilen, Erinnerungen setzen, das nächste Meeting vorbereiten. Auch hier kann die KI helfen.

### Aus dem Protokoll eine Reminder-E-Mail generieren

```
Erstelle aus den Action Items dieses Protokolls eine 
freundliche E-Mail an das Team.

INHALT:
- Kurze Zusammenfassung der wichtigsten Ergebnisse (3 Sätze)
- Action Items als Checkliste mit Deadlines
- Termin des nächsten Meetings
- Hinweis: „Bitte gebt Bescheid, falls eine Deadline 
  nicht haltbar ist"

TON: Motivierend, kollegial, kurz.
MAX. 150 Wörter.

Protokoll:
[HIER EINFÜGEN]
```

### Aus dem Protokoll eine Vorstandsfolie erstellen

```
Erstelle aus diesem Protokoll den Text für eine kompakte 
PowerPoint-Folie:

- Folientitel: [Meeting-Name + Datum]
- Top-3-Ergebnisse (je max. 15 Wörter)
- Top-3-Risiken (je max. 15 Wörter)
- Nächste Schritte (3 Punkte)

FORMAT: Stichpunkte, maximal 50 Wörter pro Abschnitt.
Keine ganzen Sätze — Folie, nicht Aufsatz.

Protokoll:
[HIER EINFÜGEN]
```

### Checkliste fürs Follow-up-Meeting

```
Erstelle eine Checkliste für das nächste Meeting, 
basierend auf den offenen Punkten und Aufgaben aus 
diesem Protokoll.

FORMAT:
- [ ] Punkt 1 (Verantwortlich: Name — Status erfragen)
- [ ] Punkt 2 ...

Sortiert nach Priorität (Hoch → Niedrig).

Protokoll:
[HIER EINFÜGEN]
```

---

## Schritt 8: Der Reflexions-Prompt — Wenn die Zusammenfassung wirklich gut sein muss

Für besonders wichtige Dokumente — Vorstandsvorlagen, Aufsichtsrats-Unterlagen, strategische Analysen — gibt es einen Trick, der die Qualität der KI-Ausgabe deutlich erhöht: Sie bitten die KI, *bevor* sie zusammenfasst, ihren Denkprozess offenzulegen.

```
Bevor du mir deine Zusammenfassung gibst:

1. Erkläre mir deine Annahmen — was hältst du für die 
   Kernbotschaft?
2. Beschreibe deinen Denkprozess — wie gehst du beim 
   Zusammenfassen vor?
3. Nenne mögliche Risiken — was könnte ich bei einer 
   Zusammenfassung übersehen?
4. Was würde deine Zusammenfassung ändern, wenn das 
   Dokument an [Vorstand / Aufsichtsrat / BaFin-Prüfer] 
   gerichtet wäre?

Gib mir danach deine Zusammenfassung mit einer 
Einschätzung deines Vertrauensniveaus (Hoch/Mittel/Niedrig).
```

**Warum funktioniert das?** Weil die KI gezwungen wird, *nachzudenken* statt automatisch loszulegen. Sie macht ihre Interpretation transparent — und Sie können korrigieren, bevor der Text steht.

> **Volksbank-Analogie:** Das ist wie wenn Sie Ihrem Mitarbeiter sagen: „Bevor du mir die Vorlage schreibst — erkläre mir erstmal in drei Sätzen, was du als die Kernbotschaft verstanden hast." Wenn die Kernbotschaft falsch verstanden wurde, sparen Sie sich den kompletten Entwurf.

---

## Was KI bei Zusammenfassungen (noch) nicht kann

| Limitation | Warum problematisch | Workaround |
|---|---|---|
| **Zwischentöne und Stimmungen** | KI versteht nicht, dass „interessanter Vorschlag" in einem Vorstandsmeeting manchmal „das werden wir nie machen" bedeutet. Ironie, Zögern und diplomatische Ablehnung gehen verloren | Stimmungen und implizite Entscheidungen manuell ergänzen. KI liefert die Fakten, Sie liefern die Interpretation |
| **Priorisierung nach Wichtigkeit** | KI gewichtet alle Themen gleich, wenn sie nicht anders angewiesen wird. Ein kurzer Satz über eine Millionen-Entscheidung steht neben einer 10-Minuten-Diskussion über den Kaffeeautomaten | Im Prompt explizit angeben, worauf der Fokus liegen soll. Oder nach der Generierung: „Sortiere die Themen nach strategischer Relevanz, nicht nach Reihenfolge im Transkript" |
| **Fehlende Kontextinformationen** | KI weiß nicht, dass „das gleiche Problem wie letztes Mal" sich auf den Server-Ausfall vom Januar bezieht. Sie kennt die Geschichte nicht | Kontext im Prompt mitgeben: „Hintergrund: Im Januar gab es einen 4-stündigen Server-Ausfall, der das Online-Banking lahmgelegt hat" |
| **Fehlende Sprecher-Erkennung** | Viele Transkripte haben keine oder falsche Sprecher-Labels. Die KI kann nicht wissen, wer was gesagt hat, wenn es nicht im Text steht | Sprecher manuell nachpflegen oder im Prompt die Teilnehmer und ihre typischen Themen nennen: „Max Müller ist der IT-Leiter und spricht über technische Themen" |
| **Rechtlich verbindliche Formulierungen** | KI kann plausibel klingende Beschlüsse formulieren, die rechtlich nicht dem entsprechen, was tatsächlich entschieden wurde | Entscheidungen und Beschlüsse immer von den Entscheidern gegenlesen lassen. KI-Protokoll ≠ Vorstandsbeschluss |
| **Vertraulichkeitsgrade** | KI unterscheidet nicht zwischen „darf ins Intranet" und „nur für den Vorstand". Sie behandelt alles gleich | Vertraulichkeitsstufe im Prompt angeben. Für kritische Themen: Getrennte Zusammenfassungen erstellen |

> **Die Kernregel:** KI ist brillant im *Extrahieren* von Informationen. Sie ist schwach im *Bewerten* von Informationen. Was wichtig ist und was nicht — das wissen Sie. Nicht die KI.

---

## Kosten-Vergleich: KI vs. Manuell

Was spart der KI-Einsatz bei Zusammenfassungen konkret? Eine Schätzung basierend auf typischen Bankaufgaben (interner Stundensatz: 45 €):

| Aufgabe | Manuell | Mit KI | Ersparnis | €-Wert |
|---|---|---|---|---|
| Meeting-Protokoll (60 Min Meeting) | 30-45 Min | 8-12 Min | ~70% | ~14-25 € |
| Management-Summary | 20-30 Min | 5-8 Min | ~70% | ~11-17 € |
| BaFin-Rundschreiben zusammenfassen (20 Seiten) | 60-90 Min | 10-15 Min | ~85% | ~34-56 € |
| BVR-Rundschreiben One-Pager | 30-45 Min | 5-10 Min | ~80% | ~15-26 € |
| Vorstandsvorlage aus Dokument | 45-60 Min | 12-18 Min | ~70% | ~20-32 € |
| Wöchentliches Teammeeting (4× pro Monat) | 2-3 Std/Monat | 30-45 Min/Monat | ~75% | ~56-101 €/Monat |

**Token-Kosten der KI-Nutzung:**

| Aufgabe | Tokens (ca.) | Kosten GPT-4o | Kosten Claude Sonnet |
|---|---|---|---|
| Meeting-Protokoll (60 Min) | ~5.000-15.000 | 0,03-0,10 € | 0,03-0,10 € |
| Management-Summary | ~3.000-8.000 | 0,02-0,05 € | 0,02-0,05 € |
| Dokument-Zusammenfassung (20 Seiten) | ~10.000-30.000 | 0,06-0,20 € | 0,06-0,20 € |
| McKinsey-Vorlage | ~5.000-12.000 | 0,03-0,08 € | 0,03-0,08 € |

> **Fazit:** Die KI-Kosten bewegen sich im Cent-Bereich. Die Zeitersparnis liegt bei 70-85%. Bei einem Team von 10 Mitarbeitern, die jeweils 2 Protokolle pro Woche schreiben, spart die KI **40-60 Stunden pro Monat** — das ist eine volle Arbeitswoche.

---

## Modell-Empfehlungen für Zusammenfassungen (Stand: Februar 2026)

| Modell | Stärke bei Zusammenfassungen | Schwäche | Am besten für |
|---|---|---|---|
| **ChatGPT (GPT-5.2)** | Schnell, vielseitig, gute Strukturierung, verarbeitet lange Texte | Neigt gelegentlich dazu, Details hinzuzufügen | Schnelle Protokolle, Dokument-Summaries |
| **Claude (Opus 4.6 / Sonnet 4)** | Sehr genau, fügt nichts hinzu, folgt Anweisungen präzise, starke lange Kontexte (bis 200K Tokens) | Manchmal zu ausführlich, wenn nicht anders angewiesen | Komplexe Dokumente, Compliance-relevante Texte, lange Transkripte |
| **Gemini (2.5 Pro)** | Sehr lange Kontextfenster (1M+ Tokens), gute Zusammenfassungen, kostenfreie Basisversion | Weniger präzise bei Detailextraktionen | Sehr lange Dokumente, schnelle Erstübersicht |

> **Tipp:** Für Meeting-Protokolle genügen GPT-4o oder Claude Sonnet (schnell, günstig, gut genug). Für 30-Seiten-BaFin-Dokumente ist Claude Opus oder Gemini Pro die bessere Wahl — wegen des größeren Kontextfensters.

---

## Entscheidungsbaum: Welcher Prompt für welche Situation?

```
┌─────────────────────────────────────────────────────────────────┐
│          🗺️ Welchen Zusammenfassungs-Prompt brauche ich?        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Was haben Sie?                                                │
│                                                                 │
│  ├── 🎤 MEETING-TRANSKRIPT                                      │
│  │   ├── Für alle Teilnehmer? → Detailliertes Protokoll        │
│  │   │                          (Schritt 3, Vorlage 1)         │
│  │   ├── Für den Vorstand?   → Management-Summary              │
│  │   │                          (Schritt 4, Vorlage 2)         │
│  │   └── Regelmäßiges Meeting? → Eigenes Template              │
│  │                               (Schritt 6)                   │
│  │                                                              │
│  ├── 📋 EIGENE NOTIZEN                                          │
│  │   └── Notizen → Protokoll (Schritt 3, Notizen-Vorlage)     │
│  │                                                              │
│  ├── 📄 DOKUMENT (Rundschreiben, BaFin, etc.)                  │
│  │   ├── Für mich + Vorstand? → Zwei-Stufen-Format            │
│  │   │                          (Schritt 5, Vorlage 3)         │
│  │   └── Nur Vorstandsvorlage? → McKinsey-Stil                │
│  │                               (Schritt 5, Vorlage 4)        │
│  │                                                              │
│  └── 📊 BESONDERS WICHTIG                                       │
│      └── Erst Reflexions-Prompt (Schritt 8),                   │
│          dann Zusammenfassung                                   │
│                                                                 │
│  Nach JEDEM Protokoll: Vier-Augen-Prinzip (Schritt 2)         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Pipeline-Zusammenfassung: Vom Rohmaterial zum fertigen Protokoll

```
┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
│ Quelle   │    │ Bereinigen│    │ KI-Prompt │    │ Prüfen   │    │ Verteilen│
│          │    │          │    │          │    │          │    │          │
│ Transkript│ → │ Anonymi- │ → │ Template │ → │ Vier-    │ → │ E-Mail,  │
│ Notizen  │    │ sieren   │    │ wählen + │    │ Augen-   │    │ Ablage,  │
│ Dokument │    │ Sensible │    │ einfügen │    │ Prinzip  │    │ Follow-up│
│          │    │ Daten    │    │          │    │          │    │          │
│          │    │ entfernen│    │ KI       │    │ Fakten ✓ │    │ Optional:│
│          │    │          │    │ generiert│    │ Daten  ✓ │    │ Reminder │
│          │    │          │    │ Protokoll│    │ Voll-  ✓ │    │ Folie    │
│          │    │          │    │          │    │ ständig  │    │ Checkliste│
└──────────┘    └──────────┘    └──────────┘    └──────────┘    └──────────┘
     1               2               3               4               5
  (1 Min)         (3-5 Min)       (1 Min)         (3-5 Min)       (2 Min)
                                                              ─────────────
                                                              Gesamt: ~12 Min
                                                              statt 30-45 Min
```

---

## Das Wichtigste auf einen Blick

| Aufgabe | Prompt-Ansatz | Zeitersparnis | Wichtigster Tipp |
|---|---|---|---|
| **Meeting-Protokoll** | Detaillierte Vorlage mit fester Struktur | 70% | Transkript vorher anonymisieren |
| **Management-Summary** | Kompakte 1-Seite mit Entscheidungen + Action Items | 70% | Executive Summary = 2-3 Sätze, nicht mehr |
| **Dokument-Zusammenfassung** | Zwei-Stufen-Format (Detail + One-Pager) | 80-85% | Zielgruppe und Fokus im Prompt angeben |
| **Vorstandsvorlage** | McKinsey-Stil mit 5 festen Abschnitten | 70% | „Empfohlene nächste Schritte" nie vergessen |
| **Wiederkehrende Meetings** | Eigene Templates erstellen und wiederverwenden | 80%+ | Template einmal gut aufsetzen, dann immer nutzen |
| **Follow-up-Aktionen** | Aus Protokoll ableiten (E-Mail, Folie, Checkliste) | 85% | Action Items als Checkliste — nicht als Fließtext |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---|---|
| Prompt-Vorlage mit fester Struktur | Nutzt Delimiter und Formatvorgaben (Tutorial 01-04, Schritt 7): Klare Markdown-Struktur als Qualitätsanker |
| „Erfinde NICHTS dazu" | Nutzt Anti-Halluzinations-Strategien (Tutorial 01-03): Explizite Anweisung gegen Hinzudichten |
| Reflexions-Prompt (Schritt 8) | Nutzt Chain-of-Thought (Tutorial 01-04, Schritt 4): KI denkt erst nach, dann schreibt sie |
| Meeting-Templates mit Rollen | Nutzt System Prompt-Prinzip (Tutorial 01-04, Schritt 2): Rollenanweisung als dauerhaftes Fundament |
| Anonymisierung vor dem Prompten | Vertieft Datenschutz-Regeln aus Tutorial 01-05 (Compliance-Hinweis): Hier systematischer und mit konkreten Beispielen |
| Zwei-Stufen-Zusammenfassung | Nutzt das Prinzip „Für die Zielgruppe schreiben" (Tutorial 01-05, Schritt 6): Detail-Version für Sie, One-Pager für den Vorstand |
| Pipeline-Diagramm | Zeigt den End-to-End-Prozess wie die 4-Schritt-E-Mail-Kette (Tutorial 01-05, Schritt 2): Klarer Ablauf statt einzelner Prompt |

---

## ⚠️ Compliance-Hinweis: Besonderheiten bei Protokollen

Protokolle haben eine *andere* Compliance-Dimension als E-Mails oder Kundenanschreiben. Warum? Weil sie als **Dokumentation gelten** — und damit unter Umständen rechtlich relevant sind.

| Regel | Warum | Praxis-Tipp |
|---|---|---|
| **Aufzeichnung nur mit Einwilligung** | Datenschutz, Persönlichkeitsrecht | Vor dem Meeting: „Ich zeichne auf für das Protokoll — ist das für alle OK?" |
| **Transkripte nach Protokollerstellung löschen** | Datensparsamkeit (DSGVO Art. 5) | Transkript nur aufbewahren, bis das Protokoll freigegeben ist |
| **Keine Kundendaten in externe KI-Tools** | Bankgeheimnis, DSGVO | Immer anonymisieren. Im Zweifel: manuell protokollieren |
| **Vorstandsprotokolle = Urkunden** | Handelsrecht (§ 37 GenG) | KI-Protokoll ist *Entwurf*. Formelles Protokoll wird vom Schriftführer verantwortet |
| **BaFin: KI unter DORA** | IKT-Risikomanagement | Wenn Sie KI für Protokolle nutzen, dokumentieren Sie das in Ihrem IKT-Verzeichnis |
| **Aufbewahrungsfristen beachten** | MaRisk, HandelsR | Protokolle von Gremien: 10 Jahre. Protokolle von Teammeetings: klären Sie mit Compliance |

> **Kurzregel:** KI für Protokolle nutzen = ja. KI-Protokoll ungeprüft als offizielle Urkunde ablegen = nein.

---

## 🚀 Starten Sie hier — Ihr erster Schritt am Montag

Acht Prompt-Vorlagen sind viel auf einmal. Deshalb hier die **eine Sache**, die Sie sofort mitnehmen:

> **Nehmen Sie Ihr nächstes Teammeeting. Lassen Sie die Aufzeichnung laufen (mit Einwilligung). Exportieren Sie das Transkript. Anonymisieren Sie es (2 Minuten). Nutzen Sie Prompt-Vorlage 1 aus Schritt 3. Prüfen Sie das Ergebnis (3 Minuten). Fertig.**

Wenn Sie das einmal gemacht haben, werden Sie es nie wieder anders machen wollen. Der Unterschied zwischen 45 Minuten Protokoll-Schreiben und 10 Minuten KI + Prüfung ist so groß, dass sich die Frage „Soll ich das nutzen?" von selbst beantwortet.

**Die Reihenfolge zum Reinwachsen:**
1. 🥇 **Woche 1:** Teammeeting-Protokoll mit KI erstellen — einmal durchspielen
2. 🥈 **Woche 2:** Eigenes Meeting-Template aufsetzen (Schritt 6) — für den häufigsten Meeting-Typ
3. 🥉 **Woche 3:** Ein Rundschreiben mit dem Zwei-Stufen-Format zusammenfassen (Schritt 5)
4. 🏅 **Danach:** McKinsey-Vorlage für die nächste Vorstandsvorlage testen (Schritt 5)

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Ihr erstes KI-Protokoll

**Aufgabe:** Verwandeln Sie diese Stichpunkte in ein strukturiertes Protokoll:

```
Teammeeting Privatkundenberatung, 25.02.2026, 10:00-11:00
Teilnehmer: Thomas (Teamleiter), Sarah, Klaus, Sonja

- Baufinanzierung läuft gut, 15% mehr Anträge als Vorjahr
- Problem: Wartezeiten bei Kreditentscheidungen zu lang
  → Thomas spricht mit Marktfolge
- Neues Online-Tool für Konditionsvergleich kommt im März
  → Klaus macht Schulung für alle, Termin nächste Woche
- Kundin hat sich beschwert über lange Wartezeit am Telefon
  → Sarah prüft ob KSC-Zeiten angepasst werden können
- Nächstes Meeting: 04.03., gleiche Zeit
```

**Ihre Aufgabe:**
1. Kopieren Sie die Notizen-Vorlage aus Schritt 3
2. Fügen Sie die Stichpunkte als „Meine Notizen" ein
3. Lassen Sie die KI ein Protokoll generieren
4. Prüfen Sie: Hat die KI etwas *hinzugefügt*, das nicht in den Notizen stand?
5. Prüfen Sie: Sind alle Action Items korrekt zugeordnet?

**Erwartetes Ergebnis:** 3 Action Items (Thomas → Marktfolge, Klaus → Schulung, Sarah → KSC-Zeiten), klare Deadlines, keine erfundenen Details.

### Hands-on 2: Zwei Zusammenfassungen — ein Dokument

**Aufgabe:** Fassen Sie diesen fiktiven Textabschnitt zusammen — einmal als detaillierte Zusammenfassung, einmal als One-Pager:

```
BVR-Rundschreiben Nr. 12/2026: Neue Anforderungen an die 
Kreditvergabe bei Wohnimmobilien

Ab dem 01.07.2026 gelten verschärfte Anforderungen an die 
Kreditwürdigkeitsprüfung bei Wohnimmobilienfinanzierungen. 
Die wesentlichen Änderungen:

1. Stresstest-Zinssatz: Der kalkulatorische Zinssatz für 
   die Tragfähigkeitsberechnung steigt von 2,5% auf 3,5%.

2. Eigenkapitalquote: Die empfohlene Mindesteigenkapitalquote 
   steigt von 10% auf 15% des Beleihungswerts.

3. Dokumentationspflicht: Jede Abweichung von den 
   Standardkriterien muss einzeln begründet und vom 
   Marktfolge-Vorstand genehmigt werden.

4. Schulungspflicht: Alle Baufinanzierungsberater müssen 
   bis 30.06.2026 eine Pflichtschulung absolvieren.

Hintergrund: Die Änderungen folgen der EBA-Leitlinie 
2025/15 zur Stärkung der Kreditvergabestandards in der EU.
```

**Ihre Aufgabe:**
1. Nutzen Sie Prompt-Vorlage 3 (Zwei-Stufen-Format) aus Schritt 5
2. Setzen Sie als Zielgruppe: „Vorstand + Baufinanzierungsberater"
3. Vergleichen Sie: Enthält der One-Pager alle To-Dos mit Fristen?
4. Bonus: Lassen Sie die KI danach den Reflexions-Prompt (Schritt 8) anwenden — was sagt sie über ihre eigenen Annahmen?

### Hands-on 3: Modellvergleich — Wer fasst besser zusammen?

**Aufgabe:** Geben Sie **zwei verschiedenen KI-Modellen** (z.B. ChatGPT + Claude, oder ChatGPT + Gemini) denselben Prompt:

```
Erstelle eine Management-Summary im McKinsey-Stil aus 
diesem Text:

„Die Volksbank Hellweg plant die Einführung eines neuen 
CRM-Systems. Aktuell nutzen die 120 Berater drei 
verschiedene Excel-Listen, ein Notizbuch-System und das 
Kernbanksystem parallel. 40% der Kundenkontakte werden 
nicht dokumentiert. Die Implementierung soll 18 Monate 
dauern und 350.000€ kosten. Erwartet wird eine Steigerung 
der Cross-Selling-Quote um 25% und eine Reduktion der 
Dokumentationszeit um 60%. Drei Anbieter wurden evaluiert. 
Der Vorstand entscheidet im April."

Max. 200 Wörter. Fokus: Entscheidungsrelevanz für 
den Vorstand.
```

**Vergleichen Sie:**
- Welches Modell strukturiert besser?
- Welches bleibt näher an den Fakten (erfindet nichts dazu)?
- Welches liefert klarere Handlungsempfehlungen?
- Bei welchem müssen Sie mehr nachbearbeiten?

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **Transkript** | Verschriftlichung eines gesprochenen Gesprächs oder Meetings. Kann automatisch (durch Software) oder manuell (durch Mitschreiben) erstellt werden |
| **Meeting-Protokoll** | Strukturierte Dokumentation eines Meetings mit Themen, Entscheidungen, Aufgaben und Verantwortlichkeiten. Offizieller als ein Transkript |
| **Management-Summary** | Kurze, verdichtete Zusammenfassung für Führungskräfte. Fokus auf Entscheidungen, Risiken und Handlungsbedarf. Typischerweise max. 1 Seite |
| **Executive Takeaway** | Die zentrale Kernaussage in 2-3 Sätzen. Beantwortet die Frage: „Was ist das Wichtigste, das ich wissen muss?" |
| **One-Pager** | Zusammenfassung auf maximal einer DIN-A4-Seite. Zwingt zur Priorisierung: Was ist wirklich wichtig, was kann weg? |
| **McKinsey-Stil** | Präsentations- und Zusammenfassungsstil, der auf Fakten, Daten und klare Empfehlungen setzt. Keine Füllwörter, keine Prosa — nur das, was zählt |
| **Action Item** | Konkrete Aufgabe aus einem Meeting mit klarem Verantwortlichen, Deadline und messbarem Ergebnis. „Klaus klärt bis Freitag" statt „das sollten wir mal besprechen" |
| **Follow-up** | Thema oder Aufgabe, die im nächsten Meeting erneut besprochen werden soll. Oft am Ende des Protokolls als Liste |
| **Decision Log** | Dokumentation aller Entscheidungen mit Entscheider, Datum und Begründung. Wichtig für Revisionssicherheit |
| **Key Takeaway** | Die 3-5 wichtigsten Erkenntnisse eines Meetings oder Dokuments. Beantwortet: „Was muss ich mir merken?" |
| **Human-in-the-Loop** | Prinzip, dass bei KI-generierten Ergebnissen immer ein Mensch die finale Verantwortung trägt und das Ergebnis prüft |
| **Anonymisierung** | Entfernung oder Ersetzung von personenbezogenen Daten (Namen, Kontonummern, Beträge) durch Platzhalter oder allgemeine Kategorien |
| **DORA** | Digital Operational Resilience Act — EU-Verordnung zur digitalen Widerstandsfähigkeit im Finanzsektor. Seit 2025 müssen Banken auch KI-Systeme als IKT-Assets behandeln und dokumentieren |
| **IKT-Risiko** | Risiko durch Informations- und Kommunikationstechnologie. Seit der BaFin-Orientierungshilfe 12/2025 fallen auch KI-Tools darunter |
| **MaRisk** | Mindestanforderungen an das Risikomanagement — BaFin-Vorgaben für Banken. Betreffen auch die Dokumentation von Meetings und Entscheidungen |
| **BVR** | Bundesverband der Deutschen Volksbanken und Raiffeisenbanken — gibt Rundschreiben und Richtlinien für Genossenschaftsbanken heraus |
| **GenG** | Genossenschaftsgesetz — regelt u.a. die Protokollpflichten bei Vorstandssitzungen (§ 37 GenG) |
| **Kontextfenster** | Maximale Textmenge, die ein KI-Modell gleichzeitig verarbeiten kann. GPT-5.2: ~128K Tokens. Claude Opus: ~200K Tokens. Gemini Pro: 1M+ Tokens. Relevant bei langen Transkripten |
| **Token** | Kleinste Verarbeitungseinheit der KI — ungefähr ¾ eines Wortes im Deutschen. 1.000 Tokens ≈ 600-700 deutsche Wörter (vgl. Tutorial 01-01) |

---


