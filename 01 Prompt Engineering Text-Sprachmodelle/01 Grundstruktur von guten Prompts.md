# Prompt Engineering — Grundlagen für gute Prompts

**Vom vagen Wunsch zum präzisen Auftrag — wie Sie KI mit den richtigen Worten zu besseren Ergebnissen führen**

---

## Warum dieses Tutorial?

In Kapitel Grundlagen LLMs haben Sie gelernt, wie KI funktioniert: wie LLMs Token vorhersagen (Tutorial 01), wie Diffusion Bilder erzeugt (Tutorial 02), wie multimodale Modelle verschiedene Sinne verbinden (Tutorial 03) und wie KI mit der Außenwelt kommuniziert (Tutorial 07). Sie wissen jetzt, was unter der Haube passiert.

Aber Wissen über den Motor macht Sie noch nicht zum guten Fahrer.

Stellen Sie sich vor, Sie haben einen neuen Kollegen eingestellt. Er ist brillant, kennt sich in hundert Fachgebieten aus, arbeitet in Sekunden — aber er nimmt **jedes Wort wörtlich**. Wenn Sie ihm sagen „Mach mal was zu Baufinanzierung", liefert er Ihnen vielleicht einen historischen Abriss der Baufinanzierung in Deutschland seit 1948. Nützlich? Vielleicht. Aber nicht das, was Sie wollten.

Genau so funktioniert KI. Sie rät nicht, was Sie meinen — sie vervollständigt, was Sie sagen. Erinnern Sie sich an Tutorial 00-01: Ein LLM berechnet bei jedem Token die Wahrscheinlichkeit für das nächste. Ihr Prompt ist der Startpunkt dieser Berechnung. Je präziser Ihr Startpunkt, desto weniger muss die KI raten — und desto besser wird das Ergebnis.

Das ist die gute Nachricht: **Sie haben die Kontrolle.** Sie müssen nur lernen, sie zu nutzen.

**Was Sie nach diesem Tutorial wissen werden:**

- Was ein Prompt ist — und warum die Formulierung über Erfolg oder Misserfolg entscheidet
- Die 6 Bausteine, aus denen jeder gute Prompt besteht
- Wie Sie einen vagen Wunsch Schritt für Schritt in einen präzisen Auftrag verwandeln
- Warum Rollen, Kontext und Beispiele die Qualität dramatisch verändern
- Wie Sie die häufigsten Fehler vermeiden — inklusive gefährlicher Halluzinationen
- Wie Sie Prompts iterativ verbessern statt auf den perfekten Wurf zu hoffen

---

## Schritt 1: Was ist ein Prompt — und warum ist er so wichtig?

Ein **Prompt** ist Ihre Anweisung an die KI. Alles, was Sie in das Eingabefeld von ChatGPT, Claude oder Gemini tippen, ist ein Prompt. Es ist Ihre Sprache, Ihr Werkzeug, Ihre Fernbedienung.

> **Volksbank-Analogie:** Stellen Sie sich vor, ein Kunde kommt an Ihren Schalter und sagt: „Machen Sie was mit meinem Geld." Was tun Sie? Sie fragen nach. Wie viel? Wohin? Bis wann? Welches Risiko? — Die KI fragt aber **nicht** nach (es sei denn, Sie sagen ihr, dass sie das soll). Sie macht einfach. Und „einfach machen" mit vagen Anweisungen führt selten zum gewünschten Ergebnis.

### Der Unterschied, den Formulierung macht

Vergleichen Sie diese beiden Prompts:

**❌ Vager Prompt:**
```
Schreib was über Baufinanzierung.
```

**✅ Präziser Prompt:**
```
Erkläre einem Erstkäufer (Mitte 30, Einkommen 4.500€ brutto, Region Hellweg) 
die 3 wichtigsten Faktoren, die er bei einer Baufinanzierung über die Volksbank 
beachten sollte. Maximal 150 Wörter, in einfacher Sprache ohne Fachjargon.
```

Der erste Prompt gibt der KI fast keinen Anhaltspunkt. Sie muss raten: Für wen? Wie lang? Welcher Aspekt? Das Ergebnis wird generisch und beliebig.

Der zweite Prompt definiert: **Wer** (Erstkäufer), **Was** (3 Faktoren), **Wie** (150 Wörter, einfache Sprache), **Wozu** (Beratung bei der Volksbank). Die KI hat einen klaren Auftrag — und liefert entsprechend.

### Warum das technisch funktioniert

Erinnern Sie sich an die **Attention-Mechanismen** aus Tutorial 01? Das LLM gewichtet bei jeder Antwort, welche Teile Ihres Prompts besonders relevant sind. Ein präziser Prompt aktiviert die richtigen „Wissens-Bereiche" im Modell. „Baufinanzierung" allein aktiviert alles von Hypothekenrecht bis zur Geschichte des Bausparvereins. „Baufinanzierung für Erstkäufer, 3 Faktoren, einfache Sprache" fokussiert das Modell wie eine Lupe.

> **Faustregel:** Was Sie nicht sagen, überlassen Sie dem Zufall. Was Sie präzise sagen, kontrollieren Sie.

---

## Schritt 2: Die 6 Bausteine eines guten Prompts

Jeder gute Prompt lässt sich aus sechs Bausteinen zusammensetzen. Nicht jeder Prompt braucht alle sechs — aber je mehr Sie nutzen, desto besser wird das Ergebnis.

