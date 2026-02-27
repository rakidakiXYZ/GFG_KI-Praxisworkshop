# Prompt-Vorlagen: Bilder für den Bankalltag

**Der Werkzeugkasten — fertige Copy-Paste-Vorlagen für Social Media, Präsentationen, Recruiting, Geschäftsberichte und Filial-Visualisierung**

---

## Warum dieses Tutorial?

In den letzten vier Tutorials haben Sie das gesamte Handwerkszeug gelernt: die Modelllandschaft (03-01), Fotorealismus (03-02), Text und Grafikdesign (03-03), Bildbearbeitung und iteratives Verfeinern (03-04). Sie kennen jetzt die Theorie, die Stellschrauben, die goldenen Regeln.

Aber Hand aufs Herz: Im Alltag haben Sie keine 20 Minuten, um einen perfekten Prompt von Grund auf zu konstruieren. Sie sitzen in der Filiale, die Marketing-Kollegin braucht bis morgen ein Social-Media-Bild für die Baufinanzierungsaktion, der Vorstand will eine ansprechende Folie für die Verbandspräsentation, und HR hat gerade festgestellt, dass die Recruiting-Anzeigen von 2019 nicht mehr zeitgemäß sind.

**Dieses Tutorial ist Ihr Werkzeugkasten.** Sie finden hier fertige Prompt-Vorlagen, die Sie **kopieren, anpassen und sofort verwenden** können. Jede Vorlage ist so gebaut, dass sie die Prinzipien aus Kapitel 03, Tutorial 01–04 anwendet — ohne dass Sie jedes Mal von vorne denken müssen.

**Was Sie nach diesem Tutorial haben werden:**

- 25+ sofort einsetzbare Prompt-Vorlagen für typische Bank-Aufgaben
- Vorlagen für 5 Kernbereiche: Social Media, Präsentationen, Recruiting, Geschäftsberichte, Filial-Visualisierung
- Ein Anpassungs-System: Wie Sie jede Vorlage in 60 Sekunden auf Ihre Bank zuschneiden
- Eine Entscheidungshilfe: Welche Vorlage für welchen Anlass?
- Dos und Don'ts: Was bei Vorlagen schiefgehen kann — und wie Sie es vermeiden

---

## Bevor Sie loslegen: Das Anpassungs-System

Jede Vorlage in diesem Tutorial enthält **Platzhalter** in eckigen Klammern — `[Ihre Bank]`, `[Produkt]`, `[Farbe]`. Diese ersetzen Sie durch Ihre konkreten Werte.

### Die 5 Standard-Variablen

| Variable | Erklärung | Beispiel |
|----------|-----------|---------|
| `[BANK]` | Name Ihrer Bank | Volksbank Hellweg eG |
| `[FARBE_PRIMÄR]` | Ihre primäre Markenfarbe | #003399 (Dunkelblau) |
| `[FARBE_SEKUNDÄR]` | Ihre sekundäre Markenfarbe | #FF6600 (Orange) |
| `[PRODUKT]` | Das beworbene Produkt/Thema | Baufinanzierung, Girokonto, Altersvorsorge |
| `[ZIELGRUPPE]` | An wen richtet sich das Bild? | Junge Erwachsene, Familien, Senioren, Geschäftskunden |

### Wie Sie jede Vorlage anpassen

```
┌──────────────────────────────────────────────────────────────────┐
│           DAS ANPASSUNGS-SYSTEM IN 60 SEKUNDEN                   │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  SCHRITT 1: Vorlage kopieren (Copy-Paste)                       │
│     │                                                            │
│  SCHRITT 2: Platzhalter ersetzen                                │
│     │        [BANK] → „Volksbank Hellweg eG"                    │
│     │        [PRODUKT] → „Baufinanzierung"                      │
│     │        [FARBE_PRIMÄR] → „dark blue #003399"               │
│     ▼                                                            │
│  SCHRITT 3: Optional — Stil anpassen                            │
│     │        „warm and inviting" → „modern and dynamic"         │
│     ▼                                                            │
│  SCHRITT 4: Generieren → Prüfen → ggf. iterieren               │
│             (Konversationelles Editing, Kapitel 03, Tutorial 04) │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** Denken Sie an Vertragsvorlagen: Kein Berater schreibt jeden Kreditvertrag von Grund auf neu. Er nimmt die Vorlage, füllt die individuellen Daten ein und passt bei Bedarf eine Klausel an. Genauso funktionieren diese Prompt-Vorlagen — die Struktur steht, Sie füllen nur noch Ihre Daten ein.

---

## Bereich 1: Social Media — Posts und Kampagnen-Visuals

Social Media ist der häufigste Anwendungsfall für KI-Bilder in Banken. Sie brauchen regelmäßig frische Visuals — aber nicht jedes Mal eine Agentur.

### Die Formate auf einen Blick

| Plattform | Format | Seitenverhältnis | Empfohlenes Modell |
|-----------|--------|-------------------|-------------------|
| **Instagram Post** | Quadrat | 1:1 (1080×1080 px) | GPT Image 1.5, Ideogram 3.0 |
| **Instagram Story / Reels** | Hochformat | 9:16 (1080×1920 px) | GPT Image 1.5, Gemini 3 Pro |
| **LinkedIn Post** | Querformat | 1.91:1 (1200×628 px) | GPT Image 1.5, Ideogram 3.0 |
| **Facebook Post** | Querformat | 16:9 (1200×675 px) | GPT Image 1.5, Gemini 3 Pro |
| **X (Twitter) Post** | Querformat | 16:9 (1600×900 px) | GPT Image 1.5 |

### Vorlage SM-01: Produkt-Ankündigung (Instagram/Facebook)

**Wann verwenden:** Neues Produkt, Aktionszins, Sonderkonditionen

```
Create a professional social media post image 
in square format (1:1 ratio).

SUBJECT: A [ZIELGRUPPE]-appropriate scene that 
represents [PRODUKT] — for example, [konkrete Szene: 
a young couple looking at a house / a family at the 
breakfast table / a person checking their phone].

STYLE: Clean, modern, approachable. 
Bright and optimistic lighting.
Color accent: [FARBE_PRIMÄR].
The overall mood should feel trustworthy and warm,
not corporate or cold.

TEXT IN IMAGE: "[HEADLINE — max 5 Wörter]"
Place the text in the upper third of the image.
Font: bold, sans-serif, white with subtle drop shadow.
Below the headline, smaller: "[SUBLINE — max 8 Wörter]"

COMPOSITION: Leave clean space in the bottom third 
for a logo overlay (will be added in post-production).
No visible brand logos in the generated image.

IMPORTANT: 
- The image must look like a professional marketing visual,
  not a stock photo
