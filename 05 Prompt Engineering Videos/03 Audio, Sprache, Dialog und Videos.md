# Audio, Sprache und Sounddesign im Video

**Das Tonstudio — wenn das Video sprechen lernt: Dialoge, Soundeffekte, Musik, Voice-Over und Lip-Sync mit KI**

---

## Warum dieses Tutorial?

In Tutorial 04-01 haben Sie die Landkarte der KI-Videogenerierung kennengelernt — acht Modelle, drei Wege zum Video, das 8-Bausteine-Framework. In Tutorial 04-02 haben Sie gelernt, wie ein Regisseur zu denken — Kamerabewegungen, Shot-Typen, Timing in Beats.

Zwei Bausteine aus dem Framework haben wir dabei bewusst nur angerissen: **Dialog** und **Audio**. Genau diese beiden sind der Grund, warum dieses Tutorial existiert — und warum es bei Video ein eigenes Audio-Kapitel gibt, das bei Bildern (Kapitel 03) schlicht nicht nötig war.

Denn Audio ist nicht das Beiwerk zum Video. **Audio ist die Hälfte des Erlebnisses.**

Das klingt übertrieben? Dann machen Sie den Test: Schauen Sie einen emotionalen Filmclip ohne Ton. Dann mit Ton. Der Unterschied ist nicht graduell — er ist fundamental. Musik erzeugt Emotion, Dialoge transportieren Information, Soundeffekte erzeugen Glaubwürdigkeit. Ein stummes KI-Video wirkt wie eine PowerPoint-Animation. Ein KI-Video mit passendem Audio wirkt wie ein Clip aus einer Doku.

Und genau hier hat sich 2025/26 alles verändert: Vier der großen Videomodelle — Veo 3.1, Sora 2, Kling 2.6 und Seedance 2.0 — generieren Audio **nativ**. Das bedeutet: Sie schreiben einen Prompt mit Dialog und Soundbeschreibung, und das fertige Video kommt mit gesprochenen Worten, passenden Geräuschen und Hintergrundmusik zurück. In einem Schritt. Kein separates Tonstudio, kein Zusammenschneiden, kein externer Sprecher.

**Was Sie nach diesem Tutorial wissen werden:**

- Wie natives Audio in KI-Videomodellen funktioniert — technisch verständlich
- Wie Sie Dialoge in Video-Prompts schreiben, die die KI zuverlässig umsetzt
- Wie Sie Soundeffekte, Ambient-Sounds und Musik im Prompt steuern
- Welche Modelle welche Audio-Fähigkeiten haben — ehrlich und aktuell
- Wie Sie mit externen Audio-Tools (ElevenLabs, Suno, Adobe) arbeiten, wenn natives Audio nicht reicht
- Wie Lip-Sync funktioniert und was die Grenzen sind
- Wie Sie Voice-Over für Erklärvideos und Schulungen erzeugen
- Was das alles kostet — nativ vs. externer Audio-Workflow

---

## Ein kurzer Blick zurück: Die Geschichte des KI-Audios

Audio und KI haben eine eigenständige Geschichte, die parallel zur Bildgenerierung verlief — und erst 2025 mit der Videogenerierung verschmolz.

| Jahr | Meilenstein | Was sich änderte |
|------|-----------|-----------------|
| **2023 Jan** | **AudioLDM** (Haohe Liu et al.) | Erster Latent-Diffusion-Ansatz für Text-to-Audio. Bewies: Diffusion funktioniert nicht nur für Bilder |
| **2023 Jan** | **MusicLM** (Google) | Erster überzeugender Text-to-Music-Generator. 280.000 Stunden Musik als Training |
| **2023 Apr** | **Bark** (Suno) | Open-Source-TTS mit Emotionen, Lachen, Pausen — erstmals „menschlich klingende" KI-Stimmen |
| **2023 Nov** | **Suno v1** | KI-generierte Songs mit Gesang — der „ChatGPT-Moment" für Musik |
| **2024 Apr** | **Udio** | Konkurrent zu Suno — höhere Audioqualität, kürzere Clips, mehr Kontrolle |
| **2024 Jun** | **ElevenLabs v2** | Voice Cloning in Minuten. 5.000+ Stimmen in 70+ Sprachen. Der Standard für TTS |
| **2024 Nov** | **Suno v4** | Komplette Songs (4+ Minuten) in 30 Sekunden. Studioqualität. Stems-Export |
| **2025 Mai** | **Veo 3** (Google) | **Der Wendepunkt:** Erstes Videomodell mit nativem synchronisiertem Audio — Dialog, Soundeffekte, Musik in einem Schritt |
| **2025 Sep** | **Sora 2** (OpenAI) | Natives Audio nachgezogen: synchronisierte Dialoge und Soundeffekte |
| **2025 Okt** | **Kling 2.6** (Kuaishou) | Natives Audio + Lip-Sync in 8 Sprachen |
| **2025 Dez** | **Suno v5** | ELO-Score 1.293 — übertrifft alle Vorgänger in Audioqualität und Stimmrealismus |
| **2026 Jan** | **LTX-2** (Lightricks) | Open Source mit nativem Audio: Foley, Ambience, Lip-Sync |
| **2026 Jan** | **Google Lyria 3** | Googles Musik-KI, integriert in Gemini — kostenlose Soundtracks für Videos |
| **2026 Feb** | **Seedance 2.0** (ByteDance) | Dual-Branch-Transformer: Video und Audio werden **gleichzeitig** generiert — beste Synchronisation |

**Das Bemerkenswerte:** Bis Mai 2025 waren KI-Videos stumm. Innerhalb von neun Monaten wurde natives Audio zum Standard. Die Verschmelzung von Video- und Audio-KI ist der größte Qualitätssprung seit der Einführung von Text-to-Video selbst.

> **Volksbank-Analogie:** Erinnern Sie sich an die Einführung von Videotelefonie? Jahrelang gab es Telefon (= Audio) und Bildschirm (= Video) getrennt. Dann kamen Zoom und Teams — und plötzlich waren Bild und Ton untrennbar verbunden. Genau dasselbe passiert gerade bei KI-Video: Audio ist nicht mehr optional, es ist integriert.

---

## Die vier Audio-Ebenen eines Videos

Bevor wir in die Praxis eintauchen, müssen Sie verstehen, aus welchen Bausteinen der Ton eines Videos besteht. Professionelle Tontechniker arbeiten mit vier Ebenen — und genau diese vier können Sie jetzt per Prompt steuern:

```
┌──────────────────────────────────────────────────────────┐
│              DIE VIER AUDIO-EBENEN                        │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  EBENE 1: DIALOG                                         │
│  ═══════════════                                         │
│  Was Personen sagen. Gesprochene Worte,                  │
│  Unterhaltungen, Monologe, Voice-Over.                   │
│  → Die informativste Ebene                               │
│                                                          │
│  EBENE 2: SOUNDEFFEKTE (SFX)                             │
│  ═════════════════════════                                │
│  Geräusche, die durch Aktionen entstehen:                │
│  Türen öffnen, Tastatur tippen, Glas abstellen,          │
│  Schritte, Papier rascheln.                              │
│  → Die glaubwürdigste Ebene                              │
│                                                          │
│  EBENE 3: AMBIENT / ATMOSPHÄRE                           │
│  ══════════════════════════════                           │
│  Hintergrundgeräusche der Umgebung:                      │
│  Büro-Gemurmel, Straßenverkehr, Vogelgezwitscher,        │
│  Klimaanlage, entferntes Telefonklingeln.                │
│  → Die immersivste Ebene                                 │
│                                                          │
│  EBENE 4: MUSIK                                          │
│  ════════════════                                        │
│  Hintergrundmusik, Score, Jingles.                       │
│  Setzt Stimmung und Emotion.                             │
│  → Die emotionalste Ebene                                │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Warum die Reihenfolge wichtig ist

In der professionellen Tonmischung gibt es eine klare Hierarchie: **Dialog ist König**. Alles andere ordnet sich unter. Wenn der Dialog nicht verständlich ist, ist das Video gescheitert — egal wie gut die Musik klingt.

Dieselbe Hierarchie gilt für KI-Video-Prompts:

```
Dialog > Soundeffekte > Ambient > Musik

  Wenn Sie nur eine Audio-Ebene beschreiben können:
  → Beschreiben Sie den Dialog.

  Wenn Sie zwei beschreiben können:
  → Dialog + die wichtigsten Soundeffekte.

  Wenn Sie alle vier beschreiben:
  → Dialog zuerst, dann SFX, dann Ambient, dann Musik.
