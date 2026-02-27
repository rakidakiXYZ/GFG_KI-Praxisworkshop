# Bildbearbeitung und iteratives Verfeinern

**Die Werkstatt — bestehende Bilder bearbeiten, Schritt für Schritt veredeln, und die Kunst der konversationellen Feedback-Schleife meistern**

---

## Warum dieses Tutorial?

In den letzten drei Tutorials haben Sie gelernt, Bilder **von Grund auf** zu erzeugen: die Modelllandschaft (03-01), Fotorealismus (03-02), Text und Grafikdesign (03-03). Aber im echten Alltag ist das nur die halbe Miete. Viel häufiger stehen Sie vor einer anderen Situation: **Sie haben bereits ein Bild** — ein Produktfoto, einen Filial-Schnappschuss, eine Agentur-Grafik — und möchten etwas daran **ändern**.

Bis 2024 hieß das: Photoshop öffnen, Freisteller machen, Ebenen jonglieren, Filter anwenden. Oder: Die Agentur anrufen und drei Tage auf eine Korrektur warten. Heute tippen Sie: *„Entferne die Person im Hintergrund"* — und es passiert. In Sekunden.

Dieses Tutorial ist **Die Werkstatt** — hier lernen Sie, wie Sie bestehende Bilder mit KI-Werkzeugen bearbeiten, Stück für Stück verfeinern und dabei die Kontrolle behalten.

**Was Sie nach diesem Tutorial wissen werden:**

- Wie Image-to-Image-Bearbeitung technisch funktioniert — und warum das für Ihre Prompts wichtig ist
- Die 5 Kern-Techniken: Inpainting, Outpainting, Style Transfer, Object Editing, Compositing
- Wie konversationelles Editing funktioniert — und warum es alles verändert
- Die goldenen Regeln für iteratives Verfeinern ohne Kontrollverlust
- Welche Modelle welche Editing-Aufgabe am besten beherrschen
- Praktische Workflows für den Bankalltag: Filialbilder aufbereiten, Kampagnen lokalisieren, Vorstandspräsentationen visuell aufwerten
- Was noch nicht funktioniert — und warum der „letzte Kilometer" immer noch menschlich ist

---

## Ein kurzer Blick zurück: Von Photoshop zu „Sag einfach, was du willst"

| Jahr | Meilenstein | Editing-Paradigma |
|------|-----------|-------------------|
| **1990** | Adobe Photoshop 1.0 | Pixel-für-Pixel — jede Änderung ist Handarbeit |
| **2016** | Content-Aware Fill (Photoshop) | Erste KI-gestützte Füll-Funktion — aber noch mit manueller Maskierung |
| **2021** | DALL·E 1, GLIDE | Erste KI-Inpainting-Demos — beeindruckend, aber nicht steuerbar |
| **2022** | Stable Diffusion Inpainting, DALL·E 2 | Masken-basiertes Inpainting — Sie markieren einen Bereich, KI füllt ihn |
| **2023** | Midjourney Vary Region, Adobe Generative Fill | KI-Editing wird Mainstream — direkt in Photoshop integriert |
| **2024** | FLUX Kontext, Ideogram Edit, GPT-4o Image | Konversationelles Editing: Kein Maskieren mehr — „Ändere X" reicht |
| **2025/26** | GPT Image 1.5, Gemini 3 Pro (Nano Banana Pro), Adobe Firefly 4 | Multi-Image-Compositing, Identity Preservation, turn-basiertes Editing — die Grenze zwischen Generator und Editor löst sich auf |

**Der Paradigmenwechsel:** Früher haben Sie dem Computer gezeigt, **wo** er etwas ändern soll (Maske malen). Heute **sagen** Sie, **was** sich ändern soll. Das Modell versteht den semantischen Inhalt des Bildes und ändert nur die relevanten Pixel.

> **Volksbank-Analogie:** Stellen Sie sich vor, Sie geben einem neuen Mitarbeiter eine Aufgabe. Früher mussten Sie sagen: „Öffne Ordner C, Blatt 3, Zeile 17, ändere die Zahl in Spalte D." Heute sagen Sie: „Aktualisiere den Zinssatz im Baufinanzierungsangebot auf 3,2 %." Der Mitarbeiter **versteht** die Aufgabe und findet die richtige Stelle selbst. So funktioniert modernes KI-Editing.

---

## Wie funktioniert Image-to-Image-Bearbeitung?

Bevor wir in die Praxis einsteigen, lohnt sich ein kurzer Blick unter die Haube. Wenn Sie verstehen, was das Modell tut, können Sie bessere Prompts schreiben.

### Das Grundprinzip

