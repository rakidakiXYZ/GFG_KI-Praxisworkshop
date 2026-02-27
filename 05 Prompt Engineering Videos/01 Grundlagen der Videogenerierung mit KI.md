# Grundlagen der Videogenerierung mit KI

**Die Karte — Modelle, Architekturen, Kosten und worauf es beim Video-Prompting ankommt**

---

## Warum dieses Tutorial?

In Tutorial 00-04 haben Sie gelernt, *wie* KI Videos generiert — der Daumenkino-Künstler, der aus Rauschsequenzen bewegte Bilder entstehen lässt, Raumzeit-Patches, temporale Attention-Layer und das ewige Ringen um Konsistenz von Frame zu Frame.

Jetzt geht es um die Praxis: **Welche Modelle gibt es heute, was können sie, und wie wählen Sie das richtige für Ihre Aufgabe?**

Die KI-Videogenerierung hat sich seit 2024 atemberaubend schnell entwickelt. Was damals mit unscharfen 4-Sekunden-Clips begann, ist im Februar 2026 ein Ökosystem aus acht ernst zu nehmenden Plattformen — manche generieren nativ synchronisierten Sound inklusive Dialoge, manche liefern 4K-Auflösung, und zwei davon sind Open Source und laufen auf Ihrem eigenen Rechner.

Und genau wie bei der Bildgenerierung (Kapitel 03) gilt: **Ein Prompt, der bei Veo 3.1 einen Kinoclip erzeugt, kann bei Kling ein ganz anderes Ergebnis liefern.** Die Modelle haben unterschiedliche Stärken, verstehen Prompts unterschiedlich, und wer das versteht, spart Stunden an Trial-and-Error.

**Was Sie nach diesem Tutorial wissen werden:**

- Welche drei grundlegend verschiedenen Wege zum KI-Video es gibt
- Was die acht wichtigsten Modelle ausmacht und wo ihre Stärken liegen
- Wie ein Video-Prompt grundsätzlich aufgebaut ist — das universelle Framework
- Was Audio-Generierung verändert und warum 2025/26 ein Wendepunkt ist
- Was die typischen Limitationen sind — und wo echte Videoproduktion unersetzlich bleibt
- Welches Modell Sie für welchen Anwendungsfall wählen sollten
- Was das alles kostet — von kostenlos bis Enterprise

---

## Ein kurzer Blick zurück: Die rasante Geschichte

In Tutorial 00-04 haben wir die technische Evolution bereits ausführlich behandelt. Hier die Kurzfassung für den Praxis-Kontext:

| Jahr | Meilenstein | Was sich änderte |
|------|-----------|-----------------|
| **2023** | **Runway Gen-2** | Erster kommerzieller Text-to-Video-Dienst. 4 Sekunden, oft verzerrt — aber der Startschuss |
| **2024 Feb** | **Sora Preview** (OpenAI) | Die Demos schockierten die Welt: 60 Sekunden, fotorealistisch. Noch nicht öffentlich |
| **2024 Jun** | **Kling 1.0** (Kuaishou) | Chinas Überraschung: 2 Minuten bei 1080p. Diffusion-Transformer-Architektur |
| **2024 Dez** | **Sora 1 + Veo 2** | Endlich öffentlich — OpenAI und Google liefern sich ein Kopf-an-Kopf-Rennen |
| **2025 Feb** | **Wan 2.1** (Alibaba) | Open Source! Läuft auf Consumer-GPUs. Demokratisierung der Videogenerierung |
| **2025 Mai** | **Veo 3** (Google) | Der Stummfilm ist vorbei: **Natives synchronisiertes Audio** — Dialoge, Soundeffekte, Ambient |
| **2025 Jun** | **Luma Ray3** | Physik-Reasoning: Videos mit realistischer Bewegungsphysik |
| **2025 Sep** | **Sora 2** (OpenAI) | Zweite Generation mit Social-Media-App und verbesserter Konsistenz |
| **2025 Okt** | **Veo 3.1** (Google) | Neueste stabile Version, verfügbar über Gemini und Google Flow |
| **2025 Dez** | **Wan 2.6** (Alibaba) | Open-Source-Upgrade: 14B Parameter, MoE-Architektur |
| **2026 Jan** | **LTX-2** (Lightricks) | Open Source mit nativem Audio — Foley, Ambience, Lip-Sync |
| **2026 Feb** | **Seedance 2.0** (ByteDance) | Ging viral — ultra-realistische Clips, Hollywood schlägt Alarm |

**Das Tempo ist das Bemerkenswerte:** Von unscharfen 4-Sekunden-Clips zu minutenlangen, fotorealistischen Videos mit Sound — in nur drei Jahren.

> **Volksbank-Analogie:** Erinnern Sie sich an die Einführung des Mobile-Bankings? 2012 waren Banking-Apps klobig und konnten wenig. 2016 konnten Sie überweisen und Kontostand prüfen. 2020 war Mobile-First Standard. 2024 erledigen Kunden alles per App. KI-Video durchläuft denselben Zyklus — nur in drei Jahren statt zwölf.

---

## Drei Wege zum KI-Video

Bevor wir in die einzelnen Modelle eintauchen, müssen Sie drei grundlegende Ansätze verstehen:

### Weg 1: Text-to-Video (T2V)

```
[Ihr Text-Prompt] ──────► [KI-Modell] ──────► [Video + ggf. Audio]
```

Sie beschreiben eine Szene per Text — die KI erzeugt daraus ein komplettes Video aus dem Nichts. Kein Ausgangsmaterial nötig.

**Typische Anwendung:** Konzeptvideos, Erklärclips, Social-Media-Content, kreative Visualisierungen.

**Beispiel:**
```
Ein sonniger Morgen vor einer modernen Bankfiliale. Eine junge
Beraterin öffnet die Eingangstür, lächelt in die Kamera und
begrüßt den Betrachter. Kamera: langsamer Dolly-Zoom auf ihr
Gesicht. Warmes Morgenlicht, cinematic style.
```

### Weg 2: Image-to-Video (I2V)

```
[Ihr Bild] + [Ihr Prompt] ──────► [KI-Modell] ──────► [Video]
```

Sie laden ein **Startbild** hoch und beschreiben, wie die KI es zum Leben erwecken soll. Das Bild wird zum ersten Frame — die KI animiert von dort aus.

**Typische Anwendung:** Produktfotos animieren, Architektur-Renderings zum Leben erwecken, vorhandene Designs in Bewegung bringen.

**Warum das oft besser funktioniert als T2V:** Sie kontrollieren das Aussehen über das Startbild — die KI muss nur noch die Bewegung hinzufügen. Das reduziert die Fehlerquellen erheblich.