```

> **Volksbank-Analogie:** Stellen Sie sich ein Beratungsgespräch vor. Das Wichtigste ist, was gesagt wird (Dialog). Dann die Geräusche, die das Gespräch begleiten — der Kugelschreiber auf dem Papier, das Umblättern der Unterlagen (SFX). Im Hintergrund das gedämpfte Büroleben (Ambient). Und wenn Ihr Imagefilm daraus wird, kommt dezente Musik dazu (Score). Genau diese Hierarchie.

---

## Natives Audio: Wie es technisch funktioniert

### Der alte Weg: Video und Audio getrennt

Bis Mai 2025 war der Workflow für KI-Video mit Audio ein Fünf-Schritte-Prozess:

```
┌──────────────────────────────────────────────────────────┐
│           DER ALTE WEG: GETRENNTE PRODUKTION              │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  Schritt 1: Video generieren (stumm)                     │
│       ↓                                                  │
│  Schritt 2: Dialog aufnehmen oder per TTS erzeugen       │
│       ↓                                                  │
│  Schritt 3: Soundeffekte suchen oder generieren          │
│       ↓                                                  │
│  Schritt 4: Musik auswählen oder generieren              │
│       ↓                                                  │
│  Schritt 5: Alles in einem Videoeditor synchronisieren   │
│       ↓                                                  │
│  Ergebnis: Fertiges Video mit Audio                      │
│                                                          │
│  Zeit: 30–120 Minuten pro Clip                           │
│  Tools: 3–5 verschiedene                                 │
│  Können: Videoediting-Grundkenntnisse nötig              │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Der neue Weg: Natives Audio

Seit Veo 3 (Mai 2025) funktioniert es so:

```
┌──────────────────────────────────────────────────────────┐
│           DER NEUE WEG: NATIVE AUDIO-GENERIERUNG          │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  Schritt 1: Prompt schreiben (Video + Audio zusammen)    │
│       ↓                                                  │
│  Schritt 2: KI generiert Video + Audio gleichzeitig      │
│       ↓                                                  │
│  Ergebnis: Fertiges Video mit synchronisiertem Audio     │
│                                                          │
│  Zeit: 1–3 Minuten pro Clip                              │
│  Tools: 1                                                │
│  Können: Prompt-Schreiben reicht                         │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Die technische Magie dahinter

Wie schaffen es Modelle wie Veo 3.1 oder Seedance 2.0, Video und Audio gleichzeitig zu generieren? Die Kernidee ist überraschend elegant:

**Klassisches Videomodell (bis 2025):**
Das Modell lernt nur, wie Bilder aussehen — Frame für Frame. Es hat keine Ahnung, wie die Welt *klingt*.

**Audio-Video-Modell (ab 2025):**
Das Modell lernt aus Millionen von Videos *mit* Tonspur. Es sieht: Wenn eine Tür sich öffnet, gibt es ein Knarzen. Wenn jemand den Mund bewegt, gibt es Sprache. Wenn Regen fällt, gibt es Prasseln. Es lernt die **Korrelation zwischen Pixeln und Schallwellen**.

```
┌──────────────────────────────────────────────────────────┐
│        WIE NATIVES AUDIO TECHNISCH FUNKTIONIERT           │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  Training:                                               │
│  ┌────────────────┐                                      │
│  │ Millionen       │     Das Modell lernt:               │
│  │ Videos MIT     │ →   Tür öffnet = Knarzen             │
│  │ Tonspur        │     Mund bewegt = Sprache            │
│  │ (YouTube etc.) │     Regen sichtbar = Prasseln        │
│  └────────────────┘     Straße = Verkehrsrauschen        │
│                                                          │
│  Generierung:                                            │
│  ┌────────┐    ┌──────────────────────┐    ┌──────────┐  │
│  │ Ihr    │ →  │ Modell generiert     │ →  │ Video +  │  │
│  │ Prompt │    │ Video-Frames UND     │    │ Audio    │  │
│  │        │    │ Audio-Waveform       │    │ synchro- │  │
│  │        │    │ GLEICHZEITIG         │    │ nisiert  │  │
│  └────────┘    └──────────────────────┘    └──────────┘  │
│                                                          │
│  Seedance 2.0 geht noch weiter:                          │
│  Dual-Branch-Transformer — zwei spezialisierte           │
│  Netzwerke (Video + Audio) die parallel arbeiten         │
│  und sich gegenseitig informieren.                       │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** Stellen Sie sich vor, Sie schulen einen neuen Mitarbeiter. Der alte Weg: Erst zeigen Sie ihm, wie ein Formular aussieht (visuell). Dann erklären Sie separat, was er sagen soll (Audio). Er muss beides selbst zusammenbringen. Der neue Weg: Sie führen das komplette Beratungsgespräch vor — er sieht und hört gleichzeitig, wie Bild und Ton zusammengehören. Natürlich lernt er so schneller, wie beides zusammenpasst.

---

## Dialoge im Video-Prompt: Die Kunst des Drehbuchs

### Die drei Arten, Dialog zu prompten

Es gibt drei grundlegend verschiedene Wege, wie Sie Personen in KI-Videos sprechen lassen können:

#### Art 1: Expliziter Dialog — Sie schreiben die exakten Worte

```
Prompt-Beispiel (explizit):

A bank consultant in a modern office looks at the camera
and says: Good morning! Today I'll show you how easy it is
to open an account with us. She smiles warmly. Soft office
ambient sounds. (no subtitles)
```

**Vorteile:** Volle Kontrolle über den Wortlaut. Perfekt für Skripte.
**Nachteile:** Text muss in ~8 Sekunden sprechbar sein. Zu viel Text = zu schnelles Sprechen.

#### Art 2: Impliziter Dialog — Sie beschreiben das Thema

```
Prompt-Beispiel (implizit):

A bank consultant warmly explains the benefits of mobile
banking to a customer. She gestures toward a tablet on the
desk. Conversational, friendly tone. Office ambient sounds.
```

**Vorteile:** Natürlicher klingend, KI improvisiert überzeugend.
**Nachteile:** Keine Kontrolle über den exakten Wortlaut. Kann überraschen.

#### Art 3: Narrativer Voice-Over — Eine Stimme erzählt über die Bilder

```
Prompt-Beispiel (Voice-Over):

Montage of a modern bank branch: customers entering, consultants
smiling, a hand signing a document. A warm, male narrator says:
"At Volksbank Hellweg, banking is more than numbers. It's about
the people behind every decision." Soft, uplifting piano music
in the background.
```

**Vorteile:** Professioneller Dokumentarstil. Trennung von Bild und Text.
**Nachteile:** Lip-Sync ist kein Thema (niemand sieht den Sprecher). Aber: Stimme muss zum Bild passen.

### Die goldenen Regeln für Dialog-Prompts

