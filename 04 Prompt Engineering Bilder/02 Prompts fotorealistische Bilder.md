# Prompting für Fotorealismus

**Die Königsdisziplin: Bilder erzeugen, die aussehen wie echte Fotos — mit dem richtigen Vokabular, den richtigen Stellschrauben und dem Denken eines Fotografen**

---

## Warum dieses Tutorial?

In Tutorial 03-01 haben Sie die **Landschaft** der KI-Bildgenerierung kennengelernt — welche Modelle es gibt, wie sie sich unterscheiden, und das universelle 6-Bausteine-Framework. Jetzt tauchen wir in die anspruchsvollste Disziplin ein: **Bilder, die nicht wie KI-Kunst, sondern wie echte Fotografien aussehen.**

Fotorealismus ist deshalb die Königsdisziplin, weil unser Gehirn Fotos sofort als „echt" oder „falsch" klassifiziert. Ein leicht surreales Gemälde akzeptieren wir — aber ein Porträt mit plastischer Haut, falschen Reflexionen oder unnatürlichem Licht enttarnen wir in Millisekunden. Die KI muss hier nicht nur gut sein, sie muss **perfekt** sein.

Die gute Nachricht: Seit 2025 können alle führenden Modelle fotorealistische Ergebnisse liefern — **wenn Sie wissen, wie Sie mit ihnen sprechen.** Und genau darum geht es in diesem Tutorial.

**Was Sie nach diesem Tutorial wissen werden:**

- Warum Fotografie-Vokabular der Schlüssel zu fotorealistischen Ergebnissen ist
- Die 7 Stellschrauben, die ein KI-Bild wie ein echtes Foto aussehen lassen
- Wie Kamera-Einstellungen im Prompt funktionieren — auch ohne Fotografiekenntnisse
- Wie Sie Beleuchtung beschreiben wie ein professioneller Fotograf
- Wie Sie bestehende Fotos als Basis nutzen und die Identität einer Person bewahren
- Welche modellspezifischen Tricks für maximalen Fotorealismus sorgen
- Wie Sie einen strukturierten Prompt aufbauen — als Fließtext oder als JSON-Vorlage

---

## Ein kurzer Blick zurück: Vom „sieht irgendwie aus wie" zum „ist das echt?"

| Jahr | Meilenstein | Fotorealismus-Level |
|------|-----------|---------------------|
| **2022** | DALL·E 2, Midjourney v1 | Erkennbar KI — weiche Details, falsche Hände, traumhafte Ästhetik |
| **2023** | Midjourney v5, DALL·E 3 | Erster Wow-Effekt — aber Haut wirkt oft wie Porzellan |
| **2024** | FLUX.1, Midjourney v6 | Durchbruch bei Hauttexturen und Reflexionen — Kamera-Prompts funktionieren |
| **2025** | GPT-4o Image, Midjourney v7, Gemini 2.5 Flash Image | Fotorealismus auf Stockfoto-Niveau — Nicht-Experten erkennen KI oft nicht mehr |
| **2025/26** | Gemini 3 Pro Image (Nano Banana Pro), FLUX.2 [max] | Kamera-Simulation, Mikrotexturen (Hautporen, Stoffgewebe), 4K-Ausgabe |

**Der entscheidende Wandel:** 2022 mussten Sie KI-Bilder „schöner" machen als die Realität, damit sie überhaupt akzeptabel aussahen. 2026 müssen Sie der KI beibringen, **kontrolliert unvollkommen** zu sein — weil echte Fotos nie perfekt sind.

> **Volksbank-Analogie:** Denken Sie an den Unterschied zwischen einer gedruckten Unterschrift und einer handschriftlichen. Die gedruckte ist technisch perfekt — aber genau deshalb erkennt jeder sofort, dass sie nicht echt ist. Bei fotorealistischen KI-Bildern ist es genauso: Zu perfekt = erkennbar künstlich.

---

## Denken Sie wie ein Fotograf, nicht wie ein Maler

Das ist die wichtigste Erkenntnis dieses Tutorials — und sie ist kontraintuitiv:

**Für fotorealistische Bilder beschreiben Sie nicht das Bild. Sie beschreiben die Aufnahmesituation.**

Statt zu sagen „eine Frau mit weichem Hintergrund" sagen Sie: „Porträt mit 85mm-Objektiv bei f/1.8, geringe Schärfentiefe." Statt „warmes Licht" sagen Sie: „Golden-Hour-Beleuchtung, Gegenlicht von links, weiches Fill-Licht durch Reflexion."

Warum funktioniert das? Weil die KI-Modelle mit **Millionen von Fotos** trainiert wurden, deren Metadaten Kamera-Einstellungen enthalten. Das Modell hat gelernt: „Wenn ein Foto mit 85mm bei f/1.8 aufgenommen wurde, sieht es SO aus." Es simuliert nicht die Optik — es **reproduziert das Muster**, das es mit diesen Begriffen assoziiert.

> **Volksbank-Analogie:** Wenn Sie einem erfahrenen Filialleiter sagen „bereite ein Beratungsgespräch für einen wohlhabenden Kunden vor", weiß er sofort: ruhiger Raum, nicht der Schalterplatz. Kaffee, nicht Automaten-Wasser. Anzug, nicht Polo. Sie beschreiben nicht jedes Detail — Sie geben das **Setting**, und die Erfahrung füllt den Rest.

### Die zwei Sprachen der Bildgenerierung

| Ansatz | Prompt-Stil | Ergebnis | Wann verwenden? |
|--------|------------|----------|-----------------|
| **„Maler-Sprache"** | „Ein Mann in einem Café, warmes Licht, unscharfer Hintergrund" | Generisches, oft leicht illustrativ wirkendes Bild | Wenn Fotorealismus nicht das Ziel ist |
| **„Fotografen-Sprache"** | „Porträt eines Mannes in einem Café, Canon EOS R5, 50mm f/1.4, natürliches Fensterlicht von links, Bokeh im Hintergrund, ISO 400, leichtes Filmkorn" | Bild mit authentischen optischen Eigenschaften — wie ein echtes Foto | Wenn das Bild wie eine Aufnahme wirken soll |

---

## Die 7 Stellschrauben für Fotorealismus

Jedes fotorealistische KI-Bild lässt sich über sieben Dimensionen steuern. Betrachten Sie diese als Ihr „Fotografen-Cockpit":

