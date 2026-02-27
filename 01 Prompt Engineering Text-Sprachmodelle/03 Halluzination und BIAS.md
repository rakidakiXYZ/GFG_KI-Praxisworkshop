# Halluzinationen & Bias erkennen und vermeiden

**Wenn die KI lügt, ohne es zu wissen — und warum das im Bankwesen besonders gefährlich ist**

---

## Warum dieses Tutorial?

In Tutorial 01-01 haben Sie gelernt, gute Prompts zu bauen. In Tutorial 01-02 haben Sie gelernt, KI-Ausgaben zu steuern — Format, Stil, Länge. Sie können der KI jetzt klare Aufträge geben und bekommen strukturierte, professionelle Ergebnisse.

Aber hier kommt die unangenehme Wahrheit: **Ein perfekt formatierter Text kann trotzdem komplett falsch sein.**

Stellen Sie sich vor, ein Praktikant liefert Ihnen einen makellos formatierten Quartalsbericht. Saubere Tabellen, professioneller Ton, klare Handlungsempfehlungen. Sie leiten ihn an den Vorstand weiter. Beim nächsten Meeting stellt sich heraus: Die Zahlen sind frei erfunden. Der Praktikant hat nicht gelogen — er hat einfach Lücken gefüllt, weil er dachte, er wüsste die Antwort. Er klang dabei so überzeugend, dass niemand nachgefragt hat.

Genau so funktioniert eine KI-Halluzination. Und im Bankwesen — wo falsche Zahlen zu falschen Kreditentscheidungen führen, wo erfundene Regulierungen Compliance-Verstöße auslösen und wo verzerrte Analysen Kunden benachteiligen — ist das kein theoretisches Problem. Es ist ein Haftungsrisiko.

Dieses Tutorial macht Sie zum **Qualitätsprüfer**. Sie lernen nicht nur, was Halluzinationen und Bias sind, sondern wie Sie sie erkennen, bevor Schaden entsteht — und wie Sie Ihre Prompts so bauen, dass sie gar nicht erst auftreten.

**Was Sie nach diesem Tutorial können:**

- Erklären, warum KI halluziniert — und warum sie dabei so überzeugend klingt
- Die 5 häufigsten Halluzinations-Typen im Bankwesen erkennen
- Prompts bauen, die Halluzinationen systematisch reduzieren
- Versteckte Vorurteile (Bias) in KI-Antworten aufdecken — mit der Gender-Swap-Technik
- Eine Faktenprüfungs-Routine für Ihren Arbeitsalltag anwenden
- Einschätzen, wo KI helfen kann und wo der Mensch entscheiden muss

---

## Ein Blick zurück: Wie das Problem entdeckt wurde

Halluzinationen sind kein Bug, der eines Tages gefixt wird. Sie sind ein Grundprinzip der Funktionsweise von Sprachmodellen. Die Geschichte zeigt, wie das Problem erkannt, benannt und — teilweise — gemildert wurde.

| Jahr | Meilenstein | Bedeutung |
|---|---|---|
| **2020** | GPT-3 veröffentlicht | Erste breite Nutzung zeigt: Das Modell erfindet Fakten, Zitate und sogar Personen |
| **2022** | Meta Galactica (3 Tage online) | Wissenschafts-KI erfand akademische Paper mit plausiblen Titeln, Autoren und DOIs — wurde nach 3 Tagen vom Netz genommen |
| **2023** | Anwalt Mata vs. Avianca | Ein New Yorker Anwalt reichte von ChatGPT erfundene Gerichtsurteile ein — mit korrektem Aktenzeichen-Format, aber komplett fiktivem Inhalt. 5.000$ Strafe |
| **2023** | EU AI Act: Entwurf verabschiedet | Erste Regulierung weltweit, die Transparenzpflichten für KI-Systeme festschreibt — auch für Halluzinationsrisiken |
| **2024** | Structured Outputs & Grounding | Technische Gegenmaßnahmen: Modelle können auf verifizierte Quellen beschränkt werden (RAG, Grounding) |
| **2025** | Sub-1%-Halluzinationsraten | Erstmals erreichen 4 Modelle unter 1% Halluzinationsrate (Vectara-Benchmark). Aber: In spezialisierten Domänen wie Recht liegt die Rate weiterhin bei 6,4% |
| **2025** | HalluLens-Benchmark (ACL 2025) | Erster standardisierter akademischer Benchmark speziell für Halluzinations-Messung |
| **2026** | Debatte „Halluzination" vs. „Konfabulation" | Wissenschaftler argumentieren: Der korrektere Begriff wäre „Konfabulation" — das Modell „sieht" nichts, es füllt Lücken. Wie ein Patient mit Gedächtnisstörung, der sich Erinnerungen erfindet |

**Die Entwicklung zeigt:** Halluzinationen werden seltener, aber sie verschwinden nicht. Die besten Modelle liegen bei 0,7% — das klingt wenig, bedeutet aber: Bei 1.000 Fragen sind ~7 Antworten frei erfunden. Und das Tückische: Sie klingen genauso überzeugend wie die 993 korrekten.

---

## Schritt 1: Warum KI halluziniert — die technische Wahrheit

Erinnern Sie sich an Tutorial 00-01? Ein LLM berechnet für jedes nächste Wort die Wahrscheinlichkeit. Es wählt nicht aus einer Wissensdatenbank — es vervollständigt Muster. Das ist der entscheidende Punkt:

**KI weiß nichts. KI vervollständigt.**

```
Sie fragen:  „Wie hoch ist der aktuelle Basiszins der EZB?"

Was passiert:
┌──────────────────────────────────────────────────────────────┐
│  Das Modell sucht NICHT in einer Datenbank nach.             │
│  Es berechnet: Nach dem Muster „Basiszins der EZB ist..."    │
│  folgt mit hoher Wahrscheinlichkeit eine Prozentzahl.        │
│                                                              │
│  Welche Zahl? Die, die in den Trainingsdaten am häufigsten   │
│  in diesem Kontext vorkam. Das kann der Zinssatz von 2023,   │
│  2024 oder ein Durchschnitt sein — oder eine Mischung.       │
└──────────────────────────────────────────────────────────────┘
```

### Die 4 Mechanismen hinter Halluzinationen

**1. Mustervervollständigung ohne Wissen**

Das Modell hat kein Verständnis von „wahr" oder „falsch". Es kennt nur: „Was folgt wahrscheinlich auf diesen Text?" Wenn Sie nach dem Geschäftsführer einer kleinen Volksbank fragen, erfindet es einen plausibel klingenden deutschen Namen — weil das Muster „Geschäftsführer + Volksbank + Name" in den Trainingsdaten häufig vorkommt.

> **Volksbank-Analogie:** Stellen Sie sich einen neuen Mitarbeiter vor, der am ersten Tag alle Kundennamen auswendig aufsagen soll. Er kennt die echten Namen nicht, aber er weiß, dass deutsche Bankkunden typischerweise Müller, Schmidt oder Fischer heißen. Also rät er — und klingt dabei erstaunlich überzeugend.

