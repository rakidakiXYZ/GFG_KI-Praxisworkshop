# Prompting für Bewegung und Kameraführung

**Der Regiestuhl — Denken wie ein Regisseur: Kamerabewegungen, Shot-Typen, Timing und wie Sie der KI sagen, was sie filmen soll**

---

## Warum dieses Tutorial?

In Tutorial 04-01 haben Sie die Landkarte kennengelernt — acht Modelle, drei Wege zum Video, das 8-Bausteine-Framework. Zwei dieser Bausteine haben wir dort nur angerissen: **Kamera** und **Aktion**.

Genau diese beiden machen den Unterschied zwischen einem Video, das „irgendwie bewegt" wirkt, und einem, das sich wie ein richtiger Film anfühlt.

Denn hier liegt das Paradox: KI-Videomodelle können atemberaubende Bilder erzeugen — aber sie wissen nicht automatisch, *wie* man eine Szene filmt. Sie haben keinen inneren Regisseur. Wenn Sie nicht beschreiben, wo die Kamera steht, wie sie sich bewegt und was der Rhythmus der Szene ist, improvisiert die KI. Manchmal gut. Oft nicht.

Dieses Tutorial macht Sie zum Regisseur. Sie lernen die Sprache des Films — nicht als Filmstudent, sondern als jemand, der in 10 Minuten ein überzeugendes Video für LinkedIn oder die Hauptversammlung braucht.

**Was Sie nach diesem Tutorial wissen werden:**

- Welche Kamerabewegungen es gibt und welche Emotion jede auslöst
- Wie Shot-Typen (Close-up, Wide, Tracking) die Wirkung einer Szene verändern
- Wie Sie Bewegung und Timing so beschreiben, dass die KI sie zuverlässig umsetzt
- Welche Modelle welche Kameraanweisungen am besten verstehen
- Wie Sie professionelle Filmsprache in Ihren Prompts einsetzen — ohne Filmschule
- Warum „weniger Bewegung = bessere Ergebnisse" die wichtigste Regel ist

---

## Die Grundregel: Ein Shot, eine Bewegung, eine Aktion

Bevor wir in die Details gehen, die wichtigste Erkenntnis aus der Praxis — und sie gilt für **alle** KI-Videomodelle:

```
┌──────────────────────────────────────────────────────────┐
│                  DIE GOLDENE REGEL                        │
│                                                          │
│   Ein Video-Prompt = Ein Shot                            │
│   Ein Shot = Eine Kamerabewegung                         │
│   Eine Kamerabewegung = Eine Hauptaktion                 │
│                                                          │
│   ✅ "Kamera schwenkt langsam nach rechts,               │
│       Beraterin steht auf und geht zum Fenster"          │
│                                                          │
│   ❌ "Kamera fährt rein, schwenkt dann links,            │
│       zoomt raus, Person dreht sich, läuft los,          │
│       greift ein Telefon, setzt sich, tippt"             │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

**Warum?** KI-Videomodelle generieren 4–25 Sekunden Film. In diesem Zeitfenster können sie **eine** flüssige Bewegung zuverlässig umsetzen. Mehrere Bewegungen gleichzeitig — Kamera schwenkt UND zoomt UND Person läuft UND dreht sich — überfordern das Modell. Das Ergebnis: unnatürliche Übergänge, springende Perspektiven, physikalisch unmögliche Bewegungen.

> **Volksbank-Analogie:** Stellen Sie sich vor, Sie geben einem neuen Praktikanten seine erste Aufgabe. „Archiviere diese Mappe" — kein Problem. „Archiviere die Mappe, ruf gleichzeitig den Kunden an, aktualisiere das CRM und bereite den Kaffee vor" — Chaos. Genauso arbeiten KI-Modelle: Eine klare Anweisung, ein sauberes Ergebnis.

### Die Faustregel für Prompt-Länge und Bewegung

| Clip-Länge | Empfohlene Kamerabewegungen | Empfohlene Aktionen |
|-----------|---------------------------|-------------------|
| 4 Sekunden | 1 einfache Bewegung | 1 kurze Aktion oder Geste |
| 8 Sekunden | 1 Bewegung, ggf. mit Übergang | 1–2 Beats (Aktionsschritte) |
| 12–15 Sekunden | 1–2 Bewegungen | 2–3 Beats |
| 25 Sekunden (Sora 2) | 2–3 Bewegungen, klar getrennt | 3–5 Beats |

---

## Kamerabewegungen: Die Sprache des Regisseurs

Jede Kamerabewegung erzählt etwas anderes. Hier sind die wichtigsten — mit dem, was sie emotional auslösen, und wie Sie sie in Prompts beschreiben.

### Übersicht: Kamerabewegungen und ihre Wirkung

```
┌──────────────────────────────────────────────────────────────┐
│              KAMERABEWEGUNGEN IM ÜBERBLICK                    │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  PAN (Schwenk horizontal)                                    │
│  ◄────────────────►                                          │
│  Kamera dreht sich auf Stativ nach links/rechts              │
│  → Raum zeigen, Umgebung erkunden, jemandem folgen           │
│                                                              │
│  TILT (Schwenk vertikal)                                     │
│       ▲                                                      │
│       │                                                      │
│       ▼                                                      │
│  Kamera neigt sich nach oben/unten                           │
│  → Größe betonen, etwas enthüllen, Ehrfurcht erzeugen        │
│                                                              │
│  DOLLY (Fahrt vor/zurück)                                    │
│  ═══════════►  oder  ◄═══════════                            │
│  Kamera bewegt sich physisch auf Subjekt zu/weg              │
│  → Intimität aufbauen (rein) oder Distanz (raus)             │
│                                                              │
│  TRACKING (Seitliche Fahrt)                                  │
│  ═══════════════════►                                        │
│  Kamera begleitet Subjekt parallel                           │
│  → Dynamik, Energie, Begleitung                              │
│                                                              │
│  DRONE / AERIAL (Drohnenflug)                                │
│       ╱  ╲                                                   │
│      ╱    ╲                                                  │
│     ╱      ╲                                                 │
│  Kamera fliegt über die Szene                                │
│  → Überblick, Majestät, Establishing Shot                    │
│                                                              │
│  ZOOM (Brennweite)                                           │
│  ○───────────────●                                           │
│  Optische Annäherung ohne Kamerabewegung                     │
│  → Fokus auf Detail, dramatische Enthüllung                  │
│                                                              │
│  STATIC (Stativ)                                             │
│  [■]                                                         │
│  Kamera bewegt sich nicht                                    │
│  → Ruhe, Beobachtung, dokumentarisch                         │
│                                                              │
│  HANDHELD (Handkamera)                                       │
│  [~■~]                                                       │
│  Leichtes Wackeln, organisch                                 │
│  → Authentizität, Nähe, Reportage-Stil                       │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### Im Detail: Jede Bewegung mit Prompt-Beispielen

#### 1. Pan (Horizontaler Schwenk)

Die Kamera steht auf einem Stativ und dreht sich horizontal — wie wenn Sie Ihren Kopf nach links oder rechts drehen, ohne sich von der Stelle zu bewegen.

**Wirkung:** Zeigt Raum, führt den Blick, verbindet zwei Elemente in einer Szene.

**Wann einsetzen:**
- Büro oder Filiale zeigen: Pan über den gesamten Raum
- Einer Person mit den Augen folgen
- Von einem Objekt zu einem anderen überleiten

```
Prompt-Beispiel (Pan):

Camera slowly pans left to right across a modern bank lobby.
Morning sunlight illuminates the reception area, then reveals
a team of consultants preparing for the day. Smooth, steady
movement. Corporate documentary style, warm color grading.
```