- No text errors — spell every word exactly as given above
- Photorealistic people with natural skin textures 
  and authentic expressions
```

**Beispiel-Ausfüllung:**
```
SUBJECT: A young couple in their late 20s standing 
in front of a charming suburban house, looking happy 
and excited, holding a set of keys.
TEXT IN IMAGE: "Ihr Eigenheim wartet"
Below: "Baufinanzierung ab 2,9 % effektiv"
```

### Vorlage SM-02: Wissens-Post / Finanz-Tipp (LinkedIn/Instagram)

**Wann verwenden:** Finanztipps, Erklär-Content, Thought Leadership

```
Create an informational social media graphic 
in [1:1 / 1.91:1] format.

LAYOUT: Split design — 
Left side (40%): A simple, elegant illustration or icon 
representing [THEMA — z.B. savings, investment, security].
Style: flat design, line art, or soft 3D render.
Color: [FARBE_PRIMÄR] as dominant color.

Right side (60%): Clean space for text overlay.
Background: Light grey (#F5F5F5) or white.

TEXT IN IMAGE: 
Headline: "[TIPP-HEADLINE — max 6 Wörter]"
Bold, [FARBE_PRIMÄR], large font.

Body text (3 bullet points):
"✓ [Punkt 1 — max 6 Wörter]"
"✓ [Punkt 2 — max 6 Wörter]"
"✓ [Punkt 3 — max 6 Wörter]"
Regular weight, dark grey (#333333).

STYLE: Professional, editorial, like a premium 
finance magazine layout. Not playful, not corporate 
— sophisticated.

IMPORTANT: Every single character must be spelled 
exactly as given. No abbreviations, no rewording.
```

### Vorlage SM-03: Saisonale Kampagne (alle Plattformen)

**Wann verwenden:** Weihnachten, Ostern, Sommerfest, Weltspartag, Jubiläum

```
Create a seasonal campaign image for [ANLASS] 
in [FORMAT — z.B. 1:1 for Instagram, 16:9 for Facebook].

SCENE: [SAISONALE SZENE — z.B.:
- Winter: A cozy bank branch entrance with warm light, 
  fresh snow, and a small Christmas tree
- Spring: A bright, flower-decorated branch with 
  open doors and sunlight streaming in
- Autumn: A golden-hued park scene with a family 
  walking toward a modern bank building]

ATMOSPHERE: [STIMMUNG — z.B. warm and festive / 
bright and fresh / golden and contemplative].
Lighting: [BELEUCHTUNG — z.B. warm golden hour / 
soft diffuse daylight / cozy evening with window glow].

TEXT IN IMAGE: "[KAMPAGNEN-HEADLINE]"
Position: [oben / mittig / unten].
Font style: [elegant serif / bold sans-serif / 
handwritten script].
Color: White with subtle shadow for readability.

COLOR PALETTE: [FARBE_PRIMÄR] as accent color 
integrated into the scene (e.g., on a banner, 
door frame, or decoration).

IMPORTANT:
- Photorealistic quality (see Kapitel 03, Tutorial 02)
- No recognizable real people (privacy)
- Text must be spelled exactly as provided
- Leave space for logo placement
```

### Vorlage SM-04: Event-Ankündigung

**Wann verwenden:** Finanz-Abend, Infoabend Baufinanzierung, Tag der offenen Tür, Vereinsförderung

```
Create an event announcement graphic in [FORMAT].

VISUAL: A [SZENE — z.B. modern conference room 
with warm lighting / outdoor summer event with 
string lights / a cozy seminar setting with 
a presenter and small audience].

The scene should feel inviting and accessible, 
not corporate or sterile.

TEXT IN IMAGE:
Line 1 (small, uppercase): "[KATEGORIE — z.B. 
EINLADUNG / INFOABEND / WORKSHOP]"
Line 2 (large, bold): "[EVENT-TITEL]"
Line 3 (medium): "[DATUM + UHRZEIT]"
Line 4 (small): "[ORT]"

Text alignment: centered.
Text area: dark overlay gradient at bottom (30% 
of image), text in white.

STYLE: Warm, professional, approachable.
Photography-quality background with text overlay.
Color accent: [FARBE_PRIMÄR] for a thin line or 
border element.
```

### Vorlage SM-05: Mitarbeiter-Spotlight / Behind the Scenes

**Wann verwenden:** Mitarbeitervorstellung, Teamkultur, Employer Branding auf Social Media

```
Create a warm, authentic-looking workplace portrait scene.

SCENE: A [BERUF — z.B. bank advisor / branch manager / 
IT specialist] in a modern bank office setting.
The person should be [BESCHREIBUNG — z.B. mid-30s, 
friendly smile, business casual clothing].

IMPORTANT: Generate a FICTIONAL person. 
Do NOT base the face on any real individual.
The person should look natural and relatable, 
not like a stock photo model.

POSE: Natural and relaxed — [z.B. sitting at a desk 
with a laptop, standing near a window, having a 
conversation with a colleague in the background].

LIGHTING: Soft, natural window light. Warm color 
temperature. Slight depth-of-field effect 
(background slightly blurred).

COMPOSITION: Portrait orientation or 4:5.
Person fills about 60% of the frame.
Background: Modern, clean office with plants 
or wooden accents — warm, not sterile.

TEXT IN IMAGE (optional):
Small text at bottom: "[NAME] | [POSITION]"
[FARBE_PRIMÄR] accent bar behind the text.
```

> **Volksbank-Analogie:** Diese Vorlagen sind wie Ihre Beratungsleitfäden für verschiedene Produkte: Sie gehen nicht ohne Struktur ins Gespräch, aber Sie lesen auch nicht stur vom Blatt ab. Die Vorlage gibt Ihnen den roten Faden — die individuelle Anpassung kommt von Ihnen.

---

## Bereich 2: Präsentationen — Folien-Visuals und Hintergrundbilder

Vorstandspräsentationen, Verbandstagungen, interne Meetings — überall werden Folien gezeigt. Und überall sehen sie gleich aus: Bullet Points auf weißem Grund, vielleicht ein Stockfoto aus 2017. Das ändern wir jetzt.

### Vorlage PR-01: Titelfolie / Keynote-Opener

**Wann verwenden:** Erste Folie einer wichtigen Präsentation

```
Create a widescreen presentation title slide background 
(16:9 ratio, 1920×1080 px).

VISUAL: A [METAPHER — z.B.:
- "digital transformation": Abstract light streams 
  flowing through a modern glass building
- "growth": A tree growing from a circuit board, 
  organic meets digital
- "security": A shield made of light, protecting 
  a city skyline
- "community": An aerial view of people forming 
  a connected network pattern].

STYLE: Premium, cinematic, slightly abstract.
Color palette: [FARBE_PRIMÄR] dominant, 
with accents of [FARBE_SEKUNDÄR] and white.
Dark background (deep blue or dark grey) 
for high contrast with white text.

COMPOSITION: The visual should be concentrated 
on the RIGHT SIDE (60%) of the image.
The LEFT SIDE (40%) must be a clean dark gradient — 
this is where the presentation title will be placed.

LIGHTING: Dramatic, with a bright focal point 
that draws the eye to the center-right area.
Subtle lens flare or light bloom allowed.

IMPORTANT:
- NO text in the image — text will be added 
  in PowerPoint/Keynote
- No people, no logos
- Must work at 1920×1080 without visible artifacts
- Should look like a premium corporate keynote, 
  not a template from 2015
```

### Vorlage PR-02: Kapitel-Trenner / Section Divider

**Wann verwenden:** Zwischen den Hauptabschnitten einer Präsentation

```
Create a presentation section divider slide background 
(16:9, 1920×1080 px).

VISUAL: A subtle, abstract background with 
[THEMA-BEZUG — z.B.:
- "Finanzen": Soft geometric patterns evoking 
  growth charts or data flows
- "Kunden": Warm, blurred background of a modern 
  bright space with natural light
- "Digitalisierung": Clean lines and nodes forming 
  a minimal network pattern
- "Region": Soft aerial/landscape view with 
  tilt-shift effect].

STYLE: Minimalist, elegant, not distracting.
The background should SUPPORT text, not compete with it.
Color palette: [FARBE_PRIMÄR] at 20% opacity as tint, 
overall muted and sophisticated.

COMPOSITION: Even distribution. 
A clean horizontal band across the center 
(slightly lighter or with a frosted-glass effect) 
where the section title will be placed.

IMPORTANT:
- NO text, NO logos, NO people
- Must be subtle enough that white or dark text 
  is clearly readable on top
- Consistent style with PR-01 (same color family)
```

### Vorlage PR-03: Daten-Visualisierungs-Hintergrund

**Wann verwenden:** Folien mit Diagrammen, Zahlen, KPIs

```
Create a clean, professional background for a data 
visualization slide (16:9, 1920×1080 px).

VISUAL: Abstract, minimal — [z.B.:
- Soft gradient from [FARBE_PRIMÄR] (dark, top-left) 
  to white (bottom-right)
- Subtle dot grid pattern at 10% opacity
- Very faint geometric lines suggesting data flow 
  or connections].

The background must be EXTREMELY subtle. 
Charts and numbers will be placed on top — 
the background must not interfere with readability.

COLOR: Predominantly white/light grey (#F8F9FA) 
with a hint of [FARBE_PRIMÄR] as accent.
No bright colors, no gradients that could be 
confused with chart colors.

IMPORTANT:
- NO text, NO icons, NO logos
- Must look clean when printed in grayscale
- Resolution: 1920×1080, artifact-free
```

### Vorlage PR-04: Konzept-Illustration für eine Folie

**Wann verwenden:** Wenn Sie ein abstraktes Konzept visuell darstellen wollen

```
Create a concept illustration for a presentation slide.

CONCEPT: [KONZEPT — z.B.:
- "Customer journey": A winding path from left to right 
  with 5 milestone markers, each a small icon 
  (handshake, document, key, house, happy face)
- "Digital ecosystem": Interconnected circles/nodes 
  with small icons (phone, cloud, lock, people, chart)
- "Risk management": A balance scale with different 
  risk factors as visual weights
- "Regional network": A simplified map with connection 
  lines between 5-7 locations].

STYLE: Flat design illustration, clean and modern.
Color palette: [FARBE_PRIMÄR], [FARBE_SEKUNDÄR], 
and 2 neutral tones (light grey, medium grey).
White or very light background.

COMPOSITION: Landscape orientation. 
The illustration should be horizontally balanced 
and leave space above and below for text.

IMPORTANT:
- No photorealism — this should look like a 
  professionally designed infographic element
- Clean lines, no gradients within shapes
- If any text labels are needed, use ONLY 
  single words: [Wort1], [Wort2], [Wort3]...
- Every label must be spelled exactly as given
```

> **Volksbank-Analogie:** Gute Präsentationsbilder sind wie das Ambiente in Ihrer Filiale: Sie fallen nicht auf, aber sie machen den Unterschied zwischen „professionell" und „zusammengeschustert". Niemand sagt: „Toll, die Beleuchtung im Beratungszimmer!" — aber in einem schlecht beleuchteten Raum fühlt sich kein Kunde wohl.

---

## Bereich 3: Recruiting — Stellenanzeigen und Employer Branding

Der Fachkräftemangel trifft Banken hart. Gute Recruiting-Visuals können den Unterschied machen zwischen einer Bewerbung und einem Scroll-weiter. Die Zeiten generischer Stockfotos mit aufgesetztem Lächeln sind vorbei.

### Vorlage REC-01: Stellenanzeige — Hero Image

**Wann verwenden:** Hauptbild für eine Stellenanzeige (Karriereseite, Indeed, StepStone, LinkedIn)

```
Create a recruiting hero image for a bank job posting.

SCENE: A modern, bright bank workspace showing 
[SZENARIO — z.B.:
- "Kundenberatung": Two people in a warm consultation 
  room, one explaining something on a tablet
- "IT / Digital": A person at a standing desk 
  with multiple monitors, modern tech office
- "Filialleitung": A confident person walking through 
  a modern bank branch, team visible in background
- "Ausbildung": A young person being mentored by 
  a senior colleague, both smiling genuinely].

PEOPLE: FICTIONAL characters only. 
[DIVERSITÄT — z.B. diverse team: mixed ages 
(25-55), mixed genders, inclusive representation].
Natural expressions — engaged, not posing.
Business casual clothing (no suits, no ties — 
modern and approachable).

ENVIRONMENT: Modern bank interior — 
glass walls, wood accents, plants, natural light.
NOT a grey cubicle farm from 2005.
The workspace should feel like somewhere people 
WANT to work.

STYLE: Photorealistic, editorial quality.
Shot with an 35mm lens, f/2.8, natural window light.
Slight depth of field — background softly blurred.
Warm color temperature (not cold fluorescent).

FORMAT: Landscape, 16:9 (1200×675 px minimum).

COMPOSITION: Rule of thirds. Main subject slightly 
off-center. Space on one side for text overlay.

IMPORTANT:
- NO text in the image (text added separately)
- People must look authentic, not like models
- No visible bank logos or brand elements
- Must comply with anti-discrimination guidelines:
  no stereotype-reinforcing imagery
```

### Vorlage REC-02: „Wir sind anders"-Carousel (Instagram/LinkedIn)

**Wann verwenden:** Mehrteilige Recruiting-Kampagne, die Unternehmenskultur zeigt

```
Create image [X] of a 5-part employer branding carousel.

THIS IMAGE'S THEME: [THEMA — z.B.:
1. "Teamwork": Three colleagues brainstorming at a 
   whiteboard with colorful sticky notes
2. "Work-Life-Balance": Person leaving a modern office 
   at sunset, bike visible
3. "Innovation": Team testing a new app on tablets, 
   excited expressions
4. "Community": Bank employees at a local charity event, 
   outdoor setting
5. "Growth": Person presenting confidently to a small 
   group, modern meeting room].

CONSISTENT STYLE ACROSS ALL 5 IMAGES:
- Same color grading: warm, slightly desaturated, 
  editorial photography look
- Same lighting quality: natural light, warm tone
- Same camera perspective: eye-level, 35mm lens feel
- Color accent: [FARBE_PRIMÄR] appears naturally 
  in each scene (a notebook, a wall accent, clothing)

FORMAT: Square (1:1) for carousel.

TEXT IN IMAGE: None — text will be added as overlay.

IMPORTANT:
- All people must be FICTIONAL (AI-generated)
- Consistent visual language across all 5 images
- Each image works standalone but also as a series
- Modern, aspirational, authentic — not corporate cringe
```

### Vorlage REC-03: Ausbildungsstart / Willkommen

**Wann verwenden:** Social-Media-Post zum Ausbildungsstart, Willkommens-Grafik

```
Create a welcoming graphic for new apprentices 
starting at a bank.

SCENE: A bright, modern bank lobby or training room.
A group of [ANZAHL] young people (ages 18-22) 
in smart casual clothing, looking excited and confident.
One person holds a welcome gift bag. 
Natural, candid-style composition — not a posed 
group photo.

ATMOSPHERE: Energetic, positive, first-day excitement.
Bright natural light, modern interior.
Small decorative elements suggesting celebration 
(e.g., a small balloon arrangement or confetti 
on a table — subtle, not a children's party).

TEXT IN IMAGE:
"Willkommen im Team!" — large, bold, [FARBE_PRIMÄR].
Below: "[BANK] Ausbildungsstart [JAHR]" — 
smaller, dark grey.

STYLE: Photorealistic, warm, youthful.
Like a high-quality Instagram post from a 
modern company's social media team.

FORMAT: 4:5 (Instagram) or 1:1.
```

---

## Bereich 4: Geschäftsberichte und Unternehmenskommunikation

Geschäftsberichte, Verbandspräsentationen, Jahresrückblicke — hier geht es um Seriosität, nicht um Likes. Die Bilder müssen professionell wirken, zur Corporate Identity passen und dürfen auf keinen Fall nach „KI-generiert" aussehen.

### Vorlage GB-01: Kapitel-Illustration für Geschäftsbericht

**Wann verwenden:** Stimmungsbilder für Kapitelseiten im Geschäftsbericht oder Jahresrückblick

```
Create an elegant, editorial-style illustration 
for a chapter page in a bank's annual report.

CHAPTER THEME: [THEMA — z.B.:
- "Nachhaltigkeit": An abstract landscape blending 
  nature and modern architecture — green hills 
  flowing into a clean glass building
- "Digitalisierung": Ethereal light streams passing 
  through geometric structures, suggesting connectivity
- "Mitarbeiter": Warm, impressionistic scene of 
  people in conversation, slightly abstracted
- "Region": Aerial-style view of a rural/suburban 
  landscape with a river, fields, and a small town
- "Finanzergebnis": Abstract golden geometric shapes 
  suggesting growth and stability].

STYLE: [STIL-WAHL:
- Option A: "Sophisticated photography" — photorealistic 
  but with artistic composition, like a premium 
  magazine editorial
- Option B: "Watercolor illustration" — soft, 
  hand-painted look with visible brushstrokes, 
  desaturated palette
- Option C: "Minimalist graphic" — clean geometric 
  shapes, limited color palette (max 4 colors), 
  flat design].

COLOR PALETTE: [FARBE_PRIMÄR] as base, 
complemented by [1-2 ZUSATZFARBEN].
Overall: Muted, sophisticated, not vibrant.

FORMAT: Full page (A4 portrait, ~2480×3508 px) 
or double-page spread (A3 landscape).

COMPOSITION: Leave generous white/light space 
at the top or bottom for chapter title placement.

IMPORTANT:
- No text in the image
- If people appear: NOT recognizable as real individuals
- Must print cleanly at 300 DPI
- Must look deliberately artistic, not accidentally vague
- Consistent style if you create multiple chapter images —
  describe the style system upfront and reference it
```

### Vorlage GB-02: Infografik-Basisgrafik

**Wann verwenden:** Visuelle Elemente für Infografiken im Bericht (die Zahlen werden extern ergänzt)

```
Create a set of [ANZAHL] consistent icons/illustrations 
for an annual report infographic.

ICONS NEEDED:
1. [THEMA 1 — z.B. "Kunden": simplified group of people]
2. [THEMA 2 — z.B. "Einlagen": a safe or piggy bank]
3. [THEMA 3 — z.B. "Kredite": a house with a key]
4. [THEMA 4 — z.B. "Mitarbeiter": a person with a badge]
5. [THEMA 5 — z.B. "Filialen": a building facade]

STYLE: All icons in the SAME visual style:
[STIL — z.B.:
- "Line art": Single-weight outlines, no fill, 
  [FARBE_PRIMÄR] as line color
- "Flat design": Filled shapes, max 3 colors, 
  no gradients, no outlines
- "Soft 3D": Subtle shadows, rounded shapes, 
  pastel-toned, modern and friendly].

ARRANGEMENT: All [ANZAHL] icons in a single image, 
arranged in a horizontal row with equal spacing.
Each icon approximately 200×200 px within the composition.

BACKGROUND: Transparent (PNG) or white.

IMPORTANT:
- Consistent line weight / style across ALL icons
- No text labels (those are added separately)
- Simple enough to be recognizable at small sizes (50×50 px)
- Professional enough for a printed annual report
```

### Vorlage GB-03: Stimmungsbild für Unternehmensbericht-Cover

**Wann verwenden:** Coverbild des Geschäftsberichts oder einer Imagebroschüre

```
Create a premium cover image for a bank's annual report.

TITLE: "[TITEL — z.B. Geschäftsbericht 2025]" — 
but do NOT include this text in the image.
The text will be typeset professionally and overlaid.

VISUAL CONCEPT: [KONZEPT — z.B.:
- "Verbundenheit": An abstract aerial view of a 
  river delta merging multiple streams into one — 
  in [FARBE_PRIMÄR] tones. Metaphor: many streams, 
  one direction.
- "Wachstum": A single tree in golden light, 
  photographed from below against a blue sky. 
  Roots visible, strong trunk, wide crown.
- "Zukunft": A glass facade reflecting clouds 
  and sky, with subtle human silhouettes visible 
  inside — the boundary between inside and outside 
  dissolving.
- "Region": A panoramic view of [REGION], 
  shot at golden hour, with the bank building 
  subtly visible in the scene].

QUALITY: Premium photography or premium illustration.
This is the COVER — it must be exceptional.
Resolution: High enough for A4 print (300 DPI).

COLOR: Dominated by [FARBE_PRIMÄR].
Rich, deep tones. Not flat, not washed out.
The image should have visual depth and texture.

COMPOSITION: 
- Portrait format (A4 ratio)
- Upper third: lighter area for title placement
- Visual weight in the center and lower half
- No distracting edge elements (the image may be cropped)
```

> **Volksbank-Analogie:** Ein Geschäftsbericht-Visual ist wie das Gebäude Ihrer Hauptstelle: Es repräsentiert die Bank nach außen. Es darf nicht billig wirken, nicht überladen sein und nicht nach „schnell zusammengebaut" aussehen. Es soll Solidität und Modernität gleichzeitig ausstrahlen.

---

## Bereich 5: Filial-Visualisierung — Innenräume, Außenansichten und Umgestaltungsplanung

Filialen modernisieren, neue Konzepte visualisieren, Fotos für die Website aufbereiten — KI-Bildgenerierung kann hier enormen Wert schaffen, weil professionelle Architekturvisualisierung normalerweise tausende Euro kostet.

### Vorlage FIL-01: Filiale modernisieren (Konzeptvisualisierung)

**Wann verwenden:** Wenn Sie zeigen wollen, wie eine Filiale nach Umbau aussehen könnte

```
Image 1: [Aktuelles Foto der Filiale hochladen]

Transform this bank branch interior into a modern, 
redesigned version.

CHANGES:
- Replace old furniture with modern, minimalist pieces 
  (light wood, clean lines)
- Add a welcoming self-service zone with 2 modern 
  digital terminals
- Change lighting from fluorescent to warm LED 
  panel lights and accent spotlights
- Add indoor plants (1 large floor plant, 
  2-3 smaller desk plants)
- Replace the floor with light oak laminate
- Add a comfortable waiting area with 
  [ANZAHL] armchairs in [FARBE_PRIMÄR]
- Keep the general room layout and window positions

STYLE: Interior design visualization, photorealistic.
Like a render from an architecture firm.
Warm, inviting lighting (3500K color temperature).

KEEP UNCHANGED:
- Window positions and sizes
- General room dimensions and ceiling height
- Entrance location

IMPORTANT:
- This is a planning visualization — label it as such
- The result should look aspirational but achievable
- No people in the scene
```

### Vorlage FIL-02: Website-Foto aufbereiten (Bestehendes Bild verbessern)

**Wann verwenden:** Vorhandenes Filialbild für Website/Google Maps optimieren

```
Image 1: [Bestehendes Filialbild hochladen]

Enhance this bank branch photo for website use:

1. Remove all recognizable people (privacy compliance)
2. Improve the lighting — make it brighter and warmer, 
   as if shot during golden hour with professional 
   interior lighting
3. Remove any visual clutter (trash cans, cables, 
   temporary signage, construction elements)
4. Enhance colors slightly — more vibrant but 
   still natural
5. Straighten the perspective if tilted

KEEP UNCHANGED:
- Building architecture and layout
- Permanent signage and branding elements
- Furniture and fixtures (unless specified above)

OUTPUT: High resolution, landscape format.
The result should look like a professional 
architectural photograph.

IMPORTANT:
- Changes must be subtle and realistic
- Should NOT look obviously edited or "too perfect"
- This image will be used publicly — no hallucinated 
  elements that don't exist in real life (except for 
  removed people/clutter)
```

### Vorlage FIL-03: Saisonale Fassaden-Varianten

**Wann verwenden:** Filialbilder saisonal anpassen für Website, Social Media, Kampagnen

```
Image 1: [Foto der Filial-Außenansicht hochladen]

Create a [SAISON]-version of this bank building exterior.

[SAISON-SPEZIFISCH:
- FRÜHLING: Add blooming cherry trees, fresh green lawn, 
  bright blue sky with white clouds, flower planters 
  near the entrance
- SOMMER: Warm sunlight, deep blue sky, people-free 
  outdoor seating area, lush green surroundings
- HERBST: Golden-orange foliage on surrounding trees, 
  warm afternoon light, fallen leaves on the ground, 
  cozy atmosphere
- WINTER: Light snow on roof and surroundings, warm 
  glow from interior lights, frost on windows, 
  small Christmas decorations near entrance]

KEEP UNCHANGED:
- Building architecture, proportions, and materials
- Permanent signage and brand elements
- Camera angle and perspective (identical to original)
- Building colors and facade details

STYLE: Photorealistic. The result should look like 
the same building photographed in a different season — 
not like a filter or overlay.

IMPORTANT:
- Maintain physical consistency (snow accumulates 
  realistically, not like sprayed-on texture)
- Seasonal elements must match the lighting 
  (winter = lower sun angle, shorter shadows)
- No people visible
```

### Vorlage FIL-04: Neues Filialkonzept „aus dem Nichts" generieren

**Wann verwenden:** Wenn es noch kein Foto gibt — z.B. Konzeptpräsentation für einen Neubau oder kompletten Umbau

```
Generate a photorealistic interior visualization of 
a modern bank branch concept.

CONCEPT: [KONZEPT — z.B.:
- "Open Banking Hub": No traditional counters. 
  Open floor plan with consultation islands, 
  a coffee bar area, digital screens showing 
  financial content, lounge seating
- "Premium Advisory Center": Elegant, hotel-lobby feel.
  Private consultation rooms with glass walls, 
  a reception desk, high-end materials (marble, 
  dark wood, brass accents)
- "Digital-First Branch": Minimal staff areas, 
  focus on self-service terminals, video consultation 
  booths, interactive digital walls
- "Community Branch": Event space that doubles 
  as banking area, flexible furniture, local art 
  on walls, community bulletin board].

DIMENSIONS: Approximately [X]m × [Y]m floor area.
Ceiling height: ~3m.

MATERIALS AND COLORS:
- Floor: [MATERIAL — z.B. light oak, polished concrete, 
  grey tile]
- Walls: [MATERIAL — z.B. white plaster, exposed brick 
  accent wall, light wood paneling]
- Accent color: [FARBE_PRIMÄR]
- Secondary accent: [FARBE_SEKUNDÄR]

LIGHTING: [BELEUCHTUNG — z.B.:
- Natural daylight through large windows + warm LED panels
- Dramatic accent lighting on feature wall
- Soft, indirect ceiling lighting with task lights 
  at consultation desks]

CAMERA: Interior architecture photography.
Wide angle (~24mm), eye level, f/8 for full depth 
of field. Shot from a corner to show maximum space.

STYLE: Architectural rendering quality.
Like a visualization from a top interior design firm.

INCLUDE:
- [MÖBLIERUNG — z.B. 3 consultation desks, 
  4-seat lounge area, 2 self-service terminals, 
  1 reception counter]
- Indoor plants (3-5, varied sizes)
- Warm lighting creating an inviting atmosphere
- A subtle view through windows to an urban/suburban 
  exterior

DO NOT INCLUDE:
- People (add later if needed)
- Visible brand logos (added in post-production)
- Screens with readable content (just glowing screens)
```

> **Volksbank-Analogie:** Diese Vorlage ist wie ein Finanzierungsszenario: Sie zeigen dem Kunden, wie sein Haus aussehen *könnte*, bevor der erste Stein gesetzt wird. Die Filial-Visualisierung macht das Gleiche — sie gibt der Entscheidung ein Gesicht, bevor das Budget freigegeben wird.

---

## Die Entscheidungsmatrix: Welche Vorlage wann?

```
┌──────────────────────────────────────────────────────────────────┐
│      ENTSCHEIDUNGSBAUM: DIE RICHTIGE VORLAGE FINDEN              │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Was brauchen Sie?                                              │
│     │                                                            │
│     ├── Social Media Post?                                      │
│     │   ├── Produkt bewerben → SM-01                            │
│     │   ├── Wissen teilen → SM-02                               │
│     │   ├── Saisonale Kampagne → SM-03                          │
│     │   ├── Event ankündigen → SM-04                            │
│     │   └── Team/Kultur zeigen → SM-05                          │
│     │                                                            │
│     ├── Präsentations-Visual?                                   │
│     │   ├── Titelfolie → PR-01                                  │
│     │   ├── Kapitel-Trenner → PR-02                             │
│     │   ├── Daten-Hintergrund → PR-03                           │
│     │   └── Konzept-Illustration → PR-04                        │
│     │                                                            │
│     ├── Recruiting?                                             │
│     │   ├── Stellenanzeige → REC-01                             │
│     │   ├── Employer Branding Serie → REC-02                    │
│     │   └── Ausbildungsstart → REC-03                           │
│     │                                                            │
│     ├── Geschäftsbericht?                                       │
│     │   ├── Kapitel-Illustration → GB-01                        │
│     │   ├── Infografik-Icons → GB-02                            │
│     │   └── Cover-Bild → GB-03                                  │
│     │                                                            │
│     └── Filiale?                                                │
│         ├── Bestehendes Foto → modernisieren: FIL-01            │
│         ├── Bestehendes Foto → aufbereiten: FIL-02             │
│         ├── Bestehendes Foto → saisonal: FIL-03               │
│         └── Kein Foto → Konzept generieren: FIL-04             │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## Was kann diese Technologie (noch) nicht? Limitationen der Vorlagen

| Limitation | Auswirkung für Banken | Workaround |
|-----------|----------------------|------------|
| **Exakte Corporate-Design-Einhaltung** | KI kennt Ihre CD-Richtlinien nicht — Schutzzone ums Logo, Mindestgrößen, Pantone-Farben werden nicht automatisch eingehalten | CD-Farben als Hex-Codes im Prompt angeben; Logo IMMER im Design-Tool platzieren; KI-Bild = Rohling, nicht Endprodukt |
| **Konsistenz über viele Bilder** | 10 Social-Media-Posts im gleichen Stil werden trotzdem leicht variieren — Farbtemperatur, Komposition, „Vibe" | Style-Guide als Referenzbild mitgeben; erste gelungene Variante als Referenz für Folgebilder nutzen |
| **Markenrechtlich geschützte Elemente** | KI kann Ihr Logo nicht korrekt reproduzieren — und sollte es auch nicht | Logo, Schriftzug, geschützte Symbole IMMER extern überlagern |
| **Fotorealistische Innenräume mit exakten Maßen** | KI-Visualisierungen sind Stimmungsbilder, keine maßstabsgetreuen Architekturpläne | Für echte Planung: CAD-Software. KI = Konzeptphase und Präsentation |
| **Rechtskonformität der generierten Personen** | KI-Personen können zufällig echten Menschen ähneln — rechtliche Grauzone | Bei Recruiting: Im Disclaimer kennzeichnen. Bei Kampagnen: Professionelles Review |
| **Text-Perfektion bei langen Texten** | Bei >10 Wörtern steigt das Fehlerrisiko signifikant (Kapitel 03, Tutorial 03) | Kurze Headlines im KI-Bild; längere Texte im Design-Tool ergänzen |
| **Druckqualität (300 DPI)** | Nicht alle Modelle liefern ausreichende Auflösung für Großformatdruck | GPT Image 1.5: bis 4096×4096 px (reicht für A4 bei 300 DPI). Für Poster: Upscaling-Tools nutzen |

### Bank-spezifische Risiken bei Vorlagen-Nutzung

| Risiko | Szenario | Maßnahme |
|--------|---------|----------|
| **„Vorlagen-Blindheit"** | Alle Social-Media-Posts sehen gleich aus, weil dieselbe Vorlage ohne Variation genutzt wird | Vorlagen als Startpunkt, nicht als Endprodukt. Regelmäßig variieren |
| **Datenschutz bei Bildbearbeitung** | Filialbild mit erkennbaren Kunden wird in Cloud-KI hochgeladen | Erst alle Personen im Design-Tool unkenntlich machen, DANN KI-Bearbeitung |
| **Compliance bei Recruiting** | KI-generierte Personen in Stellenanzeigen könnten AGG-Konformität gefährden | Diverse Darstellung explizit anfordern; rechtliche Prüfung bei der Erstverwendung |
| **Täuschungsverbot** | KI-Filialvisualisierung wird als „echtes Foto" auf Google Maps verwendet | IMMER kennzeichnen: „Visualisierung" oder „Konzeptbild" |
| **Urheberrecht** | Unklar, ob KI-generierte Bilder urheberrechtlich geschützt sind (Stand 2025: nicht eindeutig) | Für geschäftskritische Bilder: Rechtsberatung einholen. Für Social Media: Risiko gering |

---

## Was kostet das? Vorlagen-Nutzung vs. klassische Produktion

| Szenario | Klassisch (Agentur/Designer) | Mit KI-Vorlagen | Zeitersparnis |
|----------|------------------------------|-----------------|---------------|
| **12 Social-Media-Posts/Monat** | 1.200–3.600 € (Agentur) oder 600–1.200 € (Freelancer) | 20–50 € (API-Kosten) + 3-4h/Monat | 80-90% Kosten, 60% Zeit |
| **Präsentations-Set (20 Folien-Visuals)** | 2.000–5.000 € (Design-Agentur) | 30–60 € + 1 Tag | 90% Kosten, 70% Zeit |
| **Recruiting-Kampagne (5 Motive)** | 3.000–8.000 € (Fotoshooting + Agentur) | 15–40 € + halber Tag | 95% Kosten, 80% Zeit |
| **Geschäftsbericht-Illustrationen (8 Kapitel)** | 4.000–10.000 € (Illustrator) | 50–100 € + 2 Tage | 95% Kosten, 60% Zeit |
| **Filial-Visualisierung (3 Varianten)** | 5.000–15.000 € (Architekturvisualisierung) | 20–50 € + halber Tag | 98% Kosten, 90% Zeit |

**Die ehrliche Einschränkung:** Diese Zahlen gelten für den **Entwurfs- und Konzeptprozess**. Für Endprodukte in Premium-Qualität (gedruckter Geschäftsbericht, großformatige Plakate, finale Recruiting-Kampagne) werden Sie oft noch professionelle Nachbearbeitung brauchen. Aber statt bei null anzufangen, startet der Designer mit einem **fertigen Konzeptbild** — das spart trotzdem 40-60% der bisherigen Kosten.

---

## End-to-End: Von der Vorlage zum fertigen Bild

```
┌──────────────────────────────────────────────────────────────────┐
│        DER VORLAGEN-WORKFLOW: 7 SCHRITTE ZUM FERTIGEN BILD       │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. AUFGABE KLÄREN ────── Was brauche ich?                      │
│     │                     → Entscheidungsmatrix (oben)          │
│     ▼                                                            │
│  2. VORLAGE WÄHLEN ────── Passende Vorlage aus diesem Tutorial  │
│     │                     kopieren                               │
│     ▼                                                            │
│  3. ANPASSEN ──────────── Platzhalter ersetzen (60 Sekunden)    │
│     │                     [BANK], [PRODUKT], [FARBE]...         │
│     ▼                                                            │
│  4. GENERIEREN ────────── In ChatGPT, Gemini oder Ideogram      │
│     │                     einfügen und generieren lassen        │
│     ▼                                                            │
│  5. ITERIEREN ─────────── Nicht perfekt? Konversationell        │
│     │                     verfeinern (Kapitel 03, Tutorial 04): │
│     │                     „Mach die Beleuchtung wärmer."        │
│     │                     „Weniger Schatten links."              │
│     │                     „Der Text soll größer sein."          │
│     ▼                                                            │
│  6. FINALISIEREN ──────── Im Design-Tool (Canva, PowerPoint,    │
│     │                     Photoshop):                            │
│     │                     → Logo platzieren                     │
│     │                     → Lange Texte ergänzen                │
│     │                     → CD-Konformität prüfen               │
│     │                     → Format exakt zuschneiden            │
│     ▼                                                            │
│  7. FREIGABE ──────────── Compliance-Check:                     │
│                           ☐ Keine erkennbaren echten Personen?  │
│                           ☐ Keine irreführende Darstellung?     │
│                           ☐ Bildrechte geklärt?                 │
│                           ☐ Als KI-generiert gekennzeichnet     │
│                             (wo erforderlich)?                   │
│                           ☐ CD-Richtlinien eingehalten?         │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Ihre erste Social-Media-Grafik in 5 Minuten

Wählen Sie eine Vorlage aus Bereich 1 (Social Media) und erstellen Sie einen Post für Ihre Bank:

**Wo tippe ich das ein?** Öffnen Sie [ChatGPT](https://chat.openai.com) (mit GPT-4o oder neuer) oder [Gemini](https://gemini.google.com). Kopieren Sie die Vorlage, ersetzen Sie die Platzhalter, und drücken Sie Enter.

1. Kopieren Sie **Vorlage SM-01** (Produkt-Ankündigung)
2. Ersetzen Sie die Platzhalter:
   - `[ZIELGRUPPE]` → „junge Familien"
   - `[PRODUKT]` → „Baufinanzierung"
   - `[HEADLINE]` → „Ihr Eigenheim wartet"
   - `[SUBLINE]` → „Baufinanzierung ab 2,9 % effektiv"
   - `[FARBE_PRIMÄR]` → Ihre Bankfarbe (z.B. „dark blue")
3. Generieren Sie das Bild
4. Prüfen Sie: Ist der Text fehlerfrei? Wirkt die Szene authentisch? Gibt es Platz für ein Logo?
5. Falls nötig: Eine Runde konversationelles Editing (Kapitel 03, Tutorial 04)

**Zeitaufwand:** ~5 Minuten. Vergleichen Sie das mit der bisherigen Methode (Agentur briefen, 3 Tage warten, Korrekturschleife...).

### Hands-on 2: Filiale saisonal verwandeln

Nehmen Sie ein Foto Ihrer Filiale (oder ein beliebiges Gebäudefoto) und erstellen Sie eine saisonale Variante:

1. Laden Sie das Foto in ChatGPT oder Gemini hoch
2. Verwenden Sie **Vorlage FIL-03** (Saisonale Fassaden-Varianten)
3. Wählen Sie eine Saison, die gerade NICHT ist (im Sommer → Winter-Version)
4. Generieren Sie das Bild

**Beobachten Sie:**
- Stimmt die Beleuchtung zur Jahreszeit (Sonnenstand, Schattenlänge)?
- Wirken die saisonalen Elemente natürlich oder „aufgeklebt"?
- Ist das Gebäude noch klar als dasselbe erkennbar?
- Würden Sie das Bild auf Ihrer Website verwenden?

### Hands-on 3: Der Modellvergleich (Pflicht!)

Nehmen Sie **Vorlage PR-01** (Titelfolie) und generieren Sie dasselbe Konzept in **ChatGPT** und **Gemini**:

```
Metapher: "digital transformation"
Farbe primär: dark blue (#003399)
Farbe sekundär: orange (#FF6600)
```

**Vergleichen Sie:**
- Welches Modell hat die Komposition besser umgesetzt (60/40-Aufteilung)?
- Wo ist der Farbton näher an Ihren CD-Farben?
- Welches Bild wirkt professioneller und moderner?
- Welches würden Sie tatsächlich in einer Vorstandspräsentation verwenden?

---

## Zusammenfassung: Das Wichtigste auf einen Blick

| Was Sie gelernt haben | Kernaussage |
|-----------------------|-------------|
| **25+ Vorlagen** | Fertige Copy-Paste-Prompts für 5 Kernbereiche des Bankalltags |
| **Anpassungs-System** | 5 Standard-Variablen ([BANK], [FARBE], [PRODUKT], [ZIELGRUPPE], [FORMAT]) → 60-Sekunden-Personalisierung |
| **Social Media (SM-01 bis SM-05)** | Produkt-Posts, Wissens-Content, saisonale Kampagnen, Events, Employer Branding |
| **Präsentationen (PR-01 bis PR-04)** | Titelfolien, Kapitel-Trenner, Daten-Hintergründe, Konzept-Illustrationen |
| **Recruiting (REC-01 bis REC-03)** | Stellenanzeigen, Employer-Branding-Serien, Ausbildungsstart |
| **Geschäftsberichte (GB-01 bis GB-03)** | Kapitel-Illustrationen, Infografik-Icons, Cover-Bilder |
| **Filial-Visualisierung (FIL-01 bis FIL-04)** | Modernisierung, Website-Optimierung, Saisonvarianten, Konzeptvisualisierung |
| **Vorlagen sind Startpunkte** | Kopieren → Anpassen → Generieren → Iterieren → Finalisieren im Design-Tool |
| **Logo und Text extern** | KI-Bild = Rohling. Logo, lange Texte, CD-konforme Elemente → immer im Design-Tool |
| **Compliance first** | Datenschutz, Kennzeichnungspflicht, Täuschungsverbot — auch bei Vorlagen beachten |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---------------------------|--------------------------------|
| **Anpassungs-System mit Variablen** | Anwendung der Platzhalter-Logik aus Kapitel 02, Tutorial 04 (Komplexe Prompt-Architekturen) — modulare Bausteine für wiederverwendbare Prompts |
| **Fotorealismus-Prompts (SM-01, REC-01)** | Direkte Anwendung der 7 Stellschrauben aus Kapitel 03, Tutorial 02 — Kamera-Sprache, Beleuchtung, Tiefenschärfe |
| **Text-im-Bild-Vorlagen (SM-02, SM-04)** | Umsetzung der 6 goldenen Regeln aus Kapitel 03, Tutorial 03 — kurze Texte, exakte Schreibweise, Fehlerprävention |
| **Iteratives Verfeinern** | Konversationelles Editing aus Kapitel 03, Tutorial 04 — eine Änderung pro Runde, Anti-Drift-Formel |
| **Filial-Bearbeitung (FIL-01 bis FIL-03)** | Kombination aus Inpainting, Style Transfer und Szenen-Transformation aus Kapitel 03, Tutorial 04 |
| **Modellwahl-Empfehlungen** | Aufbauend auf den Modellvergleichen aus Kapitel 03, Tutorial 01 und 04 |
| **Kosten-Vergleich** | Fortsetzung der ROI-Analyse aus Kapitel 03, Tutorial 03 und 04 — diesmal für den gesamten Bilderstellungs-Workflow |
| **Compliance und Datenschutz** | Vertiefung der ethischen Aspekte aus Kapitel 01, Tutorial 03 und Kapitel 03, Tutorial 03 und 04 |
| **Vorlagen-Konzept** | Parallele zu den Text-Prompt-Vorlagen aus Kapitel 01, Tutorial 05–07 — jetzt für Bilder statt für Text |

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Prompt-Vorlage (Template)** | Ein vorformulierter, wiederverwendbarer Prompt mit Platzhaltern, der für verschiedene konkrete Anwendungsfälle angepasst werden kann |
| **Platzhalter (Variable)** | Ein markierter Bereich in der Vorlage (z.B. `[BANK]`), der vor der Verwendung durch einen konkreten Wert ersetzt wird |
| **Hero Image** | Das zentrale, größte und prominenteste Bild in einer Anzeige, auf einer Website oder in einem Social-Media-Post — der erste visuelle Eindruck |
| **Carousel (Karussell)** | Ein Social-Media-Format, bei dem mehrere Bilder horizontal durchgewischt werden können — beliebt für mehrteilige Geschichten auf Instagram und LinkedIn |
| **Section Divider (Kapitel-Trenner)** | Eine Folie in einer Präsentation, die zwischen Hauptabschnitten steht und den visuellen Übergang markiert — oft mit Stimmungsbild und Abschnittstitel |
| **Corporate Design (CD)** | Die visuellen Gestaltungsrichtlinien einer Organisation — definiert Farben, Schriften, Logo-Verwendung, Abstände und den gesamten visuellen Auftritt |
| **Flat Design** | Ein minimalistischer Illustrationsstil ohne 3D-Effekte, Schlagschatten oder Texturen — klare Formen, satte Farben, reduzierte Darstellung |
| **Architectural Rendering** | Eine fotorealistische Computervisualisierung eines Gebäudes oder Innenraums — zeigt, wie ein geplanter Raum aussehen wird, bevor er gebaut ist |
| **AGG (Allgemeines Gleichbehandlungsgesetz)** | Deutsches Gesetz, das Diskriminierung verbietet — relevant bei Recruiting-Bildern: Keine stereotypen Darstellungen, diverse Repräsentation erforderlich |
| **Upscaling** | Nachträgliche Vergrößerung eines Bildes auf höhere Auflösung mithilfe von KI — fügt Details hinzu, die im Originalbild nicht vorhanden waren |
| **Hex-Code** | Eine sechsstellige Farbcodierung (z.B. #003399 für Dunkelblau), mit der Farben digital exakt definiert werden — präziser als Farbnamen im Prompt |
| **300 DPI (Dots Per Inch)** | Auflösungsmaß für Druckqualität — 300 DPI ist der Standard für professionellen Druck. Bilder mit weniger DPI wirken im Druck unscharf |
| **CD-Schutzzone** | Der definierte Mindestabstand um ein Logo herum, in dem keine anderen Elemente platziert werden dürfen — teil der Corporate-Design-Richtlinien |
| **Batch-Konsistenz** | Die Herausforderung, bei der Erstellung mehrerer Bilder mit denselben Vorlagen einen einheitlichen visuellen Stil beizubehalten |
| **Konzeptvisualisierung** | Ein Bild, das eine Idee oder einen Plan visuell darstellt — nicht als Dokumentation des Ist-Zustands, sondern als Vorschlag für den Soll-Zustand |
| **Employer Branding** | Die strategische Positionierung eines Unternehmens als attraktiver Arbeitgeber — durch visuelle Kommunikation der Unternehmenskultur, Werte und Arbeitsbedingungen |

---