```
┌──────────────────────────────────────────────────────────────────┐
│           DIE 7 STELLSCHRAUBEN FÜR FOTOREALISMUS                 │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. 📷 KAMERA & OBJEKTIV ──── Was „fotografiert" die Szene?      │
│     │                                                            │
│  2. 🔆 BELEUCHTUNG ────────── Wie fällt das Licht?              │
│     │                                                            │
│  3. 🎯 KOMPOSITION ─────────── Wo steht was im Bild?            │
│     │                                                            │
│  4. 👤 SUBJEKT-DETAILS ────── Wie sieht die Person/das Objekt   │
│     │                         konkret aus?                       │
│     │                                                            │
│  5. 🏞️ UMGEBUNG & SETTING ── Wo findet die Szene statt?         │
│     │                                                            │
│  6. 🎨 NACHBEARBEITUNG ───── Filmkorn, Farbtemperatur, Kontrast │
│     │                                                            │
│  7. ⛔ AUSSCHLÜSSE ──────── Was soll NICHT im Bild sein?         │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

Lassen Sie uns jede Stellschraube im Detail durchgehen.

---

## Stellschraube 1: Kamera & Objektiv

Die Angabe von Kamera- und Objektivdaten ist der **wichtigste Einzelfaktor** für Fotorealismus. Nicht, weil die KI tatsächlich eine Kamera simuliert — sondern weil sie die **visuellen Muster** reproduziert, die mit bestimmten Kameras und Objektiven assoziiert sind.

### Brennweite (mm): Was Sie sehen

Die Brennweite bestimmt, wie viel von der Szene Sie einfangen und wie „nah" das Motiv erscheint:

| Brennweite | Bildwirkung | Typischer Einsatz | Prompt-Beispiel |
|-----------|-------------|-------------------|-----------------|
| **14–24mm** | Extrem weitwinklig, dramatische Perspektive, Linien laufen zusammen | Architektur, Landschaften, „Held steht vor Skyline" | „wide-angle shot, 24mm lens" |
| **35mm** | Natürliche Perspektive, wie das menschliche Auge | Straßenfotografie, Ganzkörperporträts, Reportage | „35mm street photography" |
| **50mm** | Klassisch, keine Verzerrung, universell einsetzbar | Allround-Porträts, redaktionelle Fotografie | „50mm prime lens, natural perspective" |
| **85mm** | Schmeichelhaft für Gesichter, schönes Bokeh | Porträtfotografie, Beauty-Aufnahmen | „85mm portrait lens, f/1.8" |
| **135mm+** | Komprimierte Perspektive, starke Hintergrundunschärfe | Fashion, Sport, Detailaufnahmen | „135mm telephoto, compressed perspective" |

> **Volksbank-Analogie:** Die Brennweite ist wie der Zoom Ihres Beratungsgesprächs. 24mm = Sie sehen die ganze Filiale im Überblick (Strategie-Meeting). 85mm = Sie fokussieren auf ein einzelnes Gesicht (persönliches Gespräch). 135mm = Sie betrachten nur das Kleingedruckte eines Vertrags (Detail-Analyse).

### Blende (f-Wert): Scharf oder unscharf?

Die Blende steuert die **Schärfentiefe** — wie viel vom Bild scharf ist:

| f-Wert | Effekt | Prompt-Beispiel |
|--------|--------|-----------------|
| **f/1.4 – f/2.0** | Nur das Motiv scharf, cremiges Bokeh im Hintergrund | „f/1.4, extreme shallow depth of field, dreamy bokeh" |
| **f/2.8 – f/4.0** | Motiv scharf, Hintergrund leicht unscharf — professioneller Standard | „f/2.8, shallow depth of field" |
| **f/5.6 – f/8.0** | Weitgehend alles scharf — ideal für Gruppen und Architektur | „f/8, everything in focus" |
| **f/11 – f/16** | Alles knackig scharf vom Vordergrund bis zum Horizont | „f/11, deep focus, landscape photography" |

**Die goldene Regel:** Kleine Zahl = wenig scharf (Porträt-Look). Große Zahl = alles scharf (Landschafts-Look).

### Kamera-Modelle im Prompt

Die Nennung einer konkreten Kamera verstärkt den Realismus-Effekt erheblich:

| Kamera-Angabe | Assoziierter Look | Wirkung |
|--------------|-------------------|---------|
| „shot on Canon EOS R5" | Satte Farben, warme Hauttöne | Klassische Porträtästhetik |
| „shot on Sony A7R V" | Hoher Dynamikumfang, neutrale Farben | Technisch perfekte Aufnahmen |
| „shot on Nikon Z9" | Natürliche Farben, hervorragende Details | Reportage- und Sportästhetik |
| „shot on iPhone 16 Pro" | Computational Photography, HDR-Look | Authentischer Smartphone-Snapshot |
| „shot on Hasselblad X2D" | Mittelformat-Look, extreme Detailtiefe | Luxus-Editorial, High-End-Werbung |
| „shot on Fujifilm X-T5" | Film-Simulation, leicht entsättigte Farben | Vintage-modern, Street-Fotografie |
| „vintage film camera" | Filmkorn, weichere Farben, Lichtlecks | Retro-Ästhetik, Nostalgie |

> **Praxis-Tipp:** „Shot on iPhone" erzeugt einen erstaunlich authentischen Look, weil es die computational-photography-Ästhetik simuliert, die wir täglich auf Social Media sehen. Für Social-Media-Content oft besser als „shot on Canon".

### Kamera-Angaben kombiniert: Beispiel-Prompts

**Porträt-Setup (klassisch):**
```
Shot on Canon EOS R5 with 85mm lens at f/1.8, ISO 200
```

**Reportage-Setup:**
```
Shot on Nikon Z9 with 35mm lens at f/4, ISO 800, 
slight motion blur, photojournalistic style
```

**Smartphone-Authentizität:**
```
Shot on iPhone 16 Pro, natural HDR, 
no professional lighting — candid moment
```

---

## Stellschraube 2: Beleuchtung

Licht ist **das Werkzeug**, das Fotografen am meisten beschäftigt. Ein identisches Motiv sieht unter verschiedener Beleuchtung radikal anders aus — und die KI versteht dieses Konzept erstaunlich gut.

### Natürliches Licht

| Lichtsituation | Wirkung | Prompt-Formulierung |
|---------------|---------|---------------------|
| **Golden Hour** | Warmes, weiches Licht; lange Schatten; romantische Stimmung | „golden hour lighting, warm sunlight, long soft shadows" |
| **Blue Hour** | Kühles, gedämpftes Licht; melancholisch; Übergangsstimmung | „blue hour, cool ambient light, city lights beginning to glow" |
| **Mittagssonne** | Hartes, kontrastreiches Licht; starke Schatten unter der Nase | „harsh midday sun, high contrast, strong directional shadows" |
| **Bewölkter Himmel** | Weiches, diffuses Licht; gleichmäßige Ausleuchtung | „overcast sky, soft diffused natural light, no harsh shadows" |
| **Fensterlicht** | Gerichtetes, weiches Licht von einer Seite; natürlich und schmeichelhaft | „soft natural window light from the left side" |
| **Gegenlicht** | Lichtkranz um das Motiv; Haare leuchten; dramatisch | „backlit by sunlight, rim light on hair and shoulders, lens flare" |

### Studio-Beleuchtung

| Licht-Setup | Wirkung | Prompt-Formulierung |
|------------|---------|---------------------|
| **Rembrandt-Licht** | Klassisches Porträtlicht — Schlüssellicht von oben-seitlich, kleines Lichtdreieck auf der Wange | „Rembrandt lighting, key light high and to one side, triangle of light on cheek" |
| **Butterfly/Paramount** | Licht direkt von vorne-oben; symmetrischer Schatten unter der Nase | „butterfly lighting, glamorous, even illumination" |
| **Split-Licht** | Hälfte des Gesichts beleuchtet, Hälfte im Schatten; dramatisch | „split lighting, half face illuminated, dramatic shadows" |
| **Softbox-Licht** | Gleichmäßiges, weiches Studio-Licht; professioneller Look | „studio softbox lighting, even illumination, no harsh shadows" |
| **Rim-Licht** | Licht von hinten erzeugt leuchtende Kontur; trennt Motiv vom Hintergrund | „rim light separating subject from background, backlit contour" |

> **Volksbank-Analogie:** Beleuchtung ist wie der Ton in einem Kundengespräch. Golden Hour = warmherzig und einladend (Erstberatung). Rembrandt-Licht = seriös und kompetent (Finanzierungsgespräch). Split-Licht = intensiv und direkt (schwieriges Gespräch über Kontoüberziehung).

### Licht-Richtung spezifizieren

Ein häufig unterschätzter Faktor — die **Richtung** des Lichts:

```
Licht von links     → „key light from camera-left"
Licht von rechts    → „key light from camera-right"  
Licht von oben      → „overhead lighting"
Licht von unten     → „underlighting" (Horror-Effekt!)
Gegenlicht          → „backlit, contre-jour"
45° von oben-links  → „45-degree key light from upper left" (Standard-Porträt)
```

---

## Stellschraube 3: Komposition & Perspektive

### Bildausschnitt

| Ausschnitt | Beschreibung | Prompt-Formulierung |
|-----------|------------|---------------------|
| **Extreme Close-up** | Nur Augenpartie oder Mund | „extreme close-up, intimate detail shot" |
| **Close-up** | Gesicht, Kopf und Hals | „close-up portrait, head and shoulders" |
| **Medium Shot** | Oberkörper bis Hüfte | „medium shot, waist up" |
| **Full Body** | Ganzer Körper sichtbar | „full body shot, complete figure" |
| **Wide/Establishing** | Person klein in großer Umgebung | „wide establishing shot, environmental portrait" |

### Kamerawinkel

| Winkel | Wirkung | Prompt-Formulierung |
|--------|---------|---------------------|
| **Augenhöhe** | Neutral, ehrlich, gleichwertig | „eye-level shot, neutral perspective" |
| **Leichte Untersicht** | Macht das Motiv größer, mächtiger, heroisch | „low-angle shot, looking up, heroic perspective" |
| **Leichte Aufsicht** | Macht das Motiv kleiner, verletzlicher, zugänglich | „slight high-angle, looking down" |
| **Vogelperspektive** | Überblick, Kontext, Muster werden sichtbar | „bird's eye view, overhead shot" |
| **Froschperspektive** | Extrem dramatisch, monumental | „worm's eye view, extreme low angle" |

### Kompositionsregeln

| Regel | Wirkung | Prompt-Formulierung |
|-------|---------|---------------------|
| **Drittel-Regel** | Motiv auf einem der vier Schnittpunkte — dynamisch und professionell | „rule of thirds composition, subject off-center" |
| **Zentriert** | Motiv genau in der Mitte — kraftvoll und symmetrisch | „centered composition, symmetrical framing" |
| **Negativraum** | Viel leere Fläche um das Motiv — modern und elegant | „negative space, minimalist composition" |
| **Führungslinien** | Linien im Bild führen zum Motiv — Tiefe und Dynamik | „leading lines drawing the eye toward the subject" |

---

## Stellschraube 4: Subjekt-Details

Fotorealismus steht und fällt mit den **Details der abgebildeten Person oder des Objekts**. Hier unterscheidet sich ein durchschnittlicher Prompt von einem exzellenten.

### Personen beschreiben: Die Detailpyramide

```
┌────────────────────────────────────────────────────────┐
│               DETAILPYRAMIDE: PERSONEN                  │
├────────────────────────────────────────────────────────┤
│                                                        │
│  Ebene 1: GRUNDLAGE (Pflicht)                          │
│  → Geschlecht, ungefähres Alter, Körperbau             │
│  „confident woman in her early 40s"                    │
│                                                        │
│  Ebene 2: GESICHT (für Close-ups wichtig)              │
│  → Augenfarbe, Hautton, Gesichtsform, Ausdruck        │
│  „warm olive skin, hazel eyes, high cheekbones,        │
│    subtle confident smile"                             │
│                                                        │
│  Ebene 3: HAARE (immer relevant)                       │
│  → Farbe, Länge, Styling, Textur                       │
│  „shoulder-length wavy auburn hair"                    │
│                                                        │
│  Ebene 4: KLEIDUNG (kontextabhängig)                   │
│  → Spezifische Beschreibung, Farben, Materialien      │
│  „dark navy dress shirt, top buttons open,             │
│    slim-fit beige chinos, black loafers"               │
│                                                        │
│  Ebene 5: DETAILS (für Premium-Ergebnisse)             │
│  → Accessoires, Hautdetails, Imperfektionen            │
│  „visible pores, subtle freckles, natural skin grain,  │
│    minimalist silver watch, thin-frame glasses"        │
│                                                        │
└────────────────────────────────────────────────────────┘
```

### Das Geheimnis: Kontrollierte Imperfektionen

Echte Fotos zeigen **nie** perfekte Haut. Für authentischen Fotorealismus fügen Sie bewusst hinzu:

- „visible skin pores" — sichtbare Hautporen
- „natural skin texture with subtle imperfections" — natürliche Hautstruktur
- „fine lines around the eyes" — feine Fältchen
- „subsurface scattering on skin" — der leichte Lichtdurchschein, der echte Haut lebendig wirken lässt
- „stray hairs" — einzelne fliegende Haare
- „slight asymmetry in facial features" — leichte Gesichtsasymmetrie

> **Volksbank-Analogie:** Es ist wie bei einem guten Beratungsgespräch: Wenn alles zu perfekt und einstudiert klingt, wird der Kunde misstrauisch. Ein gelegentliches „Da muss ich kurz nachschauen" wirkt authentischer als lückenlose Perfektion.

### Produkte und Objekte beschreiben

Für Produktfotografie gelten ähnliche Prinzipien:

| Detail-Ebene | Prompt-Beispiel |
|-------------|-----------------|
| **Material** | „brushed steel surface with visible micro-textures" |
| **Reflexionen** | „soft reflections on glossy surface, subtle highlights" |
| **Textur** | „200-thread-count cotton weave, visible individual threads" |
| **Umgebungsinteraktion** | „soft shadow cast on marble surface, slight reflection below" |

---

## Stellschraube 5: Umgebung & Setting

Die Umgebung erzählt eine Geschichte und verankert das Bild in der Realität.

### Ebenen beschreiben (Vordergrund → Hintergrund)

Ein professioneller Fotorealismus-Prompt beschreibt die Szene in **Schichten** — genau wie ein Fotograf die Tiefe eines Bildes plant:

**Vordergrund:** Was ist direkt vor der Kamera?
```
„In the foreground, slightly out of focus, 
a glass of espresso on a marble table"
```

**Mittelgrund:** Wo steht das Hauptmotiv?
```
„In the middle ground, the subject sits 
in a modern leather armchair"
```

**Hintergrund:** Was ist weiter hinten?
```
„Background: floor-to-ceiling windows showing 
a blurred city skyline, soft bokeh"
```

> **Volksbank-Analogie:** So wie Sie eine Filiale in Zonen aufteilen (Eingangsbereich → Beratungsinseln → Büros im Hintergrund), strukturiert ein guter Fotorealismus-Prompt das Bild in Ebenen. Der Kunde im Vordergrund ist scharf, die Beraterin im Mittelgrund der Fokus, und die Filiale im Hintergrund gibt Kontext.

### Atmosphärische Details

Diese kleinen Ergänzungen machen den Unterschied zwischen „gut" und „wow":

- „atmospheric haze in the distance" — Dunst für Tiefenwirkung
- „dust particles visible in the light beam" — Staubpartikel in einem Lichtstrahl
- „rain-soaked streets reflecting neon signs" — nasse Straßen mit Reflexionen
- „steam rising from a coffee cup" — aufsteigender Dampf
- „morning dew on grass blades" — Morgentau

---

## Stellschraube 6: Nachbearbeitung & Look

Echte Fotos durchlaufen immer eine Nachbearbeitung. Diesen Look können Sie im Prompt mitbestimmen:

| Look | Prompt-Formulierung | Wirkung |
|------|---------------------|---------|
| **Filmkorn** | „fine film grain, analog photography feel" | Authentisch, organisch, weniger digital |
| **Farbpalette** | „muted color palette with warm undertones" | Gedämpfte Farben, edler Look |
| **Hoher Kontrast** | „high contrast, deep blacks, bright highlights" | Dramatisch, moody |
| **HDR** | „HDR look, expanded dynamic range" | Alle Details sichtbar, auch in Schatten und Lichtern |
| **Entsättigt** | „slightly desaturated, muted tones" | Modern, editorial, Fujifilm-Ästhetik |
| **Vignette** | „subtle vignette, darker edges" | Lenkt den Blick zur Mitte |
| **Teal & Orange** | „teal and orange color grading, cinematic" | Hollywood-Blockbuster-Look |
| **Schwarz-Weiß** | „black and white, high-contrast, dramatic" | Zeitlos, intensiv, reduziert auf das Wesentliche |

### Qualitätsmarker

Diese Begriffe signalisieren dem Modell: „Ich will Profi-Qualität":

```
4K / 8K resolution          → Maximale Detailtiefe
ultra-detailed               → Jedes Detail ausarbeiten
photorealistic textures      → Realistische Oberflächen
sharp focus on face and eyes → Knackige Schärfe am richtigen Ort
RAW photo, unprocessed       → Natürlicher, unbearbeiteter Look
editorial quality            → Magazin-taugliche Qualität
```

---

## Stellschraube 7: Ausschlüsse (Exclude)

Genauso wichtig wie das, was Sie wollen, ist das, was Sie **nicht** wollen. Verschiedene Modelle handhaben Ausschlüsse unterschiedlich:

### Modellspezifische Ausschluss-Strategien

| Modell-Typ | Strategie | Beispiel |
|-----------|-----------|---------|
| **FLUX** | Keine negativen Prompts! Stattdessen das Gegenteil beschreiben | Statt „no crowds" → „peaceful solitude". Statt „no glasses" → „clear, unobstructed eyes" |
| **Midjourney** | Parameter `--no` verwenden | `--no text, watermark, extra fingers` |
| **ChatGPT / Gemini** | Im Fließtext ausschließen | „Exclude: cartoon look, CGI appearance, over-smoothing, watermarks" |
| **Stable Diffusion** | Dedizierter Negative-Prompt-Bereich | „negative_prompt: blurry, bad anatomy, deformed hands, text, logo" |

### Die häufigsten Ausschlüsse für Fotorealismus

```
IMMER ausschließen:
→ cartoon, CGI look, illustration, painting style
→ over-smoothing, plastic skin, airbrushed
→ watermark, logo, text overlay
→ deformed hands, extra fingers, warped anatomy
→ artifacts, banding, blown highlights
→ motion blur (außer gewünscht)

