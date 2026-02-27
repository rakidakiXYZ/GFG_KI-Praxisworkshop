# Komplexe Prompt-Architekturen

**Markdown, XML und JSON kombinieren — wie Sie aus drei Werkzeugen ein Präzisionsinstrument bauen**

---

## Warum dieses Tutorial?

In den letzten drei Tutorials haben Sie drei Strukturierungsformate kennengelernt:

- **Tutorial 02-01 (Markdown):** Schnell, lesbar, für 80% aller Prompts ausreichend
- **Tutorial 02-02 (XML):** Hierarchisch, modular, ideal für System-Prompts und Claude
- **Tutorial 02-03 (JSON):** Maschinenlesbar, perfekt für Daten-Input und strukturierten Output

Jedes Format hat seine Stärke — und seine Grenzen. Markdown ist schnell, aber wird bei langen Prompts unübersichtlich. XML ist strukturiert, aber für Dateninput umständlich. JSON ist maschinenlesbar, aber für Anweisungen unlesbar.

Die Lösung? **Kombinieren.**

Die besten Prompts der Praxis nutzen nicht ein Format, sondern mehrere — jedes dort, wo es am stärksten ist:

- **Markdown** für Anweisungen, die ein Mensch lesen und bearbeiten muss
- **XML** für die Gesamtarchitektur und modulare Abschnitte
- **JSON** für strukturierte Daten und maschinenlesbare Ausgaben

Das klingt komplex. Ist es auch — aber nach diesem Tutorial haben Sie ein klares Baukastensystem, mit dem Sie jeden Prompt systematisch aufbauen können. Egal wie komplex die Aufgabe.

> **Volksbank-Analogie:** Denken Sie an einen Kreditantrag. Das Deckblatt und die Erläuterungen sind in **Fließtext** (= Markdown). Die Formularfelder sind in **standardisierten Abschnitten** mit klaren Überschriften (= XML-Struktur). Die Finanzkennzahlen kommen als **Tabellendaten** aus dem Kernbanksystem (= JSON). Niemand würde das gesamte Dokument in nur einem Format erstellen — und genauso sollten Sie es mit komplexen Prompts halten.

**Was Sie nach diesem Tutorial können:**

- Verstehen, wann und warum man Formate kombiniert
- Das Drei-Schichten-Modell anwenden: XML-Rahmen + Markdown-Anweisungen + JSON-Daten
- Komplette System-Prompts für wiederverwendbare KI-Assistenten bauen
- Multi-Step-Pipelines entwerfen (Prompt-Ketten)
- Modulare Prompt-Bibliotheken aufbauen und pflegen
- Fehler in kombinierten Prompts erkennen und beheben
- Entscheiden, wann Kombination nötig ist — und wann ein Format reicht

---

## Historischer Rückblick: Vom Einzeiler zur Prompt-Architektur

| Jahr | Meilenstein | Was sich änderte |
|---|---|---|
| 2022 | ChatGPT-Launch (GPT-3.5) | Prompts waren Einzeiler: „Schreib mir eine E-Mail". Keine Struktur nötig |
| 2023 | GPT-4 + System-Prompts | Erstmals konnten Entwickler einen System-Prompt definieren — die „Persönlichkeit" der KI. Erste Markdown-Strukturen in Prompts |
| 2023 | Claude 2 + XML-Empfehlung | Anthropic empfahl offiziell XML-Tags für Prompts. Erste Kombination von XML-Rahmen + Fließtext |
| 2024 | Custom GPTs + Assistants API | Komplexe System-Prompts mit mehreren Abschnitten, Regeln und Datenquellen. Markdown + XML + JSON erstmals gemeinsam nötig |
| 2024 | Claude 3.5 Sonnet | Bewies, dass strukturierte Prompts messbar bessere Ergebnisse liefern als Fließtext — besonders bei komplexen Aufgaben |
| 2025 | GPT-5.2 + Claude Opus 4.6 | Modelle verstehen Multi-Format-Prompts nativ. OpenAI empfiehlt offiziell „Markdown formatting and XML tags" in Kombination. Anthropic empfiehlt XML + Markdown-Headers für verschiedene Prompt-Abschnitte |
| 2025 | Meta-Format Reasoning | Fortgeschrittene Systeme wechseln das Format dynamisch: JSON für Daten, XML für Reasoning-Schritte, Markdown für menschenlesbare Zusammenfassungen |

> **Warum das wichtig ist:** Prompt Engineering entwickelt sich von einer Kunst zu einer Ingenieursdisziplin. Wie bei Software-Architektur gibt es bewährte Muster, wiederverwendbare Bausteine und klare Trennprinzipien. Dieses Tutorial zeigt Ihnen die wichtigsten Architekturmuster.

---

## Schritt 1: Das Drei-Schichten-Modell — Ihr Bauplan für komplexe Prompts

Das Grundprinzip ist einfach: **Jedes Format hat seine Schicht.**

> **Volksbank-Analogie:** Das Drei-Schichten-Modell ist wie die Ordnung in einer Kreditakte. Der **Aktendeckel** (XML-Rahmen) definiert die Abschnitte: Antrag, Bonitätsprüfung, Sicherheiten, Entscheidung. Der **Inhalt** jedes Abschnitts (Markdown) ist in lesbarem Deutsch geschrieben, mit Aufzählungen und Hervorhebungen. Die **Kennzahlen** (JSON) kommen aus dem Kernbanksystem als strukturierte Daten. Ohne diese Ordnung wäre die Akte ein 50-seitiger Fließtext — technisch vollständig, praktisch unbrauchbar.

So sieht das als Schema aus:

```
┌─────────────────────────────────────────────────────────────────┐
│        🏗️ Das Drei-Schichten-Modell                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Schicht 1: XML-RAHMEN (Architektur)                           │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ <system>                                                 │   │
│  │   <rolle>...</rolle>                                     │   │
│  │   <kontext>...</kontext>                                 │   │
│  │   <regeln>...</regeln>                                   │   │
│  │   <aufgabe>...</aufgabe>                                 │   │
│  │   <daten>...</daten>                                     │   │
│  │   <ausgabe>...</ausgabe>                                 │   │
│  │ </system>                                                │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Schicht 2: MARKDOWN-ANWEISUNGEN (Inhalt)                      │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Innerhalb der XML-Tags:                                  │   │
│  │ - **Fettdruck** für Schlüsselwörter                      │   │
│  │ - Aufzählungen für Regeln                                │   │
│  │ - Nummerierte Listen für Schritte                        │   │
│  │ - Überschriften für Unterabschnitte                      │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Schicht 3: JSON-DATEN (Payload)                               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │ Innerhalb von <daten> oder <ausgabe>:                    │   │
│  │ { "kunde": "...", "betrag": 50000 }                      │   │
│  │ [{ "id": 1, ... }, { "id": 2, ... }]                    │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  XML definiert WO etwas steht                                  │
│  Markdown definiert WAS dort steht (lesbar)                    │
│  JSON definiert WELCHE DATEN fließen                           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Warum drei Schichten statt einer?

| Problem mit einem Format | Lösung durch Kombination |
|---|---|
| Langer Markdown-Prompt → KI übersieht Regeln am Ende | XML-Tags gruppieren Regeln → KI erkennt den Abschnitt `<regeln>` |
| XML-only → Anweisungen werden unleserlich für den Menschen | Markdown innerhalb der XML-Tags → Mensch und KI verstehen es |
| JSON-only → Für Anweisungen ungeeignet | JSON nur für Daten-Payload, Anweisungen in Markdown |
| Daten und Anweisungen vermischt → KI verwechselt beides | `<daten>` enthält JSON, `<aufgabe>` enthält Markdown → klare Trennung |

---

## Schritt 2: Ihr erster kombinierter Prompt — Kreditprüfung

Genug Theorie. Hier ein vollständiges Beispiel, das alle drei Formate nutzt:

### Nur-Markdown-Version (wie bisher)

```
Du bist ein erfahrener Kreditanalyst einer Genossenschaftsbank. 

