# JSON für Ein- und Ausgabe

**Daten rein, Daten raus — wie JSON Ihre KI-Ergebnisse maschinenlesbar und weiterverarbeitbar macht**

---

## Warum dieses Tutorial?

In Tutorial 02-01 haben Sie Markdown kennengelernt — das Werkzeug für lesbare, schnell erstellte Prompts. In Tutorial 02-02 haben Sie XML-Tags gelernt — das Werkzeug für hierarchische, modulare Prompt-Strukturen. Beide sind für *Menschen* optimiert: Sie tippen einen Prompt, die KI antwortet, Sie lesen das Ergebnis.

Aber was, wenn Sie das Ergebnis nicht nur lesen, sondern **weiterverarbeiten** wollen?

- Sie lassen die KI 20 Kreditanfragen bewerten — und wollen die Ergebnisse direkt in eine Excel-Tabelle importieren.
- Sie erstellen Kundenprofile mit KI-Unterstützung — und wollen sie ins CRM-System übertragen.
- Sie analysieren 10 Filialen — und wollen die Kennzahlen automatisch in ein Dashboard einfließen lassen.
- Sie lassen Vertriebsideen generieren — und wollen sie strukturiert in ein Projektmanagement-Tool überführen.

In all diesen Fällen ist Fließtext oder Markdown unbrauchbar. Sie bräuchten jemanden, der die KI-Antwort manuell abschreibt, in die richtige Spalte einträgt und dabei keine Fehler macht. Das dauert Stunden — und vernichtet die Zeitersparnis, die die KI gebracht hat.

**JSON löst dieses Problem.** JSON ist ein Datenformat, das sowohl Menschen als auch Maschinen lesen können. Wenn Sie die KI bitten, in JSON zu antworten, bekommen Sie strukturierte Daten zurück, die Sie direkt in Excel, CRM-Systeme oder andere Tools importieren können.

> **Volksbank-Analogie:** Stellen Sie sich vor, Sie fragen Ihren Kollegen: „Wie bewertest du diese 5 Kreditanfragen?" Wenn er auf Fließtext antwortet, bekommen Sie fünf Absätze, die Sie durchlesen, verstehen und manuell in Ihre Tabelle übertragen müssen. Wenn er stattdessen ein ausgefülltes **Formular** zurückgibt — mit definierten Feldern für Risikobewertung, Empfehlung und Begründung — können Sie die Daten sofort übernehmen. JSON ist dieses Formular.

**Was Sie nach diesem Tutorial können:**

- Verstehen, was JSON ist und wie es aufgebaut ist — ohne Programmieren
- Strukturierte Daten per JSON an die KI übergeben (JSON-Input)
- Die KI dazu bringen, in JSON zu antworten (JSON-Output)
- KI-Ergebnisse in Excel, Google Sheets oder andere Tools importieren
- Mehrere Datensätze gleichzeitig verarbeiten lassen (Batch-Verarbeitung)
- Wissen, wann JSON besser ist als Markdown oder XML — und umgekehrt

---

## Schritt 1: Was ist JSON — und warum sollte ich das als Bankmitarbeiter kennen?

### JSON in 60 Sekunden

JSON steht für **JavaScript Object Notation**. Lassen Sie sich vom Namen nicht abschrecken — Sie müssen kein JavaScript können. JSON ist einfach eine Art, Daten aufzuschreiben: mit geschweiften Klammern `{}`, eckigen Klammern `[]`, Doppelpunkten `:` und Anführungszeichen `""`.

Ein Beispiel sagt mehr als jede Definition:

```json
{
  "name": "Kunde A",
  "alter": 38,
  "beruf": "Angestellter",
  "nettoeinkommen": 4800,
  "vorhaben": "Baufinanzierung",
  "kreditbetrag": 395000
}
```

Das war's. Sechs Informationen, klar strukturiert. Jede Information hat einen **Namen** (links vom Doppelpunkt) und einen **Wert** (rechts vom Doppelpunkt).

### Die vier Regeln von JSON

| Regel | Beispiel | Erklärung |
|---|---|---|
| Geschweifte Klammern umschließen ein Objekt | `{ ... }` | Ein „Ding" mit Eigenschaften (ein Kunde, eine Anfrage, eine Bewertung) |
| Eckige Klammern umschließen eine Liste | `[ ..., ..., ... ]` | Mehrere gleichartige Dinge (5 Kunden, 3 Szenarien) |
| Schlüssel-Wert-Paare mit Doppelpunkt | `"alter": 38` | Links: Name des Feldes. Rechts: der Wert |
| Komma zwischen Einträgen | `"alter": 38, "beruf": "Angestellter"` | Trennt einzelne Felder voneinander |

### Das ist KEIN Programmieren!

Genau wie bei XML (Tutorial 02-02): JSON in Prompts ist kein Code. Sie tippen es ins Chat-Fenster wie jeden anderen Text. Die geschweiften Klammern `{}` und eckigen Klammern `[]` sind nur Markierungen — wie Tabellenrahmen in Word.

