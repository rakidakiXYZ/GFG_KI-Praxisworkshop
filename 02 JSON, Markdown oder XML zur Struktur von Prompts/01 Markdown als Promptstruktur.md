# Markdown als Prompt-Struktur

**Sie nutzen es schon, ohne es zu wissen — jetzt machen wir es bewusst und holen das Maximum heraus**

---

## Warum dieses Tutorial?

Willkommen in Kapitel 02. In Kapitel 01 haben Sie das Handwerk des Prompt Engineering gelernt — von den Grundlagen bis zu strategischen Methoden wie Six Thinking Hats und Deep Research. Dabei haben Sie bereits Strukturierungstechniken eingesetzt, wahrscheinlich ohne es zu merken.

Schauen Sie sich diesen Prompt aus Tutorial 01-06 an:

```
KONTEXT:
Du erhältst ein Meeting-Transkript...

AUFGABEN — Schritt für Schritt:
1. Lies das gesamte Transkript...
2. Erfasse die MEETING-GRUNDDATEN...

FORMATIERUNG:
- Datum: YYYY-MM-DD
```

Sehen Sie die Großbuchstaben-Überschriften? Die nummerierte Liste? Die Stichpunkte? Das **ist** Markdown. Oder zumindest eine vereinfachte Form davon. Sie haben die ganze Zeit Markdown-Delimiter benutzt — nur ohne zu wissen, dass es einen Namen hat und dass es systematisch noch besser geht.

Dieses Tutorial macht das Unbewusste bewusst. Es zeigt Ihnen, welche Markdown-Elemente als Delimiter funktionieren, warum sie die KI-Ergebnisse verbessern und wo Markdown an seine Grenzen stößt — und XML oder JSON die bessere Wahl sind (dazu mehr in Tutorial 02-02 und 02-03).

> **Volksbank-Analogie:** Markdown ist wie die Formatierung in einer Word-Vorlage: Überschriften, Aufzählungen, fett gedruckte Schlüsselwörter. Jeder nutzt sie intuitiv — aber wer sie *bewusst* und *systematisch* einsetzt, erstellt Dokumente, die professioneller aussehen und leichter zu bearbeiten sind. Genauso ist es mit Markdown in Prompts.

**Was Sie nach diesem Tutorial können:**

- Verstehen, was Markdown ist und warum es als Prompt-Struktur funktioniert
- Die 10 wichtigsten Markdown-Elemente gezielt in Prompts einsetzen
- Bestehende Prompts durch bewusste Markdown-Strukturierung verbessern
- Erkennen, wann Markdown reicht und wann Sie zu XML oder JSON wechseln sollten
- Markdown-Prompts so aufbauen, dass sie wiederverwendbar und teamtauglich sind

---

## Schritt 1: Was ist Markdown — und warum versteht die KI es?

### Markdown in 60 Sekunden

Markdown ist eine **einfache Textauszeichnung**, die 2004 von John Gruber erfunden wurde. Die Idee: Text soll auch ohne spezielle Software lesbar und formatiert sein. Statt komplizierter Menüs wie in Word tippt man einfache Zeichen:

| Was Sie tippen | Was es bedeutet | Wie es aussieht |
|---|---|---|
| `# Überschrift` | Hauptüberschrift | **Große, fette Überschrift** |
| `## Unterüberschrift` | Abschnitt | **Mittlere Überschrift** |
| `**fett**` | Hervorhebung | **fett** |
| `- Punkt 1` | Aufzählung | • Punkt 1 |
| `1. Schritt eins` | Nummerierte Liste | 1. Schritt eins |
| `---` | Horizontale Linie | ———— |
| `` `Code` `` | Technischer Begriff | `Code` |
| ` ``` ` ... ` ``` ` | Code-Block | Eingerahmter Textblock |
| `> Zitat` | Hervorgehobener Text | Eingerücktes Zitat |
| `| A | B |` | Tabelle | Tabellenzeile |

### Warum versteht die KI Markdown so gut?

Alle großen Sprachmodelle — GPT, Claude, Gemini — wurden mit *Milliarden* von Texten trainiert, die Markdown enthalten: GitHub-Dokumentationen, Wikipedia-Quellcode, technische Blogs, README-Dateien. Markdown ist für KI-Modelle so natürlich wie Fließtext. Sie erkennen:

- `#` = „Hier beginnt ein neuer Abschnitt"
- `---` = „Hier endet etwas, und etwas Neues beginnt"
- `1. 2. 3.` = „Diese Schritte gehören zusammen und haben eine Reihenfolge"
- ` ``` ` = „Das hier ist ein separater Textblock — behandle ihn anders als den Rest"
- `**fett**` = „Das ist besonders wichtig"

> **Volksbank-Analogie:** Markdown ist für die KI wie die Formatierung eines Kreditantrags für einen Sachbearbeiter: Fett gedruckte Feldnamen sagen „Hier steht was Wichtiges", nummerierte Abschnitte sagen „Bearbeite das in dieser Reihenfolge", und Trennlinien sagen „Neues Thema". Die KI „liest" Markdown-Zeichen genauso intuitiv.

---

## Schritt 2: Die 10 Markdown-Werkzeuge für bessere Prompts

Nicht alle Markdown-Elemente sind gleich nützlich in Prompts. Hier die 10, die den größten Unterschied machen — sortiert nach Wirkung:

### 🥇 Tier 1: Die Unverzichtbaren

#### 1. Überschriften (`#`, `##`, `###`) — Abschnitte definieren

```
# ROLLE
Du bist ein erfahrener Baufinanzierungsberater.

# AUFGABE
Erstelle drei Finanzierungsszenarien.

# REGELN
- Keine echten Kundennamen
- Maximale Rate: 35% des Nettos
```

**Wirkung:** Überschriften erzeugen die stärkste visuelle und semantische Trennung. Die KI erkennt: Das sind verschiedene Abschnitte mit verschiedenen Funktionen.

**Tipp:** `#` für Hauptabschnitte (Rolle, Aufgabe, Regeln), `##` für Unterabschnitte, `###` für Details. Nicht mehr als 3 Ebenen.

#### 2. Nummerierte Listen (`1. 2. 3.`) — Reihenfolge erzwingen

```
Gehe in dieser Reihenfolge vor:
1. Lies das Kundenprofil vollständig
2. Berechne die maximale Kreditrate
3. Erstelle drei Szenarien
4. Formuliere eine Empfehlung
5. Weise auf Risiken hin
```

**Wirkung:** Die KI arbeitet die Schritte in der angegebenen Reihenfolge ab. Ohne Nummerierung springt sie gelegentlich zwischen Punkten hin und her.

**Tipp:** Nummerierte Listen für **Arbeitsschritte** (Reihenfolge wichtig), Stichpunkt-Listen für **Regeln** (Reihenfolge egal).

#### 3. Strichpunkt-Listen (`-`) — Regeln und Eigenschaften

```
REGELN:
- Antworte auf Deutsch
- Maximal 500 Wörter
- Keine Fachbegriffe ohne Erklärung
- Datenschutz beachten: keine Kundennamen
```

**Wirkung:** Jede Regel steht für sich — die KI behandelt sie als separate Anweisungen, nicht als Fließtext, in dem eine untergehen könnte.

#### 4. Code-Blöcke (` ``` `) — Eingabedaten trennen

````
Analysiere das folgende Meeting-Transkript:

```
Thomas: Guten Morgen zusammen. Heute haben wir drei Punkte...
Sarah: Ich möchte kurz den Vertriebsbericht vorstellen...
Klaus: Zu Punkt zwei hätte ich eine Frage...
```

Erstelle daraus ein strukturiertes Protokoll.
````

**Wirkung:** Code-Blöcke sind der stärkste Markdown-Delimiter für **Eingabedaten**. Die KI erkennt: „Das in den Backticks ist der zu verarbeitende Input, alles davor und danach sind meine Anweisungen." Das ist entscheidend — ohne diese Trennung vermischt die KI gelegentlich Anweisungstext mit Eingabedaten.

**Tipp:** Nutzen Sie Code-Blöcke für alles, was „reingegeben" wird: Transkripte, E-Mails zum Umschreiben, Texte zum Zusammenfassen, Kundendaten.

### 🥈 Tier 2: Die Verstärker

#### 5. Fettdruck (`**text**`) — Schlüsselbegriffe hervorheben

```
Erstelle eine Empfehlung. Achte **besonders** auf:
- **Kapitaldienstfähigkeit** (max. 35% des Nettos)
- **Restschuld** nach Ablauf der Zinsbindung
- **Sondertilgungsoptionen**
```

**Wirkung:** Fettgedruckte Wörter haben eine leicht erhöhte „Aufmerksamkeit" beim Modell. Nicht dramatisch, aber messbar bei langen Prompts mit vielen Anweisungen.

#### 6. Horizontale Linien (`---`) — Themenblöcke trennen

```
# ROLLE
Du bist ein Firmenkundenberater.

---

# KUNDENDATEN
Branche: Handwerk, 12 Mitarbeiter, Umsatz 1,8 Mio €

---

# AUFGABE
Erstelle ein Angebot für einen Betriebsmittelkredit.
```

**Wirkung:** `---` erzeugt eine visuelle und semantische Pause — wie ein Seitenwechsel. Besonders nützlich, um Rolle/Kontext vom eigentlichen Arbeitsauftrag zu trennen.

