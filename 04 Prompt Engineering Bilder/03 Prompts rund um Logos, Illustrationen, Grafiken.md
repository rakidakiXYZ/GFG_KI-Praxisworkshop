# Text, Logos und Grafikdesign im Bild

**Der praxisrelevanteste Skill für Banken — wenn der Text im Bild stimmen muss: Flyer, Poster, Social Media, Infografiken und Corporate Design mit KI**

---

## Warum dieses Tutorial?

In Tutorial 03-02 haben Sie gelernt, wie Sie mit Fotografen-Sprache **fotorealistische** Bilder erzeugen. Aber seien wir ehrlich: Im Bankalltag brauchen Sie selten ein Foto mit cremigem Bokeh. Was Sie **ständig** brauchen, sind Materialien mit **Text**: Flyer für die neue Baufinanzierungsaktion, Social-Media-Posts mit Headline, Poster für die Filiale, Infografiken für den Vorstandsbericht. Und genau hier lag bis vor kurzem das größte Problem der KI-Bildgenerierung.

**Text in Bildern war der Endgegner.** Während KI-Modelle schon 2023 beeindruckende Landschaften und Porträts erzeugen konnten, scheiterten sie kläglich an einem simplen Wort wie „WILLKOMMEN" — da stand dann „WILKOMEN" oder „WILLKOMNEN" auf dem Poster. Die Modelle verstanden Pixel, aber keine Buchstaben.

Das hat sich 2025/26 **radikal geändert**. Und genau deshalb ist dieses Tutorial das praxisrelevanteste in diesem Kapitel: Sie lernen, wie Sie die neuen Fähigkeiten nutzen, um professionelle Grafiken mit korrektem Text zu erstellen — direkt einsetzbar im Bankalltag.

**Was Sie nach diesem Tutorial wissen werden:**

- Warum Text in KI-Bildern so schwierig ist — und warum es jetzt funktioniert
- Welche Modelle Text am besten beherrschen (mit konkreten Genauigkeitswerten)
- Die 6 goldenen Regeln für fehlerfreien Text im Bild
- Wie Sie Flyer, Poster und Social-Media-Grafiken mit KI erstellen
- Wie Sie Infografiken für Berichte und Präsentationen generieren
- Wie Sie Logos und Typografie-Designs prompten
- Warum Sie trotzdem ein Design-Tool für die Finalisierung brauchen
- Wann KI-Grafiken in Banken eingesetzt werden dürfen — und wann nicht

---

## Ein kurzer Blick zurück: Vom Buchstabensalat zum lesbaren Text

| Jahr | Meilenstein | Text-Qualität |
|------|-----------|---------------|
| **2022** | DALL·E 2, Stable Diffusion 1.5 | Unleserlich — „OEPN" statt „OPEN", verdrehte Buchstaben, Text als Textur |
| **2023** | DALL·E 3, Midjourney v5 | Erste Lesbarkeit — kurze Wörter (3–5 Buchstaben) zu ~60% korrekt |
| **2024** | FLUX.1, Ideogram 1.0 | Durchbruch — Ideogram spezialisiert sich auf Text, FLUX nutzt DiT-Architektur für bessere Buchstabentrennung |
| **2025** | Ideogram 2.0, GPT-4o Image, Gemini 2.5 Flash | Zuverlässiger Text — GPT-4o Image „denkt" über Buchstabenreihenfolge nach, >85% Genauigkeit bei kurzen Texten |
| **2025/26** | GPT Image 1.5, Ideogram 3.0, Gemini 3 Pro (Nano Banana Pro), FLUX.2 [max], Recraft V4 | Professionelle Qualität — GPT Image 1.5 und Ideogram 3.0 erreichen >95% bei kurzen Texten, mehrsprachig, Layout-Verständnis |

**Der entscheidende Wandel:** Ältere Modelle behandelten Text wie ein **visuelles Muster** — sie „malten" Buchstaben, ohne zu verstehen, was sie schrieben. Die aktuelle Generation (GPT Image 1.5, Gemini 3 Pro Image) nutzt **Reasoning** — das Modell „weiß", dass „WILLKOMMEN" aus genau diesen 10 Buchstaben in genau dieser Reihenfolge besteht, bevor es das Bild erzeugt.

> **Volksbank-Analogie:** Stellen Sie sich vor, jemand bittet einen hervorragenden Maler, ein Schild auf Japanisch zu beschriften — obwohl er kein Wort Japanisch kann. Er malt die Zeichen nach, aber vermutlich mit kleinen Fehlern. So war KI-Text bis 2024. Heute ist es eher wie ein Maler, der die Sprache gelernt hat: Er versteht, was er schreibt, und macht deshalb weniger Fehler.

---

## Warum ist Text im Bild so schwierig für KI?

Um die richtigen Prompt-Strategien zu wählen, hilft es zu verstehen, warum Text ein Sonderfall ist:

```
┌──────────────────────────────────────────────────────────────────┐
│           WARUM TEXT FÜR KI-BILDER SO SCHWER IST                 │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. ZEICHENEBENE ──────── Jeder einzelne Buchstabe muss         │
│     │                     exakt stimmen — „R" ≠ „B" ≠ „P"       │
│     │                     (Beim Foto reicht „ungefähr richtig")  │
│     ▼                                                            │
│  2. REIHENFOLGE ────────── „BANK" ≠ „BNAK" ≠ „BAKN"            │
│     │                     (Ein vertauschter Buchstabe             │
│     │                      und das Wort ist falsch)               │
│     ▼                                                            │
│  3. LAYOUT-REGELN ─────── Text folgt strengen Konventionen:     │
│     │                     Zeilenabstand, Ausrichtung,            │
│     │                     Hierarchie, Lesbarkeit                  │
│     ▼                                                            │
│  4. NULL TOLERANZ ──────── Bei einem Porträt stört eine          │
│     │                     leichte Asymmetrie nicht.              │
│     │                     Bei Text fällt EIN falscher             │
│     │                     Buchstabe sofort auf.                   │
│     ▼                                                            │
│  5. KONTEXT-ABHÄNGIG ──── „Sparkasse" hat 9 Buchstaben,         │
│                           „Baufinanzierung" hat 16.               │
│                           Längere Wörter = mehr Fehlerpotenzial   │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** Text im Bild ist wie eine Kontonummer auf einer Überweisung: **Jede einzelne Ziffer muss stimmen.** Bei einem Landschaftsbild ist es wie der Memo-Text — ein kleiner Tippfehler fällt kaum auf. Aber bei der Kontonummer? Ein Zahlendreher, und das Geld landet woanders.

---

## Die Modell-Landschaft: Wer kann Text am besten? (Stand: Februar 2026)

Nicht alle KI-Modelle sind gleich gut bei Text. Die Unterschiede sind **enorm**:

| Modell | Text-Genauigkeit (kurz, <10 Zeichen) | Text-Genauigkeit (lang, >20 Zeichen) | Mehrsprachig | Layout/Infografik | Preis |
|--------|--------------------------------------|--------------------------------------|-------------|-------------------|-------|
| **GPT Image 1.5** | ★★★★★ (~95%) | ★★★★☆ (~85%) | ✅ Gut | ★★★★★ | API-basiert, ~0,02–0,08 $/Bild |
| **Ideogram 3.0** | ★★★★★ (~95%) | ★★★★☆ (~85%) | ✅ Gut | ★★★★☆ | Free Tier + Abo ab 8 $/Monat |
| **Gemini 3 Pro Image (Nano Banana Pro)** | ★★★★☆ (~90%) | ★★★★☆ (~80%) | ✅ Sehr gut (Google Translate) | ★★★★★ | In Gemini-Abo enthalten |
| **FLUX.2 [max]** | ★★★★☆ (~88%) | ★★★☆☆ (~70%) | ⚠️ Nur Englisch stark | ★★★☆☆ | API-basiert |
| **Midjourney v7** | ★★★☆☆ (~75%) | ★★☆☆☆ (~50%) | ⚠️ Eingeschränkt | ★★☆☆☆ | Abo ab 10 $/Monat |
| **Recraft V4** | ★★★★☆ (~88%) | ★★★☆☆ (~75%) | ✅ Gut | ★★★★☆ | Free + Pro |

### Empfehlung nach Anwendungsfall

| Was brauchen Sie? | Bestes Modell | Warum |
|-------------------|--------------|-------|
| **Poster/Flyer mit viel Text** | GPT Image 1.5 oder Ideogram 3.0 | Höchste Textgenauigkeit, gutes Layout-Verständnis |
| **Infografiken mit Daten** | Gemini 3 Pro (Nano Banana Pro) | Reasoning + Google Search für korrekte Fakten |
| **Logo-Entwürfe** | Recraft V4 oder GPT Image 1.5 | Vektorfähigkeit (Recraft), saubere Formen |
| **Social Media Grafiken** | GPT Image 1.5 oder Gemini | Schnelle Iteration, Text + Bild in einem |
| **Mehrsprachige Materialien** | Gemini 3 Pro (Nano Banana Pro) | Beste Sprachunterstützung durch Google-Integration |
| **Typografie als Kunstform** | Ideogram 3.0 | Spezialisiert auf kreative Text-Darstellung |

---

## Die 6 goldenen Regeln für fehlerfreien Text im Bild

Diese Regeln gelten für **alle** Modelle und erhöhen Ihre Erfolgsquote dramatisch:

### Regel 1: Text in Anführungszeichen setzen

Das klingt simpel, macht aber einen riesigen Unterschied. Ohne Anführungszeichen interpretiert das Modell Ihre Wörter als **Beschreibung**. Mit Anführungszeichen versteht es: „Das ist der **exakte Text**, der im Bild erscheinen soll."

| ❌ Schlecht | ✅ Gut |
|-----------|--------|
| Create a poster with the headline Baufinanzierung leicht gemacht | Create a poster with the headline **"Baufinanzierung leicht gemacht"** |

### Regel 2: Buchstabiere bei kritischen Wörtern buchstabenweise

Für Markennamen, Fachbegriffe oder ungewöhnliche Wörter:

```
Display the text "VOLKSBANK" — spelled V-O-L-K-S-B-A-N-K — 
in bold capital letters at the top of the poster.
```

### Regel 3: Typografie-Details explizit angeben

Je mehr Sie über Schrift, Größe, Farbe und Platzierung sagen, desto besser:

```
Headline: "TRAUMHAUS FINANZIEREN" 
— bold sans-serif font (like Helvetica or Montserrat)
— white text on dark blue background
— centered at the top third of the image
— large enough to read at arm's length
```

### Regel 4: Weniger Text = weniger Fehler

**Jedes zusätzliche Wort erhöht die Fehlerwahrscheinlichkeit.** Für KI-generierte Grafiken gilt:

| Textmenge | Fehlerrisiko | Empfehlung |
|-----------|-------------|------------|
| 1–3 Wörter | Sehr niedrig (~5%) | Direkt im KI-Bild |
| 4–8 Wörter | Niedrig (~15%) | Im KI-Bild, aber prüfen |
| 9–20 Wörter | Mittel (~30%) | KI für Layout, Text nachträglich in Canva/Figma |
| 20+ Wörter | Hoch (~50%+) | KI nur für das Grunddesign, gesamten Text extern setzen |

> **Volksbank-Analogie:** Es ist wie bei einer Handschrift auf einer Grußkarte: „Frohe Ostern!" gelingt jedem fehlerfrei. Einen ganzen Absatz sauber per Hand zu schreiben, erfordert deutlich mehr Konzentration — und die Fehlerquote steigt.

### Regel 5: Text IMMER manuell prüfen — keine Ausnahme

Auch bei den besten Modellen gilt: **Vertrauen, aber verifizieren.**

```
PRÜF-CHECKLISTE FÜR TEXT IM KI-BILD:
☐ Jedes Wort korrekt geschrieben?
☐ Keine doppelten oder fehlenden Buchstaben?
☐ Richtige Groß-/Kleinschreibung?
☐ Sonderzeichen korrekt (ä, ö, ü, ß, €)?
☐ Keine zusätzlichen Wörter, die nicht im Prompt standen?
☐ Text lesbar bei der geplanten Ausgabegröße?
☐ Platzierung wie gewünscht?
```

### Regel 6: Hybrides Arbeiten — KI-Design + Design-Tool für Text

Der **professionellste Workflow** kombiniert beide Welten:

```
┌──────────────────────────────────────────────────────────────────┐
│           DER HYBRIDE WORKFLOW: KI + DESIGN-TOOL                 │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  SCHRITT 1: KI generiert das Grunddesign                        │
│  → Layout, Farben, Bildkomposition, Stimmung                    │
│  → Platzhalter oder echten Text (wird geprüft)                  │
│     │                                                            │
│     ▼                                                            │
│  SCHRITT 2: Export als hochauflösendes PNG                      │
│     │                                                            │
│     ▼                                                            │
│  SCHRITT 3: Text in Canva, Figma oder PowerPoint setzen         │
│  → 100% korrekte Schreibweise                                   │
│  → Exakte Schriftart nach Corporate Design                      │
│  → Pixel-genaue Platzierung                                     │
│  → Barrierefreie Kontraste                                       │
│     │                                                            │
│     ▼                                                            │
│  SCHRITT 4: Finales Ergebnis                                    │
│  → Professionelles Design + garantiert korrekter Text           │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