Bewerte die folgende Kreditanfrage. Berücksichtige: 
Einkommensstabilität, Verschuldungsgrad, Sicherheiten, 
Kapitaldienstfähigkeit. Beachte BaFin MaRisk-Anforderungen. 
Antwortformat: Risikobewertung (niedrig/mittel/hoch), 
Empfehlung (genehmigen/prüfen/ablehnen), Begründung, 
Auflagen. Keine persönlichen Kundendaten verwenden. 
Alle Empfehlungen unter Vier-Augen-Vorbehalt.

Kundendaten: 42 Jahre, Lehrerin verbeamtet, 3.400€ netto, 
verheiratet, 1 Kind, Ratenkredit 20.000€, 60 Monate, 
keine bestehenden Kredite.
```

Das funktioniert. Aber: Alle Regeln, Daten und Aufgaben stehen in einem Block. Bei komplexeren Fällen (mehrere Kunden, mehr Regeln, detaillierteres Ausgabeformat) wird das schnell unübersichtlich.

### Drei-Schichten-Version (kombiniert)

> **Keine Sorge:** Das sieht auf den ersten Blick nach viel aus — aber Sie füllen nur die Abschnitte zwischen den Tags aus. Die Tags selbst sind wie Überschriften in einem Formular: einmal anlegen, dann immer wieder verwenden.

```xml
<system>
  <rolle>
    Du bist ein erfahrener **Kreditanalyst** einer 
    Genossenschaftsbank mit 15 Jahren Berufserfahrung. 
    Du bewertest Kreditanfragen nach bankinternen Standards 
    und regulatorischen Vorgaben.
  </rolle>

  <kontext>
    ## Regulatorischer Rahmen
    - **BaFin MaRisk** (Mindestanforderungen an das Risikomanagement)
    - **KWG §18** (Offenlegung wirtschaftlicher Verhältnisse ab 750.000€)
    - **Haushaltsrechnung** nach Sparkassen-/VR-Standard

    ## Bewertungskriterien
    1. Einkommensstabilität (Beschäftigungsstatus, Branche)
    2. Verschuldungsgrad (bestehende Verpflichtungen / Nettoeinkommen)
    3. Sicherheitenwert (Beleihungswert, Verwertbarkeit)
    4. Kapitaldienstfähigkeit (Rate / verfügbares Einkommen)
    5. Scoring-Indikatoren (SCHUFA, interne Scores)
  </kontext>

  <regeln>
    - **Anonymisierung:** Verwende keine echten Kundennamen in der Ausgabe
    - **Vier-Augen-Prinzip:** Jede Empfehlung steht unter Vorbehalt der 
      Prüfung durch einen zweiten Sachbearbeiter
    - **Kapitaldienstgrenze:** Monatsrate darf 35% des Haushaltsnettos 
      nicht überschreiten
    - **Pauschalen:** Lebenshaltung Erwachsene 900€, Kinder 400€
    - **Puffer:** Mindestens 10% Sicherheitspuffer auf verfügbares Einkommen
  </regeln>

  <aufgabe>
    Bewerte die Kreditanfrage in `<daten>` und antworte 
    **ausschließlich im JSON-Format** gemäß `<ausgabe_schema>`.

    ## Arbeitsschritte
    1. Haushaltsrechnung aufstellen
    2. Kapitaldienstfähigkeit berechnen
    3. Risikofaktoren identifizieren
    4. Gesamtbewertung abgeben
  </aufgabe>

  <daten format="json">
{
  "antragsteller": {
    "alter": 42,
    "beruf": "Lehrerin",
    "beschaeftigung": "verbeamtet",
    "einkommen_netto_monat": 3400,
    "familienstand": "verheiratet",
    "kinder": 1,
    "partner_einkommen_netto": 0
  },
  "kredit": {
    "art": "Ratenkredit",
    "betrag": 20000,
    "laufzeit_monate": 60,
    "verwendungszweck": "Küche"
  },
  "bestehende_verpflichtungen": [],
  "sicherheiten": "keine",
  "schufa_score": "gut"
}
  </daten>

  <ausgabe_schema>
{
  "haushaltsrechnung": {
    "einnahmen_gesamt": "<Zahl>",
    "ausgaben_gesamt": "<Zahl>",
    "verfuegbar_vor_rate": "<Zahl>",
    "rate_berechnet": "<Zahl>",
    "verfuegbar_nach_rate": "<Zahl>",
    "kapitaldienst_quote_prozent": "<Zahl>"
  },
  "bewertung": {
    "risiko": "<niedrig|mittel|hoch>",
    "empfehlung": "<genehmigen|prüfen|ablehnen>",
    "begruendung": "<2-3 Sätze>",
    "staerken": ["<...>", "<...>"],
    "schwaechen": ["<...>", "<...>"],
    "auflagen": ["<...>"]
  },
  "vier_augen_hinweis": "Empfehlung unter Vorbehalt — Prüfung durch zweiten Sachbearbeiter erforderlich"
}
  </ausgabe_schema>
</system>
```

### Was ist besser — und warum?

| Kriterium | Nur Markdown | Drei-Schichten-Kombination |
|---|---|---|
| **Lesbarkeit für den Ersteller** | Gut bei kurzen Prompts | Besser bei langen Prompts — jeder Abschnitt ist klar benannt |
| **Wartbarkeit** | Schwierig — wo war nochmal die Kapitaldienstgrenze? | Einfach — `<regeln>` öffnen, Regel ändern, fertig |
| **Wiederverwendbarkeit** | Gering — alles ist verwoben | Hoch — `<daten>` austauschen = neuer Kunde, Rest bleibt |
| **KI-Verständnis** | Gut bei einfachen Aufgaben | Besser bei komplexen Aufgaben — KI erkennt Abschnittsgrenzen |
| **Datenintegrität** | Daten und Regeln vermischt | Daten in JSON, klar getrennt von Anweisungen |
| **Ausgabe-Konsistenz** | KI interpretiert Formatwunsch | Schema erzwingt exaktes Format |

> **Kernregel:** Einfache Aufgabe → Markdown reicht. Sobald Sie mehr als 3 Abschnitte haben (Rolle + Kontext + Regeln + Daten + Ausgabe), lohnt sich die Drei-Schichten-Kombination.

---

## Schritt 3: Modulare Bausteine — Prompts wie LEGO zusammensetzen

Der größte Vorteil kombinierter Prompts: **Modularität.** Jeder XML-Block ist ein austauschbarer Baustein.

```
┌─────────────────────────────────────────────────────────────────┐
│        🧱 Modulares Prompt-System                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  BAUSTEIN-BIBLIOTHEK                                           │
│                                                                 │
│  <rolle>              <kontext>           <regeln>             │
│  ┌──────────────┐    ┌──────────────┐   ┌──────────────┐      │
│  │ Kreditanalyst│    │ Privatkredit │   │ Standard-    │      │
│  │ Berater      │    │ Baufi        │   │ Compliance   │      │
│  │ Controller   │    │ Firmenkredit │   │ Datenschutz  │      │
│  │ Compliance   │    │ Wertpapier   │   │ BaFin MaRisk │      │
│  └──────────────┘    └──────────────┘   └──────────────┘      │
│         ↓                   ↓                  ↓               │
│  ┌──────────────────────────────────────────────────────┐      │
│  │            ZUSAMMENGESETZTER PROMPT                   │      │
│  │  <rolle>Kreditanalyst</rolle>                        │      │
│  │  <kontext>Baufinanzierung</kontext>                  │      │
│  │  <regeln>Standard-Compliance + BaFin</regeln>        │      │
│  │  <daten>{ ... JSON ... }</daten>                     │      │
│  │  <ausgabe_schema>{ ... }</ausgabe_schema>            │      │
│  └──────────────────────────────────────────────────────┘      │
│                                                                 │
│  Neuer Kunde? → Nur <daten> austauschen                        │
│  Andere Kreditart? → <kontext> wechseln                        │
│  Strengere Regeln? → <regeln> erweitern                        │
│  Anderer Analyst? → <rolle> anpassen                           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Praxisbeispiel: Baufinanzierung vs. Konsumentenkredit