```
┌──────────────────────────────────────────────────────────┐
│         DIE 7 GOLDENEN REGELN FÜR DIALOG-PROMPTS         │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  1. KURZ HALTEN                                          │
│     Max. 2–3 Sätze pro 8-Sekunden-Clip.                  │
│     Faustregel: ~15–20 Wörter = 8 Sekunden.              │
│                                                          │
│  2. EIN BIS ZWEI SPRECHER PRO CLIP                       │
│     Mehr als zwei Sprecher → Stimmen verschmelzen         │
│     oder werden verwechselt.                             │
│                                                          │
│  3. DOPPELPUNKT STATT ANFÜHRUNGSZEICHEN                  │
│     ✅ She says: Good morning!                           │
│     ❌ She says "Good morning!"                          │
│     (Anführungszeichen erzeugen oft Untertitel)          │
│                                                          │
│  4. (NO SUBTITLES) ANHÄNGEN                              │
│     Viele Modelle generieren sonst Texteinblendungen.    │
│     ✅ ... says: Welcome to our bank. (no subtitles)     │
│                                                          │
│  5. SPRECHWEISE BESCHREIBEN                              │
│     ✅ He says enthusiastically: ...                     │
│     ✅ She whispers: ...                                 │
│     ✅ In a calm, professional tone, he says: ...        │
│                                                          │
│  6. SPRECHER EINDEUTIG IDENTIFIZIEREN                    │
│     ✅ The woman in the navy blazer says: ...            │
│     ✅ The older man with glasses responds: ...          │
│     ❌ Someone says: ...                                 │
│                                                          │
│  7. DIALOG VOR AUDIO-BESCHREIBUNG PLATZIEREN             │
│     Erst was gesagt wird, dann Ambient/Musik.            │
│     Das Modell priorisiert, was zuerst kommt.            │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Praxis: Ein Dialog-Prompt Schritt für Schritt

Nehmen wir an, Sie wollen einen 8-Sekunden-Clip für ein Recruiting-Video: Eine Beraterin begrüßt einen neuen Kollegen.

**Schritt 1 — Szene beschreiben:**
```
A modern bank office with glass walls and warm morning light.
```

**Schritt 2 — Personen und Aktion:**
```
A 30-year-old woman in a navy blazer stands near the entrance.
A young man in business casual walks toward her.
```

**Schritt 3 — Dialog hinzufügen (explizit, Doppelpunkt-Format):**
```
The woman smiles and says: Welcome to the team! I'll show you
around today. The man nods and responds: Thanks, I'm really
excited to be here. (no subtitles)
```

**Schritt 4 — Audio-Atmosphäre ergänzen:**
```
Soft office ambient sounds — distant keyboard clicks, muffled
conversations. No music.
```

**Kompletter Prompt:**
```
A modern bank office with glass walls and warm morning light.
A 30-year-old woman in a navy blazer stands near the entrance.
A young man in business casual walks toward her. She smiles
and says: Welcome to the team! I'll show you around today.
He nods and responds: Thanks, I'm really excited to be here.
(no subtitles) Soft office ambient sounds — distant keyboard
clicks, muffled conversations. No music.
Camera: static medium shot, eye level. 8 seconds.
```

### Modellspezifische Dialog-Tipps

| Modell | Dialogqualität | Besondere Tipps |
|--------|---------------|-----------------|
| **Veo 3.1** | ✅ Beste | Doppelpunkt-Format. Dialog auf Englisch am zuverlässigsten. Deutsch für Dialoge möglich, aber weniger konsistent. „(no subtitles)" immer anhängen |
| **Sora 2** | ✅ Sehr gut | Natürliche Sprache, versteht Konversationen. Dialog kann länger sein (bis 25 Sek. Clip). Auch deutschsprachige Dialoge möglich |
| **Kling 2.6** | ✅ Gut | Lip-Sync in 8 Sprachen. Dialog kurz halten (1–2 Sätze). Separate „Audio"-Sektion hilft |
| **Seedance 2.0** | ✅ Sehr gut | Dual-Branch: Beste Audio-Video-Synchronisation. Dialog auf Englisch oder Chinesisch |
| **LTX-2** | ⚠️ Basis | Einfache Dialoge möglich. Stärker bei Foley/Ambient als bei Sprache |
| **Runway Gen-4.5** | ⚠️ Begrenzt | Audio experimentell. Dialog unzuverlässig. Besser: externes TTS |
| **Luma Ray3** | ❌ Kein Dialog | Nur einfache Soundeffekte. Dialog extern hinzufügen |
| **Pika 2.5** | ❌ Kein Dialog | Nur einfache Soundeffekte. Dialog extern hinzufügen |

### Sprache: Deutsch oder Englisch im Dialog?

Eine der häufigsten Fragen — und die ehrliche Antwort ist differenziert:

| Aspekt | Englisch | Deutsch |
|--------|---------|---------|
| **Prompt-Beschreibung** (Szene, Kamera, Stil) | ✅ Empfohlen für alle Modelle | ⚠️ Nur Veo 3.1 und Sora 2 verstehen es gut |
| **Gesprochener Dialog** im Video | ✅ Beste Qualität bei allen Modellen | ✅ Veo 3.1 und Sora 2: gut. Kling: 8 Sprachen inkl. Deutsch. Andere: schwach |
| **Voice-Over / Narrator** | ✅ Standard | ⚠️ Akzent manchmal nicht authentisch deutsch |

**Praxis-Empfehlung für den Bankalltag:**
- Wenn das Video **intern** genutzt wird (Social Media DE, Intranet): Dialog auf Deutsch prompten, bei Veo 3.1 oder Sora 2
- Wenn die Qualität **perfekt** sein muss: Dialog auf Englisch generieren, dann mit externem TTS (ElevenLabs) deutsch übersprechen
- Für **internationale Inhalte**: Englisch als Basis, dann Dubbing über ElevenLabs

> **Volksbank-Analogie:** Es ist wie bei Formularen: Die Vorlage schreiben Sie auf Deutsch (für den Kunden verständlich). Aber die Software dahinter läuft oft auf Englisch (für die Maschine optimiert). Beim KI-Video gilt dasselbe: Die Szene beschreiben Sie auf Englisch (für die KI), der Dialog kann auf Deutsch sein (für Ihr Publikum).

---

## Soundeffekte und Foley: Die unsichtbare Magie

### Was sind Foley-Sounds?

Der Begriff stammt aus Hollywood. „Foley" sind die Alltagsgeräusche, die einen Film realistisch machen — Schritte auf verschiedenen Böden, das Rascheln von Kleidung, das Klicken eines Kugelschreibers, das Geräusch einer sich schließenden Tür. In professionellen Filmstudios gibt es eigene „Foley Artists", die diese Geräusche live zum Film nachproduzieren.

Bei KI-Video werden Foley-Sounds auf drei Wegen erzeugt:

```
┌──────────────────────────────────────────────────────────┐
│           DREI WEGE ZU SOUNDEFFEKTEN                      │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  WEG 1: Nativ im Video-Prompt                           │
│  ─────────────────────────────                           │
│  Das Videomodell generiert passende Sounds               │
│  basierend auf dem, was im Video passiert.               │
│  Prompt: "A glass door opens with a soft whoosh"         │
│  → Veo 3.1, Sora 2, Kling 2.6, Seedance 2.0, LTX-2     │
│                                                          │
│  WEG 2: Separate Audio-KI                                │
│  ─────────────────────────                               │
│  ElevenLabs Sound Effects, Adobe Firefly Audio           │
│  generieren Sounds aus Textbeschreibungen.               │
│  Prompt: "Glass door opening in a modern office"         │
│  → Ergebnis: Audiodatei zum manuellen Einfügen           │
│                                                          │
│  WEG 3: Video-to-Audio-KI                                │
│  ────────────────────────                                │
│  Sie laden ein stummes Video hoch, die KI analysiert     │
│  die Szene und generiert passende Sounds.                │
│  → ElevenLabs Video-to-SFX, MMAudio                     │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Soundeffekte im Prompt beschreiben

Für natives Audio (Weg 1) beschreiben Sie Soundeffekte am besten als **Ergebnis der Aktion**, nicht als isolierten Sound:

```
❌ Schwach (isolierter Sound):
"Add a door opening sound effect."

✅ Stark (Sound als Teil der Aktion):
"A glass door opens with a soft pneumatic hiss. Footsteps
on polished marble floor."

❌ Schwach (zu vage):
"Office sounds."

✅ Stark (spezifisch):
"Distant keyboard clicking, the hum of an air conditioner,
muffled conversations from the next room, a phone buzzing
on a desk."
```

### Die wichtigsten Foley-Kategorien für den Bankalltag

| Kategorie | Beispiel-Sounds | Prompt-Formulierung |
|-----------|----------------|-------------------|
| **Büro-Basis** | Tastatur, Maus-Klick, Klimaanlage | `Soft keyboard typing, mouse clicks, low hum of air conditioning` |
| **Papier & Dokumente** | Umblättern, Stempel, Unterschrift | `Paper rustling, the scratch of a pen signing a document` |
| **Türen & Bewegung** | Glastür, Aufzug, Schritte | `Glass door slides open with a soft hiss, footsteps on tile` |
| **Technik** | Drucker, Telefon, Tablet-Tippen | `A printer whirring softly, phone buzzing on the desk` |
| **Kundenkontakt** | Handschlag, Kaffee, Kartenleser | `A firm handshake, coffee cup set down on saucer, card reader beeping` |
| **Außenbereich** | Straßenverkehr, Vögel, Wind | `Distant city traffic, birds chirping, light breeze` |

### Prompt-Beispiel: Foley-reiche Bankszene

```
Static medium shot. A consultant's desk in a quiet bank office.
Morning. She picks up a printed document (paper rustle), reviews
it briefly, then slides it across the desk to the customer
(paper sliding on wood). The customer picks up a pen (soft click)
and signs. Both smile. The consultant says: Perfect, everything
is set. (no subtitles)

Audio: Soft air conditioning hum throughout. Distant phone
ringing once. Pen scratching on paper during signing. No music.
Camera: static, warm side lighting from window. 8 seconds.
```