```
┌──────────────────────────────────────────────────────────────────┐
│           IMAGE-TO-IMAGE: WAS PASSIERT HINTER DEN KULISSEN       │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  EINGABE ───────────── Ihr bestehendes Bild                     │
│     │                  + Ihr Text-Prompt (die Anweisung)         │
│     ▼                                                            │
│  VERSTEHEN ─────────── Das Modell analysiert das Bild:          │
│     │                  „Was ist darauf zu sehen?"                │
│     │                  Personen, Objekte, Hintergrund,           │
│     │                  Beleuchtung, Stil, Perspektive            │
│     ▼                                                            │
│  PLANEN ────────────── Das Modell interpretiert den Prompt:     │
│     │                  „Was soll sich ändern?"                   │
│     │                  „Was muss GLEICH bleiben?"                │
│     ▼                                                            │
│  GENERIEREN ────────── Nur die betroffenen Bildbereiche         │
│     │                  werden neu erzeugt — der Rest bleibt     │
│     ▼                                                            │
│  AUSGABE ───────────── Das bearbeitete Bild                     │
│                        (im besten Fall: nahtlos integriert)      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Zwei entscheidende Parameter

Bei der Bildbearbeitung gibt es einen fundamentalen Trade-off, den Sie kennen müssen:

**1. Input Fidelity (Treue zum Original)**

Je höher die Fidelity, desto stärker hält das Modell am Originalbild fest. Je niedriger, desto mehr „kreative Freiheit" nimmt es sich.

| Einstellung | Wirkung | Wann nutzen? |
|------------|---------|-------------|
| **Fidelity hoch** | Minimale Änderungen, Original bleibt fast identisch | Kleine Korrekturen: Farbe ändern, Objekt entfernen, Text tauschen |
| **Fidelity mittel** | Balance zwischen Treue und Neugestaltung | Style Transfer, Beleuchtung ändern, Szene umgestalten |
| **Fidelity niedrig** | Starke Neuinterpretation, nur Grundstruktur bleibt | Komplettes Restyling, „Mach daraus eine Ölmalerei" |

Bei GPT Image 1.5 steuern Sie das über den Parameter `input_fidelity` (API) oder implizit über die Stärke Ihrer Anweisung. Bei Gemini geschieht es über die Art der Formulierung.

**2. Quality (Ausgabequalität)**

Wie in Tutorial 03-03 bereits erwähnt: Für jede Bearbeitung, bei der Details zählen, setzen Sie `quality="high"`. Das dauert etwas länger, aber die Ergebnisse — besonders bei Gesichtern und Text — sind deutlich besser.

> **Volksbank-Analogie:** Input Fidelity ist wie der Spielraum bei einer Vertragsänderung. „Hohe Fidelity" heißt: Nur den Zinssatz ändern, alles andere bleibt. „Niedrige Fidelity" heißt: Den gesamten Vertrag neu aufsetzen, aber die Eckdaten beibehalten. Je nach Situation brauchen Sie das eine oder das andere.

---

## Die 5 Kern-Techniken der KI-Bildbearbeitung

### Technik 1: Inpainting — Bereiche gezielt ersetzen

Inpainting ist die präziseste Editing-Technik: Sie sagen der KI, **was** sich in einem bestimmten Bereich des Bildes ändern soll, und alles drumherum bleibt unverändert.

**Wie es früher funktionierte (Masken-basiert):**
Sie malen mit einem Pinsel über den Bereich, der verändert werden soll → Die KI füllt nur diesen Bereich.

**Wie es heute funktioniert (konversationell):**
Sie beschreiben die Änderung in natürlicher Sprache → Die KI findet den richtigen Bereich **selbst**.

```
┌──────────────────────────────────────────────────────────────────┐
│     INPAINTING: MASKEN-BASIERT vs. KONVERSATIONELL               │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  FRÜHER (2022-2023):                                            │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                  │
│  │ Original │ →  │ Maske    │ →  │ Ergebnis │                  │
│  │  Bild    │    │ malen    │    │          │                  │
│  │ [Person] │    │ [██████] │    │ [Baum]   │                  │
│  └──────────┘    └──────────┘    └──────────┘                  │
│  „Ersetze den markierten Bereich durch einen Baum"             │
│                                                                  │
│  HEUTE (2025/26):                                               │
│  ┌──────────┐                    ┌──────────┐                  │
│  │ Original │ ─────────────────→ │ Ergebnis │                  │
│  │  Bild    │                    │          │                  │
│  │ [Person] │                    │ [Baum]   │                  │
│  └──────────┘                    └──────────┘                  │
│  „Ersetze die Person im Vordergrund durch einen Baum"          │
│  (Modell findet den Bereich selbst)                             │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

#### Praxis-Beispiele für Banken

**Objekt entfernen** (z.B. störende Elemente auf einem Filialbild):
```
Remove the trash can next to the entrance door.
Keep everything else exactly the same — 
lighting, perspective, background, ground texture.
Fill the removed area with a natural continuation 
of the surrounding pavement and wall.
```

**Objekt ersetzen** (z.B. Dekoration in der Filiale anpassen):
```
Replace the old poster in the window display 
with a modern digital screen showing a blue gradient.
Keep the window frame, reflections, and lighting realistic.
Do not change anything outside the poster area.
```

**Person entfernen** (z.B. Datenschutz auf Veranstaltungsfotos):
```
Remove all recognizable people from this bank branch photo.
Replace them with an empty, clean interior.
Preserve the exact architecture, furniture, lighting, 
and camera angle. The space should look naturally empty,
not like people were digitally erased.
```

> **Volksbank-Analogie:** Inpainting ist wie eine gezielte Korrektur in einem Dokument: Sie ändern einen bestimmten Absatz, ohne den Rest des Vertrags anzufassen. Stellen Sie sich vor, auf dem Foto Ihrer Filiale steht noch das alte Logo — Inpainting tauscht nur das Logo, alles andere bleibt pixelgenau gleich.

### Technik 2: Outpainting — Das Bild erweitern

Outpainting ist das Gegenteil von Inpainting: Statt etwas **im** Bild zu ändern, erweitern Sie das Bild **über seine Ränder hinaus**. Die KI generiert neue Bildbereiche, die nahtlos zum bestehenden Inhalt passen.

**Typische Anwendungsfälle:**

| Situation | Outpainting-Lösung |
|----------|-------------------|
| Foto ist Hochformat, Sie brauchen Querformat (16:9) | Links und rechts erweitern |
| Zu wenig Platz für eine Headline über dem Motiv | Nach oben erweitern |
| Instagram-Post (1:1) aus einem Querformat-Foto machen | Oben und unten erweitern |
| Mehr Kontext zeigen (z.B. mehr vom Gebäude sichtbar) | In die gewünschte Richtung erweitern |

```
Extend this image to the left and right to create 
a 16:9 widescreen format. 
Continue the architecture, sky, and lighting naturally.
The extended areas should blend seamlessly with 
the original image. No visible seam or style change.
Leave empty space above the building for a text overlay.
```

> **Volksbank-Analogie:** Outpainting ist wie ein Berater, der aus einer knappen Gesprächsnotiz einen vollständigen Bericht erstellt: Der Kern (das Originalfoto) bleibt identisch, aber der Kontext drumherum wird sinnvoll ergänzt — im selben Stil, im selben Ton, nahtlos weitergeführt.

### Technik 3: Style Transfer — Den visuellen Stil übertragen

Style Transfer bedeutet: Sie haben ein Bild mit dem richtigen **Inhalt** und ein Referenzbild mit dem richtigen **Stil** — und die KI kombiniert beides.