Statt zwei komplett verschiedene Prompts zu schreiben, tauschen Sie nur die relevanten Bausteine:

**Baustein `<kontext>` für Baufinanzierung:**

```xml
<kontext>
  ## Kreditart: Baufinanzierung
  - Beleihungswertermittlung nach BelWertV
  - Eigenkapitalquote: Mindestens 10% empfohlen
  - Zinsbindung: 10, 15 oder 20 Jahre
  - Tilgungsrate: Mindestens 2% p.a.
  - Nebenkosten: ~10-15% (Grunderwerbsteuer, Notar, Makler)
  - Sondertilgung: Standard 5% p.a. kostenfrei
</kontext>
```

**Baustein `<kontext>` für Konsumentenkredit:**

```xml
<kontext>
  ## Kreditart: Konsumentenkredit
  - Maximale Laufzeit: 84 Monate
  - Keine Sicherheiten erforderlich bis 50.000€
  - Effektivzins: Aktuell 5,5-8,5% je nach Bonität
  - Verwendungsnachweis: Nicht erforderlich unter 10.000€
  - Sondertilgung: Jederzeit kostenfrei
</kontext>
```

Alles andere — `<rolle>`, `<regeln>`, `<ausgabe_schema>` — bleibt identisch. Sie bauen sich eine **Bibliothek** wiederverwendbarer Bausteine.

> **Volksbank-Analogie:** Das ist wie Ihre Formularvorlagen im Kernbanksystem. Es gibt ein Basisformular für die Kreditentscheidung — und je nach Kreditart werden verschiedene Module zugeschaltet: Baufinanzierungs-Modul, KfW-Modul, Firmenkunden-Modul. Der Grundaufbau bleibt gleich, die Inhalte variieren. Genau so funktionieren modulare Prompts.

---

## Schritt 4: System-Prompts für KI-Assistenten bauen

Die anspruchsvollste Anwendung kombinierter Formate: **System-Prompts.** Das sind die Anweisungen, die definieren, wie sich ein KI-Assistent dauerhaft verhält — nicht nur für eine einzelne Frage, sondern für jedes Gespräch.

In Kapitel 03 werden wir Custom GPTs und Projekte erstellen. Dort wird der System-Prompt das Herzstück sein. Hier lernen Sie bereits die Architektur.

> **Hinweis für Einsteiger:** Dieser Schritt richtet sich vor allem an Fortgeschrittene und Ihre IT-/Digitalisierungsabteilung. Als Anwenderin oder Anwender reicht es, das Prinzip zu verstehen — Sie werden System-Prompts im Alltag eher *nutzen* als selbst *bauen*. Aber zu wissen, wie sie funktionieren, hilft Ihnen, die Möglichkeiten einzuschätzen.

### Anatomie eines professionellen System-Prompts

```xml
<system_prompt version="1.2" letzte_aenderung="2025-07">

  <identitaet>
    Du bist **KreditCheck**, ein interner Assistent der 
    Volksbank Hellweg für die Vorprüfung von Kreditanfragen.

    ## Persönlichkeit
    - Sachlich und präzise, aber nicht kalt
    - Erklärt Entscheidungen verständlich
    - Weist proaktiv auf Risiken hin
    - Spricht den Sachbearbeiter mit „Sie" an
  </identitaet>

  <faehigkeiten>
    Du kannst:
    1. Kreditanfragen nach bankinternen Kriterien vorprüfen
    2. Haushaltsrechnungen erstellen
    3. Risikofaktoren identifizieren und gewichten
    4. Vergleichbare Fälle aus der Praxis heranziehen
    5. Handlungsempfehlungen mit Auflagen formulieren

    Du kannst NICHT:
    - Endgültige Kreditentscheidungen treffen (Vier-Augen-Prinzip)
    - Auf das Kernbanksystem zugreifen
    - SCHUFA-Abfragen durchführen
    - Rechtsverbindliche Aussagen machen
  </faehigkeiten>

  <regeln>
    ## Datenschutz
    - Keine echten Kundennamen in Antworten verwenden
    - Wenn der Nutzer versehentlich echte Namen eingibt → 
      freundlich darauf hinweisen und anonymisieren
    - Keine Daten aus dem Gespräch für andere Anfragen nutzen

    ## Compliance
    - Alle Empfehlungen unter Vier-Augen-Vorbehalt
    - Bei Krediten über 750.000€ → Hinweis auf KWG §18
    - Bei gewerblichen Anfragen → Hinweis auf Rating-Pflicht
    - Kapitaldienstquote maximal 35% des Haushaltsnettos

    ## Gesprächsführung
    - Bei unvollständigen Daten → **nachfragen**, nicht raten
    - Bei grenzwertigen Fällen → beide Optionen darstellen
    - Immer die Datengrundlage der Empfehlung nennen
  </regeln>

  <eingabe_erwartung>
    Der Sachbearbeiter liefert Kundendaten idealerweise 
    als JSON:

    ```json
    {
      "antragsteller": { "alter": 0, "beruf": "..." },
      "kredit": { "art": "...", "betrag": 0 },
      "bestehende_verpflichtungen": [],
      "sicherheiten": "..."
    }
    ```

    Wenn Fließtext geliefert wird → in JSON-Struktur 
    umwandeln und dem Nutzer zur Bestätigung zeigen.
  </eingabe_erwartung>

  <ausgabe_format>
    Antworte immer in diesem Format:

    ## 1. Zusammenfassung
    *2-3 Sätze: Kernbewertung und Empfehlung*

    ## 2. Haushaltsrechnung
    *Tabelle mit Einnahmen, Ausgaben, verfügbarem Einkommen*

    ## 3. Bewertung
    ```json
    {
      "risiko": "<niedrig|mittel|hoch>",
      "empfehlung": "<genehmigen|prüfen|ablehnen>",
      "kapitaldienst_quote": "<Zahl>%",
      "staerken": ["..."],
      "schwaechen": ["..."],
      "auflagen": ["..."]
    }
    ```

    ## 4. Nächste Schritte
    *Was der Sachbearbeiter konkret tun sollte*
  </ausgabe_format>

  <beispiele>
    <beispiel typ="standard">
      <nutzer_eingabe>
        Kundin, 35, Ärztin, 5.200€ netto, ledig, 
        keine Kinder, will 15.000€ Ratenkredit für Auto, 
        48 Monate, keine bestehenden Kredite, SCHUFA gut
      </nutzer_eingabe>
      <erwartete_antwort>
        ## 1. Zusammenfassung
        Unkomplizierter Fall mit niedrigem Risiko. Hohe 
        Einkommensstabilität durch Arztberuf, keine 
        bestehenden Verpflichtungen. Genehmigung empfohlen.

        ## 2. Haushaltsrechnung
        | Position | Betrag |
        |---|---|
        | Nettoeinkommen | 5.200€ |
        | Lebenshaltung | -900€ |
        | Rate (ca. 4,9%) | -345€ |
        | **Verfügbar** | **3.955€** |

        ## 3. Bewertung
        ```json
        {
          "risiko": "niedrig",
          "empfehlung": "genehmigen",
          "kapitaldienst_quote": "6.6%",
          "staerken": ["hohes Einkommen", "keine Vorbelastung", "stabiler Beruf"],
          "schwaechen": ["keine Sicherheiten"],
          "auflagen": []
        }
        ```

        ## 4. Nächste Schritte
        - SCHUFA-Abfrage durchführen (Bestätigung „gut")
        - Konditionen kalkulieren und Angebot erstellen
        - Kein Vier-Augen erforderlich unter 50.000€
      </erwartete_antwort>
    </beispiel>
  </beispiele>

</system_prompt>
```