```
┌─────────────────────────────────────────────────────────────────┐
│        📊 JSON = Ausgefülltes Formular                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  📝 Fließtext:                                                  │
│  „Der Kunde ist 38 Jahre alt, verdient 4.800€ netto und        │
│  möchte eine Baufinanzierung über 395.000€."                   │
│                                                                 │
│  📋 JSON:                                                       │
│  {                                                             │
│    "alter": 38,                                                │
│    "nettoeinkommen": 4800,                                     │
│    "vorhaben": "Baufinanzierung",                              │
│    "kreditbetrag": 395000                                      │
│  }                                                             │
│                                                                 │
│  → Gleiche Information! Aber JSON hat:                         │
│    • Eindeutige Feldnamen (kein Raten, was was ist)            │
│    • Zahlen ohne €-Zeichen (maschinenlesbar)                   │
│    • Feste Struktur (immer gleicher Aufbau)                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** JSON ist wie eine Excel-Zeile, nur als Text geschrieben. `"alter": 38` ist wie Spalte B = 38. `"beruf": "Angestellter"` ist wie Spalte C = Angestellter. Der Unterschied zu einer echten Excel-Tabelle: JSON können Sie in einen KI-Prompt kopieren — und die KI kann JSON zurückgeben, das Sie in Excel importieren.

---

## Schritt 2: JSON als Eingabe — Daten strukturiert an die KI übergeben

### Warum nicht einfach Fließtext?

Bei einem einzelnen Kunden funktioniert Fließtext. Bei fünf Kunden wird es unübersichtlich. Bei zwanzig ist es ein Albtraum. JSON löst das Problem durch einheitliche Struktur.

### Praxisbeispiel: Fünf Kunden gleichzeitig bewerten

**Ohne JSON (Fließtext):**

```
Bewerte folgende Kunden: Kunde 1 ist 34, Angestellter, 
verdient 3.800€ netto, will 25.000€ Ratenkredit. 
Kunde 2 ist 52, selbständig seit 8 Jahren, 
Jahreseinkommen 72.000€, will 100.000€ Betriebsmittel. 
Kunde 3 ist 28, Berufseinsteigerin, 2.600€ netto, 
will 280.000€ Baufinanzierung. Kunde 4 ist 45, 
verbeamtet, 4.100€ netto, will 15.000€ für ein Auto. 
Kunde 5 ist 61, Rentnerin ab nächstes Jahr, 1.900€ 
Rente, will 30.000€ Modernisierungskredit.
```

→ Unübersichtlich. Wer hat welches Einkommen? Was ist Netto, was Jahreseinkommen? Die KI muss raten.

**Mit JSON:**

```
Bewerte die folgenden Kreditanfragen. Für jede Anfrage: 
Risikobewertung (niedrig/mittel/hoch), Empfehlung 
(genehmigen/prüfen/ablehnen), Begründung (1 Satz).

Anfragen:

[
  {
    "id": 1,
    "alter": 34,
    "beruf": "Angestellter, unbefristet",
    "einkommen_netto_monat": 3800,
    "kreditart": "Ratenkredit",
    "betrag": 25000,
    "laufzeit_monate": 48,
    "sicherheiten": "keine"
  },
  {
    "id": 2,
    "alter": 52,
    "beruf": "Selbständig, 8 Jahre",
    "einkommen_jahresueberschuss": 72000,
    "kreditart": "Betriebsmittelkredit",
    "betrag": 100000,
    "sicherheiten": "Grundschuld Gewerbeimmobilie, freier Wert 140.000€"
  },
  {
    "id": 3,
    "alter": 28,
    "beruf": "Berufseinsteigerin, befristet",
    "einkommen_netto_monat": 2600,
    "kreditart": "Baufinanzierung",
    "betrag": 280000,
    "sicherheiten": "Eigenkapital 40.000€"
  },
  {
    "id": 4,
    "alter": 45,
    "beruf": "Beamter, verbeamtet",
    "einkommen_netto_monat": 4100,
    "kreditart": "Konsumentenkredit",
    "betrag": 15000,
    "laufzeit_monate": 36,
    "sicherheiten": "keine"
  },
  {
    "id": 5,
    "alter": 61,
    "beruf": "Rentnerin ab 2027",
    "einkommen_rente_monat": 1900,
    "kreditart": "Modernisierungskredit",
    "betrag": 30000,
    "sicherheiten": "Grundschuld Eigenheim, freier Wert 180.000€"
  }
]
```

### Was ist besser — und warum?

| Kriterium | Fließtext | JSON |
|---|---|---|
| **Eindeutigkeit** | „72.000€" — netto? brutto? Jahresüberschuss? | `"einkommen_jahresueberschuss": 72000` — unmissverständlich |
| **Vollständigkeit** | Fehlende Felder fallen nicht auf | Fehlende Felder sind sichtbar (Kunde 2 hat keine `laufzeit_monate`) |
| **Skalierbarkeit** | 5 Kunden → unlesbar. 20 Kunden → unmöglich | 5 oder 50 Kunden → gleiche Struktur |
| **KI-Verarbeitung** | KI muss Freitext parsen und raten | KI erkennt sofort die Datenstruktur |
| **Ergebnis-Konsistenz** | Jeder Kunde wird anders beschrieben | Jeder Kunde hat dieselben Felder → Ergebnis vergleichbar |

> **Praxis-Tipp:** Sie müssen JSON nicht von Hand tippen. Wenn Sie Ihre Kundendaten in Excel haben, können Sie sie mit einem einfachen Online-Tool (z.B. „CSV to JSON Converter") in JSON umwandeln. In 30 Sekunden.

---

## Schritt 3: JSON als Ausgabe — Die KI strukturiert antworten lassen

Das ist die mächtigste Anwendung von JSON in Prompts: **Die KI antwortet nicht in Fließtext, sondern in strukturierten Daten.**

### Warum ist das so wertvoll?

Normale KI-Antwort (Fließtext):

```
Kunde 1 hat ein mittleres Risiko. Der unbefristete 
Arbeitsvertrag ist positiv, aber die fehlenden Sicherheiten 
geben zu denken. Ich empfehle eine genauere Prüfung...

Kunde 2 zeigt ein niedriges Risiko. Der lange 
Geschäftsbestand und die Grundschuld bieten gute 
Absicherung...
```

→ Um das in eine Tabelle zu bekommen, müssen Sie jeden Absatz lesen, die relevanten Infos extrahieren und manuell eintippen. Bei 5 Kunden: 15 Minuten. Bei 20 Kunden: eine Stunde.

KI-Antwort in JSON:

```json
[
  {
    "id": 1,
    "risiko": "mittel",
    "empfehlung": "prüfen",
    "begruendung": "Unbefristeter Arbeitsvertrag positiv, fehlende Sicherheiten erhöhen Risiko",
    "staerken": ["stabiles Einkommen", "geringe Kreditsumme"],
    "schwaechen": ["keine Sicherheiten", "bestehender Autokredit"]
  },
  {
    "id": 2,
    "risiko": "niedrig",
    "empfehlung": "genehmigen",
    "begruendung": "Langjährig etabliertes Unternehmen mit guter Besicherung",
    "staerken": ["8 Jahre Geschäftsbestand", "freie Grundschuld 140.000€"],
    "schwaechen": ["Selbständigkeit als Grundrisiko"]
  }
]
```

→ Das können Sie direkt in Excel einfügen. Keine manuelle Nacharbeit.

### Wie bringe ich die KI dazu, in JSON zu antworten?

Der Schlüssel: **Zeigen Sie der KI genau, wie die Antwort aussehen soll.** Geben Sie ein Beispiel-Schema mit.

### Prompt-Vorlage 1: JSON-Output erzwingen

```
# ROLLE
Kreditanalyst einer Genossenschaftsbank.