```
              ┌───────────────────┐
              │    1. ROLLE       │  ← Wer spricht?
              │  „Die Perspektive"│     Definiert den Blickwinkel
              └─────────┬─────────┘
                        │
              ┌─────────▼─────────┐
              │   2. KONTEXT      │  ← Was muss die KI wissen?
              │  „Die Situation"  │     Hintergrund, Daten, Zielgruppe
              └─────────┬─────────┘
                        │
         ┌──────────────▼──────────────┐
         │        3. AUFGABE           │  ← Was genau soll entstehen?
         │     „Der Arbeitsauftrag"    │     Verb + Objekt + Ergebnis
         └──────────────┬──────────────┘
                        │
         ┌──────────────▼──────────────┐
         │        4. REGELN            │  ← Was darf sie NICHT?
         │     „Die Leitplanken"       │     Länge, Ton, Verbote
         └──────────────┬──────────────┘
                        │
    ┌───────────────────▼───────────────────┐
    │           5. BEISPIELE                │  ← Wie soll es aussehen?
    │        „Zeigen statt beschreiben"     │     1-3 Muster des Ergebnisses
    └───────────────────┬───────────────────┘
                        │
    ┌───────────────────▼───────────────────┐
    │            6. FORMAT                  │  ← In welcher Form?
    │       „Das Formular bestimmen"        │     Liste, Tabelle, E-Mail, ...
    └───────────────────────────────────────┘

    ▲ oben = Rahmen setzen    ▼ unten = Ergebnis formen
    Je mehr Bausteine Sie nutzen, desto präziser das Ergebnis.
    Nicht jeder Prompt braucht alle 6 — aber AUFGABE ist immer Pflicht.
```

> **Volksbank-Analogie:** Denken Sie an einen Kreditantrag. Er hat Struktur: Wer beantragt (Rolle), welche Situation (Kontext), was genau (Aufgabe), welche Bedingungen gelten (Regeln), Referenzbeispiele (Beispiele) und ein vorgegebenes Formular (Format). Ohne diese Struktur ist ein Antrag unvollständig. Ohne diese Bausteine ist ein Prompt unvollständig.

Schauen wir uns jeden Baustein im Detail an.

---

## Schritt 3: Von schlecht zu gut — ein Prompt in 5 Stufen

Bevor wir die Bausteine einzeln vertiefen, sehen Sie den Effekt am lebenden Objekt. Wir nehmen **einen Prompt** und verbessern ihn in fünf Stufen — jede fügt einen oder mehrere Bausteine hinzu.

### Stufe 0: Der Wunsch (0 Bausteine)

```
Schreib was über unser neues Girokonto.
```

**Was die KI daraus macht:** Einen generischen Text über Girokonten. Keine Ahnung, welche Bank, welches Produkt, für wen, in welchem Kontext. Das Ergebnis ist beliebig — es könnte von jeder Bank für jeden Zweck sein.

### Stufe 1: + Aufgabe (1 Baustein)

```
Erstelle eine Produktbeschreibung für unser neues Girokonto „VR-MeinKonto Flex" 
mit den 3 wichtigsten Vorteilen für den Kunden.
```

**Was sich verbessert:** Die KI weiß jetzt *was* sie tun soll (Produktbeschreibung) und *worüber* (VR-MeinKonto Flex). Aber sie rät noch: Für wen? Welcher Ton? Wie lang?

### Stufe 2: + Rolle (2 Bausteine)

```
Du bist Marketingexpertin bei der Volksbank Hellweg. 

Erstelle eine Produktbeschreibung für unser neues Girokonto „VR-MeinKonto Flex" 
mit den 3 wichtigsten Vorteilen für den Kunden.
```

**Was sich verbessert:** Die Antwort klingt jetzt nach Bankkommunikation, nicht nach Wikipedia. Die Rolle verändert Wortwahl, Perspektive und Fokus.

### Stufe 3: + Kontext + Regeln (4 Bausteine)

```
Du bist Marketingexpertin bei der Volksbank Hellweg. 

Hintergrund: Wir launchen nächste Woche das Girokonto „VR-MeinKonto Flex" 
für junge Berufstätige (25-35 Jahre). Kernfeatures: Keine Kontoführungsgebühr 
im ersten Jahr, Apple/Google Pay, integriertes Haushaltsbuch in der VR-Banking-App.

Erstelle eine Produktbeschreibung mit den 3 wichtigsten Vorteilen für den Kunden.

Regeln: Maximal 120 Wörter. Kein Bankjargon. Duzen statt Siezen. 
Nicht „günstig" sagen (wir positionieren über Mehrwert, nicht über Preis).
```

**Was sich verbessert:** Jetzt kennt die KI die Zielgruppe, die Features und die Kommunikationsregeln. Das Ergebnis ist nicht mehr generisch — es ist maßgeschneidert für die Volksbank Hellweg.

### Stufe 4: + Beispiel + Format (6 Bausteine)

```
Du bist Marketingexpertin bei der Volksbank Hellweg.

Hintergrund: Wir launchen nächste Woche das Girokonto „VR-MeinKonto Flex" 
für junge Berufstätige (25-35 Jahre). Kernfeatures: Keine Kontoführungsgebühr 
im ersten Jahr, Apple/Google Pay, integriertes Haushaltsbuch in der VR-Banking-App.

Erstelle eine Produktbeschreibung mit den 3 wichtigsten Vorteilen für den Kunden.

Regeln: Maximal 120 Wörter. Kein Bankjargon. Duzen statt Siezen.
Nicht „günstig" sagen (wir positionieren über Mehrwert, nicht über Preis).

Beispiel für den gewünschten Stil:
„Dein Konto, das mitdenkt. VR-MeinKonto Plus hilft dir, den Überblick zu 
behalten — mit automatischer Sparziel-Funktion und Push-Benachrichtigungen 
bei jeder Buchung."

Format: 
- Headline (max. 8 Wörter)
- Einleitungssatz (1 Satz)
- 3 Vorteile als Bullet Points (je max. 15 Wörter)
- Call-to-Action (1 Satz)
```

**Was sich verbessert:** Die KI hat jetzt ein konkretes Stilmuster UND eine genaue Struktur. Das Ergebnis ist nicht nur inhaltlich richtig — es ist formatiert wie gewünscht und klingt wie der gewünschte Ton.

> **Der Unterschied:** Von „Schreib was über unser Girokonto" (Glücksspiel) zu einem präzisen Briefing mit 6 Bausteinen (kontrolliertes Ergebnis). Stufe 4 kostet Sie 30 Sekunden mehr Tipparbeit — und spart Ihnen 3 Runden Hin-und-Her mit der KI.

---

