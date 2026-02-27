# Grundlagen der Bilderstellung mit KI

**Die aktuelle Landschaft der Bildgenerierung verstehen — Modelle, Unterschiede und worauf es beim Prompting ankommt**

---

## Warum dieses Tutorial?

In Tutorial 00-02 haben Sie gelernt, *wie* Diffusion-Modelle grundsätzlich funktionieren — der Kunstrestaurator, der aus Rauschen Bilder entstehen lässt. Jetzt geht es um die Praxis: **Welche Modelle gibt es heute, was können sie, und wie sprechen Sie mit ihnen?**

Die KI-Bildgenerierung hat sich seit 2022 dramatisch weiterentwickelt. Was damals mit DALL·E 2 und den ersten Stable-Diffusion-Versionen begann, ist 2025/2026 ein reifes Ökosystem aus spezialisierten Tools — jedes mit eigenen Stärken, eigenem Prompting-Stil und eigenen Einsatzgebieten.

Und genau hier liegt die Herausforderung: **Ein Prompt, der bei Midjourney ein Meisterwerk erzeugt, kann bei DALL·E ein mittelmäßiges Ergebnis liefern — und umgekehrt.** Die Modelle „denken" unterschiedlich, und wer das versteht, spart Stunden an Trial-and-Error.

**Was Sie nach diesem Tutorial wissen werden:**

- Welche zwei grundlegend verschiedenen Ansätze zur Bildgenerierung es gibt
- Was die sechs wichtigsten Modelle ausmacht und wo ihre Stärken liegen
- Wie ein Bild-Prompt grundsätzlich aufgebaut ist — das universelle Framework
- Wie Sie mit Referenzbildern arbeiten (Image-to-Image)
- Wie Sie Ergebnisse systematisch verfeinern (die Feedback-Formel)
- Was die typischen Anfängerfehler sind und wie Sie sie vermeiden
- Welches Modell Sie für welchen Anwendungsfall wählen sollten

---

## Ein kurzer Blick zurück: Wie wir hierher gekommen sind

Die KI-Bildgenerierung hat in nur vier Jahren eine atemberaubende Entwicklung durchgemacht:

| Jahr | Meilenstein | Was sich änderte |
|------|-----------|-----------------|
| **2022** | **DALL·E 2, Stable Diffusion, Midjourney v1** | Der Durchbruch — plötzlich konnte jeder KI-Bilder erstellen |
| **2023** | **Midjourney v5, DALL·E 3 in ChatGPT** | Bildqualität explodierte. Erstmals konversationelle Bilderstellung |
| **2024** | **FLUX.1, Ideogram 2.0, Stable Diffusion 3** | Spezialisierung: Text im Bild, Fotorealismus, Open Source |
| **2025** | **GPT-4o Image (nativ), Midjourney v7, Gemini 2.5 Flash Image** | Bildgenerierung direkt in Sprachmodelle integriert. Video-Generierung startet |
| **2025/26** | **Gemini 3 Pro Image (Nano Banana Pro), FLUX.2 [max], Ideogram 3.0** | Charakterkonsistenz, 90% Textgenauigkeit, Kamera-Simulation, professionelle Workflows |

**Die Geschwindigkeit ist das Bemerkenswerte:** Was 2022 wie Science Fiction aussah (ein Bild aus Text erzeugen), ist 2026 ein Standardwerkzeug — so alltäglich wie eine Google-Suche. Und die Entwicklung beschleunigt sich weiter.

> **Volksbank-Analogie:** Erinnern Sie sich an die Einführung des Online-Bankings? 2000 war es Neuland, 2010 Standard, 2020 Pflicht. KI-Bildgenerierung durchläuft denselben Zyklus — nur 10× schneller.

---

## Zwei Welten der Bildgenerierung

Bevor wir in die einzelnen Modelle eintauchen, müssen Sie eine fundamentale Unterscheidung verstehen. In der KI-Bildgenerierung 2025/2026 gibt es zwei grundlegend verschiedene Architekturen:

### Architektur 1: Spezialisierte Bildmodelle (Diffusion)

Diese Modelle sind **ausschließlich für Bildgenerierung gebaut**. Sie nehmen Text als Input und erzeugen ein Bild — sonst nichts. Sie können nicht chatten, keine Fragen beantworten, keine Texte analysieren.

**Funktionsprinzip:** Ein Text-Encoder wandelt Ihren Prompt in eine mathematische Repräsentation um — eine Art „Übersetzung" Ihrer Worte in Zahlen, die das Bildmodell versteht. Ein Diffusion-Netzwerk erzeugt daraus schrittweise ein Bild — wie der Kunstrestaurator aus Tutorial 00-02. (Die technischen Details dazu finden Sie in Tutorial 00-02.)

**Beispiele:** Midjourney, Stable Diffusion, FLUX, Ideogram, Adobe Firefly

**Prompt-Charakter:** Beschreibend, deklarativ. Sie beschreiben das Bild, das Sie sehen wollen — wie eine Bestellung beim Fotografen.

> **Volksbank-Analogie:** Stellen Sie sich einen hochspezialisierten Grafiker vor, der ausschließlich Drucksachen gestaltet. Sie geben ihm ein Briefing, er liefert ein Design. Sie können mit ihm nicht über die Quartalszahlen diskutieren — aber bei seinem Fachgebiet ist er unschlagbar.

### Architektur 2: Multimodale Sprachmodelle mit Bildgenerierung

Diese Modelle sind **universelle KI-Systeme**, die unter anderem auch Bilder erzeugen können. Sie verstehen Kontext, führen Gespräche, können Bilder analysieren UND erstellen.

**Funktionsprinzip:** Das Sprachmodell versteht Ihre Anfrage im Kontext eines Gesprächs. Es nutzt entweder ein integriertes oder angebundenes Bildmodell, um die Ausgabe zu erzeugen. Der entscheidende Unterschied: Das Modell **versteht, was Sie meinen** — nicht nur, was Sie schreiben.

**Beispiele:** ChatGPT (GPT-4o / GPT Image), Google Gemini (Nano Banana / Gemini 3 Pro Image), Claude (mit Bilderkennung, noch keine Bildgenerierung)

**Prompt-Charakter:** Konversationell, kontextbasiert. Sie können das Modell bitten: „Mach das Bild von eben nochmal, aber mit blauem Hintergrund." Es versteht den Bezug.

> **Volksbank-Analogie:** Das ist wie Ihr Universalberater in der Filiale, der zufällig auch gut zeichnen kann. Sie diskutieren mit ihm über die Baufinanzierung, und mittendrin sagt er: „Moment, ich skizziere Ihnen mal, wie das aussehen könnte." Er versteht den gesamten Kontext Ihres Gesprächs.

### Warum ist diese Unterscheidung wichtig?

| Aspekt | Spezialisierte Modelle | Multimodale Modelle |
|--------|----------------------|---------------------|
| **Bildqualität** | Oft höher, besonders bei Ästhetik | Schnell besser werdend, teilweise gleichauf |
| **Promptverständnis** | Literal — macht genau, was Sie schreiben | Semantisch — versteht, was Sie meinen |
| **Konversation** | Keine — jeder Prompt steht für sich | Ja — iteratives Verfeinern möglich |
| **Bearbeitung** | Meist nur über Spezialtools | Im selben Chat: „Ändere die Farbe zu Rot" |
| **Text im Bild** | Variiert stark (Ideogram und FLUX führend) | GPT-4o und Gemini sehr gut |
| **Konsistenz** | Erfordert Seed-Werte und Parameter | Erinnert sich an Charaktere im Gespräch |