#### 7. Tabellen (`| Spalte | Spalte |`) — Strukturierte Ausgabe vorgeben

```
Erstelle eine Vergleichstabelle:

| Kriterium | Szenario A | Szenario B | Szenario C |
|-----------|-----------|-----------|-----------|
| Zinssatz  | ...       | ...       | ...       |
| Tilgung   | ...       | ...       | ...       |
| Rate/Monat| ...       | ...       | ...       |
```

**Wirkung:** Wenn Sie eine Tabelle als Format vorgeben, füllt die KI sie in genau diesem Format aus. Das ist wie ein Formular mit vorgedruckten Zeilen — die KI muss nur noch die Felder befüllen.

### 🥉 Tier 3: Die Spezialisten

#### 8. Blockzitate (`>`) — Beispiele und Hinweise

```
Formuliere die Empfehlung im folgenden Stil:

> Basierend auf Ihrer Einkommenssituation und dem 
> gewünschten Finanzierungsvolumen empfehle ich 
> Szenario B mit einer Tilgung von 2,5%. Diese 
> Variante bietet eine tragbare monatliche Rate 
> bei gleichzeitig überschaubarer Restschuld.

Passe den Inhalt an die konkreten Kundendaten an, 
behalte aber Tonalität und Struktur bei.
```

**Wirkung:** Blockzitate eignen sich hervorragend für **Few-Shot-Beispiele** (vgl. Tutorial 01-04, Schritt 4). Die KI erkennt: „So soll meine Antwort klingen."

#### 9. Inline-Code (`` `text` ``) — Platzhalter und Variablen

```
Ersetze folgende Platzhalter durch die konkreten Werte:
- `[KUNDENNAME]` → anonymisiert als „Kunde A"
- `[BETRAG]` → Kreditbetrag aus den Kundendaten
- `[ZINSSATZ]` → aktueller Zinssatz (Stand 02/2026)
```

**Wirkung:** Inline-Code markiert Platzhalter als „das hier muss ersetzt werden" — die KI versteht, dass `[KUNDENNAME]` kein fertiger Text ist, sondern eine Variable.

#### 10. GROSSBUCHSTABEN — Die Low-Tech-Überschrift

```
ROLLE:
Erfahrener Kreditanalyst.

KONTEXT:
Volksbank Hellweg eG, ländliche Region.

AUFGABE:
Bewerte die folgende Kreditanfrage.

WICHTIG:
Keine Kundennamen verwenden.
```

**Wirkung:** GROSSBUCHSTABEN sind die einfachste Form der Strukturierung — und überraschend effektiv. In den Prompt-Vorlagen aus Kapitel 01 haben wir sie durchgehend verwendet. Sie funktionieren bei allen Modellen und brauchen kein Markdown-Wissen.

---

## Schritt 3: Markdown-Strukturmuster für typische Bank-Prompts

Jetzt kombinieren wir die Werkzeuge zu **fertigen Mustern**, die Sie sofort einsetzen können.

### Muster 1: Der Standard-Prompt (80% aller Fälle)

```
# ROLLE
[Wer soll die KI sein?]

# KONTEXT
[Hintergrund, Bank, Situation]

# AUFGABE
[Was soll die KI tun?]
1. Erster Schritt
2. Zweiter Schritt
3. Dritter Schritt

# REGELN
- Regel 1
- Regel 2
- Regel 3

# FORMAT
[Wie soll die Ausgabe aussehen?]
```

**Wann nutzen:** Für alle Prompts, die Sie im Tagesgeschäft brauchen — E-Mails, Zusammenfassungen, Analysen. Einfach, schnell, effektiv.

### Muster 2: Der Eingabedaten-Prompt (Dokument verarbeiten)

````
# ROLLE
[Wer soll die KI sein?]

# AUFGABE
[Was soll mit dem Eingabetext passieren?]

# REGELN
- [Einschränkungen]
- [Datenschutz]

# FORMAT
[Gewünschte Ausgabe]

---

# EINGABE

```
[Hier das zu verarbeitende Dokument, Transkript, 
E-Mail oder sonstige Daten einfügen]
```
````

**Wann nutzen:** Immer wenn Sie der KI einen Text zur Verarbeitung geben — Zusammenfassungen, Analysen, Umschreibungen. Der Code-Block nach `---` trennt Anweisung sauber von Eingabe.

### Muster 3: Der Vergleichs-Prompt (A vs. B)

````
# AUFGABE
Vergleiche die folgenden zwei [Dokumente/Angebote/Texte] 
und erstelle eine Vergleichstabelle.