**Varianten:**
- `slow pan left to right` — ruhig, beobachtend
- `quick pan` / `whip pan` — schneller Schwenk, dynamisch, Energieschub
- `pan following the subject` — Kamera folgt einer Person

> **Volksbank-Analogie:** Ein Pan ist wie der Blick, den ein neuer Kunde durch Ihre Filiale schweifen lässt — von links nach rechts, alles aufnehmen, sich orientieren. Ein schneller Pan (Whip Pan) ist wie der Blick zum Kollegen, wenn ein überraschend großer Auftrag reinkommt.

---

#### 2. Tilt (Vertikaler Schwenk)

Die Kamera neigt sich auf dem Stativ nach oben oder unten — wie wenn Sie den Kopf heben, um ein Gebäude zu betrachten, oder senken, um auf Ihre Schuhe zu schauen.

**Wirkung:** Betont Höhe, Größe, Macht — oder enthüllt etwas schrittweise von oben nach unten.

**Wann einsetzen:**
- Gebäudefassade von unten nach oben zeigen (Tilt up)
- Person von Kopf bis Fuß vorstellen (Tilt down)
- Etwas am Boden enthüllen (Tilt down)

```
Prompt-Beispiel (Tilt):

Camera tilts slowly upward from the marble floor of a bank
headquarters lobby. The tilt reveals polished pillars, a
grand staircase, and finally the glass ceiling flooding the
space with natural light. Majestic, cinematic, wide angle.
```

**Varianten:**
- `tilt up` — Ehrfurcht, Aufstieg, Größe
- `tilt down` — Enthüllung, Fokus auf Detail, Landung
- `slow tilt` — feierlich, majestätisch
- `quick tilt` — Überraschung, Schock

---

#### 3. Dolly (Fahrt vor/zurück)

Die gesamte Kamera bewegt sich physisch auf das Subjekt zu (Dolly in) oder davon weg (Dolly out). Nicht zu verwechseln mit Zoom — beim Dolly ändert sich die **Perspektive**, nicht nur die Vergrößerung.

**Wirkung:**
- **Dolly in:** Zieht den Zuschauer in die Szene hinein. Intimität, Fokus, Spannung.
- **Dolly out:** Entfernt sich, zeigt den Kontext. Abschluss, Überblick, Einsamkeit.

**Wann einsetzen:**
- Emotionaler Moment: Dolly in auf das Gesicht
- Establishing Shot: Dolly out, um den gesamten Raum zu zeigen
- Spannungsaufbau: Langsamer Dolly in auf ein Detail

```
Prompt-Beispiel (Dolly in):

Slow dolly-in toward a bank consultant sitting at her desk.
She looks up from her laptop and smiles warmly at the camera.
Shallow depth of field, background softly blurred. Warm
afternoon light from the side window. Medium shot transitioning
to close-up. Professional, inviting atmosphere.
```

```
Prompt-Beispiel (Dolly out):

Camera starts on a close-up of a handshake between two people,
then slowly dollies out to reveal a modern meeting room with
a panoramic city view. Five colleagues around a glass table.
Late afternoon golden light. Corporate, optimistic mood.
```

**Der Dolly-Zoom (Vertigo-Effekt):**

Ein Spezialeffekt, bei dem die Kamera sich zurückbewegt, während gleichzeitig hineingezoomt wird (oder umgekehrt). Der Hintergrund scheint sich zu verzerren, während das Subjekt gleich groß bleibt.

```
Prompt-Beispiel (Dolly Zoom):

Dolly zoom effect on a young man standing in an empty bank
vault. The background stretches and distorts while his face
stays centered. Dramatic, suspenseful lighting. Single
overhead light source creating deep shadows.
```

**Achtung:** Der Dolly-Zoom ist komplex. Nicht alle Modelle setzen ihn zuverlässig um. **Veo 3.1** und **Sora 2** verstehen ihn am besten. Bei anderen Modellen kann das Ergebnis unberechenbar sein.

> **Volksbank-Analogie:** Ein Dolly-in ist wie das Gespräch, das vom Small Talk zur persönlichen Beratung wird — Sie kommen dem Kunden immer näher. Ein Dolly-out ist wie der Blick aus dem Bürofenster nach einem erfolgreichen Abschluss — Sie lehnen sich zurück und sehen das große Ganze.

---

#### 4. Tracking Shot (Seitliche Fahrt / Verfolgung)

Die Kamera begleitet ein sich bewegendes Subjekt — seitlich, von hinten oder von vorne. Die klassischste Form: Kamera fährt parallel neben einer gehenden Person.

**Wirkung:** Dynamik, Energie, Begleitung. Der Zuschauer „geht mit".

**Wann einsetzen:**
- Person durch ein Gebäude begleiten
- Dynamische Produktpräsentation
- Energetische Recruiting-Videos

```
Prompt-Beispiel (Tracking):

Camera tracks alongside a young professional as she walks
confidently through a modern open-plan office. Colleagues
wave and smile as she passes. Steadicam, eye level, smooth
movement. Bright, energetic atmosphere. Natural daylight
from floor-to-ceiling windows.
```

**Varianten:**
- `tracking left to right` — seitliche Begleitung
- `following from behind` — Kamera hinter dem Subjekt
- `leading from the front` — Kamera vor dem Subjekt, filmt das Gesicht
- `orbit / arc shot` — Kamera umkreist das Subjekt

```
Prompt-Beispiel (Orbit/Arc):

Camera slowly orbits around a team of four people standing
in a circle, discussing a project. The orbit reveals the
modern office environment from all angles. Warm lighting,
shallow depth of field. Collaborative, dynamic mood.
```

> **Volksbank-Analogie:** Ein Tracking Shot ist wie die Begleitung eines neuen Mitarbeiters am ersten Tag — Sie gehen neben ihm durch die Filiale, zeigen ihm alles, die Kamera ist sein Begleiter. Ein Orbit ist wie das Gefühl bei einer guten Teamrunde: alle verbunden, die Energie kreist.

---

#### 5. Drone / Aerial Shot (Drohnenaufnahme)

Die Kamera fliegt — über ein Gebäude, eine Landschaft, eine Menschenmenge. Der klassische Establishing Shot für große Szenen.

**Wirkung:** Überblick, Majestät, Kontext. Zeigt „das große Ganze".

**Wann einsetzen:**
- Firmengebäude oder -gelände zeigen
- Stadtpanorama als Eröffnung
- Event-Impression aus der Vogelperspektive

```
Prompt-Beispiel (Drone):

Aerial drone shot slowly flying over a modern glass office
building surrounded by green parks. Camera descends gradually
toward the main entrance. Morning sunlight, long shadows.
Cinematic, establishing shot. Cool blue and warm gold tones.
```

**Varianten:**
- `drone ascending` — Aufstieg, Weite enthüllen
- `drone descending` — Annäherung, von der Übersicht zum Detail
- `drone flyover` — Überflug, Panorama
- `drone orbit` — Kamera kreist um ein Gebäude
- `bird's-eye view` — direkt von oben, senkrecht nach unten

```
Prompt-Beispiel (Bird's-eye):

Bird's-eye view of a busy city intersection at rush hour.
Cars, buses, and pedestrians create geometric patterns of
movement. The camera holds steady, observing from directly
above. Time seems to slow down. Urban, contemplative mood.
```

> **Volksbank-Analogie:** Eine Drohnenaufnahme ist wie der Blick aus dem Fenster des Vorstandsbüros im 10. Stock — Sie sehen das große Ganze, die Stadt, die Filiale im Kontext. Perfekt für den Jahresbericht oder die Hauptversammlung.

---