> **Volksbank-Analogie:** Text-to-Video ist wie ein Telefonat mit Ihrem Grafikdesigner: „Machen Sie mal ein Video über unsere neue Filiale." Image-to-Video ist wie das Briefing mit einem Foto dabei: „Hier ist ein Bild unserer Filiale — lassen Sie die Tür aufgehen und einen Kunden eintreten." Natürlich ist das Zweite präziser.

### Weg 3: Video-to-Video (V2V)

```
[Ihr Video] + [Ihr Prompt] ──────► [KI-Modell] ──────► [Neues Video]
```

Sie laden ein **bestehendes Video** hoch und beschreiben, wie die KI es transformieren soll — Stiländerung, Szenenergänzung, Hintergrundwechsel.

**Typische Anwendung:** Smartphone-Videos in Filmästhetik verwandeln, Hintergründe austauschen, Stiltransfer (z.B. aus einem Bürovideo ein Animationsvideo machen).

**Noch in der Frühphase:** Video-to-Video ist 2026 die am wenigsten ausgereifte der drei Methoden. Ergebnisse können inkonsistent sein — aber die Entwicklung ist rasant.

### Welcher Weg für welchen Zweck?

| Aufgabe | Empfohlener Weg | Warum |
|---------|----------------|-------|
| Social-Media-Reel aus einer Idee | Text-to-Video | Schnell, kreativ, kein Material nötig |
| Produktfoto zum Leben erwecken | Image-to-Video | Kontrolle über Look & Feel |
| Workshop-Mitschnitt aufwerten | Video-to-Video | Ausgangsmaterial vorhanden |
| Recruiting-Video | Text-to-Video + Editing | Mehrere T2V-Szenen zusammenschneiden |
| Architektur-Rendering animieren | Image-to-Video | Rendering = perfektes Startbild |
| Erklärvideo für Kunden | Text-to-Video | Animierter Stil, keine Darsteller nötig |

---

## Der Game-Changer: Audio-Generierung

Bei Bildern (Kapitel 03) gab es dieses Thema schlicht nicht. Bei Video ist Audio **der Game-Changer 2025/26** — und der Grund, warum dieses Kapitel ein eigenes Tutorial zum Thema Audio bekommt (04-03).

### Was sich verändert hat

Bis Mitte 2025 waren KI-generierte Videos **stumm**. Sie mussten Audio separat produzieren und manuell synchronisieren — Musik, Sprecher, Soundeffekte, alles in der Nachbearbeitung. Das war aufwändig und erforderte Videoediting-Know-how.

Dann kam Veo 3 im Mai 2025 — und alles änderte sich:

```
┌──────────────────────────────────────────────────────────┐
│              VIDEO-GENERIERUNG: VOR UND NACH              │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  VOR Mai 2025:                                           │
│  ┌────────┐    ┌────────┐    ┌────────┐    ┌────────┐   │
│  │ Video  │ +  │ Musik  │ +  │ Voice  │ +  │ Sound- │   │
│  │ (KI)   │    │ (manu- │    │ Over   │    │ effekte│   │
│  │        │    │  ell)  │    │(Studio)│    │(manuell│   │
│  └────────┘    └────────┘    └────────┘    └────────┘   │
│       │              │             │             │       │
│       └──────────────┴─────────────┴─────────────┘       │
│                         │                                │
│                    Videoeditor                            │
│                   (Premiere, etc.)                        │
│                         │                                │
│                    Fertiges Video                         │
│                                                          │
│  NACH Mai 2025:                                          │
│  ┌──────────────────────────────────────────────────┐    │
│  │  Ein Prompt ──► Video + Dialog + Sounds + Musik  │    │
│  └──────────────────────────────────────────────────┘    │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Welche Modelle können natives Audio? (Stand: Februar 2026)

| Modell | Dialoge | Soundeffekte | Ambient/Musik | Lip-Sync |
|--------|---------|-------------|---------------|----------|
| **Veo 3.1** | ✅ Nativ | ✅ Nativ | ✅ Nativ | ✅ Sehr gut |
| **Sora 2** | ✅ Nativ | ✅ Nativ | ✅ Nativ | ✅ Gut |
| **Kling 2.6** | ✅ Nativ | ✅ Nativ | ✅ Nativ | ✅ Gut |
| **Seedance 2.0** | ✅ Nativ | ✅ Nativ | ✅ Nativ | ✅ Sehr gut |
| **LTX-2** | ✅ Nativ | ✅ Foley | ✅ Ambience | ✅ Gut |
| **Runway Gen-4.5** | ⚠️ Begrenzt | ⚠️ Begrenzt | ⚠️ Begrenzt | ⚠️ Basis |
| **Luma Ray3** | ❌ | ⚠️ Begrenzt | ⚠️ Begrenzt | ❌ |
| **Pika 2.5** | ❌ | ⚠️ Begrenzt | ⚠️ Begrenzt | ❌ |
| **Wan 2.2** | ❌ | ❌ | ❌ | ❌ |

**Die Trennlinie verläuft klar:** Vier der großen Modelle — Veo 3.1, Sora 2, Kling 2.6 und Seedance 2.0 — generieren im Februar 2026 **vollständiges Audio nativ**. Das bedeutet: Sie schreiben einen Prompt mit Dialog, und das fertige Video kommt mit gesprochenen Worten, passenden Soundeffekten und Hintergrundmusik zurück. In einem Schritt.

> **Volksbank-Analogie:** Stellen Sie sich vor, früher mussten Sie für eine Kundenpräsentation die Folien erstellen, dann einen Sprecher buchen, dann die Tonspur aufnehmen und alles zusammenschneiden. Jetzt schreiben Sie ein Briefing und bekommen eine fertige Videobotschaft zurück — mit Sprecher, Musik und allem Drum und Dran.

---

## Die acht wichtigsten Modelle im Überblick

### 1. Google Veo 3.1 — Der Regisseur

**Was es ist:** Googles Video-KI, verfügbar über Gemini (Google AI Pro/Ultra) und als API über Google Flow und Vertex AI.

**Stärken:**
- Beste native Audio-Qualität — Dialoge, Soundeffekte, Musik in einem Schritt
- Bis 4K Auflösung (über API; in Gemini bis 1080p)
- 8–12 Sekunden Clip-Länge (verlängerbar durch Scene Extension)
- Exzellente Prompttreue — versteht komplexe Szenen mit mehreren Elementen
- Physik-Simulation: Rauch, Wasser, Reflexionen wirken realistisch
- Verfügbar in Gemini Advanced / Google AI Ultra — kein separates Tool nötig

**Schwächen:**
- Clip-Länge auf ~12 Sekunden begrenzt (einzelne Generation)
- Wartezeiten bei hoher Auslastung
- Content-Filter können legitime Business-Inhalte blockieren
- Außerhalb von Gemini (API) teurer als Konkurrenz

**Prompt-Stil:** Veo 3.1 empfiehlt das gleiche **4-Bausteine-Framework**, das Sie im beigelegten Workshop-Material gesehen haben — Subjekt, Kontext, Aktion, Stil/Stimmung. Dialog-Zeilen können direkt in den Prompt geschrieben werden.

```
Prompt-Beispiel (Veo 3.1):

