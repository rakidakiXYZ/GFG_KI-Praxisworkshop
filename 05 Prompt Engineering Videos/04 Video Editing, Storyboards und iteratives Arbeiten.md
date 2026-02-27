# Video-Editing und iteratives Verfeinern

**Der Schneidetisch — Szenen zusammenbauen: Image-to-Video, Video-to-Video, Scene Extension, Storyboard-Workflows, Multi-Shot-Konsistenz und Nachbearbeitung**

---

## Warum dieses Tutorial?

In den letzten drei Tutorials haben Sie das Terrain der KI-Videogenerierung kartiert (04-01), gelernt wie ein Regisseur zu denken (04-02) und Ihr Video zum Klingen gebracht (04-03). Jedes Mal ging es um **einen einzelnen Clip** — ein paar Sekunden Video aus einem einzigen Prompt.

Aber ein Video ist kein Einzelclip. Ein Erklärvideo für Ihre Filiale besteht aus 8–15 Szenen. Ein Social-Media-Reel braucht einen Opener, einen Hauptteil und einen Call-to-Action. Ein Recruiting-Clip zeigt drei verschiedene Mitarbeiter an drei verschiedenen Orten.

Und genau hier wird es schwierig: **Wie bauen Sie aus Einzelclips ein zusammenhängendes Video?**

Das ist die Frage, die professionelle Cutter seit hundert Jahren beantworten — am Schneidetisch. Und genau das lernen Sie jetzt mit KI-Werkzeugen.

> **Volksbank-Analogie:** Stellen Sie sich vor, Sie haben 15 einzelne Fotos von einer Filial-Eröffnung. Jedes Foto ist gut. Aber wenn Sie die einfach hintereinander kleben, ergibt das keine Geschichte. Ein guter Schnitt macht aus losen Einzelteilen einen Film — genauso wie ein guter Kreditantrag aus losen Unterlagen ein überzeugendes Dossier macht.

**Was Sie nach diesem Tutorial wissen werden:**

- Wie Sie aus einem Standbild ein Video machen (Image-to-Video) — und warum das die wichtigste Technik für Konsistenz ist
- Wie Sie ein bestehendes Video mit KI verändern (Video-to-Video) — Stil ändern, Objekte entfernen, Szenen umgestalten
- Wie Sie Clips verlängern und Szenen erweitern (Scene Extension)
- Wie Sie einen Storyboard-Workflow aufsetzen, der von der Idee zum fertigen Video führt
- Wie Sie Charaktere über mehrere Shots hinweg konsistent halten — das härteste Problem in der KI-Videoproduktion
- Wie Sie KI-Clips in einem klassischen Schnittprogramm zum fertigen Video zusammenbauen
- Was das alles kostet — und wie der Workflow im Vergleich zu klassischer Videoproduktion abschneidet

---

## Ein kurzer Blick zurück: Die Geschichte des Videoschnitts

Der Schneidetisch ist älter als der Tonfilm. Und die Art, wie wir Szenen zusammenbauen, hat sich in hundert Jahren dramatischer verändert als jede andere Disziplin im Filmemachen.

| Jahr | Meilenstein | Was sich änderte |
|------|-----------|-----------------|
| **1903** | **„The Great Train Robbery"** (Edwin S. Porter) | Erster Film mit echtem Schnitt — mehrere Szenen, verschiedene Orte, eine Geschichte |
| **1920er** | **Montage-Theorie** (Eisenstein, Kuleschow) | Erkenntnis: Die Reihenfolge der Schnitte erzeugt Bedeutung — nicht nur die Einzelbilder |
| **1990er** | **Avid, Final Cut Pro** | Digitaler Schnitt ersetzt physisches Filmschneiden — nichtlinearer Schnitt (NLE) wird Standard |
| **2015** | **Adobe Premiere + After Effects** | VFX und Schnitt verschmelzen — jeder Laptop wird zum Schnittraum |
| **2022** | **Runway Gen-1** | Erstes Video-to-Video-Modell: bestehendes Video wird per Prompt in neuen Stil transformiert |
| **2023** | **Pika 1.0, Runway Gen-2** | Image-to-Video wird alltagstauglich — ein Standbild wird zum Videoclip |
| **2024 Jun** | **Runway Gen-3 Alpha** | Deutlich bessere Bewegungsphysik, bis 10 Sekunden, Inpainting & Outpainting |
| **2025 Mär** | **Runway Gen-4** | Referenzbild-System für Charakter-Konsistenz über mehrere Shots |
| **2025 Mai** | **Veo 3** (Google) | Image-to-Video mit nativem Audio + bis zu 3 Referenzbilder für Konsistenz |
| **2025 Okt** | **Sora 2** (OpenAI) | Storyboard-Feature: Frame-by-Frame-Planung direkt im Interface |
| **2025 Dez** | **Runway Gen-4.5 + Aleph** | Video-to-Video der nächsten Generation: Stil-Transfer, Relighting, Reanimation |
| **2026 Feb** | **Kling 3.0** (Kuaishou) | Face-Lock + Multi-Shot-Modus: Charakter-Konsistenz über Szenen hinweg gelöst |

**Die Erkenntnis:** Hundert Jahre Filmgeschichte führen zu einem Punkt: Das Zusammenbauen von Szenen ist eine Kunst, die Technik und Erzählung verbindet. KI automatisiert jetzt die technische Seite — aber die erzählerischen Prinzipien bleiben dieselben.

> **Volksbank-Analogie:** Der Wandel vom physischen Filmschnitt zum digitalen NLE hat den Beruf des Cutters nicht eliminiert — er hat ihn demokratisiert. Genauso wie Online-Banking den Bankberater nicht überflüssig macht, sondern seine Arbeit verändert. KI-Video ist die nächste Stufe dieser Demokratisierung.

---

## Die fünf Wege zum Video — und wann Sie welchen nutzen

In Tutorial 04-01 haben Sie drei Wege kennengelernt: Text-to-Video, Image-to-Video und Video-to-Video. Für den Schneidetisch brauchen wir eine feinere Unterscheidung, denn jeder Weg hat eine andere Rolle im Produktions-Workflow:

```
┌─────────────────────────────────────────────────────────────────┐
│            DIE FÜNF WEGE ZUM FERTIGEN VIDEO                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. TEXT-TO-VIDEO (T2V)                                         │
│  ═════════════════════                                          │
│  Prompt → Video. Maximale kreative Freiheit,                    │
│  minimale Kontrolle über Details.                               │
│  → Für: Ideenfindung, Mood-Boards, erste Entwürfe              │
│                                                                 │
│  2. IMAGE-TO-VIDEO (I2V)                                        │
│  ══════════════════════                                          │
│  Standbild → animiertes Video. Das Bild bestimmt               │
│  Aussehen, der Prompt bestimmt Bewegung.                        │
│  → Für: Konsistente Charaktere, kontrollierte Ästhetik          │
│                                                                 │
│  3. VIDEO-TO-VIDEO (V2V)                                        │
│  ══════════════════════                                          │
│  Bestehendes Video → transformiertes Video.                     │
│  Struktur bleibt, Stil/Inhalt ändert sich.                      │
│  → Für: Stil-Transfer, Objekt-Ersetzung, Re-Rendering           │
│                                                                 │
│  4. SCENE EXTENSION                                              │
│  ══════════════════                                              │
│  Bestehender Clip → verlängerter Clip.                          │
│  Letztes Frame wird zum Startpunkt der Fortsetzung.             │
│  → Für: Szenen verlängern, Übergänge schaffen                   │
│                                                                 │
│  5. INPAINTING / OUTPAINTING                                     │
│  ════════════════════════════                                     │
│  Teile eines Videos ändern (Inpainting) oder den                │
│  Bildausschnitt erweitern (Outpainting).                        │
│  → Für: Objekte entfernen, Seitenverhältnis ändern              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Welches Modell kann was? (Stand: Februar 2026)

| Fähigkeit | Sora 2 | Veo 3.1 | Runway Gen-4.5 / Aleph | Kling 3.0 | Pika 2.5 | Seedance 2.0 |
|-----------|--------|---------|------------------------|-----------|----------|--------------|
| **Text-to-Video** | ✅ bis 25s | ✅ bis 12s | ✅ bis 10s | ✅ bis 2min | ✅ bis 8s | ✅ bis 8s |
| **Image-to-Video** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Video-to-Video** | ⚠️ begrenzt | ⚠️ begrenzt | ✅ (Aleph) | ✅ | ✅ | ⚠️ |
| **Scene Extension** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Inpainting** | ❌ | ✅ | ✅ (Aleph) | ⚠️ | ✅ | ❌ |
| **Outpainting** | ❌ | ✅ | ✅ (Aleph) | ⚠️ | ⚠️ | ❌ |
| **Referenzbilder** | ❌ | ✅ (bis 3) | ✅ | ✅ (Multi-Ref) | ❌ | ✅ (Face-Lock) |
| **Storyboard-Modus** | ✅ | ❌ | ❌ | ✅ (Multi-Shot) | ❌ | ❌ |
| **Charakter-Lock** | ❌ | ⚠️ (via Ref) | ✅ (via Ref) | ✅ (Face-Lock) | ❌ | ✅ (Face-Lock) |

> **Lesehinweis:** ✅ = gut nutzbar | ⚠️ = vorhanden, aber mit Einschränkungen | ❌ = nicht verfügbar

---

## Schritt 1: Image-to-Video — Die Basis für alles

Wenn Sie nur eine Technik aus diesem Tutorial mitnehmen, dann diese: **Image-to-Video (I2V) ist der Schlüssel zu konsistenter KI-Videoproduktion.**

### Warum I2V so wichtig ist

Bei Text-to-Video beschreibt Ihr Prompt *alles* — und die KI interpretiert bei jeder Generation neu. Die Person in Shot 1 sieht anders aus als in Shot 2, selbst bei identischem Prompt. Das liegt daran, dass der Diffusionsprozess **stochastisch** ist (= zufallsbasiert): Kleine Unterschiede im Zufallsstartwert führen zu sichtbar unterschiedlichen Ergebnissen.

Bei Image-to-Video dagegen **starten Sie mit echten Pixeln**. Das Modell sieht das Aussehen Ihres Charakters, den Hintergrund, die Beleuchtung — und animiert genau das. Sie schreiben im Prompt nur noch die *Bewegung*, nicht das *Aussehen*.

```
VERGLEICH: TEXT-TO-VIDEO vs. IMAGE-TO-VIDEO

Text-to-Video:
┌────────────┐     ┌──────────────┐     ┌─────────────┐
│  Prompt:   │ ──→ │  KI generiert│ ──→ │  Video mit  │
│  "Frau im  │     │  Aussehen +  │     │  zufälligem  │
│  Blazer..."│     │  Bewegung    │     │  Gesicht     │
└────────────┘     └──────────────┘     └─────────────┘

Image-to-Video:
┌────────────┐     ┌──────────────┐     ┌─────────────┐
│  Referenz- │     │              │     │  Video mit   │
│  bild der  │ ──→ │  KI animiert │ ──→ │  GENAU dieser│
│  Frau im   │     │  nur Bewegung│     │  Person      │
│  Blazer    │     │              │     │              │
└────────────┘     └──────────────┘     └─────────────┘
```

> **Volksbank-Analogie:** Stellen Sie sich vor, Sie wollen drei Beratungsgespräche filmen — immer mit derselben Beraterin. Bei T2V wäre es so, als würden Sie jedes Mal eine andere Schauspielerin casten, die „wie eine Bankberaterin" aussehen soll. Bei I2V haben Sie ein Foto der echten Beraterin und sagen: „Animiere diese Person."

### Best Practices für Referenzbilder

Die Qualität Ihres Referenzbilds bestimmt die Qualität des Videos. Hier sind die wichtigsten Regeln:

| Regel | Warum | Beispiel |
|-------|-------|---------|
| **Hohe Auflösung** (min. 1024px) | Mehr Pixel = mehr Details für die KI | 1920×1080 statt 512×512 |
| **Klare Trennung zum Hintergrund** | KI muss erkennen, was Charakter und was Umgebung ist | Person vor neutralem Hintergrund |
| **Neutrale Pose** | Extreme Posen limitieren die mögliche Animation | Halbkörper, leicht seitlich |
| **Gleichmäßige Beleuchtung** | Harte Schatten verwirren das Modell | Weiches Licht, keine Gegenlichtaufnahme |
| **Konsistenter Stil** | Wenn Sie KI-Bilder als Referenz nutzen: gleicher Stil und Seed (= der Zufallsstartwert, der das Ergebnis reproduzierbar macht — in Midjourney z.B. mit `--seed 12345`) | Alle Referenzen aus demselben Bildgenerator |

### I2V-Prompt: Bewegung beschreiben, nicht Aussehen

Der häufigste Fehler bei I2V: Im Prompt das Aussehen des Charakters beschreiben. Das ist unnötig — die KI sieht ja schon das Bild. Schlimmer noch: Wenn Prompt und Bild sich widersprechen, entstehen Artefakte.

**❌ Schlecht (beschreibt Aussehen):**
> „A woman with brown hair and a blue blazer in an office, she turns to the camera and smiles"

**✅ Gut (beschreibt nur Bewegung):**
> „The person slowly turns toward the camera, smiles warmly, and gives a slight nod. Soft ambient office sounds."

**✅ Noch besser (mit Timing):**
> „[0-2s] The person looks down at documents on the desk. [2-4s] Slowly looks up toward the camera. [4-6s] Warm smile, slight nod. Soft office ambiance, paper rustling."

### Welches Modell für I2V?

| Modell | Stärke bei I2V | Schwäche | Wann nutzen? |
|--------|----------------|----------|--------------|
| **Kling 3.0** | Beste Gesichtserhaltung, bis 10s | Stil manchmal etwas „glatt" | Wenn Gesichtstreue kritisch ist |
| **Runway Gen-4** | Exzellente Detailtreue, 4K | Nur ~10s | Wenn maximale Qualität gefragt ist |
| **Seedance 2.0** | Starke Bewegungskohärenz | Nur 8s | Wenn natürliche Bewegung wichtig ist |
| **Veo 3.1** | Bis 3 Referenzbilder gleichzeitig | Manchmal übermäßig geglättet | Wenn mehrere Referenzen nötig sind |
| **Sora 2** | Gute Gesamtqualität, bis 25s | Keine Referenzbild-Steuerung | Wenn Länge wichtiger als Kontrolle ist |

---

## Schritt 2: Video-to-Video — Bestehendes transformieren

Video-to-Video (V2V) nimmt ein vorhandenes Video und transformiert es — Stil, Beleuchtung, Objekte, sogar die gesamte Ästhetik. Die Struktur (Bewegungen, Kamerawinkel, Timing) bleibt erhalten, aber das Aussehen ändert sich fundamental.

### Die drei V2V-Anwendungsfälle

```
┌──────────────────────────────────────────────────────────────┐
│               VIDEO-TO-VIDEO: DREI MODI                       │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  1. STIL-TRANSFER                                            │
│  ════════════════                                            │
│  Smartphone-Video → cineastische Ästhetik                    │
│  Echte Aufnahme → Cartoon/Anime/Illustration                 │
│  → Branding-konforme Optik aus jedem Rohmaterial             │
│                                                              │
│  2. OBJEKT-ERSETZUNG / INPAINTING                            │
│  ═══════════════════════════════                              │
│  Logo im Hintergrund → verschwunden                          │
│  Leerer Tisch → Laptop und Kaffee                            │
│  → Post-Production-Cleanup ohne Neudreh                      │
│                                                              │
│  3. RE-RENDERING                                             │
│  ════════════════                                            │
│  Niedrige Auflösung → höhere Qualität                        │
│  Alter Clip → moderner Look                                  │
│  → „Upscaling mit Verstand"                                  │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