```
┌──────────────────────────────────────────────────────────────────┐
│           STYLE TRANSFER: INHALT + STIL = ERGEBNIS               │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  INHALTSBILD ──────── Was soll zu sehen sein?                   │
│  (Ihr Filialbild,     Architektur, Personen, Objekte            │
│   Ihr Produkt)                                                   │
│     │                                                            │
│     ├──── KOMBINIERT ──────────────→ ERGEBNIS                   │
│     │                                 Ihr Inhalt im             │
│  STILREFERENZ ─────── Wie soll es aussehen?            neuen Stil│
│  (Aquarell, Retro,    Farben, Texturen, Pinselstriche,          │
│   Neon, Vintage)      Beleuchtungsstimmung                      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

#### Style Transfer mit Referenzbild

```
Use the style from the provided reference image (Image 2) 
and apply it to the bank branch photo (Image 1).
Keep the architectural structure, layout, and perspective 
of Image 1 exactly as they are.
Transfer only the color palette, texture, and artistic style
from Image 2. White background not needed.
```

#### Style Transfer per Beschreibung (ohne Referenzbild)

```
Transform this bank branch photo into a warm, 
hand-painted watercolor illustration.
Visible brushstrokes, soft edges, slightly desaturated 
warm color palette (ochre, terracotta, sage green).
Keep the architectural structure and proportions accurate.
The result should look like an illustration from 
a premium real estate brochure.
```

#### Praxis-Anwendungen für Banken

| Anwendung | Stil-Anweisung | Ergebnis |
|-----------|---------------|----------|
| **Geschäftsbericht-Illustration** | Aquarell, reduzierte Palette, elegant | Filialfotos werden zu stilvollen Kapitel-Illustrationen |
| **Social Media: „Throwback"** | Verblasstes Polaroid, Körnigkeit, warme Töne | Historische Filialbilder für Jubiläumskampagne |
| **Recruiting-Material** | Pop-Art, kräftige Farben, dynamisch | Arbeitsplatzfotos werden zu auffälligen Anzeigen |
| **Weihnachtskampagne** | Winterlich, Schnee, warmes Licht, gemütlich | Sommerfotos der Filiale werden winterlich |
| **Kinder-/Jugend-Marketing** | Comic-Stil, bunt, flächig, freundlich | Produktfotos werden kindgerecht illustriert |

> **Volksbank-Analogie:** Style Transfer ist wie Corporate Design für Bilder: Sie nehmen ein normales Foto und „ziehen es an" — in den Stil, der zur aktuellen Kampagne passt. Das gleiche Filialbild kann für den Geschäftsbericht elegant, für die Weihnachtsaktion gemütlich und für das Recruiting-Poster dynamisch wirken.

### Technik 4: Beleuchtung, Wetter und Szenen-Transformation

Eine der faszinierendsten Fähigkeiten: Die KI kann die **Umgebungsbedingungen** eines Fotos komplett verändern, ohne die eigentliche Szene zu zerstören.

#### Beleuchtung ändern

```
Change the lighting in this office photo to warm 
golden-hour sunlight streaming through the windows.
Keep the room, furniture, and layout exactly the same.
Add natural window light with soft shadows.
The mood should shift from sterile office to 
inviting workspace.
```

#### Wetter und Jahreszeit transformieren

```
Transform this summer photo of the bank building 
into a winter scene. 
Add a light layer of fresh snow on the roof, 
sidewalk, and surrounding trees.
The sky should be overcast with soft, diffuse lighting.
Add warm light glowing from the windows.
Keep the building architecture identical.
```

#### Tageszeit ändern

```
Change this daytime photo of the bank exterior 
to an evening/dusk scene.
The sky should show a gradient from deep blue to orange
at the horizon. Turn on all interior lights — 
warm glow visible through the windows.
Add subtle street lighting and reflections on wet pavement.
Keep the building structure and perspective identical.
```

### Technik 5: Multi-Image Compositing — Mehrere Bilder kombinieren

Die mächtigste, aber auch anspruchsvollste Technik: Sie geben dem Modell **mehrere Bilder** als Input und beschreiben, wie sie kombiniert werden sollen.

**Wie es funktioniert:**

```
┌──────────────────────────────────────────────────────────────────┐
│      MULTI-IMAGE COMPOSITING: ELEMENTE KOMBINIEREN               │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  BILD 1 ──── Die Szene / der Hintergrund                       │
│  (z.B. leere Filiale)                                           │
│     │                                                            │
│  BILD 2 ──── Das Element, das eingefügt werden soll             │
│  (z.B. neues Möbelstück)                                        │
│     │                                                            │
│  BILD 3 ──── Optionale Stil-Referenz                            │
│  (z.B. gewünschte Lichtstimmung)                                │
│     │                                                            │
│     ▼                                                            │
│  PROMPT ──── „Setze das Möbelstück aus Bild 2 in die            │
│              Filiale aus Bild 1. Verwende die warme              │
│              Lichtstimmung aus Bild 3. Schatten und              │
│              Perspektive müssen zur Szene passen."               │
│     │                                                            │
│     ▼                                                            │
│  ERGEBNIS ── Ein einziges, kohärentes Bild                      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

**Entscheidend beim Compositing:**

1. **Referenzieren Sie jedes Bild klar:** „Image 1: the bank lobby. Image 2: the new armchair."
2. **Beschreiben Sie die Interaktion:** „Place the armchair from Image 2 in the waiting area of Image 1."
3. **Fixieren Sie, was sich nicht ändern darf:** „Keep the lobby's lighting, camera angle, and floor unchanged."
4. **Fordern Sie physikalische Konsistenz:** „Match shadows, perspective, scale, and reflections to the existing scene."

#### Praxis: Kampagnen-Lokalisierung

Ein besonders starker Anwendungsfall — Sie haben **ein Kampagnenmotiv** und möchten es für verschiedene Standorte anpassen:

```
Image 1: Our campaign key visual with the model and product.
Image 2: Photo of the Frankfurt skyline.

Place the campaign scene from Image 1 into the Frankfurt 
setting of Image 2. The person should appear to be standing 
at a location with the skyline visible behind them.
Match the lighting of Image 1 to the natural light 
in Image 2 (time of day, color temperature).
Preserve the person's face, clothing, and pose exactly.
The composite should look like a single photograph,
not a collage.
```

> **Volksbank-Analogie:** Multi-Image Compositing ist wie ein Beratungsgespräch mit Unterlagen aus verschiedenen Quellen: Sie haben den Kontoauszug (Bild 1), den Finanzplan (Bild 2) und die Marktdaten (Bild 3). Aus diesen Einzelteilen erstellt der Berater ein kohärentes Gesamtbild — die persönliche Finanzanalyse. Kein Element wird verfälscht, aber zusammen ergeben sie etwas Neues.

---

## Konversationelles Editing: Die Revolution

Das Wichtigste, was Sie aus diesem Tutorial mitnehmen sollten, ist vermutlich dieses Konzept. **Konversationelles Editing** bedeutet: Sie bearbeiten ein Bild nicht mit einem einzelnen perfekten Prompt, sondern in einem **Gespräch** — Schritt für Schritt, wie mit einem menschlichen Designer.

### Warum ist das so wichtig?