## Schritt 4: Baustein 1 — Rolle

**Was es ist:** Sie sagen der KI, *wer* sie sein soll. Das verändert Perspektive, Wortwahl, Tiefe und Fokus der Antwort.

**Warum es funktioniert:** Erinnern Sie sich an die Attention-Gewichte aus Tutorial 01? Wenn Sie der KI sagen „Du bist Kreditanalystin", aktiviert sie andere Wissens-Bereiche als bei „Du bist Marketingexpertin". Dieselbe Frage, komplett andere Antwort.

### Gute vs. schlechte Rollen

| ❌ Schwache Rolle | ✅ Starke Rolle |
|---|---|
| „Sei hilfreich" | „Du bist Kundenberaterin für Privatkunden bei der Volksbank Hellweg" |
| „Du bist schlau" | „Du bist erfahrene Compliance-Beauftragte mit Schwerpunkt Geldwäscheprävention" |
| „Sei ein Experte" | „Du bist Kreditanalystin mit 10 Jahren Erfahrung in der Baufinanzierung für Privatkunden" |

**Was eine gute Rolle ausmacht:**
- **Spezifisch:** Nicht „Experte", sondern *welcher* Experte
- **Kontextreich:** Branche, Erfahrung, Schwerpunkt
- **Relevant:** Die Rolle muss zur Aufgabe passen

### Rollen verändern alles

Derselbe Prompt — drei verschiedene Rollen:

**Frage:** „Wie sollte die Volksbank Hellweg auf eine Kundenbeschwerde über zu lange Wartezeiten reagieren?"

**Rolle: Kundenberaterin**
→ Fokus auf Empathie, sofortige Lösung, persönliche Ansprache, Wiedergutmachung

**Rolle: Filialleitung**
→ Fokus auf Prozessoptimierung, Personalplanung, Wartezeiten-Tracking, langfristige Maßnahmen

**Rolle: Beschwerdemanagerin**
→ Fokus auf dokumentierte Antwort, Eskalationsstufen, BaFin-konforme Beschwerdebearbeitung, Follow-up

> **Volksbank-Analogie:** Die Rolle ist wie die Abteilung, der Sie einen internen Auftrag geben. Fragen Sie die Marketingabteilung nach einer Kundenbeschwerde, bekommen Sie eine Kampagne. Fragen Sie die Rechtsabteilung, bekommen Sie eine Stellungnahme. Fragen Sie den Vorstand, bekommen Sie eine Strategie. Dieselbe Frage — komplett andere Antwort, weil die Perspektive eine andere ist.

### Häufiger Fehler: Rolle ohne Aufgabe

Eine Rolle allein macht keinen guten Prompt. „Du bist Kreditanalystin" und dann nichts weiter? Das ist, als würden Sie eine Kollegin ins Büro rufen und dann schweigen. Die Rolle setzt den Rahmen — die Aufgabe füllt ihn.

---

## Schritt 5: Baustein 2 — Kontext

**Was es ist:** Sie geben der KI die Hintergrundinformationen, die sie braucht, um Ihre Aufgabe richtig zu verstehen. Daten, Situationen, Zielgruppen, Rahmenbedingungen.

**Warum es funktioniert:** Ein LLM hat keine Ahnung von Ihrer konkreten Situation. Es kennt die Volksbank Hellweg nicht, weiß nicht, was letzte Woche im Teammeeting besprochen wurde, und kennt Ihre Kunden nicht. Alles, was es nicht weiß, muss es raten — oder es halluziniert (erfindet plausibel klingende, aber falsche Informationen).

### Die 3 Stufen der Kontexttiefe

**Stufe 1: Kein Kontext**
```
Schreib eine E-Mail an einen Kunden.
```
→ Die KI rät: Welcher Kunde? Welches Thema? Welcher Anlass? Das Ergebnis ist generisch und nutzlos.

**Stufe 2: Etwas Kontext**
```
Schreib eine E-Mail an einen Kunden über die Änderung seiner Kontoführungsgebühren.
```
→ Besser: Das Thema ist klar. Aber: Welche Änderung? Wie viel? Ab wann? Welcher Ton?

**Stufe 3: Voller Kontext**
```
Schreib eine E-Mail an Herrn Meier (Privatkunde seit 15 Jahren, VR-MeinKonto). 
Seine Kontoführungsgebühr steigt ab 01.04.2026 von 3,90€ auf 4,90€/Monat. 
Grund: Erweiterung der Banking-App um Haushaltsbuch-Funktion. 
Ton: wertschätzend, transparent, nicht entschuldigend.
Erwähne die neuen Features als Mehrwert.
```
→ Jetzt hat die KI alles, was sie braucht. Das Ergebnis ist maßgeschneidert.

> **Volksbank-Analogie:** Kontext ist die Kundenakte. Würden Sie einen Beratungstermin führen, ohne vorher die Akte gelesen zu haben? Ohne zu wissen, ob der Kunde seit 2 Monaten oder seit 20 Jahren bei Ihnen ist? Ob er ein Depot hat oder nur ein Girokonto? Je mehr Sie wissen, desto besser können Sie beraten. Genauso bei der KI.

### Daten einbetten: Copy-Paste ist Ihr Freund

Einer der mächtigsten Tricks: **Kopieren Sie relevante Informationen direkt in den Prompt.** Die KI kann nur das verwenden, was Sie ihr geben.

```
Hier ist die Tagesordnung unseres letzten Teammeetings:

---
1. Quartalsabschluss Q4/2025 — Zielerreichung 94%
2. Neue Vertriebsziele Q1/2026
3. Personalplanung: 2 neue Auszubildende ab September
4. Digitalisierung: VR-Banking-App Update auf Version 3.2
---

Erstelle aus dieser Tagesordnung ein Protokoll mit den wichtigsten 
Diskussionspunkten und offenen Action Items.
```

Die Trennzeichen (`---`) helfen der KI zu verstehen, wo Ihre Daten anfangen und aufhören. Sie können auch Überschriften, Absätze oder Aufzählungszeichen verwenden — Hauptsache, die Struktur ist klar.