### Was macht diesen System-Prompt stark?

| Element | Format | Warum dieses Format |
|---|---|---|
| `<identitaet>` | XML-Rahmen + Markdown | XML grenzt den Abschnitt ab, Markdown macht die Persönlichkeitsbeschreibung lesbar |
| `<faehigkeiten>` | XML + Markdown-Listen | „Kann" und „Kann nicht" als klare Aufzählungen — KI beachtet Negationen in Listen besser als in Fließtext |
| `<regeln>` | XML + Markdown-Überschriften | Markdown-`##` gruppiert Regelkategorien innerhalb des XML-Blocks |
| `<eingabe_erwartung>` | XML + JSON-Schema | JSON-Schema zeigt der KI das erwartete Datenformat |
| `<ausgabe_format>` | XML + Markdown + JSON | Markdown für die menschenlesbaren Teile, JSON für die strukturierten Daten |
| `<beispiele>` | XML + verschachtelte XML | Few-Shot-Beispiel mit klarer Trennung von Input und Output |

> **Volksbank-Analogie:** Dieser System-Prompt ist wie die **Arbeitsanweisung** für einen neuen Mitarbeiter am Kreditschalter: Wer bist du (Rolle), was darfst du (Fähigkeiten), welche Regeln gelten (Compliance), wie sehen Eingangsunterlagen aus (Eingabe), wie sieht dein Prüfbericht aus (Ausgabe), und hier ist ein Beispiel eines fertig bearbeiteten Falls. Alles, was ein neuer Kollege am ersten Tag braucht — in einem Dokument.

---

## Schritt 5: Multi-Step-Pipelines — Prompt-Ketten für komplexe Aufgaben

Manche Aufgaben sind zu groß für einen einzelnen Prompt. Die Lösung: **Prompt-Ketten** — mehrere Prompts, die aufeinander aufbauen. Das Ergebnis von Prompt 1 wird zum Input für Prompt 2.

```
┌─────────────────────────────────────────────────────────────────┐
│        🔗 Prompt-Pipeline: Kreditentscheidung komplett          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  SCHRITT 1: Datenaufbereitung                                  │
│  ┌─────────────────────────────────────────────┐               │
│  │ Input: Fließtext-Kundenakte                  │               │
│  │ Prompt: „Extrahiere Kundendaten als JSON"    │               │
│  │ Output: Strukturiertes JSON                  │───┐           │
│  └─────────────────────────────────────────────┘   │           │
│                                                     ↓           │
│  SCHRITT 2: Kreditprüfung                                      │
│  ┌─────────────────────────────────────────────┐               │
│  │ Input: JSON aus Schritt 1                    │               │
│  │ Prompt: „Bewerte Kreditanfrage"              │               │
│  │ Output: Bewertungs-JSON                      │───┐           │
│  └─────────────────────────────────────────────┘   │           │
│                                                     ↓           │
│  SCHRITT 3: Dokumenterstellung                                 │
│  ┌─────────────────────────────────────────────┐               │
│  │ Input: Bewertungs-JSON aus Schritt 2         │               │
│  │ Prompt: „Erstelle Kreditvorlage in Markdown" │               │
│  │ Output: Fertige Entscheidungsvorlage         │               │
│  └─────────────────────────────────────────────┘               │
│                                                                 │
│  Gesamtzeit: ~5 Minuten statt ~45 Minuten manuell             │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Schritt-für-Schritt: Die drei Prompts

**Pipeline-Prompt 1: Datenextraktion (Fließtext → JSON)**

```xml
<aufgabe>
  Extrahiere aus dem folgenden Fließtext alle relevanten 
  Kreditdaten und gib sie als JSON zurück.

  ## Regeln
  - Antworte **ausschließlich** als JSON
  - Fehlende Daten als `null` markieren
  - Beträge als Zahlen ohne €-Zeichen
  - Verwende das Schema in `<schema>`
</aufgabe>

<schema>
{
  "antragsteller": {
    "alter": null,
    "beruf": null,
    "beschaeftigung": null,
    "einkommen_netto_monat": null,
    "familienstand": null,
    "kinder": null,
    "partner_einkommen_netto": null
  },
  "kredit": {
    "art": null,
    "betrag": null,
    "laufzeit_monate": null,
    "verwendungszweck": null
  },
  "bestehende_verpflichtungen": [],
  "sicherheiten": null,
  "schufa_score": null,
  "fehlende_daten": ["<Liste der Felder, die im Text nicht vorkamen>"]
}
</schema>

<eingabe_text>
Frau Schneider ist 48 und arbeitet als Teamleiterin 
bei der Telekom, unbefristet. Sie verdient 4.100€ 
netto und ist geschieden, hat zwei Kinder (14 und 17). 
Sie möchte eine Baufinanzierung über 320.000€ für ein 
Reihenhaus. Eigenkapital hat sie 45.000€. Sie zahlt 
noch einen Autokredit ab, 280€ im Monat, läuft noch 
18 Monate. SCHUFA ist unauffällig.
</eingabe_text>
```

**Pipeline-Prompt 2: Kreditprüfung (JSON → Bewertungs-JSON)**

```xml
<system>
  <rolle>
    Erfahrener Kreditanalyst einer Genossenschaftsbank.
  </rolle>

  <regeln>
    - Kapitaldienstgrenze: 35% des Haushaltsnettos
    - Pauschalen: Erwachsene 900€, Kind 400€
    - Eigenkapitalquote Baufi: Mindestens 10% empfohlen
    - Nebenkosten: 12% des Kaufpreises kalkulieren
    - Tilgung: Mindestens 2% p.a.
    - Bestehende Verpflichtungen voll anrechnen
  </regeln>

  <aufgabe>
    Bewerte die Kreditanfrage und antworte als JSON.
  </aufgabe>

  <daten>
    [Hier das JSON-Ergebnis aus Prompt 1 einfügen]
  </daten>

  <ausgabe_schema>
{
  "haushaltsrechnung": {
    "einnahmen": { "netto": 0, "partner": 0, "gesamt": 0 },
    "ausgaben": {
      "lebenshaltung": 0,
      "kinder": 0,
      "bestehende_kredite": 0,
      "nebenkosten_immobilie": 0,
      "gesamt": 0
    },
    "verfuegbar": 0,
    "max_rate": 0
  },
  "finanzierung": {
    "kaufpreis": 0,
    "nebenkosten": 0,
    "gesamtkosten": 0,
    "eigenkapital": 0,
    "finanzierungsbedarf": 0,
    "eigenkapitalquote_prozent": 0,
    "monatliche_rate_bei_2pct_tilgung": 0,
    "kapitaldienst_quote_prozent": 0
  },
  "bewertung": {
    "risiko": "<niedrig|mittel|hoch>",
    "empfehlung": "<genehmigen|prüfen|ablehnen>",
    "begruendung": "<2-3 Sätze>",
    "staerken": [],
    "schwaechen": [],
    "auflagen": []
  }
}
  </ausgabe_schema>
