# XML-Schemas für Prompts

**Warum Struktur wichtiger ist als schöne Formulierungen — und wie XML-Tags Ihre Prompts auf Profi-Niveau heben**

---

## Warum dieses Tutorial?

In Kapitel 01 haben Sie das Handwerk des Prompt Engineering gelernt: klare Rollen vergeben, Kontext liefern, Aufgaben definieren, Ergebnisse steuern. In Tutorial 01-04 haben Sie Delimiter kennengelernt — Trennzeichen, die verschiedene Teile eines Prompts voneinander abgrenzen. Darunter auch XML-Tags.

Jetzt gehen wir einen entscheidenden Schritt weiter: Von einzelnen Trennzeichen zu **kompletten Strukturen**. Von „ein bisschen Ordnung" zu „Architektur".

Warum? Weil sich Ihre Prompts seit Kapitel 01 verändert haben. Schauen Sie auf die Vorlagen aus Tutorial 01-05, 01-06 und 01-07 zurück: Die sind lang. Komplex. Mehrstufig. Sie enthalten Rollen, Kontexte, Regeln, Beispiele, Formatvorgaben und Datenschutz-Hinweise — alles in einem Textblock. Das funktioniert. Aber es funktioniert so, wie eine 40-seitige Word-Datei ohne Inhaltsverzeichnis funktioniert: Man kommt ans Ziel, aber es ist mühsam, Fehler zu finden und Änderungen vorzunehmen.

XML-Schemas lösen dieses Problem. Sie verwandeln Ihren Prompt von einem Aufsatz in ein **Formular** — mit benannten Feldern, klaren Abschnitten und einer Struktur, die sowohl Sie als auch die KI sofort verstehen.

> **Volksbank-Analogie:** Denken Sie an den Unterschied zwischen einer formlosen E-Mail „Können Sie mal die Konditionen für Herrn Müller prüfen, 350.000 Baufi, 20 Jahre, 2% Tilgung, er hat 60.000 Eigenkapital und ein Netto von 4.200" und einem standardisierten **Kreditantrag** mit definierten Feldern. Beides enthält dieselben Informationen — aber der Kreditantrag ist prüfbar, vergleichbar und fehlerfrei bearbeitbar. XML-Tags machen aus Ihrem Prompt einen Kreditantrag.

**Was Sie nach diesem Tutorial können:**

- Verstehen, warum strukturierte Prompts bessere Ergebnisse liefern als Fließtext
- XML-Tags als Strukturierungswerkzeug einsetzen — ohne Programmierkenntnisse
- Kundendaten, Dokumente und Kontexte sauber getrennt an die KI übergeben
- System-Prompts mit XML-Abschnitten professionell aufbauen
- Bestehende Prompts aus Kapitel 01 in XML-Struktur überführen
- Die Unterschiede zwischen den Modellen kennen (Claude, ChatGPT, Gemini)

---

## Schritt 1: Warum Struktur besser ist als Prosa

### Das Problem mit langen Fließtext-Prompts

Je komplexer Ihre Aufgabe, desto länger wird Ihr Prompt. Und je länger ein Fließtext-Prompt wird, desto häufiger passieren zwei Dinge:

1. **Die KI übersieht Anweisungen.** Bei einem 500-Wörter-Prompt „vergisst" die KI gelegentlich Regeln, die im Mittelteil stehen. Nicht weil sie dumm ist, sondern weil im Fließtext alles gleich aussieht — es gibt keine visuelle Hierarchie.

2. **Sie selbst verlieren den Überblick.** Wenn Sie Ihren Prompt nach 2 Wochen wieder öffnen, müssen Sie alles nochmal lesen, um zu verstehen, was wo steht und was Sie ändern müssten.