# FOKUS
- [Worauf soll der Vergleich achten?]

---

## DOKUMENT A: [Titel]

```
[Text A]
```

## DOKUMENT B: [Titel]

```
[Text B]
```

---

# FORMAT
| Kriterium | Dokument A | Dokument B | Bewertung |
|-----------|-----------|-----------|-----------|

Darunter: Fazit mit Empfehlung (max. 5 Sätze).
````

**Wann nutzen:** Konditionsvergleiche, Anbietervergleiche, Vertragsvergleiche, Alt-vs-Neu-Analysen.

### Muster 4: Der Mehrstufige Prompt (Komplexe Aufgabe)

```
# ROLLE
[Experte mit relevantem Hintergrund]

# KONTEXT
[Situation, Bank, Zielgruppe]

# AUFGABE
Arbeite die folgenden Schritte **in dieser Reihenfolge** ab:

## Schritt 1: Analyse
[Was analysieren?]

## Schritt 2: Bewertung
[Nach welchen Kriterien bewerten?]

## Schritt 3: Empfehlung
[Was empfehlen, in welchem Format?]

## Schritt 4: Risiken
[Welche Risiken identifizieren?]

---

# REGELN
- [Einschränkungen]

# FORMAT
Für jeden Schritt eine eigene Überschrift.
Gesamtlänge: max. [X] Wörter.
```

**Wann nutzen:** Strategische Analysen, Kreditbewertungen, Projektbewertungen — alles mit mehreren Arbeitsschritten.

> **Volksbank-Analogie:** Diese vier Muster sind wie vier Standard-Formulare in Ihrer Bank: Einer für einfache Anfragen (Standard), einer zum Bearbeiten eingehender Dokumente (Eingabedaten), einer zum Vergleichen (Vergleich) und einer für komplexe Prüfungen (Mehrstufig). Sie wählen das passende Formular und füllen es aus — fertig.

---

## Schritt 4: Praxisbeispiel — Ein Kapitel-01-Prompt wird besser

Nehmen wir die **E-Mail-Vorlage** aus Tutorial 01-05 und verbessern sie durch bewusste Markdown-Strukturierung.

### Vorher (Kapitel 01 — intuitiv strukturiert):

```
Du bist ein professioneller E-Mail-Autor für eine 
Genossenschaftsbank. Schreibe eine Antwort auf die 
folgende Kundenbeschwerde. Tonalität: empathisch, 
lösungsorientiert, professionell. Biete eine konkrete 
Lösung an. Entschuldige dich ohne Schuldzuweisung. 
Maximal 150 Wörter. Verwende keine Floskeln wie 
„Wir bedauern die Unannehmlichkeiten". Schließe mit 
einem konkreten nächsten Schritt ab.

Die Beschwerde lautet: [Beschwerdetext]
```

### Nachher (Kapitel 02 — bewusst strukturiert):

````
# ROLLE
Professioneller Kundenkommunikator einer Genossenschaftsbank. 
Empathisch, lösungsorientiert, auf Augenhöhe.

# AUFGABE
Schreibe eine Antwort auf die folgende Kundenbeschwerde.

# REGELN
- **Tonalität:** Empathisch, professionell, nicht unterwürfig
- **Entschuldigung:** Ja, aber ohne Schuldzuweisung an Kollegen
- **Lösung:** Immer eine konkrete Lösung anbieten
- **Verboten:** Floskeln wie „Wir bedauern die Unannehmlichkeiten"
- **Abschluss:** Konkreter nächster Schritt (Termin, Rückruf, Frist)

# FORMAT
- Betreff: [passend zur Beschwerde]
- Anrede → Bezug auf Beschwerde → Entschuldigung → Lösung → Nächster Schritt → Grußformel
- Maximal 150 Wörter

---

# BESCHWERDE

```
[HIER BESCHWERDETEXT EINFÜGEN]
```
````

### Was ist besser — und warum?

| Aspekt | Vorher | Nachher |
|---|---|---|
| **Regeln auffindbar** | Vermischt im Fließtext | Eigener `# REGELN`-Block mit Stichpunkten |
| **Beschwerdetext getrennt** | „Die Beschwerde lautet:" — schwache Trennung | Code-Block nach `---` — glasklare Trennung |
| **Wiederverwendbarkeit** | Beschwerdetext mitten im Prompt | Code-Block am Ende — einfach austauschen |
| **Floskeln-Verbot** | Kann im Fließtext untergehen | Eigener Stichpunkt mit **Verboten:** — auffällig |
| **E-Mail-Struktur** | Nicht vorgegeben | FORMAT-Block definiert die Reihenfolge |