> **Volksbank-Analogie:** Stellen Sie sich vor, Sie haben ein gutes Handy-Video von der letzten Filial-Eröffnung. Die Bewegungen, die Stimmung, die Momente — alles passt. Aber die Qualität ist mäßig und im Hintergrund steht ein Lieferwagen mit Werbung. V2V kann das Video in eine cineastische Optik transformieren und den Lieferwagen durch eine Hecke ersetzen — ohne dass Sie neu drehen müssen.

### Runway Aleph: Die V2V-Referenz

Runway hat mit **Aleph** (Dezember 2025) ein dediziertes Video-Transformations-Modell veröffentlicht, das den bisherigen Standard definiert. Aleph kann in einem Arbeitsschritt:

- **Stil-Transfer:** Realfilm → Animation, Skizze, Aquarell, jeder beliebige Stil
- **Viewpoint Change:** Perspektive ändern (z.B. von frontal zu leichter Seitenansicht)
- **Relighting:** Beleuchtung komplett ändern (Tageszeit, Stimmung, Lichtrichtung)
- **Reanimation:** Bewegungen ändern (Person hebt statt der linken die rechte Hand)
- **Inpainting:** Objekte entfernen oder ersetzen
- **Outpainting:** Bildausschnitt erweitern

**V2V-Prompt-Beispiel (Runway Aleph):**

Quellvideo: Handy-Aufnahme einer Person am Schreibtisch

> „Transform into a cinematic corporate video. Warm color grading, shallow depth of field, soft golden hour lighting from the left. Remove the water bottle on the desk. Professional corporate aesthetic."

### V2V bei anderen Modellen

| Modell | V2V-Fähigkeit | Besonderheit |
|--------|--------------|--------------|
| **Runway Aleph** | Umfassendste V2V-Suite | Stil, Licht, Perspektive, Inpainting in einem Modell |
| **Kling 3.0** | Motion Transfer + Stil | Kann Bewegungen von einem Video auf einen anderen Charakter übertragen |
| **Pika 2.5** | „Pikaffects" — kreative Effekte | Einfache Stil-Effekte (Aufschmelzen, Zerbröseln, etc.) |
| **Veo 3.1** | Inpainting + Outpainting | Über Google Flow Editor verfügbar |
| **Wan2.2 VACE** | Open Source V2V | Video-Outpainting und Inpainting, lokal ausführbar |

---

## Schritt 3: Scene Extension — Clips verlängern

Jedes KI-Videomodell hat ein Zeitlimit: 8 Sekunden, 10 Sekunden, maximal 25 Sekunden. Aber Ihre Szene braucht vielleicht 30 oder 45 Sekunden. Die Lösung: **Scene Extension** — der letzte Frame des Clips wird zum ersten Frame des nächsten Clips.

### Wie Scene Extension funktioniert

```
SCENE EXTENSION: CLIPS ANEINANDERHÄNGEN

Clip 1 (Original):                    Clip 2 (Extension):
┌─────────────────────┐               ┌─────────────────────┐
│ Frame 1 ... Frame N │──letztes──→  │ Frame N ... Frame M │
│    (8 Sekunden)     │   Frame      │    (8 Sekunden)     │
└─────────────────────┘               └─────────────────────┘
                                      ↑
                         Das letzte Frame von Clip 1
                         wird zum Startbild von Clip 2
                         (= Image-to-Video mit Kontext)
```

### Best Practices für nahtlose Extensions

1. **Prompts konsistent halten:** Wenn Clip 1 „warm office lighting" hatte, sollte Clip 2 das auch haben
2. **Neue Bewegung beschreiben, nicht wiederholen:** Clip 2 sollte die Handlung *fortsetzen*, nicht Clip 1 wiederholen
3. **Schnitt-Punkt strategisch wählen:** Verlängern Sie an ruhigen Momenten — nicht mitten in einer schnellen Bewegung
4. **Drei ist die Grenze:** Nach 2–3 Extensions wird die Qualität merklich schlechter (Artefakte akkumulieren)
5. **Audio mitdenken:** Wenn das Modell natives Audio generiert, wird der Ton an der Nahtstelle oft inkonsistent

**Extension-Prompt-Beispiel:**

Clip 1 endet: Person hat gerade ein Dokument auf den Tisch gelegt.

> „[Continuing seamlessly] The person picks up a pen, looks at the document thoughtfully, then looks up at the camera with a confident expression. Same warm office lighting, same soft ambient sounds."