```
┌─────────────────────────────────────────────────────────────────┐
│        📝 Fließtext vs. 📋 Struktur                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ❌ FLIESSTEXT-PROMPT:                                          │
│  „Du bist ein Kundenberater der Volksbank. Analysiere das      │
│  folgende Kundenprofil. Der Kunde heißt [Name], ist [Alter]    │
│  Jahre alt, verdient [Betrag] netto. Er möchte eine Bau-      │
│  finanzierung über [Summe]. Erstelle eine Empfehlung. Achte   │
│  auf Datenschutz. Nenne keine echten Namen. Formatiere als    │
│  Tabelle. Berücksichtige die aktuelle Zinslage..."             │
│  → Alles durcheinander: Rolle, Daten, Aufgabe, Regeln, Format │
│                                                                 │
│  ✅ XML-STRUKTUR:                                               │
│  <rolle>Kundenberater der Volksbank</rolle>                    │
│  <kundendaten>                                                 │
│    Name: [anonymisiert], Alter: [X], Netto: [Y]               │
│  </kundendaten>                                                │
│  <aufgabe>Erstelle Finanzierungsempfehlung</aufgabe>           │
│  <regeln>Datenschutz beachten, keine echten Namen</regeln>     │
│  <format>Tabelle mit Szenarien</format>                        │
│  → Jeder Abschnitt hat seinen Platz                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Was die Forschung sagt

Anthropic (die Firma hinter Claude) empfiehlt seit 2024 offiziell XML-Tags als bevorzugte Strukturierungsmethode. In ihren eigenen Tests zeigte sich: **Strukturierte Prompts mit XML-Tags liefern konsistentere Ergebnisse** als Fließtext-Prompts — besonders bei komplexen Aufgaben mit mehreren Arbeitsschritten.

Der Grund ist intuitiv: XML-Tags erzeugen eine klare Hierarchie im Token-Strom. Das Modell „weiß", dass alles zwischen `<regeln>` und `</regeln>` zusammengehört — und behandelt es als zusammenhängende Einheit, statt die Information über den gesamten Prompt verstreut zu verarbeiten.

> **Volksbank-Analogie:** Wenn Sie einem neuen Mitarbeiter eine Aufgabe erklären, machen Sie das auch nicht in einem einzigen Endlos-Satz. Sie sagen: „Erstens: Deine Rolle. Zweitens: Die Kundendaten. Drittens: Was du tun sollst. Viertens: Worauf du achten musst." XML-Tags sind genau diese „Erstens, Zweitens, Drittens" — nur für die KI.

---

## Schritt 2: XML-Grundlagen — In 5 Minuten verstanden

### Was ist XML?

XML steht für **Extensible Markup Language**. Klingt technisch, ist aber einfach: Es sind **benannte Klammern** um Textabschnitte.

```
<tagname>Ihr Inhalt hier</tagname>
```

Das war's. Drei Regeln:

| Regel | Beispiel | Erklärung |
|---|---|---|
| Jedes Tag wird geöffnet und geschlossen | `<rolle>...</rolle>` | Öffnend: `<rolle>` — Schließend: `</rolle>` (mit Schrägstrich) |
| Tags können verschachtelt werden | `<kunde><name>Müller</name><alter>42</alter></kunde>` | Wie Ordner in Ordnern |
| Tag-Namen wählen Sie selbst | `<kontext>`, `<aufgabe>`, `<banane>` | Die KI versteht den Namen als Hinweis, was drin steht |

### Das ist KEIN Programmieren!

Ein häufiges Missverständnis: XML-Tags in Prompts sind **kein Code**. Sie tippen sie genauso ins Chat-Fenster wie jeden anderen Text. Keine spezielle Software, kein Compiler, kein Terminal. Es sind einfach Textmarkierungen — wie farbige Post-its auf verschiedenen Abschnitten eines Dokuments.

```
┌─────────────────────────────────────────────────────────────────┐
│        🏷️ XML-Tags = Post-its für die KI                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  📝 Normaler Text:                                              │
│  „Der Kunde ist 42 Jahre alt und verdient 4.200€ netto"        │
│                                                                 │
│  🏷️ Mit XML-Tags:                                               │
│  <kundendaten>                                                 │
│    Der Kunde ist 42 Jahre alt und verdient 4.200€ netto        │
│  </kundendaten>                                                │
│                                                                 │
│  → Gleicher Text! Nur mit einem Post-it dran, das sagt:        │
│    „Achtung KI, das hier sind die Kundendaten."                │
│                                                                 │
│  Die KI versteht: Was in <kundendaten> steht, sind Fakten      │
│  über den Kunden. Was in <aufgabe> steht, soll sie tun.       │
│  Was in <regeln> steht, muss sie einhalten.                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Die 8 nützlichsten XML-Tags für Bank-Prompts

Sie müssen keine langen Tag-Namen erfinden. Hier sind die Tags, die Sie in 90% aller Fälle brauchen:

| Tag | Zweck | Beispiel |
|---|---|---|
| `<rolle>` | Wer soll die KI sein? | `<rolle>Erfahrener Baufinanzierungsberater</rolle>` |
| `<kontext>` | Hintergrundinformationen | `<kontext>Volksbank Hellweg, 120 Berater, ländliche Region</kontext>` |
| `<aufgabe>` | Was soll die KI tun? | `<aufgabe>Erstelle 3 Finanzierungsszenarien</aufgabe>` |
| `<daten>` | Eingabedaten (Kundenprofil, Dokument, Zahlen) | `<daten>Netto: 4.200€, Eigenkapital: 60.000€</daten>` |
| `<regeln>` | Einschränkungen und Pflichten | `<regeln>Keine Kundennamen, max. 500 Wörter</regeln>` |
| `<format>` | Wie soll die Ausgabe aussehen? | `<format>Tabelle mit Spalten: Szenario, Rate, Laufzeit, Kosten</format>` |
| `<beispiel>` | Musterantwort zeigen (Few-Shot) | `<beispiel>Szenario A: 3,5% Zins, 2% Tilgung → Rate: 1.604€</beispiel>` |
| `<dokument>` | Ein zu analysierendes Dokument | `<dokument>BVR-Rundschreiben Nr. 12/2026...</dokument>` |

> **Praxis-Tipp:** Die Tag-Namen sind frei wählbar. `<rolle>` und `<role>` funktionieren beide. `<kundendaten>` und `<customer_data>` auch. Wählen Sie, was für Sie am verständlichsten ist. Deutsch funktioniert genauso gut wie Englisch.

---

## Schritt 3: Praxisbeispiel 1 — Kundenprofil strukturiert übergeben

Das häufigste Szenario: Sie haben Informationen über einen Kunden und wollen, dass die KI damit arbeitet. Ohne XML-Tags mischen sich Kundendaten, Aufgabe und Regeln — die KI muss selbst herausfinden, was was ist.

### Vorher: Fließtext-Prompt

```
Du bist ein erfahrener Finanzberater bei einer 
Genossenschaftsbank. Ein Kunde möchte eine 
Baufinanzierung. Er ist 38 Jahre alt, verheiratet, 
zwei Kinder (4 und 7), Nettoeinkommen 4.800€, 
seine Frau verdient 2.100€ netto dazu, sie haben 
75.000€ Eigenkapital angespart, wollen ein Haus 
für 420.000€ kaufen, Nebenkosten geschätzt 50.000€, 
also Gesamtbedarf 470.000€ minus 75.000€ sind 
395.000€ Kreditbedarf. Erstelle bitte drei 
Finanzierungsszenarien mit unterschiedlichen 
Laufzeiten und Tilgungssätzen. Achte auf die aktuelle 
Zinslage. Beachte den Datenschutz — verwende keine 
echten Namen. Formatiere als Tabelle. Maximal eine 
Seite.
```

### Nachher: XML-Struktur