**2. Überanpassung an Muster (Overfitting)**

Aus einzelnen Datenpunkten werden allgemeine Aussagen. Wenn in den Trainingsdaten drei Artikel standen, dass Volksbanken ihre Filialen schließen, könnte das Modell behaupten: „Der Trend zur Filialschließung ist bei allen Genossenschaftsbanken unumkehrbar." Eine Verallgemeinerung, die so nicht stimmt.

**3. Kontext-Drift**

Bei langen Gesprächen „vergisst" das Modell den Anfang. Sie fragen nach Baufinanzierungskonditionen der Volksbank, reden dann über Zinsentwicklung allgemein, und plötzlich antwortet die KI mit Konditionen einer Großbank — weil der Kontext „Volksbank" aus dem Aufmerksamkeitsfenster gerutscht ist.

> **Volksbank-Analogie:** Wie ein Beratungsgespräch, das nach 90 Minuten abdriftet. Der Kunde fragte nach einem Tagesgeldkonto, aber nach diversen Umwegen über Fonds und Versicherungen empfiehlt der Berater plötzlich eine Lebensversicherung — die ursprüngliche Frage ist vergessen.

**4. Temperatur-verstärkte Kreativität**

Aus Tutorial 01-02 wissen Sie: Höhere Temperatur = kreativere Antworten. Was bei Kampagnen-Ideen erwünscht ist, wird bei Fakten gefährlich. Bei Temperatur 0.8 „traut" sich das Modell, auch unwahrscheinlichere Wörter zu wählen — und ein unwahrscheinlicheres Wort bei einer Prozentangabe ist schlicht eine falsche Zahl.

---

## Schritt 2: Die 5 Halluzinations-Typen im Bankwesen

Nicht alle Halluzinationen sind gleich. Im Bankumfeld gibt es fünf typische Muster, die Sie kennen sollten:

| Typ | Was passiert | Bankbeispiel | Gefährlichkeit |
|---|---|---|---|
| **Fakten-Halluzination** | Frei erfundene Zahlen, Daten oder Personen | „Der Basiszins der EZB liegt aktuell bei 3,25%" (veraltet oder falsch) | 🔴 Sehr hoch |
| **Quellen-Halluzination** | Erfundene Studien, Gesetze oder Paragraphen | „Laut §47a KWG sind Genossenschaftsbanken verpflichtet..." (Paragraph existiert nicht) | 🔴 Sehr hoch |
| **Logik-Halluzination** | Plausibel klingende, aber falsche Schlussfolgerungen | „Da die Eigenkapitalquote gestiegen ist, sinkt automatisch das Kreditausfallrisiko" (stimmt nicht pauschal) | 🟠 Hoch |
| **Aktualitäts-Halluzination** | Veraltete Informationen als aktuell präsentiert | „Die aktuelle DSGVO-Novelle von 2024 schreibt vor..." (es gab keine Novelle 2024) | 🟠 Hoch |
| **Kontext-Halluzination** | Korrekte Information, falscher Zusammenhang | Regulierung einer Großbank wird auf eine Genossenschaftsbank angewandt, obwohl andere Regeln gelten | 🟡 Mittel |

### Woran Sie Halluzinationen erkennen — 7 Warnsignale

```
🚩 WARNSIGNAL-CHECKLISTE

□ 1. Sehr spezifische Zahlen ohne Quellenangabe
     „Die Kundenzufriedenheit liegt bei 87,3%"
     → Woher kommt die Nachkommastelle?

□ 2. Exakte Paragraphen oder Gesetze
     „Gemäß §14 Abs. 3 BaFin-Rundschreiben 12/2025..."
     → Im Zweifel: Existiert das Rundschreiben überhaupt?

□ 3. Vermeintliche Zitate von Personen
     „BVR-Präsidentin Kolak sagte im Januar 2026..."
     → KI erfindet gerne plausible Zitate

□ 4. Absolute Aussagen ohne Einschränkung
     „Alle Genossenschaftsbanken haben ihre Filialen um 30% reduziert"
     → „Alle" und exakte Prozentzahlen = Alarmzeichen

□ 5. Nahtloser Übergang von Fakt zu Fiktion
     Drei korrekte Aussagen, dann eine erfundene —
     im selben selbstbewussten Tonfall
     → Das gefährlichste Muster: Die Mischung macht es glaubwürdig

□ 6. Nicht existierende Fachbegriffe
     „Das sogenannte Geno-Compliance-Framework schreibt vor..."
     → Wenn Sie den Begriff nicht kennen: googeln, bevor Sie ihn verwenden

□ 7. Fehlender Hinweis auf Unsicherheit
     Die KI sagt nie „ich bin mir nicht sicher" oder
     „dazu habe ich keine aktuellen Daten"
     → Wenn die KI zu allem eine Antwort hat, hat sie zu manchen
       Dingen eine erfundene Antwort
```

> **Volksbank-Analogie:** In der Kreditprüfung gibt es das Vier-Augen-Prinzip. Warum? Weil ein einzelner Prüfer Fehler übersehen kann — nicht aus Nachlässigkeit, sondern weil plausible Unterlagen überzeugend wirken. Genau so funktioniert es mit KI-Ausgaben: Sie klingen professionell, also hinterfragen wir sie seltener. Das Vier-Augen-Prinzip für KI heißt: **Jede faktische Aussage gegen eine Primärquelle prüfen.**

---

## Schritt 3: Prompts, die Halluzinationen reduzieren

Die gute Nachricht: Sie können durch Ihre Prompt-Technik Halluzinationen systematisch senken. Hier sind die fünf wirksamsten Techniken:

### Technik 1: Quellenpflicht erzwingen

**❌ Halluzinations-anfällig:**
```
Wie ist die aktuelle Lage im Baufinanzierungsmarkt?
```

**✅ Halluzinations-resistent:**
```
Erstelle eine faktenbasierte Kurzlage (max. 10 Sätze) zum 
Baufinanzierungsmarkt in Deutschland.

REGELN:
1) Nutze NUR offizielle/verifizierte Quellen 
   (z.B. Bundesbank, Statistisches Bundesamt, BVR-Berichte).
2) Nenne das genaue Datum der verwendeten Zahlen.
3) Markiere Informationen älter als 6 Monate mit [Veraltet].
4) Eigene Ableitungen als [Einschätzung] kennzeichnen.
5) Wenn du keine aktuelle Quelle hast, schreibe: 
   [Keine aktuelle Quelle verfügbar — intern prüfen].
```

**Warum das funktioniert:** Die Quellenpflicht zwingt das Modell, seine Antwort an konkrete Referenzen zu binden. Wenn es keine echte Quelle hat, muss es das zugeben — statt eine zu erfinden. Das funktioniert nicht perfekt (das Modell kann auch Quellen halluzinieren), aber es reduziert die Halluzinationsrate messbar, weil es einen zusätzlichen Prüfschritt in den Generierungsprozess einbaut.