OPTIONAL ausschließen:
→ lens flare (wenn nicht gewünscht)
→ vignette (wenn nicht gewünscht)
→ film grain (wenn cleaner Look gewünscht)
```

---

## Identitätserhaltung: Die Person aus einem Foto in neue Szenen setzen

Eine der mächtigsten Anwendungen der aktuellen Modellgeneration: Sie laden ein **echtes Foto** hoch und lassen die KI die Person in einem völlig neuen Setting darstellen — mit der **exakten Identität** beibehalten.

### Warum „Identity Lock" der Schlüsselbegriff ist

Wenn Sie der KI einfach nur sagen „erstelle ein Porträt mit diesem Referenzbild", wird sie die Person *ungefähr* nachbilden — aber nicht exakt. Für konsistente Ergebnisse brauchen Sie eine **explizite Anweisung**:

```
Identity Lock:
„Keep the exact facial structure, skin tone, hairstyle, 
and body identity from the uploaded photo unchanged."
```

Oder kompakter:
```
„Use uploaded face, 100% identity lock, no alteration."
```

### Der Workflow: Vom Foto zum neuen Bild

```
┌──────────────────────────────────────────────────────────────────┐
│         VON EINEM FOTO ZU NEUEN SZENEN                           │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. REFERENZ HOCHLADEN ─── Frontalansicht, gute Qualität        │
│     │                      Gleichmäßige Beleuchtung               │
│     ▼                                                            │
│  2. IDENTITÄTS-LOCK ────── „Keep exact facial structure,          │
│     │                       skin tone, hairstyle unchanged"       │
│     ▼                                                            │
│  3. NEUES SETTING ──────── Kleidung, Ort, Licht, Stimmung       │
│     │                      beschreiben                            │
│     ▼                                                            │
│  4. KAMERA-PARAMETER ───── Objektiv, Blende, Perspektive        │
│     │                                                            │
│     ▼                                                            │
│  5. AUSSCHLÜSSE ────────── „No alteration to face, no cartoon   │
│     │                       look, no over-smoothing"              │
│     ▼                                                            │
│  6. GENERIEREN & PRÜFEN ── Stimmt das Gesicht? Ist der Look     │
│                             konsistent? → Iterieren               │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Charakterkonsistenz über mehrere Bilder (360°-Sheet)