> **Tipp:** Für fortgeschrittene Nutzer gibt es auch formale Trennzeichen wie XML-Tags (`<daten>...</daten>`), die besonders bei langen Prompts mit vielen Datenquellen helfen. Mehr dazu in Tutorial 01-02.

---

## Schritt 6: Baustein 3 & 4 — Aufgabe und Regeln

### Die Aufgabe: Was genau soll die KI tun?

Eine gute Aufgabe hat drei Teile: **ein Verb**, **ein Objekt** und **ein Ergebnis**.

| ❌ Vage Aufgabe | ✅ Präzise Aufgabe |
|---|---|
| „Hilf mir bei einer Analyse" | „Analysiere die 5 häufigsten Beschwerdegründe und erstelle eine Rangliste" |
| „Schreib was über Altersvorsorge" | „Erkläre die 3 Säulen der Altersvorsorge in je 2 Sätzen" |
| „Mach einen Plan" | „Erstelle einen 4-Wochen-Einarbeitungsplan für neue Auszubildende in der Privatkundenberatung" |

**Die Formel:** *[Verb] + [Was genau] + [Wie viel / Wie genau]*

- „**Erstelle** [eine Checkliste] [mit 10 Punkten für die Kontoeröffnung]"
- „**Vergleiche** [Bausparvertrag und Annuitätendarlehen] [anhand von 5 Kriterien in einer Tabelle]"
- „**Formuliere** [eine Absage an einen Kreditantrag] [wertschätzend, maximal 100 Wörter]"

### Die Regeln: Welche Leitplanken gelten?

Regeln sagen der KI, was sie **nicht** tun soll, und wie das Ergebnis beschaffen sein muss. Sie sind die Compliance-Richtlinien Ihres Prompts.

**Typische Regeln:**

| Art | Beispiel |
|---|---|
| **Länge** | „Maximal 200 Wörter" / „Genau 5 Stichpunkte" |
| **Sprache/Ton** | „Einfache Sprache, kein Fachjargon" / „Formell, Siezen" |
| **Verbote** | „Nenne keine konkreten Zinssätze" / „Keine Rechtsberatung" |
| **Zielgruppe** | „Für Kunden ohne Finanzvorwissen" / „Für interne Nutzung" |
| **Stil** | „Positiv formulieren, keine Verneinungen" / „Sachlich, nicht werblich" |

> **Volksbank-Analogie:** Aufgabe und Regeln sind wie ein interner Arbeitsauftrag mit Compliance-Vermerk. Die Aufgabe sagt: „Bitte erstellen Sie ein Kundenanschreiben zur Gebührenerhöhung." Die Regeln sagen: „Bitte beachten Sie die Corporate-Language-Richtlinie, maximal eine DIN-A4-Seite, keine Vergleiche mit Mitbewerbern, Freigabe durch Vertriebsleitung vor Versand."

### Die 3 häufigsten Fehler bei Aufgabe & Regeln

**1. Zu vage:** „Hilf mir bei einer Analyse" → *Welche* Analyse? *Wovon*? *Für wen*?

**2. Widersprüchlich:** „Sei kreativ und überraschend, aber halte dich exakt an unsere Vorlage" → Die KI kann nicht beides gleichzeitig. Entscheiden Sie: Soll sie sich an ein Muster halten oder frei gestalten?

**3. Zu viele Aufgaben gleichzeitig:** „Analysiere unsere Kundenbeschwerden, schreib ein Konzept zur Verbesserung, erstelle eine Präsentation für den Vorstand und formuliere eine Pressemitteilung" → Vier Aufgaben in einem Prompt. Besser: Eine Aufgabe pro Prompt, oder klar nummerieren und trennen.

---

## Schritt 7: Baustein 5 — Beispiele

**Was es ist:** Sie zeigen der KI, wie das Ergebnis aussehen soll — nicht durch Beschreibung, sondern durch ein konkretes Muster.

**Warum es so mächtig ist:** Ein Beispiel sagt mehr als hundert Regeln. Anthropic, die Macher von Claude, formulieren es so: „Es ist oft effizienter, der KI ein oder zwei Beispiele zu zeigen, als alle Nuancen mit Text zu beschreiben." Das gilt für alle Modelle.

### Wann Beispiele Pflicht sind

- **Konsistentes Format:** Sie brauchen jede Woche denselben Newsletter-Aufbau
- **Fachjargon:** Die KI soll bankenspezifische Formulierungen verwenden
- **Tonalität:** „Wertschätzend aber bestimmt" ist subjektiv — ein Beispiel macht es objektiv
- **Tabellen und Listen:** Zeigen Sie die gewünschte Struktur

### Ein Beispiel in Aktion

**Ohne Beispiel:**
```
Erstelle Kurzbeschreibungen für unsere Bankprodukte.
```

**Mit Beispiel:**
```
Erstelle Kurzbeschreibungen für unsere Bankprodukte.

Hier ein Beispiel für den gewünschten Stil und Aufbau:

Produkt: VR-MeinKonto Plus
Beschreibung: Dein Girokonto mit Extras. Kostenlose Kreditkarte, 
weltweiter Bargeldbezug, und die VR-Banking-App mit Echtzeit-Umsätzen. 
Für alle, die mehr von ihrem Konto erwarten.

Erstelle jetzt Beschreibungen im gleichen Stil für:
1. VR-MeinKonto Flex
2. VR-Tagesgeld Komfort
3. VR-Depot Starter
```

Die KI übernimmt aus dem Beispiel: Länge, Tonalität, Struktur (Produktname → Beschreibung → Zielgruppen-Schlusssatz), Wortwahl (Duzen, aktive Sprache).

### Wann Beispiele schaden können

Ein wichtiger Hinweis: KI-Modelle wie Claude folgen Beispielen **sehr genau** — manchmal zu genau. Wenn Ihr Beispiel einen bestimmten Fehler enthält oder einen sehr speziellen Stil hat, wird die KI diesen reproduzieren.