```
┌──────────────────────────────────────────────────────────────────┐
│        KONVERSATIONELLES EDITING: DER WORKFLOW                    │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  RUNDE 1: Sie laden ein Foto hoch                               │
│  → „Entferne die Person links im Bild."                        │
│  → Modell liefert Ergebnis v1                                   │
│     │                                                            │
│  RUNDE 2: Sie reagieren auf das Ergebnis                        │
│  → „Gut, aber der Schatten am Boden ist noch da.               │
│      Entferne auch den."                                         │
│  → Modell liefert Ergebnis v2                                   │
│     │                                                            │
│  RUNDE 3: Nächste Änderung                                      │
│  → „Perfekt. Jetzt mach die Beleuchtung wärmer —               │
│      wie spätnachmittags."                                       │
│  → Modell liefert Ergebnis v3                                   │
│     │                                                            │
│  RUNDE 4: Feinschliff                                           │
│  → „Fast. Etwas weniger orange, mehr golden.                    │
│      Und der Himmel durch das Fenster soll                       │
│      zur Tageszeit passen."                                      │
│  → Modell liefert Ergebnis v4 ✓                                │
│                                                                  │
│  Ergebnis: Exakt das Bild, das Sie wollten —                   │
│  erreicht in 4 kurzen Nachrichten, nicht mit einem              │
│  Monster-Prompt.                                                 │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Die Vorteile gegenüber dem „One-Shot-Prompt"

| Ansatz | One-Shot (ein Prompt) | Konversationell (Turn-basiert) |
|--------|----------------------|-------------------------------|
| **Kontrolle** | Alles-oder-nichts | Schrittweise, präzise |
| **Fehlerkorrektur** | Komplett neu generieren | Nur den fehlerhaften Aspekt korrigieren |
| **Prompt-Komplexität** | Enorm lang, leicht widersprüchlich | Kurze, klare Einzelanweisungen |
| **Lernkurve** | Steil — Sie müssen alles vorab planen | Flach — einfach beschreiben, was stört |
| **Identitäts-Erhalt** | Risiko: Gesichter/Details ändern sich | Besser: Modell „erinnert" sich an vorherige Version |
| **Zeitaufwand** | 15 Min Prompt schreiben + 5 Min generieren | 5× je 30 Sek. tippen + generieren |

### Die goldenen Regeln des konversationellen Editings

**Regel 1: Eine Änderung pro Runde**

Nicht: „Entferne die Person, mach den Himmel blauer, ändere die Beleuchtung und füge Schnee hinzu."

Sondern:
- Runde 1: „Entferne die Person."
- Runde 2: „Mach den Himmel blauer."
- Runde 3: „Wärmere Beleuchtung."
- Runde 4: „Füge leichten Schnee hinzu."

**Warum?** Wenn Sie mehrere Änderungen gleichzeitig anfordern und eine davon schiefgeht, wissen Sie nicht, welche das Problem verursacht hat. Außerdem steigt bei Multi-Edits die Gefahr von **Drift** — unbeabsichtigte Änderungen an Teilen, die gleich bleiben sollten.

**Regel 2: Sagen Sie, was GLEICH bleiben muss**

Bei jeder Runde: Wiederholen Sie explizit, was sich **nicht** ändern darf. Modelle „vergessen" Constraints über mehrere Runden hinweg.

```
Remove the coffee cup from the desk.
KEEP UNCHANGED: the person's face, clothing, pose,
the room lighting, the background, all other objects 
on the desk. Do not alter anything except the coffee cup.
```

**Regel 3: Referenzieren Sie vorherige Versionen**

Wenn etwas in einer früheren Runde besser war:

```
The lighting from version 2 was better — go back to 
that warm tone, but keep the edits from version 3 
(the removed background person).
```

**Regel 4: Nutzen Sie „input_fidelity: high" für Korrekturen**

Wenn Sie nur kleine Änderungen machen (Farbnuance, ein Detail entfernen), signalisieren Sie dem Modell maximale Treue zum Ausgangs-Bild. Bei ChatGPT und der OpenAI API ist das der Parameter `input_fidelity="high"`.

**Regel 5: Wissen, wann Sie aufhören sollten**

Nach 5–7 Runden Editing können sich subtile Artefakte ansammeln — leichte Unschärfe, veränderte Hauttöne, „überarbeitete" Texturen. Wenn das passiert:
- Exportieren Sie die beste bisherige Version
- Starten Sie einen neuen Chat mit dieser Version als frischem Input
- Oder wechseln Sie für den Feinschliff in ein Design-Tool

> **Volksbank-Analogie:** Konversationelles Editing ist wie eine Kreditverhandlung: Sie starten mit einem Angebot (Version 1). Der Kunde sagt: „Der Zinssatz passt, aber die Laufzeit nicht." Sie passen **nur die Laufzeit** an (Version 2). Der Kunde: „Fast. Noch eine Sondertilgungsoption." Sie ergänzen (Version 3). Jede Runde ändert **ein** Element. Am Ende haben beide Seiten exakt den Vertrag, den sie wollen — ohne jedes Mal bei null anzufangen.

---

## Das Drift-Problem: Die unsichtbare Gefahr

Wenn Sie ein Bild über mehrere Runden hinweg bearbeiten, passiert etwas Subtiles: Das Modell verändert nicht nur, worum Sie gebeten haben, sondern auch **kleine Details**, um die Sie nicht gebeten haben. Die Hautfarbe wird einen Tick heller. Der Hintergrund verschiebt sich leicht. Ein Schatten ändert seine Richtung. Das nennt man **Drift**.

```
┌──────────────────────────────────────────────────────────────────┐
│                  DAS DRIFT-PROBLEM VISUALISIERT                   │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ORIGINAL        EDIT 1          EDIT 2          EDIT 3         │
│  ┌────────┐     ┌────────┐     ┌────────┐     ┌────────┐      │
│  │Gesicht │     │Gesicht │     │Gesicht │     │Gesicht │      │
│  │  100%  │     │  97%   │     │  93%   │     │  88%   │      │
│  │Original│     │ähnlich │     │ähnlich │     │anders! │      │
│  └────────┘     └────────┘     └────────┘     └────────┘      │
│                                                                  │
│  Sie haben NUR den Hintergrund geändert —                       │
│  aber das Gesicht hat sich trotzdem verändert.                  │
│                                                                  │
│  GEGENMASSSNAHMEN:                                              │
│  1. „Preserve the person's face EXACTLY" bei jeder Runde       │
│  2. input_fidelity="high" verwenden                             │
│  3. Nach 3-4 Runden: Beste Version exportieren,                │
│     neuen Chat starten                                          │
│  4. Identitäts-kritische Teile NICHT in der letzten             │
│     Runde ändern                                                 │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Anti-Drift-Checkliste