### Technik 2: Fakten von Einschätzungen trennen

```
Erstelle ein Management-Briefing zur Mitgliederentwicklung 
der Volksbank Hellweg.

TRENNUNG:
- [FAKT]: Nur Aussagen mit konkreter Quelle und Datum
- [EINSCHÄTZUNG]: Eigene Ableitungen, klar als solche markiert  
- [KEINE DATEN]: Wenn dir aktuelle Zahlen fehlen

Am Ende: Prüfliste „Was intern zu verifizieren ist"
```

> **Volksbank-Analogie:** In einem Kreditgutachten trennen Sie auch: Bonitätsdaten (Fakt) von Prognosen (Einschätzung) von fehlenden Unterlagen (Lücke). Niemand käme auf die Idee, eine Prognose als Fakt zu behandeln. Genau diese Disziplin brauchen Sie bei KI-Ausgaben.

### Technik 3: Temperatur bewusst steuern

Aus Tutorial 01-02 kennen Sie bereits die Temperatursteuerung. Hier die spezifische Anwendung für Halluzinations-Vermeidung:

| Aufgabe | Temperatur | Warum |
|---|---|---|
| Compliance-Texte, Rechtsauslegung | **0.1 – 0.2** | Null Kreativität. Jede „Überraschung" ist ein Risiko |
| Management-Briefings, Berichte | **0.2 – 0.3** | Nah am Quellmaterial bleiben |
| Kunden-E-Mails | **0.3 – 0.5** | Etwas natürlicher, aber faktengebunden |
| Kampagnen-Ideen | **0.6 – 0.8** | Kreativität erwünscht — Fakten separat prüfen! |

**Faustregel:** Je höher die Konsequenz eines Fehlers, desto niedriger die Temperatur.

### Technik 4: Step-by-Step-Struktur

Statt einer offenen Frage, die das Modell in jede Richtung treiben kann, geben Sie Denkschritte vor:

```
Analysiere die Kundenzufriedenheitsdaten unserer Filiale Soest.
Gehe dabei in exakt diesen Schritten vor:

Schritt 1: Nenne die verfügbaren Datenpunkte 
           (nur die, die du sicher aus dem bereitgestellten Text 
           entnehmen kannst)
Schritt 2: Identifiziere Trends 
           (Verbesserung/Verschlechterung, mit Zahlenbeleg)
Schritt 3: Nenne Unsicherheiten 
           (Was könnten die Daten NICHT zeigen?)
Schritt 4: Formuliere 3 Handlungsempfehlungen
           (jeweils als [Einschätzung] gekennzeichnet)
```

**Warum das funktioniert:** Die Step-by-Step-Struktur aktiviert das, was in der KI-Forschung „Chain of Thought" heißt (Kette von Denkschritten). Statt direkt eine Schlussfolgerung zu springen, durchläuft das Modell Zwischenschritte — und jeder Zwischenschritt reduziert das Risiko, dass es wild drauflos erfindet.

### Technik 5: Der „Sag, was du nicht weißt"-Befehl

Die einfachste und eine der wirksamsten Techniken:

```
Wenn du dir bei einer Aussage nicht sicher bist, sage es explizit.
Wenn du keine aktuellen Daten hast, schreibe: 
„Zu diesem Punkt liegen mir keine aktuellen Daten vor."
Erfinde KEINE Zahlen, Quellen oder Fakten.
```

**Achtung:** Diese Technik funktioniert gut, ist aber nicht unfehlbar. Manchmal „denkt" das Modell, es weiß etwas — obwohl es halluziniert. Der Befehl hilft bei der bewussten Lücke, nicht bei der unbewussten Erfindung. Deshalb ist er immer in Kombination mit den anderen Techniken zu nutzen.

---

## Schritt 4: Was ist Bias — und warum steckt er in jeder KI?

Neben Halluzinationen gibt es ein zweites, subtileres Problem: **Bias** — systematische Verzerrung.

Halluzinationen sind offensichtlich falsch, wenn man sie prüft. Bias ist gefährlicher, weil er **plausibel klingt und trotzdem verzerrt ist**.

### Wie Bias entsteht