**Faustregel:**
- **1 Beispiel** = Die KI versteht den Stil
- **2-3 Beispiele** = Die KI versteht das Muster (ideal)
- **Zu viele Beispiele** = Die KI kopiert nur noch statt kreativ zu sein

> **Volksbank-Analogie:** Beispiele sind wie Mustervorlagen in der Fachabteilung. Wenn Sie einem neuen Kollegen sagen „Schreib ein Kundenanschreiben", stellt er 20 Rückfragen. Wenn Sie ihm eine Mustervorlage geben, versteht er sofort, was erwartet wird. Aber: Wenn die Mustervorlage aus 2015 stammt und noch alte Formulierungen enthält, übernimmt er die auch.

---

## Schritt 8: Baustein 6 — Format

**Was es ist:** Sie definieren, in welcher Form die KI ihre Antwort liefern soll.

**Warum es wichtig ist:** Ohne Format-Angabe entscheidet die KI selbst — und ihre Wahl passt nicht immer zu Ihrem Bedarf. Sie wollen eine Tabelle? Sie bekommen einen Fließtext. Sie brauchen Stichpunkte? Sie bekommen drei Absätze.

### Welches Format für welchen Zweck?

| Format | Wann nutzen | Prompt-Formulierung |
|---|---|---|
| **Nummerierte Liste** | Reihenfolge wichtig, Schritte, Rankings | „Erstelle eine nummerierte Liste mit..." |
| **Bullet Points** | Schnellüberblick, Aufzählung | „Liste 5 Vorteile als Stichpunkte" |
| **Tabelle** | Vergleiche, Übersichten, Planung | „Erstelle eine Tabelle mit den Spalten: X, Y, Z" |
| **E-Mail** | Kundenanschreiben, interne Kommunikation | „Formuliere eine E-Mail mit Betreff und Grußformel" |
| **Fließtext** | Berichte, Zusammenfassungen | „Schreib einen zusammenhängenden Text, 3 Absätze" |
| **Schritt-für-Schritt** | Anleitungen, Prozesse | „Erkläre Schritt für Schritt, wie..." |

### Kombination aus Inhalt und Form

Die stärksten Prompts definieren beides — **was** drin steht und **wie** es aussieht:

```
Erstelle eine Vergleichstabelle für unsere drei Girokonto-Modelle.

Spalten: Produktname | Kontoführungsgebühr | Kreditkarte inklusive | 
Besonderheiten | Empfohlen für

Zeilen: VR-MeinKonto Basis, VR-MeinKonto Flex, VR-MeinKonto Plus

Stil: Kundenfreundlich, keine internen Kürzel, Preise mit €-Zeichen
```

> **Volksbank-Analogie:** Format ist wie das Formular. Eine Kreditvoranfrage hat ein festes Format. Ein Gesprächsprotokoll hat ein anderes. Eine Kundeninfo ein drittes. Sie würden die Ergebnisse eines Beratungsgesprächs nicht in ein Überweisungsformular eintragen. Genauso sollte Ihre KI-Antwort das richtige Format haben.

---

## Schritt 9: Wenn es schiefgeht — Fehler erkennen und beheben

Selbst mit den 6 Bausteinen wird nicht jeder Prompt beim ersten Mal perfekt. Hier sind die häufigsten Probleme und wie Sie sie lösen.

### Die 5 häufigsten Prompt-Fehler

| # | Problem | Symptom | Lösung |
|---|---|---|---|
| 1 | **Zu vage** | Antwort ist generisch und oberflächlich | Kontext und Aufgabe spezifischer formulieren |
| 2 | **Zu lang und widersprüchlich** | KI ignoriert Teile oder wirkt verwirrt | Kürzen, Widersprüche entfernen, eine Aufgabe pro Prompt |
| 3 | **Keine Rolle** | Antwort klingt wie Wikipedia | Passende Expertenrolle ergänzen |
| 4 | **Kein Format** | Antwort in unbrauchbarer Form | Gewünschtes Format explizit angeben |
| 5 | **Blind vertrauen** | Halluzinationen unbemerkt übernommen | Immer prüfen, besonders bei Fakten, Zahlen, Vorschriften |

### Halluzinationen: Die unsichtbare Gefahr

Das größte Risiko bei KI ist nicht eine schlechte Antwort — die erkennen Sie sofort. Das größte Risiko sind Antworten, die **überzeugend klingen, aber falsch sind.** Das nennt man **Halluzination.**

**Ein Beispiel:** Sie fragen die KI nach den aktuellen BaFin-Vorschriften für Baufinanzierung. Die KI antwortet mit einem konkreten Paragraphen, einer Jahreszahl und einer überzeugenden Erklärung. Klingt perfekt. Nur: Den Paragraphen gibt es nicht. Die KI hat ihn erfunden — aber so formuliert, dass er plausibel klingt.

**Warum passiert das?** Erinnern Sie sich: Das LLM berechnet das wahrscheinlichste nächste Wort. Wenn es nach einem plausiblen Paragraphen „klingt", generiert die KI einen — egal ob er existiert oder nicht. Die KI lügt nicht absichtlich. Sie hat kein Konzept von „wahr" und „falsch". Sie berechnet Wahrscheinlichkeiten.

### 4 Strategien gegen Halluzinationen

Diese Techniken stammen direkt aus den Empfehlungen von Anthropic (den Machern von Claude) und funktionieren bei allen Modellen:

**1. „Sag ‚Ich weiß es nicht'" anfordern:**
```
Wenn du dir bei einer Angabe nicht sicher bist, sage explizit 
„Diese Information konnte ich nicht verifizieren" statt zu raten.
```

**2. Nur bei hoher Konfidenz antworten:**
```
Antworte nur mit Informationen, bei denen du dir sehr sicher bist. 
Kennzeichne unsichere Angaben deutlich mit [UNGEPRÜFT].
```

**3. Erst denken, dann antworten:**
```
Denk Schritt für Schritt nach, bevor du antwortest. 
Prüfe jede Aussage auf Plausibilität.
```

