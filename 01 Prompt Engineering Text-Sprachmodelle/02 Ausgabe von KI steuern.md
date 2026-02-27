# KI-Ausgaben steuern — Struktur, Format & Tonalität

**Von der Rohausgabe zum sofort einsetzbaren Ergebnis — wie Sie kontrollieren, WAS die KI liefert und WIE es aussieht**

---

## Warum dieses Tutorial?

In Tutorial 01-01 haben Sie gelernt, gute Prompts zu bauen — mit Rolle, Kontext, Aufgabe, Regeln, Beispielen und Format. Sie wissen jetzt, wie Sie der KI einen klaren Auftrag geben.

Aber hier passiert etwas Seltsames: Sie schreiben einen perfekten Prompt — und die KI liefert einen Fließtext, wo Sie eine Tabelle wollten. Oder sie schreibt drei Seiten, wo Sie drei Sätze brauchten. Oder sie klingt wie ein Wikipedia-Artikel, obwohl Sie eine Kunden-E-Mail brauchen.

Das Problem ist nicht Ihr Prompt. Das Problem ist, dass Sie den **Output** nicht gesteuert haben.

Stellen Sie sich vor, Sie bestellen bei einem Architekten ein Haus. Sie beschreiben genau, was Sie wollen: drei Zimmer, Garten, Garage. Der Architekt liefert — aber die Pläne sind auf Japanisch beschriftet, im A0-Format, und die Zimmer sind in umgekehrter Reihenfolge. Technisch korrekt. Praktisch unbrauchbar.

Dieses Tutorial macht Sie vom Auftraggeber zum **Art Director** Ihrer KI-Ergebnisse. Sie lernen, nicht nur das *Was*, sondern auch das *Wie* zu kontrollieren.

**Was Sie nach diesem Tutorial können:**

- KI-Ausgaben in drei Ebenen strukturieren (Container → Komponenten → Constraints)
- Das richtige Format für jeden Zweck wählen (Tabelle, Liste, Template, E-Mail, JSON)
- Tonalität und Stil gezielt nach Zielgruppe steuern (Vorstand, Kunden, Kollegen)
- Token sparen — schneller, günstiger und mit weniger Nacharbeit zum Ergebnis
- Die 4-K-Schnellformel für den Alltag anwenden
- Fehlerhafte Ausgaben systematisch debuggen und korrigieren
- Output-Verträge formulieren, die konsistente Ergebnisse garantieren

---

## Ein Blick zurück: Wie Output-Kontrolle entstand

Die Idee, KI-Ausgaben zu steuern, ist so alt wie die Sprachmodelle selbst — aber die Methoden haben sich dramatisch verändert.

| Jahr | Meilenstein | Bedeutung |
|---|---|---|
| **2020** | GPT-3 veröffentlicht | Erste Experimente mit Format-Anweisungen — funktionierte nur sporadisch |
| **2022** | ChatGPT + Instruction Tuning | Modelle folgen erstmals zuverlässig Formatvorgaben wie „als Tabelle" oder „in 3 Sätzen" |
| **2023** | System Prompts + JSON Mode | Getrennte Steuerungsebene für Output-Regeln; strukturierte Ausgabe wird Standard |
| **2024** | Structured Outputs (OpenAI) | Modelle können garantiert valides JSON nach Schema liefern — keine Ratearbeit mehr |
| **2025** | Output Contracts (Best Practice) | Die Community standardisiert: Format, Länge, Ton und Prüfschritte als „Vertrag" mit dem Modell |
| **2026** | Multimodale Output-Kontrolle | Nicht nur Text, sondern auch Bild-, Audio- und Code-Ausgaben werden formatsteuerbar |

**Die Entwicklung zeigt:** Früher war Output-Kontrolle Glückssache. Heute ist sie ein präzises Handwerk — wenn Sie die richtigen Techniken kennen.

---

## Schritt 1: Das Struktur-Framework — Container, Komponenten, Constraints

Jede gute KI-Ausgabe basiert auf drei Ebenen. Denken Sie an eine Aktentasche:

```
┌─────────────────────────────────────────────────┐
│  CONTAINER (Hauptabschnitte)                    │
│  ┌───────────────────────────────────────────┐  │
│  │  KOMPONENTEN (Unterelemente)              │  │
│  │  ┌─────────────────────────────────────┐  │  │
│  │  │  CONSTRAINTS (Einschränkungen)      │  │  │
│  │  │  Wortanzahl · Stil · Zielgruppe     │  │  │
│  │  └─────────────────────────────────────┘  │  │
│  │  Zahlen · Beispiele · Argumente           │  │
│  └───────────────────────────────────────────┘  │
│  Hintergrund · Empfehlung · Fazit               │
└─────────────────────────────────────────────────┘
```

**1. Container** — Die Hauptabschnitte Ihres Ergebnisses. Wie die Kapitel eines Berichts: Zusammenfassung, Analyse, Empfehlung, Nächste Schritte.

**2. Komponenten** — Die Unterelemente pro Container. In der Analyse stecken: Zahlen, Vergleiche, Grafik-Beschreibungen. In der Empfehlung: Argumente, Kosten, Risiken.

**3. Constraints** — Die Einschränkungen, die alles zusammenhalten. Maximale Wortanzahl, Tonalität, Zielgruppe, verbotene Begriffe.

### Am lebenden Objekt: Vorstandsvorlage

**Version 1 — ohne Struktur-Framework:**
```
Erstelle eine Vorlage für den Vorstand über unsere Digitalisierungsstrategie.
```
→ Ergebnis: Ein 500-Wörter-Fließtext ohne klare Gliederung. Nicht vorstandstauglich.

**Version 2 — mit Containern:**
```
Erstelle eine Vorstandsvorlage zur Digitalisierungsstrategie mit folgenden Abschnitten:
- Management Summary
- Ausgangslage
- Strategische Optionen
- Empfehlung
- Nächste Schritte
```
→ Besser: Klare Gliederung. Aber die Abschnitte sind noch beliebig gefüllt.

**Version 3 — mit Containern + Komponenten + Constraints:**
```
Erstelle eine Vorstandsvorlage zur Digitalisierungsstrategie 2026 
der Volksbank Hellweg.

[Management Summary]
- 3 Kernaussagen, je max. 1 Satz
- 1 Handlungsempfehlung

[Ausgangslage]
- Aktuelle Digitalisierungsquote (Platzhalter: [ZAHL]%)
- 3 Benchmark-Vergleiche mit anderen Genossenschaftsbanken
- Stärken und Schwächen als Bullet Points

[Strategische Optionen]
- 3 Optionen als Tabelle: Option | Investition | Zeithorizont | Risiko
- Pro/Contra je Option (je 2 Punkte)

[Empfehlung]
- 1 empfohlene Option mit Begründung (max. 50 Wörter)
- 3 KPIs zur Erfolgsmessung

[Nächste Schritte]
- To-do-Tabelle: Maßnahme | Verantwortlich | Frist

Constraints:
- Gesamtlänge: max. 1 A4-Seite
- Ton: sachlich, entscheidungsorientiert
- Keine Marketing-Sprache
- Platzhalter für interne Zahlen mit [ZAHL] kennzeichnen
```