> **Volksbank-Analogie:** Foley-Sounds sind wie die nonverbale Kommunikation in einem Gespräch — Nicken, Lächeln, Handgesten. Sie sagen nichts Konkretes, aber ohne sie fehlt etwas. Ein Video ohne Foley wirkt wie ein Gespräch, bei dem der Gegenüber ausdruckslos starrt: technisch korrekt, aber seltsam.

---

## Ambient-Sounds: Die Atmosphäre einer Szene

Ambient-Sounds (Atmosphäre, Atmo) sind die Hintergrundgeräusche, die einen Ort definieren. Sie bemerken sie nicht bewusst — aber wenn sie fehlen, fühlt sich die Szene „tot" an.

### Ambient-Sounds nach Ort

| Ort | Typische Atmosphäre | Prompt-Formulierung |
|-----|-------------------|-------------------|
| **Bankfiliale (Schalterhalle)** | Gemurmel, Fußtritte, Piepen des Nummernautomaten | `Busy bank lobby ambience: muffled conversations, footsteps on marble, number ticket machine beeping` |
| **Beratungszimmer** | Gedämpft, Klimaanlage, entferntes Büroleben | `Quiet consultation room. Soft air conditioning hum, muffled office activity from beyond the glass wall` |
| **Großraumbüro** | Tastaturklappern, Gespräche, Drucker | `Open-plan office atmosphere: keyboard sounds, scattered conversations, printer whirring, phone ringing in the distance` |
| **Konferenzraum** | Ruhig, Projektor-Lüfter, Papier | `Conference room. Low projector fan hum, occasional paper shuffling, water being poured into a glass` |
| **Vorstand / Executive Office** | Sehr ruhig, Uhr tickt, Stadt gedämpft | `Executive office. Near silence. A wall clock ticking softly. Muffled city sounds from far below` |
| **Außenbereich / Filialfront** | Straße, Passanten, Vögel | `Street-level bank entrance. Passing pedestrians, distant traffic, birds, automatic door whooshing` |

### Die Lautstärke-Hierarchie

Ein häufiger Fehler: Alle Audio-Ebenen gleich laut beschreiben. In der Praxis gilt die folgende empfohlene Lautstärke-Verteilung:

```
Lautstärke-Hierarchie:

  DIALOG        ████████████████████  100%
  SFX           ████████████          60%
  AMBIENT       ████████              40%
  MUSIK         ██████                30%
```

Im Prompt können Sie das steuern mit Adjektiven:

| Lautstärke | Prompt-Begriffe |
|-----------|----------------|
| Laut/Vordergrund | `loud`, `prominent`, `close` |
| Normal | `natural`, `clear` |
| Leise/Hintergrund | `soft`, `distant`, `muffled`, `faint`, `subtle` |
| Kaum hörbar | `barely audible`, `very distant`, `whisper-quiet` |

```
Prompt-Beispiel mit Lautstärke-Steuerung:

The consultant speaks clearly: Welcome, how can I help you today?
(no subtitles)

Prominent: her voice, close and warm.
Soft: paper rustling as she adjusts documents on the desk.
Distant: muffled office conversations from the hallway.
Barely audible: the hum of the building's ventilation system.
No music.
```

---

## Musik im Video: Emotion per Prompt steuern

### Natives Musik im Video-Prompt

Die vier Audio-Modelle mit nativem Sound (Veo 3.1, Sora 2, Kling 2.6, Seedance 2.0) können auch Hintergrundmusik generieren. Die Qualität ist überraschend gut für kurze Clips — aber mit Einschränkungen.

**Was funktioniert:**
- Einfache Stimmungsmusik: Piano, Gitarre, Ambient-Electronic
- Genre-Angaben: „uplifting corporate music", „tense cinematic score"
- Instrumenten-Angaben: „soft piano melody", „gentle acoustic guitar"

**Was (noch) nicht gut funktioniert:**
- Komplexe Arrangements mit vielen Instrumenten
- Spezifische Melodien oder Harmonien
- Exakte BPM-Vorgaben
- Gesang in der Hintergrundmusik

### Musik im Prompt beschreiben

```
┌──────────────────────────────────────────────────────────┐
│         MUSIK-BESCHREIBUNG IM VIDEO-PROMPT                │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  FORMAT:                                                 │
│  [Stimmung] + [Instrument(e)] + [Tempo] + [Stil]        │
│                                                          │
│  BEISPIELE:                                              │
│                                                          │
│  Corporate / Professionell:                              │
│  "Soft, uplifting background music with piano and        │
│   gentle strings. Corporate, optimistic, moderate tempo" │
│                                                          │
│  Emotional / Imagefilm:                                  │
│  "Warm piano melody, slowly building. Hopeful,           │
│   cinematic. Minimal arrangement — piano only"           │
│                                                          │
│  Energetisch / Social Media:                             │
│  "Upbeat electronic music with a positive vibe.          │
│   Energetic but not aggressive. Modern, clean beat"      │
│                                                          │
│  Seriös / Geschäftsbericht:                              │
│  "Subtle ambient music. Low, warm tones. Almost          │
│   imperceptible — it sets mood without demanding          │
│   attention. No melody, just texture"                    │
│                                                          │
│  Kein Musik gewünscht:                                   │
│  "No music. Only natural ambient sounds and dialogue"    │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Dedizierte Musik-KIs für höhere Qualität

Wenn die native Musikgenerierung nicht reicht — und für professionellere Produktionen ist das oft der Fall — gibt es spezialisierte Musik-KIs:

| Tool | Was es kann | Kosten | Beste Anwendung |
|------|-----------|--------|-----------------|
| **Suno (v5)** | Komplette Songs (4+ Min) mit Gesang in 30 Sek. | Free Tier + ab 10 $/Mo | Social-Media-Jingles, Background-Songs, Kampagnen-Musik |
| **Udio** | Kürzere Clips (30–90 Sek), höhere Audioqualität, mehr Kontrolle | Free Tier + ab 10 $/Mo | Cinematic Scores, Werbemusik, präzise Stil-Kontrolle |
| **Google Lyria 3** | Musikgenerierung in Gemini integriert | In Gemini Advanced inklusive | Schnelle Soundtracks, lizenzfreie Hintergrundmusik |
| **AIVA** | Klassisch/orchestral, lizenzfrei für Kommerz | Free + ab 11 $/Mo | Orchestrale Scores, Imagefilme, Präsentationsmusik |
| **Soundraw** | Loop-basierte Background-Tracks, editierbar | Ab 16,99 $/Mo | Hintergrundmusik für Videos, anpassbare Länge |
| **Beatoven.ai** | Stimmungsbasierte Tracks, automatische Anpassung an Videolänge | Free + ab 6 $/Mo | Podcast-Untermalung, Erklärvideos, Hintergrund-Scores |

### Workflow: Video mit separater Musik

```
┌──────────────────────────────────────────────────────────┐
│    WORKFLOW: KI-VIDEO + SEPARATE KI-MUSIK                 │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  1. Video mit Veo/Sora generieren                        │
│     → Prompt enthält "No music" oder "minimal music"     │
│     → Nur Dialog + SFX + Ambient                         │
│                                                          │
│  2. Musik separat generieren                             │
│     → Suno: "Uplifting corporate, piano and light        │
│        strings, 15 seconds, moderate tempo, no vocals"   │
│     → ODER: Lyria in Gemini: "Background music for       │
│        a professional bank video, warm and inviting"     │
│                                                          │
│  3. Video + Musik zusammenführen                         │
│     → CapCut (kostenlos, einfach)                        │
│     → Canva Video Editor (Browser-basiert)               │
│     → Adobe Premiere (professionell)                     │
│     → DaVinci Resolve (kostenlos, professionell)         │
│                                                          │
│  4. Musik-Lautstärke anpassen                            │
│     → Musik auf ~20–30% des Dialog-Levels                │
│     → Faustregel: Wenn Sie den Dialog nicht klar         │
│       verstehen, ist die Musik zu laut                   │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** Native Musik im Video-Prompt ist wie die Wartemusik Ihrer Telefonanlage — funktional, okay, tut ihren Job. Separate Musik-KI ist wie ein Jingle, den ein Komponist für Ihre Kampagne schreibt — individueller, professioneller, aber Sie müssen ihn selbst einbauen. Für Social-Media-Reels reicht die Wartemusik. Für den Imagefilm wollen Sie den Jingle.

---

## Voice-Over: Die Erzählstimme für Erklärvideos