**4. Belege einfordern:**
```
Zitiere bei jeder Aussage die relevante Quelle oder Vorschrift. 
Wenn du keine Quelle nennen kannst, kennzeichne die Aussage als unsicher.
```

> **Volksbank-Analogie:** Halluzinationen bei KI sind wie ein Kollege, der bei einer Kundenberatung Zahlen improvisiert, weil er die aktuellen Konditionen nicht nachgeschlagen hat. Er klingt überzeugend, der Kunde vertraut ihm — aber die Zahlen stimmen nicht. Die Konsequenz? Im besten Fall Vertrauensverlust. Im schlimmsten Fall Haftung. Deshalb: **KI-Output ist immer ein Entwurf, nie ein freigegebenes Dokument.** Jede faktische Aussage — besonders zu Vorschriften, Zinssätzen, Fristen — muss geprüft werden.

---

## Schritt 10: Iterativ verbessern — der Prompt ist nie fertig

Einer der wichtigsten Perspektivwechsel: **Prompting ist kein Einmal-Schuss, sondern ein Gespräch.**

Die wenigsten Prompts sind beim ersten Mal perfekt. Und das ist völlig in Ordnung. Der Trick ist, dass Sie die KI-Antwort als Feedback nutzen und Ihren Prompt verfeinern.

### Die Verfeinerungsschleife

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Prompt       │ →   │ KI-Antwort   │ →   │ Bewertung    │
│ formulieren  │     │ lesen        │     │ Was fehlt?    │
└──────────────┘     └──────────────┘     │ Was stimmt    │
       ↑                                  │ nicht?        │
       │                                  └──────┬───────┘
       │                                         │
       └──── Prompt anpassen ◄───────────────────┘
```

### In der Praxis

**Runde 1:** Sie prompten und die Antwort ist zu lang.
→ Ergänzen Sie: „Maximal 100 Wörter."

**Runde 2:** Jetzt passt die Länge, aber der Ton ist zu förmlich.
→ Ergänzen Sie: „Freundlich und nahbar, als würdest du einem Kollegen schreiben."

**Runde 3:** Ton passt, aber ein wichtiger Punkt fehlt.
→ „Ergänze bitte noch einen Punkt zur Einlagensicherung."

**Wichtig:** Sie müssen nicht jedes Mal den ganzen Prompt neu schreiben! In ChatGPT, Claude und Gemini können Sie einfach im selben Gespräch weiterschreiben:

```
Das ist gut, aber:
- Mach es 30% kürzer
- Ersetze den dritten Punkt durch einen Hinweis zur Einlagensicherung
- Verwende aktivere Verben
```

Die KI erinnert sich an das bisherige Gespräch und baut auf Ihrer vorherigen Anfrage auf. Nutzen Sie das! Sie müssen nicht jedes Mal von vorne anfangen.

> **Volksbank-Analogie:** Denken Sie an einen Kreditausschuss. Die erste Vorlage ist selten die letzte. Es gibt Rückfragen, Überarbeitungen, Ergänzungen — und am Ende eine Freigabe. Genauso arbeiten Sie mit der KI: Erste Fassung → Feedback → Verfeinerung → Ergebnis.

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: „Vom Wunsch zum Auftrag"

**Ihre Aufgabe:** Verbessern Sie diesen vagen Prompt mit allen 6 Bausteinen.

**Ausgangsprompt:**
```
Erstelle eine Kundeninformation über unsere neuen Öffnungszeiten.
```

**Szenario:** Die Volksbank Hellweg passt ab dem 01.03.2026 die Öffnungszeiten an. Die Filiale Soest ist jetzt Mo-Fr 9:00-16:00 statt bisher Mo-Fr 8:30-17:00 geöffnet. Dafür gibt es erweiterte Servicezeiten über die VR-Banking-App und die Telefon-Hotline (Mo-Sa 7:00-22:00). Zielgruppe: Bestandskunden der Filiale Soest.

Öffnen Sie ChatGPT, Claude oder Gemini und erstellen Sie einen Prompt mit allen 6 Bausteinen. Vergleichen Sie das Ergebnis mit Ihrem ersten Versuch.

<details>
<summary>💡 Beispiel-Lösung anzeigen</summary>

```
Rolle: Du bist Kundenberaterin in der Filiale Soest der Volksbank Hellweg.

Kontext: Ab 01.03.2026 ändern sich unsere Öffnungszeiten:
- Neu: Mo-Fr 9:00-16:00 Uhr (bisher: Mo-Fr 8:30-17:00)
- Erweitert: Telefon-Hotline Mo-Sa 7:00-22:00
- Erweitert: VR-Banking-App mit 24/7-Service für Überweisungen, 
  Kontostandsabfragen und Terminvereinbarungen

Aufgabe: Erstelle ein Kundenanschreiben, das die neuen Öffnungszeiten 
kommuniziert und die erweiterten digitalen Services als Mehrwert 
hervorhebt.