---

## Die sechs wichtigsten Modelle im Überblick

### 1. Midjourney (v7) — Der Ästhet

**Was es ist:** Ein spezialisiertes Bildmodell, das über Discord oder eine eigene Web-App genutzt wird.

**Stärken:**
- Unerreichte ästhetische Qualität — Bilder sehen einfach „schön" aus
- Exzellente Fine Details: Augen, Reflexionen, kleine Hintergrundelemente
- Video-Generierung (5–21 Sekunden) seit Juni 2025
- „Draft Mode" für 10× schnellere Generierung bei halben Kosten
- Style Reference System — konsistenter Stil über Bilder hinweg

**Schwächen:**
- Textdarstellung im Bild weiterhin problematisch
- Kein konversationelles Editing — jeder Prompt steht für sich
- Discord-Interface gewöhnungsbedürftig (Web-App existiert mittlerweile)

**Prompt-Stil:** Midjourney bevorzugt **atmosphärische, poetische Prompts**. Es reagiert stark auf Stimmungsbeschreibungen, Lichtangaben und künstlerische Referenzen.

```
Prompt-Beispiel (Midjourney):

a weathered lighthouse keeper standing in morning fog,
golden hour light streaming through salt-crusted windows,
oil painting style, muted earth tones, intimate composition --ar 16:9 --v 7
```

**Besonderheit:** Midjourney nutzt **Parameter** (mit `--`), die ans Ende des Prompts gestellt werden:
- `--ar 16:9` → Seitenverhältnis
- `--v 7` → Modellversion
- `--s 250` → Stilisierung (0–1000, höher = künstlerischer)
- `--c 20` → Chaos/Variation (0–100, höher = überraschender)

**Kosten:** 10–120 $/Monat je nach Plan

> **Volksbank-Analogie:** Midjourney ist wie der Starfotograf, den Sie für den Jahresbericht engagieren. Teuer, eigenwillig, braucht ein spezielles Briefing — aber das Ergebnis hängen Sie sich an die Wand.

---

### 2. ChatGPT / GPT Image (OpenAI) — Der Allrounder

**Was es ist:** Die Bildgenerierung in ChatGPT, seit 2025 nativ im GPT-4o-Modell integriert (nicht mehr DALL·E als separates System).

**Stärken:**
- Hervorragende Prompttreue — macht, was Sie sagen
- Exzellente Textdarstellung im Bild (Überschriften, Schilder, Logos)
- Konversationelles Editing: „Mach den Hintergrund blauer"
- 4× schnellere Generierung als Vorgänger
- Bis zu 4096×4096 Pixel über die API
- Nahtlose Integration mit Textgenerierung im selben Chat

**Schwächen:**
- Ästhetisch manchmal „zu sauber" — weniger künstlerisch als Midjourney
- Stilisierung erfordert explizite Anweisungen
- Rate Limits je nach Abo-Stufe

**Prompt-Stil:** GPT Image versteht **natürliche Sprache und Konversation**. Sie können so schreiben, wie Sie mit einem Menschen sprechen würden.

```
Prompt-Beispiel (ChatGPT):

Erstelle ein professionelles Foto für unsere Firmenwebseite:
Ein modernes Büro mit Glaswänden, Blick auf eine Stadt bei
Sonnenuntergang. Auf einem Whiteboard steht "Innovation 2026".
Stil: Clean, corporate, warmes Licht. Hochformat.
```

**Besonderheit:** Sie können im Gespräch iterieren:
- „Mach die Schrift auf dem Whiteboard größer"
- „Ändere den Sonnenuntergang zu Morgengrauen"
- „Gleiche Szene, aber als Aquarell"

**Kosten:** ChatGPT Plus 20 $/Monat, Free-Tier mit Limits

> **Volksbank-Analogie:** ChatGPT ist wie der IT-affine Kollege, der nebenbei auch noch gut mit Canva umgehen kann. Er versteht, was Sie wollen, macht es schnell, und wenn's nicht passt, sagen Sie einfach: „Nee, doch lieber so."

---

### 3. Google Gemini / Nano Banana Pro — Der Kontextversteher

**Was es ist:** Googles multimodales KI-System mit integrierter Bildgenerierung. Der interne Codename „Nano Banana" ist in der Community zum geflügelten Wort geworden. Aktuell: Gemini 2.5 Flash Image und Gemini 3 Pro Image (Nano Banana Pro).

**Stärken:**
- Exzellente Charakterkonsistenz — gleicher Charakter über mehrere Bilder
- Konversationelles Editing mit echtem Verständnis
- Logik und Reasoning: „Zeige, was passieren würde, wenn die Person stolpert"
- Stil-Transfer: Vorhandenes Bild in komplett neuem Stil rendern
- Blending: Mehrere Konzepte zu einem Bild verschmelzen
- SynthID-Wasserzeichen in jedem generierten Bild

**Schwächen:**
- Stylisierung manchmal inkonsistent
- Textdarstellung im Bild noch nicht perfekt (Rechtschreibfehler möglich)
- Komplexe Bearbeitungen (Tag→Nacht, Masken-Editing) können Artefakte erzeugen
- Feine Details (kleine Gesichter) gelegentlich unscharf

**Prompt-Stil:** Gemini empfiehlt ein **6-Elemente-Framework**:

```
Prompt-Aufbau (Gemini):

1. Subjekt: Wer oder was ist im Bild?
2. Komposition: Wie ist die Aufnahme gerahmt?
3. Aktion: Was passiert?
4. Ort: Wo spielt die Szene?
5. Stil: Welche Ästhetik?
6. Bearbeitungsanweisungen: Was soll geändert werden?
```

```
Prompt-Beispiel (Gemini):

Eine detaillierte Illustration eines kleinen, leuchtenden
Pilzgeist-Charakters mit einem biolumineszenten Pilzhut,
neugierigen großen Augen und einem Körper aus gewobenen Ranken.
Stehend auf einem Felsen in einem Wald bei Mondlicht.
Stil: Kinderbuch-Illustration mit warmen Farben.
```

**Besonderheit:** Geminis Stärke liegt im **mehrstufigen kreativen Prozess**:
1. Charakter erstellen → 2. In neue Szene setzen → 3. Stil ändern → 4. Details anpassen

**Kosten:** Gemini Advanced 21,99 $/Monat, kostenloser Zugang mit Limits

> **Volksbank-Analogie:** Gemini ist wie ein Berater, der Ihr gesamtes Kundenhistorie kennt. Sie sagen „Machen Sie das wie beim letzten Mal, aber für den Mittelstands-Kunden", und er versteht sofort, was Sie meinen.

---

### 4. FLUX (Black Forest Labs) — Der Präzisionist

**Was es ist:** Ein spezialisiertes Bildmodell von Black Forest Labs (den Machern hinter Stable Diffusion). Varianten: FLUX.2 [pro], [max], [schnell], [dev].