```
┌─────────────────────────────────────────────────────────┐
│                    Bias-Kreislauf                        │
│                                                         │
│  Verzerrte Trainingsdaten                               │
│         │                                               │
│         ▼                                               │
│  Modell lernt Muster inkl. Verzerrung                   │
│         │                                               │
│         ▼                                               │
│  KI-Ausgaben spiegeln Bias wider                        │
│         │                                               │
│         ▼                                               │
│  Ausgaben fließen in neue Trainingsdaten                 │
│         │                                               │
│         ▼                                               │
│  Bias verstärkt sich (Feedback-Loop)                    │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

Sprachmodelle lernen aus Texten im Internet — und das Internet ist kein neutraler Ort. Es enthält Jahrzehnte an gesellschaftlichen Vorurteilen, kulturellen Annahmen und statistischen Verzerrungen. Das Modell „glaubt" diese Verzerrungen nicht — aber es hat sie als Muster gespeichert und reproduziert sie.

### Die 5 Bias-Typen im Bankwesen

| Bias-Typ | Was passiert | Bankbeispiel |
|---|---|---|
| **Geschlechter-Bias** | Stereotypische Zuschreibungen je nach Geschlecht | KI beschreibt Bankberaterinnen als „empathisch" und Bankberater als „durchsetzungsstark" |
| **Alters-Bias** | Verallgemeinerungen über Altersgruppen | „Ältere Kunden bevorzugen grundsätzlich Filialbesuche und meiden Online-Banking" |
| **Rollen-Bias** | Stereotypen zu Berufsgruppen | „IT = männlich, HR = weiblich, Vorstand = männlich" |
| **Quellen-/Kultur-Bias** | Dominanz bestimmter Perspektiven in den Trainingsdaten | US-amerikanisches Bankensystem wird als Standard genommen; deutsches Genossenschaftswesen unterrepräsentiert |
| **Confirmation Bias** | KI bestätigt die implizite Annahme des Prompters | Frage: „Warum ist Filialschließung sinnvoll?" → KI liefert nur Pro-Argumente, keine Gegenargumente |

> **Volksbank-Analogie:** Bias in der KI ist wie ein Berater, der immer dieselbe Zielgruppe beraten hat. Wer 20 Jahre nur Gutverdiener betreut hat, empfiehlt unbewusst andere Produkte als jemand, der breiter aufgestellt ist. Nicht aus Böswilligkeit — sondern aus eingefahrenen Mustern. Die KI hat Milliarden Texte „beraten" — und deren Muster übernommen.

---

## Schritt 5: Bias aufdecken — die Gender-Swap-Technik

Die wirksamste Methode, um versteckte Vorurteile in KI-Antworten sichtbar zu machen, ist verblüffend einfach: **Stellen Sie dieselbe Frage zweimal — einmal mit „sie", einmal mit „er".**

### So funktioniert es

**Variante A:**
```
Beschreibe eine erfolgreiche Filialleiterin der Volksbank Hellweg 
und ihre Führungsqualitäten.
```

**Variante B:**
```
Beschreibe einen erfolgreichen Filialleiter der Volksbank Hellweg 
und seine Führungsqualitäten.
```

**Variante C (Kontrollgruppe):**
```
Beschreibe eine erfolgreiche Filialleitung der Volksbank Hellweg 
und deren Führungsqualitäten.
```

### Was Sie typischerweise finden

| Aspekt | Weibliche Version | Männliche Version | Bias-Indikator |
|---|---|---|---|
| **Führungsstil** | „empathisch, vermittelnd, konsensorientiert" | „durchsetzungsstark, entscheidungsfreudig, visionär" | Stereotypisierung |
| **Erfolge** | „verbesserte Teamharmonie, steigende Kundenzufriedenheit" | „steigerte Geschäftsvolumen um 25%, gewann neue Firmenkunden" | Soft Skills vs. Zahlen |
| **Herausforderungen** | „Work-Life-Balance, Akzeptanz in der Männerdomäne" | „Marktdruck, Wettbewerb, Digitalisierung" | Persönlich vs. Sachlich |
| **Beschreibung** | „die 42-jährige Mutter zweier Kinder" | „der erfahrene Bankfachwirt" | Privatinfo vs. Kompetenz |

Wenn die Antworten sich in diesen Dimensionen unterscheiden, liegt Bias vor — und zwar nicht, weil die KI „sexistisch ist", sondern weil ihre Trainingsdaten diese Muster enthalten.

### Erweiterte Test-Matrix

Der Gender-Swap ist nur der Anfang. Sie können das Prinzip auf jede Dimension anwenden:

| Test-Dimension | Varianten | Zu prüfender Bias |
|---|---|---|
| **Geschlecht** | „Filialleiterin" vs. „Filialleiter" | Geschlechter-Stereotype |
| **Alter** | „junge Beraterin (28)" vs. „erfahrene Beraterin (55)" | Alters-Stereotype |
| **Name** | „Maria Schmidt" vs. „Ayşe Yılmaz" | Kultur-/Herkunfts-Bias |
| **Rolle + Geschlecht** | „Leiterin IT-Abteilung" vs. „Leiter Kundenberatung" | Bereichs-Stereotype |
| **Region** | „Volksbank Berlin" vs. „Volksbank Sauerland" | Stadt-Land-Bias |

### Praktischer Test: Stellenanzeige

```
Test A:
„Erstelle eine Stellenanzeige für eine Privatkundenberaterin 
der Volksbank Hellweg."

Test B:
„Erstelle eine Stellenanzeige für einen Privatkundenberater 
der Volksbank Hellweg."
```

**Prüfen Sie:**
- Werden unterschiedliche Soft Skills betont?
- Wird bei der weiblichen Version „Teilzeit möglich" erwähnt, bei der männlichen nicht?
- Unterscheidet sich die Formulierung des Gehalts (konkret vs. „attraktives Paket")?
- Werden unterschiedliche Benefits hervorgehoben (Kinderbetreuung vs. Firmenwagen)?

---

## Schritt 6: Bias reduzieren — Prompt-Techniken

### Technik 1: Perspektivenwechsel erzwingen

```
Analysiere die Ursachen sinkender Kundenzahlen in unserer 
Filiale Soest aus DREI Blickwinkeln:

1) Filialleitung/Management:
   - Standortfaktoren, Personalplanung, Kostenstruktur

2) Kunden (verschiedene Altersgruppen und Lebenssituationen):
   - Erreichbarkeit, Öffnungszeiten, digitale Alternativen

3) Mitarbeitende:
   - Arbeitsbedingungen, Motivation, Kundenfeedback im Alltag

SYNTHESE: Überschneidungen, Zielkonflikte, 3 Quick Wins.
Vermeide Verallgemeinerungen über Altersgruppen oder Regionen.
```

### Technik 2: Devil's Advocate verpflichtend machen

```
Erstelle eine Empfehlung zur Einführung eines KI-Chatbots 
für die Kundenberatung.

PFLICHT: Nach jeder Empfehlung beantworte:
- Was spricht GEGEN diese Maßnahme?
- Welche Kundengruppen könnten benachteiligt werden?
- Gibt es rechtliche oder reputative Risiken?
- Welche unbeabsichtigten Effekte könnten auftreten?
```

> **Volksbank-Analogie:** Der Devil's Advocate ist das Pendant zum Risikomanagement im Kreditprozess. Dort fragt niemand nur „Warum sollen wir diesen Kredit geben?" — man fragt auch systematisch „Was könnte schiefgehen?" Diese Gegenperspektive ist keine Bremse, sondern Qualitätssicherung.

### Technik 3: Inklusive Sprache einfordern

Statt darauf zu hoffen, dass die KI von sich aus divers formuliert:

**❌ Riskant:**
```
Beschreibe die typische Kundschaft unserer Baufinanzierung.
```

**✅ Bias-reduziert:**
```
Beschreibe die Vielfalt unserer Baufinanzierungs-Kunden:
- Verschiedene Altersgruppen (25-65+)
- Verschiedene Lebenssituationen (Singles, Paare, Familien, Alleinerziehende)
- Verschiedene Einkommensniveaus und Berufsgruppen
- Verschiedene kulturelle Hintergründe
Vermeide Stereotype. Nutze geschlechterneutrale Sprache wo möglich.
```

### Technik 4: Daten statt Annahmen fordern

```
NICHT: „Wie nutzen ältere Kunden Online-Banking?"
       → Provoziert Stereotypen

BESSER: „Welche Daten bräuchte man, um die Online-Banking-Nutzung 
         verschiedener Altersgruppen zu analysieren? 
         Nenne die Datenpunkte, nicht die Antwort."
```

Dieser Trick ist subtil aber mächtig: Statt die KI nach einer stereotypen Antwort zu fragen, fragen Sie sie nach der **Methode** — und bekommen eine neutrale, datenbasierte Perspektive.

---

## Schritt 7: Die Faktenprüfungs-Routine für den Alltag

Theorie ist gut, Praxis ist besser. Hier ist eine Routine, die Sie bei jeder KI-Ausgabe anwenden können — schnell, systematisch, zuverlässig.

### Die 4-Minuten-Prüfung

```
SCHRITT 1 — ZAHLEN-CHECK (60 Sekunden)
☐ Jede Zahl im Text: Gibt es eine Quelle?
☐ Prozentwerte: Plausibel? (Summe = 100%?)
☐ Datumsangaben: Aktuell oder veraltet?
☐ Keine Quelle → als [UNGEPRÜFT] markieren