Regeln: 
- Maximal 150 Wörter
- Wertschätzend und positiv formulieren (nicht „Wir schließen früher", 
  sondern „Wir erweitern unseren Service")
- Siezen
- Keine negativen Formulierungen über die verkürzten Schalterzeiten

Beispiel für den Ton:
„Liebe Kundinnen und Kunden, wir bauen unseren Service für Sie aus — 
mit noch mehr Möglichkeiten, Ihre Bankgeschäfte flexibel und bequem 
zu erledigen."

Format:
- Betreff
- Anrede
- 2 kurze Absätze
- Tabellarische Übersicht der neuen Zeiten
- Grußformel
```
</details>

---

### Hands-on 2: „Das Rollen-Experiment"

**Ihre Aufgabe:** Testen Sie, wie stark eine Rolle die Antwort verändert.

**Stellen Sie folgende Frage an ChatGPT, Claude oder Gemini — dreimal, jeweils mit einer anderen Rolle:**

**Frage:** „Ein Kunde der Volksbank Hellweg beschwert sich, dass seine Überweisung nach 3 Tagen noch nicht angekommen ist. Was sollten wir tun?"

**Rolle A:** „Du bist eine empathische Kundenberaterin."
**Rolle B:** „Du bist ein analytischer Prozess-Experte für Zahlungsverkehr."
**Rolle C:** „Du bist Beschwerdemanagerin mit juristischem Hintergrund."

Vergleichen Sie die drei Antworten: Welche Aspekte betont jede Rolle? Wo überschneiden sie sich? Welche ist für welche Situation am nützlichsten?

---

### Hands-on 3: „Die Prompt-Klinik"

**Ihre Aufgabe:** Diagnostizieren Sie das Problem bei diesen 5 kaputten Prompts und reparieren Sie sie.

**Prompt 1:** „Schreib einen Text."
<details>
<summary>💡 Diagnose</summary>

**Problem:** Kein Kontext, keine Aufgabe, kein Format — alles fehlt.
**Reparatur:** „Schreib einen informativen Text (200 Wörter) über die Vorteile des VR-Tagesgeldkontos für Bestandskunden der Volksbank Hellweg. Zielgruppe: sicherheitsorientierte Sparer ab 50."
</details>

**Prompt 2:** „Du bist der beste Finanzberater der Welt. Erstelle einen perfekten, umfassenden, detaillierten und gleichzeitig kurzen Überblick über alle Anlageprodukte."
<details>
<summary>💡 Diagnose</summary>

**Problem:** Widersprüchlich („umfassend + detailliert" vs. „kurz"), übertriebene Rolle („bester der Welt"), Aufgabe zu breit („alle Anlageprodukte").
**Reparatur:** „Du bist Anlageberaterin bei der Volksbank Hellweg. Erstelle eine Vergleichstabelle unserer 4 wichtigsten Sparprodukte (Tagesgeld, Festgeld, Sparbrief, VR-Depot) mit je 3 Stichpunkten zu Vorteilen. Maximal eine Bildschirmseite."
</details>

**Prompt 3:** „Erkläre die BaFin-Vorschriften zur Geldwäscheprävention im Bankensektor mit allen relevanten Paragraphen und aktuellen Änderungen 2026."
<details>
<summary>💡 Diagnose</summary>

**Problem:** Halluzinations-Falle! Die KI wird wahrscheinlich plausibel klingende Paragraphen erfinden. Rechtliche Detailfragen sind ein Hochrisiko-Bereich für KI.
**Reparatur:** „Gib mir einen groben Überblick über die wichtigsten Prinzipien der Geldwäscheprävention im deutschen Bankwesen. Nenne keine konkreten Paragraphen — kennzeichne unsichere Angaben mit [PRÜFEN]. Ich werde die Details anschließend mit unserer Rechtsabteilung verifizieren."
</details>

**Prompt 4:** „Schreib einen Social-Media-Post. Und dann analysiere unsere Quartalszahlen. Und dann erstelle eine Präsentation für den Vorstand. Und dann formuliere eine Pressemitteilung."
<details>
<summary>💡 Diagnose</summary>

**Problem:** Vier Aufgaben in einem Prompt. Die KI wird alles oberflächlich abhandeln statt eine Aufgabe richtig zu machen.
**Reparatur:** Eine Aufgabe pro Prompt. Starten Sie mit: „Erstelle einen LinkedIn-Post (max. 200 Zeichen) über unsere Quartalsergebnisse Q4/2025. Highlight: 94% Zielerreichung im Kreditgeschäft."
</details>

**Prompt 5:** „Schreibe eine freundliche Absage an einen Kreditantrag."
<details>
<summary>💡 Diagnose</summary>

**Problem:** Kein Kontext (welcher Kredit? Warum Absage? Welcher Kunde?), keine Regeln (rechtliche Anforderungen bei Kreditabsagen!).
**Reparatur:** „Du bist Kundenberaterin bei der Volksbank Hellweg. Formuliere eine wertschätzende Absage an einen Baufinanzierungsantrag. Grund: Eigenkapitalquote unter 10%. Ton: empathisch, aber klar. Erwähne alternative Optionen (z.B. Bausparvertrag zum Eigenkapitalaufbau). Weise darauf hin, dass der Kunde jederzeit ein erneutes Gespräch vereinbaren kann. Maximal 150 Wörter."
</details>

---

## Was diese Technologie (noch) nicht kann

So mächtig gute Prompts sind — sie haben Grenzen. Und gerade im Bankumfeld ist es entscheidend, diese zu kennen.

| Grenze | Was das bedeutet | Workaround |
|---|---|---|
| **Kein aktuelles Wissen** | Die KI kennt keine Zinssätze von heute, keine aktuellen BaFin-Rundschreiben, keine internen Volksbank-Richtlinien | Aktuelle Daten immer per Copy-Paste im Kontext mitgeben |
| **Kein „Verstehen" von Wahrheit** | Die KI berechnet Wahrscheinlichkeiten, nicht Fakten. Sie kann Falsches überzeugend formulieren | Anti-Halluzinations-Strategien nutzen (Schritt 9), Ergebnisse immer prüfen |
| **Kein Zugang zu internen Systemen** | Die KI kennt weder Ihr CRM noch Ihre Kundendaten noch Ihre internen Prozesse | Relevante Infos explizit im Prompt bereitstellen |
| **Keine Rechtsberatung** | KI kann bei regulatorischen Texten (BaFin, MaRisk, KWG) halluzinieren | KI für Entwürfe nutzen, Rechtsabteilung für Freigabe |
| **Kontextfenster begrenzt** | Sehr lange Prompts (>50.000 Wörter) können die Qualität mindern (vgl. Tutorial 00-01) | Fokussierte Prompts schreiben, lange Dokumente vorher zusammenfassen |
| **DSGVO & Datenschutz** | Kundendaten gehören nicht in öffentliche KI-Tools wie ChatGPT oder Claude | Anonymisieren oder interne KI-Lösungen nutzen |

> **Besonders wichtig:** Ein perfekter Prompt macht die KI nicht allwissend. Er macht sie nur zum bestmöglichen Assistenten *innerhalb ihrer Fähigkeiten*. Denken Sie an die KI wie an einen brillanten Praktikanten: schnell, kreativ, belesen — aber noch nicht berechtigt, Dokumente zu unterschreiben.

---

## Was es kostet — und was es spart

| Aufgabe | Ohne KI | Mit KI + gutem Prompt | Ersparnis |
|---|---|---|---|
| Kunden-E-Mail formulieren | 15-20 Min | 2-3 Min + Prüfung | ~80% Zeit |
| Produktvergleichs-Tabelle erstellen | 45-60 Min | 5-10 Min + Anpassung | ~85% Zeit |
| Meeting-Protokoll aus Notizen | 30-45 Min | 5-10 Min + Review | ~75% Zeit |
| Social-Media-Post entwerfen | 20-30 Min | 3-5 Min + Feinschliff | ~80% Zeit |
| Einarbeitungsplan für Azubi | 2-3 Std | 15-20 Min + Anpassung | ~85% Zeit |
| **Kosten pro Prompt (API)** | — | **~0,01-0,10€** | — |
| **Kosten ChatGPT/Claude Pro** | — | **~20€/Monat** | — |

> **Hinweis:** Die Zeitersparnis setzt gute Prompts voraus. Mit vagen Prompts verbringen Sie mehr Zeit mit Nachbesserungen als Sie sparen. Investieren Sie die 30 Sekunden für einen strukturierten Prompt — sie zahlen sich bei jeder Nutzung aus.

---

## Der Prompt-Prozess auf einen Blick

```
┌──────────┐    ┌──────────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
│  BEDARF  │    │   PROMPT     │    │   KI     │    │ PRÜFUNG  │    │ ERGEBNIS │
│ erkennen │ →  │   bauen      │ →  │generiert │ →  │ durch    │ →  │ nutzen   │
│          │    │  (6 Bausteine)│    │          │    │ Mensch   │    │          │
└──────────┘    └──────────────┘    └──────────┘    └──────────┘    └──────────┘
                       ↑                                  │
                       └───────── verfeinern ◄────────────┘
```

**Schritt 1: Bedarf erkennen** — Was brauche ich? Ein Text? Eine Analyse? Eine Idee?
**Schritt 2: Prompt bauen** — Die 6 Bausteine durchgehen: Rolle, Kontext, Aufgabe, Regeln, Beispiele, Format
**Schritt 3: KI generiert** — Prompt absenden, Ergebnis abwarten
**Schritt 4: Prüfen** — Stimmt der Inhalt? Passt der Ton? Sind Fakten korrekt? Besonders bei Zahlen, Vorschriften und Kundendaten!
**Schritt 5: Ergebnis nutzen** — Oder zurück zu Schritt 2 und verfeinern

---

## Das Wichtigste auf einen Blick

| Baustein | Was er tut | Merksatz |
|---|---|---|
| **1. Rolle** | Definiert die Perspektive | „Wer spricht?" |
| **2. Kontext** | Liefert Hintergrundinformationen | „Was muss die KI wissen?" |
| **3. Aufgabe** | Beschreibt die konkrete Aktion | „Was genau soll entstehen?" |
| **4. Regeln** | Setzt Leitplanken und Grenzen | „Was darf sie NICHT?" |
| **5. Beispiele** | Zeigt das gewünschte Ergebnis | „Zeigen statt beschreiben" |
| **6. Format** | Bestimmt die Form der Antwort | „Wie soll es aussehen?" |

**Die 3 goldenen Regeln:**

1. **Präzision > Länge** — Ein kurzer, präziser Prompt schlägt einen langen, vagen
2. **Zeigen > Beschreiben** — Ein Beispiel sagt mehr als hundert Regeln
3. **Iterieren > Perfektionieren** — Der erste Prompt muss nicht perfekt sein, aber der dritte sollte es

---

## Parallelen zu vorherigen Tutorials

| Konzept in diesem Tutorial | Woher Sie es kennen |
|---|---|
| „KI berechnet das wahrscheinlichste nächste Token" | Tutorial 00-01: Wie LLMs funktionieren |
| Attention-Gewichte verschieben sich je nach Kontext | Tutorial 00-01: Attention-Mechanismus |
| Kontextfenster begrenzt die Prompt-Länge | Tutorial 00-01: Token-Kosten und Context Window |
| Halluzinationen sind Wahrscheinlichkeits-Artefakte | Tutorial 00-01: Temperatur und Sampling |
| Multimodale Prompts (Bild + Text) | Tutorial 00-03: Multimodale Modelle |
| KI kann Werkzeuge nutzen wenn angebunden | Tutorial 00-07: MCP und A2A |

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **Prompt** | Ihre Anweisung an die KI — alles, was Sie in das Eingabefeld tippen |
| **Halluzination** | Eine KI-Antwort, die plausibel klingt, aber faktisch falsch ist |
| **Kontext** | Hintergrundinformationen, die Sie der KI mitgeben, damit sie Ihre Situation versteht |
| **Rolle (Persona)** | Eine Identität, die Sie der KI zuweisen, um ihre Perspektive zu steuern |
| **Few-Shot-Prompting** | Eine Technik, bei der Sie der KI 1-5 Beispiele geben, um das gewünschte Muster zu zeigen |
| **Zero-Shot-Prompting** | Ein Prompt ohne Beispiele — die KI muss allein aus der Anweisung verstehen, was gemeint ist |
| **Iteratives Prompting** | Der Prozess, einen Prompt schrittweise zu verbessern, basierend auf den KI-Antworten |
| **Delimiter** | Trennzeichen (z.B. `---`, Überschriften, XML-Tags), die verschiedene Teile eines Prompts voneinander abgrenzen |
| **Token** | Die kleinste Einheit, in der KI Text verarbeitet (ca. ¾ eines deutschen Wortes, vgl. Tutorial 00-01) |
| **Kontextfenster** | Die maximale Menge an Text, die ein KI-Modell gleichzeitig verarbeiten kann (vgl. Tutorial 00-01) |
| **Chain-of-Thought** | Eine Technik, die KI Schritt für Schritt denken zu lassen — vertieft in Tutorial 01-02 |

---