#### 6. Zoom (Brennweitenveränderung)

Die Kamera bleibt stehen, aber die Optik vergrößert (Zoom in) oder verkleinert (Zoom out). Anders als beim Dolly verändert sich nicht die Perspektive, nur die Vergrößerung.

**Wirkung:**
- **Zoom in:** Aufmerksamkeit auf Detail lenken, dramatische Enthüllung
- **Zoom out:** Kontext zeigen, Überraschung durch Enthüllung des Umfelds

```
Prompt-Beispiel (Zoom in):

Static camera. Slow zoom into the screen of a laptop showing
financial charts. The numbers on the screen become readable.
Soft office lighting, shallow depth of field. Corporate,
analytical mood. The zoom takes the full 8 seconds.
```

**Dolly vs. Zoom — der Unterschied im Prompt:**

| Anweisung | Was passiert | Wann verwenden |
|-----------|-------------|---------------|
| `dolly in` | Kamera bewegt sich physisch näher | Natürliche Annäherung, Intimität |
| `zoom in` | Optik vergrößert, Kamera steht still | Fokus auf Detail, analytisch |
| `push in` | Allgemeinerer Begriff, KI interpretiert frei | Wenn beides OK ist |

**Praxis-Tipp:** Der Begriff `push in` wird von den meisten KI-Modellen als sanfter Dolly-in interpretiert und ist der sicherste Universalbegriff, wenn Sie keine spezifische Technik brauchen.

---

#### 7. Static Shot (Statische Kamera)

Die Kamera bewegt sich überhaupt nicht. Stativ, fest, unbewegt.

**Wirkung:** Ruhe, Beobachtung, dokumentarische Distanz. Lässt die Aktion vor der Kamera wirken.

**Wann einsetzen:**
- Dialoge und Gespräche
- Dokumentarische Szenen
- Wenn die Aktion im Bild genug Bewegung hat

```
Prompt-Beispiel (Static):

Static wide shot of a bank consultation room. Two people sit
across a desk — a consultant gestures toward a document while
the customer nods thoughtfully. Camera doesn't move. Natural
window light, clean composition. Documentary style.
```

**Warum Static manchmal die beste Wahl ist:** Bei KI-Video gilt: Je weniger die Kamera tun muss, desto mehr Rechenleistung bleibt für die **Aktion** im Bild. Ein Static Shot mit komplexer Handlung (drei Personen reden, gestikulieren, stehen auf) funktioniert oft besser als ein Tracking Shot mit derselben Handlung.

> **Volksbank-Analogie:** Ein Static Shot ist wie die Überwachungskamera in Ihrer Filiale — neutral, beobachtend, dokumentierend. Klingt langweilig? Manche der besten Filmszenen aller Zeiten sind statisch gefilmt. Die Kraft liegt in dem, was *vor* der Kamera passiert.

---

#### 8. Handheld (Handkamera)

Leichtes, organisches Wackeln. Die Kamera ist „in der Hand" statt auf dem Stativ.

**Wirkung:** Authentizität, Nähe, Reportage-Charakter. Fühlt sich „echt" an.

**Wann einsetzen:**
- Behind-the-Scenes-Content
- Authentische Recruiting-Videos
- „Wir sind mittendrin"-Gefühl

```
Prompt-Beispiel (Handheld):

Handheld camera follows a team through a busy office during
a product launch. People high-five, someone carries coffee,
screens show dashboards. Slightly shaky, authentic feel.
Natural fluorescent lighting with warm accents. Energetic,
documentary, real. No color grading — raw look.
```

**Varianten:**
- `handheld, subtle shake` — leichtes Wackeln, professionell
- `shaky cam` — stärkeres Wackeln, Action, Chaos
- `steadicam` — flüssig wie Dolly, aber freier in der Bewegung (Kompromiss zwischen Handheld und Stativ)

```
Prompt-Beispiel (Steadicam):

Steadicam glides through the corridors of a bank headquarters.
The camera passes meeting rooms with glass walls, a coffee
area, and arrives at an open workspace. Smooth, continuous
movement. Morning light. Modern, inviting corporate atmosphere.
```

---

## Shot-Typen: Wie nah ist die Kamera?

Neben der *Bewegung* der Kamera ist die *Entfernung* zum Subjekt entscheidend. Filmemacher nennen das den „Shot-Typ" oder die „Einstellungsgröße".

### Übersicht: Shot-Typen

```
┌──────────────────────────────────────────────────────────────┐
│                    SHOT-TYPEN IM ÜBERBLICK                    │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  EXTREME WIDE SHOT (EWS)          [............●..........]  │
│  Totale Übersicht. Person winzig.  Establishing, Landschaft  │
│                                                              │
│  WIDE SHOT (WS)                   [.......●●●●●..........]  │
│  Ganze Person + Umgebung.          Kontext, Architektur      │
│                                                              │
│  MEDIUM WIDE / COWBOY SHOT        [.....●●●●●●●●..........]  │
│  Person ab Oberschenkel.           Ganghaltung, Auftreten    │
│                                                              │
│  MEDIUM SHOT (MS)                 [....●●●●●●●●●●..........]│
│  Person ab Hüfte.                  Standard für Dialoge      │
│                                                              │
│  MEDIUM CLOSE-UP (MCU)            [...●●●●●●●●●●●●.......] │
│  Person ab Brust.                  Emotion + Kontext         │
│                                                              │
│  CLOSE-UP (CU)                    [..●●●●●●●●●●●●●●..]     │
│  Nur Gesicht.                      Emotion, Intimität        │
│                                                              │
│  EXTREME CLOSE-UP (ECU)           [●●●●●●●●●●●●●●●●●●]     │
│  Detail: Auge, Hand, Objekt.       Spannung, Fokus           │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### Shot-Typen im Prompt

| Shot-Typ | Prompt-Begriffe | Wirkung | Typischer Einsatz |
|----------|----------------|---------|-------------------|
| **Extreme Wide** | `extreme wide shot`, `establishing shot`, `aerial wide` | Kontext, Orientierung | Eröffnung, Standort zeigen |
| **Wide Shot** | `wide shot`, `full shot`, `long shot` | Übersicht, Architektur | Gebäude, Raum, Gruppe |
| **Medium Wide** | `medium wide shot`, `cowboy shot`, `3/4 shot` | Körpersprache, Auftritt | Person in Umgebung |
| **Medium Shot** | `medium shot`, `waist shot`, `mid shot` | Standard-Dialog, Interview | Beratungsgespräch |
| **Medium Close-up** | `medium close-up`, `chest shot` | Emotion + Kontext | Präsentation, Gespräch |
| **Close-up** | `close-up`, `face shot` | Emotion, Intimität | Reaktion, Empathie |
| **Extreme Close-up** | `extreme close-up`, `macro`, `detail shot` | Spannung, Fokus | Hand am Produkt, Bildschirm |

### Kamerawinkel: Von wo schauen wir?

Neben der Entfernung zählt der **Winkel**, aus dem die Kamera blickt:

| Winkel | Prompt-Begriffe | Wirkung |
|--------|----------------|---------|
| **Augenhöhe** | `eye level`, `neutral angle` | Gleichwertig, natürlich |
| **Leicht von unten** | `low angle`, `slight low angle` | Macht, Autorität, Stärke |
| **Leicht von oben** | `high angle`, `slight high angle` | Verletzlichkeit, Unterlegenheit |
| **Froschperspektive** | `worm's-eye view`, `extreme low angle` | Dramatik, Überwältigung |
| **Vogelperspektive** | `bird's-eye view`, `top-down`, `overhead` | Überblick, Muster, Abstraktion |
| **Über-die-Schulter** | `over-the-shoulder`, `OTS` | Dialog, Perspektive eines Teilnehmers |
| **POV** | `first-person view`, `POV shot`, `subjective camera` | Immersion, „Ich bin dabei" |