Cinematic style with warm morning light and modern aesthetics.
A 35-year-old bank consultant with shoulder-length brown hair
and a friendly smile sits at a modern consultation desk. She
explains the mobile banking app on a tablet to a young customer.

Consultant: "Good morning! Let me show you how easy it is to
manage your finances on your phone."
Customer (nods): "That sounds great."

The camera slowly zooms in on the tablet screen. Soft background
music with piano and gentle electronic elements. Ambient office
sounds — soft keyboard clicking, muffled conversations.
```

**Kosten:** Gemini Advanced / Google AI Pro ab 19,99 $/Monat (inkl. Veo). API: ~0,10–0,50 $/Sekunde je nach Anbieter.

> **Volksbank-Analogie:** Veo 3.1 ist wie der Regisseur, der auch gleichzeitig Kameramann, Tontechniker und Cutter ist — ein One-Man-Filmteam. Sie geben das Drehbuch ab und bekommen einen fertigen Clip zurück. Nicht Oscar-reif, aber gut genug für die Hauptversammlung.

---

### 2. OpenAI Sora 2 — Der Storyteller

**Was es ist:** OpenAIs Videogenerator, verfügbar über ChatGPT Plus/Pro und eine eigene Social-Media-App (sora.com).

**Stärken:**
- Längste Clips unter den Premium-Modellen — bis 25 Sekunden
- Natives Audio mit Dialogen und Soundeffekten
- Starke narrative Kohärenz — versteht Geschichten
- Konversationelles Interface in ChatGPT — „Mach das gleiche nochmal, aber mit blauem Hintergrund"
- Social-Media-App zum Teilen und Entdecken von Community-Creations

**Schwächen:**
- Kostenlos nur über die Sora-App (mit Einschränkungen)
- Physik-Simulation manchmal inkonsistent (Hände, Finger, Reflexionen)
- Content-Moderation strenger als bei manchen Konkurrenten
- Generierungszeit bei hoher Auflösung teils über 2 Minuten

**Prompt-Stil:** Sora 2 versteht **natürliche Sprache und Konversation** — wie ChatGPT für Text. Sie können Szenen beschreiben, als würden Sie mit einem Regisseur sprechen.

```
Prompt-Beispiel (Sora 2):

Erstelle einen 15-Sekunden-Recruiting-Teaser für eine Volksbank:
Ein junger Mann betritt ein modernes Bürogebäude. Die Kamera folgt
ihm im Steadicam-Stil durch ein offenes Großraumbüro. Kollegen
lächeln und grüßen. Er setzt sich an seinen Arbeitsplatz mit
Blick auf die Stadt. Text erscheint: "Deine Karriere bei uns."
Stil: Cinematic, warmes Licht, positive Energie.
Inspirierende Hintergrundmusik.
```

**Kosten:** ChatGPT Plus 20 $/Monat (begrenzte Generierungen). Sora-App: Free Tier mit Einschränkungen. API: ~0,10–0,50 $/Sekunde.

> **Volksbank-Analogie:** Sora 2 ist wie der kreative Marketingmitarbeiter, der sofort versteht, was Sie meinen. Sie sagen „Mach mal was Emotionales für unsere Azubi-Kampagne" und er liefert — vielleicht nicht perfekt beim ersten Mal, aber er versteht Ihre Intention und Sie können iterieren.

---

### 3. Runway Gen-4 / Gen-4.5 — Der Profi-Editor

**Was es ist:** Die Kreativ-Plattform für professionelle Video-Workflows. Runway war einer der Pioniere der KI-Videogenerierung und bietet das ausgereifteste Ökosystem an Tools.

**Stärken:**
- Bestes Ökosystem für professionelle Video-Workflows
- Gen-4 Turbo für schnelle Iterationen, Gen-4.5 für maximale Qualität
- 4K-Upscaling von Clips
- Starke Image-to-Video-Fähigkeiten — beste Kontrolle über Startframe
- Multi-Shot-Workflows: Storyboard-basiertes Arbeiten möglich
- Green-Screen-Funktion und Hintergrund-Entfernung

**Schwächen:**
- Audio-Generierung noch nicht auf Veo/Sora-Niveau
- Credit-basiertes Preismodell — teuer bei intensiver Nutzung
- Maximale Clip-Länge ~10 Sekunden (einzelne Generation)
- Steile Lernkurve für das volle Feature-Set

**Prompt-Stil:** Runway bevorzugt **präzise, technische Beschreibungen**. Kameraanweisungen werden sehr gut verstanden.

```
Prompt-Beispiel (Runway Gen-4.5):

A modern glass-walled bank office at golden hour. Camera slowly
tracks right, revealing a team meeting through the glass.
Three people around a table with laptops and coffee cups.
Warm afternoon sunlight creates long shadows. Shallow depth
of field. Cinematic, corporate documentary style.
```

**Kosten:** Ab 12 $/Monat (Standard), 28 $/Monat (Pro), 76 $/Monat (Unlimited). Credits-basiert: Ein 10-Sekunden-Clip in Gen-4 kostet ~100 Credits (Standard), 50 Credits (Turbo).

> **Volksbank-Analogie:** Runway ist wie die externe Werbeagentur, die Ihr Jahresvideo produziert. Professionelle Tools, beeindruckende Ergebnisse, aber Sie brauchen ein Budget und müssen sich einarbeiten. Für das schnelle Social-Media-Video vielleicht oversized — für die Kampagne genau richtig.

---

### 4. Kling 2.6 — Das Kraftpaket

**Was es ist:** Kuaishous Video-KI aus China, verfügbar über klingai.com und verschiedene internationale Plattformen. Mit Kling 3.0 steht bereits die nächste Generation in den Startlöchern.

**Stärken:**
- Längste Clips: bis **2 Minuten** in einem Durchlauf
- Natives Audio: Dialoge, Soundeffekte, Ambient
- Exzellentes Preis-Leistungs-Verhältnis — großzügiger Free Tier
- Starke Charakterkonsistenz über längere Clips
- Breites Kreativspektrum: Realismus, Anime, Cartoon, alles überzeugend
- Kling 3.0 (gerade erschienen): 4K nativ, 15-Sekunden-Clips, „Intelligent Storyboarding"

**Schwächen:**
- Interface teils auf Chinesisch (internationale Version besser werdend)
- Physik bei komplexen Szenen nicht immer korrekt
- Datenschutz: Server in China — für sensible Inhalte kritisch prüfen
- Promptverständnis bei sehr langen, komplexen Prompts schwächer als Veo

**Prompt-Stil:** Kling reagiert gut auf **klare, strukturierte Beschreibungen**. Kürzere Prompts (50–80 Wörter) funktionieren oft besser als lange.

```
Prompt-Beispiel (Kling 2.6):