Für Kampagnen, bei denen dieselbe Person in verschiedenen Szenen auftauchen soll, ist die **360°-Referenz-Methode** am zuverlässigsten:

1. **Generieren Sie ein Referenz-Sheet:** Erstellen Sie die Person in einer einzigen Generierung aus mehreren Winkeln (frontal, Profil links, Profil rechts, von hinten)
2. **Verwenden Sie alle Winkel als Referenz:** Bei jeder weiteren Generierung laden Sie das gesamte Sheet als Input hoch
3. **Beschreiben Sie die neue Szene:** Die KI „kennt" jetzt die Person aus allen Perspektiven

**Beispiel-Prompt für das Sheet:**
```
Studio portrait of a young woman looking directly into the lens.
Neutral, sophisticated expression. Visible pores, subtle freckles,
natural skin grain. Soft directional lighting. Charcoal grey suit.
```
Dann iterativ: „Show the woman turned around", „Make her look left", „Make her look right"

> **Volksbank-Analogie:** Das ist wie das Corporate-Branding-Handbuch Ihrer Bank: Es zeigt das Logo in verschiedenen Anwendungen (auf Briefpapier, auf der Fassade, auf dem Bildschirm), damit jeder Mitarbeiter es korrekt verwenden kann. Das 360°-Sheet ist das „Branding-Handbuch" für Ihre KI-Personen.