```
Prompt-Beispiel (Low Angle + Close-up):

Low angle close-up of a confident businesswoman giving a
keynote speech. She looks slightly past the camera toward the
audience. Dramatic stage lighting from above creates sharp
shadows. Bokeh lights in the dark background. Powerful,
inspiring mood.
```

```
Prompt-Beispiel (Over-the-shoulder):

Over-the-shoulder shot from behind a bank consultant. We see
the customer's face across the desk, smiling and nodding.
A tablet between them shows financial charts. Shallow depth
of field — the consultant's shoulder blurred in the foreground.
Warm, professional lighting.
```

```
Prompt-Beispiel (POV):

First-person POV: Walking into a modern bank branch. Glass
doors open automatically. The reception area is bright and
welcoming. A consultant waves from behind the counter.
Camera height: eye level, slight handheld wobble. Natural
daylight, modern architecture. Inviting atmosphere.
```

> **Volksbank-Analogie:** Shot-Typen sind wie die verschiedenen Perspektiven in einem Kundengespräch. Der Wide Shot ist der Überblick: „Die Filiale sieht modern aus." Der Medium Shot ist das Gespräch am Tisch. Der Close-up ist der Moment, in dem der Kunde sagt: „Ja, das mache ich." Und der Extreme Close-up ist die Unterschrift auf dem Vertrag.

---

## Bewegungsphysik und Timing

### Geschwindigkeit beschreiben

Die Geschwindigkeit der Kamerabewegung verändert die Stimmung komplett:

| Tempo | Prompt-Begriffe | Wirkung | Einsatz |
|-------|----------------|---------|---------|
| **Sehr langsam** | `very slow`, `glacial`, `barely perceptible` | Meditation, Ehrfurcht, Schwere | Imagefilm, emotional |
| **Langsam** | `slow`, `gentle`, `gradual` | Ruhe, Eleganz, Professionalität | Corporate, Architektur |
| **Normal** | `steady`, `smooth`, `even` | Neutral, dokumentarisch | Standard-Content |
| **Schnell** | `fast`, `dynamic`, `energetic` | Action, Energie, Aufregung | Recruiting, Social Media |
| **Sehr schnell** | `rapid`, `whip`, `snap` | Überraschung, Chaos, Energie | Teaser, Trailer, TikTok |

### Timing in Beats beschreiben

Der wichtigste Trick für kontrollierbare Video-Prompts: **Beschreiben Sie Aktionen in Beats** — kleine, zählbare Schritte.

```
❌ Schwach:
"A person walks across the room and sits down."

✅ Stark:
"The consultant takes three steps toward the window,
pauses for a beat, then turns to face the camera."
```

**Warum Beats funktionieren:** Wenn Sie sagen „nimmt drei Schritte", gibt das dem Modell einen **zeitlichen Anker**. Es weiß: drei Schritte ≈ 2–3 Sekunden. Dann Pause ≈ 1 Sekunde. Dann Drehung ≈ 1 Sekunde. Die Aktion füllt die Clip-Länge natürlich aus.

### Beat-Framework für verschiedene Clip-Längen

```
┌──────────────────────────────────────────────────────────┐
│              TIMING: BEATS PRO CLIP-LÄNGE                │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  4 Sekunden:                                             │
│  ┌─────────┐ ┌─────────┐                                │
│  │ Beat 1  │ │ Beat 2  │                                │
│  │ Aktion  │ │ Reaktion│                                │
│  │ ~2 Sek. │ │ ~2 Sek. │                                │
│  └─────────┘ └─────────┘                                │
│                                                          │
│  Beispiel: "She picks up the phone (2s) and smiles (2s)" │
│                                                          │
│  8 Sekunden:                                             │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐                    │
│  │ Beat 1  │ │ Beat 2  │ │ Beat 3  │                    │
│  │ Setup   │ │ Aktion  │ │ Resultat│                    │
│  │ ~3 Sek. │ │ ~3 Sek. │ │ ~2 Sek. │                    │
│  └─────────┘ └─────────┘ └─────────┘                    │
│                                                          │
│  Beispiel: "He enters the room (3s), walks to the desk   │
│  and opens a folder (3s), then nods approvingly (2s)"    │
│                                                          │
│  12 Sekunden:                                            │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐            │
│  │ Beat 1 │ │ Beat 2 │ │ Beat 3 │ │ Beat 4 │            │
│  │ Intro  │ │Aufbau  │ │ Höhepkt│ │ Ende   │            │
│  │ ~3 Sek.│ │ ~3 Sek.│ │ ~3 Sek.│ │ ~3 Sek.│            │
│  └────────┘ └────────┘ └────────┘ └────────┘            │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Zeitangaben im Prompt

Manche Modelle verstehen direkte Zeitangaben:

```
Prompt mit Zeitangaben (Sora 2):

0.00–3.00: Wide shot of an empty bank lobby at dawn. Camera
is static. Soft blue morning light fills the space.

3.00–6.00: A woman enters through the glass door. Camera
begins a slow dolly-in as she walks toward the reception.

6.00–8.00: Medium close-up of her face. She smiles warmly.
The morning light catches her eyes.
```

**Modell-Kompatibilität für Zeitangaben:**

| Modell | Versteht Zeitangaben? | Empfehlung |
|--------|---------------------|------------|
| **Sora 2** | ✅ Gut | Zeitangaben funktionieren zuverlässig |
| **Veo 3.1** | ⚠️ Teilweise | Beats besser als Sekunden |
| **Runway Gen-4.5** | ⚠️ Teilweise | Keyframes nutzen statt Zeitangaben |
| **Kling 2.6** | ❌ Kaum | Reihenfolge der Beschreibung = Reihenfolge im Video |
| **Luma Ray3** | ⚠️ Teilweise | Beats funktionieren |
| **Pika 2.5** | ❌ Kaum | Kurz und einfach halten |

> **Volksbank-Analogie:** Timing in Beats ist wie ein gut strukturiertes Beratungsgespräch: Begrüßung (Beat 1), Bedarfsanalyse (Beat 2), Produktvorstellung (Beat 3), Abschluss (Beat 4). Jeder Schritt hat seinen Rhythmus — und wenn Sie den kennen, läuft das Gespräch wie ein guter Film.

---

## Modellspezifische Stärken bei Kamera und Bewegung

Nicht jedes Modell versteht Kameraanweisungen gleich gut. Hier die ehrliche Einschätzung:

### Kamera-Verständnis nach Modell

```
┌─────────────────────────────────────────────────────────────────┐
│           KAMERA-VERSTÄNDNIS DER MODELLE (FEB 2026)             │
├──────────────┬──────────┬──────────┬──────────┬────────────────┤
│ Bewegung     │ Veo 3.1  │ Sora 2   │ Runway   │ Kling 2.6     │
│              │          │          │ Gen-4.5  │               │
├──────────────┼──────────┼──────────┼──────────┼────────────────┤
│ Pan          │ ✅ Sehr  │ ✅ Sehr  │ ✅ Sehr  │ ✅ Gut        │
│              │    gut   │    gut   │    gut   │               │
│ Tilt         │ ✅ Gut   │ ✅ Gut   │ ✅ Gut   │ ⚠️ OK        │
│ Dolly        │ ✅ Sehr  │ ✅ Sehr  │ ✅ Sehr  │ ✅ Gut        │
│              │    gut   │    gut   │    gut   │               │
│ Tracking     │ ✅ Gut   │ ✅ Gut   │ ✅ Sehr  │ ⚠️ OK        │
│              │          │          │    gut   │               │
│ Drone/Aerial │ ✅ Gut   │ ✅ Gut   │ ✅ Gut   │ ✅ Gut        │
│ Zoom         │ ✅ Gut   │ ⚠️ OK   │ ✅ Gut   │ ⚠️ OK        │
│ Dolly Zoom   │ ⚠️ OK   │ ⚠️ OK   │ ❌       │ ❌            │
│ Static       │ ✅ Sehr  │ ✅ Sehr  │ ✅ Sehr  │ ✅ Sehr gut   │
│              │    gut   │    gut   │    gut   │               │
│ Handheld     │ ✅ Gut   │ ✅ Gut   │ ⚠️ OK   │ ⚠️ OK        │
│ Orbit/Arc    │ ✅ Gut   │ ⚠️ OK   │ ✅ Gut   │ ⚠️ Inkonsist. │
├──────────────┼──────────┼──────────┼──────────┼────────────────┤
│ Luma Ray3    │ Pika 2.5 │ Wan 2.2  │ LTX-2   │               │
├──────────────┼──────────┼──────────┼──────────┤               │
│ Pan          │ ✅ Gut   │ ⚠️ OK   │ ⚠️ OK   │               │
│ Tilt         │ ⚠️ OK   │ ⚠️ OK   │ ⚠️ OK   │               │
│ Dolly        │ ✅ Gut   │ ⚠️ OK   │ ⚠️ OK   │               │
│ Tracking     │ ⚠️ OK   │ ❌       │ ⚠️ OK   │               │
│ Drone/Aerial │ ✅ Gut   │ ⚠️ OK   │ ⚠️ OK   │               │
│ Physik       │ ✅ Beste │ ⚠️ OK   │ ⚠️ OK   │               │
└──────────────┴──────────┴──────────┴──────────┘               │
                                                                 │
  Legende: ✅ Sehr gut = folgt Anweisung zuverlässig             │
           ✅ Gut = folgt meistens, gelegentlich Abweichung      │
           ⚠️ OK = versteht den Begriff, Umsetzung variiert     │
           ❌ = Anweisung wird oft ignoriert oder falsch umgesetzt│