A professional woman in business attire walks through a modern
bank lobby. Sunlight streams through floor-to-ceiling windows.
She stops at the reception, smiles at a colleague, and they
shake hands. Camera follows from behind, then cuts to a
frontal medium shot. Corporate style, warm color grading.
Natural office ambient sounds.
```

**Kosten:** Free Tier (66 Credits/Tag, ~10 Clips). Pro: ab 9,90 $/Monat.

> **Volksbank-Analogie:** Kling ist wie der erstaunlich gute Praktikant aus einer anderen Abteilung — überraschend leistungsfähig, unschlagbar im Preis-Leistungs-Verhältnis, aber Sie sollten sensible Kundendaten nicht über seinen Laptop laufen lassen.

---

### 5. Luma Ray3 (Dream Machine) — Der Physiker

**Was es ist:** Luma Labs' Video-KI, bekannt als „Dream Machine". Ray3 ist das erste Video-Modell mit **Reasoning-Fähigkeit** — es „denkt" über physikalische Plausibilität nach.

**Stärken:**
- Beste Bewegungsphysik aller Modelle — Objekte fallen, rollen, brechen realistisch
- HDR-Unterstützung und Keyframe-Editing
- Starke Ästhetik bei cinematic Content
- „Modify Video"-Funktion: Bestehende Videos neu interpretieren
- Großzügiger Free Tier für Einstieg

**Schwächen:**
- Keine native Audio-Generierung (nur begrenzte Soundeffekte)
- Clip-Länge auf ~8 Sekunden begrenzt
- Dialogverständnis schwächer als Veo/Sora
- Textdarstellung im Video nicht zuverlässig

**Prompt-Stil:** Ray3 glänzt bei **visuell-kinematischen Beschreibungen**. Physik-Details werden besonders gut umgesetzt.

```
Prompt-Beispiel (Luma Ray3):

A glass of water tips over on an office desk. Water spills
across the surface in slow motion, catching sunlight from
the window. Droplets scatter. A hand reaches in quickly to
save a stack of documents. Macro lens, shallow depth of field,
dramatic slow-motion, natural office lighting.
```

**Kosten:** Free Tier verfügbar. Paid: ab 7,99 $/Monat (Starter), 24,99 $/Monat (Standard).

> **Volksbank-Analogie:** Luma Ray3 ist wie der Dokumentarfilmer, der die kleinen, realistischen Momente einfängt — den Kugelschreiber, der über den Schreibtisch rollt, die Regentropfen am Filialen-Fenster. Für große Produktionen fehlt ihm das Team — aber bei Detailaufnahmen ist er unschlagbar.

---

### 6. Pika 2.5 — Der Kreative

**Was es ist:** Ein Video-KI-Tool, das besonders bei kreativen Effekten und viralen Social-Media-Formaten glänzt. Bekannt für spielerische Features.

**Stärken:**
- „Pikaframes": Szenen verketten für längere Narrative
- Kreative Spezialeffekte (Explosionen, Morphing, Stilwechsel)
- Intuitive Benutzeroberfläche — niedrigste Einstiegshürde
- Gut für TikTok/Reels-Formate optimiert
- Text-to-Video und Image-to-Video

**Schwächen:**
- Keine native Audio-Generierung (nur begrenzt)
- Maximale Auflösung 1080p
- Fotorealismus nicht auf Veo/Sora-Niveau
- Für professionelle Corporate-Videos weniger geeignet

**Prompt-Stil:** Pika funktioniert am besten mit **kurzen, kreativen Prompts**. Weniger technisch, mehr emotional.

```
Prompt-Beispiel (Pika 2.5):

A magical transformation: a boring office document turns into
a colorful infographic, pages flying and folding themselves
into 3D charts. Playful, energetic, bright colors.
```

**Kosten:** Free Tier begrenzt. Standard: 10 $/Monat (700 Credits). Pro: 35 $/Monat (2.300 Credits).

> **Volksbank-Analogie:** Pika ist wie der junge Azubi, der sich mit TikTok auskennt. Für den seriösen Geschäftsbericht nicht der richtige — aber wenn Sie einen viralen Reel über Ihre neue App brauchen, ist er in seinem Element.

---

### 7. Seedance 2.0 (ByteDance) — Der Disruptor

**Was es ist:** ByteDances neuestes Video-KI-Modell, im Februar 2026 viral gegangen. Verfügbar über die CapCut/Jianying-Plattform (aktuell primär mit chinesischem Account).

**Stärken:**
- Ultra-realistische Videogenerierung — Hollywood schlägt Alarm
- 4-Modalitäten-Input: Text, Bild, Video UND Audio als Eingabe
- @ Reference System: Personen, Orte, Stile als wiederverwendbare Referenzen
- Native 2K-Auflösung
- Natives Audio mit exzellenter Lip-Sync-Qualität
- Joint Audio-Video-Synthese — Audio und Video werden gleichzeitig generiert

**Schwächen:**
- Aktuell hauptsächlich mit chinesischem Douyin-Account nutzbar
- Verfügbarkeit außerhalb Chinas eingeschränkt (Creative Partner Program)
- Ethisch kontrovers: Deepfake-Potential sorgt für regulatorische Bedenken
- Content-Moderation noch nicht ausgereift für europäische Standards
- Datenschutz: ByteDance-Server, DSGVO-Konformität unklar

**Prompt-Stil:** Seedance 2.0 versteht sehr **detaillierte, filmische Beschreibungen** und das @ Reference System ermöglicht Charakterkonsistenz.

```
Prompt-Beispiel (Seedance 2.0):