---

## Prompt-Strukturen: Fließtext vs. JSON-Vorlage

Für den Alltag reicht ein gut strukturierter Fließtext. Für **reproduzierbare, professionelle Workflows** bietet sich eine JSON-Vorlage an.

### Variante A: Strukturierter Fließtext

Der pragmatische Weg für die meisten Anwendungsfälle:

```
Ultra-realistic cinematic vertical portrait (9:16). 

A confident professional woman in her early 40s sits 
in a modern glass-walled office. She wears a navy blue 
blazer over a white blouse, minimalist silver jewelry. 
Warm, trustworthy expression with a subtle smile.

Shot on Canon EOS R5 with 85mm lens at f/2.8. 
Soft natural window light from the left. 
Shallow depth of field, blurred city skyline 
visible through floor-to-ceiling windows.

Visible skin pores, natural skin texture, 
fine film grain, editorial quality.

Exclude: cartoon look, over-smoothing, plastic skin, 
watermark, text, logo.
```

### Variante B: JSON-Prompt-Vorlage

Für systematische, wiederholbare Ergebnisse — besonders wenn mehrere Personen oder Teams damit arbeiten:

```json
{
  "task": "text-to-image",
  "subject": {
    "who": "confident professional woman, early 40s",
    "expression": "warm, trustworthy, subtle smile",
    "skin": "natural texture, visible pores, fine lines"
  },
  "wardrobe": "navy blue blazer, white blouse, silver jewelry",
  "scene": {
    "location": "modern glass-walled office",
    "background": "blurred city skyline through windows"
  },
  "lighting": {
    "key": "soft natural window light from the left",
    "fill": "ambient bounce from white walls",
    "mood": "warm, professional"
  },
  "camera": {
    "device": "Canon EOS R5",
    "lens": "85mm prime",
    "aperture": "f/2.8",
    "aspect_ratio": "9:16",
    "depth_of_field": "shallow"
  },
  "style": "editorial, photorealistic, fine film grain",
  "exclude": [
    "cartoon, CGI look, over-smoothing",
    "watermark, logo, text",
    "plastic skin, airbrushed"
  ]
}
```

**Wichtig:** Die meisten KI-Tools verstehen JSON nicht direkt als Prompt. Die Vorlage dient als **Strukturierungshilfe** — Sie übersetzen sie in Fließtext, bevor Sie sie eingeben. ChatGPT und Gemini können JSON allerdings interpretieren und daraus selbst einen optimalen Prompt formulieren.

> **Volksbank-Analogie:** Der JSON-Prompt ist wie ein standardisiertes Kreditantragsformular: Jedes Feld hat seinen Platz, nichts wird vergessen, und verschiedene Sachbearbeiter können es gleich befüllen. Der Fließtext-Prompt ist wie das persönliche Gespräch — flexibler, aber weniger reproduzierbar.

---

## Modellspezifische Tipps für Fotorealismus

Jedes Modell hat eigene Stärken und Eigenheiten. Hier die wichtigsten modellspezifischen Optimierungen:

### Midjourney v7

- **`--style raw` ist Pflicht für Fotorealismus.** Ohne diesen Parameter fügt Midjourney automatisch eine ästhetische Stilisierung hinzu, die Bilder „künstlerischer" macht — schön, aber nicht fotorealistisch
- **Personalisierung nutzen:** V7 hat ein Personalisierungssystem. Bewerten Sie ~200 Bildpaare, damit das Modell Ihren Stil lernt
- **Natürliche Sprache:** V7 versteht Sätze besser als Keyword-Listen. Schreiben Sie „Ein Geschäftsmann steht am Fenster" statt „businessman, window, standing"
- **Wichtigstes zuerst:** V7 gewichtet den Anfang des Prompts stärker. Beginnen Sie mit dem, was am wichtigsten ist

**Beispiel:**
```
A weathered fisherman mending nets on a wooden dock at dawn. 
His hands show decades of work — calloused, tanned, strong. 
Shot on Hasselblad, 85mm, f/2.8, golden hour light from behind. 
Photojournalistic style, raw and authentic. --style raw --ar 3:2
```

### ChatGPT (GPT-4o / GPT Image 1.5)

- **Konversationell iterieren:** Der große Vorteil — Sie können sagen „Mach den Hintergrund dunkler" oder „Ändere die Jacke zu blau" ohne den gesamten Prompt zu wiederholen
- **Reasoning-Modelle für komplexe Szenen:** Verwenden Sie o3 oder o4-mini für Bilder mit vielen Elementen — die Reasoning-Engine plant die Szene besser
- **Seitenverhältnis immer angeben:** GPT-4o defaultet zu 1:1 wenn unklar
- **„Draw" oder „create" verwenden:** Diese Verben funktionieren zuverlässiger als „imagine" oder „show me"
- **Neuer Chat für neue Bilder:** Das Modell „erinnert" sich an vorherige Generierungen im selben Chat — gut für Iterationen, schlecht wenn Sie etwas komplett Neues wollen

### Google Gemini (Nano Banana / Nano Banana Pro)

- **Nano Banana (Flash)** = Schnelle Bearbeitungen und Style-Transfers. Pattern-Matching-basiert
- **Nano Banana Pro (Gemini 3 Pro)** = Komplexe Szenen, Reasoning, Text im Bild, 4K-Ausgabe
- **Live Google Search:** Nano Banana Pro kann Echtzeitdaten einbeziehen (aktuelles Wetter, reale Orte)
- **Image Mixing:** Mehrere Referenzbilder kombinieren (Person aus Bild 1 + Kleidung aus Bild 2)
- **Semantische Bearbeitung:** „Remove the statue from the foreground" statt manuelles Maskieren
- **Für Bearbeitung:** „Keep everything else in the image exactly the same" als Sicherheitsanker

**Beispiel für Bearbeitung:**
```
Using this image, replace the office background with 
a modern co-working space with exposed brick walls. 
Keep everything else in the image exactly the same, 
preserving the original style, lighting, and composition.
```

### FLUX (1.1 Pro / 2 [max])