Voice-Over (VO) ist eine Stimme, die über den Bildern liegt, ohne dass ein Sprecher im Bild zu sehen ist. Der klassische Einsatz: Erklärvideos, Dokumentationen, Schulungsmaterial.

### Voice-Over im nativen Video-Prompt

Sie können Voice-Over direkt im Video-Prompt als Narrator-Stimme einbauen:

```
Prompt-Beispiel (nativer Voice-Over):

A montage of a modern bank branch: the entrance, the
consultation area, a team meeting behind glass walls.
Smooth, slow camera movements.

A warm male narrator says: At Volksbank Hellweg, we believe
that great banking starts with great people. Our team
combines tradition with innovation — every single day.
(no subtitles)

Soft, uplifting piano music in the background. Natural office
ambient sounds faintly underneath. Cinematic, warm color grading.
12 seconds.
```

**Einschränkungen des nativen Voice-Over:**
- Stimme ist zufällig — Sie können nicht wählen, wie der Narrator klingt
- Deutsch als VO-Sprache ist bei den meisten Modellen weniger natürlich als Englisch
- Emotion und Betonung sind schwer steuerbar
- Keine Stimmkonsistenz über mehrere Clips

### Externer Voice-Over: ElevenLabs als Standard

Für professionellen Voice-Over gibt es einen klaren Marktführer: **ElevenLabs**.

| Feature | Was es kann | Relevanz für Video |
|---------|-----------|-------------------|
| **Text-to-Speech** | 5.000+ Stimmen in 70+ Sprachen | Jede erdenkliche Stimme für jeden Clip |
| **Voice Cloning** | Eigene Stimme mit wenigen Minuten Audio klonen | Konsistente „Hausstimme" für alle Videos |
| **Emotionale Steuerung** | Freude, Empathie, Aufregung, Ruhe per Prompt | Stimme passt zur Szene |
| **Multilingual** | Deutsch, Englisch, + 68 weitere Sprachen | Ein Video, viele Sprachversionen |
| **Dubbing** | Automatische Synchronisation: Stimme + Lip-Sync | Internationalisierung bestehender Videos |

**Workflow: Video + ElevenLabs Voice-Over:**

```
1. Video generieren (stumm oder mit "no dialogue, no narrator")
2. Skript schreiben für den Voice-Over
3. ElevenLabs: Stimme wählen oder eigene klonen
4. Text eingeben → Audio generieren
5. In Videoeditor zusammenführen
6. Timing anpassen (Voice über passende Szenen legen)
```

**Kosten:**
- ElevenLabs Free: 10.000 Zeichen/Monat
- Starter: 5 $/Monat (30.000 Zeichen)
- Creator: 22 $/Monat (100.000 Zeichen)
- Pro: 99 $/Monat (500.000 Zeichen, Voice Cloning)

**Für automatisierte Workflows:** ElevenLabs bietet eine REST-API, über die Sie Text-to-Speech, Voice Cloning und Sound Effects programmatisch nutzen können. Suno und Udio bieten ebenfalls API-Zugang über Drittanbieter (z.B. Replicate). Ideal, wenn Sie regelmäßig viele Clips produzieren.

**Praxis-Tipp: Die eigene Bankstimme:**
Wenn Ihre Bank regelmäßig Videos produziert, klonen Sie die Stimme Ihres besten Sprechers (mit dessen Einverständnis!) bei ElevenLabs. Ab dann hat jedes Video dieselbe konsistente, professionelle „Hausstimme" — ohne dass der Sprecher jedes Mal verfügbar sein muss.

> **Volksbank-Analogie:** Ein nativer Voice-Over im KI-Video ist wie der Kollege, der spontan eine Ansage für den Anrufbeantworter einspricht — brauchbar, aber nicht optimal. ElevenLabs ist wie das professionelle Tonstudio, das Ihre Telefonansage aufnimmt — konsistent, professionell, wiederverwendbar. Für das schnelle Social-Media-Reel reicht der Kollege. Für die offizielle Schulungsreihe wollen Sie das Studio.

---

## Lip-Sync: Wenn der Mund zum Ton passt

Lip-Sync (Lippensynchronisation) ist die Kunst, dass die Mundbewegungen einer Person im Video exakt zu den gesprochenen Worten passen. In traditionellen Filmen passiert das natürlich — der Schauspieler spricht ja wirklich. Bei KI-generiertem Video ist es eine technische Herausforderung.

### Wie Lip-Sync bei KI-Video funktioniert

```
┌──────────────────────────────────────────────────────────┐
│              LIP-SYNC: ZWEI ANSÄTZE                       │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  ANSATZ 1: Natives Lip-Sync (integriert)                 │
│  ─────────────────────────────────────                   │
│  Das Videomodell generiert Video UND Audio zusammen.     │
│  Die Mundbewegungen entstehen synchron zur Sprache.      │
│                                                          │
│  Modelle: Veo 3.1, Sora 2, Kling 2.6, Seedance 2.0     │
│                                                          │
│  Vorteil: Ein Schritt, automatisch synchron              │
│  Nachteil: Nicht immer perfekt. Bei schnellem            │
│  Sprechen oder mehreren Personen kann es                 │
│  zu Asynchronität kommen.                                │
│                                                          │
│  ANSATZ 2: Nachträgliches Lip-Sync                       │
│  ────────────────────────────────                        │
│  Erst Video generieren (stumm), dann Audio separat       │
│  erzeugen, dann per Lip-Sync-Tool synchronisieren.       │
│                                                          │
│  Tools: OmniHuman (ByteDance), VEED Lip Sync,           │
│  Kling AI Avatar, Hedra                                  │
│                                                          │
│  Vorteil: Mehr Kontrolle über Stimme und Timing          │
│  Nachteil: Zusätzlicher Arbeitsschritt, manchmal         │
│  unnatürliche Mundbewegungen                             │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Lip-Sync-Qualität nach Modell (Stand: Februar 2026)

**Hinweis:** Stand Februar 2026 gibt es keine standardisierten Benchmarks für natives Video-Audio. Die folgenden Bewertungen basieren auf Community-Tests, Vergleichsartikeln und eigener Erprobung.

| Modell | Lip-Sync-Qualität | Sprachen | Typische Probleme |
|--------|------------------|----------|-------------------|
| **Seedance 2.0** | ✅ Sehr gut | EN, CN | Beste Synchronisation dank Dual-Branch. Selten Drift |
| **Veo 3.1** | ✅ Sehr gut | EN, multi | Gelegentlich Drift bei >8 Sek. Multi-Speaker möglich |
| **Sora 2** | ✅ Gut | EN, multi | Bei schnellem Dialog manchmal Asynchronität |
| **Kling 2.6** | ✅ Gut | 8 Sprachen | Gut bei einzelnem Sprecher. Multi-Speaker schwächer |
| **Kling 3.0** | ✅ Gut | 8 Sprachen | Verbessertes Lip-Sync, Multi-Shot-System |
| **LTX-2** | ⚠️ Basis | EN | Einfache Dialoge OK, komplexe Szenen unzuverlässig |
| **Runway Gen-4.5** | ❌ Kein natives | — | Audio extern hinzufügen + Lip-Sync-Tool |
| **Luma Ray3** | ❌ Kein natives | — | Kein Dialog, kein Lip-Sync |
| **Pika 2.5** | ❌ Kein natives | — | Kein Dialog, kein Lip-Sync |

### Tipps für besseres Lip-Sync

```
┌──────────────────────────────────────────────────────────┐
│         TIPPS FÜR BESSERES LIP-SYNC                       │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  1. EIN SPRECHER PRO CLIP                                │
│     Zuverlässigstes Lip-Sync bei einem Sprecher.         │
│     Zwei Sprecher: möglich, aber häufiger Fehler.        │
│     Drei+: nicht empfohlen.                              │
│                                                          │
│  2. GESICHT SICHTBAR UND GROSS GENUG                     │
│     Close-up oder Medium Close-up für bestes Lip-Sync.   │
│     Wide Shot: Mund zu klein für sichtbare Sync.         │
│                                                          │
│  3. DIALOG-LÄNGE = CLIP-LÄNGE                            │
│     Nicht zu viel Text in kurzen Clip packen.            │
│     ~15-20 Wörter für 8 Sekunden.                       │
│     Zu viel → hastiges Sprechen → schlechte Sync.        │
│                                                          │
│  4. PAUSEN EINBAUEN                                      │
│     "She pauses briefly, then says: ..."                 │
│     Pausen helfen dem Modell, Sync zu halten.            │
│                                                          │
│  5. EINFACHE PHONETIK BEVORZUGEN                         │
│     Kurze, klare Sätze. Keine Zungenbrecher.             │
│     Keine Fachtermini, die das Modell nicht kennt.       │
│                                                          │
│  6. MEHRFACH GENERIEREN                                  │
│     Lip-Sync variiert zwischen Generierungen.            │
│     3-5 Versuche, den besten wählen.                     │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** Lip-Sync ist wie die Übereinstimmung zwischen dem, was ein Berater sagt, und dem, was in der Präsentation auf dem Bildschirm steht. Wenn beides synchron ist, wirkt es professionell. Wenn der Berater über Baufinanzierung spricht, aber die Folie zeigt Wertpapiere — verliert das Publikum das Vertrauen. Genauso beim Lip-Sync: Wenn der Mund nicht zum Wort passt, fühlt sich das Video sofort „fake" an.