└─────────────────────────────────────────────────────────────────┘
```

### Empfehlungen pro Modell

**Veo 3.1 — Der Allrounder:**
- Versteht die meisten Kameraanweisungen zuverlässig
- Tipp: Verwenden Sie das **4-Bausteine-Format** (Subjekt, Kontext, Aktion, Stil) und platzieren Sie Kameraanweisungen am Anfang oder Ende des Prompts
- Bonus: Akzeptiert professionelle Filmterminologie (z.B. „35mm lens, shallow DOF, rack focus")

**Sora 2 — Der Narrative:**
- Zeitangaben im Prompt funktionieren gut (0.00–3.00, 3.00–6.00)
- Versteht komplexe Shot-Listen mit mehreren Einstellungen
- Tipp: Das OpenAI-Format funktioniert besonders gut:
```
[Prose scene description]
Cinematography:
Camera shot: [framing and angle]
Mood: [tone]
Actions:
- [Beat 1]
- [Beat 2]
```

**Runway Gen-4.5 — Der Technische:**
- Beste Unterstützung für professionelle Kamerasprache
- Keyframe-basiertes Arbeiten möglich
- Tipp: Verwenden Sie filmtechnische Begriffe wie in einem Produktions-Briefing

**Kling 2.6 — Der Pragmatiker:**
- Einfache Kameraanweisungen gut, komplexe Bewegungen weniger zuverlässig
- Tipp: Halten Sie Kamerabeschreibungen kurz (max. 1 Satz). Fokus auf Aktion statt auf Kameratechnik.

**Luma Ray3 — Der Physiker:**
- Beste Bewegungsphysik (Objekte, Flüssigkeiten, Partikel)
- Kameraanweisungen solide, aber nicht die Stärke
- Tipp: Beschreiben Sie die **physikalische Bewegung** detailliert, die Kamera einfach

---

## Vom Schwachen zum Starken Prompt: Vorher/Nachher

### Beispiel 1: Recruiting-Video

```
❌ Schwacher Prompt:
"A video of a bank office with people working. Make it look professional."

✅ Starker Prompt:
Steadicam tracking shot through a modern open-plan bank office.
Camera follows a young professional from behind as she walks past
glass-walled meeting rooms. She pauses at a standing desk, picks
up a coffee, and turns to smile at a colleague. Warm morning
sunlight from floor-to-ceiling windows. Shallow depth of field.
Corporate documentary style, natural color grading.
Duration: 8 seconds.
```

**Was den Unterschied macht:**
| Element | Schwach | Stark |
|---------|---------|-------|
| Kamerabewegung | nicht angegeben | Steadicam tracking from behind |
| Shot-Typ | nicht angegeben | implizit Medium Wide (following) |
| Aktion | „people working" | 3 Beats: walks, pauses, turns |
| Licht | nicht angegeben | warm morning sunlight |
| Tiefenschärfe | nicht angegeben | shallow depth of field |
| Dauer | nicht angegeben | 8 seconds |

### Beispiel 2: Produktvideo Banking-App

```
❌ Schwacher Prompt:
"Show a banking app on a phone. Cinematic."

✅ Starker Prompt:
Extreme close-up of a smartphone screen showing a banking app
dashboard. A thumb swipes through different tabs — account
balance, transfers, investment portfolio. Camera: static,
macro lens, shallow depth of field. The phone rests on a
clean white desk with soft side lighting. Each swipe reveals
colorful charts and numbers. Smooth finger movement, 3 swipes
in 8 seconds. Modern, clean aesthetic.
```

### Beispiel 3: Emotionaler Imagefilm

```
❌ Schwacher Prompt:
"An emotional scene in a bank. A customer is happy."

✅ Starker Prompt:
Medium close-up, eye level. A 60-year-old man sits across from
a bank consultant in a quiet meeting room. The consultant slides
a document across the table. The man reads it, looks up, and his
eyes fill with tears of relief. He reaches across and shakes the
consultant's hand firmly. Camera: static, intimate framing.
Soft, warm window light. Piano note fades in. The moment speaks
for itself. 8 seconds.
```

> **Volksbank-Analogie:** Der Unterschied zwischen einem schwachen und einem starken Prompt ist wie der Unterschied zwischen „Machen Sie mal was Nettes für unsere Webseite" und einem detaillierten Kreativ-Briefing an die Agentur. Beides kann funktionieren — aber nur bei einem wissen Sie, was Sie bekommen.

---

## Das Ultra-Detail-Format für maximale Kontrolle

Für komplexe, hochwertige Shots gibt es ein Format, das dem professionellen Film-Briefing nahekommt. Nicht nötig für Social-Media-Reels — aber wenn Sie einen Clip brauchen, der wie ein Kinotrailer aussieht:

### Struktur des Ultra-Detail-Formats

```
┌──────────────────────────────────────────────────────────┐
│           ULTRA-DETAIL-FORMAT (FÜR PROFI-SHOTS)          │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  FORMAT & LOOK                                           │
│  Dauer, Shutter, Filmstock-Emulation, Grain, Halation    │
│                                                          │
│  LINSEN & FILTER                                         │
│  Brennweite, Blende, Filtration (Pro-Mist, CPL)          │
│                                                          │
│  GRADE / PALETTE                                         │
│  Highlights, Mitteltöne, Schatten — jeweils Farbton      │
│                                                          │
│  LICHT & ATMOSPHÄRE                                      │
│  Hauptlicht, Fülllicht, Gegenlicht, Practicals, Atmo     │
│                                                          │
│  LOCATION & FRAMING                                      │
│  Vordergrund, Mittelgrund, Hintergrund                   │
│                                                          │
│  WARDROBE / PROPS / EXTRAS                               │
│  Hauptperson-Detail, Statistenkleidung, Requisiten       │
│                                                          │
│  SOUND                                                   │
│  Diegetisch, Ambience, Lautstärke, kein Score            │
│                                                          │
│  SHOT LIST (optimiert)                                   │
│  Shot 1: Zeitraum — Kamera — Beschreibung — Zweck        │
│  Shot 2: Zeitraum — Kamera — Beschreibung — Zweck        │
│                                                          │
│  KAMERA-NOTIZEN                                          │
│  Warum die Shots funktionieren                           │
│                                                          │
│  FINISHING                                               │
│  Grain, LUT, Mix-Prioritäten, Poster-Frame              │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### Beispiel: Ultra-Detail für einen Volksbank-Imagefilm