> **Volksbank-Analogie:** Container, Komponenten und Constraints sind wie ein Kreditantrag. Der Antrag hat feste Abschnitte (Container): Antragsteller, Objekt, Finanzierung. Jeder Abschnitt hat definierte Felder (Komponenten): Name, Einkommen, Eigenkapital. Und es gibt Regeln (Constraints): Eigenkapitalquote mindestens 20%, Kreditlaufzeit maximal 30 Jahre. Ohne diese drei Ebenen wäre jeder Kreditantrag ein unstrukturiertes Durcheinander.

---

## Schritt 2: Die Format-Palette — Das richtige Werkzeug für jeden Zweck

In Tutorial 01-01 haben Sie Baustein 6 (Format) kennengelernt. Jetzt gehen wir in die Tiefe: Welches Format löst welches Problem?

### Die 7 Format-Typen

| Format | Wann nutzen | Stärke | Schwäche |
|---|---|---|---|
| **Tabelle** | Vergleiche, Übersichten, Statusberichte | Auf einen Blick erfassbar | Wenig Platz für Nuancen |
| **Nummerierte Liste** | Schritte, Rankings, Prioritäten | Reihenfolge klar | Kein Zusammenhang zwischen Punkten |
| **Bullet Points** | Schnellüberblick, Brainstorming | Schnell erfassbar | Kann beliebig wirken |
| **Template** | Wiederkehrende Vorlagen (E-Mails, Anschreiben) | Sofort wiederverwendbar | Muss angepasst werden |
| **Fließtext** | Berichte, Zusammenfassungen, Storytelling | Zusammenhänge werden klar | Langsam zu lesen |
| **Markdown** | Wiki-Artikel, interne Doku, Anleitungen | Strukturiert + lesbar | Nicht jedes Tool versteht Markdown |
| **JSON** | Datenübergabe an andere Systeme | Maschinenlesbar, fehlerfrei parsbar | Für Menschen schwer lesbar |

### Format-Anweisungen, die funktionieren

Nicht jede Format-Anweisung kommt bei der KI gleich gut an. Hier sind bewährte Formulierungen:

**Für Tabellen:**
```
Erstelle eine Tabelle mit den Spalten: Maßnahme | Zielgruppe | Aufwand | Frist | Verantwortlich
```
→ Spalten explizit benennen — sonst erfindet die KI eigene.

**Für Templates mit Platzhaltern:**
```
Erstelle eine E-Mail-Vorlage. Verwende Platzhalter in {{geschweiften Klammern}} 
für variable Inhalte: {{Kundenname}}, {{Produktname}}, {{Datum}}.
```
→ Platzhalter-Syntax definieren — verschiedene KIs verwenden sonst verschiedene Formate.

**Für JSON:**
```
Gib das Ergebnis als JSON zurück:
{
  "zusammenfassung": "2-3 Sätze",
  "kernpunkte": ["...", "..."],
  "naechste_schritte": [{"aktion": "...", "verantwortlich": "...", "frist": "..."}]
}
```
→ Das Schema als Beispiel mitgeben — die KI füllt es dann aus.

**Für strukturierten Fließtext:**
```
Schreib einen zusammenhängenden Text in 3 Absätzen:
Absatz 1: Ausgangslage (max. 50 Wörter)
Absatz 2: Kernaussage (max. 80 Wörter)  
Absatz 3: Handlungsempfehlung (max. 40 Wörter)
```
→ Absätze nummerieren und jedem eine Wortgrenze geben.

### Format-Kombination: Die Profi-Technik

Die stärksten Ergebnisse entstehen, wenn Sie Formate **kombinieren**:

```
Erstelle einen Quartalsrückblick für die Privatkundenberatung:

1. Executive Summary (3 Bullet Points, je max. 15 Wörter)
2. Kennzahlen als Tabelle: KPI | Q3/2025 | Q4/2025 | Veränderung | Bewertung
3. Top-3-Erfolge als nummerierte Liste mit je 1 Satz
4. Handlungsfelder als Fließtext (max. 100 Wörter)
5. Nächste Schritte als Checkliste mit [ ] Checkboxen
```

> **Volksbank-Analogie:** Format ist wie der Unterschied zwischen einem Beratungsgespräch (Fließtext), einem Kontoauszug (Tabelle) und einer Checkliste für die Kontoeröffnung (Liste). Alle enthalten wichtige Informationen — aber das Format bestimmt, wie schnell und wie richtig sie verstanden werden. Sie würden einem Kunden seine Vermögensübersicht nicht als Fließtext vorlesen. Und Sie würden dem Vorstand keinen Kontoauszug als Strategiepapier präsentieren.

---

## Schritt 3: Die 4-K-Schnellformel — Für den Alltag

In Tutorial 01-01 haben Sie die 6 Bausteine eines guten Prompts gelernt. Für den täglichen Gebrauch gibt es eine kompaktere Version: die **4-K-Formel**.

```
┌───────────────────────────────────────────┐
│           Die 4-K-Formel                  │
│                                           │
│  K₁  KONTEXT      → Worum geht's?        │
│  K₂  KONKRETE     → Was genau tun?        │
│       AUFGABE                             │
│  K₃  KRITERIEN    → Tonalität, Tiefe,     │
│                     Umfang, Prüfschritte  │
│  K₄  KONTROLLE    → Format, Länge,        │
│                     Zielgruppe            │
│                                           │
│  Eselsbrücke: „Klar Kommunizieren,        │
│                Korrekt Kontrollieren"      │
└───────────────────────────────────────────┘
```

**Wie 4-K und die 6 Bausteine zusammenhängen:**

| 4-K-Formel | Entspricht den 6 Bausteinen |
|---|---|
| K₁ Kontext | Rolle + Kontext |
| K₂ Konkrete Aufgabe | Aufgabe |
| K₃ Kriterien | Regeln + Beispiele |
| K₄ Kontrolle | Format |

Die 4-K-Formel ist keine Konkurrenz zu den 6 Bausteinen — sie ist eine **Schnellversion für den Kopf**. Wenn Sie morgens schnell eine E-Mail per KI entwerfen wollen, denken Sie an 4-K. Wenn Sie ein wichtiges Strategiepapier erstellen, greifen Sie auf die 6 Bausteine zurück.

### 4-K in Aktion: Kundenbrief