</system>
```

**Pipeline-Prompt 3: Dokumenterstellung (JSON → Vorlage)**

```xml
<aufgabe>
  Erstelle aus den folgenden Bewertungsdaten eine 
  **Kreditentscheidungsvorlage** im Markdown-Format, 
  die der Sachbearbeiter dem Vorgesetzten vorlegen kann.

  ## Format-Vorgaben
  - Professioneller Ton
  - Keine Abkürzungen
  - Tabellen für Kennzahlen
  - Ampel-System: 🟢 niedrig, 🟡 mittel, 🔴 hoch
  - Datum und Vorbehaltsvermerk am Ende
</aufgabe>

<bewertungsdaten>
  [Hier das JSON-Ergebnis aus Prompt 2 einfügen]
</bewertungsdaten>
```

### Warum Pipeline statt Mega-Prompt?

| Aspekt | Ein großer Prompt | Pipeline (3 Schritte) |
|---|---|---|
| **Komplexität pro Schritt** | Sehr hoch — KI muss alles gleichzeitig | Niedrig — jeder Schritt hat eine Aufgabe |
| **Fehlersuche** | Schwierig — wo ging es schief? | Einfach — Schritt-für-Schritt prüfen |
| **Ergebnis-Qualität** | Gut, aber inkonsistent bei langen Prompts | Besser — jeder Schritt ist fokussiert |
| **Wiederverwendbarkeit** | Gering — alles ist verwoben | Hoch — Schritt 1 für jede Datenextraktion nutzbar |
| **Kosten (Tokens)** | Weniger Tokens insgesamt | Mehr Tokens, aber bessere Ergebnisse |
| **Menschliche Kontrolle** | Nur am Ende prüfbar | Nach jedem Schritt prüfbar |

> **Praxis-Tipp:** Die Pipeline ist besonders wertvoll, wenn Sie nach Schritt 1 (Datenextraktion) die JSON-Daten **manuell prüfen** möchten, bevor die KI damit weiterarbeitet. So stellen Sie sicher, dass die Grundlage stimmt — bevor eine fehlerhafte Bewertung entsteht.

> **Ausblick Automatisierung:** Diese Pipelines können Sie auch vollständig automatisieren — über die API von OpenAI oder Anthropic, über No-Code-Tools wie Zapier/Make, oder über Custom GPTs mit mehreren „Instructions"-Blöcken. In Kapitel 03 lernen Sie, wie Sie aus dieser Pipeline einen fertigen KI-Assistenten bauen, der alle drei Schritte automatisch durchläuft.

> **Volksbank-Analogie:** Die Pipeline ist wie der Kreditprozess in Ihrer Bank: Erst erfasst der Kundenberater die Daten (Schritt 1). Dann prüft die Kreditabteilung die Bonität (Schritt 2). Dann erstellt der Sachbearbeiter die Entscheidungsvorlage (Schritt 3). Jede Station hat ihre Aufgabe, jede kann ihren Teil prüfen. Niemand macht alles alleine.

---

## Schritt 6: Architektur-Muster für häufige Anwendungsfälle

Hier sind vier bewährte Muster, die Sie als Vorlage für Ihre eigenen Prompts nutzen können:

### Muster 1: Analyse mit strukturiertem Output

**Anwendung:** Einzelne komplexe Analyse (Kreditprüfung, Kundenanalyse, Filialvergleich)

```xml
<system>
  <rolle>Markdown: Wer bist du?</rolle>
  <kontext>Markdown: Welche Rahmenbedingungen gelten?</kontext>
  <regeln>Markdown-Listen: Was muss beachtet werden?</regeln>
  <aufgabe>Markdown: Was genau soll getan werden?</aufgabe>
  <daten format="json">JSON: Die zu analysierenden Daten</daten>
  <ausgabe_schema>JSON: Exaktes Antwortformat</ausgabe_schema>
</system>
```

**Wann nutzen:** Wenn Sie ein klares Ergebnis in einem definierten Format brauchen.

### Muster 2: Batch-Verarbeitung mit Qualitätskontrolle

**Anwendung:** Viele gleichartige Datensätze verarbeiten (20 Kreditanfragen, 50 Kundenbriefe, 15 Filialen)

```xml
<system>
  <rolle>Markdown: Wer bist du?</rolle>
  <regeln>
    ## Verarbeitungsregeln
    - Jeden Datensatz einzeln bewerten
    - Bei Unsicherheit: `"confidence": "niedrig"` setzen
    - Fehlende Daten als `null`, nicht raten

    ## Qualitätskontrolle
    - Am Ende: Zusammenfassung mit Gesamtstatistik
    - Ausreißer markieren (ungewöhnliche Werte)
  </regeln>
  <daten format="json">
    [{ ... }, { ... }, { ... }]   ← JSON-Array
  </daten>
  <ausgabe_schema>
{
  "ergebnisse": [{ ... }],
  "zusammenfassung": {
    "gesamt": 0,
    "genehmigt": 0,
    "abgelehnt": 0,
    "zur_pruefung": 0,
    "ausreisser": []
  }
}
  </ausgabe_schema>
</system>
```

**Wann nutzen:** Wenn Sie viele Datensätze gleichzeitig verarbeiten und eine Gesamtübersicht brauchen.

### Muster 3: Konversationeller Assistent mit Rückfragen

**Anwendung:** System-Prompt für einen interaktiven KI-Assistenten (Custom GPT, Claude-Projekt)

```xml
<system_prompt>
  <identitaet>Markdown: Name, Persönlichkeit, Tonfall</identitaet>
  <faehigkeiten>Markdown-Listen: Kann / Kann nicht</faehigkeiten>
  <regeln>Markdown: Compliance, Datenschutz, Grenzen</regeln>
  <gespraechsablauf>
    ## Bei unvollständigen Daten
    1. Freundlich nachfragen: „Mir fehlt noch: [Feld]"
    2. JSON-Vorlage anbieten zum Ausfüllen
    3. Erst nach Bestätigung bewerten

    ## Bei grenzwertigen Fällen
    1. Beide Optionen darstellen
    2. Risiken transparent machen
    3. Empfehlung mit Begründung geben
  </gespraechsablauf>
  <eingabe_erwartung>JSON-Schema: Ideales Datenformat</eingabe_erwartung>
  <ausgabe_format>Markdown + JSON: Lesbarer Text + strukturierte Daten</ausgabe_format>
  <beispiele>
    <beispiel>XML: Frage → Antwort</beispiel>
  </beispiele>