- **Keine negativen Prompts!** FLUX versteht keine „no"-Anweisungen. Beschreiben Sie stattdessen das Gegenteil: „peaceful solitude" statt „no crowds"
- **Natürliche Sprache:** Wie Midjourney v7 — Sätze funktionieren besser als Keywords
- **Wort-Reihenfolge zählt:** Das Wichtigste an den Anfang. FLUX gewichtet frühe Begriffe stärker
- **Kamera-Settings sehr effektiv:** FLUX reagiert hervorragend auf Brennweiten, Blenden und Kameramodelle
- **„White background" vermeiden bei FLUX [dev]:** Erzeugt unscharfe Ergebnisse. Stattdessen: „clean, light-colored backdrop"
- **Keine Prompt-Gewichtung:** (keyword)++ funktioniert bei FLUX nicht. Verwenden Sie „with emphasis on" oder „with a focus on"

**Beispiel:**
```
Professional headshot of a business executive in her 50s, 
clean white studio backdrop, studio lighting with soft boxes, 
85mm lens, f/1.4, shallow depth of field. 
Natural skin texture, confident expression, 
editorial fashion photography quality.
```

### Übersicht: Welches Modell wann?

| Aufgabe | Bestes Modell 2025/26 | Warum |
|---------|----------------------|-------|
| **Porträts mit maximaler Ästhetik** | Midjourney v7 (--style raw) | Unerreichte Gesichtsdetails, Reflexionen in Augen |
| **Schnelle Iteration, konversationell** | ChatGPT (GPT-4o) | „Mach das nochmal, aber mit roter Jacke" funktioniert |
| **Produkt-Fotografie** | FLUX 2 [max] oder Midjourney v7 | Präzise Materialwiedergabe, kontrollierbare Beleuchtung |
| **Person aus Foto in neue Szene** | Gemini (Nano Banana) oder ChatGPT | Beste Identity-Lock-Ergebnisse bei Image-to-Image |
| **Team-Kampagne mit vielen Varianten** | Gemini (Nano Banana Pro) | 360°-Sheet + Multi-Reference-Logik |
| **Social-Media-Content (authentisch)** | ChatGPT + „shot on iPhone" | Smartphone-Ästhetik, schnelle Ergebnisse |
| **Maximale technische Kontrolle** | Stable Diffusion + ControlNet | Seed-Kontrolle, LoRA-Training, volle Parameter-Freiheit |

---

## Praxis-Prompts: Vom Einfachen zum Komplexen

Lassen Sie uns jetzt die Theorie in die Praxis überführen. Hier fünf Szenarien mit steigender Komplexität — alle für den Volksbank-Kontext:

### Szenario 1: LinkedIn-Porträt (Basis)

**Ziel:** Professionelles Profilbild-Konzept für die Karriereseite

```
Photorealistic portrait of a confident woman in her mid-30s.
Navy blue blazer over white blouse. Warm, approachable smile.
Modern office background, soft and blurred.

Shot with 85mm lens at f/2.0, soft natural studio lighting.
Vertical format 9:16, shallow depth of field.
Natural skin texture, visible pores, editorial quality.

Exclude: artificial look, over-smoothing, logos, text.
```

### Szenario 2: Beratungssituation (Mittel)

**Ziel:** Authentisches Bild einer Kundenberatung für eine Broschüre

```
Ultra-realistic photograph of a banking consultation.
A male financial advisor (early 50s, grey-templed, glasses, 
dark suit) sits across from a young couple at a modern desk.

The advisor gestures toward a tablet showing charts 
(charts blurred, not legible). The couple looks engaged, 
leaning slightly forward. 

Setting: bright, modern bank office with glass partitions 
and warm wood accents. Plants visible in the background.

Shot on Sony A7R V, 35mm lens, f/4, soft overhead lighting 
combined with natural window light from the right side.
Horizontal 16:9 format.

Visible skin textures, natural expressions — not posed.
Fine film grain, warm color grading.

Exclude: stock photo look, forced smiles, CGI, logos.
```

### Szenario 3: Recruiting-Kampagne (Fortgeschritten)

**Ziel:** Diverse, authentische Porträts für eine Employer-Branding-Kampagne

**Prompt-Vorlage (für jede Person anpassbar):**
```json
{
  "task": "text-to-image",
  "subject": {
    "who": "[HIER ANPASSEN: z.B. young professional, late 20s]",
    "expression": "genuine confidence, approachable",
    "skin": "realistic texture, authentic, not airbrushed"
  },
  "wardrobe": "[HIER ANPASSEN: business casual, brand colors]",
  "scene": {
    "location": "[HIER ANPASSEN: modern office / co-working / outdoor]",
    "background": "clean, professional, slightly blurred"
  },
  "lighting": {
    "type": "soft natural light with studio fill",
    "mood": "welcoming, modern, dynamic"
  },
  "camera": {
    "lens": "85mm",
    "aperture": "f/2.8",
    "aspect_ratio": "4:5",
    "depth_of_field": "shallow"
  },
  "style": "employer branding campaign, authentic not stock-photo",
  "brand": "navy blue and white color accents where natural",
  "exclude": ["stock photo aesthetic", "forced poses", "over-smoothing"]
}
```

**In Fließtext umgewandelt (für ChatGPT oder Gemini):**
```
Create a photorealistic portrait for an employer branding campaign.
Show a young professional in her late 20s, genuine confidence 
and approachable expression. Business casual: white blouse, 
navy blazer. Realistic skin texture, not airbrushed.

Setting: modern co-working space with green plants and 
warm wood accents. Background slightly blurred.

Shot with 85mm lens at f/2.8, soft natural light with 
studio fill. 4:5 aspect ratio, shallow depth of field.

Style: authentic employer branding — NOT a stock photo.
Subtle navy blue and white color accents where natural.

Exclude: stock photo aesthetic, forced poses, over-smoothing.
```

### Szenario 4: Mitarbeiter in neuem Setting (Image-to-Image)

**Ziel:** Ein Foto eines Mitarbeiters in eine neue Szene übertragen

```
Using the uploaded photo as reference — keep the exact facial 
structure, skin tone, hairstyle, and body identity unchanged.

Place this person in a modern TK office environment. 
They wear a navy blue blazer over a white shirt, looking 
confident and trustworthy. Warm natural light from large windows.

Shot on Canon EOS R5, 50mm lens, f/2.8, vertical 9:16 format.
Shallow depth of field, professional editorial quality.

Skin: natural texture, visible pores, no over-smoothing.

Exclude: artificial look, cartoon/CGI, logos, text, 
altered facial features, plastic skin.
```

### Szenario 5: Kreatives Porträt für Social Media (Königsklasse)

**Ziel:** Aufmerksamkeitsstarkes Bild für eine LinkedIn- oder Instagram-Kampagne

```
Dramatic, ultra-realistic close-up in black and white with 
high-contrast cinematic lighting from the side, highlighting 
the contours of his face and beard, casting deep shadows.

He wears round, reflective sunglasses. He gazes confidently 
upward. The sunglasses reflect a modern city skyline.

The atmosphere is mysterious with a minimalist black background.
Shot on Hasselblad X2D, 85mm lens, f/2.0.

Details in 4K: every skin pore visible, authentic stubble texture,
fine film grain, subsurface scattering on skin.
High dynamic range for shadow detail.

Exclude: color, soft focus, cartoon look, over-smoothing.
```

---

## Was kann Fotorealismus-Prompting (noch) nicht?