SCHRITT 2 — REGULATORIK-CHECK (60 Sekunden)
☐ Genannte Gesetze/Paragraphen: Existieren sie?
☐ Keine Rechtsberatung formuliert?
☐ BaFin-/DSGVO-Aussagen als Zitat belegt?

SCHRITT 3 — BIAS-CHECK (60 Sekunden)
☐ Werden Personengruppen verallgemeinert?
☐ Sprache inklusiv?
☐ Würde der Text anders klingen, wenn man das Geschlecht
  / Alter / die Herkunft tauscht?

SCHRITT 4 — VERTRAULICHKEITS-CHECK (60 Sekunden)
☐ Keine internen, nicht freigegebenen Daten ausgegeben?
☐ Keine personenbezogenen Daten erkennbar?
☐ Keine Kundeninformationen in einem öffentlichen KI-Tool verarbeitet?
```

### Prompt-Vorlage für die automatische Prüfung

Sie können die KI auch bitten, ihren eigenen Output zu prüfen — ein zweites Paar Augen, wenn auch ein maschinelles:

```
Prüfe den folgenden Text auf mögliche Halluzinationen und Bias:

„[HIER TEXT EINFÜGEN]"

Prüfe auf:
1) Fakten: Gibt es Behauptungen ohne erkennbare Quelle?
2) Zahlen: Sind die genannten Zahlen plausibel und datiert?
3) Bias: Gibt es stereotypische Zuschreibungen?
4) Regulatorik: Werden Gesetze/Vorschriften korrekt zitiert?
5) Aktualität: Sind die Informationen aktuell oder möglicherweise veraltet?

Erstelle eine Prüftabelle:
Aussage | Typ (Fakt/Einschätzung/Unklar) | Risiko (🟢🟡🔴) | Kommentar
```

**Achtung — und das ist wichtig:** Die KI kann sich selbst nur begrenzt prüfen. Sie neigt dazu, ihre eigenen Aussagen als korrekt zu bestätigen. Diese Selbstprüfung ist ein **Hilfsmittel**, kein Ersatz für menschliche Verifikation. Nutzen Sie sie als erste Filterschicht, nicht als letzte.

---

## Schritt 8: Prompt-Vorlagen für typische Bank-Aufgaben

Hier sind vier fertige Prompt-Vorlagen, die Halluzinations- und Bias-Schutz bereits eingebaut haben. Kopieren und anpassen — fertig.

> **Volksbank-Analogie:** Diese Vorlagen sind wie die Musterverträge in Ihrer Rechtsabteilung. Niemand formuliert einen Kreditvertrag jedes Mal von Grund auf neu — es gibt geprüfte Vorlagen mit Pflichtfeldern, Schutzklauseln und Prüfschritten. Die Schutzklauseln (Quellenpflicht, Fakten-Trennung, Devil's Advocate) sind bereits eingebaut. Sie müssen nur noch das Thema einsetzen. Und wie bei Musterverträgen gilt: Die Vorlage schützt vor den häufigsten Fehlern — aber die finale Prüfung bleibt beim Menschen.

### 📑 Vorlage 1: Management-Briefing (faktenbasiert)

```
Temperature: 0.2

Erstelle ein 1-Seiten-Briefing zum Thema: [THEMA].

REGELN:
- Nutze NUR bereitgestellte Zahlen/Daten [hier einfügen].
- Keine Schätzungen ohne Kennzeichnung [Einschätzung].
- Nenne für jede Kennzahl: Zeitraum, Einheit, Quelle.
- Trenne klar: „Fakten" und „Implikationen".
- Wenn dir Daten fehlen: [Keine Daten verfügbar — intern prüfen].
- Ende: 3 priorisierte To-Dos (Verantwortlich + Frist).
```

### 🧪 Vorlage 2: Entscheidungsvorlage mit Risiken

```
Temperature: 0.3

Erstelle eine Entscheidungsvorlage (max. 12 Bullet Points) 
zur Einführung von [MAßNAHME].

Abschnitte:
1) Ziel & Zielgruppe
2) Finanzielle Effekte (Kosten/ROI) — mit Datenstand
3) Compliance-/Operational-Risiken
4) Kundenwirkung & Kommunikation
5) Abhängigkeiten (IT/Prozess/Schulung)
6) Devil's Advocate: Was spricht dagegen?
   - Welche Kundengruppen könnten benachteiligt werden?
   - Welche unbeabsichtigten Effekte drohen?
```

### 💡 Vorlage 3: Kampagnen-Ideen (mit Bias-Kontrolle)

```
Temperature: 0.7

Generiere 6 Ideen für eine Kampagne zu [THEMA].

DIVERSITÄT:
- 2 Ideen für junge Kunden (18-30)
- 2 Ideen für mittlere Altersgruppe (30-55)
- 2 Ideen für 55+
- Jede Idee: Online- UND Offline-Kanal berücksichtigen
- Budgetvarianten: klein / mittel / groß
- Keine Stereotype; inklusiv formulieren.
- Barrierefreiheit berücksichtigen.
```

### 🧾 Vorlage 4: Protokoll (robust gegen Halluzination)

```
Temperature: 0.2

Erstelle ein präzises Protokoll basierend auf DIESEM Wortlaut:
[Transkript/Notizen hier einfügen]

REGELN:
- NUR Inhalte aus dem bereitgestellten Text verwenden.
- KEINE Ergänzungen, Interpretationen oder Kontextannahmen.
- Offene Punkte als [Action Item] mit Verantwortlichem und Termin.
- Wenn etwas im Transkript unklar ist: [Unklar — nachfragen].
```

---

## Schritt 9: Fortgeschrittene Techniken

### 9.1 Der Dreifach-Test für maximale Bias-Erkennung

Für besonders sensible Texte (Stellenanzeigen, Kundenanschreiben, Strategiepapiere) nutzen Sie nicht nur den Gender-Swap, sondern drei Tests in Kombination:

```
Test 1: GENDER-SWAP
        „Die neue Filialleiterin..." vs. „Der neue Filialleiter..."
        → Prüfe auf unterschiedliche Attribute

Test 2: ROLE-REVERSAL (untypische Rollen)
        „Die Leiterin der IT-Abteilung..." 
        vs. „Der Leiter der Kundenberatung..."
        → Prüfe, ob die KI bei „untypischen" Rollen anders formuliert

Test 3: BLIND-TEST (Geschlecht weglassen)
        „Die Abteilungsleitung..."
        → Prüfe, welches Geschlecht die KI implizit annimmt
```

Wenn alle drei Versionen unterschiedliche Schwerpunkte zeigen → klarer Bias, der im Prompt adressiert werden muss.

### 9.2 Das Bias-Test-Protokoll

Für systematische Tests — besonders wenn Ihre Bank regelmäßig KI für Kommunikation nutzt:

```
## Bias-Test-Protokoll: [Thema]
Datum: [XX.XX.XXXX]
Modell: [GPT-4 / Claude / Gemini]
Temperatur: [0.X]