```
<rolle>
Erfahrener Baufinanzierungsberater einer 
Genossenschaftsbank. Konservative, sicherheitsorientierte 
Beratung. Immer im Sinne des Kunden.
</rolle>

<kundenprofil>
  <person>
    Alter: 38, verheiratet, 2 Kinder (4 und 7 Jahre)
  </person>
  <einkommen>
    Netto Kunde: 4.800 €/Monat
    Netto Partnerin: 2.100 €/Monat
    Haushaltsnetto: 6.900 €/Monat
  </einkommen>
  <vorhaben>
    Objekttyp: Einfamilienhaus
    Kaufpreis: 420.000 €
    Nebenkosten (geschätzt): 50.000 €
    Gesamtbedarf: 470.000 €
    Eigenkapital: 75.000 €
    Kreditbedarf: 395.000 €
  </vorhaben>
</kundenprofil>

<aufgabe>
Erstelle drei Finanzierungsszenarien mit unterschiedlichen 
Laufzeiten und Tilgungssätzen:
- Szenario A: Konservativ (hohe Tilgung, kurze Laufzeit)
- Szenario B: Ausgewogen (mittlere Tilgung)
- Szenario C: Flexibel (niedrige Tilgung, Sondertilgung)
Berücksichtige die aktuelle Zinslage (Stand: Februar 2026).
</aufgabe>

<regeln>
- Maximale Kreditrate: 35% des Haushaltsnettos
- Datenschutz: Keine echten Kundennamen verwenden
- Immer Restschuld nach 10 Jahren angeben
- Auf Risiken hinweisen (Zinsänderung nach Zinsbindung)
</regeln>

<format>
Tabelle mit Spalten:
| Szenario | Zinssatz | Tilgung | Rate/Monat | Zinsbindung | 
Restschuld nach 10J | Gesamtlaufzeit |

Darunter: Empfehlung mit Begründung (max. 5 Sätze)
</format>
```

### Was ist besser — und warum?

| Kriterium | Fließtext | XML-Struktur |
|---|---|---|
| **Lesbarkeit für Sie** | Alles in einem Block — Regeln, Daten, Aufgabe vermischt | Jeder Abschnitt sofort erkennbar |
| **Änderbarkeit** | Für einen anderen Kunden müssen Sie den ganzen Text umschreiben | Nur `<kundenprofil>` austauschen — Rest bleibt |
| **Vollständigkeit** | Leicht etwas zu vergessen | Leere Tags fallen auf: „Oh, ich habe `<regeln>` nicht ausgefüllt" |
| **KI-Ergebnis** | Gut, aber gelegentlich werden Regeln übersehen | Konsistenter, besonders bei langen Prompts |
| **Wiederverwendbarkeit** | Gering — jeder Prompt ist ein Unikat | Hoch — Template einmal bauen, Daten austauschen |

> **Volksbank-Analogie:** Der Fließtext-Prompt ist wie ein handgeschriebener Brief. Der XML-Prompt ist wie ein standardisierter Kreditantrag mit vorgedruckten Feldern. Beides transportiert die gleichen Informationen — aber den Kreditantrag kann jeder Sachbearbeiter sofort bearbeiten, auch wenn er ihn zum ersten Mal sieht.

---

## Schritt 4: Praxisbeispiel 2 — Dokumente sauber trennen

Ein häufiger Anwendungsfall: Sie wollen die KI zwei oder mehr Texte vergleichen lassen. Ohne klare Trennung weiß die KI oft nicht, wo Dokument A aufhört und Dokument B anfängt.

### Das Problem

```
Vergleiche diese beiden Texte:

Die aktuelle Konditionenliste der Volksbank Hellweg 
bietet Baufinanzierungen ab 3,2% effektiv...

[2 Seiten Text]

Die Sparkasse Soest-Werl bewirbt aktuell 
Baufinanzierungen ab 2,99% effektiv...

[2 Seiten Text]

Erstelle eine Vergleichstabelle.
```

→ Die KI weiß nicht exakt, wo „Volksbank-Text" endet und „Sparkasse-Text" beginnt, besonders bei langen Dokumenten.

### Die Lösung mit XML-Tags

```
<aufgabe>
Vergleiche die folgenden zwei Konditionenlisten und erstelle 
eine Vergleichstabelle. Fokus: Zinssätze, Tilgungsoptionen, 
Sondertilgung, Bereitstellungszinsen, Besonderheiten.
</aufgabe>

<dokument_a titel="Konditionenliste Volksbank Hellweg, Stand 02/2026">
Die aktuelle Konditionenliste der Volksbank Hellweg 
bietet Baufinanzierungen ab 3,2% effektiv...

[kompletter Text Dokument A]
</dokument_a>

<dokument_b titel="Konditionenliste Sparkasse Soest-Werl, Stand 02/2026">
Die Sparkasse Soest-Werl bewirbt aktuell 
Baufinanzierungen ab 2,99% effektiv...

[kompletter Text Dokument B]
</dokument_b>

<format>
Vergleichstabelle:
| Kriterium | Volksbank Hellweg | Sparkasse Soest-Werl | Vorteil |
Darunter: 3-5 Sätze Fazit mit Empfehlung.
</format>

<regeln>
- Nur Fakten aus den Dokumenten verwenden
- Nichts hinzufügen, was nicht in den Texten steht
- Bei unklaren Angaben: „nicht angegeben" schreiben
</regeln>
```

### Warum das funktioniert

- `<dokument_a>` und `<dokument_b>` erzeugen **glasklare Grenzen** — die KI verwechselt nie, welche Zahl zu welchem Anbieter gehört
- Das `titel`-Attribut gibt der KI Kontext, ohne dass Sie es im Fließtext erklären müssen
- Die Struktur ist **erweiterbar**: Für einen dritten Anbieter fügen Sie einfach `<dokument_c>` hinzu
- `<regeln>` mit „Nichts hinzufügen" verhindert Halluzinationen (vgl. Tutorial 01-03)