Ultra-realistic corporate video. A confident woman in her 40s
gives a keynote presentation in a modern conference room.
The audience of 20 people listens attentively. Camera: slow
dolly from audience perspective towards the speaker.
Warm stage lighting, professional corporate atmosphere.
Speaker: "The future of banking is not digital — it's personal."
Audience applauds. 2K resolution, cinematic color grading.
```

**Kosten:** Aktuell kostenlos über CapCut/Jianying (mit Account-Einschränkung). Enterprise-Pricing noch nicht veröffentlicht.

> **Volksbank-Analogie:** Seedance ist wie der brillante Freelancer, den alle haben wollen — atemberaubende Ergebnisse, aber er arbeitet nur mit chinesischen Auftraggebern und Sie sind sich nicht sicher, ob Ihre Kundendaten bei ihm sicher sind. Beobachten, aber noch nicht einsetzen.

---

### 8. Open Source: Wan 2.2/2.6 + LTX-2 — Die Demokratisierer

**Was sie sind:** Frei verfügbare Video-KI-Modelle, die auf eigener Hardware oder über Cloud-Dienste laufen. Wan (Alibaba) und LTX-2 (Lightricks) sind die führenden Open-Source-Optionen.

**Wan 2.2 (Juli 2025) / Wan 2.6 (Dez 2025):**
- 1.3B–14B Parameter, Apache 2.0 Lizenz (Wan 2.2)
- Läuft auf Consumer-GPUs (ab 8 GB VRAM für Wan 2.2)
- LoRA-Support: Auf eigene Stile und Marken trainierbar
- Wan 2.6: MoE-Architektur, bessere Qualität, aber kommerziell lizenziert
- Kein natives Audio

**LTX-2 (Januar 2026):**
- 19B Parameter, Apache 2.0 Lizenz
- **Natives Audio**: Foley, Ambience, Lip-Sync
- Bis 4K Auflösung
- Distilled 20GB-Version für Consumer-Hardware
- Ideal für Audio-kritische Projekte ohne Cloud-Abhängigkeit

**Stärken (gemeinsam):**
- Kostenlos (eigene Hardware) oder günstig (Cloud: fal.ai, Replicate, ComfyUI)
- Volle Kontrolle über Modell, Parameter, Training
- Keine Content-Filter (konfigurierbar)
- Trainierbar auf Corporate Design, eigene Charaktere, Markenästhetik
- Datenschutz: Daten bleiben auf Ihrem Server

**Schwächen (gemeinsam):**
- Technisches Know-how erforderlich (Installation, GPU-Setup)
- Bildqualität unter den Premium-Modellen
- Kein konversationelles Interface
- Community-Support statt Enterprise-SLA

```
Prompt-Beispiel (Wan 2.2):

A professional woman in a navy blazer walks through a modern
office corridor. Natural daylight from side windows. She carries
a tablet and smiles. Camera follows from behind. Corporate
documentary style, clean, minimal.
```

**Kosten:** Kostenlos (eigene Hardware, ≥ 8 GB VRAM). Cloud: ab 0,03–0,10 $/Sekunde via fal.ai oder Replicate.

> **Volksbank-Analogie:** Open Source ist wie Ihre eigene Druckmaschine im Keller. Keine laufenden Lizenzkosten, volle Kontrolle, aber Sie brauchen jemanden, der sie bedienen kann. Und wenn Sie Ihr Corporate Design einmal eingepflegt haben, druckt sie konsistent — ohne dass ein Dritter Ihre Materialien sieht.

---

## Das universelle Video-Prompt-Framework

Trotz aller Unterschiede gibt es ein Framework, das bei **allen** Modellen funktioniert. Es erweitert das 6-Bausteine-Framework für Bilder (Tutorial 03-01) um die zeitliche Dimension:

### Die 8 Bausteine eines Video-Prompts

```
┌──────────────────────────────────────────────────────────┐
│                   VIDEO-PROMPT AUFBAU                     │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  1. STIL/GENRE ─────── Wie soll es aussehen?             │
│     │                  „Cinematic, dokumentarisch,        │
│     │                   animiert, Social-Media-Reel"      │
│     ▼                                                    │
│  2. SUBJEKT ────────── Wer/Was ist im Video?             │
│     │                  „Eine 35-jährige Beraterin         │
│     │                   mit dunklem Blazer"               │
│     ▼                                                    │
│  3. ORT/SETTING ────── Wo spielt die Szene?              │
│     │                  „Moderne Bankfiliale,              │
│     │                   Vormittag, Tageslicht"            │
│     ▼                                                    │
│  4. AKTION ─────────── Was passiert? (im Präsens!)       │
│     │                  „Sie erklärt dem Kunden die App    │
│     │                   auf dem Tablet"                   │
│     ▼                                                    │
│  5. KAMERA ─────────── Wie wird gefilmt?                 │
│     │                  „Langsamer Dolly-Zoom,             │
│     │                   Medium Shot, Augenhöhe"           │
│     ▼                                                    │
│  6. DIALOG ─────────── Was wird gesprochen?              │
│     │                  „Beraterin: Schauen Sie mal hier..." │
│     │                  (nur bei Modellen mit Audio)       │
│     ▼                                                    │
│  7. AUDIO ──────────── Wie klingt es?                    │
│     │                  „Sanfte Pianomusik, leises          │
│     │                   Büroambiente, Tastaturklicken"     │
│     ▼                                                    │
│  8. LICHT/STIMMUNG ─── Wie fühlt es sich an?             │
│                        „Warm, einladend, professionell,   │
│                         goldenes Nachmittagslicht"        │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Zwei neue Bausteine gegenüber Bildern

Gegenüber dem Bild-Framework (Tutorial 03-01) kommen zwei Elemente hinzu:

| Baustein | Warum bei Video wichtig | Bei Bildern? |
|----------|------------------------|-------------|
| **Kamera** | Video *bewegt* sich — Pan, Tilt, Dolly, Zoom, Drohne | Statische Perspektive reicht |
| **Dialog/Audio** | Video hat eine Tonspur — Sprache, Sounds, Musik | Existiert nicht |

### Die goldene Regel: Aktion immer im Präsens

Bei Bildern beschreiben Sie einen **Zustand** — „eine Frau sitzt an einem Tisch". Bei Video beschreiben Sie eine **Handlung** — „die Frau steht auf, geht zum Fenster und blickt hinaus".

```
❌ „Die Beraterin hat dem Kunden die App erklärt."  (Vergangenheit)
❌ „Die Beraterin wird die App erklären."           (Zukunft)
✅ „Die Beraterin erklärt dem Kunden die App."      (Präsens)
✅ „The consultant explains the app to the customer." (Präsens)
```

**Warum:** KI-Videomodelle interpretieren Prompts als „was gerade passiert". Vergangenheitsformen verwirren das Modell, Gegenwartsformen erzeugen die klarsten Ergebnisse.

### Sprache: Deutsch oder Englisch?

| Modell | Deutsch? | Empfehlung |
|--------|---------|------------|
| **Veo 3.1** | ✅ Für Dialoge gut | Prompt auf Englisch, Dialoge auf Deutsch möglich |
| **Sora 2** | ✅ Gut (über ChatGPT) | Deutsch funktioniert, Englisch manchmal präziser |
| **Kling 2.6** | ⚠️ Eingeschränkt | Englisch empfohlen |
| **Runway Gen-4.5** | ⚠️ Eingeschränkt | Englisch empfohlen |
| **Luma Ray3** | ⚠️ Eingeschränkt | Englisch empfohlen |
| **Pika 2.5** | ⚠️ Eingeschränkt | Englisch empfohlen |
| **Seedance 2.0** | ⚠️ Chinesisch/Englisch | Englisch, teils Chinesisch bevorzugt |
| **Wan 2.2 / LTX-2** | ❌ Kaum | Englisch |