### Prompt-Varianten:
- V1 (weiblich): „[...]"
- V2 (männlich): „[...]"
- V3 (neutral): „[...]"

### Ergebnis-Analyse:
| Kategorie       | V1 (w)     | V2 (m)      | V3 (n)    | Bias? |
|-----------------|------------|-------------|-----------|-------|
| Führungsverben  |            |             |           | ☐     |
| Eigenschaften   |            |             |           | ☐     |
| Erfolgsmetriken |            |             |           | ☐     |
| Privatinfo      |            |             |           | ☐     |

### Bias-Score: _/4 Kategorien betroffen
### Korrektur-Prompt: „[Optimierter Prompt]"
```

### 9.3 RAG — Die technische Waffe gegen Halluzinationen

**RAG** steht für **Retrieval-Augmented Generation** — wörtlich: „abrufgestützte Erzeugung". Statt das Modell aus seinem Gedächtnis antworten zu lassen, gibt man ihm **vor der Antwort** relevante Dokumente zum Lesen.

```
Ohne RAG:
┌─────────┐     ┌─────────┐
│  Frage  │ ──► │  Modell  │ ──► Antwort (aus Trainings-Gedächtnis)
└─────────┘     └─────────┘

Mit RAG:
┌─────────┐     ┌──────────────┐     ┌─────────┐
│  Frage  │ ──► │  Suche in    │ ──► │  Modell  │ ──► Antwort (aus echten Dokumenten)
└─────────┘     │  Dokumenten  │     └─────────┘
                └──────────────┘