```
K₁ Kontext: 
Interner Brief der Volksbank Hellweg an Bestandskunden der Filiale 
Soest. Anlass: Einführung des neuen VR-Banking-App-Updates mit 
Haushaltsbuch-Funktion.

K₂ Konkrete Aufgabe: 
Erstelle ein Anschreiben, das die neue Funktion vorstellt und 
zum Ausprobieren motiviert.

K₃ Kriterien: 
Wertschätzend, positiv, Siezen. Keine technischen Details zur 
App-Architektur. Keine Vergleiche mit Konkurrenzprodukten. 
Die Funktion als Mehrwert für den Alltag darstellen.

K₄ Kontrolle: 
- Max. 150 Wörter
- Betreff + Anrede + 2 Absätze + Grußformel
- Am Ende: 1 Call-to-Action („Jetzt ausprobieren")
```

---

## Schritt 4: Stil und Tonalität gezielt steuern

Dieselbe Information klingt völlig anders, je nachdem, wer sie liest. Ein Quartalsbericht für den Vorstand ist nicht dasselbe wie eine Info-Mail an Mitarbeitende — auch wenn beides dieselben Zahlen enthält.

### Das Stil-Spektrum

Die KI hat fünf Stellschrauben für den Stil. Definieren Sie mindestens drei davon:

```
Stil-Parameter:
─────────────────────────────────────────────────────────
Formalität:     [ locker ←──────────→ hochformell ]
Komplexität:    [ einfach ←─────────→ fachlich    ]
Emotionalität:  [ sachlich ←────────→ motivierend ]
Länge:          [ prägnant ←────────→ ausführlich ]
Perspektive:    [ wir | Sie | du | man | neutral  ]
─────────────────────────────────────────────────────────
```

### Drei Zielgruppen, drei Stimmen

Dieselbe Nachricht — drei verschiedene Stile:

**Nachricht:** Die Volksbank Hellweg hat die Baufinanzierungsquote im Q4/2025 um 12% gesteigert.

---

**Zielgruppe A: Vorstand / Management**
```
STIL: Präzise, faktenorientiert, entscheidungsrelevant
PERSPEKTIVE: Neutral / „die Bank"
LÄNGE: Max. 3 Sätze
```
→ *„Die Baufinanzierungsquote stieg im Q4/2025 um 12% gegenüber dem Vorquartal. Haupttreiber: Sonderkondition ‚Eigentum25' und gezielte Nachfassaktion im Bestandskundenportfolio. Empfehlung: Sonderkondition auf Q1/2026 verlängern."*

---

**Zielgruppe B: Mitarbeitende (Intranet-Meldung)**
```
STIL: Kollegial, wertschätzend, motivierend
PERSPEKTIVE: „Wir"
LÄNGE: 4-5 Sätze
```
→ *„Starkes Quartal! Wir haben unsere Baufinanzierungsquote im Q4 um 12% gesteigert — das ist das beste Ergebnis seit zwei Jahren. Besonderer Dank an die Beraterinnen und Berater der Filialen Soest und Werl, die mit der ‚Eigentum25'-Kampagne den größten Beitrag geleistet haben. Ihr habt gezeigt, dass persönliche Beratung und digitale Tools Hand in Hand gehen können. Weiter so!"*

---

**Zielgruppe C: Kunden (Newsletter)**
```
STIL: Persönlich, vertrauenswürdig, einladend
PERSPEKTIVE: „Sie"
LÄNGE: 3-4 Sätze
```
→ *„Immer mehr Menschen in der Region Hellweg entscheiden sich für eine Baufinanzierung bei uns — und das freut uns sehr. Im letzten Quartal durften wir besonders viele Familien auf dem Weg ins Eigenheim begleiten. Haben auch Sie Pläne? Unsere Beraterinnen und Berater freuen sich auf ein Gespräch mit Ihnen."*

> **Volksbank-Analogie:** Denken Sie an den Jahresbericht. Dieselben Zahlen stehen im Vorstandsbericht (nüchtern, mit KPIs), im Mitarbeiter-Newsletter (feiernd, mit Dank) und in der Kundenbroschüre (vertrauenswürdig, mit Einladung). Drei Dokumente, drei Stimmen — ein und dieselbe Wahrheit. Die KI kann alle drei, wenn Sie ihr sagen, für wen sie schreibt.

### Stil-Transformation als Technik

Eine besonders mächtige Anwendung: Sie haben bereits einen Text und wollen ihn in eine andere Tonalität übersetzen.

```
Transformiere den folgenden internen Bericht in eine kundenfreundliche 
Version für den Newsletter:

[Interner Text:]
Die Konvertierungsrate im Segment U30 stieg um 8,3 Prozentpunkte 
auf 34,7%. Die Kampagne „Junge Profis" generierte 847 Leads bei 
einem CPL von 12,40€. Cross-Selling-Quote: 1,8 Produkte/Neukunde.

[Anforderungen an den Newsletter-Text:]
- Keine internen Kennzahlen
- Perspektive: „Sie" 
- Emotional: Vertrauen + Einladung
- Max. 80 Wörter
```

### Die Stellschrauben unter der Haube: Temperatur, Top-P & Co.

Neben Ihren Worten im Prompt gibt es **technische Parameter**, die das Verhalten der KI direkt beeinflussen. Die meisten KI-Tools lassen Sie diese einstellen — und es lohnt sich, sie zu kennen.

#### Temperatur: Der Kreativitätsregler

Erinnern Sie sich an Tutorial 00-01? Die KI berechnet für jedes nächste Wort Wahrscheinlichkeiten. Die **Temperatur** bestimmt, wie streng sie diesen Wahrscheinlichkeiten folgt.

```
Temperatur 0.0 ──────────────────── Temperatur 1.0
     │                                    │
     ▼                                    ▼
 Vorhersagbar                        Überraschend
 Wiederholbar                        Kreativ
 Faktenorientiert                    Abwechslungsreich
 Manchmal monoton                    Manchmal unsinnig
```

**Konkrete Empfehlungen für den Bankalltag:**

| Aufgabe | Temperatur | Warum |
|---|---|---|
| Compliance-Texte, Vertragsentwürfe | **0.1 – 0.3** | Fakten, keine Kreativität. Jede „Überraschung" ist ein Risiko. |
| Meeting-Protokolle, Berichte | **0.2 – 0.4** | Nah am Original bleiben, wenig Interpretation. |
| Kunden-E-Mails, interne Kommunikation | **0.4 – 0.6** | Etwas natürlicher Sprachfluss, aber kontrolliert. |
| Kampagnen-Ideen, Brainstorming | **0.6 – 0.8** | Kreativität erwünscht — Fakten separat prüfen! |
| Kreative Texte, Slogans, Social Media | **0.7 – 0.9** | Maximale Variation — aber Ergebnisse sichten. |