> **Praxis-Tipp:** Sie müssen Ihre funktionierenden Prompts aus Kapitel 01 nicht wegwerfen. Aber wenn Sie einen Prompt **regelmäßig nutzen**, lohnt es sich, ihn einmal in die bewusste Markdown-Struktur zu überführen — danach geht jede Nutzung schneller.

---

## Schritt 5: Wo Markdown an seine Grenzen stößt

Markdown ist fantastisch für 80% aller Prompts. Aber es gibt Situationen, in denen es nicht reicht:

```
┌─────────────────────────────────────────────────────────────────┐
│        ✅ Markdown reicht          🔄 XML/JSON besser           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ✅ Einfache Aufgaben              🔄 Verschachtelte Daten      │
│     (E-Mail, Zusammenfassung)         (Kunde → Einkommen →     │
│                                        Partnerin → Einkommen)  │
│                                                                 │
│  ✅ Ein Eingabedokument             🔄 Mehrere gleichartige     │
│     (ein Transkript, ein Text)        Datensätze (5 Kunden     │
│                                        gleichzeitig bewerten)  │
│                                                                 │
│  ✅ Wenige, klare Regeln            🔄 Komplexe Regelwerke     │
│     (5-8 Stichpunkte)                (Pflichten vs. Verbote    │
│                                        vs. Eskalationsregeln)  │
│                                                                 │
│  ✅ Menschlicher Leser              🔄 Maschinelle Weiter-     │
│     (Prompt wird manuell               verarbeitung (KI-       │
│     kopiert und eingefügt)             Ausgabe → Excel/CRM)    │
│                                                                 │
│  ✅ Einmal-Prompts                  🔄 System-Prompts für      │
│     (einmal nutzen, fertig)            Chatbots/Custom GPTs    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Konkretes Beispiel: Wo Markdown scheitert

**Aufgabe:** Drei Kreditanfragen gleichzeitig bewerten.

**Markdown-Versuch:**

````
## Anfrage 1
Alter: 34, Angestellter, Netto: 3.800€
Vorhaben: Ratenkredit 25.000€

## Anfrage 2  
Alter: 52, Selbständig, Jahreseinkommen: 72.000€
Vorhaben: Betriebsmittelkredit 100.000€

## Anfrage 3
Alter: 28, Berufseinsteigerin, Netto: 2.600€
Vorhaben: Baufinanzierung 280.000€
````

**Problem:** Die Anfragen haben unterschiedliche Felder (mal Netto, mal Jahreseinkommen). Markdown zeigt nicht, welche Felder zusammengehören. Bei 10 Anfragen wird es unübersichtlich. Und wenn ein Feld fehlt, fällt es nicht auf.

**XML-Lösung** (→ Tutorial 02-02):

```
<anfrage id="1">
  <person>Alter: 34, Angestellter</person>
  <einkommen>Netto: 3.800 €/Monat</einkommen>
  <vorhaben>Ratenkredit 25.000 €</vorhaben>
</anfrage>
```

**JSON-Lösung** (→ Tutorial 02-03):

```json
{
  "anfragen": [
    {"id": 1, "alter": 34, "beruf": "Angestellter", 
     "netto": 3800, "vorhaben": "Ratenkredit", "betrag": 25000},
    {"id": 2, "alter": 52, "beruf": "Selbständig",
     "jahreseinkommen": 72000, "vorhaben": "Betriebsmittelkredit", "betrag": 100000}
  ]
}
```

### Die Drei-Format-Regel

| Wann | Format | Warum |
|------|--------|-------|
| **Einfache bis mittlere Prompts** | Markdown | Lesbar, schnell, alle können es |
| **Komplexe Strukturen, System-Prompts** | XML | Klare Hierarchie, modular, ideal für Claude |
| **Daten rein/raus, Automatisierung** | JSON | Maschinenlesbar, strukturierte Ein-/Ausgabe |

> **Volksbank-Analogie:** Markdown ist wie ein Word-Dokument — flexibel, schnell geschrieben, jeder versteht es. XML ist wie ein PDF-Formular mit definierten Feldern — strukturierter, aber aufwändiger. JSON ist wie eine Excel-Tabelle — perfekt für Daten, aber kein Mensch will einen Brief in Excel schreiben. Jedes Format hat seinen Platz.

---

## Schritt 6: Markdown-Prompts teamtauglich machen

Wenn Sie Prompts mit Kollegen teilen, wird Lesbarkeit entscheidend. Hier drei Techniken:

### Technik 1: Platzhalter-Konvention

Einigen Sie sich im Team auf eine Schreibweise für „hier müssen Sie etwas einfügen":

```
# KUNDENDATEN
- Name: [ANONYMISIERT]
- Alter: [ALTER]
- Nettoeinkommen: [NETTO €/MONAT]
- Vorhaben: [KREDITART + BETRAG]
```

`[GROSSBUCHSTABEN]` signalisiert: „Das ist ein Platzhalter — hier Ihre Daten einsetzen." Nutzen Sie das konsistent in allen Prompts.

### Technik 2: Kommentare für Kollegen

```
# ROLLE
Erfahrener Baufinanzierungsberater.
<!-- Hinweis: Bei Firmenkundenprompts "Firmenkundenberater" 
     verwenden und REGELN-Block anpassen -->