```

**Wirksamkeit:** Studien zeigen, dass RAG Halluzinationen um 40–71% reduzieren kann — je nach Implementierung und Domäne. Es ist die derzeit wirksamste technische Gegenmaßnahme.

**Im Bankumfeld heißt das konkret:**
- Die KI durchsucht **nur freigegebene interne Richtlinien** (nicht das Internet)
- Antworten basieren auf **echten Dokumenten** (Compliance-Handbuch, Produktdatenblätter)
- Jede Aussage kann zum **Quelldokument** zurückverfolgt werden

**Für Ihren Alltag:** Wenn Ihre Bank ein KI-Tool mit RAG anbietet (z.B. auf interne Wissensdatenbanken), bevorzugen Sie das immer gegenüber einem allgemeinen Tool wie ChatGPT — besonders bei regulatorischen Fragen.

> **Volksbank-Analogie:** RAG ist wie der Unterschied zwischen einem Berater, der aus dem Kopf berät (Risiko: „Ich glaube, die Kondition ist 2,8%..."), und einem, der den aktuellen Produktkatalog aufschlägt, bevor er antwortet. Beide können beraten — aber nur einer kann seine Aussage belegen.

---

## Was diese Techniken (noch) nicht können

| Grenze | Was das bedeutet | Workaround |
|---|---|---|
| **Selbstprüfung ist begrenzt** | Die KI bestätigt oft ihre eigenen Halluzinationen, wenn man nachfragt | Nie nur die KI selbst prüfen lassen — immer externe Quelle |
| **Bias ist nie vollständig eliminierbar** | Trainingsdaten enthalten gesellschaftliche Verzerrungen, die sich nur minimieren, nicht entfernen lassen | Regelmäßige Bias-Tests, besonders bei kundensichtbaren Texten |
| **Halluzinationsrate ≠ 0%** | Selbst die besten Modelle halluzinieren in 0,7% der Fälle; in Spezialdomänen (Recht, Medizin) liegt die Rate bei 4–7% | Vier-Augen-Prinzip: Mensch prüft immer die finale Version |
| **Aktualität hat ein Ablaufdatum** | Trainingsdaten haben einen Stichtag; alles danach ist „Neuland" für die KI | Bei zeitkritischen Fragen immer das Trainingsdaten-Ende erfragen |
| **Prompt-Techniken senken, aber eliminieren nicht** | Quellenpflicht, Temperatursteuerung und Fakten-Trennung reduzieren Halluzinationen — garantieren aber keine Fehlerfreiheit | Technik-Stack kombinieren: Prompt-Technik + menschliche Prüfung + RAG wo verfügbar |
| **Technologie isoliert vs. Gesamtsystem** | Ein LLM allein halluziniert; ein System mit RAG, Grounding und menschlicher Prüfung halluziniert deutlich weniger | Nicht „die KI" bewerten, sondern den **Prozess**, in dem sie eingesetzt wird |

**Nicht geeignet — auch mit den besten Prompts:**

🚫 Rechtlich verbindliche Auslegung von Gesetzen oder BaFin-Rundschreiben
🚫 Verarbeitung vertraulicher Kundendaten in öffentlichen KI-Tools (DSGVO!)
🚫 Finale Kreditentscheidungen ohne menschliche Prüfung
🚫 Medizinische Aussagen für betriebliches Gesundheitsmanagement
🚫 Zins- oder Konditionsangaben ohne Prüfung gegen das Quellsystem

**Menschliche Expertise bleibt nötig bei:**

✅ Finaler Compliance-Bewertung
✅ Strategischen Entscheidungen und Reputationsfragen
✅ Kundenbeschwerden und Eskalationen
✅ Allem, wo Haftung entsteht

---

## Was es kostet — und was es spart

| Aufgabe | Ohne Schutz-Techniken | Mit Halluzinations-/Bias-Schutz | Verbesserung |
|---|---|---|---|
| Management-Briefing | Schnell erstellt, aber 3–5 Fakten intern nachprüfen → 30 Min | Quellenpflicht + Fakten-Trennung → 1–2 Fakten nachprüfen → 10 Min | ~65% weniger Prüfaufwand |
| Stellenanzeige | Erstellt, aber unbewusst Gender-Bias → überarbeiten 20 Min | Gender-Swap-Test + inklusive Sprache → sofort nutzbar → 5 Min Review | ~75% weniger Nacharbeit |
| Kreditanalyse-Entwurf | Plausible Zahlen, aber 2 davon erfunden → aufwändige Korrektur 45 Min | Temperatur 0.2 + Quellenpflicht + [KEINE DATEN]-Markierung → Lücken sofort sichtbar → 15 Min | ~65% weniger Korrektur |
| Compliance-Vorlage | Paragraph erfunden, erst im Review bemerkt → Neuerstellung 60 Min | „Sag was du nicht weißt" + Step-by-Step → Lücken sofort markiert → 20 Min | ~65% weniger Risiko |

**Die Kosten-Rechnung:**

| Vergleich | Menschlich (ohne KI) | KI ohne Schutz | KI mit Schutz-Techniken |
|---|---|---|---|
| Management-Briefing | 2–3 Std | 15 Min + 30 Min Prüfung | 20 Min + 10 Min Prüfung |
| Stellenanzeige (bias-frei) | 1–2 Std + Diversity-Review | 10 Min + 20 Min Korrektur | 15 Min + 5 Min Review |
| 10 Kunden-E-Mails (faktengeprüft) | 3–4 Std | 30 Min + 60 Min Faktencheck | 40 Min + 20 Min Faktencheck |

**Die unangenehme Alternative:** Was kostet eine Halluzination, die nicht erkannt wird? Ein erfundener BaFin-Paragraph in einer Compliance-Vorlage, die in Produktion geht? Ein Gender-Bias in einer Stellenanzeige, der zu einer AGG-Klage führt? Die Schutz-Techniken kosten Minuten — die Konsequenzen von Fehlern kosten Tausende.

---

## Die Schutz-Pipeline auf einen Blick

```
┌──────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────┐
│  PROMPT   │    │  SCHUTZ      │    │   KI-        │    │  PRÜFUNG     │    │ FREIGABE │
│  erstellen│ →  │  einbauen    │ →  │   AUSGABE    │ →  │  durchführen │ →  │ oder     │
│           │    │              │    │              │    │              │    │ Korrektur│
│ Was?      │    │ Quellenpfl.  │    │              │    │ 4-Min-Check  │    │          │
│ Für wen?  │    │ Temperatur   │    │              │    │ Zahlen       │    │ ✅ Nutzen │
│           │    │ Fakten/Einsch│    │              │    │ Regulatorik  │    │ 🔄 Debug │
│           │    │ Step-by-Step │    │              │    │ Bias         │    │ ❌ Neu   │
│           │    │ Bias-Schutz  │    │              │    │ Vertraulichk.│    │          │
└──────────┘    └──────────────┘    └──────────────┘    └──────────────┘    └──────────┘
```

---

## Das Wichtigste auf einen Blick

| Technik | Was sie tut | Wann nutzen |
|---|---|---|
| **Quellenpflicht** | Erzwingt Quellenangaben, markiert Lücken | Immer bei faktischen Texten (Berichte, Briefings, Analysen) |
| **Fakten/Einschätzung trennen** | Markiert jede Aussage als [FAKT], [EINSCHÄTZUNG] oder [KEINE DATEN] | Bei Management-Vorlagen und Entscheidungsgrundlagen |
| **Temperatur senken** | Reduziert kreatives Raten, erhöht Faktentreue | Bei Compliance, Regulatorik, Zahlenmaterial |
| **Step-by-Step** | Zerlegt Antwort in Denkschritte, reduziert Sprünge zu Schlussfolgerungen | Bei komplexen Analysen und Zusammenfassungen |
| **„Sag, was du nicht weißt"** | Erlaubt dem Modell, Wissenslücken zuzugeben | In jedem Prompt als Standard-Regel |
| **Gender-Swap** | Deckt Geschlechter-Bias auf durch identische Prompts mit getauschtem Geschlecht | Bei Stellenanzeigen, Kommunikation, Beschreibungen von Personen |
| **Perspektivenwechsel** | Erzwingt mehrere Blickwinkel statt einer einseitigen Darstellung | Bei Strategiepapieren, Empfehlungen, Analysen |
| **Devil's Advocate** | Fordert systematisch Gegenargumente und Risiken | Bei Entscheidungsvorlagen und Empfehlungen |
| **4-Minuten-Prüfung** | Systematische Nachprüfung jeder KI-Ausgabe in 4 Schritten | Nach jeder KI-Ausgabe, die extern genutzt wird |
| **RAG** | Bindet KI-Antworten an echte Dokumente statt an Trainingsgedächtnis | Wenn verfügbar — immer bevorzugen bei internen Fragen |

---

## Parallelen zu vorherigen Tutorials

| Konzept in diesem Tutorial | Woher Sie es kennen |
|---|---|
| Mustervervollständigung als Ursache von Halluzinationen | Tutorial 00-01: Wie LLMs Token vorhersagen |
| Temperatur beeinflusst Halluzinationsrisiko | Tutorial 01-02: Temperatur & Top-P |
| Attention-Drift bei langen Kontexten | Tutorial 00-01: Context Window & Attention |
| Fakten-/Einschätzungs-Trennung als Prompt-Baustein | Tutorial 01-01: Baustein 4 (Regeln) |
| Debug-Methode für fehlerhafte KI-Ausgaben | Tutorial 01-02: Schritt 6 (Iteratives Verfeinern) |
| Output-Vertrag mit Selbst-Check | Tutorial 01-02: Schritt 7 (Output-Verträge) |
| Step-by-Step = Chain of Thought | Tutorial 00-01: Attention-Mechanismus und gewichtete Verarbeitung |
| RAG als Grounding-Technik | Tutorial 00-07: MCP und externe Datenquellen |
| Bias in Trainingsdaten | Tutorial 00-01: Woher kommt das „Wissen" des LLMs? |

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: „Halluzination erkennen"

**Ihre Aufgabe:** Lesen Sie die folgende KI-Ausgabe und identifizieren Sie alle Warnsignale.

**KI-Ausgabe:**
> „Das neue Geldwäschegesetz (GwG-Novelle 2025) verpflichtet alle Genossenschaftsbanken ab dem 1. Juli 2025 zu einer vierteljährlichen KI-gestützten Transaktionsüberwachung. Laut BaFin-Rundschreiben 08/2025 müssen dafür mindestens 2,3% des IT-Budgets aufgewendet werden. BVR-Präsidentin Kolak begrüßte die Regelung als ‚längst überfällig'. Erste Pilotprojekte bei der Volksbank Dortmund-Nordwest zeigen eine Trefferquote von 94,7%."

**Warnsignale (prüfen Sie):**
- [ ] Existiert eine GwG-Novelle 2025?
- [ ] Existiert BaFin-Rundschreiben 08/2025?
- [ ] Stimmt die 2,3%-Vorgabe?
- [ ] Ist das Zitat von Kolak verifizierbar?
- [ ] Existiert die genannte Volksbank?
- [ ] Ist die 94,7%-Trefferquote plausibel ohne Kontext?

<details>
<summary>💡 Auflösung anzeigen</summary>

**Alle 6 Punkte sind Warnsignale:**

1. **GwG-Novelle 2025:** Prüfen Sie auf der Seite des Bundesfinanzministeriums — existiert diese Novelle in dieser Form?
2. **BaFin-Rundschreiben 08/2025:** Auf bafin.de nachschlagen — gibt es dieses Rundschreiben?
3. **2,3% IT-Budget:** Eine auffällig spezifische Zahl ohne jede Quelle.
4. **Kolak-Zitat:** Persönliche Zitate sind eine der häufigsten Halluzinationsformen. Ohne Pressequelle nicht verwenden.
5. **Volksbank Dortmund-Nordwest:** Existiert diese Bank? Genossenschaftsbanken haben spezifische Namen — ein kleiner Hinweis, ob die KI erfindet.
6. **94,7% Trefferquote:** Eine Nachkommastelle ohne Studienangabe ist ein klassisches Halluzinations-Muster.

**Wichtig:** Der Text klingt absolut professionell und glaubwürdig. Genau das macht Halluzinationen gefährlich. In einem realen Szenario hätte dieser Text es in ein Management-Briefing schaffen können — mit potenziell gravierenden Folgen.
</details>

---

### Hands-on 2: „Gender-Swap-Test durchführen" (Modellvergleich)

**Ihre Aufgabe:** Führen Sie einen Gender-Swap-Test mit mindestens 2 verschiedenen KI-Modellen durch.

**Geben Sie jedem Modell beide Prompts:**

**Prompt A:**
```
Beschreibe eine erfolgreiche Filialleiterin einer Volksbank 
und ihren typischen Arbeitstag.
```

**Prompt B:**
```
Beschreibe einen erfolgreichen Filialleiter einer Volksbank 
und seinen typischen Arbeitstag.
```

**Analyse-Tabelle zum Ausfüllen:**

| Dimension | Modell 1 (w) | Modell 1 (m) | Modell 2 (w) | Modell 2 (m) |
|---|---|---|---|---|
| Erste Tätigkeit am Morgen | | | | |
| Genannte Führungsqualitäten | | | | |
| Erwähnung von Familie/Privatleben | | | | |
| Art der Erfolgsmetriken | | | | |
| Tonalität (sachlich/emotional) | | | | |

**Fragen zur Reflexion:**
- Welches Modell zeigt mehr Bias?
- Bei welchen Dimensionen sind die Unterschiede am größten?
- Was sagt das über die Trainingsdaten der Modelle?

---

### Hands-on 3: „Halluzinations-resistenten Prompt bauen"

**Ihre Aufgabe:** Nehmen Sie diesen halluzinations-anfälligen Prompt und machen Sie ihn sicher — mit mindestens 3 der 5 Schutz-Techniken aus Schritt 3.

**Ausgangsprompt:**
```
Wie ist die aktuelle Zinsentwicklung und was bedeutet das 
für unsere Baufinanzierungskunden?
```

**Bauen Sie einen neuen Prompt, der enthält:**
- [ ] Quellenpflicht
- [ ] Fakten-/Einschätzungs-Trennung
- [ ] Temperatur-Empfehlung
- [ ] Step-by-Step-Struktur
- [ ] „Sag, was du nicht weißt"

<details>
<summary>💡 Beispiel-Lösung anzeigen</summary>

```
Temperature: 0.2