```
FORMAT & LOOK
Duration: 8s. Digital capture emulating 35mm photochemical warmth.
Fine grain. Subtle halation on window highlights. No gate weave.

LENSES & FILTRATION
40mm spherical prime. Shallow DOF (f/2.0). Black Pro-Mist 1/8
for gentle glow on skin highlights.

GRADE / PALETTE
Highlights: clean morning sunlight with amber lift.
Mids: balanced warm neutrals.
Blacks: soft, lifted — inviting, not heavy.
Anchors: honey, cream, walnut, sage green, steel blue.

LIGHTING & ATMOSPHERE
Natural sunlight from camera-right, low morning angle.
Bounce: soft silver fill from left. Practical: desk lamp
warm glow. Atmosphere: light haze from coffee steam.

LOCATION & FRAMING
Modern bank consultation room. Foreground: blurred plant leaf.
Midground: consultant and customer at desk, diagonal composition.
Background: city skyline through floor-to-ceiling window, soft focus.

WARDROBE / PROPS
Consultant: mid-30s woman, navy blazer, white blouse, minimal
jewelry. Customer: 50s man, casual smart, reading glasses
on the table. Props: tablet, coffee cups, printed document.

SOUND
Diegetic: soft paper rustle, distant phone, muffled office hum.
No score. Ambient: morning bird chirps from cracked window.

SHOT (single continuous take, 8s)
0.00–4.00 — "The Approach" (40mm, slow dolly-in from medium wide)
Camera drifts toward the desk. Consultant gestures at tablet.
Customer leans in, engaged. Morning light blooms across the table.

4.00–8.00 — "The Connection" (40mm, settle into medium close-up)
Consultant points at a chart, customer nods with a warm smile.
She looks up — brief eye contact with camera, barely perceptible.
Sunlight catches her face. Moment of trust.

CAMERA NOTES
Keep transitions imperceptible — the dolly-in should feel like
a held breath, not a camera move. Let the actors carry the scene.

FINISHING
Fine grain overlay. Warm-cool morning LUT. Mix: prioritize
paper and ambient over dialogue. Poster frame: the moment
of eye contact, golden rim light, city skyline soft behind.
```

**Wann lohnt sich dieses Format?**
- Hauptfilm für Hauptversammlung oder Jahresbericht
- Kampagnenvideo mit hohem Qualitätsanspruch
- Wenn Sie exakte Kontrolle über Look & Feel brauchen
- In Kombination mit Veo 3.1 oder Sora 2 (verstehen dieses Format am besten)

**Wann ist es Overkill?**
- Social-Media-Reels (5–15 Sekunden, schnell produziert)
- Interne Kommunikation
- Prototypen und Konzeptvideos
- Kling, Pika, Luma — profitieren weniger von Ultra-Details

> **Volksbank-Analogie:** Das Ultra-Detail-Format ist wie ein 20-seitiges Beratungsprotokoll für die Großkundenbetreuung. Für den Firmenkunden mit Millionendepot genau richtig — für die Kontoeröffnung eines Studenten eine Nummer zu groß.

---

## Professionelle Filmsprache: Cheat Sheet

Hier die wichtigsten filmtechnischen Begriffe, die KI-Modelle verstehen — zum Nachschlagen:

### Kamerabewegungen

| Begriff | Bedeutung | Prompt-Formulierung |
|---------|-----------|-------------------|
| **Pan** | Horizontaler Schwenk | `camera pans left to right` |
| **Tilt** | Vertikaler Schwenk | `camera tilts up slowly` |
| **Dolly** | Kamera fährt vor/zurück | `slow dolly-in toward subject` |
| **Truck** | Kamera fährt seitlich | `camera trucks right` |
| **Pedestal** | Kamera hebt/senkt sich vertikal | `camera rises smoothly` |
| **Crane** | Kran-Bewegung (hoch + vor/zurück) | `crane shot ascending` |
| **Steadicam** | Stabilisierte Handkamera | `steadicam follows subject` |
| **Jib** | Kurze Kran-Bewegung | `jib up and over the desk` |

### Linsen und Optik

| Begriff | Bedeutung | Prompt-Formulierung |
|---------|-----------|-------------------|
| **Wide angle** | Weitwinkel (< 35mm) | `24mm wide angle lens` |
| **Normal** | Normalobjektiv (35–50mm) | `50mm lens, natural perspective` |
| **Telephoto** | Tele (> 85mm) | `85mm telephoto, compressed background` |
| **Anamorphic** | Breitbild-Linse, ovales Bokeh | `anamorphic 2.0x lens, oval bokeh` |
| **Shallow DOF** | Geringe Tiefenschärfe | `shallow depth of field, blurred background` |
| **Deep focus** | Alles scharf | `deep focus, everything in sharp detail` |
| **Rack focus** | Schärfeverlagerung | `rack focus from foreground to background` |

### Licht-Typen

| Begriff | Bedeutung | Prompt-Formulierung |
|---------|-----------|-------------------|
| **Key light** | Hauptlicht | `strong key light from camera left` |
| **Fill light** | Aufhellung der Schatten | `soft fill from right side` |
| **Rim/Back light** | Gegenlicht, Konturenlicht | `warm rim light separating subject from background` |
| **Practical** | Sichtbare Lichtquelle im Bild | `desk lamp as practical light source` |
| **Ambient** | Umgebungslicht | `soft ambient office lighting` |
| **Golden hour** | Letzte Stunde vor Sonnenuntergang | `golden hour sunlight, long shadows` |
| **High key** | Hell, wenig Schatten | `high-key lighting, bright and clean` |
| **Low key** | Dunkel, starke Schatten | `low-key lighting, dramatic shadows` |
| **Chiaroscuro** | Extremer Licht-Schatten-Kontrast | `chiaroscuro lighting, Rembrandt style` |

---

## Kombinationsrezepte: Kamera + Shot + Bewegung

Hier fertige Kombinationen für typische Banken-Szenarien:

### Rezept 1: Der Filial-Rundgang (Recruiting/Imagefilm)

```
Steadicam, medium wide shot, eye level.
Camera follows subject from behind through the building.
Smooth, continuous movement. Bright, modern architecture.

Prompt:
Steadicam medium wide shot follows a young professional from
behind as she walks through a modern bank branch. She passes
the open reception, a consultation area with glass partitions,
and arrives at an open workspace. Colleagues greet her along
the way. Natural daylight, warm tones. 12 seconds.
```

### Rezept 2: Das Beratungsgespräch (Corporate/Erklärvideo)

```
Static camera, medium shot, eye level.
Two people at a desk. Focus on dialogue and interaction.

Prompt:
Static medium shot, eye level. A bank consultant and customer
sit across a modern desk. The consultant explains something
on a tablet, pointing at the screen. The customer nods and
asks a question. Soft window light from the left. Professional,
warm atmosphere. 8 seconds.
```