### Modell-Vergleich für Extensions

| Modell | Max. Verlängerung | Nahtqualität | Tipp |
|--------|-------------------|--------------|------|
| **Kling 3.0** | Beliebig oft | ⭐⭐⭐⭐ | Beste Nahtlosigkeit durch starke temporale Konsistenz |
| **Runway Gen-4** | 3–4× empfohlen | ⭐⭐⭐⭐ | Nutzt letztes Frame als Referenz automatisch |
| **Veo 3.1** | 2–3× empfohlen | ⭐⭐⭐ | Frame Conditioning über API steuerbar |
| **Sora 2** | 3× empfohlen | ⭐⭐⭐ | Storyboard-Feature für geplante Extensions ideal |
| **Pika 2.5** | 2× empfohlen | ⭐⭐ | Deutlicher Qualitätsverlust nach 2. Extension |

---

## Schritt 4: Storyboard-Workflows — Von der Idee zum Video

Ein professionelles Video beginnt nicht mit einem Prompt. Es beginnt mit einem **Storyboard** — einer visuellen Szene-für-Szene-Planung. In der KI-Videoproduktion ist das Storyboard wichtiger als je zuvor, weil es die Grundlage für konsistente Multi-Shot-Produktion bildet.

### Der 6-Schritte-Workflow

```
┌────────────────────────────────────────────────────────────────────────┐
│                STORYBOARD-WORKFLOW FÜR KI-VIDEO                        │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│  SCHRITT 1: SKRIPT                                                     │
│  ─────────────────                                                     │
│  Was ist die Geschichte? Welche Botschaft?                             │
│  → Schreiben Sie 2-3 Sätze pro Szene                                  │
│                                                                        │
│  SCHRITT 2: SZENEN-KARTEN                                              │
│  ────────────────────────                                              │
│  Pro Szene: Beschreibung + Kamerawinkel + Dauer + Audio               │
│  → Format: „Shot-Card" (siehe unten)                                   │
│                                                                        │
│  SCHRITT 3: REFERENZBILDER                                             │
│  ─────────────────────────                                             │
│  Konsistente Charaktere per KI-Bildgenerator erstellen                 │
│  → Midjourney, DALL-E, Flux — gleicher Seed, gleicher Stil             │
│                                                                        │
│  SCHRITT 4: VIDEO-GENERIERUNG                                          │
│  ────────────────────────────                                          │
│  Image-to-Video für jeden Shot. Iterieren bis es passt.                │
│  → 2-4 Varianten pro Shot generieren, beste auswählen                  │
│                                                                        │
│  SCHRITT 5: REVIEW & ITERATION                                         │
│  ────────────────────────────                                          │
│  Clips im Kontext anschauen (nicht isoliert!).                         │
│  → Passt der Übergang? Stimmt die Farbgebung? Konsistenz?              │
│                                                                        │
│  SCHRITT 6: MONTAGE & NACHBEARBEITUNG                                  │
│  ─────────────────────────────────────                                  │
│  Clips in Schnittprogramm zusammenbauen.                               │
│  → Übergänge, Farbkorrektur, Audio-Mischung, Untertitel               │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

### Die Shot-Card: Ihr Planungswerkzeug

Für jeden Shot erstellen Sie eine Karte mit allen relevanten Informationen. Das ist Ihr „Drehbuch für die KI":

```
┌──────────────────────────────────────────────┐
│  SHOT-CARD #3                                │
├──────────────────────────────────────────────┤
│  Szene: Beratungsgespräch                    │
│  Dauer: 6 Sekunden                           │
│  Kamera: Medium Close-Up, leichte Bewegung   │
│          nach rechts                         │
│  Beschreibung: Beraterin erklärt etwas,      │
│    zeigt auf den Bildschirm, Kunde nickt     │
│  Audio: Leises Büro-Gemurmel, Tastatur       │
│  Referenzbild: beraterin_ref_01.png          │
│  Übergang von Shot #2: Schnitt               │
│  Modell: Kling 3.0 (Face-Lock)              │
│  Prompt: "The person gestures toward a       │
│    screen, explaining something with a warm  │
│    expression. Subtle camera dolly right.    │
│    Soft office ambiance."                    │
└──────────────────────────────────────────────┘
```

### Sora 2 Storyboard-Feature

Sora 2 bietet als einziges Modell ein **eingebautes Storyboard-Interface**: Sie planen Ihr Video Frame-by-Frame direkt in der Oberfläche, bevor Sie generieren. Jeder Frame bekommt einen eigenen Prompt, und Sora versucht, die Übergänge nahtlos zu gestalten.

**Vorteile:**
- Kein externes Tool nötig — alles in einem Interface
- Die KI kennt den Kontext aller Frames und optimiert Übergänge
- Ideal für Anfänger, die keinen komplexen Workflow aufsetzen wollen

**Nachteile:**
- Begrenzt auf Sora-Ökosystem (keine Modellwechsel zwischen Shots)
- Weniger Kontrolle über einzelne Shots als im I2V-Workflow
- Charakter-Konsistenz über viele Shots noch nicht zuverlässig

### Kling 3.0 Multi-Shot-Modus

Kling 3.0 hat einen **Multi-Shot-Modus**, der speziell für Storyboard-Workflows entwickelt wurde:

- **Start- und End-Frame festlegen:** Sie definieren, wie eine Szene beginnt und endet
- **Element-Lock:** Charaktere, Objekte und Hintergründe werden per Referenzbild „eingesperrt"
- **Szene-für-Szene-Generierung:** Jeder Shot wird einzeln generiert, aber mit geteiltem Charakter-Verständnis

> **Volksbank-Analogie:** Der Multi-Shot-Modus ist wie ein Drehbuch-Template für einen Filialfilm: Sie definieren vorher, wer in welcher Szene vorkommt und wie der Übergang sein soll — und die KI hält sich daran, statt jede Szene als eigenständiges Projekt zu behandeln.

---

## Schritt 5: Multi-Shot-Konsistenz — Das härteste Problem

Charakter-Konsistenz über mehrere Shots ist **das größte ungelöste Problem** in der KI-Videoproduktion. Wenn Sie Shot 1 und Shot 2 separat generieren, sieht die Person in beiden Shots unterschiedlich aus — auch bei identischem Prompt. Haarfarbe driftet, Gesichtszüge morphen, Kleidung ändert sich.

### Warum das Problem so schwer ist

KI-Videomodelle haben kein „Gedächtnis" zwischen Generierungen. Jeder Clip ist eine unabhängige Stichprobe aus einer gelernten Verteilung. Selbst bei identischem Prompt sorgt der stochastische Diffusionsprozess für Variation. Das ist kein Bug — es ist eine Eigenschaft des Systems.

In der traditionellen Filmproduktion löst ein Schauspieler dieses Problem automatisch: Die gleiche Person sieht in jeder Szene gleich aus. In der KI-Produktion müssen Sie diese Konsistenz aktiv herstellen.

### Die vier Methoden für Charakter-Konsistenz

```
┌─────────────────────────────────────────────────────────────────┐
│        VIER METHODEN FÜR CHARAKTER-KONSISTENZ                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  METHODE 1: IMAGE-TO-VIDEO MIT REFERENZBILD                     │
│  ═══════════════════════════════════════════                     │
│  Aufwand: ⭐ (gering)    Konsistenz: ⭐⭐⭐⭐                     │
│  Jeder Shot startet vom selben Referenzbild.                    │
│  Einfachste und zuverlässigste Methode.                         │
│  Limitierung: Charakter ist an Pose/Winkel des                  │
│  Referenzbilds gebunden.                                        │
│                                                                 │
│  METHODE 2: FACE-LOCK / CHARACTER REFERENCE                     │
│  ═══════════════════════════════════════════                     │
│  Aufwand: ⭐⭐ (mittel)   Konsistenz: ⭐⭐⭐⭐⭐                   │
│  Modell „sperrt" Gesicht/Körper des Charakters                  │
│  basierend auf Referenzmaterial.                                │
│  Verfügbar bei: Kling 3.0, Seedance 2.0, Runway Gen-4          │
│                                                                 │
│  METHODE 3: LORA-TRAINING (für Fortgeschrittene)                │
│  ═════════════════════════════════════════════════                │
│  Aufwand: ⭐⭐⭐⭐ (hoch)  Konsistenz: ⭐⭐⭐⭐⭐                   │
│  Trainieren Sie einen kleinen Modell-Adapter (50-200 MB)        │
│  auf 10-30 Bilder Ihres Charakters.                             │
│  Maximale Flexibilität: Jede Pose, jeder Winkel.               │
│  Plattformen: Replicate, ComfyUI + kohya, RunPod               │
│  ⚠️ Keine Sorge: Diese Methode ist optional! Methode 1+2       │
│  reichen für 90% aller Anwendungsfälle völlig aus.              │
│                                                                 │
│  METHODE 4: PROMPT-DISZIPLIN                                    │
│  ══════════════════════════                                      │
│  Aufwand: ⭐ (gering)    Konsistenz: ⭐⭐                        │
│  Identische Charakter-Beschreibung in jedem Prompt.             │
│  Funktioniert nur als Ergänzung zu Methode 1-3.                │
│  Allein nicht zuverlässig genug.                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Der Charakter-Konsistenz-Workflow (Empfohlen)