# AUFGABE
Bewerte die folgenden Kreditanfragen und gib deine 
Bewertung **ausschließlich als JSON** zurück. 
Kein Fließtext, keine Erklärungen — nur JSON.

# AUSGABE-SCHEMA
Antworte exakt in diesem Format:

[
  {
    "id": <Anfrage-ID>,
    "risiko": "<niedrig|mittel|hoch|kritisch>",
    "empfehlung": "<genehmigen|prüfen|ablehnen>",
    "begruendung": "<1 Satz>",
    "max_rate_empfohlen": <Zahl in Euro>,
    "kapitaldienstfaehigkeit_prozent": <Zahl>
  }
]

# REGELN
- Antwort ist NUR JSON — kein Text davor oder danach
- Felder exakt wie im Schema benennen
- Risiko-Werte nur aus der vorgegebenen Liste
- Beträge als Zahlen ohne €-Zeichen
- Kapitaldienstfähigkeit = Rate / Haushaltsnetto × 100

# ANFRAGEN
[Hier JSON-Daten der Kunden einfügen]
```

### Warum das Beispiel-Schema entscheidend ist

Ohne Schema antwortet die KI in ihrem eigenen Format — mal mit anderen Feldnamen, mal mit zusätzlichen Feldern, mal mit fehlendem Komma. **Das Schema ist der Vertrag:** „So sieht deine Antwort aus. Genau so. Keine Abweichung."

```
┌─────────────────────────────────────────────────────────────────┐
│        📋 Schema = Vertrag zwischen Ihnen und der KI            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ❌ OHNE Schema:                                                │
│  KI antwortet: „Der Kunde hat ein mittleres Risiko..."         │
│  Oder: { "risk": "medium", "recommendation": "check" }         │
│  Oder: { "Risikobewertung": "MITTEL" }                         │
│  → Jedes Mal anders. Nicht automatisierbar.                    │
│                                                                 │
│  ✅ MIT Schema:                                                 │
│  KI antwortet: { "risiko": "mittel", "empfehlung": "prüfen" } │
│  → Immer gleich. Direkt weiterverarbeitbar.                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** Das Schema ist wie das Pflichtenheft für einen Prüfbericht: „Feld 1: Risikokategorie (nur: niedrig/mittel/hoch). Feld 2: Empfehlung (nur: genehmigen/prüfen/ablehnen). Feld 3: Begründung (max. 1 Satz)." Wenn der Prüfer sich an das Pflichtenheft hält, kann jeder Sachbearbeiter den Bericht sofort weiterverarbeiten. Ohne Pflichtenheft schreibt jeder Prüfer anders.

---

## Schritt 4: JSON-Ergebnisse in Excel importieren

Der praktischste Nutzen von JSON-Output: **direkter Import in Excel oder Google Sheets.** So geht's:

### Methode 1: Copy-Paste + Power Query (Excel)

1. Kopieren Sie die JSON-Antwort der KI
2. Öffnen Sie Excel → Reiter „Daten" → „Daten abrufen" → „Aus anderen Quellen" → „Leere Abfrage"
3. Im Power Query Editor: „Erweiterter Editor" → Einfügen: `= Json.Document("` + Ihr JSON + `")`
4. Excel wandelt das JSON automatisch in Spalten und Zeilen um

### Methode 2: Online-Konverter (am schnellsten)