Trotz der beeindruckenden Fortschritte gibt es klare Grenzen:

| Limitation | Auswirkung | Workaround |
|-----------|-----------|------------|
| **Hände und Finger** | Immer noch die häufigste Fehlerquelle — extra Finger, verschmolzene Finger, verzerrte Hände | Hände im Prompt verstecken (z.B. „hands in pockets", „arms crossed") oder mehrfach regenerieren |
| **Exakte Text-Wiedergabe** | Text im Bild ist besser geworden, aber nicht 100% zuverlässig | Text nachträglich in einem Design-Tool einfügen, oder Gemini Nano Banana Pro / Ideogram verwenden |
| **Zahndetails bei Lachen** | Zu perfekte oder unsymmetrische Zähne | „subtle, natural smile with lips slightly parted" statt „wide grin showing teeth" |
| **Spezifische reale Personen** | Ethische und rechtliche Einschränkungen; Modelle verweigern oft | Image-to-Image mit eigenem Foto + Identity Lock nutzen |
| **Gruppenfotos (>3 Personen)** | Identitäten verschmelzen, Proportionen stimmen nicht | Einzeln generieren und compositen, oder Gemini Nano Banana Pro für Multi-Reference |
| **Konsistente Serie** | Dieselbe Person sieht über mehrere Bilder leicht anders aus | 360°-Sheet als Referenz, Seed-Werte fixieren (wo möglich) |
| **Spezifische Marken/Logos** | Werden oft verweigert oder falsch dargestellt | Neutrale Kleidung generieren, Logo nachträglich einsetzen |
| **Schmuck und Accessoires** | Ringe, Ohrringe, Uhren können verzerrte Details haben | In separatem Schritt zoomen und regenerieren, oder Inpainting |

### Bank-spezifische Risiken

- **Compliance:** KI-generierte Bilder von „Mitarbeitern" dürfen nicht als echte Fotos ausgegeben werden. Immer kennzeichnen!
- **Datenschutz:** Laden Sie nur Mitarbeiterfotos hoch, für die eine Einwilligung vorliegt
- **CD-Konformität:** Prüfen Sie, ob die generierten Bilder zu Ihren Corporate-Design-Richtlinien passen
- **Diskriminierung:** Achten Sie bei der Prompt-Gestaltung auf diverse, inklusive Darstellung

> **Volksbank-Analogie:** Es ist wie bei der neuen Software-Einführung: Man braucht die Schulung UND die Compliance-Freigabe. Nur weil es technisch geht, heißt es nicht, dass Sie es ungeprüft einsetzen dürfen.

---

## Was kostet das? KI-Fotorealismus vs. echtes Fotoshooting

| Szenario | Klassisch (Fotograf) | KI-generiert | Zeitersparnis |
|----------|---------------------|-------------|---------------|
| **1 Porträt-Konzept (Exploration)** | 200–500 € (Fotograf-Stundensatz) | 0–5 € (Abo-anteilig) | 3 Tage → 5 Minuten |
| **10 LinkedIn-Porträts (Kampagne)** | 1.500–3.000 € (Shooting + Retusche) | 10–30 € (Abo + Iterationszeit) | 1 Woche → 2 Stunden |
| **Recruiting-Kampagne (20 diverse Motive)** | 5.000–12.000 € (Agentur + Modelle) | 30–80 € (Abo + Prompt-Entwicklung) | 3–4 Wochen → 1 Tag |
| **Produkt-Fotografie (Konzepte)** | 500–2.000 € (Studio + Styling) | 5–20 € | 1 Woche → 3 Stunden |
| **Echte Team-Fotos** | 1.000–3.000 € | ❌ Nicht empfohlen — Authentizität wichtiger | — |

**Empfehlung für Ihren Workflow:** KI für die ersten 80% (Konzepte, Moodboards, Varianten, Content-Ideen). Professionelles Shooting für die letzten 20% (offizielle Team-Fotos, Geschäftsbericht, regulierte Materialien).

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Der Brennweiten-Vergleich

Generieren Sie dasselbe Motiv mit drei verschiedenen Brennweiten und beobachten Sie den Unterschied:

**Basis-Prompt (in ChatGPT, Gemini oder Midjourney):**
```
Photorealistic portrait of a business professional 
in her 40s, standing in a modern office hallway.
Navy blazer, white blouse, confident expression.
Natural window light from the left. 
Fine film grain, editorial quality.
```

**Variante A:** Fügen Sie hinzu: `Shot with 24mm wide-angle lens, f/8`
**Variante B:** Fügen Sie hinzu: `Shot with 50mm lens, f/2.8`
**Variante C:** Fügen Sie hinzu: `Shot with 135mm telephoto lens, f/2.0`

**Was fällt Ihnen auf?**
- 24mm: Breiter Raum sichtbar, Person wirkt dynamisch, Linien laufen zusammen
- 50mm: Natürlich, wie Sie es mit eigenen Augen sehen würden
- 135mm: Starke Hintergrundkompression, cremiges Bokeh, Person „springt" aus dem Bild

### Hands-on 2: Der Beleuchtungs-Vergleich

Generieren Sie dasselbe Porträt mit unterschiedlicher Beleuchtung:

**Basis-Prompt:**
```
Close-up portrait of a man in his 50s, 
greying temples, warm brown eyes, slight smile.
Dark suit, minimal background.
85mm lens, f/2.0.
```

**Variante A:** `soft natural window light from the left, gentle shadows`
**Variante B:** `Rembrandt lighting, dramatic, triangle of light on cheek`
**Variante C:** `backlit by golden hour sun, rim light on hair, lens flare`
**Variante D:** `split lighting, half face in shadow, moody and intense`

### Hands-on 3: Der Modellvergleich (Pflicht!)

Nehmen Sie **einen** der Prompts aus Hands-on 1 oder 2 und geben Sie ihn in **zwei verschiedene Tools** ein (z.B. ChatGPT + Gemini, oder ChatGPT + Midjourney):

**Beobachten Sie:**
- Welches Modell trifft die Kamera-Angaben besser?
- Wo wirkt die Haut natürlicher?
- Welches Modell interpretiert die Beleuchtung überzeugender?
- Gibt es auffällige Unterschiede bei Händen, Haaren, Reflexionen?

---

## End-to-End: Die Fotorealismus-Pipeline