Für die beste Konsistenz kombinieren Sie mehrere Methoden:

**1. Charakter-Sheet erstellen:**
Generieren Sie mit einem Bildgenerator (Midjourney, DALL-E, Flux) ein Set von 5-8 Bildern Ihres Charakters aus verschiedenen Winkeln. Achten Sie auf:
- Gleicher Prompt-Kern (Name, Aussehen, Kleidung)
- Gleicher Seed (wenn möglich)
- Verschiedene Posen: frontal, 3/4, Profil, Ganzkörper, Halbkörper

**2. Face-Lock aktivieren (wenn verfügbar):**
- **Kling 3.0:** Laden Sie 1-3 Referenzbilder hoch → das Modell sperrt Gesicht, Körperhaltung und Kleidung
- **Seedance 2.0:** Face-Lock-Funktion für Gesichtstreue
- **Runway Gen-4:** Bis zu 5 Referenzbilder für Charakter + Umgebung

**3. Pro Shot: I2V mit dem passenden Winkel:**
Wählen Sie aus Ihrem Charakter-Sheet das Bild, das am besten zur geplanten Szene passt, und nutzen Sie es als I2V-Referenz.

**4. Prompt-Template für alle Shots:**
```
[CHARAKTER-BLOCK — in jedem Prompt identisch:]
"A woman in her mid-40s, auburn hair in a neat bun,
 navy blue blazer, pearl necklace, warm brown eyes"

[SZENEN-BLOCK — variiert pro Shot:]
"Shot 3: She leans forward slightly, gesturing at the
 screen with her right hand. Medium close-up,
 slight dolly left. Warm office lighting."
```

> **Volksbank-Analogie:** Das Charakter-Sheet ist wie die Personalakte eines Mitarbeiters — die Fotos darauf stellen sicher, dass jeder weiß, wie die Person aussieht, egal ob am Schalter, im Beratungszimmer oder auf dem Parkplatz. Ohne Personalakte verwechselt die KI bei jedem neuen „Einsatzort" die Person.

### Konsistenz-Tabelle: Was funktioniert wie gut?

| Methode | Setup-Zeit | Konsistenz (Gesicht) | Konsistenz (Kleidung) | Flexibilität (Posen) | Kosten |
|---------|-----------|---------------------|----------------------|---------------------|--------|
| I2V mit Referenz | 5 Min | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐ (an Pose gebunden) | Niedrig |
| Face-Lock (Kling 3.0) | 10 Min | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Mittel |
| LoRA-Training | 2-4 Std | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Hoch ($5-20) |
| Nur Prompt | 0 Min | ⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ | Kostenlos |