</system_prompt>
```

**Wann nutzen:** Wenn die KI nicht nur einmal antwortet, sondern ein Gespräch führt.

### Muster 4: Vergleichs-Analyse (Entscheidungsmatrix)

**Anwendung:** Zwei oder mehr Optionen systematisch vergleichen (Filialen, Produkte, Strategien)

```xml
<system>
  <aufgabe>
    Vergleiche die folgenden Optionen anhand der 
    definierten Kriterien. Antworte als JSON.
  </aufgabe>
  <kriterien>
    1. **Wirtschaftlichkeit** (Gewicht: 30%)
    2. **Kundennutzen** (Gewicht: 25%)
    3. **Umsetzbarkeit** (Gewicht: 25%)
    4. **Risiko** (Gewicht: 20%)
  </kriterien>
  <optionen format="json">
    [
      { "name": "Option A", "beschreibung": "..." },
      { "name": "Option B", "beschreibung": "..." }
    ]
  </optionen>
  <ausgabe_schema>
{
  "vergleich": [
    {
      "option": "<Name>",
      "scores": {
        "wirtschaftlichkeit": { "score": 0, "begruendung": "..." },
        "kundennutzen": { "score": 0, "begruendung": "..." },
        "umsetzbarkeit": { "score": 0, "begruendung": "..." },
        "risiko": { "score": 0, "begruendung": "..." }
      },
      "gewichteter_gesamtscore": 0
    }
  ],
  "empfehlung": "<Name der besten Option>",
  "begruendung": "<2-3 Sätze>"
}
  </ausgabe_schema>
</system>
```

**Wann nutzen:** Bei Entscheidungen, die auf mehreren Kriterien basieren.

---

## Schritt 7: Fehlerquellen in kombinierten Prompts — und wie Sie sie vermeiden

Kombinierte Formate sind mächtig, aber auch fehleranfällig. Hier die häufigsten Stolperfallen:

### Die 7 häufigsten Fehler

| # | Fehler | Beispiel | Lösung |
|---|---|---|---|
| 1 | **XML-Tag nicht geschlossen** | `<regeln>... (kein </regeln>)` | Jedes öffnende Tag braucht ein schließendes Tag. Tipp: Zuerst alle Tags schreiben, dann füllen |
| 2 | **JSON innerhalb von XML hat falsches Escaping** | `<daten>{"wert": "Kundin "A""}</daten>` | Anführungszeichen in JSON-Werten mit `\"` escapen, oder einfache Anführungszeichen im Text verwenden |
| 3 | **Formate an der falschen Stelle** | Anweisungen als JSON: `{"aufgabe": "Bewerte..."}` | Anweisungen gehören in Markdown. JSON nur für Daten und Schemas |
| 4 | **Zu viele Verschachtelungsebenen** | XML 5 Ebenen tief, darin JSON 3 Ebenen tief | Maximum: 3 XML-Ebenen, 2 JSON-Ebenen. Sonst verliert die KI den Überblick |
| 5 | **Widersprüche zwischen Abschnitten** | `<regeln>` sagt 35% Kapitaldienstgrenze, `<beispiel>` zeigt 40% | Beispiele müssen die Regeln widerspiegeln — sonst folgt die KI dem Beispiel |
| 6 | **Markdown-Überschriften kollidieren mit XML-Struktur** | `# Rolle` als Markdown-H1 + `<rolle>` als XML → was gilt? | Entscheiden: Entweder XML-Tags ODER Markdown-Überschriften für die Gliederung. Nicht beides auf derselben Ebene |
| 7 | **Schema-Mismatch: Input-JSON hat andere Felder als erwartet** | Schema erwartet `einkommen_netto`, Input hat `netto_gehalt` | Feldnamen konsistent halten. Einmal definieren, überall verwenden |

### Selbst-Check: 5 Fragen vor dem Absenden

Bevor Sie einen kombinierten Prompt absenden, prüfen Sie:

1. ✅ **Ist jeder XML-Tag geschlossen?** (Öffnend + schließend)
2. ✅ **Ist das JSON syntaktisch korrekt?** (Im Zweifelsfall: jsonlint.com)
3. ✅ **Sind Anweisungen in Markdown, Daten in JSON?** (Nicht vermischen)
4. ✅ **Stimmen die Feldnamen im Schema mit dem Input überein?**
5. ✅ **Widersprechen sich Regeln und Beispiele?**

> **Volksbank-Analogie:** Das ist wie die Checkliste vor einer Kreditentscheidung: Unterschriften vollständig? Alle Unterlagen da? Beträge korrekt? Ein vergessenes Häkchen kann den ganzen Prozess aufhalten. Bei kombinierten Prompts ist es genauso — ein vergessenes `</regeln>` kann die gesamte Antwort durcheinanderbringen.

---

## Schritt 8: Wann brauche ich die Kombination — und wann nicht?

Nicht jeder Prompt braucht drei Formate. Die Kunst ist, die richtige Komplexitätsstufe zu wählen.