---

## Das Audio-Toolkit: Externe Tools für den professionellen Workflow

Wenn natives Audio nicht reicht — und das ist bei professionellen Produktionen oft der Fall — brauchen Sie externe Tools. Hier die wichtigsten:

### Übersicht: Audio-Tools für Video-Produktion

```
┌──────────────────────────────────────────────────────────┐
│              DAS AUDIO-TOOLKIT FÜR KI-VIDEO               │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  SPRACHE / VOICE-OVER                                    │
│  ┌─────────────────────────────────────────────┐         │
│  │ ElevenLabs         — TTS, Voice Cloning,    │         │
│  │                      Dubbing, 70+ Sprachen  │         │
│  │ Google Cloud TTS    — Solide, günstig       │         │
│  │ Amazon Polly        — AWS-integriert        │         │
│  │ OpenAI TTS          — In ChatGPT integriert │         │
│  └─────────────────────────────────────────────┘         │
│                                                          │
│  SOUNDEFFEKTE / FOLEY                                    │
│  ┌─────────────────────────────────────────────┐         │
│  │ ElevenLabs SFX v2   — Text-to-Sound, Foley  │         │
│  │ Adobe Firefly Audio — SFX + Ambient          │         │
│  │ Freesound.org       — Kostenlose SFX-Lib     │         │
│  │ Epidemic Sound      — Kuratierte SFX-Lib     │         │
│  └─────────────────────────────────────────────┘         │
│                                                          │
│  MUSIK                                                   │
│  ┌─────────────────────────────────────────────┐         │
│  │ Suno (v5)           — Komplette Songs, 30s   │         │
│  │ Udio                — Hochwertige Clips      │         │
│  │ Google Lyria 3      — Kostenlos in Gemini    │         │
│  │ AIVA                — Orchestral, lizenzfrei │         │
│  │ Soundraw            — Anpassbare Loops       │         │
│  │ Beatoven.ai         — Stimmungsbasiert       │         │
│  └─────────────────────────────────────────────┘         │
│                                                          │
│  LIP-SYNC (nachträglich)                                 │
│  ┌─────────────────────────────────────────────┐         │
│  │ OmniHuman (ByteDance) — Beste Qualität      │         │
│  │ VEED Lip Sync        — Browser-basiert      │         │
│  │ Kling AI Avatar      — Bild + Audio → Video │         │
│  │ Hedra                — Foto → sprechendes   │         │
│  │                        Video                │         │
│  └─────────────────────────────────────────────┘         │
│                                                          │
│  VIDEOEDITOR (zum Zusammenführen)                        │
│  ┌─────────────────────────────────────────────┐         │
│  │ CapCut              — Kostenlos, einfach     │         │
│  │ Canva Video         — Browser, intuitiv      │         │
│  │ DaVinci Resolve     — Kostenlos, Profi       │         │
│  │ Adobe Premiere Pro  — Industrie-Standard     │         │
│  └─────────────────────────────────────────────┘         │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Entscheidungsbaum: Nativer oder externer Audio-Workflow?

```
            Brauchen Sie Audio im Video?
                       │
              ┌────────┴────────┐
              ▼                 ▼
           JA                  NEIN
              │                 │
    ┌─────────┴─────────┐      ▼
    ▼                   ▼    Stummes Video
  Dialog               Nur Musik/           reicht
  nötig?               Ambient?
    │                   │
 ┌──┴──┐            ┌──┴──┐
 ▼     ▼            ▼     ▼
Kurz   Lang/      Einfach  Professionell
(1-2   Profi        │        │
Sätze)   │          ▼        ▼
 │       │      Natives    Suno/Udio/
 ▼       ▼      Audio      Lyria +