> **Für Fortgeschrittene — LoRA in der Praxis:** Wer LoRA ausprobieren will, startet am einfachsten auf **Replicate.com** — dort können Sie 10-20 Bilder hochladen, einen Trigger-Word definieren (z.B. „ohwx person") und das Training in der Cloud laufen lassen (~$2-5 pro Trainingsrun). Für lokales Training brauchen Sie eine GPU mit mindestens 12 GB VRAM und das Open-Source-Tool **kohya_ss** in Kombination mit **ComfyUI**. Alle großen Modelle sind auch per **API** steuerbar (Runway, Kling, Veo über die jeweiligen Entwickler-Portale) — ideal, wenn Sie den Workflow automatisieren möchten.

---

## Schritt 6: Nachbearbeitung — Vom Rohschnitt zum fertigen Video

KI generiert einzelne Clips. Ein fertiges Video entsteht in der **Nachbearbeitung** — dem klassischen Videoschnitt. Hier kombinieren Sie Ihre KI-Clips mit Übergängen, Farbkorrektur, Untertiteln und der finalen Audio-Mischung.

### Die Nachbearbeitungs-Pipeline

```
KI-CLIPS → IMPORT → TIMELINE → FEINSCHNITT → COLOR → AUDIO → EXPORT

┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
│ KI-Clips │→ │ Schnitt- │→ │ Übergänge│→ │ Farb-    │→ │ Audio-   │→ FERTIG
│ sammeln  │  │ programm │  │ + Timing │  │ korrektur│  │ Mischung │
│          │  │ importier│  │          │  │          │  │ + Unter- │
│          │  │          │  │          │  │          │  │ titel    │
└──────────┘  └──────────┘  └──────────┘  └──────────┘  └──────────┘
```

### Welches Schnittprogramm?

| Programm | Preis | KI-Features | Für wen? |
|----------|-------|-------------|----------|
| **CapCut** ⭐ Empfehlung für Einsteiger | Kostenlos / $9.99/mo | Auto-Cut, Smart-Untertitel, Effekte | Einsteiger, Social Media |
| **DaVinci Resolve** | Kostenlos (!) | Magic Mask, Voice Isolation, Farbkorrektur | Fortgeschrittene, professioneller Look |
| **Adobe Premiere Pro** | $22.99/mo | Generative Extend, Auto-Remix, AI-Schnitt | Profis, bestehendes Adobe-Ökosystem |
| **Descript** | $24/mo | Text-basierter Schnitt (!) — editieren wie in Word | Podcaster, Erklärvideos |

> **Volksbank-Analogie:** CapCut ist wie die Online-Banking-App — schnell, einfach, für die meisten Fälle ausreichend. DaVinci Resolve ist wie die vollwertige Banking-Software — kostenlos, unglaublich mächtig, aber mit Lernkurve. Premiere Pro ist wie das SAP-System — Industriestandard, aber nur sinnvoll wenn Sie es täglich nutzen.

### Tipps für den KI-Video-Schnitt

**1. Schnitte an Bewegungspunkten setzen:**
KI-Videos haben manchmal „weiche Stellen" — Momente, in denen die Physik kurz stockt oder Artefakte aufblitzen. Setzen Sie Ihre Schnitte genau an diesen Stellen, und der Zuschauer bemerkt nichts.

**2. Farbkorrektur vereinheitlicht:**
Verschiedene KI-Modelle und verschiedene Generierungen haben leicht unterschiedliche Farbprofile. Eine einheitliche Farbkorrektur (Color Grading) in der Nachbearbeitung lässt alles aus einem Guss aussehen.

**3. Audio-Brücken über Schnitte:**
Selbst wenn die KI natives Audio generiert hat: Lassen Sie die Hintergrundmusik oder Ambient-Sounds über die Schnitte hinweg weiterlaufen. Das verbindet Szenen stärker als jeder visuelle Übergang.

**4. Tempo variieren:**
KI-Clips haben oft gleichmäßiges Tempo. Im Schnittprogramm können Sie Clips beschleunigen (Zeitraffer für Establishing Shots) oder verlangsamen (Slow Motion für emotionale Momente).

**5. Untertitel sind Pflicht:**
85% aller Social-Media-Videos werden ohne Ton angesehen. Auto-Untertitel in CapCut oder Descript sind in Sekunden erstellt.

---

## Was kann diese Technik (noch) nicht?

Wie jede KI-Technologie hat auch das KI-gestützte Video-Editing klare Grenzen. Hier sind die wichtigsten Limitationen — spezifisch für Sie als Bankmitarbeiter:

### Limitationen im Überblick

| Limitation | Warum das ein Problem ist | Workaround |
|-----------|--------------------------|-----------|
| **Charakter-Drift über viele Shots** | Ab 10+ Shots driftet selbst Face-Lock merklich. Für einen 3-Minuten-Film mit 20 Shots ist das kritisch | Shots in Blöcken von 3-5 generieren, zwischen Blöcken manuell Referenzen anpassen |
| **Keine exakte Text-Kontrolle** | Wenn Ihr Video einen Bildschirm mit konkretem Text zeigen soll (z.B. Kontonummer, Formular), wird der Text unleserlich oder falsch | Text in der Nachbearbeitung als Overlay einfügen — nie im KI-Prompt |
| **Physik-Fehler bei komplexen Interaktionen** | Zwei Personen, die sich die Hand geben, ein Stift der unterschrieben wird — feinmotorische Aktionen scheitern oft | Solche Szenen vermeiden oder sehr kurz halten (<2s) |
| **Zeitliche Kohärenz über 30+ Sekunden** | Selbst mit Extensions wird die Qualität nach 3-4 Verlängerungen schlechter | Szenen kurz halten (5-10s), im Schnittprogramm zusammenbauen |
| **Brand-Compliance** | KI-generierte Videos enthalten keine garantiert korrekten Logos, CI-Farben oder Schriftarten | CI-Elemente immer in der Nachbearbeitung einfügen |
| **Rechtliche Unklarheit** | Wem gehört das generierte Video? Darf es kommerziell genutzt werden? Je nach Modell und Tarifstufe verschieden | Immer die Nutzungsbedingungen prüfen; Runway bietet klare kommerzielle Lizenzen |

### Technologie allein vs. Gesamtsystem

Viele dieser Limitationen gelten für die **KI-Generierung allein**. Im **Gesamtworkflow** (KI-Generierung + Nachbearbeitung) sind die meisten lösbar:

- Text-Overlays → Schnittprogramm
- Logo/CI → After Effects oder CapCut
- Farbkonsistenz → Color Grading
- Audio-Nahtstellen → Audio-Mischung in Post

Die KI ist das Rohmaterial. Die Nachbearbeitung macht daraus ein professionelles Produkt. Wer nur auf die KI-Generierung schaut, unterschätzt das Gesamtsystem.

> **Für Ihren Bankalltag heißt das:** Ein KI-generiertes Erklärvideo direkt aus dem Generator zu veröffentlichen ist wie einen Kreditantrag ohne Prüfung durchzuwinken. Es fehlt die Qualitätssicherung. Die Nachbearbeitung *ist* Ihre Qualitätssicherung.

---

## Kosten-Vergleich: KI-Workflow vs. klassische Produktion

Was kostet ein 60-Sekunden-Erklärvideo für Ihre Filiale — klassisch vs. mit KI?

| Posten | Klassische Produktion | KI-Workflow | Ersparnis |
|--------|----------------------|-------------|-----------|
| **Konzept & Skript** | 500–1.000 € (Agentur) | 0 € (selbst oder mit KI-Textassistent) | ~100% |
| **Dreh** (Kamera, Licht, Team) | 2.000–5.000 € | 0 € | 100% |
| **Schauspieler / Sprecher** | 500–1.500 € | 0–20 € (KI-Stimme) | ~98% |
| **Schnitt & Post-Production** | 1.000–3.000 € | 50–100 € (Abo-Kosten Tools) | ~95% |
| **KI-Generierung** | — | 20–50 € (Credits/Abos) | — |
| **Gesamt** | **4.000–10.500 €** | **70–170 €** | **~98%** |
| **Zeitaufwand** | 2–4 Wochen | 1–2 Tage | ~90% |

**Wichtige Einschränkung:** Diese Rechnung gilt für einfache Erklärvideos und Social-Media-Content. Für imageträchtige Markenfilme, TV-Spots oder Videos mit echten Mitarbeitern bleibt klassische Produktion oft die bessere Wahl — KI-generierte Gesichter können bei genauem Hinsehen noch als künstlich erkannt werden.

> **Der Business Case für Ihre Bank:** Wenn Sie statt eines teuren Agentur-Videos vier KI-Videos pro Monat produzieren können, steigt Ihre Content-Frequenz um das 4-fache bei einem Bruchteil der Kosten. Für Social Media — wo Quantität und Aktualität zählen — ist das ein klarer Vorteil.

---

## Werkzeuge & Stellschrauben: Der komplette Workflow auf einen Blick

### Die empfohlene Tool-Kette

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    DER KOMPLETTE KI-VIDEO-WORKFLOW                        │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  PHASE 1: PLANUNG                                                        │
│  ┌─────────────┐     ┌────────────────┐     ┌───────────────┐           │
│  │ Skript      │ ──→ │ Shot-Cards     │ ──→ │ Referenzbilder│           │
│  │ (ChatGPT /  │     │ (Notion /      │     │ (Midjourney / │           │
│  │  Claude)    │     │  Google Docs)  │     │  DALL-E / Flux│           │
│  └─────────────┘     └────────────────┘     └───────────────┘           │
│                                                                          │
│  PHASE 2: GENERIERUNG                                                    │
│  ┌─────────────────────────────────────────────────────────┐            │
│  │  Image-to-Video: Kling 3.0 / Runway Gen-4 / Veo 3.1   │            │
│  │  Scene Extension: gleiches Modell wie Hauptclip         │            │
│  │  V2V (falls nötig): Runway Aleph                       │            │
│  └─────────────────────────────────────────────────────────┘            │
│                                                                          │
│  PHASE 3: NACHBEARBEITUNG                                                │
│  ┌─────────────┐     ┌────────────────┐     ┌───────────────┐           │
│  │ Zusammen-   │ ──→ │ Farbkorrektur  │ ──→ │ Audio-Mix +   │           │
│  │ schnitt     │     │ + Übergänge    │     │ Untertitel    │           │
│  │ (CapCut /   │     │ (DaVinci)      │     │ + Export      │           │
│  │  DaVinci)   │     │                │     │               │           │
│  └─────────────┘     └────────────────┘     └───────────────┘           │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Stellschrauben pro Phase

| Phase | Stellschraube | Empfehlung |
|-------|--------------|------------|
| Planung | Anzahl Shots | 8–15 für 60-Sekunden-Video |
| Planung | Shot-Dauer | 3–8 Sekunden pro Shot |
| Planung | Referenzbilder pro Charakter | 5–8 aus verschiedenen Winkeln |
| Generierung | Varianten pro Shot | 2–4 generieren, beste auswählen |
| Generierung | Extensions pro Clip | Maximal 2–3 |
| Generierung | Modell-Mix | Ja — verschiedene Modelle für verschiedene Shot-Typen |
| Nachbearbeitung | Übergänge | Harte Schnitte bevorzugen, Überblendungen sparsam |
| Nachbearbeitung | Farbkorrektur | Immer — vereinheitlicht den Look |
| Nachbearbeitung | Audio | Durchgehende Musikspur + Ambient als Klammer |

---

## Pipeline-Zusammenfassung

```
GESAMTE PIPELINE: VOM KONZEPT ZUM FERTIGEN VIDEO

KONZEPT          STORYBOARD         REFERENZEN         GENERIERUNG
───────          ──────────         ──────────         ───────────
  │                  │                  │                   │
  ▼                  ▼                  ▼                   ▼
┌──────┐      ┌────────────┐     ┌──────────┐      ┌────────────┐
│Idee  │─────→│Shot-Cards  │────→│Charakter-│─────→│I2V / T2V   │
│Skript│      │mit Prompts │     │Sheet     │      │+ Extension │
│Ziel  │      │Timing      │     │Face-Lock │      │+ V2V       │
└──────┘      │Kamera      │     │LoRA      │      │2-4 Varianten│
              └────────────┘     └──────────┘      └────────────┘
                                                        │
                                                        ▼
              NACHBEARBEITUNG              ←─────  REVIEW
              ─────────────────                    ──────
              ┌────────────────┐            ┌───────────┐
              │Schnitt (CapCut/│ ←──────── │Passt der   │
              │DaVinci)        │            │Clip? Farbe?│
              │Farbkorrektur   │            │Konsistenz? │
              │Audio-Mix       │            │→ Ja: weiter│
              │Untertitel      │            │→ Nein: neu │
              │CI-Overlays     │            │  generieren│
              │Export          │            └───────────┘
              └────────────────┘
                    │
                    ▼
              ┌────────────┐
              │ FERTIGES   │
              │ VIDEO      │
              │ 🎬         │
              └────────────┘
```

---

## Das Wichtigste auf einen Blick

| Konzept | Kernaussage |
|---------|-------------|
| **Image-to-Video** | Die wichtigste Technik: Referenzbild steuert Aussehen, Prompt steuert nur Bewegung |
| **Video-to-Video** | Bestehendes Video transformieren — Stil, Licht, Objekte ändern ohne Neudreh |
| **Scene Extension** | Clips verlängern über das Zeitlimit hinaus — max. 2–3× empfohlen |
| **Storyboard-Workflow** | Professionelle Planung: Skript → Shot-Cards → Referenzen → Generierung → Schnitt |
| **Multi-Shot-Konsistenz** | Das härteste Problem — gelöst durch Kombination aus I2V + Face-Lock + Prompt-Disziplin |
| **Face-Lock** | Kling 3.0 und Seedance 2.0 sperren Gesicht/Kleidung per Referenz-Upload |
| **LoRA-Training** | Für wiederkehrende Charaktere: Modell-Adapter trainieren (10-30 Bilder, 2-4 Stunden) |
| **Nachbearbeitung** | Unverzichtbar — Farbkorrektur, Audio-Mix, Untertitel und CI-Overlays machen den Unterschied |
| **Kosten** | 60-Sekunden-Erklärvideo: ~100 € (KI) vs. ~7.000 € (klassisch) |
| **Limitation** | Charakter-Drift bei 10+ Shots, keine exakte Textkontrolle, Physik-Fehler bei Interaktionen |

---

## Parallelen zu vorherigen Tutorials

- **Tutorial 04-01 (Grundlagen):** Dort lernten Sie die drei Wege zum Video (T2V, I2V, V2V). Hier vertiefen wir alle drei und fügen Scene Extension + Inpainting/Outpainting hinzu
- **Tutorial 04-02 (Kamera & Bewegung):** Die Shot-Typen und Kamerabewegungen aus 04-02 fließen direkt in Ihre Shot-Cards ein — jeder Shot braucht eine bewusste Kameraentscheidung
- **Tutorial 04-03 (Audio):** Audio-Planung ist Teil jeder Shot-Card. Das native Audio aus 04-03 wird in der Nachbearbeitung mit der Gesamtmischung harmonisiert
- **Tutorial 03-04 (Bildbearbeitung):** Die iterativen Verfeinerungstechniken für Bilder (Inpainting, Outpainting, Upscaling) haben ihre Entsprechungen in der Videobearbeitung
- **Tutorial 00-02 (Diffusion):** Das Verständnis, warum Diffusionsmodelle stochastisch arbeiten, erklärt direkt, warum Charakter-Konsistenz so schwer ist

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Image-to-Video (I2V)** | Technik, bei der ein Standbild als Ausgangspunkt für die Videogenerierung dient. Die KI animiert das Bild basierend auf einem Bewegungs-Prompt |
| **Video-to-Video (V2V)** | Transformation eines bestehenden Videos — Stil, Beleuchtung oder Inhalte ändern bei Beibehaltung der Grundstruktur |
| **Scene Extension** | Verlängerung eines bestehenden Clips über das Zeitlimit hinaus, indem das letzte Frame als Startpunkt für eine Fortsetzung dient |
| **Storyboard** | Visuelle Szene-für-Szene-Planung eines Videos. In der KI-Produktion: Shot-Cards mit Prompts, Referenzbildern und Timing |
| **Shot-Card** | Planungsdokument für einen einzelnen Videoshot: Beschreibung, Kamerawinkel, Dauer, Audio, Referenzbild, Prompt |
| **Multi-Shot-Konsistenz** | Die Fähigkeit, Charaktere und Umgebungen über mehrere separat generierte Videoclips hinweg visuell identisch zu halten |
| **Face-Lock** | Feature (Kling 3.0, Seedance 2.0), das Gesichtszüge und Erscheinung eines Charakters basierend auf Referenzmaterial „sperrt" |
| **LoRA** | Low-Rank Adaptation — kleiner Modell-Adapter (50–200 MB), der auf 10–30 Bilder eines Charakters trainiert wird und dessen Identität in beliebigen Szenen reproduziert |
| **Character Sheet** | Set von 5–8 KI-generierten oder echten Bildern eines Charakters aus verschiedenen Winkeln, als Referenz für konsistente Videoproduktion |
| **Inpainting** | Teile eines Videos selektiv verändern — Objekte entfernen, ersetzen oder hinzufügen |
| **Outpainting** | Den Bildausschnitt eines Videos erweitern — z.B. von 9:16 auf 16:9 umwandeln |
| **NLE** | Non-Linear Editing — digitaler Videoschnitt, bei dem Clips in beliebiger Reihenfolge auf einer Timeline arrangiert werden |
| **Color Grading** | Nachträgliche Farbkorrektur, die allen Clips einen einheitlichen Look gibt |
| **Aleph** | Runways dediziertes V2V-Modell (Dez 2025) — kombiniert Stil-Transfer, Relighting, Inpainting und Outpainting |
| **Multi-Shot-Modus** | Feature in Kling 3.0, das szenenübergreifende Generierung mit geteiltem Charakter-Verständnis ermöglicht |

---

## 🔬 Probieren Sie es selbst!

### Übung 1: Vom Standbild zum Videoclip (I2V-Grundlagen)

**Ziel:** Verstehen, wie Image-to-Video funktioniert und warum der Prompt nur Bewegung beschreiben sollte.

**Dauer:** 10 Minuten

**Was Sie brauchen:** Zugang zu einem KI-Bildgenerator (DALL-E in ChatGPT, Gemini) + einem KI-Videogenerator (Kling kostenlos, oder Sora/Veo über ChatGPT Plus/Gemini Advanced)

1. **Referenzbild erstellen:** Generieren Sie mit DALL-E oder Gemini ein Porträtfoto einer fiktiven Bankberaterin:
   > „Professional portrait photo of a friendly woman in her 40s, auburn hair in a bun, navy blazer, pearl earrings, warm smile. Office background with blurred bookshelves. High resolution, natural lighting."

2. **Video generieren (falsch):** Nutzen Sie das Bild als I2V-Input und beschreiben Sie das Aussehen nochmal:
   > „A woman with auburn hair in a navy blazer turns to the camera and smiles"

3. **Video generieren (richtig):** Gleiches Bild, aber nur Bewegung beschreiben:
   > „The person slowly turns toward the camera, tilts her head slightly, and gives a warm, professional nod. Subtle camera zoom in. Soft office ambiance."

4. **Vergleichen:** Achten Sie auf den Unterschied — insbesondere bei Gesichtstreue und natürlicher Bewegung.

### Übung 2: Zwei Shots, ein Charakter (Konsistenz-Test)

**Ziel:** Erleben, warum Charakter-Konsistenz ein Problem ist — und wie I2V es löst.

**Dauer:** 15 Minuten

1. **Text-to-Video — Shot 1:**
   > „A woman in her 40s with auburn hair and a navy blazer sits at a desk in a modern bank office, looking at documents. Medium shot."

2. **Text-to-Video — Shot 2 (gleicher Prompt, neuer Clip):**
   > „A woman in her 40s with auburn hair and a navy blazer stands up from her desk and walks toward the camera. Medium shot."

3. **Vergleichen:** Sehen die beiden Frauen gleich aus? (Spoiler: Nein.)

4. **Jetzt mit I2V:** Nehmen Sie Ihr Referenzbild aus Übung 1 und generieren Sie beide Shots damit. Vergleichen Sie die Konsistenz.

### Übung 3: Mini-Storyboard — 3 Shots, 1 Geschichte

**Ziel:** Den kompletten Storyboard-Workflow einmal durchspielen.

**Dauer:** 30 Minuten (nehmen Sie sich beim ersten Mal ruhig länger — das ist die Königsdisziplin dieses Tutorials!)

1. **Skript schreiben (3 Szenen):**
   - Shot 1: Beraterin am Schreibtisch, schaut auf den Bildschirm
   - Shot 2: Beraterin wendet sich dem Kunden zu, lächelt
   - Shot 3: Beide schauen gemeinsam auf ein Dokument

2. **Shot-Cards erstellen:** Für jeden Shot: Kamerawinkel, Dauer, Audio, Prompt

3. **Referenzbild(er) erstellen:** Mindestens 1 Referenz für die Beraterin

4. **3 Clips generieren:** Via I2V mit Ihrem Referenzbild

5. **Zusammenschneiden:** In CapCut (kostenlos) oder einem anderen Tool Ihrer Wahl — Übergänge, Hintergrundmusik, fertig

**Reflexion:** Was hat gut funktioniert? Wo war die Konsistenz problematisch? Was würden Sie beim nächsten Mal anders machen?

---