```
┌─────────────────────────────────────────────────────────────────┐
│        🎯 Entscheidungsbaum: Welche Komplexitätsstufe?          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Wie komplex ist Ihre Aufgabe?                                 │
│                                                                 │
│  ├── 📝 Einfach (1 Frage, 1 Antwort)                          │
│  │   → NUR MARKDOWN                                            │
│  │   „Fasse dieses Protokoll zusammen"                         │
│  │                                                              │
│  ├── 📋 Mittel (Rolle + Regeln + Aufgabe)                      │
│  │   → MARKDOWN mit Überschriften                              │
│  │   „Du bist X. Beachte Y. Tue Z."                           │
│  │                                                              │
│  ├── 📊 Komplex (Daten rein, strukturiertes Ergebnis raus)     │
│  │   → MARKDOWN + JSON                                         │
│  │   Daten als JSON-Input, Schema für JSON-Output              │
│  │                                                              │
│  ├── 🏗️ Sehr komplex (System-Prompt, viele Regeln, Beispiele)  │
│  │   → XML-RAHMEN + MARKDOWN + JSON                            │
│  │   Das Drei-Schichten-Modell aus diesem Tutorial             │
│  │                                                              │
│  └── 🔗 Mehrstufig (Ergebnis → nächster Schritt)               │
│      → PIPELINE (mehrere kombinierte Prompts)                  │
│      Prompt-Kette aus Schritt 5                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Faustregel: Die 3-Abschnitts-Regel

- **1-3 Abschnitte** → Markdown reicht
- **4-6 Abschnitte** → XML-Rahmen hinzufügen
- **Daten-Input oder strukturierter Output** → JSON hinzufügen
- **Wiederverwendbar für viele Fälle** → Modulare Bausteine mit XML

> **Kernregel:** Starten Sie immer mit Markdown. Fügen Sie XML hinzu, wenn die Struktur unübersichtlich wird. Fügen Sie JSON hinzu, wenn Daten fließen. Nicht umgekehrt. Komplexität nur da, wo sie Mehrwert bringt.

---

## Was kombinierte Prompts (noch) nicht können

| Limitation | Warum problematisch | Workaround |
|---|---|---|
| **Höhere Fehlerquote** | Drei Formate = drei Fehlerquellen. Ein vergessenes XML-Tag oder JSON-Komma kann alles stören | Selbst-Check (5-Punkte-Liste aus Schritt 7). Erst mit Markdown starten, dann Format für Format hinzufügen |
| **Mehr Tokens = höhere Kosten** | XML-Tags und JSON-Schemas verbrauchen Tokens, die bei Markdown eingespart wären. Beispielrechnung: Ein Markdown-Prompt mit ~500 Tokens wird durch XML-Rahmen + JSON-Schema zu ~1.200 Tokens — der Overhead beträgt ~140%, kostet aber nur 0,01€ mehr. Bei Pipeline (3 Schritte) summiert sich der Overhead auf ~3× | Nur dort kombinieren, wo es die Ergebnis-Qualität verbessert. Für einfache Aufgaben bleibt Markdown günstiger |
| **Lernkurve für das Team** | Nicht jeder Kollege kennt JSON oder XML. Prompts werden schwerer zu warten | Vorlagen erstellen, bei denen nur der `<daten>`-Block geändert werden muss. Den Rest als Blackbox behandeln |
| **Modell-Unterschiede** | Claude bevorzugt XML, GPT bevorzugt JSON/Markdown. Es gibt kein universelles Optimum | Für Claude: XML-Rahmen betonen. Für GPT: JSON-Schemas + Markdown. Für Gemini: Markdown + JSON (XML weniger zuverlässig) |
| **Kein Garantie-Format** | Selbst mit Schema antwortet die KI manchmal nicht exakt im gewünschten Format | „Antworte NUR als JSON" explizit betonen. JSON-Validator nutzen. Bei wiederholten Abweichungen: Modell wechseln |
| **Pipeline-Overhead** | Drei Prompts statt einem = dreifache Latenz und dreifache Kosten | Pipeline nur bei komplexen Aufgaben. Für Standard-Fälle reicht ein kombinierter Prompt |

---

## Kosten-Vergleich: Einfach vs. Kombiniert vs. Pipeline

| Ansatz | Tokens (ca.) | Kosten | Ergebnis-Qualität | Wartbarkeit |
|---|---|---|---|---|
| **Nur Markdown** (einfacher Prompt) | 500-1.500 | 0,01-0,02€ | Gut für einfache Aufgaben | Einfach |
| **Kombiniert** (XML + Markdown + JSON) | 2.000-5.000 | 0,03-0,08€ | Sehr gut für komplexe Aufgaben | Mittel |
| **Pipeline** (3 Schritte kombiniert) | 5.000-15.000 | 0,08-0,20€ | Exzellent für mehrstufige Prozesse | Hoch (modular) |
| **Manuell ohne KI** | — | 30-120€/Stunde Arbeitszeit | Abhängig vom Sachbearbeiter | — |

> **Fazit:** Der Kostenunterschied zwischen den KI-Varianten ist marginal (Cent-Bereich). Der Unterschied zur manuellen Bearbeitung ist enorm. Die Frage ist nicht „Kann ich mir den kombinierten Prompt leisten?" — sondern „Kann ich mir leisten, es nicht zu tun?"

---

## Modell-Empfehlungen für kombinierte Prompts

| Modell | Kombinations-Fähigkeit | Besonderheiten | Empfehlung |
|---|---|---|---|
| **Claude (Opus 4.6 / Sonnet 4)** | ⭐⭐⭐ Exzellent | XML-Tags sind Claudes „Muttersprache". Versteht verschachtelte XML + Markdown + JSON nativ. Hält sich sehr genau an Ausgabe-Schemas | Erste Wahl für komplexe kombinierte Prompts |
| **ChatGPT (GPT-5.2)** | ⭐⭐⭐ Exzellent | OpenAI empfiehlt offiziell „Markdown formatting and XML tags" in Kombination (Stand 2025). JSON-Mode für garantiert valide JSON-Ausgabe | Sehr gut, besonders mit JSON-Mode für Output |
| **Gemini (2.5 Pro)** | ⭐⭐ Gut | Versteht die Kombination, ist aber bei tief verschachtelten XML-Strukturen weniger zuverlässig. Markdown + JSON funktioniert besser als XML + JSON | Für einfache Kombinationen gut, bei hoher Komplexität Claude oder GPT bevorzugen |

### Modell-spezifische Optimierung

**Für Claude — XML betonen:**
```xml
<system>
  <rolle>...</rolle>
  <regeln>
    Markdown-Listen hier
  </regeln>
  <daten format="json">
    { ... }
  </daten>
</system>
```

**Für GPT — Markdown + JSON betonen:**
```
# ROLLE
...

# REGELN
- ...
- ...

# DATEN
```json
{ ... }
```

# AUSGABE-SCHEMA
```json
{ ... }
```
```

**Für Gemini — Markdown + klare JSON-Blöcke:**
```
## Rolle
...

## Regeln
- ...

## Daten (JSON)
{ ... }