```
┌──────────────────────────────────────────────────────────────────┐
│            VON DER IDEE ZUM FOTOREALISTISCHEN BILD               │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. ZIEL DEFINIEREN ───── Was soll das Bild zeigen?              │
│     │                     Porträt? Produkt? Szene?               │
│     ▼                                                            │
│  2. REFERENZ? ──────────── Habe ich ein Foto als Basis?          │
│     │   Ja → Identity Lock + Image-to-Image                     │
│     │   Nein → Text-to-Image mit detaillierter Beschreibung     │
│     ▼                                                            │
│  3. 7 STELLSCHRAUBEN ──── Alle durchgehen:                       │
│     │  📷 Kamera (Brennweite, Blende, Gerät)                    │
│     │  🔆 Beleuchtung (Typ, Richtung, Stimmung)                 │
│     │  🎯 Komposition (Ausschnitt, Winkel, Regel)               │
│     │  👤 Subjekt (Person/Objekt, Details, Imperfektionen)       │
│     │  🏞️ Umgebung (Vorder-/Mittel-/Hintergrund)                │
│     │  🎨 Nachbearbeitung (Filmkorn, Farben, Kontrast)          │
│     │  ⛔ Ausschlüsse (was NICHT im Bild sein soll)             │
│     ▼                                                            │
│  4. MODELL WÄHLEN ─────── Je nach Aufgabe (Tabelle oben)        │
│     ▼                                                            │
│  5. PROMPT FORMULIEREN ── Fließtext oder JSON-Vorlage           │
│     ▼                                                            │
│  6. GENERIEREN ─────────── 3-4 Varianten gleichzeitig           │
│     ▼                                                            │
│  7. PRÜFEN & ITERIEREN ── Stimmt das Licht? Die Haut?           │
│     │                     Die Hände? → Feedback-Formel:          │
│     │                     „Ändere X, weil Y, gemessen an Z"     │
│     ▼                                                            │
│  8. FINALISIEREN ──────── Export, CD-Check, Kennzeichnung       │
│                            als KI-generiert                      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## Zusammenfassung

| Was Sie gelernt haben | Kernaussage |
|-----------------------|-------------|
| **Fotografen-Sprache** | Kamera-Begriffe funktionieren besser als bildliche Beschreibungen, weil die KI mit Foto-Metadaten trainiert wurde |
| **7 Stellschrauben** | Kamera, Licht, Komposition, Subjekt, Umgebung, Nachbearbeitung, Ausschlüsse — Ihr Cockpit für Fotorealismus |
| **Brennweite = Perspektive** | 24mm (weitwinklig, dramatisch) → 85mm (Porträt, schmeichelhaft) → 135mm (komprimiert, Bokeh) |
| **Blende = Schärfentiefe** | Kleine Zahl (f/1.4) = unscharfer Hintergrund. Große Zahl (f/11) = alles scharf |
| **Beleuchtung entscheidet** | Rembrandt, Split, Butterfly, Golden Hour — jedes Setup erzeugt eine andere Emotion |
| **Kontrollierte Imperfektionen** | Hautporen, Fältchen, Filmkorn — zu perfekt = erkennbar künstlich |
| **Identity Lock** | „Keep exact facial structure unchanged" — der Schlüssel für Image-to-Image |
| **JSON-Vorlagen** | Strukturierte Prompts für reproduzierbare, professionelle Ergebnisse |
| **Modellspezifisch denken** | Midjourney: --style raw. FLUX: keine Negativ-Prompts. ChatGPT: konversationell. Gemini: Multi-Reference |
| **Ausschlüsse** | Genauso wichtig wie Einschlüsse — „Exclude: cartoon, over-smoothing, plastic skin" |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---------------------------|--------------------------------|
| **7 Stellschrauben** | Erweiterung des 6-Bausteine-Frameworks aus Kapitel 03, Tutorial 01 |
| **Kamera-Metadaten als Trainingsgrundlage** | Basiert auf dem Prinzip der Muster-Erkennung aus Kapitel 00, Tutorial 02 (Diffusion) |
| **JSON-Prompt-Vorlage** | Anwendung der strukturierten Prompt-Techniken aus Kapitel 02, Tutorial 03 (JSON) |
| **Modellspezifische Anpassung** | Vertieft die Modell-Übersicht aus Kapitel 03, Tutorial 01 |
| **Identity Lock bei Image-to-Image** | Nutzt das Image-to-Image-Prinzip aus Kapitel 03, Tutorial 01 |
| **Feedback-Formel für Iterationen** | Dieselbe Formel (Änderung → Grund → Messung) aus Kapitel 03, Tutorial 01 |
| **Ausschlüsse vs. positive Formulierung** | Verbindung zu „klar und spezifisch prompten" aus Kapitel 01, Tutorial 01 |

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Bokeh** | Die ästhetische Qualität der Unschärfe im Hintergrund eines Fotos, erzeugt durch große Blendenöffnung (z.B. f/1.4). Japanisch für „Unschärfe" |
| **Brennweite (mm)** | Abstand zwischen Objektivlinse und Bildsensor. Bestimmt den Bildwinkel — kurz (24mm) = weit, lang (85mm) = eng |
| **Blende (f-Wert)** | Öffnung im Objektiv, die Lichtmenge und Schärfentiefe steuert. Kleine Zahl = große Öffnung = wenig Schärfentiefe |
| **Schärfentiefe (Depth of Field)** | Der Bereich im Bild, der scharf abgebildet wird. Gering = nur Motiv scharf, tief = alles scharf |
| **Rembrandt-Licht** | Beleuchtungstechnik mit Licht von oben-seitlich, die ein kleines Lichtdreieck auf der abgewandten Wange erzeugt |
| **Golden Hour** | Die Stunde nach Sonnenaufgang und vor Sonnenuntergang, in der das Licht besonders warm und weich fällt |
| **Identity Lock** | Anweisung an die KI, die exakte Gesichtsstruktur, Hautton und Merkmale eines hochgeladenen Referenzfotos beizubehalten |
| **360°-Sheet** | Referenzbilder einer Person aus mehreren Winkeln (frontal, Profil, Rücken), die als Basis für konsistente Generierungen dienen |
| **Style Raw** | Midjourney-Parameter (--style raw), der die automatische Ästhetisierung deaktiviert und natürlichere Ergebnisse liefert |
| **Subsurface Scattering** | Der physikalische Effekt, bei dem Licht in Haut oder andere transluzente Materialien eindringt und sie von innen leuchten lässt |
| **Rim Light** | Gegenlicht, das eine leuchtende Kontur um das Motiv erzeugt und es vom Hintergrund trennt |
| **Filmkorn** | Zufällige Textur in analogen Fotos, die durch die lichtempfindlichen Kristalle im Film entsteht. Wird digital als Stilmittel eingesetzt |
| **Computational Photography** | Bildverarbeitung durch Software (wie in Smartphones), die optische Limitierungen durch Algorithmen ausgleicht — HDR, Nachtmodus etc. |
| **Key Light** | Die Hauptlichtquelle in einem Beleuchtungssetup, die die dominante Richtung von Licht und Schatten bestimmt |
| **Fill Light** | Aufheller, der die Schatten des Key Light abschwächt, ohne eigene starke Schatten zu erzeugen |
| **ISO** | Lichtempfindlichkeit des Sensors. Höherer ISO = heller, aber mehr Bildrauschen |
| **Inpainting** | Technik, bei der nur ein ausgewählter Bereich eines Bildes neu generiert wird, während der Rest unverändert bleibt |
| **Prompt-Gewichtung** | Bei manchen Modellen (Stable Diffusion) können Teile des Prompts stärker gewichtet werden — bei FLUX nicht verfügbar |
| **HDR (High Dynamic Range)** | Technik, die Details sowohl in sehr hellen als auch in sehr dunklen Bildbereichen sichtbar macht |

---