Wiederholen Sie bei **jeder** Editing-Runde diese Formel:

```
[Ihre gewünschte Änderung].
PRESERVE EXACTLY: [Liste aller Elemente, die gleich bleiben müssen].
Do not alter anything beyond the specified change.
```

---

## Die Modell-Landschaft: Wer bearbeitet Bilder am besten? (Stand: Februar 2026)

| Modell | Inpainting | Outpainting | Style Transfer | Identity Preservation | Multi-Image | Konversationell | Preis |
|--------|-----------|------------|---------------|---------------------|------------|----------------|-------|
| **GPT Image 1.5** | ★★★★★ | ★★★★☆ | ★★★★★ | ★★★★★ | ★★★★★ (bis 14 Bilder) | ★★★★★ | API: ~0,02–0,08 $/Bild |
| **Gemini 3 Pro (Nano Banana Pro)** | ★★★★★ | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★★★ | In Gemini Advanced enthalten |
| **Adobe Firefly 4** | ★★★★★ | ★★★★★ | ★★★☆☆ | ★★★★☆ | ★★★☆☆ | ⚠️ Photoshop-UI, kein Chat | In Creative Cloud enthalten |
| **FLUX Kontext** | ★★★★☆ | ★★★☆☆ | ★★★★☆ | ★★★★☆ | ★★★☆☆ | ★★★★☆ | API-basiert |
| **Ideogram 3.0** | ★★★★☆ | ★★★☆☆ | ★★★☆☆ | ★★★☆☆ | ★★★☆☆ | ★★★☆☆ | Free + Abo ab 8 $/Monat |
| **Leonardo AI Canvas** | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★☆☆ | ★★★☆☆ | ⚠️ Canvas-UI, kein Chat | Free + Pro |

### Empfehlung nach Editing-Aufgabe

| Was brauchen Sie? | Bestes Modell | Warum |
|-------------------|--------------|-------|
| **Konversationelles Editing im Chat** | GPT Image 1.5 oder Gemini 3 Pro | Natürliches Turn-basiertes Arbeiten, Kontext bleibt erhalten |
| **Präzises Inpainting (einzelnes Objekt)** | GPT Image 1.5 oder Adobe Firefly | GPT: konversationell; Firefly: maskenbasiert mit Photoshop-Präzision |
| **Outpainting / Bildformat anpassen** | Adobe Firefly oder Leonardo AI Canvas | Beste Randkontinuität, intuitive UI |
| **Style Transfer auf Fotos** | GPT Image 1.5 oder FLUX Kontext | Stärkste Stil-Übernahme bei Beibehaltung der Struktur |
| **Multi-Image Compositing** | GPT Image 1.5 | Unterstützt bis zu 14 Eingangsbilder, beste Kompositionsqualität |
| **Kampagnen-Varianten (Batch)** | GPT Image 1.5 API | Automatisierung über API, konsistente Ergebnisse |
| **Gesichts-Erhalt über mehrere Edits** | GPT Image 1.5 | Stärkste Identity Preservation bei sequenziellen Edits |

---

## Praxis-Workflow: Konversationelles Editing Schritt für Schritt

Hier ein realistisches Beispiel — Sie haben ein Foto der Filiale und wollen es für eine Winterkampagne aufbereiten:

### Runde 1: Aufräumen

```
Sie: [laden das Filialbild hoch]
"Remove the parked cars from in front of the building.
Fill the area with a natural continuation of the 
street and sidewalk."
```

### Runde 2: Personendaten schützen

```
Sie: "Good. Now remove all recognizable people 
from the image. Replace them with an empty scene.
Keep the building and surroundings exactly as they are."
```

### Runde 3: Atmosphäre ändern

```
Sie: "Perfect. Now transform this into a cozy 
winter evening scene:
- Add fresh snow on the roof, sidewalk, and trees
- Change the sky to a blue-grey winter twilight
- Make warm golden light glow from all windows
- Add a subtle snowfall effect
Keep the building architecture 100% identical."
```

### Runde 4: Feinschliff

```
Sie: "Almost there. The snow on the roof looks 
a bit too heavy — reduce it by half. 
And add a small lit Christmas tree next to the entrance.
Keep everything else from this version."
```

### Runde 5: Text-Overlay vorbereiten

```
Sie: "Last edit: Darken the top 20% of the image 
slightly (gradient to dark blue) to create a 
clean area for a text overlay. 
Don't change the bottom 80% at all."
```

**Ergebnis nach 5 Runden (~5 Minuten):** Aus einem normalen Sommerfoto wird ein stimmungsvolles Winterbild, bereit für die Kampagnen-Headline. Ohne Photoshop. Ohne Agentur. Ohne Wartezeit.

---

## Praxis: Typische Bank-Workflows

### Workflow 1: Filialbilder für verschiedene Kampagnen aufbereiten

Ein Satz guter Filialfotos kann über das Jahr hinweg für verschiedene Zwecke wiederverwendet werden:

| Kampagne | Editing-Anweisung | Ergebnis |
|----------|------------------|----------|
| **Frühjahrsaktion** | „Make it a bright spring day. Add blooming trees." | Filiale im Frühling |
| **Sommeraktion** | „Add warm sunlight, blue sky, outdoor café tables." | Einladende Sommerszene |
| **Herbst (Altersvorsorge)** | „Transform to golden autumn. Warm, contemplative mood." | Herbstliches Stimmungsbild |
| **Weihnachten** | „Add snow, Christmas decorations, warm window light." | Winterliche Filiale |
| **Nacht-/Event-Version** | „Transform to elegant evening. Interior lights glow." | Abendstimmung für Events |

**ROI:** Ein professionelles Outdoor-Shooting kostet 1.500–3.000 € pro Saison. Mit KI-Editing erstellen Sie 5 Saisonvarianten aus einem einzigen Foto für unter 20 €.

### Workflow 2: Kampagnen-Lokalisierung

Sie haben ein nationales Kampagnenmotiv und möchten es für verschiedene Regionen anpassen:

```
Image 1: National campaign image with the model 
and product in a generic setting.

Change only the visible background cityscape to show 
[Stadt-Name], with recognizable architecture.
Keep the person, lighting angle, product placement,
and color grading exactly the same.
Realistic composite — it should look like the photo 
was taken in [Stadt-Name].
```

### Workflow 3: Vorstandspräsentation visuell aufwerten