Natives  Externes reicht    Videoeditor
Audio    TTS
(Veo/   (ElevenLabs
Sora/    + Video-
Kling)   editor)
```

---

## Was KI-Audio (noch) nicht kann

### Die ehrlichen Grenzen

| Limitation | Auswirkung im Bankalltag | Workaround |
|-----------|------------------------|------------|
| **Stimmkonsistenz über Clips** | Dieselbe Person klingt in Clip 2 anders als in Clip 1. Stimme, Tonhöhe, Akzent variieren | ElevenLabs Voice Cloning: Eine geklonte Stimme klingt immer gleich. Natives Audio → gleichen Prompt wiederverwenden, besten Clip wählen |
| **Deutsches Lip-Sync** | Mundbewegungen passen besser zu englischer Phonetik als zu deutscher | Für perfektes deutsches Lip-Sync: ElevenLabs TTS + nachträgliches Lip-Sync-Tool (VEED, OmniHuman) |
| **Multi-Speaker-Dialoge** | Ab 3+ Sprechern verwechseln Modelle Stimmen oder Timing wird falsch | Max. 2 Sprecher pro Clip. Längere Dialoge: Mehrere Clips, je ein Sprecher, im Editor zusammenschneiden |
| **Emotion in der Stimme** | Native Stimmen klingen oft neutral. Freude, Trauer, Aufregung schwer steuerbar | Adjektive im Prompt helfen: „excitedly", „with a warm smile in her voice". Oder: ElevenLabs mit emotionaler Steuerung |
| **Präzises Timing** | Musik setzt nicht auf die Sekunde genau ein. Sound startet manchmal zu früh/spät | Für präzises Timing: Audio extern erstellen und im Videoeditor platzieren |
| **Stille/Pause** | KI füllt Stille oft mit Ambient oder generiert ungewollte Sounds | „Moment of silence" oder „quiet pause" im Prompt. Oder: Audio in Post trimmen |
| **Gesang** | Native Videomodelle können keinen Gesang im Video generieren | Suno/Udio für Songs, dann als Audio-Layer in den Videoeditor |
| **Musikalische Präzision** | Keine Kontrolle über Tonart, BPM, Harmonien bei nativem Audio | Suno/Udio/AIVA für präzise Musikgenerierung verwenden |
| **Urheberrecht Musik** | Rechtslage bei KI-generierter Musik unklar. Die drei großen Labels (UMG, Sony Music, Warner) haben im Juni 2024 Klage gegen Suno und Udio eingereicht — die Verfahren laufen | Für kommerzielle Nutzung: AIVA (lizenzfrei ab 11 $/Mo), Epidemic Sound (lizenziert), oder Soundraw. Für interne/nicht-kommerzielle Nutzung: Suno/Udio Free Tier ausreichend |
| **Hintergrundgeräusche** | Natives Audio generiert manchmal unpassende Sounds (z.B. Hundegebell in einer Bank) | Audio-Prompt spezifisch formulieren. „No animals, no outdoor sounds" als Negative. Oder: Audio nachbearbeiten |

### Die Technologie isoliert vs. Gesamtsystem

Wichtig zu verstehen: Viele dieser Limitationen gelten für die **nativen Video-Audio-Modelle allein**. Im Gesamtsystem — also Videomodell + externes TTS + Musik-KI + Videoeditor — gibt es für fast jede Limitation einen Workaround. Die Frage ist: Wie viel Aufwand wollen Sie investieren?

| Qualitätsanspruch | Empfohlener Workflow | Zeitaufwand |
|-------------------|---------------------|-------------|
| **Schnell & gut genug** (Social Media, intern) | Natives Audio in Veo 3.1 oder Sora 2 | 2–5 Minuten |
| **Professionell** (Kampagne, Webseite) | Video nativ + Musik extern (Suno) + VO extern (ElevenLabs) | 15–30 Minuten |
| **Premium** (Imagefilm, Hauptversammlung) | Video nativ (stumm) + kompletter Audio-Mix extern + professioneller Editor | 1–3 Stunden |

---

## Kosten: KI-Audio vs. professionelle Audioproduktion

| Szenario | Klassisch (Studio/Agentur) | KI-generiert | Ersparnis |
|----------|--------------------------|-------------|-----------|
| **Voice-Over (30 Sek., DE)** | 150–500 € (Sprecher + Studio) | 0–5 € (ElevenLabs) | 95–100% |
| **Hintergrundmusik (15 Sek.)** | 200–1.000 € (Komposition) oder 30–100 € (Stock) | 0–10 € (Suno/Lyria) | 90–100% |
| **Soundeffekte (Foley-Set)** | 100–500 € (Foley Artist) oder 20–50 € (SFX-Bibliothek) | 0–5 € (ElevenLabs SFX) | 90–100% |
| **Kompletter Audio-Mix (1 Min.)** | 500–2.000 € (Tonstudio) | 20–50 € (Tools-Abos) | 95–97% |
| **Voice Cloning (eigene Stimme)** | 2.000–5.000 € (professionell) | 22–99 € (ElevenLabs/Monat) | 98% |
| **Nativer Audio im Video** | N/A (gab es nicht) | 0 € (im Video-Abo enthalten) | 100% |

**Die wahre Ersparnis:** Noch wichtiger als die Kosten ist die **Zeit**. Ein professioneller Voice-Over braucht: Sprecher buchen → Skript finalisieren → Studio buchen → Aufnahme → Schnitt → Freigabe. Das sind 3–7 Tage. Mit ElevenLabs: 5 Minuten. Mit nativem Audio: 0 extra Minuten.

> **Volksbank-Analogie:** Der Kostenvergleich ist wie beim Kontoeröffnungsprozess: Früher kamen Kunden in die Filiale, füllten Formulare aus, warteten auf Bestätigung — 3 Tage. Heute: Online, Video-Ident, fertig in 15 Minuten. Technisch nicht 100% identisch, aber für 95% der Fälle gut genug — und 99% schneller.

---

## Der Audio-Prompt als Ganzes: Pipeline-Zusammenfassung

Hier die komplette Pipeline, wie Audio in einem KI-Video entsteht — von der Idee bis zum fertigen Clip:

```
┌──────────────────────────────────────────────────────────────────┐
│              AUDIO-PIPELINE: VON DER IDEE ZUM FERTIGEN CLIP      │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  PLANUNG                                                         │
│  ┌────────────────────────────────────────────────────────┐      │
│  │ 1. Welche Audio-Ebenen brauche ich?                    │      │
│  │    □ Dialog  □ SFX  □ Ambient  □ Musik                │      │
│  │                                                        │      │
│  │ 2. Reicht natives Audio oder brauche ich externe Tools?│      │
│  │    → Schnell & intern = nativ                          │      │
│  │    → Professionell & extern = externe Tools            │      │
│  │                                                        │      │
│  │ 3. Sprache? Deutsch oder Englisch?                     │      │
│  │    → DE-Publikum + schnell = nativ DE (Veo/Sora)       │      │
│  │    → DE-Publikum + perfekt = EN-Video + DE-VO extern   │      │
│  └────────────────────────────────────────────────────────┘      │
│       ↓                                                          │
│  PROMPT SCHREIBEN                                                │
│  ┌────────────────────────────────────────────────────────┐      │
│  │ Szene + Kamera + Aktion (aus Tutorial 04-01 & 04-02)  │      │
│  │       ↓                                                │      │
│  │ Dialog: Wer sagt was? (Doppelpunkt-Format)             │      │
│  │       ↓                                                │      │
│  │ SFX: Welche Aktions-Geräusche? (spezifisch!)          │      │
│  │       ↓                                                │      │
│  │ Ambient: Welcher Ort = welche Atmosphäre?              │      │
│  │       ↓                                                │      │
│  │ Musik: Welche Stimmung? (oder "No music")             │      │
│  │       ↓                                                │      │
│  │ "(no subtitles)" anhängen                              │      │
│  └────────────────────────────────────────────────────────┘      │
│       ↓                                                          │
│  GENERIEREN                                                      │
│  ┌────────────────────────────────────────────────────────┐      │
│  │ Video + Audio in einem Schritt (Veo/Sora/Kling)        │      │
│  │ ODER: Video stumm + Audio extern                       │      │
│  └────────────────────────────────────────────────────────┘      │
│       ↓                                                          │
│  QUALITÄTSKONTROLLE                                              │
│  ┌────────────────────────────────────────────────────────┐      │
│  │ □ Dialog verständlich?                                 │      │
│  │ □ Lip-Sync stimmt?                                     │      │
│  │ □ Keine unpassenden Geräusche?                         │      │
│  │ □ Musik-Lautstärke angemessen?                         │      │
│  │ □ Keine ungewollten Untertitel?                         │      │
│  │ → Nicht zufrieden? 3–5 Regenerierungen versuchen       │      │
│  └────────────────────────────────────────────────────────┘      │
│       ↓                                                          │
│  NACHBEARBEITUNG (optional)                                      │
│  ┌────────────────────────────────────────────────────────┐      │
│  │ □ Musik-Layer hinzufügen (Suno/Udio/Lyria)            │      │
│  │ □ Voice-Over hinzufügen (ElevenLabs)                   │      │
│  │ □ Unpassende Sounds entfernen (Videoeditor)            │      │
│  │ □ Lautstärke-Mix anpassen                              │      │
│  └────────────────────────────────────────────────────────┘      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## Das Wichtigste auf einen Blick

| Was Sie gelernt haben | Kernaussage |
|-----------------------|-------------|
| **Vier Audio-Ebenen** | Dialog > SFX > Ambient > Musik — in dieser Hierarchie |
| **Natives Audio** | Veo 3.1, Sora 2, Kling 2.6, Seedance 2.0 generieren Audio im Video-Prompt |
| **Dialog-Prompting** | Doppelpunkt-Format, 15–20 Wörter pro 8 Sek., max. 2 Sprecher, „(no subtitles)" |
| **SFX/Foley** | Als Teil der Aktion beschreiben, nicht als isolierte Sounds |
| **Ambient** | Ort = Atmosphäre. Spezifische Geräusche benennen, nicht „office sounds" |
| **Musik** | Stimmung + Instrument + Tempo + Stil. Oder: „No music" für reine Dialog-Szenen |
| **Voice-Over** | Nativ: schnell, nicht wählbar. ElevenLabs: professionell, konsistent, kontrollierbar |
| **Lip-Sync** | Ein Sprecher, Close-up, kurze Sätze, Pausen — dann funktioniert es gut |
| **Externe Tools** | ElevenLabs (Stimme), Suno/Udio (Musik), ElevenLabs SFX (Sounds), CapCut (Editor) |
| **Kosten** | Natives Audio: 0 € extra. Professioneller Mix: 20–50 €/Video statt 500–2.000 € |

---

## Parallelen zu vorherigen Tutorials

| Konzept | Wo eingeführt | Wie es hier weitergeht |
|---------|-------------|----------------------|
| **8-Bausteine-Framework** | Tutorial 04-01 | Bausteine 6 (Dialog) und 7 (Audio) werden hier vollständig erschlossen |
| **Beats und Timing** | Tutorial 04-02 | Beats steuern auch den Rhythmus des Dialogs — ein Beat = ein Satz |
| **Modellspezifische Stärken** | Tutorial 04-01 + 04-02 | Audio-Fähigkeiten ergänzen die Kamera- und Bewegungs-Stärken |
| **Prompt auf Englisch** | Tutorial 03-01 (Bilder), 04-01 | Dialog kann auf Deutsch sein, Prompt-Beschreibung auf Englisch |
| **Kosten-Vergleich** | Tutorial 04-01 | Audio-Kosten ergänzen die Video-Kosten → Gesamtbild |
| **Limitationen ehrlich benennen** | Alle Tutorials | Audio-Limitationen sind spezifisch: Stimmkonsistenz, Multi-Speaker, Lip-Sync DE |

---

## Hands-on Übung 1: Dialog-Vergleich — nativ vs. extern

**Aufgabe:** Erstellen Sie denselben Dialog auf zwei Wegen und vergleichen Sie.

**Szenario:** Eine Bankberaterin begrüßt einen Kunden.