### Rezept 3: Das Produktvideo (App/Service)

```
Static or slow dolly-in, extreme close-up to close-up.
Focus on the product (screen, device, document).

Prompt:
Slow dolly-in from medium shot to extreme close-up of a
smartphone screen. A hand navigates a banking app — swiping
through accounts, tapping a transfer button. Clean white desk,
soft side lighting. Macro lens, shallow depth of field. Each
interaction smooth and deliberate. 8 seconds.
```

### Rezept 4: Der Establishing Shot (Imagefilm/Event)

```
Drone ascending or dolly out, extreme wide shot.
Show the building, the location, the context.

Prompt:
Aerial drone shot ascending slowly from street level. A modern
glass bank headquarters is revealed against a blue sky with
scattered clouds. Green parks surround the building. Cars and
pedestrians move below. Golden morning light. Cinematic,
establishing shot. 8 seconds.
```

### Rezept 5: Der Emotionale Moment (Storytelling/Kampagne)

```
Slow dolly-in, close-up, eye level.
Focus on face, emotion, minimal action.

Prompt:
Slow dolly-in to close-up, eye level. A retired couple sits
in a bank office. The consultant slides a document across the
table. The woman reads it, looks at her husband, and smiles
with relief. He squeezes her hand. Soft afternoon light.
Warm tones. Piano note rises gently. 8 seconds.
```

### Rezept 6: Der Social-Media-Hook (Reel/Short)

```
Dynamic handheld or whip pan, close-up or medium shot.
Fast, energetic, attention-grabbing in the first 2 seconds.

Prompt:
Dynamic handheld close-up. A hand slams a laptop shut with
a confident gesture. Quick whip pan to the person's face —
they smile directly into the camera. Text overlay space.
Bright, energetic lighting. Modern office background blurred.
Fast-paced, 4 seconds.
```

### Rezept 7: Der Pixar-Stil (Storytelling/Prävention)

```
Smooth dolly or static, medium shot.
Animated character in a stylized environment.

Prompt:
Pixar-style 3D animation. A small, cheerful piggy bank character
with big eyes sits on a desk. It watches as coins drop in from
above — each coin makes it smile wider. After the third coin,
it does a little happy dance. Warm, colorful lighting. Playful
orchestral music. The character says: "Every little bit counts!"
8 seconds.
```

> **Volksbank-Analogie:** Diese Rezepte sind wie Ihre Beratungsleitfäden — bewährte Gesprächsstrukturen für verschiedene Kundentypen. Sie müssen nicht jedes Mal das Rad neu erfinden. Nehmen Sie das passende Rezept, passen Sie die Details an, und der Rest ergibt sich.

---

## Häufige Fehler und wie Sie sie vermeiden

### Die Top 7 Kamera-Fehler in Video-Prompts

| # | Fehler | Problem | Lösung |
|---|--------|---------|--------|
| 1 | **Zu viele Bewegungen** | Kamera springt, Physik bricht | Max. 1 Kamerabewegung pro Shot |
| 2 | **Keine Kameraangabe** | KI wählt zufällig, oft unruhig | Immer mindestens Shot-Typ + Bewegung angeben |
| 3 | **Widersprüchliche Anweisungen** | „Static shot with smooth dolly" — was denn nun? | Einen Typ wählen und dabei bleiben |
| 4 | **Zu schnelle Aktionen** | Bewegungen wirken gehetzt, unrealistisch | Weniger Aktion = mehr Qualität |
| 5 | **Kein Licht beschrieben** | KI wählt zufällige, oft flache Beleuchtung | Mindestens Lichtrichtung + Qualität angeben |
| 6 | **Deutsche Kamerabegriffe** | Modelle verstehen „Schwenk" schlechter als „pan" | Kameraanweisungen auf Englisch |
| 7 | **Zoom und Dolly verwechselt** | Falscher visueller Effekt | Zoom = Optik ändert sich. Dolly = Kamera bewegt sich |

### Der 5-Punkte-Selbst-Check

Bevor Sie einen Video-Prompt absenden, prüfen Sie:

```
□ 1. Habe ich NUR EINE Kamerabewegung?
□ 2. Habe ich den Shot-Typ genannt? (wide, medium, close-up)
□ 3. Habe ich die Aktion in Beats beschrieben? (nicht als Ablauf)
□ 4. Sind Kameraanweisungen auf Englisch?
□ 5. Passt die Menge der Aktion zur Clip-Länge?
```

---

## Hands-on Übung 1: Kamerabewegung vergleichen

**Aufgabe:** Generieren Sie dieselbe Szene mit drei verschiedenen Kamerabewegungen und beobachten Sie, wie sich die Wirkung verändert.

**Basis-Szene:**
Eine Person betritt eine moderne Bankfiliale und geht zum Empfang.

**Prompt A — Static:**
```
Static wide shot, eye level. A young man enters a modern bank
branch through glass doors. He walks toward the reception desk.
Natural morning light. Clean, corporate atmosphere. 8 seconds.
```

**Prompt B — Tracking:**
```
Steadicam tracking shot, medium wide, following from behind.
A young man walks through a modern bank branch toward the
reception desk. We see the space unfold as he moves. Natural
morning light. Clean, corporate atmosphere. 8 seconds.
```

**Prompt C — Drone:**
```
High angle drone shot, slowly descending. A young man enters
a modern bank branch through glass doors below. The camera
descends to reveal the full lobby layout. Natural morning
light through a glass ceiling. 8 seconds.
```

**Beobachten Sie:**
1. Welche Version fühlt sich am „professionellsten" an?
2. Welche erzeugt die meiste Energie/Dynamik?
3. Welche zeigt die Architektur am besten?
4. Welche hat die wenigsten visuellen Fehler?
5. Bei welcher fühlen Sie sich als Zuschauer am meisten „dabei"?

---

## Hands-on Übung 2: Shot-Typen für Emotionen

**Aufgabe:** Erzählen Sie denselben Moment in drei verschiedenen Shot-Typen.

**Moment:** Ein Kunde erhält eine gute Nachricht von seinem Berater.

**Prompt A — Wide Shot:**
```
Wide shot, eye level. In a modern bank meeting room, a consultant
slides a document across the table. The customer reads it and
breaks into a relieved smile. We see both people, the room,
and the city view behind them. Warm afternoon light. 8 seconds.
```

**Prompt B — Medium Close-up:**
```
Medium close-up, eye level. A customer's face as he reads a
document handed to him by a consultant (partially visible).
His expression shifts from concentration to relief to joy.
Soft, warm side lighting. Blurred office background. 8 seconds.
```

**Prompt C — Extreme Close-up:**
```
Extreme close-up of a customer's eyes. We see them scanning
a document, then widening slightly. A subtle smile forms at
the corners — reflected in the way the eyes soften. Macro lens,
very shallow depth of field. Warm golden light. 4 seconds.
```

**Vergleichen Sie:** Welcher Shot erzählt die „größte" Geschichte? Welcher die „intimste"?

---

## Hands-on Übung 3: Von der Idee zum Multi-Shot-Storyboard

**Aufgabe:** Erstellen Sie ein 3-Shot-Storyboard für ein 24-Sekunden-Recruiting-Video.

**Szenario:** „Ein Tag bei unserer Bank" — drei Szenen, drei Stimmungen.

**Shot 1 — Establishing (8 Sek.):**
```
[Ihr Prompt hier — Drohnenaufnahme des Gebäudes, Morgen]
```