Ein trockener Konferenzraumfoto wird zur stilvollen Illustration:

```
Transform this meeting room photo into an elegant,
slightly desaturated editorial-style image.
Enhance the lighting to be soft and professional.
Reduce visual clutter — simplify the background.
Add a subtle depth-of-field effect focusing on the table.
The result should look like a premium business magazine photo.
```

### Workflow 4: Produktfotos extrahieren und neu inszenieren

Sie haben ein Foto eines Bankterminals oder -produkts vor unschönem Hintergrund:

```
Extract the ATM/terminal from this photo.
Place it on a clean, neutral gradient background 
(light grey to white).
Add a subtle contact shadow beneath it for realism.
The product should look like a professional catalog photo.
Keep all text, labels, and product details sharp and legible.
```

---

## Was kann KI-Bildbearbeitung (noch) nicht?

| Limitation | Auswirkung für Banken | Workaround |
|-----------|----------------------|------------|
| **Exakte Pixel-Kontrolle** | Wenn ein Logo pixelgenau an Position X,Y stehen muss — KI platziert „ungefähr richtig" | Logo nachträglich im Design-Tool platzieren |
| **Konsistente Serienbilder** | 10 Varianten desselben Motivs haben leichte Unterschiede in Details | Style-Guide als Referenzbild mitgeben; kritische Elemente extern fixieren |
| **Feine Typografie-Anpassungen** | Kerning, Schriftgröße, exakte Ausrichtung sind nicht steuerbar | Text immer im Design-Tool finalisieren (Kapitel 03, Tutorial 03) |
| **Fotografische Fakten** | KI kann eine Filiale winterlich machen, die es im Winter nie gab — das Ergebnis ist ein „KI-Bild", kein „Foto" | Kennzeichnungspflicht beachten: „Visualisierung / KI-generiert" |
| **Gesichts-Manipulation** | Technisch möglich, ethisch/rechtlich problematisch | Niemals echte Mitarbeiter-/Kundengesichter verändern ohne Einwilligung |
| **Komplexe Perspektiv-Korrekturen** | KI kann eine Perspektive anpassen, aber bei extremen Winkeln werden Proportionen fehlerhaft | Professionelle Perspektivkorrektur in Lightroom/Photoshop |
| **Verlustfreie Qualität** | Jedes Edit-Runde führt zu minimalem Qualitätsverlust (wie bei JPEG-Neukomprimierung) | Höchste Qualitätsstufe verwenden; nach 5-7 Runden frischen Start |
| **Verständnis von Corporate-Design-Regeln** | KI kennt Ihre Brand-Guidelines nicht — Schutzzone um Logo, Mindestgrößen, Farbregeln | CD-Richtlinien explizit im Prompt beschreiben oder externe Prüfung |

### Bank-spezifische Editing-Risiken

| Risiko | Szenario | Maßnahme |
|--------|---------|----------|
| **Deepfake-Verdacht** | Mitarbeiterfoto wird bearbeitet (Hintergrund getauscht) → sieht manipuliert aus | Originale aufbewahren; Änderungen dokumentieren |
| **Datenschutz** | Personenbezogene Bilder werden in Cloud-Modelle hochgeladen | On-Premise-Lösung prüfen; keine Kundenfotos in ChatGPT/Gemini |
| **Urheberrecht** | Agenturbilder bearbeiten → kann gegen Lizenz verstoßen | Nutzungsrechte prüfen: „Bearbeitungsrecht" in der Bildlizenz? |
| **Täuschung** | KI-bearbeitetes Filialbild suggeriert Zustand, der nicht existiert | Transparenz: „Visualisierung" kennzeichnen |
| **Qualitätssicherung** | Artefakte, die auf kleinem Bildschirm unsichtbar sind, fallen im Druck auf | Immer auf Ziel-Medium prüfen (Print: 300 DPI, Monitor: 72 DPI) |

> **Volksbank-Analogie:** KI-Bildbearbeitung unterliegt denselben Sorgfaltspflichten wie die Bearbeitung eines Kreditantrags: Sie dürfen Daten aktualisieren und formatieren, aber nichts **verfälschen**. Wenn Sie ein Filialbild winterlich machen, ist das Dekoration. Wenn Sie bauliche Mängel wegretuschieren, ist das Täuschung. Die Grenze liegt bei der **Absicht** — und im Zweifel bei der Compliance-Abteilung.

---

## Was kostet das? KI-Editing vs. klassische Bildbearbeitung

| Szenario | Klassisch (Designer/Agentur) | KI-Editing | Zeitersparnis |
|----------|------------------------------|-----------|---------------|
| **Hintergrund entfernen (1 Bild)** | 15–50 € (Freelancer) | 0–2 € + 2 Min | 30 Min → 2 Min |
| **5 Saisonvarianten einer Filiale** | 1.500–3.000 € (5 Shootings) oder 500–1.000 € (Photoshop) | 5–15 € + 30 Min Editing | Wochen → 30 Minuten |
| **Person entfernen / Datenschutz** | 30–80 € pro Bild | 0–2 € + 3 Min | 1 Stunde → 3 Minuten |
| **Kampagnen-Lokalisierung (5 Städte)** | 2.000–5.000 € (Komposit-Arbeit) | 10–30 € + 1h | 1–2 Wochen → 1 Stunde |
| **Style Transfer (10 Bilder, ein Stil)** | 500–1.500 € (Illustrator) | 10–20 € + 1h | 3–5 Tage → 1 Stunde |
| **Produktfoto extrahieren + neu inszenieren** | 80–200 € pro Bild | 2–5 € + 10 Min | Halber Tag → 10 Minuten |
| **Vorstandspräsentation aufwerten (20 Slides)** | 1.000–3.000 € (Design-Agentur) | 20–50 € + 3h | 1 Woche → halber Tag |

**Die ehrliche Rechnung:** Für Routine-Editing (Hintergrund entfernen, Farben anpassen, Objekte entfernen) ist KI 10–50× schneller und günstiger. Für Feinarbeit (exakte Marken-Compliance, druckfertige Qualität, rechtssichere Bearbeitung) brauchen Sie weiterhin professionelle Designer — aber die starten jetzt von einem **viel weiter fortgeschrittenen Ausgangspunkt**.

---

## End-to-End: Die Bildbearbeitungs-Pipeline