**Stärken:**
- Höchste Prompttreue unter den spezialisierten Modellen
- Exzellente Textdarstellung — lesbare Typografie in Bildern
- Fotorealismus auf Profi-Niveau
- Kamera- und Objektiv-Simulation (z.B. „Shot on Hasselblad X2D, 80mm, f/2.8")
- Strukturiertes Prompting möglich (JSON für komplexe Szenen)
- HEX-Farbcodes werden direkt verstanden

**Schwächen:**
- Keine konversationelle Bearbeitung — reines Text-zu-Bild
- Keine Negative Prompts (anders als Stable Diffusion)
- Benötigt präzise Formulierungen — weniger „künstlerische Freiheit"

**Prompt-Stil:** FLUX nutzt das **Subject + Action + Style + Context**-Framework. Die **Reihenfolge zählt** — was zuerst kommt, bekommt mehr Gewicht.

```
Prompt-Beispiel (FLUX):

Soaking wet tiger cub taking shelter under a banana leaf
in the rainy jungle, close-up photo, shot on Sony A7IV,
natural lighting, shallow depth of field, raindrops visible
on fur, editorial wildlife photography
```

**Besonderheit:** FLUX kann Kamera-Ästhetik simulieren:

| Stil | Prompt-Zusatz |
|------|--------------|
| **Modern Digital** | „shot on Sony A7IV, clean sharp, high dynamic range" |
| **2000er Digicam** | „early digital camera, slight noise, flash photography, 2000s digicam style" |
| **80er Vintage** | „film grain, warm color cast, soft focus, 80s vintage photo" |
| **Analog Film** | „shot on Kodak Portra 400, natural grain, organic colors" |

**Empfohlene Prompt-Länge:**
- **Kurz (10–30 Wörter):** Schnelle Konzepte und Stil-Exploration
- **Mittel (30–80 Wörter):** Ideal für die meisten Projekte
- **Lang (80+ Wörter):** Komplexe Szenen mit detaillierten Spezifikationen

**Kosten:** API-basiert, verschiedene Plattformen (fal.ai, Replicate etc.)

> **Volksbank-Analogie:** FLUX ist wie der Compliance-Beauftragte, der Dokumente erstellt: Absolut präzise, folgt jeder Vorgabe exakt, aber erwarten Sie keine kreative Eigeninitiative. Was Sie schreiben, bekommen Sie — nicht mehr und nicht weniger.

---

### 5. Ideogram (3.0) — Der Typograf

**Was es ist:** Ein spezialisiertes Bildmodell, gegründet von ehemaligen Google-Brain-Forschern. Fokus auf Text im Bild.

**Stärken:**
- Beste Textdarstellung aller Modelle — 90% Genauigkeit bei Text-Rendering
- Versteht typografische Konzepte (Handschrift, 3D-Text, Graffiti, Kalligraphie)
- Stark bei Grafikdesign, Logos, Poster, Werbematerialien
- Kreative Stilkontrolle mit Tags

**Schwächen:**
- Fotorealismus nicht auf Midjourney/FLUX-Niveau
- Weniger geeignet für rein fotografische Szenen
- Kein konversationelles Editing

**Prompt-Stil:** Ideogram reagiert am besten auf **klare Designbeschreibungen** mit expliziter Textangabe.

```
Prompt-Beispiel (Ideogram):

Ein minimalistisches Buchcover mit dem Titel "Die Zukunft der Arbeit"
in eleganter Serifenschrift, darunter der Untertitel "Wie KI unsere
Büros verändert" in kleinerer Sans-Serif. Hintergrund: Abstraktes
Muster aus Schaltkreisen in Blau und Gold. Stil: Modern, clean, editorial.
```

**Kosten:** Freemium, Premium ab 8 $/Monat

> **Volksbank-Analogie:** Ideogram ist Ihre Hausdruckerei, die Flyer, Plakate und Broschüren gestaltet. Bei Text auf Bildern macht ihr keiner was vor — aber für das Foto im Geschäftsbericht engagieren Sie lieber den Fotografen.

---

### 6. Stable Diffusion (SDXL / 3.5) — Der Bastler

> **Hinweis für Einsteiger:** Dieser Abschnitt beschreibt ein technisch anspruchsvolles Tool. Sie müssen Stable Diffusion nicht kennen oder nutzen — er ist hier der Vollständigkeit halber und für technisch Interessierte. Für die meisten Aufgaben sind ChatGPT, Gemini oder Midjourney die bessere Wahl.

**Was es ist:** Ein Open-Source-Bildmodell, das lokal auf dem eigenen Computer oder über Cloud-Dienste läuft. Maximale Kontrolle, maximale Komplexität.

**Stärken:**
- **Kostenlos und Open Source** — läuft auf Ihrem eigenen Rechner
- Totale Kontrolle über jeden Parameter
- Riesiges Ökosystem an Erweiterungen (ControlNet, LoRA, Inpainting)
- Keine Content-Filter (je nach Konfiguration)
- Trainierbar auf eigene Bilder/Stile

**Schwächen:**
- Technisches Know-how erforderlich (Installation, Konfiguration)
- Braucht leistungsstarke Grafikkarte (≥ 8 GB VRAM)
- Textdarstellung im Bild schwach ohne Spezial-Erweiterungen
- Kein One-Click-Interface — erfordert Tools wie ComfyUI oder Automatic1111

**Prompt-Stil:** Stable Diffusion nutzt **Keyword-basiertes Prompting** mit Gewichtungen und Negativprompts.

```
Prompt-Beispiel (Stable Diffusion):

professional corporate headshot of a middle-aged man,
confident smile, studio lighting, shallow depth of field,
(sharp focus:1.3), (professional:1.2), business suit,
neutral gray background, 85mm lens

Negative Prompt: blurry, low quality, deformed, cartoon,
illustration, painting, watermark, text, bad anatomy
```

**Besonderheit:** Gewichtungen mit Klammern:
- `(scharf:1.3)` = 30% mehr Gewicht
- `(unscharf:0.7)` = 30% weniger Gewicht
- Negative Prompts: Was das Modell **nicht** erzeugen soll

**Kosten:** Kostenlos (eigene Hardware) oder über Cloud-Dienste

> **Volksbank-Analogie:** Stable Diffusion ist wie eine Druckmaschine, die Sie sich selbst in den Keller stellen. Sie können damit alles drucken — aber Sie müssen sie selbst bedienen, warten und kalibrieren. Wer die Technik liebt, bekommt unschlagbare Ergebnisse. Wer einfach nur einen Flyer braucht, geht besser zur Druckerei.

---

## Das universelle Prompt-Framework für Bilder

Trotz aller Unterschiede zwischen den Modellen gibt es ein **universelles Framework**, das überall funktioniert. Betrachten Sie es als Grundrezept, das Sie je nach Modell anpassen:

### Die 6 Bausteine eines Bild-Prompts

```
┌──────────────────────────────────────────────────────────┐
│                    BILD-PROMPT AUFBAU                     │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  1. SUBJEKT ──────── Wer/Was ist im Bild?                │
│     │                „Eine ältere Frau mit grauem Haar"   │
│     ▼                                                    │
│  2. AKTION ──────── Was passiert?                        │
│     │                „liest ein Buch auf einer Parkbank"  │
│     ▼                                                    │
│  3. UMGEBUNG ────── Wo spielt die Szene?                 │
│     │                „in einem herbstlichen Park,         │
│     │                 Blätter auf dem Weg"                │
│     ▼                                                    │
│  4. STIL ────────── Welche Ästhetik?                     │
│     │                „Ölgemälde im Stil der               │
│     │                 Impressionisten"                    │
│     ▼                                                    │
│  5. LICHT/STIMMUNG ─ Wie fühlt es sich an?               │
│     │                „warmes Nachmittagslicht,            │
│     │                 melancholisch, ruhig"               │
│     ▼                                                    │
│  6. TECHNIK ─────── Kamera/Komposition?                  │
│     │                „Weitwinkel, geringe Tiefenschärfe,  │
│     │                 Goldener Schnitt"                   │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Wie die Modelle das Framework interpretieren

| Baustein | Midjourney | ChatGPT/GPT Image | Gemini | FLUX |
|----------|-----------|-------------------|--------|------|
| **Subjekt** | Poetisch beschreiben | Klar und direkt | Spezifische Details | Subjekt zuerst, präzise |
| **Aktion** | Stimmung > Aktion | Explizit formulieren | Als eigenen Punkt | Nach Subjekt, knapp |
| **Umgebung** | Atmosphäre betonen | Konkret benennen | Als „Ort" definieren | Als Context am Ende |
| **Stil** | Künstler-Referenzen | Explizit: „im Stil von..." | Als eigenes Element | In der Mitte platzieren |
| **Licht** | Sehr wichtig — reagiert stark | Hilfreich, nicht zwingend | In Stimmung integrieren | Als technische Angabe |
| **Technik** | Als `--`Parameter | In natürlicher Sprache | Optional | Kamera + Objektiv explizit |

### Sprache: Deutsch oder Englisch?

Eine häufige Frage: Muss ich auf Englisch prompten?

| Modell | Deutsch? | Empfehlung |
|--------|---------|------------|
| **ChatGPT / GPT Image** | ✅ Ja, sehr gut | Deutsch funktioniert hervorragend |
| **Google Gemini** | ✅ Ja, gut | Deutsch geht, Englisch manchmal präziser |
| **Midjourney** | ⚠️ Eingeschränkt | Englisch empfohlen — Deutsch wird oft missverstanden |
| **FLUX** | ⚠️ Eingeschränkt | Englisch empfohlen für beste Ergebnisse |
| **Ideogram** | ⚠️ Eingeschränkt | Englisch empfohlen |
| **Stable Diffusion** | ❌ Kaum | Fast ausschließlich Englisch |

**Faustregel:** Bei ChatGPT und Gemini können Sie bedenkenlos **Deutsch** schreiben. Bei spezialisierten Modellen liefert **Englisch** bessere Ergebnisse. In den folgenden Beispielen zeigen wir beide Varianten.

### Praxis-Beispiel: Derselbe Wunsch, vier Prompts

**Ziel:** Ein professionelles Foto einer Bankberaterin im Kundengespräch

**Midjourney:**
```
a confident female bank advisor in her 40s, warm professional smile,
sitting across from a client in a modern glass-walled office,
documents and tablet on the desk, golden afternoon light streaming
through windows, photorealistic, editorial photography --ar 16:9 --v 7
```

**ChatGPT / GPT Image:**
```
Erstelle ein professionelles Foto für die Webseite einer Volksbank:
Eine Bankberaterin Mitte 40, freundlich und kompetent, sitzt einem
Kunden gegenüber in einem modernen Büro mit Glaswänden. Auf dem Tisch
liegen Dokumente und ein Tablet. Warmes Nachmittagslicht. Der Fokus
liegt auf der Beraterin. Stil: Editorial, wie in einem Geschäftsbericht.
Querformat 16:9.
```

**Gemini:**
```
Subjekt: Professionelle Bankberaterin, Mitte 40, im Businesskostüm.
Komposition: Medium shot, leichte Untersicht, Beraterin links im Bild.
Aktion: Im Kundengespräch, Dokumente erklärend, warmes Lächeln.
Ort: Modernes Bankbüro mit Glaswänden und Stadtblick.
Stil: Fotorealistisch, editorial, wie ein Corporate-Magazin.
Licht: Warmes goldenes Nachmittagslicht von rechts.
```

**FLUX:**
```
Professional female bank advisor in her 40s explaining documents
to a client, confident warm expression, modern glass-walled bank
office with city view, shot on Canon 5D Mark IV, 35mm f/2.0,
golden hour natural lighting from right, editorial corporate
photography, shallow depth of field focusing on advisor
```

---

## Zwei Wege zum Bild: Text-to-Image vs. Image-to-Image

Bisher haben wir nur über **Text-to-Image** gesprochen — Sie beschreiben etwas, die KI erzeugt es aus dem Nichts. Aber es gibt einen zweiten, in der Praxis oft wichtigeren Weg:

### Text-to-Image: Aus Worten ein neues Bild

```
[Ihr Prompt] ──────► [KI-Modell] ──────► [Neues Bild]
```

Sie beschreiben das Bild komplett per Text. Die KI hat **keine visuelle Vorlage** — alles entsteht aus Ihrer Beschreibung.

**Typische Anwendung:** Kreative Konzepte, Illustrationen, Szenen die nicht existieren.

### Image-to-Image: Ein vorhandenes Bild als Ausgangspunkt

```
[Ihr Foto] + [Ihr Prompt] ──────► [KI-Modell] ──────► [Neues Bild]
```

Sie laden ein **Referenzbild** hoch und beschreiben, wie die KI es **neu interpretieren, umgestalten oder ergänzen** soll. Die KI nutzt das Bild als visuelle Grundlage.

**Typische Anwendung:** Porträts in neuen Stilen, Produktfotos-Varianten, Raumgestaltung, Corporate-Bildwelten.

> **Volksbank-Analogie:** Text-to-Image ist wie eine Auftragszeichnung: „Zeichnen Sie mir eine Filiale." Image-to-Image ist wie ein Renovierungsvorschlag: „Hier ist ein Foto unserer Filiale — zeigen Sie mir, wie sie nach dem Umbau aussehen könnte."

### Welche Modelle können Image-to-Image?

| Modell | Image-to-Image | Besonderheit |
|--------|---------------|--------------|
| **ChatGPT / GPT Image** | ✅ | Bild im Chat hochladen, dann per Konversation bearbeiten |
| **Google Gemini / Nano Banana** | ✅ | Starke Identitätserhaltung, Stil-Transfer, Blending |
| **Midjourney** | ✅ | Über Bild-URL als Referenz, Style Reference |
| **FLUX** | ✅ | Über API und Plattformen (fal.ai, Replicate) |
| **Ideogram** | ✅ | Gut für Design-Variationen |
| **Stable Diffusion** | ✅ | Stärkstes Image-to-Image mit ControlNet, Inpainting etc. |

### Der Schlüssel: Identitätserhaltung

Wenn Sie **Ihr eigenes Foto** oder das Foto einer Person als Referenz verwenden, ist eine Sache entscheidend: Die KI muss das **Gesicht und die Identität beibehalten**, während sie alles andere verändert.

**So formulieren Sie das:**

```
Identitätserhaltung im Prompt:

✅ "Keep the subject's exact facial structure, skin tone,
    and hair texture unchanged"
✅ "Maintain identical facial features from the reference image"
✅ "Use the uploaded image as identity reference — preserve
    all distinguishing features"

❌ Einfach nur ein Bild hochladen ohne Hinweis
   → Die KI verändert das Gesicht oft erheblich
```

> **Praxis-Tipp:** Google Gemini / Nano Banana ist aktuell am stärksten bei der Identitätserhaltung. ChatGPT/GPT Image kommt nah heran. Bei spezialisierten Modellen wie Midjourney brauchen Sie oft mehrere Anläufe.

---

## Das Prompt-Protokoll: Strukturierte Bilderstellung für Profis

Das universelle 6-Bausteine-Framework von oben ist ein guter Start. Für professionelle, wiederholbare Ergebnisse gehen Profis aber einen Schritt weiter: Sie nutzen ein **strukturiertes Protokoll** — eine Art Formular, das alle relevanten Aspekte abdeckt.

### Das 7-Felder-Protokoll

Dieses Protokoll eignet sich besonders für **multimodale Modelle** (ChatGPT, Gemini), die natürliche Sprache und Struktur verstehen:

```
┌──────────────────────────────────────────────────────────┐
│              BILD-PROMPT-PROTOKOLL (Profi)                │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  [Aufgabe]    Was soll die KI tun?                       │
│               „Erzeuge ein fotorealistisches 16:9-Bild"  │
│                                                          │
│  [Ziel]       Wofür wird das Bild verwendet?             │
│               „LinkedIn-Post zum Thema Digitalisierung"  │
│                                                          │
│  [Stil]       Welche Ästhetik?                           │
│               „Fotorealistisch, natürliches Licht"       │
│                                                          │
│  [Komposition] Was ist im Bild zu sehen?                 │
│               „Beraterin erklärt Tablet-App, Kunde       │
│                nickt interessiert, Filiale im Hinter-    │
│                grund mit Volksbank-Logo dezent sichtbar" │
│                                                          │
│  [Text]       Welcher Text soll im Bild erscheinen?     │
│               „Headline: ‚Zukunft gestalten.'"           │
│                                                          │
│  [Technik]    Format, Auflösung, Dateiformat?            │
│               „Format 16:9, 2048 px, PNG"                │
│                                                          │
│  [Qualität]   Barrierefreiheit, Corporate Design?        │
│               „Kontrast ≥ 4.5:1, Alt-Text erzeugen"     │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Praxis-Beispiel: Volksbank Social-Media-Bild

```
[Aufgabe]
Erzeuge ein fotorealistisches 1:1-Bild für Social Media
(Volksbank Heilbronn).

[Ziel]
Recruiting-Kampagne „Karriere bei der Volksbank" — vermittelt
Innovation und Teamgeist.

[Stil]
Fotorealistisch, natürliches Licht, authentische Atmosphäre,
Corporate-Farben Blau und Orange dezent integriert.

[Komposition]
Diverse Gruppe junger Mitarbeitender in modernem Büro,
kollaborative Arbeitssituation am großen Bildschirm,
im Hintergrund Volksbank-Branding dezent sichtbar.

[Text]
Headline: „Deine Zukunft im Banking."
CTA: „Jetzt bewerben"

[Technik]
Format 1:1, lange Kante 2048 px, PNG.

[Qualität]
Kontrast ≥ 4.5:1, Alt-Text erzeugen, keine künstlichen
Gesichter mit offensichtlichen KI-Artefakten.
```

**Warum das funktioniert:** Jedes Feld beantwortet eine spezifische Frage. Nichts wird vergessen. Das Protokoll ist wiederverwendbar — für das nächste Bild ändern Sie nur die Inhalte, nicht die Struktur.

> **Volksbank-Analogie:** Das Protokoll ist wie ein standardisiertes Auftragsformular für Ihre Hausdruckerei. Statt „Machen Sie mal was Schönes für Social Media" füllen Sie ein klares Briefing aus — und bekommen, was Sie bestellt haben.

### Das Image-to-Image-Template

Wenn Sie ein **Referenzbild** verwenden (z.B. ein Porträt-Foto für einen neuen Stil), ergänzen Sie das Protokoll um Identitätserhaltung.

**So geht's praktisch:**
- **ChatGPT:** Klicken Sie auf das 📎-Symbol im Chat, laden Sie Ihr Foto hoch, und schreiben Sie den Prompt darunter
- **Gemini:** Klicken Sie auf das Bild-Symbol, laden Sie Ihr Foto hoch, und beschreiben Sie die gewünschte Änderung
- **Midjourney:** Laden Sie das Bild in Discord hoch und verwenden Sie die Bild-URL im Prompt

```
Prompt-Template für Image-to-Image:

Ultra-realistic cinematic portrait of [Ihre Beschreibung].
The subject is [Alter, Geschlecht, Aussehen kurz] —
use the uploaded image as reference, keep exact facial
structure and identity unchanged.
Setting: [Ort oder Umgebung].
Lighting: [Lichtart, Richtung, Stimmung].
Style: [fotografischer Stil oder Kunststil].
Camera: [Brennweite, Perspektive, Framing].
Mood: [Gefühl, Atmosphäre].
Exclude: [unerwünschte Fehler wie AI-artifacts,
          extra fingers, plastic skin].
```

**Konkretes Beispiel:**

```
Ultra-realistic cinematic portrait of a bank advisor
(use uploaded photo, maintain exact face).
Sitting at a modern desk with a tablet showing financial charts.
She wears a navy blazer, white blouse, subtle pearl earrings.
Lighting: warm, directional sunlight from camera right,
soft ambient fill from left.
Style: minimalist editorial, shallow depth of field, high realism.
Camera: 85mm f/2.2, eye-level.
Mood: confident, approachable, professional.
Exclude: cartoon effects, over-smoothing, warped hands,
plastic skin texture.
```

---

## Ergebnisse verfeinern: Die Feedback-Formel

Kein Bild ist beim ersten Versuch perfekt. Profis nutzen eine **strukturierte Feedback-Formel**, um Ergebnisse systematisch zu verbessern — statt vage „mach es besser" zu sagen.

### Die Formel: Änderung → Grund → Messung

```
┌─────────────────────────────────────────────────┐
│           FEEDBACK-FORMEL FÜR BILDER            │
├─────────────────────────────────────────────────┤
│                                                 │
│  1. ÄNDERUNG ──── Was genau soll anders sein?   │
│                   „Erhöhe die Helligkeit um 15%" │
│                                                 │
│  2. GRUND ─────── Warum?                        │
│                   „Bild soll dynamischer wirken  │
│                    und besser zum Corporate      │
│                    Design passen"                │
│                                                 │
│  3. MESSUNG ───── Woran erkennen wir Erfolg?    │
│                   „Kontrast ≥ 4.5:1,            │
│                    Hauptfarbe im Bereich #0055A4"│
│                                                 │
└─────────────────────────────────────────────────┘
```

### Praxis-Beispiele

**Statt vage:**
```
❌ „Das Bild gefällt mir nicht so. Mach es besser."
❌ „Zu dunkel. Mehr Licht."
```

**Strukturiert:**
```
✅ Änderung: Erhöhe Helligkeit um 15% und verstärke den
   blauen Farbton im Hintergrund.
   Grund: Bild soll dynamischer wirken und das
   Volksbank-Branding stärker transportieren.
   Messung: Ziel-Kontrast ≥ 4.5:1; Hintergrundfarbe
   im Bereich des Corporate-Blaus.
```

```
✅ Änderung: Ersetze den unscharfen Hintergrund durch eine
   erkennbare Volksbank-Filiale.
   Grund: Kampagne soll lokalen Bezug herstellen.
   Messung: Filiale klar erkennbar, aber nicht
   dominant — Beraterin bleibt im Fokus.
```

```
✅ Änderung: Gesichtsausdruck freundlicher, leichtes
   Lächeln statt ernster Blick.
   Grund: Zielgruppe sind Berufseinsteigerinnen —
   einladend statt einschüchternd.
   Messung: Mundwinkel leicht nach oben, Augen
   freundlich, natürlich (nicht übertrieben).
```

**Warum das funktioniert:** Die KI versteht die **Absicht** hinter der Änderung und kann intelligentere Entscheidungen treffen. „Mach es heller" vs. „Mach es heller, damit die Recruiting-Anzeige einladender wirkt" erzeugt unterschiedliche Ergebnisse.

> **Volksbank-Analogie:** Das ist wie ein Revisionsbericht: Nicht „Da stimmt was nicht" (nutzlos), sondern „Zeile 47: Betrag falsch → korrekt: 12.500 € → Prüfvermerk: Kontoauszug vom 15.03." Präzises Feedback führt zu schnellen Korrekturen.

---

## Profi-Tipps für starke Ergebnisse

Bevor wir zu den häufigsten Fehlern kommen, hier die wichtigsten Profi-Tipps, die in der Praxis den Unterschied machen:

### Tipp 1: Präzise Adjektive statt vager Beschreibungen

```
❌ Vage: beautiful, nice, cool, interesting
✅ Präzise: cinematic, editorial, matte, glowing, ambient,
           textured, weathered, luminous, grainy
```

Vage Wörter geben der KI **keine visuellen Hinweise**. „Beautiful" hat für ein Bildmodell keine klare Bedeutung — „soft golden backlight with matte color grading" hingegen schon.

### Tipp 2: Kameraobjektive angeben

Die Angabe von Brennweiten und Blendenwerten macht Bilder **sofort realistischer**:

| Objektiv | Effekt | Wann verwenden |
|----------|--------|---------------|
| **24mm f/2.8** | Weitwinkel, viel Umgebung sichtbar | Räume, Landschaften, Architektur |
| **35mm f/1.8** | Leicht weit, natürliche Perspektive | Street Photography, Reportage |
| **50mm f/1.4** | Menschliches Sehfeld, universell | Porträts, Produkte, Editorial |
| **85mm f/1.8** | Porträt-Objektiv, schönes Bokeh | Gesichter, Headshots, Details |
| **135mm f/2.0** | Stark komprimiert, Hintergrund cremig | Fashion, Beauty, Stimmungsbilder |

### Tipp 3: Lichtquellen explizit benennen

```
✅ "Softbox from left, warm fill light from below"
✅ "Golden hour sunlight streaming through windows, hard shadows"
✅ "Overcast sky, diffused natural light, no harsh shadows"
✅ "Neon-lit alley, cyan and magenta color cast, reflections on wet ground"
```

### Tipp 4: Die KI als Prompt-Helfer nutzen

Wenn Sie nicht wissen, wie Sie einen Prompt formulieren sollen:

```
An ChatGPT oder Gemini:
"Hilf mir, einen Prompt für ein Volksbank-Motiv zum Thema
digitale Baufinanzierung zu schreiben. Zielgruppe: junge
Familien. Einsatz: Instagram-Post, 1:1."
```

Das Modell erstellt daraus automatisch einen strukturierten Prompt — den Sie dann als Basis verwenden und verfeinern können.

### Tipp 5: Varianten systematisch anfordern

Statt ein einzelnes Bild zu erzeugen und von vorne anzufangen:

```
Erzeuge 3 Varianten des gleichen Motivs:
1. Warme Farbstimmung, Herbst-Atmosphäre
2. Kühle, moderne Farbgebung, Business-Look
3. Schwarz-Weiß, dramatischer Kontrast
```

---

## Die 7 häufigsten Anfängerfehler

### Fehler 1: Zu vage prompten

```
❌ „Ein schönes Bild von einer Stadt"
✅ „Eine Luftaufnahme von München bei Nacht, Lichter der Altstadt
    reflektieren sich in der Isar, leichter Nebel, Langzeitbelichtung"
```

**Warum:** KI-Modelle brauchen Spezifität. „Schön" bedeutet für jedes Modell etwas anderes — und meist gar nichts.

### Fehler 2: Negative Formulierungen verwenden (außer bei Stable Diffusion)

```
❌ „Ein Hund, aber kein Pudel, ohne Hintergrund, nicht im Regen"
✅ „Ein Golden Retriever, freistehend vor weißem Hintergrund,
    sonniger Tag, Studiobeleuchtung"
```

**Warum:** Die meisten Modelle verarbeiten Negationen schlecht. Sie fokussieren auf „Pudel" und „Regen" — und erzeugen genau das. Beschreiben Sie, was Sie wollen, nicht was Sie nicht wollen.

### Fehler 3: Alles in einen Prompt packen

```
❌ „Ein Foto von einem Berg mit einem See davor und einer Hütte
    links und einem Boot auf dem See und ein Adler am Himmel und
    Wildblumen im Vordergrund und es ist Sonnenuntergang und Nebel
    und ein Regenbogen und ein Wanderer auf dem Weg"

✅ „Alpenhütte an einem Bergsee bei Sonnenuntergang. Nebel steigt
    vom Wasser auf. Ein einzelnes Ruderboot am Ufer. Warme goldene
    Lichtstimmung. Landschaftsfotografie, Weitwinkel."
```

**Warum:** Jedes Element konkurriert um Aufmerksamkeit. Weniger ist mehr — fokussieren Sie auf 3–5 Kernelemente.

### Fehler 4: Das falsche Modell für den Job

| Aufgabe | Falsche Wahl | Richtige Wahl |
|---------|-------------|---------------|
| Logo mit Text | Midjourney | Ideogram oder FLUX |
| Kunstwerk fürs Büro | Stable Diffusion (ohne Erfahrung) | Midjourney |
| Iteratives Design mit Feedback | FLUX | ChatGPT oder Gemini |
| Produktfotos-Serie, konsistenter Stil | ChatGPT | FLUX oder Midjourney mit Style Reference |
| Technische Diagramme | Midjourney | ChatGPT oder Gemini |

### Fehler 5: Seitenverhältnis vergessen

Die meisten Modelle generieren standardmäßig quadratische Bilder (1:1). Für professionelle Ergebnisse:
- **16:9** → Webseiten-Banner, Präsentationen, YouTube-Thumbnails
- **9:16** → Instagram Stories, TikTok, Smartphone-Wallpaper
- **4:3** → Klassisches Foto, Drucksachen
- **1:1** → Social-Media-Posts, Profilbilder

### Fehler 6: Keine Stilangabe

Ohne Stilangabe entscheidet das Modell — und das Ergebnis ist oft ein generischer Mix.

```
❌ „Ein Porträt einer Frau"
✅ „Ein Porträt einer Frau, Ölgemälde im Stil von Vermeer,
    weiches Seitenlicht, dunkler Hintergrund"
```

### Fehler 7: Nicht iterieren

Ein einzelner Prompt liefert selten das perfekte Ergebnis. Profis generieren **5–10 Variationen** und verfeinern dann:

```
Runde 1: Grundkonzept → „Passt die Stimmung?"
Runde 2: Stil anpassen → „Mehr Kontrast, dramatischer"
Runde 3: Details → „Schärferer Fokus auf das Gesicht"
Runde 4: Finalisieren → „Jetzt als 16:9 für die Webseite"
```

---

## Entscheidungsbaum: Welches Modell für welchen Zweck?

```
                    Was brauchen Sie?
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
     Ästhetisches    Konversa-       Technische
     Meisterwerk     tionelles       Kontrolle
          │          Arbeiten             │
          │              │                │
     ┌────┴────┐    ┌────┴────┐     ┌────┴────┐
     ▼         ▼    ▼         ▼     ▼         ▼
   Budget?   Text  ChatGPT  Gemini  Foto-   Total
     │       im     /GPT     (für   realis- frei?
     │       Bild?  Image    Konsis- mus?      │
     │         │    (für     tenz)     │       ▼
  ┌──┴──┐     ▼    schnelle           ▼    Stable
  ▼     ▼  Ideo-  Iteratio-         FLUX  Diffusion
 Ja   Nein gram   nen)
  │     │
  ▼     ▼
FLUX  Midjourney
```

---

## Hands-on Übung 1: Modell-Vergleich

**Aufgabe:** Verwenden Sie den folgenden Prompt in mindestens zwei verschiedenen Modellen und vergleichen Sie die Ergebnisse.

**Basis-Prompt:**

```
Eine gemütliche Buchhandlung an einem Regentag. Warmes Licht
aus den Fenstern. Ein Schild über der Tür mit dem Text
"Bücherwurm". Nasse Kopfsteinpflasterstraße reflektiert
die Lichter. Abendstimmung.
```

**Beobachten Sie:**
1. Wurde der Text „Bücherwurm" auf dem Schild korrekt dargestellt?
2. Wie unterscheidet sich die Stimmung zwischen den Modellen?
3. Welches Modell hat Ihrer Meinung nach die „schönere" Interpretation?
4. Welche Details hat ein Modell hinzugefügt, die Sie nicht beschrieben haben?

---

## Hands-on Übung 2: Das universelle Framework anwenden

**Aufgabe:** Wählen Sie eines der folgenden Szenarien und schreiben Sie einen Prompt nach dem 6-Bausteine-Framework:

**Szenario A:** Ein Werbebild für eine neue Filiale Ihrer Volksbank
**Szenario B:** Ein Titelbild für einen LinkedIn-Artikel über KI im Banking
**Szenario C:** Eine Illustration für eine interne Präsentation zum Thema „Digitale Transformation"

Füllen Sie aus:
1. **Subjekt:** ___
2. **Aktion:** ___
3. **Umgebung:** ___
4. **Stil:** ___
5. **Licht/Stimmung:** ___
6. **Technik:** ___

Dann: Formulieren Sie daraus einen zusammenhängenden Prompt für ein Modell Ihrer Wahl.

---

## Hands-on Übung 3: Fehler erkennen und korrigieren

**Aufgabe:** Die folgenden Prompts enthalten typische Anfängerfehler. Identifizieren Sie den Fehler und schreiben Sie eine verbesserte Version.

**Prompt A:**
```
Ein Bild ohne Menschen und ohne Autos von einem Gebäude,
das nicht alt ist und kein Hochhaus
```

**Prompt B:**
```
Ein süßer Hund mit einem Hut neben einer Katze in einem Park
mit Blumen und einem Teich und Enten und einem Regenbogen
und einer Bank und einem Eisverkäufer und Kindern die spielen
```

**Prompt C:**
```
Professionelles Foto
```

---

## Was KI-Bildgenerierung (noch) nicht kann

Bevor Sie jetzt losrennen und Ihren Fotografen kündigen — hier die ehrlichen Grenzen:

### Für Bankmitarbeiter besonders relevant

| Limitation | Auswirkung im Bankalltag | Workaround |
|-----------|------------------------|------------|
| **Gesichter realer Personen** | KI kann keine „echten" Mitarbeiterfotos erzeugen — nur fiktive Gesichter | Für Teamfotos weiterhin Fotograf nutzen. KI für Stockfoto-Ersatz und Konzeptbilder |
| **Exakter Text im Bild** | Rechtschreibfehler kommen vor, besonders bei längeren Texten | Text nachträglich in Canva/PowerPoint einfügen. Oder Ideogram/FLUX nutzen für kurze Headlines |
| **Corporate Design-Treue** | KI kennt Ihr CD nicht — Farben und Schriften weichen ab | Farben als HEX-Code im Prompt angeben. Logo nachträglich platzieren |
| **Datenschutz** | Hochgeladene Bilder werden möglicherweise zum Training verwendet | Keine Kundenfotos oder vertrauliche Dokumente hochladen. Interne KI-Richtlinie beachten |
| **Konsistenz über Materialien** | Dasselbe Motiv sieht bei jedem Generieren anders aus | Seed-Werte nutzen (wo möglich) oder Gemini-Sessions für Charakterkonsistenz |
| **Feine Details** | Hände, Finger, Schmuck, kleine Schrift — oft fehlerhaft | Kritisch prüfen vor Veröffentlichung. Bei Bedarf nachbearbeiten |
| **Rechtliches** | Urheberrecht bei KI-Bildern ist in Deutschland noch unklar | Für kommerzielle Nutzung: Adobe Firefly (IP-geschützt) oder eigene Fotos als Basis |

### Die ehrliche Einschätzung

KI-Bildgenerierung ist **hervorragend für:**
- Social-Media-Grafiken und Konzeptbilder
- Schnelle Visualisierung von Ideen
- Präsentationen und interne Kommunikation
- Mockups und Entwürfe vor dem Fotografen-Briefing

KI-Bildgenerierung ist **nicht geeignet für:**
- Offizielle Porträtfotos von Mitarbeitern
- Rechtsverbindliche Dokumente mit Bildern
- Materialien, bei denen 100% Markentreue Pflicht ist (ohne Nachbearbeitung)
- Bilder mit langen, fehlerfreien Texten

> **Volksbank-Analogie:** KI-Bilder sind wie Entwurfszeichnungen Ihres Architekten — perfekt, um eine Idee zu vermitteln. Aber den Bauantrag reichen Sie mit echten technischen Zeichnungen ein.

---

## Was kostet das? KI vs. klassische Bildproduktion

Die Frage, die Ihr Chef stellen wird:

| Szenario | Klassisch (Fotograf/Agentur) | KI-generiert | Ersparnis |
|----------|-------|-------|-----------|
| **10 Social-Media-Bilder** | 800–2.000 € (Fotograf + Bildrechte) | 0–20 € (ChatGPT Plus Abo) | 95–100% |
| **Konzeptbild für Präsentation** | 150–500 € (Stockfoto-Lizenz) | 0–1 € (einzelne Generierung) | 99% |
| **Recruiting-Kampagne (20 Motive)** | 3.000–8.000 € (Agentur) | 20–60 € (Abo + Iterationszeit) | 97–99% |
| **Geschäftsbericht-Fotos** | 2.000–5.000 € (Fotograf vor Ort) | ❌ Nicht empfohlen | — |
| **Logo-Entwürfe (Exploration)** | 500–2.000 € (Designer-Vorentwürfe) | 20–60 € (für erste Richtung) | 90–97% |

**Aber:** Die Zeiteinsparung ist oft wichtiger als die Kostenersparnis. Ein Social-Media-Bild, das in 30 Sekunden statt 3 Tagen (Briefing → Fotograf → Nachbearbeitung → Freigabe) entsteht, verändert Ihren gesamten Content-Workflow.

> **Praxis-Tipp:** Nutzen Sie KI für die **ersten 80%** (Konzepte, Entwürfe, Varianten) und investieren Sie Agenturbudget in die **letzten 20%** (Feinschliff, rechtlich saubere Materialien, echte Teamfotos).

---

## End-to-End: Von der Idee zum fertigen Bild

Hier ist der vollständige Workflow als Übersicht:

```
┌──────────────────────────────────────────────────────────────────┐
│                 VON DER IDEE ZUM FERTIGEN BILD                   │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. IDEE ──────────── Was brauche ich?                           │
│     │                 „Social-Media-Bild für Recruiting"          │
│     ▼                                                            │
│  2. MODELL-WAHL ───── Welches Tool passt?                        │
│     │                 → Entscheidungsbaum (siehe oben)            │
│     ▼                                                            │
│  3. REFERENZ? ─────── Habe ich ein Ausgangsbild?                 │
│     │                 Ja → Image-to-Image                        │
│     │                 Nein → Text-to-Image                       │
│     ▼                                                            │
│  4. PROMPT ────────── Protokoll ausfüllen (7 Felder)             │
│     │                 Oder: 6-Bausteine-Framework nutzen         │
│     ▼                                                            │
│  5. GENERIEREN ────── Erste Version erstellen                    │
│     │                 3 Varianten gleichzeitig anfordern          │
│     ▼                                                            │
│  6. BEWERTEN ──────── Passt es?                                  │
│     │                 Ja → Schritt 7                              │
│     │                 Nein → Feedback-Formel anwenden             │
│     │                        (Änderung → Grund → Messung)        │
│     │                        Zurück zu Schritt 5                  │
│     ▼                                                            │
│  7. FINALISIEREN ──── Export, Format, Alt-Text                   │
│     │                 CD-Check, Rechtsprüfung                    │
│     ▼                                                            │
│  8. VERÖFFENTLICHEN ─ Social Media, Präsentation, Print          │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## Zusammenfassung

| Was Sie gelernt haben | Kernaussage |
|-----------------------|-------------|
| **Zwei Architekturen** | Spezialisierte Bildmodelle vs. multimodale Sprachmodelle — jede mit eigenen Stärken |
| **6 Modelle** | Midjourney (Ästhetik), ChatGPT (Allrounder), Gemini (Kontext), FLUX (Präzision), Ideogram (Text), Stable Diffusion (Freiheit) |
| **Universelles Framework** | Subjekt → Aktion → Umgebung → Stil → Licht → Technik |
| **Text-to-Image vs. Image-to-Image** | Ohne Vorlage vs. mit Referenzbild — Identitätserhaltung als Schlüsselkonzept |
| **Prompt-Protokoll** | Strukturiertes 7-Felder-Formular für wiederholbare, professionelle Ergebnisse |
| **Feedback-Formel** | Änderung → Grund → Messung — systematisch verfeinern statt vage nachbessern |
| **7 Anfängerfehler** | Zu vage, negativ formulieren, überladen, falsches Modell, kein Seitenverhältnis, kein Stil, nicht iterieren |
| **Modell-Wahl** | Richtet sich nach Aufgabe — kein Modell ist universell das Beste |

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Diffusion-Modell** | KI-Architektur, die Bilder erzeugt, indem sie schrittweise Rauschen aus einem zufälligen Bild entfernt |
| **Multimodal** | Ein KI-Modell, das verschiedene Medientypen versteht und/oder erzeugt (Text, Bild, Audio, Video) |
| **Prompttreue** | Wie genau ein Modell das erzeugt, was der Prompt beschreibt (englisch: prompt adherence) |
| **Text-Rendering** | Die Fähigkeit eines Bildmodells, lesbaren Text in generierten Bildern darzustellen |
| **Seitenverhältnis** | Das Verhältnis von Breite zu Höhe eines Bildes (z.B. 16:9, 4:3, 1:1) |
| **Style Reference** | Funktion in Midjourney, die den Stil eines Referenzbildes auf neue Generierungen überträgt |
| **Negative Prompt** | Eine Beschreibung dessen, was das Modell *nicht* erzeugen soll — nur bei bestimmten Modellen (z.B. Stable Diffusion) |
| **ControlNet** | Erweiterung für Stable Diffusion, die zusätzliche Steuerung über Pose, Kanten oder Tiefe ermöglicht |
| **LoRA** | Low-Rank Adaptation — eine Methode, um Bildmodelle effizient auf bestimmte Stile oder Konzepte nachzutrainieren |
| **Seed** | Ein Zahlenwert, der den Zufallsprozess bei der Bildgenerierung steuert. Gleicher Seed + gleicher Prompt = (fast) gleiches Bild |
| **SynthID** | Googles unsichtbares Wasserzeichen-System, das KI-generierte Bilder als solche kennzeichnet |
| **Latent Space** | Der komprimierte mathematische Raum, in dem Bildmodelle intern arbeiten — nicht direkt sichtbar, aber entscheidend für die Qualität |
| **CFG-Scale** | Classifier-Free Guidance — ein Parameter, der steuert, wie streng das Modell dem Prompt folgt (höher = prompttreuer, aber weniger kreativ) |
| **Inference Steps** | Die Anzahl der Entrauschungsschritte bei der Bildgenerierung — mehr Schritte = bessere Qualität, aber langsamer |
| **Image-to-Image** | Bildgenerierung, die ein vorhandenes Bild als Ausgangspunkt nutzt und per Prompt transformiert |
| **Text-to-Image** | Bildgenerierung rein aus Textbeschreibung, ohne visuelles Referenzbild |
| **Identitätserhaltung** | Technik beim Image-to-Image, bei der Gesichtszüge und Merkmale einer Person beibehalten werden |
| **Stil-Transfer** | Übertragung eines visuellen Stils (z.B. Ölgemälde, Anime) auf ein vorhandenes Bild unter Beibehaltung des Inhalts |
| **Prompt-Protokoll** | Strukturiertes Formular mit definierten Feldern (Aufgabe, Ziel, Stil etc.) für reproduzierbare Bildgenerierung |
| **Bokeh** | Ästhetische Unschärfe im Hintergrund eines Fotos, erzeugt durch große Blendenöffnung (z.B. f/1.4) |
| **Alt-Text** | Alternativtext für Bilder, der den Inhalt für Screenreader und Barrierefreiheit beschreibt |

---