**Warum hybrid?** Weil selbst 95% Genauigkeit bedeutet: Bei 20 Flyern haben Sie statistisch 1 Flyer mit einem Tippfehler. Im Bankbereich ist das inakzeptabel — stellen Sie sich „Baufinazierung" auf einem Schaufenster-Poster vor.

> **Volksbank-Analogie:** Es ist wie bei der Kreditvergabe: Die KI macht die Vorarbeit (Scoring, Datensammlung, Entwurf). Aber die **finale Freigabe** macht immer ein Mensch. Kein automatisierter Prozess ersetzt die Vier-Augen-Prüfung bei wichtigen Dokumenten.

---

## Praxis: Flyer und Poster erstellen

### Der Prompt-Aufbau für Werbematerialien

Für Flyer, Poster und Print-Materialien hat sich eine **5-Schichten-Struktur** bewährt:

```
┌──────────────────────────────────────────────────────────────────┐
│         5 SCHICHTEN FÜR WERBEMATERIALIEN                         │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. FORMAT & ZWECK ────── Was ist es? Für wen? Welches Format?  │
│     „A4 flyer for a home loan campaign,                         │
│      target audience: young families"                            │
│                                                                  │
│  2. VISUELLES KONZEPT ── Was zeigt das Bild?                    │
│     „Modern family home with garden,                            │
│      warm sunlight, inviting atmosphere"                         │
│                                                                  │
│  3. TEXT & TYPOGRAFIE ── Exakter Wortlaut + Schrift-Details     │
│     „Headline: 'TRAUMHAUS FINANZIEREN'                          │
│      bold sans-serif, centered top third"                        │
│                                                                  │
│  4. FARBSCHEMA ────────── Markenfarben oder Stimmung            │
│     „Dark blue (#003366) and white with                         │
│      gold accent (#D4AF37)"                                      │
│                                                                  │
│  5. LAYOUT-ANWEISUNGEN ── Wo steht was?                         │
│     „Text in upper third, image fills lower                     │
│      two thirds, logo space bottom right"                        │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Sprache im Prompt: Englisch oder Deutsch?

Eine häufige Frage: **Muss ich meine Prompts auf Englisch schreiben?** Die kurze Antwort: Es hilft, muss aber nicht.

- **Englische Prompts** erzeugen tendenziell bessere Ergebnisse, weil die Modelle überwiegend mit englischen Daten trainiert wurden
- **Deutsche Prompts** funktionieren bei ChatGPT und Gemini gut — die Modelle verstehen Deutsch als Prompt-Sprache zuverlässig
- **Der Text IM BILD** kann immer Deutsch sein, egal in welcher Sprache der Prompt geschrieben ist

**Praxis-Empfehlung:** Schreiben Sie den Prompt auf Englisch, aber den gewünschten Bildtext auf Deutsch in Anführungszeichen. So holen Sie das Beste aus beiden Welten:

```
Create a professional flyer for a regional bank.
Headline text (EXACT): "BAUFINANZIERUNG LEICHT GEMACHT"
Subline text (EXACT): "Jetzt beraten lassen"
```

> **Volksbank-Analogie:** Es ist wie bei einer internationalen Bankkonferenz: Die Arbeitssprache ist Englisch (= Prompt), aber die Kundenunterlagen vor Ort sind selbstverständlich in der Landessprache (= Text im Bild).

### Beispiel-Prompt: Baufinanzierungs-Flyer

```
Create a professional A4 flyer for a regional bank's 
home loan campaign.

Visual: A modern family home with a small garden, 
bathed in warm golden-hour sunlight. 
A young couple stands in front of it, looking happy. 
The image should feel aspirational but authentic, 
not like a stock photo.

Headline text (EXACT, verbatim): 
"TRAUMHAUS FINANZIEREN"
— Bold sans-serif font, white letters with subtle drop shadow
— Centered in the upper quarter of the flyer
— Large enough to be the clear focal point

Subheadline text (EXACT): 
"Ab 2,9 % effektiver Jahreszins"
— Smaller, regular weight, same font family
— Directly below the headline, also centered