> **Praxis-Tipp:** Diese Technik funktioniert für jeden Vergleich: Zwei Anbieterangebote, zwei Vertragsentwürfe, zwei BaFin-Rundschreiben, alter vs. neuer Prozess. Immer wenn Sie „Vergleiche A mit B" sagen, nutzen Sie `<dokument_a>` und `<dokument_b>`.

---

## Schritt 5: Praxisbeispiel 3 — System-Prompts professionell aufbauen

In Tutorial 01-04 haben Sie System-Prompts kennengelernt — die dauerhafte Grundkonfiguration für KI-Assistenten. Mit XML-Tags wird ein System-Prompt von einer Textwand zu einem **modularen Baukasten**.

### Vorher: System-Prompt als Fließtext

```
Du bist ein freundlicher Kundenberater der Volksbank 
Hellweg eG. Du berätst Privatkunden zu Girokonten, 
Sparanlagen, Baufinanzierung und Versicherungen. Du 
sprichst Deutsch, professionell aber nahbar. Du darfst 
keine Rechtsberatung geben, keine konkreten Konditionen 
zusagen und musst immer auf einen persönlichen 
Beratungstermin verweisen wenn es um verbindliche 
Angebote geht. Du kennst die Genossenschaftsidee und 
die Vorteile der Mitgliedschaft...
```

### Nachher: System-Prompt mit XML-Architektur

```
<system>

<identitaet>
  <name>VB-Assistent</name>
  <bank>Volksbank Hellweg eG</bank>
  <region>Soest, Werl, Wickede (Südwestfalen)</region>
  <sprache>Deutsch</sprache>
  <tonalitaet>Professionell, nahbar, vertrauensvoll. 
  Wie ein kompetenter Nachbar, der sich auskennt.</tonalitaet>
</identitaet>

<kompetenzen>
  <bereich>Girokonto und Zahlungsverkehr</bereich>
  <bereich>Sparanlagen und Vermögensaufbau</bereich>
  <bereich>Baufinanzierung</bereich>
  <bereich>Versicherungen (Überblick, keine Details)</bereich>
  <bereich>Genossenschaftsmodell und Mitgliedschaft</bereich>
</kompetenzen>

<regeln>
  <pflicht>Immer auf persönlichen Beratungstermin verweisen 
  bei verbindlichen Angeboten</pflicht>
  <pflicht>Genossenschaftsvorteile erwähnen wo passend</pflicht>
  <pflicht>Bei Unsicherheit: „Das kläre ich gern mit meinem 
  Kollegen für Sie" statt raten</pflicht>
  
  <verbot>Keine Rechtsberatung oder Steuerberatung</verbot>
  <verbot>Keine konkreten Konditionen zusagen</verbot>
  <verbot>Keine Aussagen über einzelne Kunden</verbot>
  <verbot>Keine Empfehlung gegen die Volksbank</verbot>
</regeln>

<eskalation>
  Wenn der Kunde fragt nach:
  - Konkreten Konditionen → „Dafür vereinbaren wir am 
    besten einen persönlichen Termin: [Telefonnummer]"
  - Beschwerden → „Das nehme ich ernst. Ich verbinde Sie 
    mit unserem Qualitätsmanagement."
  - Technischen Problemen (Online-Banking) → „Unser 
    technischer Support hilft Ihnen: [Telefonnummer]"
</eskalation>

<wissen>
  <fakt>Die Volksbank Hellweg hat 15 Filialen in der 
  Region Soest</fakt>
  <fakt>Mitgliedschaft ab 1 Genossenschaftsanteil 
  (Betrag: bitte im Beratungsgespräch klären)</fakt>
  <fakt>Online-Banking über VR-Banking App und 
  Website</fakt>
</wissen>

</system>
```

### Warum die XML-Version besser ist

| Vorteil | Erklärung |
|---|---|
| **Modular** | Sie können `<kompetenzen>` erweitern, ohne den Rest anzufassen |
| **Klar getrennt: Pflichten vs. Verbote** | `<pflicht>` und `<verbot>` in eigenen Tags — kein „du darfst / du darfst nicht" durcheinander |
| **Eskalationslogik** | Eigener Abschnitt für „Wenn-dann"-Situationen — die KI weiß genau, wann sie weiterleiten soll |
| **Faktenwissen** | `<wissen>` enthält nur geprüfte Fakten — kein Halluzinationsrisiko |
| **Teamfähig** | Ein Kollege kann den System-Prompt lesen und sofort verstehen, was konfiguriert ist |

> **Volksbank-Analogie:** Der Fließtext-System-Prompt ist wie eine mündliche Einweisung für den neuen Azubi — er hört zu und vergisst die Hälfte. Der XML-System-Prompt ist wie ein Handbuch mit Inhaltsverzeichnis, Regelteil und FAQ — er kann jederzeit nachschlagen.

---

## Schritt 6: Praxisbeispiel 4 — Bestehende Prompts in XML überführen

Lassen Sie uns eine Vorlage aus Kapitel 01 nehmen und in XML umwandeln. Wir verwenden die **Meeting-Protokoll-Vorlage** aus Tutorial 01-06 (Schritt 3) als Beispiel.

### Original (Fließtext mit Markdown):

```
Du bist ein professioneller Meeting-Analyst für eine 
deutsche Genossenschaftsbank. Du erstellst aus Meeting-
Transkripten klare, strukturierte und umsetzbare Protokolle. 
Schreibe auf Deutsch, professionell aber verständlich.

KONTEXT:
Du erhältst ein Meeting-Transkript der Volksbank Hellweg eG...

AUFGABEN — Schritt für Schritt:
1. Lies das gesamte Transkript sorgfältig durch.
2. Erfasse die MEETING-GRUNDDATEN...
[... 50 Zeilen Anweisungen ...]

FORMATIERUNG:
- Datum: YYYY-MM-DD...

AUSGABEFORMAT (Markdown):
### Meeting-Grunddaten
[...]
```