**Faustregel für Video:** Prompt-Beschreibungen auf **Englisch** liefern bei den meisten Modellen bessere Ergebnisse. **Dialoge** (gesprochener Text im Video) können bei Veo und Sora auch auf Deutsch geschrieben werden — die KI generiert dann deutschsprachiges Audio.

---

## Modellvergleich auf einen Blick

### Technische Spezifikationen (Stand: Februar 2026)

```
┌─────────────────────────────────────────────────────────────────────┐
│                    MODELLVERGLEICH: DAS WESENTLICHE                  │
├──────────────┬──────────┬──────────┬────────┬───────┬──────────────┤
│ Modell       │ Max.     │ Max.     │ Audio  │ Preis │ Besonderheit │
│              │ Länge    │ Auflösg. │ nativ? │ ab    │              │
├──────────────┼──────────┼──────────┼────────┼───────┼──────────────┤
│ Veo 3.1      │ ~12 Sek. │ 4K      │ ✅     │ 20$/m │ Bestes Audio │
│ Sora 2       │ ~25 Sek. │ 1080p   │ ✅     │ 20$/m │ Längste Clips│
│ Runway G-4.5 │ ~10 Sek. │ 4K      │ ⚠️     │ 12$/m │ Profi-Tools  │
│ Kling 2.6    │ ~2 Min.  │ 1080p   │ ✅     │ Free  │ Preis/Leist. │
│ Luma Ray3    │ ~8 Sek.  │ 4K HDR  │ ⚠️     │ 8$/m  │ Physik       │
│ Pika 2.5     │ ~8 Sek.  │ 1080p   │ ⚠️     │ 10$/m │ Kreativ-FX   │
│ Seedance 2.0 │ ~15 Sek. │ 2K      │ ✅     │ Free* │ Ultra-real   │
│ Wan 2.2      │ variabel │ 720p    │ ❌     │ Free  │ Open Source  │
│ LTX-2        │ variabel │ 4K      │ ✅     │ Free  │ OS + Audio   │
└──────────────┴──────────┴──────────┴────────┴───────┴──────────────┘
                                              * = CN-Account nötig
```

### Was kostet das? KI-Video vs. klassische Videoproduktion

| Szenario | Klassisch | KI-generiert | Ersparnis |
|----------|-----------|-------------|-----------|
| **15-Sek. Social-Media-Reel** | 500–2.000 € (Dreh + Schnitt) | 0–5 € (ein Abo-Monat) | 95–100% |
| **60-Sek. Erklärvideo (animiert)** | 3.000–8.000 € (Agentur) | 20–60 € (Abo + Iterationen) | 97–99% |
| **Recruiting-Teaser (3 Clips)** | 5.000–15.000 € (Filmteam) | 20–60 € | 99% |
| **Produktvideo für Webseite** | 2.000–5.000 € (Dreh vor Ort) | 20–100 € (mehrere Iterationen) | 95–98% |
| **Imagefilm (2–3 Min.)** | 10.000–30.000 € (Produktion) | ❌ Noch nicht empfohlen | — |
| **Schulungsvideo mit echten MA** | 3.000–8.000 € (interner Dreh) | ❌ Nicht empfohlen | — |

**Aber:** Genau wie bei Bildern gilt — die **Zeiteinsparung** ist oft wichtiger als die Kostenersparnis. Ein Social-Media-Reel, das in 5 Minuten statt 5 Tagen entsteht, verändert Ihre Content-Strategie fundamental.

> **Praxis-Tipp:** Nutzen Sie KI-Video für die **ersten 80%** — Konzepte, Social-Media-Content, interne Kommunikation, Pitch-Videos. Investieren Sie Produktionsbudget in die **letzten 20%** — den Imagefilm, das Schulungsvideo mit echten Mitarbeitern, den professionellen Recruitingfilm.

---

## Was KI-Video (noch) nicht kann

### Die ehrlichen Grenzen

| Limitation | Auswirkung im Bankalltag | Workaround |
|-----------|------------------------|------------|
| **Maximale Clip-Länge** | Die meisten Modelle erzeugen 8–25 Sekunden. Für längere Videos müssen Sie Clips aneinanderschneiden | Scene Extension nutzen, oder mehrere Clips in einem Videoeditor zusammenfügen |
| **Konsistenz über Szenen** | Dieselbe Person sieht in Szene 2 anders aus als in Szene 1 — Kleidung, Gesicht, Haarfarbe können variieren | Image-to-Video: Immer dasselbe Startbild für dieselbe Figur. Oder: Seedance 2.0 @ Reference System |
| **Hände und feine Details** | Finger, Schmuck, kleine Texte — werden oft falsch dargestellt | Kritisch prüfen. Szenen mit sichtbaren Händen mehrfach generieren. Hände aus dem Frame halten |
| **Text im Video** | Überschriften, Logos, Untertitel — unzuverlässig | Text NACHTRÄGLICH in einem Videoeditor (CapCut, Canva, Premiere) einfügen |
| **Echte Personen** | KI kann keine Videos echter Mitarbeiter erzeugen, die authentisch aussehen | Für Teamvideos: Echte Aufnahmen. KI nur für Konzept-Personen oder animierte Stile |
| **Exakte Markentreue** | Corporate Design, exakte Farben, Logo-Platzierung — KI kennt Ihr CD nicht | Farben als HEX im Prompt. Logo nachträglich einblenden. Oder: LoRA-Training (Open Source) |
| **Rechtliche Klarheit** | Urheberrecht bei KI-Videos in EU noch unklar. Persönlichkeitsrechte bei realistischen Personen | Für kommerzielle Nutzung: Rechtslage prüfen. Keine realen Personen ohne Einwilligung generieren |
| **Längere Narrative** | Videos über 30 Sekunden mit kohärenter Handlung — noch nicht zuverlässig | Multi-Clip-Workflow: Einzelne Szenen generieren, dann schneiden |

### Die ehrliche Einschätzung

KI-Video ist **hervorragend für:**
- Social-Media-Reels und -Shorts (5–15 Sekunden)
- Konzeptvideos und Mood-Videos für interne Pitches
- Animierte Erklärclips
- Schnelle Visualisierung von Ideen
- Event-Teaser und Ankündigungen
- Prototyping vor dem professionellen Dreh