Call-to-action text at the bottom (EXACT): 
"Jetzt Beratungstermin vereinbaren"
— Inside a rounded button shape, white text on blue (#003366)
— Positioned in the bottom quarter, centered

Color scheme: Dark navy blue (#003366) as primary, 
white for text, warm gold (#D4AF37) as accent.
Clean, modern, professional banking aesthetic.
Leave empty space in the bottom-right corner for a logo.

No watermarks. No extra text beyond what is specified.
```

### Beispiel-Prompt: Social-Media-Kampagne (Instagram-Post)

```
Create a square (1:1) Instagram post for a bank's 
savings account campaign.

Background: Clean gradient from navy blue (#003366) 
at the top to lighter blue (#4A90D9) at the bottom.

In the center: A stylized piggy bank icon or 
3D illustration, modern and playful.

Text at the top (EXACT, verbatim):
"SPAREN LEICHT GEMACHT"
— Bold white sans-serif (like Montserrat Bold)
— Centered, high contrast against the dark background

Text below the piggy bank (EXACT):
"0,5 % Tagesgeldzins"
— Large, gold (#D4AF37) color, eye-catching
— This is the hero number, make it prominent

Text at the bottom (EXACT):
"Jetzt Konto eröffnen →"
— Smaller, white, regular weight
— With a subtle arrow or CTA indicator

Modern, clean, mobile-optimized design. 
No clutter. 
High contrast for outdoor phone viewing.
No watermarks or logos.
```

---

## Praxis: Infografiken erstellen

Infografiken sind die **Königsdisziplin** für KI-Bildgenerierung mit Text — weil sie viele Textelemente, Daten, Symbole und ein strukturiertes Layout kombinieren. Gleichzeitig sind sie einer der größten Hebel für den Bankalltag: Ein trockener Quartalsbericht wird zur teilbaren Grafik.

### Warum KI-Infografiken funktionieren

Gemini 3 Pro (Nano Banana Pro) und GPT Image 1.5 haben einen entscheidenden Vorteil: Sie **verstehen**, was eine Infografik ist. Sie kennen die Layout-Konventionen (Headline oben, Abschnitte mit Icons, Datenvisualisierung, CTA am Ende) und setzen diese auch ohne pixelgenaue Anweisungen um.

### Der strukturierte Infografik-Prompt

```
Create a detailed infographic explaining 
"5 Schritte zur Baufinanzierung" 
(5 Steps to a Home Loan).

Target audience: Young first-time homebuyers in Germany.

Layout: Vertical format (9:16), clean and modern.

Structure:
1. Title section at top: "5 SCHRITTE ZUR BAUFINANZIERUNG"
   — Bold, large, dark blue text
2. Five numbered sections flowing top to bottom:
   Step 1: "Budget berechnen" — with calculator icon
   Step 2: "Eigenkapital prüfen" — with savings/piggy bank icon
   Step 3: "Angebote vergleichen" — with comparison/checklist icon
   Step 4: "Beratungstermin buchen" — with calendar icon
   Step 5: "Vertrag abschließen" — with handshake icon
3. Each step has: Number, Title, 1-2 sentence explanation
4. Bottom section: Call-to-action area

Color scheme: Navy blue (#003366), white, light grey (#F5F5F5), 
gold accents (#D4AF37).
Style: Professional, clean, Scandinavian-inspired with 
plenty of white space. Not cluttered.

All text must be in German, correctly spelled.
No watermarks, no external branding.
```

### Infografiken für Vorstandsberichte

Für datengetriebene Infografiken (Quartalsberichte, KPI-Dashboards) nutzen Sie das **Reasoning** der Modelle:

```
Create a professional data infographic summarizing 
quarterly bank performance.

Display these KPIs at the top as large hero numbers:
- "12.450" new customers (with upward arrow, +8%)
- "€ 2,3 Mrd." total deposits (with upward arrow, +5%)
- "94 %" customer satisfaction (with checkmark icon)

Below the KPIs, show:
- A simple bar chart comparing Q1-Q4 customer growth
- A pie chart showing deposit distribution 
  (Tagesgeld 45%, Festgeld 30%, Sparbuch 25%)

Color scheme: Dark blue and gold on white background.
Professional, executive-presentation quality.
Clean sans-serif typography throughout.

All text in German, all numbers exactly as specified.
Wide 16:9 format, suitable for a PowerPoint slide.
```

> **Volksbank-Analogie:** Eine gute Infografik ist wie eine gute Beratung: Sie nimmt komplexe Finanzdaten und macht sie verständlich, visuell ansprechend und handlungsrelevant. Statt 20 Seiten Quartalsbericht liest der Vorstand ein Bild — und versteht sofort, wo die Bank steht.

---

## Praxis: Logo-Entwürfe generieren

**Wichtiger Hinweis vorweg:** KI-generierte Logos sind **Konzepte und Inspiration** — keine fertigen Logos. Für ein finales Corporate-Logo brauchen Sie einen Designer, der das Konzept in eine saubere Vektordatei überführt. Aber für die **erste Ideenfindung** sind KI-Logos unschlagbar schnell.

### Warum Logo-Prompting anders funktioniert

Logos sind das Gegenteil von fotorealistischen Bildern: Statt Komplexität und Detailreichtum brauchen sie **Reduktion, Klarheit und Skalierbarkeit**.

### Der Logo-Prompt

```
Create an original, non-infringing logo for 
"Volksbank Musterstadt" — a modern regional bank.

Requirements:
- Clean, minimal, timeless design
- Symbol mark + wordmark combined
- The symbol should suggest trust, growth, and community
  (abstract, no literal house or money imagery)
- Strong silhouette that reads clearly at small sizes
  (favicon, app icon) and large sizes (building signage)
- Flat design, no gradients unless essential
- Colors: Dark blue (#003366) and gold (#D4AF37) on white
- Sans-serif typeface for the wordmark (clean, modern)

Plain white background with generous padding.
Deliver a single centered logo.
No watermark. No tagline. No secondary elements.
```

**Varianten generieren:** Fordern Sie 4 Varianten an und vergleichen Sie:

```
Generate 4 different logo concepts for the same brief.
Each should take a distinct design direction:
1. Abstract geometric mark
2. Lettermark (monogram from VBM)
3. Symbol with nature element (tree/leaf, abstract)
4. Bold typographic wordmark only
```

### Logo-Iteration: Konversationelles Verfeinern

Der große Vorteil bei ChatGPT und Gemini — Sie iterieren im Gespräch:

```
Iteration 1: „I like concept 3 best. Make the leaf 
more abstract — just curved lines, no realistic detail."

Iteration 2: „Good direction. Make the blue darker 
and increase the spacing in the wordmark."

Iteration 3: „Almost perfect. Show me this logo 
on a dark background variant too."
```

---

## Praxis: Mehrsprachige Materialien und Übersetzung

Eine oft übersehene Stärke aktueller Modelle: Sie können **Text in Bildern übersetzen**, ohne das Design zu verändern.

### Text-Übersetzung im Bild

```
Translate all German text in this infographic to English.
Keep the exact same layout, colors, design elements, 
icons, and overall visual structure.
Do not change anything except the text language.
Preserve typography style, size, and placement.
```

### Mehrsprachige Materialien von Grund auf

Für Banken mit internationalem Kundenstamm:

```
Create the same savings account flyer in three languages.
Use identical layout, colors, and visual design.

Version 1 (German): Headline "SPAREN LEICHT GEMACHT"
Version 2 (English): Headline "SAVING MADE EASY"  
Version 3 (Turkish): Headline "TASARRUF KOLAY"

Each version: Square (1:1) format, navy blue gradient 
background, white text, gold accent, piggy bank icon.
```

> **Volksbank-Analogie:** Es ist wie das mehrsprachige Informationsblatt am Schalter: Der Inhalt ist identisch, aber jede Sprachversion muss **eigenständig professionell** wirken — nicht wie eine holprige automatische Übersetzung.

---

## Praxis: Marketing-Creatives und Werbebanner

### Display-Werbung (Online-Banner)

```
Create a web banner ad, 728x90 pixels (leaderboard format).

Left third: Small product image — modern banking app 
on smartphone screen, clean and sharp.

Center: Headline text (EXACT): "Banking. Einfach. Digital."
— Bold white sans-serif on dark blue background
— Clean kerning, professional typography

Right third: CTA button — rounded rectangle, gold (#D4AF37),
text "Jetzt testen" in dark blue.

Overall: Clean, high-contrast, optimized for banner blindness 
breakthrough. Professional banking aesthetic.
No clutter, maximum 3 visual elements.
```

### Social-Media-Story (9:16)

```
Create an Instagram Story ad (1080x1920, vertical 9:16).

Full-screen background: Lifestyle photo of a young professional 
using a banking app on her phone in a modern café.
Warm, natural lighting, slightly blurred background.

Text overlay at the top (EXACT):
"DEIN GELD. DEINE KONTROLLE."
— Bold white text with subtle text shadow for readability
— Large, attention-grabbing

Text overlay at the bottom (EXACT):
"Swipe up für die neue App"
— Smaller, with upward arrow icon

Subtle dark gradient overlay at top and bottom edges 
for text readability over the photo.
Modern, authentic, not overly corporate.
```

### Produktvergleichs-Grafik

```
Create a clean comparison graphic (1:1 square format) 
showing three bank account types side by side.

Three columns with headers:
Column 1: "GIRO BASIS" — blue header
Column 2: "GIRO PLUS" — gold header, highlighted as recommended
Column 3: "GIRO PREMIUM" — dark blue header

Each column lists 4 features with checkmarks or X marks:
- Online Banking: ✓ ✓ ✓
- Kreditkarte: ✗ ✓ ✓  
- Reiseversicherung: ✗ ✗ ✓
- Persönlicher Berater: ✗ ✗ ✓

Pricing at the bottom of each column:
"0 €/Monat" | "4,90 €/Monat" | "12,90 €/Monat"

Clean, modern table design with subtle grid lines.
White background, navy blue and gold color scheme.
Professional banking aesthetic.
All text in German, perfectly spelled.
```

---

## Werkzeuge und Stellschrauben für Text im Bild

### Die wichtigsten Parameter

| Stellschraube | Wirkung | Empfehlung |
|--------------|---------|------------|
| **Qualitätsstufe „high"** | Mehr Rechenzeit → bessere Textschärfe und Detail | Immer „high" für textlastige Grafiken |
| **Seitenverhältnis** | Format bestimmt Layout-Möglichkeiten | 1:1 (Social), 9:16 (Story), 16:9 (Präsentation), 3:4 (Print) |
| **Anführungszeichen** | Markiert exakten Text vs. Beschreibung | Immer verwenden für jeden Text, der im Bild erscheinen soll |
| **Buchstabenweise Schreibung** | Hilft bei komplexen/ungewöhnlichen Wörtern | Bei Markennamen, Fachbegriffen, fremdsprachigen Wörtern |
| **Font-Angaben** | Steuert Typografie-Stil | Bekannte Schriften nennen: „Helvetica", „Montserrat", „Georgia" |
| **Platzierungsanweisungen** | Steuert Layout | „centered at top third", „bottom-right corner", „left-aligned" |
| **Farbangaben mit Hex** | Präzise Farbsteuerung | „white text on dark blue (#003366)" statt „weißer Text auf Blau" |
| **Ausschlüsse** | Verhindert unerwünschte Elemente | „No extra text", „no watermark", „no additional elements" |

### Modellspezifische Text-Tipps

**GPT Image 1.5 (ChatGPT):**
- Konversationell iterieren: „Fix the spelling of the headline" funktioniert
- Reasoning-Modelle (o3, o4-mini) planen Text besser
- Explizit „verbatim" sagen: „Display this text EXACT and verbatim"
- Bei Fehlern: Selben Prompt nochmal — oft klappt es beim 2. Versuch

**Gemini 3 Pro (Nano Banana Pro):**
- Versteht komplexe Layouts besonders gut (Infografiken, Diagramme)
- Google Search für faktisch korrekte Daten in Infografiken
- Bis zu 14 Referenzbilder für Multi-Image-Compositing
- „Keep everything else exactly the same" als Sicherheitsanker bei Edits

**Ideogram 3.0:**
- Spezialist für Typografie — kreative Text-Designs, Poster, Thumbnails
- Einfache Prompts funktionieren oft besser als überladene
- Besonders gut für kurze, plakative Headlines

**FLUX.2 [max]:**
- Keine negativen Prompts — das Gegenteil beschreiben
- Text am Prompt-Anfang für höhere Priorität
- Englische Texte deutlich zuverlässiger als deutsche

**Recraft V4:**
- Kann **Vektorgrafiken (SVG)** erzeugen — einzigartig für Logos und Icons
- Saubere geometrische Formen
- Gut für Brand-Identity-Elemente

---

## Was kann KI-Text-im-Bild (noch) nicht?

| Limitation | Auswirkung für Banken | Workaround |
|-----------|----------------------|------------|
| **Lange Texte (>20 Wörter)** | Disclaimer, AGB-Verweise, Fußnoten werden fehlerhaft | Text nachträglich im Design-Tool setzen |
| **Deutsche Sonderzeichen (ä, ö, ü, ß)** | Werden manchmal zu ae, oe, ue, ss oder ganz verschluckt | Buchstabenweise schreiben: „ä" betonen, oder hybrid arbeiten |
| **Exakte Schriftarten** | KI erzeugt „ähnlich wie Helvetica", nicht Helvetica selbst | Für CD-konforme Materialien: Text extern setzen |
| **Pixel-genaues Layout** | Abstände und Ausrichtungen weichen leicht ab | Für Print: KI als Entwurf, Feinschliff in InDesign/Canva |
| **Kleine Schriftgrößen** | Text unter ~12pt wird unleserlich oder fehlerhaft | Großen Text im KI-Bild, Kleingedrucktes nachträglich |
| **Tabellen mit vielen Zellen** | Zeilenumbrüche, Ausrichtung und Konsistenz problematisch | Einfache Tabellen (≤4 Spalten, ≤6 Zeilen) machbar, darüber hinaus: extern |
| **Handschrift-Simulation** | Sieht oft unnatürlich oder unleserlich aus | Echte Handschrift-Fonts in Canva verwenden |
| **Mathematische Formeln** | Brüche, Integrale, Indizes werden verzerrt | LaTeX rendern und als Bild einfügen |
| **QR-Codes** | Werden generiert, sind aber **nicht funktional** | QR-Code extern generieren und einfügen |

### Bank-spezifische Risiken und Compliance

| Risiko | Erklärung | Maßnahme |
|--------|-----------|----------|
| **Falsche Zahlen** | „2,9 % Jahreszins" könnte zu „2,6 %" werden | Jede Zahl manuell prüfen — Haftungsrisiko! |
| **Fehlende Pflichtangaben** | BaFin-relevante Hinweise, Risikoaufklärung | Immer nachträglich im Design-Tool einfügen |
| **Markenrecht** | KI könnte geschützte Logos/Designs nachahmen | Nur eigene Markenelemente verwenden, KI-Output prüfen |
| **Täuschung** | KI-generierte „Fotos" von Filialen oder Mitarbeitern | Immer als KI-generiert kennzeichnen |
| **Barrierefreiheit** | Text-Kontraste könnten unter WCAG-Standards liegen | Kontrastverhältnis prüfen (mind. 4,5:1) |
| **CD-Konformität** | KI kennt Ihr Corporate Design nicht | CD-Richtlinien als Referenz hochladen oder Farb-Hex-Codes angeben |

> **Volksbank-Analogie:** KI-generierte Werbematerialien sind wie ein Kreditantrag aus der automatisierten Vorprüfung: Das Scoring sieht gut aus, aber bevor Sie den Vertrag unterschreiben, prüft ein Mensch die **Pflichtangaben, die rechtlichen Hinweise und die Compliance.** Automatisierung beschleunigt, ersetzt aber nicht die Sorgfaltspflicht.

---

## Was kostet das? KI-Grafiken vs. Agentur/Designer

| Szenario | Klassisch (Agentur/Designer) | KI-generiert + Feinschliff | Zeitersparnis |
|----------|------------------------------|---------------------------|---------------|
| **1 Social-Media-Post** | 80–200 € (Freelancer) | 0–5 € (Abo-anteilig) + 15 Min Canva | 1–2 Tage → 30 Min |
| **10 Instagram-Posts (Kampagne)** | 800–2.000 € | 10–30 € + 3h Canva | 1–2 Wochen → 1 Tag |
| **A4-Flyer** | 300–800 € (Design + Satz) | 5–15 € + 1h Feinschliff | 3–5 Tage → 3 Stunden |
| **Infografik (Quartalsbericht)** | 500–1.500 € | 10–20 € + 1h Prüfung | 1 Woche → halber Tag |
| **Logo-Konzepte (5 Varianten)** | 1.000–3.000 € (Designagentur) | 10–30 € (Ideation) + Designer für Finalisierung | 2–3 Wochen Ideation → 1 Tag |
| **20 mehrsprachige Banner** | 3.000–8.000 € | 30–80 € + 4h Anpassung | 3–4 Wochen → 2 Tage |

**Automatisierung für Kampagnen:** Für Klaus und andere Fortgeschrittene: Wenn Sie 20+ Varianten eines Social-Media-Posts brauchen (z.B. verschiedene Produkte, Regionen, Sprachen), können Sie das über die API von GPT Image 1.5 oder Gemini **automatisieren** — ein Skript generiert alle Varianten aus einer Vorlage. Das ist Stoff für einen separaten Workshop, aber merken Sie sich: Ab ~10 Varianten lohnt sich die Automatisierung über Batch-Processing.

**Die ehrliche Rechnung:** KI eliminiert nicht den Designer — sie macht den Designer **10x produktiver.** Statt 2 Tage für einen Flyer braucht ein Designer mit KI-Unterstützung 2 Stunden: KI erzeugt 10 Konzepte, Designer wählt das beste, perfektioniert Layout und Text, exportiert druckfertig.

---

## End-to-End: Die Text-im-Bild-Pipeline

```
┌──────────────────────────────────────────────────────────────────┐
│        VON DER IDEE ZUR FERTIGEN GRAFIK MIT TEXT                 │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. ZIEL DEFINIEREN ────── Flyer? Social Post? Infografik?      │
│     │                      Zielgruppe? Kanal? Format?            │
│     ▼                                                            │
│  2. TEXT VORBEREITEN ───── Exakte Texte vorformulieren           │
│     │                      (Headline, Subline, CTA, Fußnoten)   │
│     │                      Rechtschreibung vorab prüfen!         │
│     ▼                                                            │
│  3. MODELL WÄHLEN ──────── Je nach Aufgabe (Tabelle oben)       │
│     │                      GPT Image 1.5 → Text-Genauigkeit     │
│     │                      Gemini → Infografiken + Layout        │
│     │                      Ideogram → Kreative Typografie        │
│     ▼                                                            │
│  4. PROMPT BAUEN ──────── 5-Schichten-Struktur anwenden         │
│     │                      Format → Visual → Text → Farben →    │
│     │                      Layout                                │
│     │                      Text in „Anführungszeichen"!          │
│     ▼                                                            │
│  5. GENERIEREN ─────────── 3-4 Varianten erzeugen              │
│     ▼                                                            │
│  6. TEXT PRÜFEN ────────── Checkliste durchgehen:               │
│     │                      ☐ Jedes Wort korrekt?                │
│     │                      ☐ Zahlen stimmen?                     │
│     │                      ☐ Sonderzeichen?                      │
│     ▼                                                            │
│  7. ENTSCHEIDUNG ──────── Text korrekt UND kurz?                │
│     │   Ja → Direkt verwenden (nach Compliance-Check)           │
│     │   Nein → Export + Text im Design-Tool ersetzen            │
│     ▼                                                            │
│  8. FINALISIEREN ──────── CD-Check, Pflichtangaben ergänzen,    │
│                            als KI-generiert kennzeichnen,        │
│                            Format-Export (PNG/PDF/SVG)           │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## 🔬 Probieren Sie es selbst!

### Hands-on 1: Der Headline-Test

Testen Sie, wie zuverlässig Ihr Modell deutschen Text rendert. Verwenden Sie diesen Prompt in **ChatGPT** oder **Gemini**:

```
Create a simple poster with a dark blue background.
Display this text in large, bold, white letters, 
centered in the middle:

"BAUFINANZIERUNG
leicht gemacht"

Below that, in smaller gold text:
"Ihre Volksbank Musterstadt"

Clean, minimal, professional banking design.
No other elements.
```

**Wo tippe ich das ein?** Öffnen Sie [ChatGPT](https://chat.openai.com) oder [Gemini](https://gemini.google.com) im Browser. Kopieren Sie den Prompt in das Textfeld und drücken Sie Enter. Das Modell erzeugt das Bild direkt im Chat.

**Prüfen Sie:**
- Ist „BAUFINANZIERUNG" korrekt geschrieben? (häufiger Fehler: fehlendes „I" oder doppeltes „N")
- Stimmt die Groß-/Kleinschreibung?
- Ist das „ß" in eventuellen Varianten korrekt?
- Wie sieht die Typografie aus — professionell oder etwas wackelig?

**Bonus:** Versuchen Sie denselben Prompt mit „ü" und „ö": „GÜNSTIGER DENN JE — FÜR SIE UND IHRE ZUKUNFT"

### Hands-on 2: Die Infografik-Challenge

Erstellen Sie eine einfache Infografik mit **Gemini** oder **ChatGPT**:

```
Create a vertical infographic (9:16) titled 
"3 TIPPS FÜR IHRE ALTERSVORSORGE"

Three sections, each with a number, icon, and short text:
1. "Früh anfangen" — clock icon — 
   "Schon 50 € monatlich machen langfristig einen Unterschied."
2. "Breit streuen" — pie chart icon — 
   "Mischen Sie verschiedene Anlageformen."
3. "Regelmäßig prüfen" — checkmark icon — 
   "Passen Sie Ihre Strategie an Ihre Lebensphase an."

Color scheme: Navy blue, white, gold accents.
Professional banking infographic style.
All text in German, correctly spelled.
```

**Beobachten Sie:**
- Wie viele der deutschen Wörter sind korrekt?
- Ist das Layout sauber strukturiert?
- Sehen die Icons professionell aus?
- Würden Sie das (nach Textprüfung) für einen LinkedIn-Post verwenden?

### Hands-on 3: Der Modellvergleich (Pflicht!)

Nehmen Sie den Poster-Prompt aus Hands-on 1 und geben Sie ihn in **zwei verschiedene Tools** ein (z.B. ChatGPT + Gemini, oder ChatGPT + Ideogram):

**Vergleichen Sie:**
- Welches Modell gibt den deutschen Text fehlerfrei wieder?
- Welches Layout wirkt professioneller?
- Wie reagieren die Modelle auf die Sonderzeichen (ü, ö, ß)?
- Welches Modell kommt einem „echten" Agentur-Design näher?

---

## Zusammenfassung: Das Wichtigste auf einen Blick

| Was Sie gelernt haben | Kernaussage |
|-----------------------|-------------|
| **Text war der Endgegner** | Bis 2024 scheiterte KI an Buchstabenreihenfolge — heute erreichen Top-Modelle >95% bei kurzen Texten |
| **Reasoning macht den Unterschied** | GPT Image 1.5 und Gemini 3 Pro „verstehen" Buchstaben, statt sie nur zu malen |
| **6 goldene Regeln** | Anführungszeichen, buchstabenweise Schreibung, Typografie-Details, weniger Text, immer prüfen, hybrid arbeiten |
| **Modellwahl entscheidet** | GPT Image 1.5 / Ideogram für Text, Gemini für Infografiken, Recraft für Logos |
| **5-Schichten-Prompt** | Format → Visual → Text → Farben → Layout — systematischer Aufbau für Werbematerialien |
| **Hybrides Arbeiten** | KI für Konzept + Design, Design-Tool für finalen Text — der professionelle Standard |
| **Sonderzeichen sind heikel** | ä, ö, ü, ß erhöhen die Fehlerquote — buchstabenweise betonen oder nachträglich setzen |
| **Compliance beachten** | Jede Zahl prüfen, Pflichtangaben extern setzen, KI-generierte Materialien kennzeichnen |
| **Kosten-Revolution** | 10 Social-Media-Posts: Agentur 2.000 € vs. KI+Feinschliff ~30 € + 3h Arbeit |
| **QR-Codes: extern** | KI-generierte QR-Codes funktionieren nicht — immer separat erstellen |

---

## Parallelen zu vorherigen Tutorials

| Konzept aus diesem Tutorial | Verbindung zu früheren Tutorials |
|---------------------------|--------------------------------|
| **Reasoning für Text** | Basiert auf dem LLM-Reasoning-Prinzip aus Kapitel 00, Tutorial 01 (wie LLMs „denken") |
| **5-Schichten-Prompt** | Erweiterung des 6-Bausteine-Frameworks aus Kapitel 03, Tutorial 01 — spezialisiert auf Grafik-Design |
| **Modellspezifische Tipps** | Vertieft die Modellvergleiche aus Kapitel 03, Tutorial 01 und Tutorial 02 |
| **Hybrides Arbeiten** | Entspricht dem „KI + Mensch"-Prinzip aus Kapitel 01, Tutorial 03 (Halluzinationen) — Vertrauen, aber verifizieren |
| **Konversationelle Iteration** | Anwendung der iterativen Prompt-Technik aus Kapitel 01, Tutorial 04 (Fortgeschrittene Techniken) |
| **JSON-Prompt-Vorlage** | Aufgriff der strukturierten Prompts aus Kapitel 02, Tutorial 03 (JSON) |
| **Text in Anführungszeichen** | Parallele zur „klar und spezifisch"-Regel aus Kapitel 01, Tutorial 01 |
| **Compliance und Kennzeichnung** | Vertieft die ethischen Aspekte aus Kapitel 01, Tutorial 03 (Halluzinationen und Bias) |

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Typografie** | Die Kunst und Technik der Schriftgestaltung — umfasst Schriftart, Größe, Abstände, Ausrichtung und Hierarchie von Text |
| **Sans-Serif** | Schriftart ohne Serifen (Füßchen an den Buchstaben). Beispiele: Helvetica, Arial, Montserrat. Wirkt modern und klar |
| **Serif** | Schriftart mit Serifen. Beispiele: Times New Roman, Georgia. Wirkt traditionell und seriös |
| **Kerning** | Der Abstand zwischen einzelnen Buchstabenpaaren — gutes Kerning sorgt dafür, dass Text gleichmäßig und professionell aussieht |
| **Headline / Subline** | Überschrift (Headline) und Unterüberschrift (Subline) — die zwei wichtigsten Textelemente eines Werbemittels |
| **CTA (Call-to-Action)** | Handlungsaufforderung wie „Jetzt Termin buchen" oder „Mehr erfahren" — meist als Button oder hervorgehobener Text |
| **Infografik** | Visuelle Darstellung von Informationen, Daten oder Wissen. Kombiniert Text, Zahlen, Icons und Layout zu einem leicht verständlichen Gesamtbild |
| **Hex-Code** | 6-stelliger Farbcode (z.B. #003366 für Dunkelblau). Ermöglicht pixelgenaue Farbangaben im Prompt |
| **Verbatim** | „Wörtlich" — Anweisung an die KI, Text exakt wie angegeben wiederzugeben, ohne kreative Abweichungen |
| **Vektorgrafik (SVG)** | Bilddatei aus mathematischen Formen statt Pixeln. Kann verlustfrei skaliert werden — ideal für Logos und Icons |
| **Layout** | Die Anordnung von Text, Bildern und Grafik-Elementen auf einer Fläche — bestimmt den visuellen Lesefluss |
| **Rendering** | Der Prozess, bei dem die KI aus dem Text-Prompt ein fertiges Bild berechnet und darstellt |
| **Wordmark** | Logo-Typ, der nur aus dem gestalteten Firmennamen besteht (z.B. Google, Coca-Cola), ohne separates Symbol |
| **Brand Identity** | Die Gesamtheit aller visuellen Elemente einer Marke: Logo, Farben, Schriften, Bildsprache, Icons |
| **WCAG** | Web Content Accessibility Guidelines — internationale Standards für barrierefreie Webinhalte, inkl. Mindest-Kontrastverhältnisse für Text |
| **Reasoning (bei Bildgenerierung)** | Die Fähigkeit des KI-Modells, vor der Bilderzeugung zu „denken" — z.B. die korrekte Buchstabenreihenfolge zu planen, statt sie nur visuell zu reproduzieren |
| **DiT (Diffusion Transformer)** | Architektur, die FLUX und neuere Modelle nutzen. Trennt Text-Rendering von visueller Komposition für bessere Ergebnisse |
| **OCR-Validierung** | Optical Character Recognition — automatische Texterkennung, mit der die Genauigkeit von Text im KI-Bild gemessen wird |

---