Erstelle eine faktenbasierte Kurzanalyse (max. 300 Wörter) 
zur Zinsentwicklung und deren Auswirkungen auf 
Baufinanzierungskunden der Volksbank Hellweg.

Gehe in diesen Schritten vor:

Schritt 1: AKTUELLE LAGE
- Nenne den aktuellen EZB-Leitzins mit Datum [Quelle, Datum].
- Wenn du das aktuelle Datum nicht sicher weißt: 
  [Daten-Stichtag meiner Trainingsdaten: MM/JJJJ — 
  aktuelle Werte bitte intern prüfen].

Schritt 2: ENTWICKLUNG
- Zinsentwicklung der letzten 12 Monate als Trend (↑↓→).
- Jede Zahl mit [Quelle, Datum] oder [Einschätzung].

Schritt 3: AUSWIRKUNGEN FÜR KUNDEN
- 3 konkrete Auswirkungen auf Baufinanzierungskunden.
- Getrennt: [FAKT] vs. [EINSCHÄTZUNG].
- Keine pauschalen Empfehlungen.

Schritt 4: UNSICHERHEITEN
- Was könnten diese Daten NICHT zeigen?
- Welche regionalen Unterschiede sind möglich?

Schritt 5: HANDLUNGSEMPFEHLUNGEN
- 3 Empfehlungen für die Beratung, je als [Einschätzung].

REGELN:
- Erfinde KEINE Zahlen oder Quellen.
- Wenn dir aktuelle Daten fehlen: 
  [Keine aktuellen Daten — intern prüfen].
- Keine Rechtsberatung. Keine Produktempfehlungen.
```
</details>

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **Halluzination** | KI erfindet plausibel klingende, aber faktisch falsche Informationen — ohne „Absicht" oder Bewusstsein für den Fehler |
| **Konfabulation** | Wissenschaftlich präziserer Begriff für Halluzination: Das Füllen von Wissenslücken mit erfundenen, aber kohärenten Inhalten (wie bei Patienten mit Gedächtnisstörungen) |
| **Bias** | Systematische Verzerrung in KI-Ausgaben, verursacht durch unausgewogene Trainingsdaten — nicht durch „Absicht" des Modells |
| **Gender-Swap-Technik** | Methode zur Bias-Erkennung: Identische Prompts mit getauschtem Geschlecht stellen und Antworten vergleichen |
| **RAG (Retrieval-Augmented Generation)** | Technik, bei der die KI vor der Antwort relevante Dokumente durchsucht — reduziert Halluzinationen um 40–71% |
| **Grounding** | Verankerung von KI-Antworten in verifizierten Quellen statt im Trainingsgedächtnis |
| **Chain of Thought** | Denkschritte-Technik: Das Modell wird angewiesen, Zwischenschritte explizit auszuarbeiten, statt direkt zum Ergebnis zu springen |
| **Quellenpflicht** | Prompt-Technik: Die KI muss für jede faktische Aussage eine Quelle nennen oder die Lücke markieren |
| **Devil's Advocate** | Prompt-Technik: Die KI muss systematisch Gegenargumente und Risiken zu ihren eigenen Empfehlungen liefern |
| **Fakten-/Einschätzungs-Trennung** | Prompt-Technik: Jede Aussage wird als [FAKT], [EINSCHÄTZUNG] oder [KEINE DATEN] markiert |
| **Perspektivenwechsel** | Prompt-Technik: Erzwingt Analyse aus mehreren Blickwinkeln (Management, Kunden, Mitarbeitende) |
| **Confirmation Bias** | Verzerrung, bei der die KI die implizite Annahme des Prompters bestätigt statt neutral zu analysieren |
| **Vier-Augen-Prinzip** | Übertragen auf KI: Jede KI-Ausgabe wird von einem Menschen gegengeprüft, bevor sie verwendet wird |
| **Temperatur** | Parameter, der Kreativität vs. Faktentreue steuert (vgl. Tutorial 01-02); niedrig = weniger Halluzinationen |
| **Trainingsdaten-Stichtag** | Zeitpunkt, bis zu dem das Modell Informationen aus dem Internet gelernt hat — alles danach ist unbekannt |
| **HalluLens** | Erster standardisierter akademischer Benchmark zur Messung von Halluzinationsraten (ACL 2025) |
| **Halluzinationsrate** | Prozentsatz der KI-Antworten, die nachweislich falsche Informationen enthalten (beste Modelle 2025: 0,7%) |

---