KI-Video ist **nicht geeignet für:**
- Imagefilme über 60 Sekunden mit durchgängiger Handlung
- Schulungsvideos mit echten Mitarbeitern
- Rechtsverbindliche oder compliance-kritische Videoinhalte
- Videos, die 100% Markentreue ohne Nachbearbeitung erfordern
- Dokumentation realer Ereignisse (Hauptversammlungen, Events)

> **Volksbank-Analogie:** KI-Video ist wie ein guter Entwurf — perfekt, um dem Vorstand zu zeigen, wie die Kampagne aussehen könnte. Aber den finalen Film drehen Sie mit dem Filmteam. Noch. In einem Jahr könnte das anders sein.

---

## Entscheidungsbaum: Welches Modell für welchen Zweck?

```
                        Was brauchen Sie?
                             │
          ┌──────────────────┼──────────────────┐
          ▼                  ▼                  ▼
     Video MIT           Video OHNE         Volle
     Audio/Dialog        Audio              Kontrolle
          │                  │                  │
     ┌────┴────┐        ┌───┴───┐          ┌───┴───┐
     ▼         ▼        ▼       ▼          ▼       ▼
   Budget?   Beste    Profi-  Kreative   Daten-  Marken-
     │       Qualität Tools?  Effekte?   schutz? training?
     │         │        │       │          │       │
  ┌──┴──┐     ▼        ▼       ▼          ▼       ▼
  ▼     ▼  Veo 3.1  Runway   Pika      Wan 2.2  LTX-2
Klein  Groß          Gen-4.5  2.5      (lokal)  (lokal)
  │     │
  ▼     ▼
Kling  Sora 2
2.6    (25 Sek.)
```

### Schnellempfehlung nach Anwendungsfall

| Anwendungsfall | Erstwahl | Alternative |
|---------------|----------|-------------|
| **Social-Media-Reel** (schnell, günstig) | Kling 2.6 | Pika 2.5 |
| **Recruiting-Teaser** (professionell) | Veo 3.1 | Sora 2 |
| **Erklärvideo** (animiert, mit Sprechtext) | Veo 3.1 | Sora 2 |
| **Produktvideo** (Startbild animieren) | Runway Gen-4.5 | Luma Ray3 |
| **Internes Pitch-Video** (schnell) | Sora 2 (ChatGPT) | Kling 2.6 |
| **Physik-Demo** (Produkt in Aktion) | Luma Ray3 | Veo 3.1 |
| **Corporate-CI-konform** (eigene Marke trainiert) | Wan 2.2 + LoRA | LTX-2 |
| **Virales Social-Media** (kreative Effekte) | Pika 2.5 | Kling 2.6 |
| **Datenschutz-kritisch** (EU, DSGVO) | LTX-2 (lokal) | Wan 2.2 (lokal) |

---

## Zugang: Wo und wie nutzen Sie diese Modelle?

Für Einsteiger ist der Zugang oft die größte Hürde. Hier die unkompliziertesten Wege zu jedem Modell:

| Modell | Einfachster Zugang | Was Sie brauchen |
|--------|-------------------|-----------------|
| **Veo 3.1** | [gemini.google.com](https://gemini.google.com) → Google AI Pro/Ultra Abo | Google-Account + Abo (19,99 $/Monat) |
| **Sora 2** | [chatgpt.com](https://chatgpt.com) → ChatGPT Plus/Pro | OpenAI-Account + Abo (20 $/Monat) |
| **Runway Gen-4.5** | [app.runwayml.com](https://app.runwayml.com) | Runway-Account (ab 12 $/Monat) |
| **Kling 2.6** | [klingai.com](https://klingai.com) | E-Mail-Registrierung (Free Tier) |
| **Luma Ray3** | [lumalabs.ai/dream-machine](https://lumalabs.ai/dream-machine) | E-Mail-Registrierung (Free Tier) |
| **Pika 2.5** | [pika.art](https://pika.art) | E-Mail-Registrierung (Free Tier) |
| **Seedance 2.0** | [jianying.com](https://jianying.com) | Douyin-Account (CN-Nummer nötig) |
| **Wan 2.2** | [fal.ai](https://fal.ai) oder [replicate.com](https://replicate.com) | Account + API-Credits |
| **LTX-2** | [fal.ai](https://fal.ai) oder lokal via ComfyUI | Account + API-Credits oder eigene GPU |

**Tipp für den Einstieg:** Starten Sie mit **Kling 2.6** (kostenlos, großzügig) oder **Veo 3.1** in Gemini (wenn Sie bereits ein Google-AI-Abo haben). Beide bieten den besten Einstieg mit dem geringsten Aufwand.

> **Volksbank-Analogie:** Denken Sie an die verschiedenen Kontoeröffnungswege — Online in 5 Minuten (Kling, Luma), per Videoident mit Abo (Veo, Sora), oder persönlich in der Filiale mit vollständiger Legitimation (lokale Installation von Wan/LTX-2). Je mehr Aufwand, desto mehr Kontrolle.

---

## Hands-on Übung 1: Modell-Vergleich

**Aufgabe:** Verwenden Sie den folgenden Prompt in mindestens zwei Modellen und vergleichen Sie die Ergebnisse.

**Basis-Prompt:**
```
A glass door of a modern bank branch opens. A young woman in
business attire enters, smiles at the camera, and walks toward
the reception desk. Morning sunlight through large windows.
Camera: static wide shot. Style: corporate documentary,
warm color grading. Duration: 5 seconds.
```

**Beobachten Sie:**
1. Wie flüssig ist die Türbewegung? Öffnet sich die Tür realistisch?
2. Wie natürlich geht die Person? (Achten Sie auf Füße und Arme)
3. Stimmen Beleuchtung und Schatten über die gesamte Dauer?
4. Wie unterscheidet sich die „Stimmung" zwischen den Modellen?
5. Falls Audio generiert wurde — passt es zur Szene?

**Empfohlene Modelle zum Testen:** Kling 2.6 (kostenlos) + Veo 3.1 oder Sora 2 (Abo).

---

## Hands-on Übung 2: Das 8-Bausteine-Framework anwenden

**Aufgabe:** Wählen Sie eines der folgenden Szenarien und füllen Sie das Framework aus:

**Szenario A:** Ein 10-Sekunden-Recruiting-Reel für Instagram
**Szenario B:** Ein 15-Sekunden-Erklärvideo zur neuen Banking-App
**Szenario C:** Ein 8-Sekunden-Event-Teaser für die Hauptversammlung

Füllen Sie aus:
1. **Stil/Genre:** ___
2. **Subjekt:** ___
3. **Ort/Setting:** ___
4. **Aktion:** ___
5. **Kamera:** ___
6. **Dialog:** ___ (falls gewünscht)
7. **Audio:** ___
8. **Licht/Stimmung:** ___

Dann: Formulieren Sie daraus einen zusammenhängenden Prompt und generieren Sie ein Video mit einem Modell Ihrer Wahl.

---

## Hands-on Übung 3: Text-to-Video vs. Image-to-Video

**Aufgabe:** Erstellen Sie dasselbe Motiv auf zwei Wegen und vergleichen Sie.

**Schritt 1 — Text-to-Video:**
```
A modern laptop on a clean white desk. The screen shows
a banking dashboard with charts. A hand moves the mouse,
clicking through different tabs. Soft ambient light.
Close-up, shallow depth of field.
```

**Schritt 2 — Image-to-Video:**
Generieren Sie zuerst ein **Bild** des Szenarios (mit ChatGPT, Gemini oder einem Bildgenerator). Laden Sie dieses Bild dann als Startframe in ein Videomodell (Runway, Kling oder Luma) und prompten Sie:
```
The hand moves the mouse, clicking through different tabs
on the banking dashboard. Smooth cursor movement. 5 seconds.
```

**Vergleichen Sie:**
1. Welcher Weg erzeugt das realistischere Ergebnis?
2. Welcher gibt Ihnen mehr Kontrolle über das Aussehen?
3. Welcher ist schneller zum gewünschten Ergebnis?
4. Bei welchem stimmt die Beleuchtung besser?

---

## Zusammenfassung

| Was Sie gelernt haben | Kernaussage |
|-----------------------|-------------|
| **Drei Wege zum Video** | Text-to-Video, Image-to-Video, Video-to-Video — jeder mit eigenen Stärken |
| **Audio als Game-Changer** | 4 von 8 Modellen generieren natives Audio inkl. Dialoge — das verändert alles |
| **8 Modelle** | Veo 3.1 (Regisseur), Sora 2 (Storyteller), Runway (Profi), Kling (Kraftpaket), Luma (Physiker), Pika (Kreative), Seedance (Disruptor), Open Source (Demokratisierer) |
| **8-Bausteine-Framework** | Stil → Subjekt → Ort → Aktion → Kamera → Dialog → Audio → Stimmung |
| **Kosten** | Von kostenlos (Kling, Open Source) bis 20 $/Monat (Veo, Sora) — 95–99% günstiger als klassische Videoproduktion |
| **Limitationen** | Clip-Länge (8–25 Sek.), Konsistenz über Szenen, Hände/Details, Text im Video |
| **Modell-Wahl** | Richtet sich nach Aufgabe, Budget, Datenschutz — kein Modell ist universell das Beste |
| **Image-to-Video** | Oft bessere Ergebnisse als Text-to-Video — mehr Kontrolle über das Aussehen |

---

## Ausblick: Was kommt als Nächstes?

In den folgenden Tutorials dieses Kapitels vertiefen wir jeden Aspekt:

- **04-02: Prompting für Bewegung und Kameraführung** — Denken wie ein Regisseur: Pan, Tilt, Dolly, Drohne, Shot-Typen, Timing
- **04-03: Audio, Sprache und Sounddesign** — Das Tonstudio: Dialoge, Soundeffekte, Musik, Voice-Over, Lip-Sync
- **04-04: Video-Editing und iteratives Verfeinern** — Der Schneidetisch: Multi-Clip-Workflows, Storyboards, Scene Extension
- **04-05: Prompt-Vorlagen: Videos für den Bankalltag** — Der Werkzeugkasten: Copy-Paste-Templates für Recruiting, Marketing, Schulung

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Text-to-Video (T2V)** | Videogenerierung rein aus Textbeschreibung, ohne visuelles Ausgangsmaterial |
| **Image-to-Video (I2V)** | Videogenerierung, die ein Standbild als Ausgangspunkt (ersten Frame) nutzt und per Prompt animiert |
| **Video-to-Video (V2V)** | Transformation eines bestehenden Videos durch KI — Stilwechsel, Hintergrundaustausch, Effekte |
| **Temporale Konsistenz** | Die Eigenschaft eines generierten Videos, dass Objekte, Farben und Personen über alle Frames hinweg identisch bleiben |
| **Scene Extension** | Funktion, um einen generierten Clip nahtlos zu verlängern — die KI erzeugt Folgeframes passend zum letzten Frame |
| **Lip-Sync** | Synchronisation von Mundbewegungen mit gesprochenem Text — bei nativem Audio automatisch, sonst manuell |
| **Natives Audio** | Audio (Sprache, Soundeffekte, Musik), das direkt vom Videomodell erzeugt wird — im Gegensatz zu nachträglich hinzugefügtem Sound |
| **Foley** | Filmtechnischer Begriff für nachträglich erzeugte Alltagsgeräusche (Schritte, Türen, Gläser). Bei LTX-2 nativ generiert |
| **LoRA (Low-Rank Adaptation)** | Methode, um ein KI-Modell effizient auf eigene Stile, Personen oder Marken nachzutrainieren — ohne das gesamte Modell neu zu trainieren |
| **MoE (Mixture of Experts)** | Architektur, bei der verschiedene spezialisierte „Experten-Module" je nach Aufgabe aktiviert werden — effizienter als ein einzelnes großes Modell |
| **Diffusion-Transformer** | Hybridarchitektur, die Diffusion-basierte Bildgenerierung mit Transformer-basierter Sequenzverarbeitung kombiniert — Basis der meisten aktuellen Videomodelle |
| **Keyframe** | Ein definierter Schlüsselpunkt in einem Video, an dem bestimmte Eigenschaften (Position, Kamera, Stil) festgelegt werden — die KI interpoliert dazwischen |
| **Credits** | Virtuelle Währung bei Plattformen wie Runway, Pika und Kling. Ein Clip kostet je nach Länge und Qualität unterschiedlich viele Credits |
| **Free Tier** | Kostenloser Zugang mit eingeschränkter Nutzung (begrenzte Credits, niedrigere Auflösung, Wasserzeichen) |
| **4K / 2K / 1080p** | Auflösungsstufen: 4K = 3840×2160 Pixel, 2K = 2560×1440, 1080p = 1920×1080. Höher = schärfer, aber rechenintensiver und teurer |
| **HDR** | High Dynamic Range — erweiterter Kontrastumfang für hellere Lichter und tiefere Schatten. Von Luma Ray3 unterstützt |
| **Dolly / Pan / Tilt / Zoom** | Kamerabewegungstypen: Dolly = Kamera fährt vor/zurück, Pan = schwenkt horizontal, Tilt = schwenkt vertikal, Zoom = Brennweite ändert sich |
| **Storyboard** | Visuelle Planung eines Videos als Abfolge von Einzelbildern (Szenen), bevor die eigentliche Produktion beginnt |
| **Content-Filter** | Automatische Prüfung, die bestimmte Inhalte (Gewalt, NSFW etc.) blockiert. Variiert stark zwischen Modellen |

---