### In XML überführt:

```
<rolle>
Professioneller Meeting-Analyst für eine deutsche 
Genossenschaftsbank. Erstellt aus Transkripten klare, 
strukturierte und umsetzbare Protokolle. Sprache: Deutsch, 
professionell aber verständlich.
</rolle>

<kontext>
Bank: Volksbank Hellweg eG
Transkript-Quelle: Teams/Zoom-Aufzeichnung oder 
handschriftliche Notizen
Vertraulichkeit: Intern
</kontext>

<transkript>
[HIER TRANSKRIPT EINFÜGEN]
</transkript>

<arbeitsschritte>
  <schritt n="1">Lies das gesamte Transkript sorgfältig 
  durch</schritt>
  <schritt n="2">Erfasse Meeting-Grunddaten: Titel, Datum, 
  Uhrzeit, Teilnehmer, Abwesende</schritt>
  <schritt n="3">Liste die Hauptthemen auf</schritt>
  <schritt n="4">Erstelle für jedes Thema eine Zusammenfassung 
  (3-5 Stichpunkte) und dokumentiere Entscheidungen</schritt>
  <schritt n="5">Sammle Key Takeaways (3-5 wichtigste 
  Punkte)</schritt>
  <schritt n="6">Extrahiere Action Items als Tabelle: 
  Was | Wer | Bis wann | Priorität</schritt>
  <schritt n="7">Liste Follow-ups fürs nächste Meeting</schritt>
  <schritt n="8">Dokumentiere offene Fragen</schritt>
  <schritt n="9">Erfasse Risiken oder Abhängigkeiten</schritt>
  <schritt n="10">Notiere Unklarheiten mit Zeitstempel</schritt>
  <schritt n="11">Nächstes Meeting: Datum + Agenda</schritt>
</arbeitsschritte>

<datenschutz>
  <anonymisierung>Kundennamen → „[Kunde A]"</anonymisierung>
  <anonymisierung>Kontonummern → „[anonymisiert]"</anonymisierung>
  <anonymisierung>Konkrete Kundenbeträge → „[Betrag]"</anonymisierung>
  <grundregel>Erfinde NICHTS — nur Informationen aus dem 
  Transkript verwenden</grundregel>
</datenschutz>

<format>
  <stil>Markdown</stil>
  <datum>YYYY-MM-DD</datum>
  <namen>„Vorname Nachname (Rolle)"</namen>
  <fehlend>„unbekannt" oder „tbd"</fehlend>
</format>
```

### Was hat sich verbessert?

| Aspekt | Fließtext | XML |
|---|---|---|
| Transkript einfügen | Irgendwo am Ende drankleben | Eigenes `<transkript>`-Tag — unmissverständlich |
| Arbeitsschritte | Nummerierte Liste im Fließtext | Nummerierte `<schritt>`-Tags — KI erkennt die Reihenfolge explizit |
| Datenschutz | Irgendwo unter den Aufgaben | Eigener `<datenschutz>`-Block — wird nicht übersehen |
| Wiederverwenden | Schwierig: Alles ist verwoben | Einfach: `<transkript>` austauschen, Rest bleibt |

### Müssen Sie alle Ihre Prompts umschreiben?

**Nein.** Die Fließtext-Vorlagen aus Kapitel 01 funktionieren weiterhin. XML ist eine Verbesserung, kein Muss. Nutzen Sie XML, wenn:
- Ihr Prompt länger als ~300 Wörter ist
- Sie den Prompt regelmäßig wiederverwenden
- Sie verschiedene Daten in denselben Prompt einfügen (verschiedene Kunden, verschiedene Dokumente)
- Sie einen System-Prompt für einen Chatbot oder Custom GPT bauen (→ Kapitel 03)

> **Praxis-Tipp:** Fangen Sie mit einem Prompt an, den Sie häufig nutzen. Überführen Sie nur diesen einen in XML. Wenn Sie merken, dass es sich lohnt, machen Sie nach und nach weitere. Es gibt keinen Zwang, alles auf einmal umzustellen.

---

## Schritt 7: Verschachtelte Strukturen — Wenn es komplexer wird

Für fortgeschrittene Anwendungen können Sie XML-Tags ineinander verschachteln — wie Ordner in Ordnern. Das ist besonders nützlich, wenn Sie **mehrere Kunden, mehrere Szenarien oder mehrere Schritte mit Unterpunkten** haben.

### Praxisbeispiel: Drei Kunden gleichzeitig bewerten

```
<rolle>
Erfahrener Kreditanalyst einer Genossenschaftsbank.
</rolle>

<aufgabe>
Bewerte die Kreditwürdigkeit der folgenden drei 
Kreditanfragen und erstelle für jede eine Empfehlung 
(Genehmigung / Ablehnung / Nachbesserung).
</aufgabe>

<kreditanfragen>

  <anfrage id="1">
    <person>Alter: 34, Angestellter, unbefristet</person>
    <einkommen>Netto: 3.800 €/Monat</einkommen>
    <vorhaben>Ratenkredit 25.000 €, 48 Monate</vorhaben>
    <sicherheiten>Keine</sicherheiten>
    <bestehende_kredite>Autofinanzierung 180 €/Monat, 
    Restlaufzeit 14 Monate</bestehende_kredite>
  </anfrage>

  <anfrage id="2">
    <person>Alter: 52, Selbständig seit 8 Jahren</person>
    <einkommen>Durchschnittliches Jahreseinkommen: 
    72.000 € (letzte 3 BWAs)</einkommen>
    <vorhaben>Betriebsmittelkredit 100.000 €</vorhaben>
    <sicherheiten>Grundschuld auf Gewerbeimmobilie 
    (Verkehrswert: 320.000 €, bestehende Belastung: 
    180.000 €)</sicherheiten>
    <bestehende_kredite>Immobilienkredit 1.200 €/Monat</bestehende_kredite>
  </anfrage>

  <anfrage id="3">
    <person>Alter: 28, Berufseinsteigerin, befristet 
    (Verlängerung wahrscheinlich)</person>
    <einkommen>Netto: 2.600 €/Monat</einkommen>
    <vorhaben>Baufinanzierung 280.000 €</vorhaben>
    <sicherheiten>Eigenkapital: 40.000 €, keine 
    weitere Grundschuld</sicherheiten>
    <bestehende_kredite>Keine</bestehende_kredite>
  </anfrage>

</kreditanfragen>

<bewertungskriterien>
- Kapitaldienstfähigkeit (max. 35% des Nettos)
- Sicherheitendeckung
- Beschäftigungsstabilität
- Gesamtverschuldung
- Risikobewertung (niedrig / mittel / hoch)
</bewertungskriterien>

<format>
Für jede Anfrage:
| Kriterium | Bewertung | Kommentar |
Darunter: Empfehlung + Begründung (3 Sätze)
Am Ende: Priorisierung aller drei Anfragen.
</format>
```