1. Kopieren Sie die JSON-Antwort
2. Öffnen Sie einen kostenlosen Online-Konverter (z.B. „JSON to CSV Converter")
3. JSON einfügen → „Convert" klicken → CSV herunterladen
4. CSV in Excel öffnen — fertig

### Methode 3: Google Sheets (am einfachsten)

1. In Google Sheets: Erweiterungen → Apps Script
2. Einfügen:
```
function importJSON() {
  var json = '[Ihr JSON hier]';
  var data = JSON.parse(json);
  var sheet = SpreadsheetApp.getActiveSheet();
  // Überschriften
  var headers = Object.keys(data[0]);
  sheet.getRange(1, 1, 1, headers.length).setValues([headers]);
  // Daten
  var rows = data.map(function(obj) {
    return headers.map(function(h) { return obj[h] || ""; });
  });
  sheet.getRange(2, 1, rows.length, headers.length).setValues(rows);
}
```
3. Ausführen → Ihre Tabelle wird automatisch befüllt

### Methode 4: KI bitten, eine Tabelle zu erstellen (für Nicht-Techniker)

Wenn Ihnen die obigen Methoden zu technisch sind — kein Problem. Nutzen Sie einen **Zwei-Schritt-Prozess:**

**Schritt 1:** KI generiert JSON (wie in Schritt 3)
**Schritt 2:** Neuer Prompt:

```
Wandle das folgende JSON in eine Markdown-Tabelle um, 
die ich in Excel kopieren kann:

[HIER JSON EINFÜGEN]
```

Die KI liefert eine Tabelle, die Sie direkt in Excel kopieren können (Strg+C → Strg+V). Kein Power Query, kein Apps Script.

> **Praxis-Tipp:** Methode 4 ist der pragmatische Weg. Ja, Sie „verschwenden" einen KI-Aufruf für die Umwandlung. Aber das kostet 0,01 € und dauert 10 Sekunden. Der Vorteil: Sie müssen kein neues Tool lernen.

---

## Schritt 5: Praxisbeispiel — Filialanalyse mit JSON-Pipeline

Ein komplettes Beispiel von Anfang bis Ende: Sie wollen 5 Filialen Ihrer Bank nach Kennzahlen bewerten lassen.

### Schritt 5a: Daten als JSON-Input vorbereiten

```json
[
  {
    "filiale": "Soest Zentrum",
    "mitarbeiter": 18,
    "kundenfrequenz_tag": 145,
    "umsatz_2025_mio": 2.8,
    "kosten_2025_mio": 2.1,
    "kundenzufriedenheit_score": 4.2,
    "digitalisierungsgrad_prozent": 65
  },
  {
    "filiale": "Werl",
    "mitarbeiter": 12,
    "kundenfrequenz_tag": 88,
    "umsatz_2025_mio": 1.9,
    "kosten_2025_mio": 1.6,
    "kundenzufriedenheit_score": 4.5,
    "digitalisierungsgrad_prozent": 45
  },
  {
    "filiale": "Wickede",
    "mitarbeiter": 6,
    "kundenfrequenz_tag": 32,
    "umsatz_2025_mio": 0.7,
    "kosten_2025_mio": 0.8,
    "kundenzufriedenheit_score": 4.7,
    "digitalisierungsgrad_prozent": 30
  },
  {
    "filiale": "Bad Sassendorf",
    "mitarbeiter": 8,
    "kundenfrequenz_tag": 55,
    "umsatz_2025_mio": 1.2,
    "kosten_2025_mio": 1.0,
    "kundenzufriedenheit_score": 4.3,
    "digitalisierungsgrad_prozent": 55
  },
  {
    "filiale": "Möhnesee",
    "mitarbeiter": 4,
    "kundenfrequenz_tag": 18,
    "umsatz_2025_mio": 0.4,
    "kosten_2025_mio": 0.5,
    "kundenzufriedenheit_score": 4.8,
    "digitalisierungsgrad_prozent": 20
  }
]
```

### Schritt 5b: Prompt mit JSON-Input und JSON-Output

```
# ROLLE
Strategieberater für Filialoptimierung einer 
Genossenschaftsbank.

# AUFGABE
Analysiere die folgenden 5 Filialen und erstelle eine 
Bewertung. Antworte **ausschließlich als JSON**.

# AUSGABE-SCHEMA

[
  {
    "filiale": "<Name>",
    "ergebnis_2025": "<Gewinn oder Verlust in Mio €>",
    "cost_income_ratio": "<Kosten/Umsatz in Prozent>",
    "effizienz_pro_mitarbeiter": "<Umsatz/Mitarbeiter in T€>",
    "stärken": ["<Stärke 1>", "<Stärke 2>"],
    "schwächen": ["<Schwäche 1>", "<Schwäche 2>"],
    "handlungsempfehlung": "<1-2 Sätze>",
    "priorität": "<hoch|mittel|niedrig>",
    "potential_digitalisierung": "<hoch|mittel|niedrig>"
  }
]

# REGELN
- Ergebnis = Umsatz minus Kosten
- Cost-Income-Ratio = Kosten / Umsatz × 100
- Effizienz = Umsatz / Mitarbeiter × 1000 (in T€)
- Antwort ist NUR JSON — kein Fließtext
- Sortiert nach Priorität (hoch zuerst)

# FILIALDATEN

[Hier die JSON-Daten von oben einfügen]
```

### Schritt 5c: KI-Ergebnis (Beispiel)

```json
[
  {
    "filiale": "Wickede",
    "ergebnis_2025": -0.1,
    "cost_income_ratio": 114.3,
    "effizienz_pro_mitarbeiter": 116.7,
    "stärken": ["Höchste Kundenzufriedenheit (4.7)", "Kleine, agile Einheit"],
    "schwächen": ["Verlustbringend", "Niedrigster Digitalisierungsgrad (30%)"],
    "handlungsempfehlung": "Filiale in Beratungsstützpunkt umwandeln oder mit Bad Sassendorf zusammenlegen. Digitalisierung priorisieren.",
    "priorität": "hoch",
    "potential_digitalisierung": "hoch"
  },
  {
    "filiale": "Möhnesee",
    "ergebnis_2025": -0.1,
    "cost_income_ratio": 125.0,
    "effizienz_pro_mitarbeiter": 100.0,
    "stärken": ["Beste Kundenzufriedenheit (4.8)", "Regionale Verankerung"],
    "schwächen": ["Verlustbringend", "Niedrigste Kundenfrequenz (18/Tag)", "Geringe Digitalisierung (20%)"],
    "handlungsempfehlung": "Öffnungszeiten reduzieren auf 3 Tage/Woche, SB-Terminal installieren, Beratung nach Termin.",
    "priorität": "hoch",
    "potential_digitalisierung": "hoch"
  },
  {
    "filiale": "Werl",
    "ergebnis_2025": 0.3,
    "cost_income_ratio": 84.2,
    "effizienz_pro_mitarbeiter": 158.3,
    "stärken": ["Profitabel", "Gute Kundenzufriedenheit (4.5)"],
    "schwächen": ["Digitalisierungsgrad unter Durchschnitt (45%)"],
    "handlungsempfehlung": "Digitalisierung vorantreiben, Online-Terminbuchung einführen.",
    "priorität": "mittel",
    "potential_digitalisierung": "mittel"
  },
  {
    "filiale": "Bad Sassendorf",
    "ergebnis_2025": 0.2,
    "cost_income_ratio": 83.3,
    "effizienz_pro_mitarbeiter": 150.0,
    "stärken": ["Profitabel", "Guter Digitalisierungsgrad (55%)"],
    "schwächen": ["Mittlere Kundenzufriedenheit"],
    "handlungsempfehlung": "Stabil halten, ggf. Wickede-Kunden integrieren.",
    "priorität": "niedrig",
    "potential_digitalisierung": "niedrig"
  },
  {
    "filiale": "Soest Zentrum",
    "ergebnis_2025": 0.7,
    "cost_income_ratio": 75.0,
    "effizienz_pro_mitarbeiter": 155.6,
    "stärken": ["Höchster Umsatz", "Beste Cost-Income-Ratio", "Höchster Digitalisierungsgrad (65%)"],
    "schwächen": ["Niedrigste Kundenzufriedenheit (4.2)"],
    "handlungsempfehlung": "Kundenzufriedenheit verbessern: Wartezeiten reduzieren, Service-Qualität prüfen.",
    "priorität": "niedrig",
    "potential_digitalisierung": "niedrig"
  }
]
```

### Schritt 5d: In Excel importieren

Dieses JSON → CSV-Konverter → Excel-Tabelle. Ergebnis:

| Filiale | Ergebnis 2025 | CIR | Effizienz/MA | Priorität |
|---------|--------------|-----|-------------|-----------|
| Wickede | -0,1 Mio | 114% | 117 T€ | hoch |
| Möhnesee | -0,1 Mio | 125% | 100 T€ | hoch |
| Werl | +0,3 Mio | 84% | 158 T€ | mittel |
| Bad Sassendorf | +0,2 Mio | 83% | 150 T€ | niedrig |
| Soest Zentrum | +0,7 Mio | 75% | 156 T€ | niedrig |

**Gesamtzeit:** 10 Minuten (Daten vorbereiten + Prompt + Import). Ohne KI: Ein Berater hätte einen halben Tag für die gleiche Analyse gebraucht.

> **Volksbank-Analogie:** Das ist wie ein automatischer Filial-Check-up. Sie füttern die Kennzahlen rein, die KI liefert eine strukturierte Diagnose — mit Stärken, Schwächen und konkreten Empfehlungen. Und weil alles in JSON ist, landet es direkt in Ihrer Controlling-Tabelle, statt dass jemand handschriftliche Notizen abtippen muss.

---

## Schritt 6: Verschachtelte JSON-Strukturen — Wenn Daten komplex werden

Manchmal haben Ihre Daten Unterkategorien. Ein Kunde hat mehrere Konten. Eine Filiale hat mehrere Abteilungen. Ein Kredit hat mehrere Sicherheiten. JSON kann das mit **Verschachtelung** abbilden.

### Praxisbeispiel: Kunde mit mehreren Produkten

```json
{
  "kunde_id": "K-2026-0042",
  "segment": "Privatkunde",
  "alter": 45,
  "beziehung_seit": 2008,
  "produkte": [
    {
      "typ": "Girokonto",
      "status": "aktiv",
      "umsatz_monat": 4200
    },
    {
      "typ": "Baufinanzierung",
      "status": "aktiv",
      "restschuld": 185000,
      "rate_monat": 1250,
      "zinsbindung_bis": "2028-06"
    },
    {
      "typ": "Depot",
      "status": "aktiv",
      "volumen": 32000,
      "letzte_transaktion": "2026-01-15"
    }
  ],
  "cross_selling_potential": {
    "altersvorsorge": "hoch",
    "versicherung": "mittel",
    "bausparvertrag": "hoch_wegen_zinsbindungsende_2028"
  }
}
```

### Prompt dazu:

```
# AUFGABE
Analysiere das folgende Kundenprofil und erstelle 
einen Beratungsvorschlag für das nächste Kundengespräch.

# FOKUS
- Welche Cross-Selling-Chancen sind am vielversprechendsten?
- Beachte: Zinsbindung der Baufinanzierung endet 2028
- Was sollte der Berater ansprechen — in welcher Reihenfolge?

# KUNDENPROFIL
[Hier das JSON einfügen]

# AUSGABE-SCHEMA
{
  "gespraechsvorbereitung": {
    "prioritaet_1": {
      "thema": "<Hauptthema>",
      "argumentation": "<2-3 Sätze Gesprächsführung>",
      "produkt": "<konkretes Produkt>",
      "dringlichkeit": "<hoch|mittel|niedrig>"
    },
    "prioritaet_2": { ... },
    "prioritaet_3": { ... }
  },
  "eisbrecher": "<Gesprächseinstieg, 1 Satz>",
  "achtung": "<Worauf der Berater besonders achten sollte>"
}
```

> **Praxis-Tipp:** Dieses Muster — Kundenprofil als JSON rein, Gesprächsvorbereitung als JSON raus — ist ein idealer Kandidat für einen Custom GPT (→ Kapitel 03). Einmal aufgesetzt, können Berater vor jedem Kundengespräch das Profil einfügen und in 30 Sekunden eine strukturierte Gesprächsvorbereitung erhalten.

---

## Schritt 7: Häufige JSON-Fehler — und wie Sie sie vermeiden

JSON ist weniger fehlertolerant als Markdown oder XML. Ein fehlendes Komma oder ein falsches Anführungszeichen kann das Format zerstören. Hier die häufigsten Fehler:

### Die 5 häufigsten JSON-Fehler

| Fehler | Beispiel (falsch) | Richtig | Tipp |
|---|---|---|---|
| **Fehlendes Komma** | `"alter": 38 "beruf": "..."` | `"alter": 38, "beruf": "..."` | Komma nach jedem Wert — außer dem letzten |
| **Letztes Komma zu viel** | `"alter": 38, "beruf": "...",` | `"alter": 38, "beruf": "..."` | Kein Komma nach dem letzten Eintrag |
| **Einfache statt doppelte Anführungszeichen** | `{'alter': 38}` | `{"alter": 38}` | JSON verwendet immer `"doppelte"` |
| **Text ohne Anführungszeichen** | `"beruf": Angestellter` | `"beruf": "Angestellter"` | Text-Werte immer in `""`. Zahlen ohne |
| **Euro-Zeichen in Zahlen** | `"betrag": "395.000€"` | `"betrag": 395000` | Zahlen ohne €, ohne Punkt als Tausender-Trenner |

### Was passiert, wenn die KI fehlerhaftes JSON liefert?

Manchmal antwortet die KI mit fast-richtigem JSON — ein fehlendes Komma, eine fehlende Klammer. Zwei Lösungen:

**Lösung 1: Nachfragen**
```
Dein JSON hat einen Syntaxfehler. Bitte korrigiere es 
und gib es erneut aus — nur das korrigierte JSON, 
kein Fließtext.
```

**Lösung 2: JSON-Validator nutzen**
Kopieren Sie das JSON in einen Online-Validator (z.B. jsonlint.com). Der zeigt Ihnen genau, wo der Fehler ist.

> **Praxis-Tipp:** Wenn die KI regelmäßig fehlerhaftes JSON liefert, fügen Sie diese Zeile in Ihren Prompt ein: `Stelle sicher, dass dein JSON syntaktisch korrekt ist. Prüfe Kommas, Klammern und Anführungszeichen.` — Das reduziert Fehler deutlich.

---

## Schritt 8: Wann JSON, wann XML, wann Markdown?

Jetzt kennen Sie alle drei Formate. Hier die finale Entscheidungshilfe:

```
┌─────────────────────────────────────────────────────────────────┐
│       🗺️ Welches Format für welchen Zweck?                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Was ist Ihre Hauptanforderung?                                │
│                                                                 │
│  ├── 📝 „Ich will einen Prompt schnell schreiben"              │
│  │   └── MARKDOWN (Tutorial 02-01)                             │
│  │       Schnell, lesbar, für 80% aller Fälle                  │
│  │                                                              │
│  ├── 🏗️ „Ich brauche modulare, hierarchische Struktur"         │
│  │   └── XML (Tutorial 02-02)                                  │
│  │       System-Prompts, verschachtelte Regeln, Chatbots       │
│  │                                                              │
│  ├── 📊 „Ich will Daten rein- und rausgeben"                   │
│  │   └── JSON (dieses Tutorial)                                │
│  │       Batch-Verarbeitung, Excel-Export, Automatisierung      │
│  │                                                              │
│  └── 🔧 „Ich will alles kombinieren"                           │
│      └── KOMBINATION (Tutorial 02-04)                          │
│          Markdown für Anweisungen, XML für Struktur,           │
│          JSON für Daten                                         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Direkt-Vergleich: Dasselbe Problem, drei Formate

**Aufgabe:** Kundenprofil an die KI übergeben.

**Markdown:**
```
## KUNDENDATEN
- Name: Kunde A
- Alter: 38
- Einkommen: 4.800 € netto
- Vorhaben: Baufinanzierung 395.000 €
```

**XML:**
```xml
<kundenprofil>
  <name>Kunde A</name>
  <alter>38</alter>
  <einkommen typ="netto" waehrung="EUR">4800</einkommen>
  <vorhaben>
    <art>Baufinanzierung</art>
    <betrag>395000</betrag>
  </vorhaben>
</kundenprofil>
```

**JSON:**
```json
{
  "name": "Kunde A",
  "alter": 38,
  "einkommen_netto": 4800,
  "vorhaben": "Baufinanzierung",
  "kreditbetrag": 395000
}
```

| Kriterium | Markdown | XML | JSON |
|---|---|---|---|
| **Lesbarkeit für Menschen** | ⭐⭐⭐ Sehr gut | ⭐⭐ Gut | ⭐⭐ Gut |
| **Maschinenlesbarkeit** | ⭐ Schlecht | ⭐⭐ Gut | ⭐⭐⭐ Sehr gut |
| **Mehrere Datensätze** | ⭐ Unübersichtlich | ⭐⭐ Gut (mit IDs) | ⭐⭐⭐ Ideal (Array) |
| **Verschachtelung** | ⭐ Schwierig | ⭐⭐⭐ Sehr gut | ⭐⭐⭐ Sehr gut |
| **Schnell getippt** | ⭐⭐⭐ Am schnellsten | ⭐⭐ Mittel | ⭐⭐ Mittel |
| **Excel-Import** | ⭐ Nur per Copy-Paste | ⭐⭐ Möglich | ⭐⭐⭐ Direkt importierbar |
| **Fehlertoleranz** | ⭐⭐⭐ Sehr tolerant | ⭐⭐ Tolerant | ⭐ Streng |

> **Kernregel:** Markdown für Anweisungen. XML für Struktur. JSON für Daten. Und wenn Sie unsicher sind: Markdown ist immer ein guter Start.

---

## Was JSON bei Prompts (noch) nicht kann

| Limitation | Warum problematisch | Workaround |
|---|---|---|
| **Fehlerintolerant** | Ein fehlendes Komma macht das gesamte JSON ungültig. Im Gegensatz zu Markdown, wo ein vergessenes `#` kein Problem ist | JSON-Validator nutzen (jsonlint.com). Oder die KI bitten, das JSON zu korrigieren |
| **Schlecht für Prosa** | JSON ist für Daten, nicht für Fließtext. Eine „Begründung" in JSON wirkt abgehackt | Für narrative Teile Markdown oder XML nutzen, JSON nur für strukturierte Felder |
| **Schwer von Hand zu schreiben** | Bei 20 Feldern pro Datensatz wird manuelles Tippen mühsam und fehleranfällig | Daten aus Excel exportieren. Oder die KI bitten, ein JSON-Template zu generieren, das Sie befüllen |
| **Nicht selbsterklärend** | `"cir": 84.2` — was ist CIR? JSON hat keine eingebauten Beschreibungen | Feldnamen lang und beschreibend wählen: `"cost_income_ratio_prozent": 84.2` |
| **Modelle liefern nicht immer valides JSON** | Gelegentlich fügt die KI Kommentare hinzu oder vergisst eine Klammer | Im Prompt betonen: „NUR JSON, kein Fließtext." Und: „Prüfe die JSON-Syntax." |
| **Kein Standardschema für Prompts** | Jeder definiert eigene Feldnamen | Im Team auf Standard-Feldnamen einigen. Einmal definieren, überall verwenden |

---

## Kosten-Vergleich: Manuelle Verarbeitung vs. JSON-Pipeline

| Aufgabe | Manuell | Mit JSON-Pipeline | Ersparnis |
|---|---|---|---|
| 5 Kreditanfragen bewerten + in Excel | 45-60 Min (lesen + eintippen) | 10-15 Min (JSON-Prompt + Import) | ~75% |
| 15 Filialen analysieren + Ranking | 3-4 Stunden | 20-30 Min | ~85% |
| 20 Kundengespräche vorbereiten | 5-6 Stunden | 30-45 Min | ~90% |
| Wöchentlicher Vertriebsbericht aus Kennzahlen | 2-3 Stunden | 15-20 Min | ~85% |

**Token-Kosten:**

| Aufgabe | Tokens (ca.) | Kosten GPT-5.2 / Claude |
|---|---|---|
| 5 Kreditanfragen bewerten (JSON in + out) | 5.000-10.000 | 0,03-0,07 € |
| Filialanalyse 5 Filialen | 8.000-15.000 | 0,05-0,10 € |
| 20 Gesprächsvorbereitungen (Batch) | 15.000-30.000 | 0,10-0,20 € |

> **Fazit:** Die Token-Kosten sind vernachlässigbar. Der wahre Wert liegt in der Zeitersparnis — und darin, dass Sie die Ergebnisse direkt weiterverarbeiten können, statt sie manuell abzutippen.

---

## Modell-Empfehlungen für JSON

| Modell | JSON-Fähigkeit | Besonderheiten | Empfehlung |
|---|---|---|---|
| **ChatGPT (GPT-5.2)** | ⭐⭐⭐ Exzellent | Hat einen dedizierten „JSON Mode" (in der API). Auch im Chat-Fenster: Liefert zuverlässig valides JSON, wenn das Schema klar ist | Erste Wahl für JSON-Output |
| **Claude (Opus 4.6 / Sonnet 4)** | ⭐⭐⭐ Exzellent | Befolgt Schema-Vorgaben sehr genau. Neigt weniger dazu, ungewollten Fließtext hinzuzufügen | Sehr gut, besonders bei komplexen Schemas |
| **Gemini (2.5 Pro)** | ⭐⭐ Gut | Versteht JSON-Schemas, fügt aber gelegentlich erklärenden Text vor oder nach dem JSON ein | Funktioniert, braucht klarere „NUR JSON"-Anweisung |

---

## Das Wichtigste auf einen Blick

| Konzept | Erklärung | Wichtigster Tipp |
|---|---|---|
| **JSON-Input** | Daten als JSON an die KI übergeben | Eindeutige Feldnamen, Zahlen ohne €-Zeichen |
| **JSON-Output** | KI antwortet in JSON statt Fließtext | Schema mitgeben — das ist der „Vertrag" |
| **Batch-Verarbeitung** | Mehrere Datensätze gleichzeitig verarbeiten | JSON-Array `[{...}, {...}, {...}]` |
| **Excel-Import** | JSON → CSV → Excel | Online-Konverter oder Methode 4 (KI macht Tabelle) |
| **Verschachtelung** | Objekte in Objekten, Listen in Objekten | Für komplexe Daten (Kunde → Produkte → Details) |
| **Fehlertoleranz** | JSON ist strenger als Markdown/XML | Kommas, Klammern, Anführungszeichen prüfen |
| **Drei-Format-Regel** | Markdown = Anweisungen, XML = Struktur, JSON = Daten | Im Zweifel: Markdown ist immer ein guter Start |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---|---|
| JSON-Schema als „Vertrag" für die Ausgabe | Erweitert Formatvorgaben aus Tutorial 01-02 und 01-04, Schritt 7: Statt „Antworte als Tabelle" → exaktes Datenformat definieren |
| Batch-Verarbeitung (5 Kunden gleichzeitig) | Baut auf verschachtelte XML-Strukturen aus Tutorial 02-02, Schritt 7 auf: Gleiche Idee (mehrere Datensätze), anderes Format |
| „NUR JSON, kein Fließtext" | Nutzt Constraint-Technik aus Tutorial 01-04, Schritt 7: Klare Verbote erzwingen gewünschtes Format |
| Filialanalyse als Praxisbeispiel | Verbindet sich mit Six Thinking Hats und Deep Research aus Tutorial 01-07: JSON liefert die Datengrundlage für strategische Analysen |
| Excel-Import der Ergebnisse | Schließt die Lücke, die in allen bisherigen Tutorials bestand: KI-Ergebnisse blieben im Chat-Fenster — jetzt fließen sie in Ihre Arbeitstools |
| Drei-Format-Vergleich (Markdown/XML/JSON) | Zusammenfassung der gesamten Kapitel-02-Lernkurve: Jedes Format hat seinen Platz |

---

## ⚠️ Compliance-Hinweis: JSON ändert nichts am Datenschutz

Alle Datenschutz-Regeln aus Kapitel 01 gelten unverändert:

| Regel | Gilt auch mit JSON |
|---|---|
| Keine Kundennamen in externe Tools | ✅ `"name": "Max Müller"` ist genauso verboten wie im Fließtext |
| Anonymisieren vor dem Prompten | ✅ `"name": "Kunde A"` oder `"kunde_id": "K-2026-0042"` verwenden |
| Keine echten Finanzdaten | ✅ Für Übungszwecke: fiktive Zahlen nutzen. Für echte Analysen: interne KI-Lösung oder anonymisierte Daten |
| Vier-Augen-Prinzip | ✅ JSON-Ergebnisse sind genauso zu prüfen wie Fließtext-Ergebnisse |
| BaFin / DORA | ✅ Automatisierte KI-Pipelines (JSON → Excel → Bericht) müssen ins IKT-Verzeichnis |

**Besonderer Hinweis für JSON-Pipelines:** Wenn Sie KI-Ergebnisse automatisiert weiterverarbeiten (JSON → Excel → Entscheidungsvorlage), ist das ein höheres Risiko als manuelles Lesen. Warum? Weil Fehler nicht mehr beim Lesen auffallen. **Stichprobenkontrollen einbauen.** Mindestens 10% der JSON-Ergebnisse manuell prüfen.

---

## 🚀 Starten Sie hier — Ihr erster Schritt am Montag

> **Nehmen Sie 3 Kunden (anonymisiert) und schreiben Sie ihre Daten als JSON auf. Nutzen Sie die Prompt-Vorlage aus Schritt 3 und lassen Sie die KI alle drei gleichzeitig bewerten — mit JSON-Output. Dann wandeln Sie das Ergebnis mit einem Online-Konverter in eine Excel-Tabelle um.**

Das dauert 15 Minuten beim ersten Mal. Und Sie werden nie wieder 5 Kreditanfragen einzeln durchgehen wollen.

**Die Reihenfolge zum Reinwachsen:**
1. 🥇 **Woche 1:** Ein einfaches JSON-Objekt schreiben (1 Kunde, 5 Felder)
2. 🥈 **Woche 2:** JSON-Output erzwingen (Schema mitgeben)
3. 🥉 **Woche 3:** Batch-Verarbeitung (3-5 Datensätze gleichzeitig)
4. 🏅 **Danach:** JSON → Excel-Pipeline einrichten. Filialanalyse ausprobieren
5. 🎓 **Fortgeschritten:** Verschachtelte Strukturen (Kunde → Produkte → Cross-Selling)

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Ihr erstes JSON

**Aufgabe:** Schreiben Sie das folgende Kundenprofil als JSON:

```
Kundin, 42 Jahre, Lehrerin (verbeamtet), 
Nettoeinkommen 3.400€, verheiratet, 1 Kind, 
will 20.000€ Ratenkredit für eine Küche, 
Laufzeit 60 Monate, keine bestehenden Kredite.
```

**Ihre Aufgabe:**
1. Erstellen Sie ein JSON-Objekt mit sinnvollen Feldnamen
2. Achten Sie auf: Doppelte Anführungszeichen, Kommas, Zahlen ohne €
3. Testen Sie: Geben Sie das JSON in einen JSON-Validator (jsonlint.com) ein — ist es gültig?
4. Bonus: Fügen Sie einen zweiten Kunden hinzu (als JSON-Array mit `[{...}, {...}]`)

### Hands-on 2: JSON-Output erzwingen

**Aufgabe:** Nutzen Sie die Prompt-Vorlage aus Schritt 3 mit folgendem Schema:

```json
{
  "empfehlung": "<genehmigen|prüfen|ablehnen>",
  "risiko": "<niedrig|mittel|hoch>",
  "max_rate": "<Zahl>",
  "begruendung": "<1 Satz>",
  "cross_selling": ["<Produkt 1>", "<Produkt 2>"]
}
```

Geben Sie das Kundenprofil aus Hands-on 1 als Input und fordern Sie JSON-Output.

**Prüfen Sie:**
- Hält sich die KI an das Schema?
- Sind die Feldnamen exakt wie vorgegeben?
- Ist das JSON syntaktisch korrekt (Validator)?
- Wenn nicht: Was mussten Sie am Prompt ändern?

### Hands-on 3: Modellvergleich — Wer liefert besseres JSON?

**Aufgabe:** Geben Sie **zwei verschiedenen KI-Modellen** denselben Prompt:

```
# AUFGABE
Bewerte die folgende Kreditanfrage und antworte 
ausschließlich als JSON. Kein Fließtext.

# SCHEMA
{
  "risiko": "<niedrig|mittel|hoch>",
  "empfehlung": "<genehmigen|prüfen|ablehnen>",
  "tragfaehigkeit_prozent": <Zahl>,
  "staerken": ["...", "..."],
  "schwaechen": ["...", "..."],
  "begruendung": "<2 Sätze>"
}

# ANFRAGE
{
  "alter": 33,
  "beruf": "Selbständige Grafikdesignerin, 3 Jahre",
  "einkommen_jahresueberschuss": 48000,
  "kreditart": "Betriebsmittelkredit",
  "betrag": 35000,
  "sicherheiten": "keine",
  "schufa": "gut"
}
```

**Vergleichen Sie:**
- Welches Modell liefert syntaktisch korrektes JSON?
- Welches hält sich genauer an das Schema?
- Welches fügt ungewollten Fließtext hinzu?
- Welches gibt die differenziertere Bewertung?

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **JSON** | JavaScript Object Notation — ein leichtgewichtiges Datenformat mit geschweiften Klammern `{}`, eckigen Klammern `[]` und Schlüssel-Wert-Paaren. Sowohl von Menschen als auch von Maschinen lesbar. Kein Programmieren nötig |
| **Objekt** | Ein JSON-Datensatz in geschweiften Klammern: `{"name": "Kunde A", "alter": 38}`. Repräsentiert ein „Ding" mit Eigenschaften |
| **Array** | Eine JSON-Liste in eckigen Klammern: `[{...}, {...}, {...}]`. Enthält mehrere gleichartige Objekte. Ideal für Batch-Verarbeitung |
| **Schlüssel-Wert-Paar** | Ein einzelnes Datenfeld: `"alter": 38`. Links der Name (Schlüssel), rechts der Inhalt (Wert). Getrennt durch Doppelpunkt |
| **Schema** | Die Vorlage für ein JSON-Objekt — definiert, welche Felder erwartet werden und welche Werte erlaubt sind. Im Prompt: Das Ausgabe-Schema ist der „Vertrag" zwischen Ihnen und der KI |
| **Batch-Verarbeitung** | Mehrere Datensätze gleichzeitig durch die KI verarbeiten lassen, statt jeden einzeln. In JSON: Ein Array mit mehreren Objekten |
| **JSON-Validator** | Online-Tool (z.B. jsonlint.com), das prüft, ob ein JSON syntaktisch korrekt ist. Findet fehlende Kommas, Klammern und Anführungszeichen |
| **CSV** | Comma-Separated Values — einfaches Tabellenformat, bei dem Werte durch Kommas getrennt sind. Kann direkt in Excel geöffnet werden. JSON lässt sich leicht in CSV umwandeln |
| **Power Query** | Excel-Werkzeug zum Importieren und Transformieren von Daten aus verschiedenen Quellen — darunter auch JSON. Unter „Daten → Daten abrufen" zu finden |
| **Cost-Income-Ratio (CIR)** | Aufwand-Ertrags-Verhältnis einer Bank oder Filiale: Kosten geteilt durch Erträge × 100. Ein CIR von 75% bedeutet: Für jeden Euro Ertrag fallen 75 Cent Kosten an. Je niedriger, desto effizienter |
| **Cross-Selling** | Verkauf zusätzlicher Produkte an bestehende Kunden (vgl. Tutorial 01-07). Mit JSON-Kundenprofilen können Cross-Selling-Potenziale systematisch identifiziert werden |
| **Pipeline** | Mehrere aufeinander aufbauende Verarbeitungsschritte: JSON-Input → KI-Verarbeitung → JSON-Output → Excel-Import. Automatisiert den Gesamtprozess |

---