**Weg 1 — Nativer Dialog (Veo 3.1 oder Sora 2):**
```
Medium close-up, eye level. A friendly bank consultant in her
mid-30s, wearing a navy blazer, sits at a modern desk. She looks
at the camera and says: Good morning! Thank you for coming in
today. I've prepared everything for our meeting. (no subtitles)

Soft office ambient: distant keyboard, air conditioning hum.
Warm side lighting from window. 8 seconds.
```

**Weg 2 — Externes Audio (Video + ElevenLabs):**
```
Schritt 1: Generieren Sie das Video mit demselben Prompt,
ABER: "No dialogue, no narrator. Only ambient sounds."

Schritt 2: Gehen Sie zu elevenlabs.io → wählen Sie eine
weibliche Stimme (z.B. "Rachel" oder "Bella") → geben Sie ein:
"Good morning! Thank you for coming in today. I've prepared
everything for our meeting."

Schritt 3: Laden Sie das Audio herunter und fügen Sie es
im Videoeditor (CapCut) zum Video hinzu.
```

**Vergleichen Sie:**
1. Welche Version klingt natürlicher?
2. Stimmt das Lip-Sync bei der nativen Version?
3. Welche Stimme gefällt Ihnen besser?
4. Welcher Workflow war schneller?
5. Für welchen Einsatz (intern/extern) reicht welche Version?

---

## Hands-on Übung 2: Foley und Ambient — das stille Video zum Leben erwecken

**Aufgabe:** Generieren Sie ein Video **ohne Dialog** und steuern Sie nur über Soundeffekte und Ambient die Atmosphäre.

**Szenario A — Ruhige Morgenszene:**
```
Static wide shot. An empty bank consultation room, early morning.
Sunlight slowly fills the space through floor-to-ceiling windows.

Audio: Complete silence at first, then slowly building —
a wall clock ticking softly, the distant hum of the building
waking up, a coffee machine gurgling in another room, then
footsteps approaching in the corridor.

No dialogue. No music. Let the sounds tell the story. 12 seconds.
```

**Szenario B — Geschäftiger Mittag:**
```
Static wide shot. A busy bank lobby at noon. People crossing,
a consultant guiding a customer, someone using the ATM.

Audio: Rich soundscape — multiple footsteps on marble, the
beep of the number ticket machine, muffled conversations
blending together, a phone ringing at the reception desk,
the pneumatic hiss of the entrance door opening and closing.

No dialogue. No music. Pure atmosphere. 12 seconds.
```

**Beobachten Sie:** Wie stark verändert sich die Stimmung des Videos allein durch den Sound — ohne ein einziges Wort?

---

## Hands-on Übung 3: Modellvergleich — Audio-Qualität

**Aufgabe:** Verwenden Sie den folgenden Prompt in mindestens zwei Modellen und vergleichen Sie die Audio-Qualität.

**Prompt:**
```
Medium shot, eye level. A young bank consultant in a modern
office picks up his desk phone. He says: Hi, this is Max from
the investment team. How can I help you today? (no subtitles)

He pauses, listens, then nods and begins typing on his laptop.

Audio: Phone ring at the start (2 rings), his voice clear and
professional, soft keyboard clicking as he types. Distant
office ambient. No music. 8 seconds.
```

**Vergleichen Sie (z.B. Kling 2.6 kostenlos auf [klingai.com](https://klingai.com) + Veo 3.1 in Gemini oder Sora 2 in ChatGPT Plus):**
1. Wie natürlich klingt die Stimme?
2. Hören Sie den Telefonklingelton? Passt er?
3. Stimmt das Lip-Sync?
4. Sind die Tastaturgeräusche synchron zum Tippen?
5. Gibt es unpassende Hintergrundgeräusche?

---

## Ausblick

Im nächsten Tutorial geht es um den **Schneidetisch**: Tutorial 04-04 „Video-Editing und iteratives Verfeinern" zeigt Ihnen, wie Sie mehrere Clips zu einem kohärenten Video zusammenbauen — Multi-Shot-Workflows, Storyboard-Strategien, Scene Extension und wie Sie Konsistenz über Szenen hinweg sicherstellen.

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Natives Audio** | Audio (Sprache, Soundeffekte, Musik), das direkt vom Videomodell während der Videogenerierung erzeugt wird — im Gegensatz zu nachträglich hinzugefügtem Sound |
| **Dialog (im Video-Kontext)** | Gesprochene Worte von Personen im Video. Kann explizit (exakte Worte vorgeben) oder implizit (Thema beschreiben) im Prompt formuliert werden |
| **Voice-Over (VO)** | Eine Erzählstimme, die über den Bildern liegt, ohne dass der Sprecher im Video sichtbar ist. Klassisch für Dokumentationen und Erklärvideos |
| **Foley** | Filmtechnischer Begriff für nachträglich erzeugte oder synchron generierte Alltagsgeräusche — Schritte, Türen, Papier, Gläser. Benannt nach Jack Foley, dem Pionier dieser Technik |
| **SFX (Sound Effects)** | Oberbegriff für alle Soundeffekte in einem Video — umfasst Foley, aber auch nicht-diegetische Sounds wie Whooshes oder UI-Klänge |
| **Ambient / Atmosphäre** | Hintergrundgeräusche, die einen Ort definieren: Büro-Gemurmel, Straßenverkehr, Vogelgezwitscher. Meist nicht bewusst wahrgenommen, aber bei Fehlen sofort bemerkt |
| **Diegetisch** | Sounds, die innerhalb der Filmwelt existieren — die Figuren könnten sie hören. Beispiel: das Klingeln eines Telefons im Bild |
| **Nicht-diegetisch** | Sounds von außerhalb der Filmwelt — die Figuren hören sie nicht. Beispiel: Hintergrundmusik (Score), Erzähler-Stimme |
| **Lip-Sync (Lippensynchronisation)** | Die Übereinstimmung zwischen Mundbewegungen einer Person im Video und den gesprochenen Worten. Bei nativem Audio automatisch; bei externem Audio nachträglich synchronisiert |
| **Dual-Branch-Transformer** | Architektur von Seedance 2.0: Zwei parallele Netzwerkzweige — einer für Video, einer für Audio — die sich gegenseitig informieren und so die beste Synchronisation erzeugen |
| **TTS (Text-to-Speech)** | Technologie, die geschriebenen Text in gesprochene Sprache umwandelt. Moderne TTS-Systeme (ElevenLabs) klingen nahezu menschlich |
| **Voice Cloning** | Technologie, die eine menschliche Stimme aus wenigen Minuten Audio klont. Ermöglicht konsistente „Hausstimmen" für Unternehmen |
| **Dubbing** | Nachvertonung: Audio eines Videos wird durch eine andere Sprachversion ersetzt. KI-Dubbing passt auch die Mundbewegungen an |
| **Suno** | KI-Musik-Generator, der komplette Songs (mit Gesang) aus Textbeschreibungen erzeugt. Marktführer 2025/26 |
| **Udio** | KI-Musik-Generator mit Fokus auf Audioqualität und Kontrolle. Kürzere Clips als Suno, aber oft präzisere Ergebnisse |
| **ElevenLabs** | Marktführer für KI-Stimmen: Text-to-Speech, Voice Cloning, Sound Effects, Dubbing. 5.000+ Stimmen in 70+ Sprachen |
| **Lyria 3** | Googles KI-Musik-Modell, integriert in Gemini. Generiert lizenzfreie Hintergrundmusik kostenlos |
| **Score (Filmmusik)** | Die nicht-diegetische Hintergrundmusik eines Films. Setzt Stimmung und Emotion, ohne dass die Figuren sie hören |
| **Jingle** | Kurze, einprägsame Melodie für Werbezwecke. Typisch 3–10 Sekunden. Perfekter Anwendungsfall für Suno/Udio |
| **DAW (Digital Audio Workstation)** | Professionelle Audio-Software zum Aufnehmen, Bearbeiten und Mischen von Ton. Beispiele: Logic Pro, Ableton, Audacity (kostenlos) |
| **Stems** | Einzelne Audiospuren eines Musikstücks (z.B. nur Schlagzeug, nur Gesang, nur Bass). Ermöglicht separates Bearbeiten einzelner Instrumente |
| **Phonem** | Kleinste Lauteinheit einer Sprache. Relevant für Lip-Sync: Das Modell ordnet Phoneme den entsprechenden Visemen (Mundbild-Formen) zu — ein Prozess, der im Training aus Millionen von Sprechvideos gelernt wird |
| **Latent Diffusion (Audio)** | Dieselbe Technologie wie bei Bildgenerierung (Kapitel 00-02), angewandt auf Audio: Rauschen wird schrittweise in Klang umgewandelt |

---