### Warum Verschachtelung hier hilft

- Jede `<anfrage>` ist eine eigenständige Einheit mit identischer Struktur
- Die KI verwechselt **nie** die Daten von Anfrage 1 mit Anfrage 3
- Sie können eine vierte Anfrage einfach als `<anfrage id="4">` hinzufügen
- Die `id`-Attribute helfen bei der Zuordnung in der Ausgabe

> **Volksbank-Analogie:** Das ist wie ein Stapel Kreditanträge auf Ihrem Schreibtisch — jeder in seiner eigenen Mappe, mit identischem Aufbau. Sie bearbeiten einen nach dem anderen, und es gibt keine Verwechslungsgefahr.

---

## Schritt 8: Modell-Unterschiede — Wer versteht XML am besten?

Nicht alle KI-Modelle reagieren gleich auf XML-Tags. Hier die wichtigsten Unterschiede:

| Modell | XML-Verständnis | Besonderheiten | Empfehlung |
|---|---|---|---|
| **Claude (Opus 4.6 / Sonnet 4)** | ⭐⭐⭐ Exzellent | XML-Tags sind von Anthropic offiziell empfohlen. Claude respektiert Tag-Hierarchien, liest Attribute, und trennt Abschnitte sauber | Erste Wahl für XML-strukturierte Prompts |
| **ChatGPT (GPT-5.2)** | ⭐⭐ Sehr gut | Versteht XML-Tags zuverlässig, nutzt sie aber nicht so strikt wie Claude. Bei sehr tiefer Verschachtelung (4+ Ebenen) gelegentlich ungenau | Funktioniert gut, Markdown-Delimiter als Alternative |
| **Gemini (2.5 Pro)** | ⭐⭐ Gut | Versteht XML-Grundstruktur. Bei komplexen verschachtelten Strukturen weniger zuverlässig als Claude | Für einfache XML-Strukturen gut, für komplexe besser Claude |

### Was wenn mein Modell XML nicht perfekt versteht?

Kein Problem. XML-Tags sind **abwärtskompatibel**: Selbst wenn ein Modell die Tags nicht als Struktur erkennt, versteht es sie als Textmarkierungen — und das allein verbessert die Ergebnisse. Im schlimmsten Fall ignoriert das Modell die Tags und behandelt den Inhalt als normalen Text. Es wird nie *schlechter* durch XML-Tags.

> **Praxis-Tipp:** Wenn Sie nicht sicher sind, welches Modell Sie nutzen, verwenden Sie XML-Tags trotzdem. Sie helfen immer — manchmal als echte Strukturerkennung, manchmal einfach als visuelle Trennung.

---

## Was XML bei Prompts (noch) nicht kann

| Limitation | Warum problematisch | Workaround |
|---|---|---|
| **Keine Validierung** | Die KI prüft nicht, ob Ihre XML-Tags korrekt geschlossen sind. `<rolle>...<rolle>` (fehlendes `/`) wird oft trotzdem verstanden, aber nicht immer | Tags sorgfältig schließen. Tipp: Öffnendes und schließendes Tag gleichzeitig tippen, dann Inhalt einfügen |
| **Keine echte Datentyp-Prüfung** | `<alter>vierundzwanzig</alter>` wird akzeptiert, obwohl Sie eine Zahl meinen | Für kritische Daten: explizit angeben was erwartet wird, z.B. `<alter format="Zahl">42</alter>` |
| **Token-Overhead** | XML-Tags verbrauchen Tokens. Ein stark strukturierter Prompt kann 10-15% mehr Tokens kosten als die Fließtext-Version | Bei einfachen, kurzen Prompts (unter 100 Wörter) lohnt sich XML nicht — da reicht Fließtext |
| **Lernkurve** | Für absolute Einsteiger wirken XML-Tags einschüchternd — „Das sieht aus wie Code" | Betonen: Es sind nur Post-its. Und: Nicht jeder Prompt braucht XML |
| **Kein Standard-Schema** | Es gibt kein „offizielles" Tag-Set. Jeder erfindet eigene Tag-Namen | Einheitlichkeit im Team: Einigt euch auf 8-10 Standard-Tags (siehe Schritt 2) |

> **Kernregel:** XML-Tags sind ein Werkzeug, kein Gesetz. Nutzen Sie sie, wenn sie helfen — bei langen, komplexen oder wiederverwendbaren Prompts. Nutzen Sie sie nicht, wenn ein kurzer Fließtext ausreicht. Die beste Struktur ist die, die Sie tatsächlich verwenden.

---

## Kosten-Vergleich: Fließtext vs. XML