```
┌──────────────────────────────────────────────────────────────────┐
│        VOM VORHANDENEN BILD ZUM FERTIGEN ERGEBNIS                │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. ZIEL DEFINIEREN ────── Was soll das Bild am Ende zeigen?    │
│     │                      Für welchen Kanal? Welches Format?    │
│     ▼                                                            │
│  2. TECHNIK WÄHLEN ─────── Welches Problem lösen Sie?           │
│     │   Objekt entfernen → Inpainting                           │
│     │   Format anpassen → Outpainting                           │
│     │   Stil ändern → Style Transfer                            │
│     │   Szene transformieren → Beleuchtung/Wetter               │
│     │   Elemente kombinieren → Multi-Image Compositing          │
│     ▼                                                            │
│  3. MODELL WÄHLEN ──────── Je nach Aufgabe (Tabelle oben)      │
│     │   Konversationell → GPT Image 1.5 / Gemini               │
│     │   Pixel-präzise → Adobe Firefly / Photoshop               │
│     │   Batch-Verarbeitung → GPT Image 1.5 API                 │
│     ▼                                                            │
│  4. ITERATIV BEARBEITEN ── Eine Änderung pro Runde!            │
│     │   → Änderung beschreiben                                  │
│     │   → Ergebnis prüfen                                       │
│     │   → Nächste Änderung ODER Korrektur                       │
│     │   → Anti-Drift-Formel bei jeder Runde                    │
│     ▼                                                            │
│  5. QUALITÄTSKONTROLLE ── Prüf-Checkliste:                     │
│     │   ☐ Gewünschte Änderung korrekt umgesetzt?               │
│     │   ☐ Keine unbeabsichtigten Änderungen (Drift)?           │
│     │   ☐ Text noch korrekt? (falls vorhanden)                  │
│     │   ☐ Gesichter/Identitäten unverändert?                   │
│     │   ☐ Keine sichtbaren Artefakte?                           │
│     │   ☐ Auflösung für Zielmedium ausreichend?                │
│     ▼                                                            │
│  6. COMPLIANCE-CHECK ────── Bank-spezifisch:                    │
│     │   ☐ Datenschutz: Keine erkennbaren Personen ohne         │
│     │     Einwilligung?                                          │
│     │   ☐ Keine Täuschung: Bild stellt reale Verhältnisse     │
│     │     korrekt dar?                                           │
│     │   ☐ Kennzeichnung: Als „KI-bearbeitet" markiert?         │
│     │   ☐ Bildrechte: Bearbeitung durch Lizenz gedeckt?        │
│     ▼                                                            │
│  7. EXPORT & FINALISIEREN ── Format-gerecht exportieren        │
│                              (PNG/JPG, Auflösung, Farbprofil)  │
│                              Ggf. Text/Logo im Design-Tool     │
│                              finalisieren                       │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Konversationelles Editing in 3 Runden

Suchen Sie ein beliebiges Foto auf Ihrem Handy — ein Urlaubsfoto, ein Bürobild, ein Landschaftsfoto. Laden Sie es in **ChatGPT** oder **Gemini** hoch und führen Sie drei Editing-Runden durch:

**Wo tippe ich das ein?** Öffnen Sie [ChatGPT](https://chat.openai.com) oder [Gemini](https://gemini.google.com). Klicken Sie auf das Büroklammer-/Bild-Symbol, um Ihr Foto hochzuladen. Tippen Sie dann Ihre Anweisungen.

**Runde 1:** Entfernen Sie etwas aus dem Bild.
```
Remove [das störende Element] from this photo.
Keep everything else exactly the same.
```

**Runde 2:** Ändern Sie die Stimmung.
```
Now change the lighting to [golden hour / moody evening / 
bright morning]. Keep the previous edit.
```

**Runde 3:** Fügen Sie etwas hinzu.
```
Add [ein Element, z.B. Schnee, Blumen, ein Schild] 
to the scene. Keep all previous edits intact.
```

**Beobachten Sie:**
- Wie gut erkennt das Modell, WAS entfernt werden soll (ohne Maske)?
- Wie realistisch ist die Stimmungsänderung?
- Hat sich etwas verändert, worum Sie NICHT gebeten haben? (Drift!)
- Wie natürlich wirkt das hinzugefügte Element?

### Hands-on 2: Style Transfer — Ein Foto, drei Stile

Nehmen Sie dasselbe Foto und erstellen Sie drei Stilvarianten:

**Variante A — Aquarell:**
```
Transform this photo into a soft watercolor painting.
Visible brushstrokes, slightly desaturated warm colors.
Keep the composition and content accurate.
```

**Variante B — Retro/Vintage:**
```
Transform this photo into a 1970s vintage photograph.
Faded colors, warm yellow cast, subtle film grain,
slightly soft focus, rounded vignette.
```

**Variante C — Minimalistisch/Illustration:**
```
Transform this photo into a flat, minimalist illustration.
Simplified shapes, limited color palette (max 5 colors),
clean lines, geometric style. Like a modern poster design.
```

**Vergleichen Sie:**
- Bleibt die Grundstruktur des Bildes in allen drei Varianten erkennbar?
- Welcher Stil hat das Original am stärksten verändert?
- Welche Variante würden Sie für einen LinkedIn-Post verwenden?
- Gibt es Artefakte oder unnatürlich wirkende Bereiche?

### Hands-on 3: Der Modellvergleich (Pflicht!)

Nehmen Sie ein Foto und geben Sie **beiden** Tools (ChatGPT UND Gemini) dieselbe Editing-Anweisung:

```
Remove the background from this photo and replace it 
with a clean, modern office interior.
Keep the person in the foreground exactly as they are —
same face, clothing, pose, lighting on the person.
The office background should have natural lighting 
that matches the person's lighting direction.
```

**Vergleichen Sie:**
- Welches Modell hat den Freisteller sauberer gemacht (Haare, Kanten)?
- Welcher Hintergrund wirkt realistischer?
- Stimmt die Beleuchtungsrichtung (Licht auf Person = Licht im Büro)?
- Hat sich das Gesicht der Person verändert?
- Welches Ergebnis würden Sie für ein Mitarbeiterporträt auf der Website verwenden?

---

## Zusammenfassung: Das Wichtigste auf einen Blick

| Was Sie gelernt haben | Kernaussage |
|-----------------------|-------------|
| **5 Kern-Techniken** | Inpainting (ersetzen), Outpainting (erweitern), Style Transfer (umstilisieren), Szenen-Transformation (Beleuchtung/Wetter), Compositing (kombinieren) |
| **Konversationelles Editing** | Bilder bearbeiten wie im Gespräch — eine Änderung pro Runde, schrittweise zum perfekten Ergebnis |
| **Drift ist der Feind** | Über mehrere Runden ändern sich unbeabsichtigt Details. Gegenmittel: Explizit sagen, was gleich bleiben muss |
| **Input Fidelity** | Hohe Fidelity = minimale Änderung (Korrektur). Niedrige Fidelity = starke Neuinterpretation (Restyling) |
| **Modellwahl entscheidet** | GPT Image 1.5 = konversationell + Multi-Image-Champion. Gemini = stark bei Layout. Firefly = pixelgenaue Kontrolle |
| **Anti-Drift-Formel** | Bei JEDER Runde: [Gewünschte Änderung] + „PRESERVE EXACTLY: [alles, was gleich bleiben muss]" |
| **Hybrides Arbeiten** | KI für die Hauptarbeit, Design-Tool für Feinschliff — genau wie in Tutorial 03-03 |
| **Compliance beachten** | Datenschutz (keine Kundenfotos in Cloud-KI), Kennzeichnung (KI-bearbeitet), Bildrechte (Lizenzen prüfen) |
| **ROI ist enorm** | 5 Saisonvarianten: Agentur 3.000 € vs. KI-Editing 15 € + 30 Min. Person entfernen: 80 € vs. 2 Min |
| **Grenze bei 5-7 Runden** | Danach: Artefakte möglich. Beste Version exportieren und frisch starten |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---------------------------|--------------------------------|
| **Konversationelles Editing** | Anwendung der iterativen Prompt-Technik aus Kapitel 01, Tutorial 04 (Fortgeschrittene Techniken) — diesmal auf Bilder statt auf Text |
| **Input Fidelity** | Parallele zu Temperature/Creativity-Steuerung aus Kapitel 01, Tutorial 02 (KI-Ausgaben steuern) — wie stark darf das Modell „kreativ" werden? |
| **Anti-Drift-Formel** | Erweiterung des Constraint-Prinzips aus Kapitel 02, Tutorial 04 (Komplexe Architekturen) — explizite Invarianten definieren |
| **Hybrides Arbeiten** | Vertieft den hybriden Workflow aus Kapitel 03, Tutorial 03 — KI + Design-Tool als Standard-Pipeline |
| **5-Schichten-Prompt für Edits** | Spezialisierung des 6-Bausteine-Frameworks aus Kapitel 03, Tutorial 01 — angepasst an Bearbeitungsaufgaben |
| **Modellvergleich bei Editing** | Fortsetzung der Modellvergleiche aus Kapitel 03, Tutorial 01 und 02 — jetzt mit Fokus auf Editing-Stärken |
| **Compliance und Datenschutz** | Vertieft die ethischen Aspekte aus Kapitel 01, Tutorial 03 (Halluzinationen und Bias) + Kapitel 03, Tutorial 03 (Bank-spezifische Risiken) |
| **Multi-Image Compositing** | Parallele zu Multi-Step-Pipelines aus Kapitel 02, Tutorial 04 — mehrere Inputs zu einem kohärenten Output verbinden |

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Image-to-Image (I2I)** | Oberbegriff für alle KI-Techniken, bei denen ein bestehendes Bild als Eingabe dient und ein verändertes Bild als Ausgabe entsteht |
| **Inpainting** | Gezieltes Ersetzen eines Bildbereichs — entweder durch manuelles Maskieren oder durch natürlichsprachliche Beschreibung. „Fülle diesen Bereich mit etwas Neuem" |
| **Outpainting** | Erweiterung eines Bildes über seine ursprünglichen Ränder hinaus. Die KI generiert neue Bildbereiche, die nahtlos zum bestehenden Inhalt passen |
| **Style Transfer** | Übertragung des visuellen Stils (Farben, Texturen, Pinselduktus) von einem Referenzbild auf ein anderes, wobei der Inhalt erhalten bleibt |
| **Compositing** | Das Zusammensetzen mehrerer Bilder oder Bildelemente zu einem einzigen, kohärenten Bild — wie eine digitale Fotomontage |
| **Konversationelles Editing** | Bildbearbeitung in einem Chat-Dialog: Sie beschreiben Änderungen in natürlicher Sprache, Runde für Runde, statt einen einzigen perfekten Prompt zu formulieren |
| **Drift** | Unbeabsichtigte, schrittweise Veränderung von Bilddetails (Gesicht, Farben, Proportionen) über mehrere Bearbeitungsrunden hinweg — das Bild „driftet" vom Original weg |
| **Input Fidelity** | Parameter, der steuert, wie stark das Modell am Originalbild festhält. Hohe Fidelity = minimale Änderung, niedrige Fidelity = starke Neuinterpretation |
| **Identity Preservation** | Die Fähigkeit des Modells, bei der Bildbearbeitung die Identität einer Person (Gesichtszüge, Proportionen, Ausdruck) über mehrere Runden hinweg beizubehalten |
| **Maske / Maskierung** | Ein Schwarz-Weiß-Bild, das definiert, welcher Bereich des Originalbilds bearbeitet werden soll (weiß = bearbeiten, schwarz = unverändert lassen) |
| **Turn-basiertes Editing** | Anderer Name für konversationelles Editing — betont die „Runden"-Struktur: Sie machen einen Zug, das Modell antwortet, Sie reagieren |
| **Artefakt** | Sichtbare Fehler im generierten/bearbeiteten Bild — z.B. unscharfe Ränder, unnatürliche Texturen, verzerrte Proportionen oder „geisterhaft" durchscheinende entfernte Objekte |
| **Batch-Processing** | Automatisierte Massenverarbeitung — z.B. dieselbe Bearbeitungsanweisung auf 50 Bilder gleichzeitig anwenden, typischerweise über eine API |
| **SynthID** | Googles digitales Wasserzeichen-System für KI-generierte Bilder. Unsichtbar im Bild, aber maschinenlesbar — auch nach Beschnitt oder Komprimierung |
| **Generative Fill** | Adobes Markenname für KI-basiertes Inpainting in Photoshop. Nutzt Firefly-Modelle und funktioniert über manuelles Maskieren + Textbeschreibung |
| **RGBA / Transparenz** | Bildformat mit Transparenz-Kanal (Alpha). RGB = Rot-Grün-Blau (Farbe), A = Alpha (Durchsichtigkeit). Wird für Freisteller und Compositing benötigt |
| **Content-Aware** | Photoshop-Funktion, die beim Entfernen oder Füllen von Bildbereichen den umgebenden Inhalt „versteht" und passend ergänzt — der Vorläufer von KI-Inpainting |

---