## Antwortformat (JSON)
{ ... }
```

---

## Das Wichtigste auf einen Blick

| Konzept | Erklärung | Wichtigster Tipp |
|---|---|---|
| **Drei-Schichten-Modell** | XML für Struktur, Markdown für Anweisungen, JSON für Daten | Jedes Format dort, wo es am stärksten ist |
| **Modulare Bausteine** | XML-Blöcke als austauschbare Prompt-Komponenten | Einmal bauen, überall wiederverwenden |
| **System-Prompts** | Dauerhafte Persönlichkeit + Regeln für KI-Assistenten | Beispiele (`<beispiele>`) einbauen — die KI lernt daraus |
| **Prompt-Pipelines** | Mehrere Prompts, die aufeinander aufbauen | Nach jedem Schritt prüfen, bevor der nächste startet |
| **4 Architektur-Muster** | Analyse, Batch, Assistent, Vergleich | Das passende Muster wählen spart Entwurfszeit |
| **Fehlerquellen** | 7 typische Fehler bei kombinierten Formaten | 5-Punkte-Selbst-Check vor jedem Absenden |
| **Entscheidungsbaum** | Wann reicht Markdown? Wann brauche ich alle drei? | 3-Abschnitts-Regel: Erst Markdown, dann XML, dann JSON |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---|---|
| Drei-Schichten-Modell | Vereint die drei Formate aus Tutorial 02-01 (Markdown), 02-02 (XML) und 02-03 (JSON) zu einem kohärenten System |
| Modulare Bausteine | Erweitert das „Vier Muster"-Konzept aus Tutorial 02-01 (Standard, Eingabedaten, Vergleich, Mehrstufig) um austauschbare Komponenten |
| System-Prompt-Architektur | Baut auf dem XML-System-Prompt aus Tutorial 02-02, Schritt 6 auf — jetzt mit JSON-Integration für Daten und Schemas |
| Prompt-Pipeline | Verbindet die JSON-Pipeline aus Tutorial 02-03, Schritt 5 mit dem mehrstufigen Markdown-Prompt aus Tutorial 02-01, Muster 4 |
| Fehler-Prävention | Erweitert die JSON-Fehlerliste aus Tutorial 02-03, Schritt 7 und die XML-Fallstricke aus Tutorial 02-02, Schritt 8 um kombinierte Fehlerquellen |
| Modell-Empfehlungen | Konsolidiert die modellspezifischen Tipps aus allen drei Vorgänger-Tutorials zu einer Gesamtempfehlung |
| Kosten-Vergleich | Erweitert den Token-Kosten-Vergleich aus Tutorial 02-03 um Pipeline-Kosten und den Vergleich zur manuellen Bearbeitung |
| Entscheidungsbaum | Schließt den Kapitel-02-Bogen: Vom Entscheidungsbaum in Tutorial 02-03, Schritt 8 (Markdown vs. XML vs. JSON) zur Frage „Wann kombiniere ich?" |

---

## ⚠️ Compliance-Hinweis: Komplexität ändert nichts an den Grundregeln

Alle Datenschutz- und Compliance-Regeln aus den vorherigen Tutorials gelten unverändert:

| Grundregel | Bedeutung für kombinierte Prompts |
|---|---|
| **Keine echten Kundendaten** | Auch wenn der Prompt drei Formate nutzt: Anonymisieren bleibt Pflicht |
| **Vier-Augen-Prinzip** | Komplexere Prompts → komplexere Ergebnisse → Prüfung noch wichtiger |
| **Stichprobenkontrollen** | Bei Pipelines: Nach jedem Schritt stichprobenartig prüfen, nicht nur am Ende |
| **BaFin / DORA** | System-Prompts für KI-Assistenten müssen als IKT-Systeme dokumentiert werden |
| **Versionierung** | System-Prompts mit `version="1.2"` und `letzte_aenderung` kennzeichnen — für Audits |

**Besonderer Hinweis für Pipelines:** Bei mehrstufigen Prompt-Ketten ist die **Transparenz** besonders wichtig. Dokumentieren Sie, welche Schritte die Pipeline durchläuft. Wenn ein Prüfer fragt „Wie ist diese Empfehlung entstanden?", müssen Sie jeden Schritt nachvollziehbar machen können.

---

## 🚀 Starten Sie hier — Ihr erster Schritt am Montag

> **Nehmen Sie einen bestehenden Prompt aus Kapitel 01 (z.B. die Kreditbewertung aus Tutorial 01-05 oder die Meeting-Zusammenfassung aus Tutorial 01-06) und überführen Sie ihn in das Drei-Schichten-Modell: XML-Rahmen für die Gliederung, Markdown für die Anweisungen, JSON für die Daten. Vergleichen Sie das Ergebnis mit dem Original.**

**Die Reihenfolge zum Reinwachsen:**
1. 🥇 **Woche 1:** Einen bestehenden Prompt in XML-Rahmen + Markdown umbauen (ohne JSON)
2. 🥈 **Woche 2:** JSON-Daten-Input hinzufügen (Kundendaten als JSON statt Fließtext)
3. 🥉 **Woche 3:** JSON-Ausgabe-Schema hinzufügen (strukturierter Output)
4. 🏅 **Woche 4:** Einen System-Prompt für einen KI-Assistenten bauen (Muster 3)
5. 🎓 **Fortgeschritten:** Pipeline entwerfen (3-Schritte-Kette für einen kompletten Prozess)

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Vom Markdown-Prompt zum Drei-Schichten-Prompt

**Aufgabe:** Überführen Sie den folgenden Markdown-Prompt in das Drei-Schichten-Modell:

```
Du bist ein Kundenberater der Volksbank. 
Erstelle einen Gesprächsleitfaden für ein 
Beratungsgespräch mit folgendem Kunden: 
45 Jahre, Angestellter, 3.800€ netto, verheiratet, 
2 Kinder, will Baufinanzierung 280.000€, 
hat 35.000€ Eigenkapital. 
Beachte: Cross-Selling-Potenzial prüfen, 
Zinsbindungsende ansprechen, KfW-Förderung 
erwähnen. Antworte strukturiert mit Gesprächsphasen.
```

**Ihre Aufgabe:**
1. Identifizieren Sie die Abschnitte: Was ist Rolle? Was ist Kontext? Was sind Regeln? Was sind Daten?
2. Erstellen Sie XML-Tags für jeden Abschnitt
3. Schreiben Sie die Anweisungen in Markdown innerhalb der Tags
4. Überführen Sie die Kundendaten in JSON innerhalb von `<daten>`
5. Definieren Sie ein JSON-Ausgabe-Schema für den Gesprächsleitfaden

### Hands-on 2: System-Prompt bauen

**Aufgabe:** Entwerfen Sie einen System-Prompt für einen KI-Assistenten „**MeetingHelper**", der:
- Meeting-Transkripte zusammenfasst
- Aufgaben extrahiert (als JSON-Array)
- Follow-up-E-Mails formuliert
- Bei unklaren Punkten nachfragt

Nutzen Sie das System-Prompt-Muster aus Schritt 4. Bauen Sie mindestens ein `<beispiel>` ein.

### Hands-on 3: Modellvergleich — Wer versteht die Kombination besser?

**Aufgabe:** Geben Sie den Kreditprüfungs-Prompt aus Schritt 2 (Drei-Schichten-Version) in **zwei verschiedene Modelle** ein.

**Vergleichen Sie:**
- Hält sich die KI an alle XML-Abschnitte?
- Ist das JSON-Output valide?
- Werden die Markdown-Regeln beachtet (z.B. Kapitaldienstgrenze 35%)?
- Welches Modell liefert die nützlichere Bewertung?
- Bei welchem Modell müssen Sie nachbessern?

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **Drei-Schichten-Modell** | Architektur-Prinzip für komplexe Prompts: XML als Rahmen (Struktur), Markdown als Inhalt (Anweisungen), JSON als Payload (Daten). Jedes Format wird dort eingesetzt, wo es am stärksten ist |
| **Modularer Baustein** | Ein austauschbarer Prompt-Abschnitt in einem XML-Tag (z.B. `<kontext>`, `<regeln>`), der unabhängig vom Rest geändert oder ersetzt werden kann. Wie ein Formular-Modul im Kernbanksystem |
| **System-Prompt** | Die dauerhafte Anweisung, die definiert, wie sich ein KI-Assistent in jedem Gespräch verhält. Enthält Identität, Fähigkeiten, Regeln und Ausgabeformat. Wird einmal konfiguriert und gilt dann für alle Interaktionen |
| **Prompt-Pipeline** | Eine Kette von 2-5 Prompts, bei denen das Ergebnis eines Prompts als Input für den nächsten dient. Zerlegt komplexe Aufgaben in überschaubare Einzelschritte |
| **Prompt-Kette** | Synonym für Prompt-Pipeline. Betont den sequentiellen Charakter: Schritt 1 → Schritt 2 → Schritt 3 |
| **Ausgabe-Schema** | Ein JSON-Template, das der KI zeigt, wie ihre Antwort exakt aussehen soll. Definiert Feldnamen, Datentypen und erlaubte Werte. Der „Vertrag" zwischen Prompt-Ersteller und KI |
| **Escaping** | Das Kennzeichnen von Sonderzeichen, damit sie nicht als Format-Steuerzeichen interpretiert werden. Beispiel: `\"` in JSON für ein Anführungszeichen innerhalb eines Textwertes |
| **Few-Shot-Beispiel** | Ein konkretes Eingabe-Ausgabe-Paar im Prompt, das der KI zeigt, wie die Antwort aussehen soll. In kombinierten Prompts: Innerhalb von `<beispiele>`-Tags |
| **Custom GPT** | Ein personalisierter ChatGPT-Assistent mit eigenem System-Prompt, der für eine bestimmte Aufgabe konfiguriert ist. System-Prompts aus diesem Tutorial sind die Grundlage für Custom GPTs (→ Kapitel 03) |
| **Meta-Format Reasoning** | Fortgeschrittene Technik (2025), bei der KI-Systeme dynamisch zwischen Formaten wechseln: JSON für Datenverarbeitung, XML für Reasoning, Markdown für menschenlesbare Zusammenfassungen |
| **IKT-Verzeichnis** | Verzeichnis aller Informations- und Kommunikationstechnologie-Systeme einer Bank, vorgeschrieben durch DORA (Digital Operational Resilience Act). KI-Assistenten mit System-Prompts gehören dokumentiert |
| **Versionierung** | Kennzeichnung von System-Prompts mit Version und Änderungsdatum (z.B. `version="1.2"`). Ermöglicht Nachvollziehbarkeit bei Audits und Rückkehr zu früheren Versionen |

---