**Shot 2 — Aktion (8 Sek.):**
```
[Ihr Prompt hier — Tracking Shot durch das Büro, Energie]
```

**Shot 3 — Emotion (8 Sek.):**
```
[Ihr Prompt hier — Close-up eines Teammoments, Wärme]
```

**Tipp:** Halten Sie die visuelle Sprache konsistent — gleicher Farbton (warm), ähnliche Lichtstimmung (Tageslicht), einheitlicher Stil (corporate documentary). Generieren Sie jeden Shot einzeln und schneiden Sie sie in einem Videoeditor (CapCut, Canva, Premiere) zusammen.

---

## Zusammenfassung

| Was Sie gelernt haben | Kernaussage |
|-----------------------|-------------|
| **Die goldene Regel** | Ein Shot = eine Kamerabewegung = eine Hauptaktion |
| **8 Kamerabewegungen** | Pan, Tilt, Dolly, Tracking, Drone, Zoom, Static, Handheld — jede mit eigener emotionaler Wirkung |
| **7 Shot-Typen** | Extreme Wide bis Extreme Close-up — die Entfernung bestimmt die Intimität |
| **Kamerawinkel** | Eye Level (neutral), Low Angle (Macht), High Angle (Verletzlichkeit), OTS (Dialog) |
| **Timing in Beats** | Aktionen in zählbare Schritte aufteilen statt vage Abläufe beschreiben |
| **Modellspezifische Stärken** | Veo 3.1 + Sora 2 verstehen komplexe Kamerasprache. Kling/Pika: einfach halten |
| **Ultra-Detail-Format** | Für Profi-Shots: Linse, Grade, Licht, Sound, Shot-Liste — wie ein echtes Briefing |
| **Kombinationsrezepte** | 7 fertige Kamera-Setups für typische Banken-Szenarien |
| **Schwach vs. Stark** | Der Unterschied: Kamerabewegung + Shot-Typ + Licht + Beats = professionell |

### Die drei wichtigsten Erkenntnisse

1. **Kamera ist Emotion.** Ein Dolly-in fühlt sich anders an als ein Static Shot — auch wenn die Szene identisch ist. Wählen Sie die Bewegung nach der gewünschten Wirkung.

2. **Weniger ist mehr.** Eine saubere Kamerabewegung in 8 Sekunden schlägt drei hastige Bewegungen. Simplizität ist kein Kompromiss — sie ist ein Stilmittel.

3. **Beats sind Ihr bester Freund.** „Drei Schritte, Pause, Drehung" gibt dem Modell einen zeitlichen Rahmen. „Geht durch den Raum" gibt ihm nichts.

---

## Ausblick

Im nächsten Tutorial geht es um den anderen Game-Changer: **Audio**. Tutorial 04-03 „Das Tonstudio" zeigt Ihnen, wie Sie Dialoge, Soundeffekte, Musik und Voice-Over in Ihre Video-Prompts integrieren — und warum der Ton oft wichtiger ist als das Bild.

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Pan** | Horizontaler Schwenk der Kamera auf dem Stativ — links/rechts, ohne die Position zu verändern |
| **Tilt** | Vertikaler Schwenk der Kamera auf dem Stativ — nach oben oder unten neigen |
| **Dolly** | Physische Kamerafahrt vor oder zurück. Dolly-in = Annäherung, Dolly-out = Entfernung. Verändert die Perspektive (anders als Zoom) |
| **Dolly Zoom** | Kamera fährt zurück + Zoom rein (oder umgekehrt). Hintergrund verzerrt sich, Subjekt bleibt gleich groß. Auch „Vertigo-Effekt" genannt |
| **Tracking Shot** | Kamera begleitet ein Subjekt — seitlich, von hinten oder von vorne. Auf Schienen, Steadicam oder virtuell |
| **Orbit / Arc Shot** | Kamera umkreist das Subjekt auf einer Kreisbahn |
| **Crane Shot** | Kamera auf einem Kran — ermöglicht hohe vertikale Bewegungen kombiniert mit horizontaler Fahrt |
| **Steadicam** | Stabilisierungssystem für handgeführte Kamera — flüssige Bewegung wie auf Schienen, aber flexibler |
| **Handheld** | Kamera in der Hand des Kameramanns — leichtes natürliches Wackeln. Erzeugt Authentizität und Nähe |
| **Whip Pan** | Sehr schneller horizontaler Schwenk — erzeugt Bewegungsunschärfe. Für dynamische Übergänge |
| **Shot-Typ / Einstellungsgröße** | Wie nah die Kamera am Subjekt ist: von Extreme Wide (Totale) bis Extreme Close-up (Detail) |
| **Wide Shot (WS)** | Die gesamte Person ist im Bild, plus Umgebung. Auch „Long Shot" oder „Totale" |
| **Medium Shot (MS)** | Person ab Hüfte aufwärts. Standard für Dialoge und Interviews |
| **Close-up (CU)** | Nur das Gesicht. Zeigt Emotion und Intimität |
| **Extreme Close-up (ECU)** | Ein einzelnes Detail: Auge, Hand, Objekt. Maximale Spannung und Fokus |
| **Over-the-Shoulder (OTS)** | Kamera blickt über die Schulter einer Person auf die andere. Standard für Dialogszenen |
| **POV (Point of View)** | Kamera zeigt, was eine Figur sieht — der Zuschauer ist „die Person" |
| **Eye Level** | Kamera auf Augenhöhe des Subjekts. Neutrale, gleichwertige Perspektive |
| **Low Angle** | Kamera blickt von unten nach oben auf das Subjekt. Vermittelt Macht und Autorität |
| **High Angle** | Kamera blickt von oben auf das Subjekt herab. Vermittelt Verletzlichkeit oder Überblick |
| **Bird's-eye View** | Kamera direkt senkrecht über der Szene. Zeigt Muster und Geometrie |
| **Depth of Field (DOF)** | Bereich der Schärfe im Bild. Shallow DOF = nur Subjekt scharf, Hintergrund unscharf. Deep DOF = alles scharf |
| **Rack Focus** | Schärfeverlagerung während der Aufnahme — von einem Objekt zum anderen. Lenkt den Blick des Zuschauers |
| **Bokeh** | Ästhetische Qualität der Unschärfe im Hintergrund. Kreisförmig (sphärisch) oder oval (anamorphisch) |
| **Anamorphic** | Breitbild-Linsentyp mit charakteristischem ovalen Bokeh und horizontalen Lensflares. Kino-Look |
| **Key Light** | Hauptlichtquelle einer Szene. Bestimmt die grundlegende Lichtstimmung |
| **Rim Light / Back Light** | Licht von hinten, das eine leuchtende Kontur um das Subjekt erzeugt. Trennt es vom Hintergrund |
| **Practical Light** | Sichtbare Lichtquelle im Bild (Lampe, Kerze, Bildschirm) — dient als natürlicher Lichtgeber |
| **Golden Hour** | Die Stunde vor Sonnenuntergang (oder nach Sonnenaufgang). Warmes, weiches, goldenes Licht |
| **High Key** | Beleuchtungsstil mit viel Licht und wenig Schatten. Hell, freundlich, offen |
| **Low Key** | Beleuchtungsstil mit wenig Licht und starken Schatten. Dramatisch, geheimnisvoll |
| **Beat** | Ein einzelner Aktionsschritt oder Moment innerhalb einer Szene. Zeitlicher Baustein für die Choreografie |
| **Establishing Shot** | Eröffnungseinstellung, die den Ort und Kontext einer Szene zeigt — meist Extreme Wide oder Drone Shot |
| **Push-in** | Allgemeiner Begriff für eine langsame Annäherung an das Subjekt — kann Dolly oder Zoom sein |

---