> **Volksbank-Analogie:** Temperatur ist wie der Unterschied zwischen einem Formularbrief und einem persönlichen Beratungsgespräch. Der Formularbrief (niedrige Temperatur) ist immer gleich, immer korrekt, aber auch immer steif. Das Beratungsgespräch (höhere Temperatur) ist lebendiger und individueller — aber es besteht die Gefahr, dass der Berater etwas Ungenaues sagt. In der Kreditabteilung: Temperatur niedrig. Im Marketing: Temperatur höher.

#### Top-P: Der Wortschatz-Filter

Während die Temperatur regelt, *wie mutig* die KI wählt, bestimmt **Top-P**, *aus wie vielen Kandidaten* sie überhaupt wählt.

```
Top-P = 0.1  → Nur die wahrscheinlichsten 10% der Wörter stehen zur Wahl
Top-P = 0.5  → Die oberen 50% — ausgewogener Wortschatz
Top-P = 0.95 → Fast alle Wörter sind möglich — maximale Vielfalt
```

**Faustregel:** Temperatur und Top-P verstärken sich gegenseitig. Für die meisten Anwendungen reicht es, **einen** der beiden Parameter anzupassen:

| Ziel | Empfehlung |
|---|---|
| Maximale Präzision (Fakten, Compliance) | Temperatur **0.2**, Top-P **0.3** |
| Ausgewogener Alltagseinsatz | Temperatur **0.5**, Top-P **0.7** |
| Kreative Vielfalt (Kampagnen, Ideen) | Temperatur **0.7**, Top-P **0.9** |

#### Weitere Parameter im Überblick

Nicht alle KI-Tools bieten alle Parameter an — aber wenn Sie Zugang haben, lohnt es sich:

| Parameter | Was er tut | Typischer Wert | Wann anpassen |
|---|---|---|---|
| **Temperatur** | Kreativität vs. Vorhersagbarkeit | 0.0 – 1.0 | Fast immer relevant |
| **Top-P** | Größe des Wortschatz-Pools | 0.1 – 1.0 | Bei Feinsteuerung |
| **Max. Tokens** | Maximale Länge der Ausgabe | 100 – 4.000+ | Wenn Ausgabe zu lang/kurz |
| **Frequency Penalty** | Bestraft Wiederholung von Wörtern | 0.0 – 2.0 | Bei repetitiven Ausgaben |
| **Presence Penalty** | Belohnt neue Themen/Begriffe | 0.0 – 2.0 | Bei monotonen Texten |
| **Stop-Sequenz** | KI stoppt bei bestimmtem Text (z.B. „---") | Frei definierbar | Bei Templates, automatisierter Verarbeitung |

#### Wo Sie diese Parameter einstellen

| Tool | Temperatur | Top-P | Max. Tokens | Weitere |
|---|---|---|---|---|
| **ChatGPT (Web)** | Nicht direkt einstellbar* | — | — | — |
| **ChatGPT (API)** | ✅ | ✅ | ✅ | ✅ Frequency/Presence Penalty |
| **Claude (Web)** | Nicht direkt einstellbar* | — | — | — |
| **Claude (API)** | ✅ | ✅ | ✅ | ✅ Stop-Sequenzen |
| **Gemini (Web)** | ✅ (in Advanced) | ✅ | ✅ | — |
| **Gemini (API)** | ✅ | ✅ | ✅ | ✅ Stop-Sequenzen |

*\*In den Web-Oberflächen von ChatGPT und Claude steuern Sie die „Temperatur" implizit über Ihre Wortwahl im Prompt: „Sei kreativ" → hohe Temperatur-Wirkung, „Sei exakt und faktentreu" → niedrige Temperatur-Wirkung. Die Modelle sind darauf trainiert, solche Anweisungen in ihr Verhalten zu übersetzen.*

**Praxis-Tipp:** Wenn Sie nur die Web-Oberfläche nutzen (kein API-Zugang), können Sie den Temperatur-Effekt im Prompt nachbilden:

```
Für niedrige Temperatur:
„Antworte faktenbasiert und präzise. Bevorzuge gebräuchliche 
Formulierungen. Keine kreativen Umschreibungen."

Für hohe Temperatur:
„Sei kreativ und überraschend. Nutze ungewöhnliche Metaphern 
und frische Formulierungen. Variiere den Satzbau."
```

---

## Schritt 5: Token-Bewusstsein — Schneller, günstiger, besser

Erinnern Sie sich an Token aus Tutorial 00-01? Jedes Wort, das Sie eingeben, und jedes Wort, das die KI ausgibt, kostet Token. Token kosten Zeit und Geld. Und: Das Kontextfenster — das „Arbeitsgedächtnis" der KI — ist begrenzt.

Token-Bewusstsein heißt nicht, an jeder Silbe zu sparen. Es heißt: **Nicht verschwenden, wo es nichts bringt.**

### Die drei Spar-Strategien

**Strategie 1: Abkürzungen definieren**

Wenn Sie in einem längeren Gespräch immer wieder dieselben Begriffe verwenden, definieren Sie Abkürzungen:

```
Ab jetzt verwende ich diese Abkürzungen:
VBH = Volksbank Hellweg
BF = Baufinanzierung
PKB = Privatkundenberatung
EA = Eigenkapitalanteil

Erstelle eine Vergleichstabelle: BF-Konditionen der VBH 
für Kunden mit EA >20% vs. EA <20%.
```

**Strategie 2: Format erzwingen statt Fließtext**

Fließtext verbraucht 2-3x so viele Token wie strukturierte Formate:

| Technik | Vorher (Token) | Nachher (Token) | Ersparnis |
|---|---|---|---|
| Abkürzungen & Glossar | ~150 | ~90 | ~40% |
| Tabelle statt Fließtext | ~300 | ~120 | ~60% |
| Bullet Points statt Absätze | ~250 | ~100 | ~60% |
| Wortlimit setzen | ~500 | ~200 | ~60% |

**Strategie 3: Inkrementell arbeiten**

Statt alles in einem riesigen Prompt zu fordern, arbeiten Sie in Schritten:

```
Schritt 1: „Liste die 5 größten Risiken bei der Einführung 
           eines neuen Online-Banking-Systems."
                     ↓
Schritt 2: „Detailliere Risiko 3 (Ursache, Wirkung, Gegenmaßnahme)."
                     ↓
Schritt 3: „Erstelle einen Maßnahmenplan für die Gegenmaßnahme 
           (Verantwortlich + Frist + KPI)."
```

Jeder Schritt verbraucht wenig Token, liefert fokussierte Ergebnisse und gibt Ihnen die Möglichkeit, nach jedem Schritt den Kurs zu korrigieren.

### Token-Fallen im Alltag

```
❌ „Könntest du bitte so freundlich sein und mir erklären, 
    wie das mit den neuen Konditionen zusammenhängt?"
   → 22 Wörter, davon 12 Füllwörter

✅ „Erkläre die neuen BF-Konditionen in 3 Bullet Points."
   → 8 Wörter, alles relevant
```

> **Volksbank-Analogie:** Token-Bewusstsein ist wie Kostenbewusstsein bei internen Projekten. Niemand schreibt ein 20-seitiges Memo, wenn eine halbe Seite reicht. Niemand bucht einen Konferenzraum für 50 Personen, wenn 5 kommen. Genauso verschwenden Sie keine Token für Höflichkeitsfloskeln, wenn die KI das nicht braucht. Die KI hat keine Gefühle, die Sie verletzen könnten — aber sie hat ein Token-Budget, das Sie schonen sollten.

---

## Schritt 6: Iteratives Verfeinern — Wenn das Ergebnis nicht passt

In Tutorial 01-01 haben Sie die Verfeinerungsschleife kennengelernt. Jetzt lernen Sie die **Debug-Methode** — ein systematischer Ansatz, wenn das Ergebnis nicht stimmt.

### Der Troubleshooting-Guide

| Problem | Symptom | Ursache | Lösung | Erfolgsquote |
|---|---|---|---|---|
| **Zu allgemein** | Generische Phrasen, keine konkreten Details | Fehlende Zielgruppe/Kontext | Zielgruppe + Kontext präzisieren | ~85% |
| **Falscher Stil** | Zu förmlich, zu salopp, zu werblich | Kein Tonalitätsrahmen | Stilparameter definieren (Schritt 4) | ~90% |
| **Falsches Format** | Fließtext statt Tabelle, Liste statt Absatz | Keine Format-Anweisung | Format explizit vorgeben (Schritt 2) | ~80% |
| **Zu lang** | 500 Wörter statt 150 | Kein Wortlimit | Wortanzahl oder Satzanzahl festlegen | ~95% |
| **Widersprüche** | Aussagen widersprechen sich | Kontext fehlt oder ist unklar | Referenztext mitgeben, Kontext schärfen | ~75% |
| **Halluziniert** | Erfundene Zahlen, falsche Fakten | Kein Fakten-Anker | Quellenanforderung + [UNGEPRÜFT]-Markierung | ~70% |

### Die Debug-Prompt-Technik

Wenn eine Ausgabe nicht stimmt, schreiben Sie keinen komplett neuen Prompt. Schreiben Sie einen **Debug-Prompt**, der das Problem benennt und die Korrektur definiert:

```
Die vorherige Ausgabe war zu allgemein und nicht vorstandstauglich. 
Bitte überarbeite:

1. Kürzer (max. 180 Wörter statt ~400)
2. Mehr Fakten, weniger Adjektive
3. Empfehlungen als nummerierte Bullet Points (nicht Fließtext)
4. Jede Zahl mit Quelle oder [PLATZHALTER]

Markiere Änderungen gegenüber der vorherigen Version mit → am Zeilenanfang.
```

**Der Trick mit dem →:** Wenn Sie die KI bitten, Änderungen zu markieren, sehen Sie sofort, was sie verändert hat — ohne beide Versionen Wort für Wort vergleichen zu müssen.

### Die Zwei-Iterationen-Regel

Eine Erkenntnis aus der Praxis: **Mehr als zwei Korrekturschleifen lohnen sich selten.** Wenn das Ergebnis nach zwei Debug-Prompts immer noch nicht passt, ist der Original-Prompt das Problem. Gehen Sie zurück und bauen ihn mit dem Struktur-Framework (Schritt 1) neu auf.

```
Iteration 0: Erster Prompt → Rohfassung
Iteration 1: Debug-Prompt → Korrektur 1 (Format, Länge, Ton)
Iteration 2: Fein-Tuning → Finale Version
    │
    └─ Wenn immer noch schlecht → Prompt von Grund auf neu bauen
```

> **Volksbank-Analogie:** Stellen Sie sich einen Kreditvorschlag vor, der nicht durch den Ausschuss kommt. Einmal überarbeiten: Zahlen korrigieren, Struktur anpassen. Zweimal überarbeiten: Risikobewertung nachschärfen. Beim dritten Mal zurückkommen? Dann stimmt das Konzept nicht — dann brauchen Sie keine Korrektur, sondern ein neues Konzept.

---

## Schritt 7: Output-Verträge — Die Profi-Technik

Die fortgeschrittenste Methode der Output-Steuerung: Sie formulieren einen **Vertrag** mit der KI. Nicht im juristischen Sinne — sondern als präzise Spezifikation, die das Ergebnis messbar macht.

Ein Output-Vertrag beantwortet drei Fragen:

1. **Was ist „fertig"?** → Erfolgskriterien
2. **Wie sieht es aus?** → Format-Spezifikation
3. **Wie prüfe ich es?** → Selbst-Check

### Output-Vertrag: Template

```
ZIEL: {{Ein Satz, was entstehen soll}}

ERFOLGSKRITERIEN:
- {{Muss-Kriterium 1}}
- {{Muss-Kriterium 2}}
- {{Darf-nicht: Was das Ergebnis NICHT enthalten soll}}

FORMAT:
- Abschnitt 1: {{Name}} ({{Constraints: Länge, Inhalt}})
- Abschnitt 2: {{Name}} ({{Constraints}})
- Abschnitt 3: {{Name}} ({{Constraints}})

STIL:
- Tonalität: {{sachlich | wertschätzend | motivierend}}
- Zielgruppe: {{Wer liest das?}}
- Perspektive: {{wir | Sie | du}}
- Max. Länge: {{Wörter / Sätze / Zeilen}}

SELBST-CHECK (vor der Ausgabe prüfen):
☐ Alle Erfolgskriterien erfüllt?
☐ Format exakt eingehalten?
☐ Keine Behauptungen ohne Quelle oder [UNGEPRÜFT]-Markierung?
☐ Länge eingehalten?
```

### Output-Vertrag in Aktion

```
ZIEL: Quartalsbericht Q4/2025 für die Vorstandssitzung 
      der Volksbank Hellweg.

ERFOLGSKRITERIEN:
- Enthält 5 KPIs mit Vorquartalsvergleich
- Jede Zahl mit Quelle oder [PLATZHALTER]
- Enthält genau 1 strategische Empfehlung
- Keine Marketing-Sprache, keine Superlative

FORMAT:
- Management Summary (3 Bullet Points, je max. 15 Wörter)
- KPI-Tabelle (Spalten: KPI | Q3/2025 | Q4/2025 | Δ | Bewertung)
- Analyse (max. 100 Wörter Fließtext)
- Empfehlung (1 Satz + 3 Maßnahmen als nummerierte Liste)
- Nächste Schritte (Tabelle: Was | Wer | Bis wann)

STIL:
- Tonalität: Sachlich, entscheidungsorientiert
- Zielgruppe: Vorstand (kein Erklären von Grundlagen)
- Perspektive: „Die Bank" / neutral
- Max. Länge: 300 Wörter gesamt

SELBST-CHECK:
☐ Genau 5 KPIs? Nicht 4, nicht 6?
☐ Jede Zahl quellenmarkiert?
☐ Management Summary ≤ 15 Wörter pro Punkt?
☐ Empfehlung in einem Satz formulierbar?
☐ Keine Adjektive wie „hervorragend", „beeindruckend"?
```

**Warum das funktioniert:** Aktuelle Modelle wie GPT-4, Claude und Gemini reagieren besonders gut auf checklisten-artige Constraints. Der Selbst-Check am Ende sorgt dafür, dass das Modell seine eigene Ausgabe gegen Ihre Kriterien prüft, *bevor* es sie ausgibt. Das reduziert Fehler messbar.

> **Volksbank-Analogie:** Ein Output-Vertrag ist wie eine Arbeitsanweisung in der Kreditabteilung. Dort steht nicht „Bitte prüfen Sie den Kredit." Dort steht: „Prüfen Sie: Eigenkapitalquote ≥20%? Schufa-Score ≥C? Beleihungsauslauf ≤80%? Wenn alle ja: Weitergabe an Kreditausschuss. Wenn nein: Ablehnung mit Begründung, Format: Standardbrief V-4.2." Klare Erfolgskriterien, klares Format, klare Prüfschritte. Genau das gibt der Output-Vertrag der KI.

---

## Schritt 8: Komplexe Aufgaben orchestrieren — Prompt-Ketten

Manchmal ist eine Aufgabe zu groß für einen einzelnen Prompt. Dann zerlegen Sie sie in eine **Prompt-Kette**: Eine Sequenz von Prompts, bei der das Ergebnis des einen in den nächsten einfließt.

### Beispiel: Vorbereitung einer Vertriebskampagne

```
PROMPT-SEQUENZ:

Prompt 1: „Erstelle eine Executive Summary (max. 100 Wörter) 
           zur Vertriebskampagne ‚Frühjahrs-BF 2026'."
           → Ergebnis speichern als {SUMMARY}

Prompt 2: „Entwickle auf Basis dieser Summary drei Kampagnenvarianten 
           mit Fokus: Social Media, Filiale, Events.
           
           Summary: {SUMMARY}"
           → Ergebnis speichern als {VARIANTEN}

Prompt 3: „Für Variante 1 (Social Media) erstelle:
           - Content-Plan (8 Posts über 4 Wochen)
           - Textentwürfe (max. 200 Zeichen pro Post)
           - 3 Hashtag-Vorschläge
           
           Kampagnen-Summary: {SUMMARY}
           Varianten-Übersicht: {VARIANTEN}"
```

**Warum Prompt-Ketten?**
- Jeder Schritt ist fokussiert → bessere Qualität
- Sie können nach jedem Schritt prüfen und korrigieren
- Token-effizienter als ein Mega-Prompt
- Ergebnisse sind modular wiederverwendbar

### Prompt-Ketten im Modellvergleich

Ein wichtiger Unterschied: Nicht jedes Modell handhabt Ketten gleich.

| Aspekt | ChatGPT | Claude | Gemini |
|---|---|---|---|
| **Chat-Verlauf** | Erinnert sich innerhalb der Session | Erinnert sich innerhalb der Session | Erinnert sich innerhalb der Session |
| **Lange Kontexte** | Bis ~128.000 Token | Bis ~200.000 Token | Bis ~1.000.000 Token |
| **Stärke bei Ketten** | Gute Format-Treue bei jedem Schritt | Exzellent bei langen, strukturierten Ketten | Sehr gut bei großen Datenmengen als Input |
| **Tipp** | Zwischenergebnisse explizit zusammenfassen | Vertrag + Selbst-Check bei jedem Schritt | Längere Kontexte nutzen, weniger Schritte nötig |

> **Volksbank-Analogie:** Prompt-Ketten sind wie ein Kreditprozess. Schritt 1: Vorprüfung (passt der Kunde grundsätzlich?). Schritt 2: Detailprüfung (Bonität, Sicherheiten). Schritt 3: Kreditvorschlag erstellen. Schritt 4: Vorstandsvorlage. Jeder Schritt baut auf dem vorherigen auf, aber jeder Schritt hat eigene Regeln, eigene Verantwortliche und eigene Prüfkriterien. Niemand würde versuchen, das alles in einem einzigen Formular zu erledigen.

---

## Was diese Techniken (noch) nicht können

Selbst mit perfekter Output-Steuerung gibt es Grenzen — und im Bankumfeld ist es besonders wichtig, diese zu kennen.

| Grenze | Was das bedeutet | Workaround |
|---|---|---|
| **Formatgarantie ist keine Faktengarantie** | Eine perfekt formatierte Tabelle kann trotzdem falsche Zahlen enthalten | Immer: Fakten separat prüfen. Format ≠ Wahrheit |
| **Längenangaben sind Richtwerte** | „Max. 150 Wörter" kann ±20% abweichen — KI zählt keine Wörter exakt | Toleranz einplanen oder per Nachkorrektur kürzen |
| **Stil-Feinsteuerung hat Grenzen** | „Exakt wie unser CEO schreiben würde" überfordert die KI ohne Beispiele | 2-3 Beispieltexte mitgeben, die den Stil zeigen |
| **JSON kann brechen** | Bei sehr langen oder verschachtelten Ausgaben kann die KI ungültiges JSON produzieren | Schema-Validierung nachschalten, Ausgabelänge begrenzen |
| **Corporate Language muss trainiert werden** | Die KI kennt Ihre internen Formulierungen nicht | Glossar + Stilbeispiele im Prompt mitgeben |
| **Compliance-Texte brauchen Menschen** | Die KI kann Entwürfe liefern, aber keine rechtsverbindlichen Formulierungen garantieren | KI für Entwurf, Fachabteilung für Freigabe |

**Besonders im Bankumfeld:**
- **Vertragstexte:** KI kann Entwürfe erstellen, aber die Rechtsabteilung muss freigeben
- **Zinssätze und Konditionen:** Niemals aus der KI übernehmen — immer aus dem Quellsystem
- **Kundendaten:** Gehören nicht in öffentliche KI-Tools (DSGVO!)
- **BaFin-konforme Dokumente:** KI kennt die aktuellen Rundschreiben nicht — immer gegenprüfen

> **Faustregel:** Die Techniken aus diesem Tutorial machen die KI-Ausgabe *sofort nutzbarer* — aber sie machen sie nicht *automatisch korrekt*. Format-Kontrolle ist Qualität der Darstellung. Fakten-Kontrolle bleibt Menschensache.

---

## Was es kostet — und was es spart

| Aufgabe | Ohne Technik (02-01 Basics) | Mit Output-Steuerung (02-02) | Verbesserung |
|---|---|---|---|
| Vorstandsvorlage erstellen | 3 Iterationen, ~15 Min | 1 Iteration + 1 Debug, ~5 Min | ~65% schneller |
| E-Mail in 3 Zielgruppen-Varianten | 3 separate Prompts, ~10 Min | 1 Prompt mit Stil-Parametern, ~4 Min | ~60% schneller |
| Quartalsbericht formatieren | KI liefert Fließtext, manuell umformatieren ~20 Min | KI liefert im Zielformat, ~3 Min Review | ~85% schneller |
| Meeting-Protokoll aus Notizen | Mehrfach nachkorrigieren ~15 Min | Output-Vertrag, 1. Ergebnis brauchbar ~5 Min | ~65% schneller |

**Token-Kosten:**

| Prompt-Typ | Ø Token (Input + Output) | Ø Kosten (GPT-4 API) | Ø Kosten (Claude API) |
|---|---|---|---|
| Einfacher Prompt ohne Struktur | ~800 Token | ~0,04€ | ~0,04€ |
| Strukturierter Prompt mit 4-K | ~500 Token | ~0,025€ | ~0,025€ |
| Output-Vertrag (komplex) | ~1.200 Token | ~0,06€ | ~0,06€ |
| 3-Schritt-Prompt-Kette | ~1.500 Token | ~0,075€ | ~0,075€ |

**Die Rechnung:** Ein gut strukturierter Prompt mit Output-Vertrag kostet ~50% mehr Token als ein einfacher Prompt — spart aber 2-3 Korrekturschleifen, die jeweils eigene Token verbrauchen. Netto: günstiger *und* schneller.

| Vergleich | Menschlich (ohne KI) | KI mit Output-Steuerung |
|---|---|---|
| Vorstandsvorlage (1 Seite) | 2-3 Std, Senior-Level | 15 Min, jedes Level |
| Quartalsbericht (Entwurf) | 4-6 Std | 30-45 Min + Review |
| 10 Kunden-E-Mails (personalisiert) | 3-4 Std | 30 Min + Prüfung |
| Kampagnen-Konzept (Grobstruktur) | 1-2 Tage | 2-3 Std + Feinschliff |

---

## Die Output-Pipeline auf einen Blick

```
┌──────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────┐    ┌──────────┐
│  BEDARF  │    │  STRUKTUR    │    │    PROMPT     │    │  OUTPUT  │    │  PRÜFUNG │
│ erkennen │ →  │  planen      │ →  │  mit Vertrag │ →  │  prüfen  │ →  │  nutzen  │
│          │    │              │    │  senden      │    │          │    │  oder    │
│ Was?     │    │ Container    │    │              │    │ Format?  │    │  Debug   │
│ Für wen? │    │ Komponenten  │    │ 4-K oder     │    │ Inhalt?  │    │          │
│ Welches  │    │ Constraints  │    │ 6 Bausteine  │    │ Ton?     │    │          │
│ Format?  │    │ Format       │    │ + Output-    │    │ Länge?   │    │          │
│          │    │ Stil         │    │   Vertrag    │    │          │    │          │
└──────────┘    └──────────────┘    └──────────────┘    └──────────┘    └──────────┘
       ↑                                                       │
       └────────────── Debug-Prompt bei Problemen ◄────────────┘
```

---

## Das Wichtigste auf einen Blick

| Technik | Was sie tut | Wann nutzen |
|---|---|---|
| **Struktur-Framework** | Gliedert Ausgabe in Container → Komponenten → Constraints | Immer, wenn das Ergebnis mehr als 3 Sätze hat |
| **4-K-Formel** | Schnell-Check: Kontext, Konkrete Aufgabe, Kriterien, Kontrolle | Für alltägliche Prompts (E-Mails, kurze Texte) |
| **Format-Palette** | Tabelle, Liste, Template, Fließtext, JSON — je nach Zweck | Immer Format explizit angeben |
| **Stil-Parameter** | Formalität, Komplexität, Emotionalität, Länge, Perspektive | Wenn Zielgruppe klar ist (Vorstand ≠ Kunden ≠ Kollegen) |
| **Temperatur & Top-P** | Technische Regler für Kreativität vs. Präzision | Fakten: niedrig (0.2), Kreativ: hoch (0.7) |
| **Token-Strategien** | Abkürzungen, Format erzwingen, inkrementell arbeiten | Bei häufiger KI-Nutzung, API-Kosten, langen Gesprächen |
| **Debug-Methode** | Problem benennen → Korrektur definieren → max. 2 Iterationen | Wenn die erste Ausgabe nicht passt |
| **Output-Vertrag** | Erfolgskriterien + Format + Selbst-Check als „Spezifikation" | Für wichtige Dokumente (Vorstandsvorlagen, Kampagnen, Berichte) |
| **Prompt-Ketten** | Komplexe Aufgaben in Sequenz zerlegen | Wenn 1 Prompt zu viel auf einmal verlangt |

---

## Parallelen zu vorherigen Tutorials

| Konzept in diesem Tutorial | Woher Sie es kennen |
|---|---|
| 6 Bausteine eines Prompts → 4-K als Schnellversion | Tutorial 01-01: Die 6 Bausteine |
| Format-Angabe als Baustein 6 | Tutorial 01-01: Schritt 8 (Format) |
| Token als Kosten- und Qualitätsfaktor | Tutorial 00-01: Token-Kosten und Context Window |
| Iteratives Verfeinern → Debug-Methode als Erweiterung | Tutorial 01-01: Schritt 10 (Iterativ verbessern) |
| Attention-Gewichte reagieren auf Struktur im Prompt | Tutorial 00-01: Attention-Mechanismus |
| Kontextfenster als Grund für Token-Sparsamkeit | Tutorial 00-01: Context Window |
| Halluzinationen → Format-Qualität ≠ Inhalts-Qualität | Tutorial 01-01: Schritt 9 (Halluzinationen) |
| Temperatur beeinflusst Wortauswahl bei der Generierung | Tutorial 00-01: Temperatur und Sampling |

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: „Vom Fließtext zur Struktur"

**Ihre Aufgabe:** Nehmen Sie diesen vagen Prompt und verwandeln Sie ihn mit dem Struktur-Framework in eine professionelle Anfrage.

**Ausgangsprompt:**
```
Schreib einen Bericht über die Kundenzufriedenheit in unserer Filiale.
```

**Szenario:** Die Volksbank Hellweg hat im Q4/2025 eine Kundenbefragung in der Filiale Soest durchgeführt (Rücklaufquote 34%, 847 Teilnehmer). Die Ergebnisse sollen als 1-Seiten-Vorlage für die Filialleitung aufbereitet werden.

Öffnen Sie ChatGPT, Claude oder Gemini und erstellen Sie einen Prompt mit:
- Mindestens 3 Containern (z.B. Summary, Ergebnisse, Maßnahmen)
- Komponenten pro Container (was genau drin stehen soll)
- Constraints (Stil, Länge, Zielgruppe)

**Vergleichen Sie:** Wie unterscheidet sich das Ergebnis vom Ausgangsprompt?

<details>
<summary>💡 Beispiel-Lösung anzeigen</summary>

```
Erstelle einen Kundenzufriedenheitsbericht für die Filiale Soest 
der Volksbank Hellweg.

[Zusammenfassung]
- 3 Kernaussagen, je max. 1 Satz
- Gesamtbewertung als Schulnote (Platzhalter: [NOTE])

[Ergebnisse]
- Tabelle: Kategorie | Bewertung (1-5) | Vorjahr | Trend (↑↓→)
- Kategorien: Beratungsqualität, Wartezeit, Erreichbarkeit, 
  Freundlichkeit, Digitale Angebote
- Rücklaufquote: 34% (847 Teilnehmer) — Einordnung, 
  ob statistisch aussagekräftig

[Handlungsfelder]
- Top 3 Stärken (je 1 Satz + konkretes Zitat aus Befragung [ZITAT])
- Top 3 Verbesserungsfelder (je 1 Satz + Maßnahmenvorschlag)

[Nächste Schritte]
- To-do-Tabelle: Maßnahme | Verantwortlich | Frist | KPI

Constraints:
- Max. 1 A4-Seite
- Ton: sachlich, lösungsorientiert
- Zielgruppe: Filialleitung (kein Erklären von Grundlagen)
- Platzhalter für interne Zahlen: [ZAHL] / [NOTE] / [ZITAT]
```
</details>

---

### Hands-on 2: „Die Stil-Transformation" (Modellvergleich)

**Ihre Aufgabe:** Testen Sie, wie verschiedene KI-Modelle mit Stil-Transformationen umgehen.

**Geben Sie diesen Prompt an mindestens 2 verschiedene KI-Modelle** (ChatGPT + Claude, oder ChatGPT + Gemini):

```
Transformiere diesen internen Sachtext in drei Versionen:

[Sachtext:]
Die Volksbank Hellweg führt ab 01.04.2026 ein neues digitales 
Beratungstool ein. Kunden können künftig per Videocall beraten 
werden. Die Investitionskosten betragen 120.000€. Die erwartete 
Steigerung der Beratungstermine liegt bei 25%. Die Implementierung 
dauert 8 Wochen.

Version A — Vorstandsvorlage:
Stil: sachlich, KPI-fokussiert, max. 80 Wörter

Version B — Mitarbeitende (Intranet):
Stil: motivierend, wertschätzend, max. 100 Wörter

Version C — Kundennewsletter:
Stil: einladend, vertrauenswürdig, max. 80 Wörter, keine internen Zahlen
```

**Vergleichen Sie:**
- Welches Modell trifft die Zielgruppen-Tonalität besser?
- Hält jedes Modell die Wortlimits ein?
- Welches Modell lässt in Version C konsequent die internen Zahlen weg?

---

### Hands-on 3: „Der Output-Vertrag"

**Ihre Aufgabe:** Erstellen Sie einen Output-Vertrag für eine Aufgabe aus Ihrem echten Arbeitsalltag.

**Schritt 1:** Wählen Sie eine Aufgabe, die Sie regelmäßig machen:
- Monatlicher Statusbericht
- Kunden-E-Mail zu Produktänderungen
- Protokoll einer Besprechung
- Stellenanzeige

**Schritt 2:** Formulieren Sie einen Output-Vertrag nach dem Template aus Schritt 7:
- ZIEL (1 Satz)
- ERFOLGSKRITERIEN (3-5 Punkte)
- FORMAT (Abschnitte mit Constraints)
- STIL (Tonalität, Zielgruppe, Perspektive, Länge)
- SELBST-CHECK (4-5 Prüfpunkte)

**Schritt 3:** Testen Sie den Vertrag mit einer KI Ihrer Wahl. Wie gut hält sie sich daran?

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **Container** | Ein Hauptabschnitt einer KI-Ausgabe (z.B. Summary, Analyse, Empfehlung) — die oberste Strukturebene |
| **Komponente** | Ein Unterelement innerhalb eines Containers (z.B. Zahlen, Argumente, Beispiele) |
| **Constraint** | Eine Einschränkung, die das Ergebnis formt (Wortlimit, Tonalität, Verbote) |
| **4-K-Formel** | Schnell-Check für Prompts: Kontext, Konkrete Aufgabe, Kriterien, Kontrolle |
| **Output-Vertrag** | Eine formale Spezifikation für KI-Ausgaben mit Erfolgskriterien, Format und Selbst-Check |
| **Debug-Prompt** | Ein Nachfolge-Prompt, der ein spezifisches Problem der vorherigen Ausgabe benennt und korrigiert |
| **Prompt-Kette** | Eine Sequenz von aufeinander aufbauenden Prompts für komplexe Aufgaben |
| **Stil-Parameter** | Steuerungsgrößen für den Ton einer Ausgabe: Formalität, Komplexität, Emotionalität, Länge, Perspektive |
| **Temperatur** | Parameter, der steuert, wie „kreativ" vs. „vorhersagbar" die KI antwortet (0.0 = exakt, 1.0 = kreativ) |
| **Top-P** | Parameter, der den Wortschatz-Pool der KI filtert — niedrig = nur wahrscheinlichste Wörter, hoch = mehr Vielfalt |
| **Frequency Penalty** | Bestraft die KI für Wortwiederholungen — höhere Werte erzwingen abwechslungsreichere Sprache |
| **Presence Penalty** | Belohnt die KI für neue Themen/Begriffe — nützlich gegen monotone Ausgaben |
| **Stop-Sequenz** | Ein definierter Text, bei dem die KI ihre Ausgabe automatisch beendet (z.B. „---" oder „ENDE") |
| **Token** | Kleinste Verarbeitungseinheit der KI (ca. ¾ eines deutschen Wortes, vgl. Tutorial 00-01) |
| **Structured Output** | Technische Funktion moderner KI-APIs, die garantiert valides JSON nach einem Schema liefert |
| **Inkrementelles Prompting** | Komplexe Aufgaben in kleine, aufeinander aufbauende Schritte zerlegen |
| **Format-Spezifikation** | Explizite Angabe des gewünschten Ausgabeformats (Tabelle, Liste, JSON, Template, etc.) |
| **Iteration** | Ein Durchlauf der Prompt-Korrektur-Schleife: Prompt → Ausgabe → Bewertung → Verbesserung |

---