| Aspekt | Fließtext-Prompt | XML-Prompt |
|---|---|---|
| **Erstellungszeit (erstmalig)** | 5 Min | 8-10 Min (+60%) |
| **Änderungszeit (Daten austauschen)** | 3-5 Min (Text durchsuchen) | 30 Sek (Tag finden, Inhalt ersetzen) |
| **Token-Kosten** | Baseline | +10-15% durch Tags |
| **Ergebnisqualität bei einfachen Prompts** | Sehr gut | Gleich gut (kein Vorteil) |
| **Ergebnisqualität bei komplexen Prompts** | Gut, gelegentlich Regeln übersehen | Sehr gut, konsistenter |
| **Wiederverwendbarkeit** | Gering | Hoch (Template-Prinzip) |
| **Team-Tauglichkeit** | Schwer — jeder versteht den Prompt anders | Gut — Struktur ist selbsterklärend |

> **Fazit:** XML lohnt sich **nicht** für den schnellen Einmal-Prompt. XML lohnt sich **sehr** für Prompts, die Sie wiederverwenden, im Team teilen oder als Grundlage für Custom GPTs nutzen (→ Kapitel 03).

---

## Entscheidungsbaum: Wann XML, wann Fließtext?

```
┌─────────────────────────────────────────────────────────────────┐
│       🗺️ Brauche ich XML für diesen Prompt?                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Ist der Prompt kürzer als 100 Wörter?                         │
│  ├── JA → Fließtext reicht ✅                                   │
│  └── NEIN ↓                                                    │
│                                                                 │
│  Enthält der Prompt verschiedene Datentypen?                   │
│  (Kundendaten + Aufgabe + Regeln + Dokumente)                 │
│  ├── JA → XML empfohlen 🏷️                                     │
│  └── NEIN ↓                                                    │
│                                                                 │
│  Werde ich den Prompt wiederverwenden?                          │
│  ├── JA → XML empfohlen 🏷️                                     │
│  └── NEIN ↓                                                    │
│                                                                 │
│  Teile ich den Prompt mit Kollegen?                            │
│  ├── JA → XML empfohlen 🏷️                                     │
│  └── NEIN → Fließtext reicht ✅                                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Das Wichtigste auf einen Blick

| Konzept | Erklärung | Wichtigster Tipp |
|---|---|---|
| **XML-Tags** | Benannte Klammern um Textabschnitte: `<tag>Inhalt</tag>` | Kein Code — tippen Sie es ins Chat-Fenster wie normalen Text |
| **Strukturierung** | Prompt in benannte Abschnitte aufteilen statt Fließtext | Die 8 Standard-Tags decken 90% aller Fälle ab |
| **Verschachtelung** | Tags in Tags für komplexe Daten | Maximal 2-3 Ebenen tief — mehr verwirrt |
| **Dokumententrennung** | `<dokument_a>` und `<dokument_b>` für Vergleiche | Immer wenn „Vergleiche A mit B" → separate Tags |
| **System-Prompts** | XML macht System-Prompts modular und wartbar | Eigener Block für Pflichten, Verbote und Eskalation |
| **Template-Prinzip** | Einmal Struktur bauen, Daten austauschen | Der wahre Vorteil zeigt sich ab der zweiten Nutzung |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---|---|
| XML-Tags als Delimiter | Vertieft Tutorial 01-04, Schritt 3: Dort eingeführt als eine von mehreren Delimiter-Optionen — hier als vollständiges Strukturierungssystem |
| `<regeln>` mit Pflichten und Verboten | Nutzt Constraint-basiertes Prompting aus Tutorial 01-04, Schritt 7: Klare Einschränkungen in eigenem Block |
| `<transkript>` als Eingabe-Container | Ersetzt das „Füge jetzt bitte das Transkript hier ein" aus Tutorial 01-06: Sauberer, eindeutiger |
| Anonymisierung in `<datenschutz>` | Vertieft Datenschutz-Regeln aus Tutorial 01-05 und 01-06: Eigener Block statt Nebensatz |
| Verschachtelte Kundendaten | Baut auf Few-Shot-Prinzip aus Tutorial 01-04, Schritt 4: Mehrere strukturierte Beispiele statt loser Text |
| System-Prompt mit XML | Erweitert Tutorial 01-04, Schritt 2: Vom Fließtext-System-Prompt zum modularen XML-System-Prompt |

---

## ⚠️ Compliance-Hinweis: XML ändert nichts am Datenschutz

XML-Tags machen Ihre Prompts strukturierter — aber **nicht sicherer**. Alle Datenschutz-Regeln aus Tutorial 01-05 und 01-06 gelten weiterhin:

| Regel | Gilt auch mit XML |
|---|---|
| Keine Kundennamen in externe Tools | ✅ `<kunde><name>Herr Müller</name></kunde>` ist genauso verboten wie „Herr Müller" im Fließtext |
| Anonymisieren vor dem Prompten | ✅ `<kunde><name>[Kunde A]</name></kunde>` — anonymisieren passiert VOR dem Einfügen |
| Vier-Augen-Prinzip | ✅ Auch XML-generierte Ergebnisse sind Entwürfe, keine fertigen Dokumente |
| BaFin: KI unter DORA | ✅ Strukturierte Prompts ändern nichts an der IKT-Dokumentationspflicht |

---

## 🚀 Starten Sie hier — Ihr erster Schritt am Montag

> **Nehmen Sie einen Prompt, den Sie diese Woche ohnehin verwenden. Fügen Sie nur drei XML-Tags hinzu: `<rolle>`, `<aufgabe>` und `<daten>`. Vergleichen Sie das Ergebnis mit Ihrer bisherigen Fließtext-Version.**

Das dauert 2 Minuten extra. Und Sie werden sehen: Die KI-Antwort wird nicht revolutionär anders — aber sie wird *konsistenter*. Besonders, wenn Sie den gleichen Prompt morgen mit anderen Daten nochmal verwenden.

**Die Reihenfolge zum Reinwachsen:**
1. 🥇 **Woche 1:** Drei Standard-Tags verwenden: `<rolle>`, `<aufgabe>`, `<daten>`
2. 🥈 **Woche 2:** `<regeln>` und `<format>` ergänzen
3. 🥉 **Woche 3:** Ein Dokumenten-Vergleich mit `<dokument_a>` / `<dokument_b>`
4. 🏅 **Danach:** Einen System-Prompt mit XML-Architektur aufbauen

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Ihren ersten XML-Prompt bauen

**Aufgabe:** Überführen Sie diesen Fließtext-Prompt in eine XML-Struktur:

```
Du bist ein Kundenberater der Volksbank. Ein Kunde 
möchte 50.000€ anlegen, Zeitraum 5 Jahre, möglichst 
sicher, moderate Rendite. Er ist 55 Jahre alt und 
will das Geld für die Renovierung seines Hauses nutzen. 
Erstelle drei Anlagevorschläge als Tabelle mit 
Produktname, erwarteter Rendite, Risiko und Verfügbarkeit. 
Erkläre Fachbegriffe verständlich.
```

**Ihre Aufgabe:**
1. Identifizieren Sie die verschiedenen Informationstypen (Rolle, Kundendaten, Aufgabe, Format, Regeln)
2. Erstellen Sie eine XML-Struktur mit passenden Tags
3. Testen Sie beide Versionen (Fließtext + XML) im gleichen KI-Tool
4. Vergleichen Sie: Sind die Ergebnisse unterschiedlich? Welches ist strukturierter?

### Hands-on 2: Dokumentenvergleich mit XML

**Aufgabe:** Nutzen Sie XML-Tags, um die KI zwei kurze Texte vergleichen zu lassen:

```
Text A: „Die Volksbank bietet Tagesgeld mit 2,1% Zinsen, 
tägliche Verfügbarkeit, Einlagensicherung bis 100.000€ 
über die Sicherungseinrichtung des BVR."