# REGELN
- Max. Rate: 35% des Haushaltsnettos
<!-- Für Firmenkunden: 40% des Jahresüberschusses -->
```

`<!-- Kommentar -->` ist ein HTML/XML-Kommentar. Die KI ignoriert ihn normalerweise — er ist nur für menschliche Leser. Ideal für Hinweise an Kollegen, die den Prompt nutzen.

### Technik 3: Template-Bibliothek

Speichern Sie Ihre besten Prompts als Dateien mit klarer Benennung:

```
prompt-bibliothek/
├── kundenberatung/
│   ├── baufinanzierung-szenario.md
│   ├── beschwerdeantwort.md
│   └── cross-selling-kampagne.md
├── protokolle/
│   ├── kreditausschuss.md
│   ├── teammeeting.md
│   └── filialleiter-runde.md
└── strategie/
    ├── six-thinking-hats.md
    ├── deep-research.md
    └── markenstrategie.md
```

Jede Datei enthält den fertigen Prompt mit Platzhaltern. Ein Kollege öffnet die Datei, ersetzt die Platzhalter, kopiert den Prompt ins KI-Tool — fertig.

> **Praxis-Tipp:** Legen Sie diese Bibliothek in einem geteilten Ordner an (z.B. Teams, SharePoint oder ein gemeinsames Laufwerk). Nach 2-3 Monaten haben Sie 15-20 erprobte Prompts — ein enormer Wissensvorsprung gegenüber Banken, die noch „Fasse das mal zusammen" in ChatGPT tippen.

---

## Was Markdown bei Prompts (noch) nicht kann

| Limitation | Warum problematisch | Workaround |
|---|---|---|
| **Keine echte Verschachtelung** | `##` unter `#` ist visuell verschachtelt, aber die KI erkennt die Hierarchie weniger strikt als bei XML-Tags | Für flache Strukturen (2 Ebenen) reicht Markdown. Ab 3+ Ebenen → XML (Tutorial 02-02) |
| **Keine eindeutige Datentrennung** | Markdown hat kein „Anfang" und „Ende" für Datenblöcke. `---` ist eine Linie, kein Container | Code-Blöcke (` ``` `) als Container nutzen. Für mehrere Datensätze → XML oder JSON |
| **Kein maschinenlesbares Format** | Markdown-Ausgabe kann kein anderes System direkt weiterverarbeiten | Wenn die KI-Ausgabe in Excel/CRM importiert werden soll → JSON-Output (Tutorial 02-03) |
| **Überschriften sind mehrdeutig** | `# AUFGABE` könnte ein Prompt-Abschnitt sein oder eine Überschrift im Ausgabetext | Konvention: `# GROSSBUCHSTABEN` = Prompt-Struktur. `# Normale Schrift` = Ausgabeformat |
| **Kein Standard-Schema** | Jeder strukturiert Markdown-Prompts anders | Im Team auf ein Muster einigen (Schritt 3) |

> **Kernregel:** Markdown ist das Schweizer Taschenmesser der Prompt-Strukturierung — vielseitig, schnell, überall verfügbar. Aber für Spezialaufgaben brauchen Sie Spezialwerkzeuge: XML für Hierarchie (02-02), JSON für Daten (02-03).

---

## Kosten-Vergleich: Unstrukturiert vs. Markdown

| Aspekt | Unstrukturierter Fließtext | Markdown-Struktur |
|---|---|---|
| **Erstellungszeit** | 3 Min | 4-5 Min (+50%) |
| **Änderungszeit** | 2-3 Min (Text durchlesen) | 30 Sek (Abschnitt finden) |
| **Token-Kosten** | Baseline | +3-5% (Markdown-Zeichen) |
| **Ergebnisqualität (einfach)** | Gut | Gleich gut |
| **Ergebnisqualität (komplex)** | Mittelmäßig — Regeln werden übersehen | Gut — Abschnitte werden respektiert |
| **Wiederverwendbarkeit** | Gering | Hoch (Platzhalter, Templates) |
| **Team-Tauglichkeit** | Schlecht — jeder versteht es anders | Gut — Struktur ist selbsterklärend |

**Token-Overhead:** Markdown-Zeichen (`#`, `-`, `---`, ` ``` `) verbrauchen minimal mehr Tokens — typischerweise 3-5% mehr als reiner Fließtext. Bei einem 500-Wörter-Prompt sind das ca. 15-25 zusätzliche Tokens — Kosten: unter 0,01 €. Vernachlässigbar.

---

## Das Wichtigste auf einen Blick

| Werkzeug | Wirkung | Wann nutzen |
|---|---|---|
| **`# Überschrift`** | Stärkste Trennung, definiert Abschnitte | Immer: Rolle, Aufgabe, Regeln, Format |
| **`1. 2. 3.`** | Erzwingt Reihenfolge | Arbeitsschritte, Prozesse |
| **`- Stichpunkt`** | Gleichwertige Aufzählung | Regeln, Eigenschaften, Anforderungen |
| **` ``` Code ``` `** | Trennt Eingabedaten von Anweisungen | Transkripte, E-Mails, Dokumente |
| **`**fett**`** | Hebt Schlüsselwörter hervor | Wichtige Begriffe, Verbote |
| **`---`** | Themenblock-Trenner | Zwischen Anweisungsteil und Datenteil |
| **`> Zitat`** | Markiert Beispiele | Few-Shot-Beispiele, Muster-Antworten |
| **Tabelle** | Strukturierte Ausgabe vorgeben | Vergleiche, Szenarien, Bewertungen |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---|---|
| Markdown-Überschriften als Abschnittstrenner | Formalisiert das intuitive `KONTEXT:` / `AUFGABE:` / `REGELN:` aus allen Tutorials in Kapitel 01 |
| Code-Blöcke für Eingabedaten | Ersetzt „Füge jetzt hier ein:" aus Tutorial 01-06 durch klare Container |
| Fettdruck für Schlüsselwörter | Verstärkt die Constraint-Technik aus Tutorial 01-04, Schritt 7: Verbote werden sichtbarer |
| Nummerierte Listen für Arbeitsschritte | Formalisiert die „Schritt für Schritt"-Anweisung aus Chain-of-Thought (Tutorial 01-04, Schritt 1) |
| Template-Bibliothek | Baut auf die Prompt-Vorlagen aus Tutorial 01-05, 01-06, 01-07 auf: Von Einzelprompts zu wiederverwendbaren Werkzeugen |
| Grenzen von Markdown → XML/JSON | Bereitet den Übergang zu Tutorial 02-02 (XML) und 02-03 (JSON) vor |

---

## ⚠️ Compliance-Hinweis

Markdown-Strukturierung ändert nichts an den Datenschutz- und Compliance-Regeln aus Kapitel 01. Ein sauber strukturierter Prompt mit Kundennamen ist genauso verboten wie ein unstrukturierter Prompt mit Kundennamen. Alle Regeln aus Tutorial 01-05 (Schritt 2) und 01-06 (Schritt 2) gelten unverändert.

---

## 🚀 Starten Sie hier — Ihr erster Schritt am Montag

> **Nehmen Sie Ihren meistgenutzten Prompt aus Kapitel 01. Fügen Sie drei Dinge hinzu: (1) `# ÜBERSCHRIFTEN` für die Hauptabschnitte, (2) `- Stichpunkte` für die Regeln, (3) einen ` ``` Code-Block ``` ` für die Eingabedaten. Fertig.**

Das dauert 3 Minuten. Ab der zweiten Nutzung sparen Sie jedes Mal 2 Minuten beim Anpassen. Und die Ergebnisse werden konsistenter.

**Die Reihenfolge zum Reinwachsen:**
1. 🥇 **Woche 1:** Standard-Muster (Schritt 3, Muster 1) auf einen vorhandenen Prompt anwenden
2. 🥈 **Woche 2:** Eingabedaten mit Code-Block trennen (Muster 2)
3. 🥉 **Woche 3:** Einen Vergleichs-Prompt bauen (Muster 3)
4. 🏅 **Danach:** Template-Bibliothek im Team starten (Schritt 6)

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Fließtext → Markdown

**Aufgabe:** Überführen Sie diesen Fließtext-Prompt in die Markdown-Struktur:

```
Ich brauche eine kurze Marktanalyse über den Immobilienmarkt 
in Südwestfalen. Du bist ein Immobilienexperte. Fokus auf 
Preisentwicklung Einfamilienhäuser 2024-2026, Angebot und 
Nachfrage, und Prognose für die nächsten 2 Jahre. Schreibe 
maximal 400 Wörter. Nenne Quellen wenn möglich. Formatiere 
als Executive Summary mit Stichpunkten.
```

**Ihre Aufgabe:**
1. Identifizieren Sie die Bestandteile: Rolle, Aufgabe, Regeln, Format
2. Strukturieren Sie den Prompt mit `#`, `-`, und `**fett**`
3. Testen Sie beide Versionen in Ihrem KI-Tool
4. Vergleichen Sie: Welche Version liefert die strukturiertere Antwort?

### Hands-on 2: Muster anwenden — Dokumentenvergleich

**Aufgabe:** Nutzen Sie Muster 3 (Vergleichs-Prompt) aus Schritt 3, um die KI diese zwei Zitate vergleichen zu lassen:

```
Text A: „Die Genossenschaftsbank lebt von der Nähe zu ihren 
Mitgliedern. Persönliche Beratung ist unser Kernversprechen."

Text B: „Digitale Bankdienstleistungen ermöglichen 24/7-Zugang 
zu allen Services. Der Kunde erwartet Self-Service."
```

**Ihre Aufgabe:**
1. Bauen Sie den Vergleichs-Prompt mit `## DOKUMENT A`, `## DOKUMENT B`, Code-Blöcken und einer Format-Tabelle
2. Fragen Sie die KI: „Wie kann eine Volksbank beide Positionen vereinen?"
3. Prüfen Sie: Behandelt die KI beide Texte gleichwertig oder bevorzugt sie einen?

### Hands-on 3: Modellvergleich — Markdown-Verständnis

**Aufgabe:** Geben Sie **zwei verschiedenen KI-Modellen** denselben Markdown-Prompt:

````
# ROLLE
Risikoanalyst einer Genossenschaftsbank

# AUFGABE
Bewerte das folgende Kreditengagement und erstelle eine 
Risikoeinschätzung.

# REGELN
- **Keine** Empfehlung zur Genehmigung oder Ablehnung
- Nur Risikofaktoren identifizieren und bewerten
- Risikoskala: niedrig / mittel / hoch / kritisch

# FORMAT
| Risikofaktor | Bewertung | Begründung |
Darunter: Gesamtrisiko in einem Satz.

---

# EINGABE

```
Kreditnehmer: Handwerksbetrieb, 8 Mitarbeiter, seit 15 Jahren 
Kunde. Umsatz 2025: 1,2 Mio € (Vorjahr: 1,4 Mio €, -14%). 
Kreditwunsch: 200.000 € Betriebsmittel. Sicherheit: 
Globalzession auf Forderungen. Kontoführung: regelmäßige 
Limit-Ausschöpfung bis 95%.
```
````

**Vergleichen Sie:**
- Welches Modell respektiert die Tabellenformat-Vorgabe?
- Welches hält sich an die Regel „keine Empfehlung"?
- Welches liefert die differenzierteren Risikofaktoren?

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **Markdown** | Einfache Textauszeichnungssprache, 2004 von John Gruber erfunden. Nutzt Zeichen wie `#`, `-`, `**` und ` ``` ` zur Formatierung. Wird von allen großen KI-Modellen nativ verstanden |
| **Delimiter** | Trennzeichen, die verschiedene Teile eines Prompts voneinander abgrenzen. Markdown-Elemente (`#`, `---`, ` ``` `) sind eine Form von Delimitern (vgl. Tutorial 01-04, Schritt 3) |
| **Code-Block** | Text, der von dreifachen Backticks (` ``` `) umschlossen ist. In Prompts der stärkste Markdown-Delimiter für Eingabedaten — trennt „Anweisung" von „zu verarbeitendem Text" |
| **Fließtext-Prompt** | Prompt ohne bewusste Strukturierung — alle Anweisungen, Daten und Regeln in einem durchgehenden Textblock. Funktioniert bei kurzen Prompts, wird bei langen unübersichtlich |
| **Template** | Wiederverwendbare Prompt-Vorlage mit fester Struktur und Platzhaltern. Markdown-Prompts eignen sich als Templates, weil die Abschnitte klar benannt sind |
| **Platzhalter** | Markierungen für einzusetzende Inhalte: `[KUNDENNAME]`, `[BETRAG]`, `[HIER EINFÜGEN]`. Signalisieren sowohl dem Menschen als auch der KI: „Hier muss etwas ersetzt werden" |
| **Few-Shot** | Prompt-Technik, bei der Beispiele mitgegeben werden (vgl. Tutorial 01-04, Schritt 4). In Markdown mit Blockzitaten (`>`) oder Code-Blöcken realisierbar |
| **Token-Overhead** | Zusätzlicher Token-Verbrauch durch Strukturierungszeichen. Bei Markdown typischerweise 3-5% — vernachlässigbar |
| **Tier-System** | Einteilung der Markdown-Werkzeuge nach Wirkung: Tier 1 (unverzichtbar), Tier 2 (verstärkend), Tier 3 (spezialisiert) |

---