Text B: „Die Online-Bank bietet Tagesgeld mit 3,5% Zinsen, 
tägliche Verfügbarkeit, Einlagensicherung bis 100.000€ 
über die gesetzliche Einlagensicherung."
```

**Ihre Aufgabe:**
1. Strukturieren Sie den Prompt mit `<dokument_a>`, `<dokument_b>`, `<aufgabe>` und `<format>`
2. Fragen Sie die KI: „Vergleiche und empfehle — welches Angebot passt für einen sicherheitsorientierten Kunden mit 30.000€?"
3. Prüfen Sie: Verwechselt die KI die Daten der beiden Anbieter?

### Hands-on 3: Modellvergleich — Wer versteht XML besser?

**Aufgabe:** Geben Sie **zwei verschiedenen KI-Modellen** denselben XML-strukturierten Prompt:

```
<rolle>Kreditanalyst einer Genossenschaftsbank</rolle>

<anfrage>
  <person>Alter: 45, selbständiger Handwerker seit 12 Jahren</person>
  <einkommen>Jahresüberschuss laut BWA: 85.000 €</einkommen>
  <vorhaben>Betriebserweiterung: Neue Werkstatt, 180.000 €</vorhaben>
  <sicherheiten>Grundschuld auf Privatimmobilie (Wert: 
  350.000 €, Belastung: 120.000 €)</sicherheiten>
</anfrage>

<aufgabe>
Bewerte die Kreditwürdigkeit. Nenne Stärken, Schwächen 
und eine Empfehlung.
</aufgabe>

<format>
Stärken: Stichpunkte
Schwächen: Stichpunkte  
Empfehlung: 3 Sätze
Risikobewertung: niedrig / mittel / hoch
</format>
```

**Vergleichen Sie:**
- Welches Modell respektiert die XML-Struktur in der Ausgabe?
- Welches trennt sauberer zwischen Stärken und Schwächen?
- Welches gibt die hilfreichere Empfehlung?

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **XML** | Extensible Markup Language — eine Auszeichnungssprache mit benannten Tags. In Prompts verwendet als Strukturierungswerkzeug: `<tag>Inhalt</tag>`. Kein Programmieren — nur Textmarkierungen |
| **Tag** | Ein XML-Bezeichner in spitzen Klammern. Jedes Tag hat eine öffnende (`<rolle>`) und eine schließende (`</rolle>`) Variante. Der Schrägstrich im schließenden Tag ist wichtig |
| **Verschachtelung** | Tags innerhalb von Tags: `<kunde><name>Müller</name></kunde>`. Wie Ordner in Ordnern — erzeugt Hierarchie und Gruppierung |
| **Attribut** | Zusatzinformation im öffnenden Tag: `<dokument titel="Konditionenliste">`. Gibt der KI Kontext, ohne einen eigenen Tag zu benötigen |
| **Delimiter** | Trennzeichen, die verschiedene Teile eines Prompts voneinander abgrenzen. XML-Tags sind die mächtigste Form von Delimitern (vgl. Tutorial 01-04, Schritt 3) |
| **Schema** | Die Gesamtstruktur eines XML-Prompts — welche Tags in welcher Reihenfolge mit welcher Verschachtelung. Wie der Aufbau eines Formulars |
| **System-Prompt** | Dauerhafte Grundkonfiguration einer KI (vgl. Tutorial 01-04, Schritt 2). Mit XML-Tags wird ein System-Prompt modular und wartbar |
| **Template** | Wiederverwendbare Vorlage mit fester Struktur und austauschbaren Inhalten. XML-Prompts eignen sich ideal als Templates, weil die Daten-Tags einfach neu befüllt werden können |
| **Token-Overhead** | Zusätzlicher Token-Verbrauch durch die Tags selbst. Bei XML-Prompts typischerweise 10-15% mehr als bei Fließtext — in den meisten Fällen vernachlässigbar |
| **Anthropic** | Firma hinter dem KI-Modell Claude. Empfiehlt seit 2024 offiziell XML-Tags als bevorzugte Strukturierungsmethode für Prompts |

---

