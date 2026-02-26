# Wie KI sich die Welt vorstellt

**Von der Vorhersage zum Verständnis — wie KI lernt, ganze Welten zu simulieren, und warum das alles verändert**

---

## Warum dieses Tutorial?

In den vorherigen Tutorials haben Sie gelernt, wie KI Text versteht (Tutorial 00-01), Bilder erzeugt (Tutorial 00-02), verschiedene Modalitäten verbindet (Tutorial 00-03), Videos generiert (Tutorial 00-04) und Audio erschafft (Tutorial 00-05). Jedes dieser Systeme ist beeindruckend — aber keines von ihnen **versteht die Welt wirklich**.

Ein Bildgenerator erzeugt ein schönes Foto, hat aber keine Ahnung, was passiert, wenn Sie einen Ball fallen lassen. Ein LLM schreibt überzeugend über Schwerkraft, hat aber nie erlebt, dass Dinge nach unten fallen. Ein Videogenerator produziert beeindruckende Clips, aber die Physik darin ist bestenfalls ungefähr richtig.

Schließen Sie die Augen und stellen Sie sich vor, durch Ihre Wohnung zu gehen. Ohne hinzusehen, wissen Sie: Der Flur führt zur Küche. Der Boden ist fest unter Ihren Füßen. Wenn Sie ein Glas fallen lassen, zersplittert es. Sie haben ein **mentales Modell**, wie die Welt funktioniert.

Genau das ist ein **World Model** — eine KI, die sich die Welt nicht nur anschaut, sondern **vorstellt**. Nicht ein einzelnes Bild. Nicht ein einzelnes Wort. Sondern: Was passiert **als Nächstes**? Und danach? Und danach? Und zwar so, dass die Regeln stimmen: Schwerkraft zieht nach unten, Wände sind fest, und aus Tag wird nicht zufällig Nacht.

2025 und 2026 hat dieses Feld explodiert. Yann LeCun, Turing-Preisträger und Ex-Meta, hat AMI Labs gegründet und 500 Millionen Euro eingesammelt, um World Models zur Grundlage der nächsten KI-Generation zu machen. Google DeepMind hat mit **Genie 3** das erste interaktive Echtzeit-Weltmodell vorgestellt. NVIDIA hat mit **Cosmos** eine ganze Plattform für physikalische KI gebaut. Das ist kein Nischenthema mehr — es ist das nächste große Ding.

**Was Sie nach diesem Tutorial wissen werden:**

- Was ein World Model ist und warum es mehr kann als Bilder, Text oder Video allein
- Warum bisherige KI-Systeme die physische Welt nicht wirklich verstehen
- Wie ein World Model intern funktioniert: Encoder, latenter Raum, Vorhersage, Decoder
- Was „aktionsbedingte Vorhersage" bedeutet und warum sie der Schlüssel ist
- Wie man ein World Model Schritt für Schritt aufbaut — von Datensammlung bis Planung
- Welche Modelle heute den Markt bestimmen — von Genie 3 über Cosmos bis AMI Labs
- Warum World Models die „große Vereinigung" aller bisherigen KI-Technologien darstellen
- Was das für Ihren Arbeitsalltag bedeutet — und wo die Grenzen liegen

---

## Ein kurzer Blick zurück: Wie KI lernte, sich Welten vorzustellen

| Jahr | Meilenstein | Was es konnte |
|------|------------|---------------|
| **1989** | **Schmidhuber: „Making the World Differentiable"** | Erste theoretische Grundlage: Ein neuronales Netz soll ein internes Modell der Welt lernen, um vorherzusagen, was als Nächstes passiert |
| **2015** | **DeepMind: Atari mit Deep RL** | KI lernt, Atari-Spiele zu spielen — aber durch Versuch und Irrtum, nicht durch Vorstellungskraft |
| **2018** | **Ha & Schmidhuber: „World Models"** | Der Durchbruch: KI lernt ein komprimiertes Modell ihrer Umgebung und kann darin **träumen** — d. h. Situationen simulieren, ohne sie real zu erleben |
| **2020** | **Dreamer v1** (Hafner et al.) | Erstes World Model, das in komplexen 3D-Umgebungen (DeepMind Control Suite) aus reiner Vorstellungskraft Strategien lernt |
| **2023 Jan** | **Dreamer v3** | Universelles World Model: Lernt Minecraft, Atari und Robotersteuerung mit denselben Einstellungen — ein Modell für alles |
| **2023 Dez** | **GameNGen** (Google) | Simuliert das Spiel DOOM in Echtzeit als neuronales Netz — kein Game-Engine-Code, nur gelernte Physik |
| **2024 Feb** | **Genie 1** (Google DeepMind) | Aus einem einzigen Bild wird eine spielbare 2D-Welt generiert — der erste „Bildschirm, in den man einsteigen kann" |
| **2024 Mai** | **DIAMOND** (NeurIPS Spotlight) | World Model auf Diffusion-Basis: Erzielt übermenschliche Scores in Atari — trainiert rein im Traum, ohne echtes Spiel |
| **2024 Dez** | **Genie 2** (Google DeepMind) | 3D-Welten aus einem Bild, mit konsistenter Physik und interaktiver Steuerung |
| **2025 Jan** | **NVIDIA Cosmos** | Open-Source-Plattform für World Foundation Models — fokussiert auf Robotik und autonomes Fahren. 2 Mio. Downloads |
| **2025 Aug** | **Genie 3** (Google DeepMind) | Erstes Echtzeit-Weltmodell: 24 fps, 720p, minutenlange konsistente 3D-Welten aus Text-Prompts |
| **2025 Okt** | **World Labs: Marble** (Fei-Fei Li) | Kommerzielles World Model: 3D-Umgebungen aus Text/Bild generieren, Preise ab kostenlos bis 95$/Monat |
| **2025 Dez** | **Runway GWM-1** | Erstes „General World Model" eines Videogenerator-Unternehmens — erkundbare Umgebungen für Robotik-Training |
| **2025 Dez** | **Yann LeCun gründet AMI Labs** | €500 Mio. Finanzierung bei €3 Mrd. Bewertung — die größte Wette auf World Models in der KI-Geschichte |
| **2026 Jan** | **V-JEPA 2** (Meta) | Visuelles World Model: 65–80% Erfolgsrate bei Roboter-Greifaufgaben mit minimalen Trainingsdaten |

**Das Muster:** Von theoretischen Träumereien (1989) über spielende KI-Agenten (2018–2024) zu interaktiven 3D-Welten in Echtzeit (2025–2026). World Models sind innerhalb von zwei Jahren vom Forschungslabor zum Milliarden-Dollar-Markt geworden.

> **Bank-Analogie:** Stellen Sie sich vor, ein neuer Azubi kommt in Ihre Filiale. Er könnte entweder a) jeden möglichen Kundenfall auswendig lernen (= LLM, Pattern Matching) oder b) ein **mentales Modell** der Bank aufbauen: Wie Konten funktionieren, warum Überweisungen Zeit brauchen, was passiert, wenn ein Kredit nicht bedient wird. Mit dem mentalen Modell kann er auch **neue** Situationen meistern, die in keinem Handbuch stehen. Genau das ist der Unterschied zwischen bisheriger KI und einem World Model.

---

## Die Analogie: Das Planetarium im Kopf

Stellen Sie sich vor, Sie haben ein **Planetarium im Kopf**. Nicht eines, das nur den Sternenhimmel zeigt — sondern eines, das eine komplette kleine Welt simuliert:

1. **Die Kamera** (Encoder) — Sie schauen auf die echte Welt und übersetzen das, was Sie sehen, in ein kompaktes inneres Bild. Nicht jedes Detail, sondern das Wesentliche: Wo sind die Objekte? Was bewegt sich? Was ist fest?

2. **Die Miniaturwelt** (Latenter Raum) — In Ihrem Kopf existiert eine vereinfachte Version der Welt. Nicht fotorealistisch, aber **funktional korrekt**: Schwerkraft stimmt, Objekte kollidieren, Türen führen in Räume.

3. **Die Kristallkugel** (Vorhersagemodell) — Sie können sich vorstellen, was passiert, wenn Sie etwas tun: „Wenn ich den Ball werfe, fliegt er in einem Bogen." Die Miniaturwelt spielt die Zukunft durch — **bevor** Sie handeln.

4. **Der Projektor** (Decoder) — Wenn nötig, können Sie Ihre innere Vorstellung in ein konkretes Bild oder Video übersetzen — das, was die KI dann tatsächlich ausgibt.

```
┌─────────────────────────────────────────────────────────────┐
│                    DAS PLANETARIUM IM KOPF                   │
│                                                              │
│  Echte Welt ──→ [📷 Kamera] ──→ ┌──────────────┐           │
│                   (Encoder)      │ Miniaturwelt │           │
│                                  │  (Latenter   │           │
│  Aktion: ────────────────────→   │    Raum)     │           │
│  "Ball werfen"                   │              │           │
│                                  │  🔮 Kristall-│           │
│                                  │     kugel    │           │
│                                  │  (Vorhersage)│           │
│                                  └──────┬───────┘           │
│                                         │                    │
│                                    [🎥 Projektor]            │
│                                      (Decoder)               │
│                                         │                    │
│                                         ▼                    │
│                                   Vorgestellte               │
│                                   Zukunft (Bild/Video)       │
└─────────────────────────────────────────────────────────────┘
```

Das Besondere: Die Kristallkugel berücksichtigt **Ihre Aktion**. Sie sagt nicht einfach „das passiert als Nächstes", sondern „**wenn** Sie das tun, **dann** passiert das". Das ist der entscheidende Unterschied zu einem Videogenerator, der einfach „weitererzählt".

> **Bank-Analogie:** Das ist wie der erfahrene Kreditberater, der im Kopf durchspielt: „Wenn wir den Zinssatz senken, bleibt der Kunde, aber die Marge sinkt. Wenn wir ablehnen, verlieren wir ihn an die Konkurrenz." Er hat ein **internes Modell** der Kundenbeziehung und kann verschiedene Szenarien simulieren, bevor er handelt. Ein unerfahrener Berater hingegen folgt nur der Checkliste (= regelbasiertes System) oder erinnert sich an ähnliche Fälle (= LLM-Pattern-Matching).

---

## Schritt 1: Warum bisherige KI die Welt nicht versteht

Bevor wir verstehen, wie World Models funktionieren, müssen wir begreifen, warum alles, was wir bisher gelernt haben, **nicht ausreicht**.

### Die Grenzen der bisherigen Systeme

| System | Was es kann | Was es NICHT kann |
|--------|------------|-------------------|
| **LLM** (Tutorial 00-01) | „Ein Ball fällt, wenn man ihn loslässt" — korrekt formulieren | Vorhersagen, wo genau der Ball in 0,5 Sekunden ist |
| **Bildgenerator** (Tutorial 00-02) | Ein fotorealistisches Bild eines fallenden Balls erzeugen | Das nächste Bild konsistent generieren — der Ball könnte plötzlich schweben |
| **Multimodal** (Tutorial 00-03) | Bild + Text kombinieren und beschreiben | Verstehen, dass im Bild Schwerkraft herrscht und was das für die nächste Sekunde bedeutet |
| **Videogenerator** (Tutorial 00-04) | Einen kurzen Clip eines fallenden Balls generieren | Garantieren, dass die Physik über 30 Sekunden konsistent bleibt |
| **Audiogenerator** (Tutorial 00-05) | Das Geräusch eines aufprallenden Balls erzeugen | Wissen, dass das Geräusch vom Material und der Fallhöhe abhängt |

Jedes dieser Systeme hat Teilwissen, aber keines hat ein **kohärentes Weltbild**. Es ist, als hätte man fünf Experten, die jeweils nur Bruchstücke kennen, aber nie miteinander reden.

### Das Halluzinations-Problem — physikalisch

Sie kennen Halluzinationen bereits aus Tutorial 00-01 (LLMs erfinden Fakten). Bei World Models gibt es ein physikalisches Pendant:

- Ein Videogenerator zeigt einen Ball, der plötzlich **nach oben** fällt
- Ein generierter Charakter geht **durch eine Wand**
- Ein sonniger Tag wird im nächsten Frame zur **Mitternacht**
- Ein Glas fällt auf den Boden und **bleibt heil**

Das sind keine sprachlichen Halluzinationen — es sind **physikalische** Halluzinationen. Die KI hat keine Vorstellung davon, dass bestimmte Dinge in der realen Welt einfach nicht passieren.

> **Bank-Analogie:** Kennen Sie diese Situation? Ein KI-Chatbot hilft einem Kunden und schlägt vor, gleichzeitig Geld vom Sparkonto abzuheben **und** es dort zu lassen — logisch unmöglich, aber das Modell hat kein Verständnis für den „Zustand" eines Kontos. Es halluziniert physisch unmögliche Finanzzustände. Ein World Model würde den Kontostand als **Zustandsvariable** führen und wissen: Wenn 500 € abgehen, sind sie weg.

### Die LLM-Decke

2024 bewiesen Forscher mathematisch, dass LLMs **nicht alle berechenbaren Funktionen lernen können** und daher zwangsläufig halluzinieren, wenn man sie als allgemeine Problemlöser einsetzt. Die Ursache: LLMs sagen vorher, welches Wort auf das vorherige folgt — basierend auf Mustern in Trainingsdaten. Sie haben keinerlei **Verankerung in der physischen Realität**.

Yann LeCun, Turing-Preisträger und Vater der Convolutional Neural Networks, formuliert es so: „LLMs sind zu limitiert. Sie hochzuskalieren wird uns nicht zu AGI bringen." Seine Alternative: World Models, die **Repräsentationen der physischen Realität** lernen.

```
LLM:          Text → „nächstes Wort" → Text
                     (Muster in Sprache)

World Model:  Welt + Aktion → „nächster Zustand" → Welt
                              (Regeln der Physik)
```

---

## Schritt 2: Der latente Raum — die komprimierte Welt

Das erste Problem: Die echte Welt ist **absurd komplex**. Ein einziges Videobild bei 1080p hat über 6 Millionen Pixel. Eine Sekunde Video bei 30 fps hat 180 Millionen Pixel. Direkt in diesen Rohdaten die Zukunft vorherzusagen? Unmöglich — zu viel Rauschen, zu viel irrelevantes Detail.

Die Lösung: **Komprimierung in einen latenten Raum** — eine Art „Essenz" der Welt.

### Was ist ein latenter Raum?

Sie kennen das Konzept bereits aus Tutorial 00-02 (Diffusion-Modelle) und Tutorial 00-05 (Audio-Codecs). Dort haben Encoder die Eingabe in eine kompakte Darstellung verwandelt. Bei World Models ist der latente Raum das Herzstück:

```
Rohes Bild (6 Mio. Pixel)
         │
    [🔽 Encoder]
         │
         ▼
Latenter Zustand (z. B. 256 Zahlen)
    → Position der Objekte
    → Geschwindigkeiten
    → Materialien
    → Licht und Schatten
    → Zustand (Tür offen/zu, Ball in Luft/am Boden)
```

Statt 6 Millionen Pixel zu verarbeiten, arbeitet das World Model mit vielleicht **256 bis 4.096 Zahlen** — ein Kompressionsvorgang um den Faktor 1.000 bis 10.000.

### Die VAE-Architektur (Variational Autoencoder)

Der klassische Ansatz (Ha & Schmidhuber, 2018) nutzt einen **Variational Autoencoder**:

```
┌────────────────────────────────────────────────────┐
│              VARIATIONAL AUTOENCODER                │
│                                                     │
│  Eingabe-Bild ──→ [Encoder] ──→ z (latenter Code)  │
│       🖼️            🔽              📊              │
│                                      │              │
│                              [Decoder] ──→ Bild     │
│                                 🔼           🖼️     │
│                                                     │
│  Training: Bild → z → rekonstruiertes Bild          │
│  Ziel: z soll so klein wie möglich sein,            │
│        aber genug Info für Rekonstruktion behalten   │
└────────────────────────────────────────────────────┘
```

Das Prinzip: Der Encoder **presst** das Bild durch einen Flaschenhals. Der Decoder muss es aus dem komprimierten Code wieder aufbauen. Was überlebt, ist das Wesentliche — Position, Form, Zustand der Objekte. Was verloren geht: Pixel-Rauschen, exakte Texturen, irrelevante Details.

> **Bank-Analogie:** Denken Sie an Ihren **Kontostand**. Er ist eine extreme Komprimierung tausender Einzelbuchungen zu einer einzigen Zahl. Sie verlieren die Details (wann genau haben Sie den Kaffee gekauft?), behalten aber die **essenzielle Information** (wie viel Geld habe ich?). Der latente Raum eines World Models ist wie ein multidimensionaler Kontostand — nicht eine Zahl, sondern vielleicht 256, die zusammen den „Zustand der Welt" beschreiben.

### Neuere Architektur: Diskrete Tokens statt VAE

Modernere World Models (Genie, GameNGen) nutzen statt fließender VAE-Vektoren **diskrete Tokens** — genau wie die Audio-Codecs aus Tutorial 00-05:

```
Klassisch (VAE):    Bild → [0.42, -0.18, 0.73, ...] (fließende Zahlen)
Modern (VQ-VAE):    Bild → [Token 847, Token 23, Token 1204, ...] (diskrete Codes)
```

Der Vorteil: Diskrete Tokens kann man mit denselben Transformer-Architekturen verarbeiten, die auch LLMs nutzen (Tutorial 00-01). Die Welt wird in eine „Sprache" übersetzt — und die KI kann dann „den nächsten Weltzustand vorhersagen" genau wie ein LLM „das nächste Wort vorhersagt".

### Die Küchen-Analogie: Latenter Raum als abstraktes Gedächtnis

Sie erinnern sich nicht an jede einzelne Fliese auf Ihrem Küchenboden. Sie erinnern sich: „Ich bin in der Küche, der Herd ist an, und die Katze liegt an der Tür." Diese **abstrakte Zusammenfassung** ist Ihr latenter Zustand — und sie reicht aus, um vorherzusagen, was als Nächstes passiert (die Katze wird wahrscheinlich aufstehen, wenn Sie den Kühlschrank öffnen).

Genau so arbeitet der Encoder eines World Models: Er speichert nicht Millionen Pixel, sondern **die wesentliche Situation** — Positionen, Zustände, Beziehungen zwischen Objekten.

---

## Schritt 3: Die Vorhersage — Was passiert als Nächstes?

Jetzt haben wir die Welt komprimiert. Der nächste Schritt ist der entscheidende: **Vorhersage**. Das Modell lernt, aus dem aktuellen Zustand (latenter Code) und einer **Aktion** den nächsten Zustand vorherzusagen.

### Aktionsbedingte Vorhersage

Das ist der Kern, der World Models von reinen Videogeneratoren unterscheidet:

```
Videogenerator:
  Frame 1 → Frame 2 → Frame 3 → ...
  (Was passiert als Nächstes? → nur eine Antwort)

World Model:
  Frame 1 + Aktion „links gehen"  → Frame 2a (Charakter geht links)
  Frame 1 + Aktion „springen"     → Frame 2b (Charakter springt)
  Frame 1 + Aktion „nichts tun"   → Frame 2c (Charakter steht)
  (Was passiert als Nächstes? → kommt darauf an, was SIE tun!)
```

Mathematisch:

```
z_{t+1} = f(z_t, a_t)

z_t     = Aktueller Zustand (latenter Code)
a_t     = Aktion zum Zeitpunkt t
z_{t+1} = Vorhergesagter nächster Zustand
f       = Das gelernte Vorhersagemodell
```

### Drei Architekturen für die Vorhersage

| Architektur | Wie es funktioniert | Beispiel |
|-------------|---------------------|----------|
| **RNN/LSTM** (Klassisch, 2018) | Sequenzielles Gedächtnis — merkt sich vergangene Zustände als versteckten Vektor | Ha & Schmidhuber „World Models" |
| **Transformer** (Modern, 2023+) | Attention über alle bisherigen Zustände — kann gezielt auf relevante Momente zurückblicken | Genie 1, 2, 3 |
| **Diffusion** (Neueste, 2024+) | Generiert den nächsten Zustand durch schrittweises Entrauschen — wie ein Bildgenerator, aber für Weltzustände | DIAMOND, GameNGen |

**Der Architektur-Wandel:** Die klassischen RNN-basierten World Models (2018) hatten ein Problem: **Vergessen**. Je weiter in der Vergangenheit ein Ereignis lag, desto schwächer die Erinnerung. Transformer lösen das mit ihrem Attention-Mechanismus (Tutorial 00-01) — sie können gezielt auf jeden früheren Zustand zugreifen. Diffusion-basierte Modelle (Tutorial 00-02) gehen noch einen Schritt weiter: Sie erzeugen visuell schärfere, detailreichere Vorhersagen, weil der Diffusionsprozess von Natur aus hochfrequente Details gut modelliert.

> **Bank-Analogie:** Die drei Architekturen sind wie drei Arten von Kreditprüfung: **RNN** ist der Berater, der sich an die letzten paar Gespräche erinnert, aber die Details von vor drei Jahren vergessen hat. **Transformer** ist der Berater mit Zugriff auf die komplette digitale Kundenakte — er kann jederzeit jede Transaktion nachschlagen. **Diffusion** ist der Berater, der zusätzlich ein detailliertes Zukunftsszenario durchrechnet: nicht nur „Kredit ja/nein", sondern „so könnte die Finanzlage in 12 Monaten aussehen" — mit allen Nuancen.

### Zeitliche Konsistenz: Ursache kommt vor Wirkung

Ein kritischer Aspekt, der World Models von Videogeneratoren unterscheidet: **Kausalität in der Zeit**. Das Modell sieht tausende Beispiele, in denen auf „Bremse treten" das Auto langsamer wird. In seiner Vorstellung wird das Bremsen daher **immer** zum Langsamerwerden führen — morgen folgt auf heute, Wirkung folgt auf Ursache, in einer sinnvollen Reihenfolge.

Ein Videogenerator hingegen erzeugt manchmal Sequenzen, in denen die Wirkung **vor** der Ursache eintritt — das Auto bremst, bevor der Fahrer das Pedal berührt. Für einen Zuschauer sieht das „fast richtig" aus. Für ein System, das in der echten Welt handeln soll, wäre es katastrophal.

### Räumliches Bewusstsein: Die Welt ist 3D

World Models verstehen, dass Raum dreidimensional und kontinuierlich ist. Wenn Sie sich vorwärtsbewegen, bewegen sich nahe Objekte schneller durchs Blickfeld als entfernte — ein Phänomen namens **Parallaxe**. Wenn Sie sich umdrehen, sollte das, was hinter Ihnen war, immer noch da sein und genauso aussehen.

```
Vorwärtsbewegung → Parallaxe-Effekt:

Nah:   ████████░░░░░░░░  →  ░░░░░░░░████████  (schnell)
Mittel: ░░████████░░░░░░  →  ░░░░████████░░░░  (mittel)
Fern:  ░░░░░░████████░░  →  ░░░░░████████░░░  (kaum Bewegung)
```

Das ist eine der beeindruckendsten Fähigkeiten von Genie 3: Es hält eine **konsistente räumliche Vorstellung** aufrecht — auch wenn Sie sich umdrehen und wieder zurückblicken. Videogeneratoren scheitern hier oft: Was hinter der Kamera war, wird bei Rückblick „neu erfunden" und sieht anders aus.

> **Bank-Analogie:** Räumliches Bewusstsein in World Models ist wie das Verständnis eines Beraters für die **Zusammenhänge** im Kundenportfolio: Wenn der Aktienanteil sinkt, muss der Anleihenanteil relativ steigen — die Teile stehen in Beziehung zueinander. Ein System ohne räumliches Bewusstsein wäre wie ein Berater, der jede Position isoliert betrachtet, ohne zu merken, dass sie ein zusammenhängendes Ganzes bilden.

---

## Schritt 4: Das Träumen — Training im Kopf statt in der Welt

Hier wird es richtig faszinierend. Sobald ein World Model gelernt hat, die Welt vorherzusagen, kann es **träumen** — also Situationen durchspielen, die nie real passiert sind.

### Warum Träumen wichtig ist

Ein selbstfahrendes Auto muss lernen, wie es bei Glatteis reagiert. Optionen:

- **Option A:** Echtes Auto auf echtes Glatteis schicken → teuer, gefährlich, langsam
- **Option B:** Millionen von Glatteis-Situationen **im World Model simulieren** → kostenlos, sicher, schnell

Das Prinzip heißt **„Imagination-Based Training"**: Der Agent (die handelnde KI) trainiert nicht in der echten Welt, sondern in der vorgestellten Welt des World Models.

```
┌──────────────────────────────────────────────────────┐
│                  TRAINING IM TRAUM                     │
│                                                        │
│  1. World Model hat gelernt, wie die Welt funktioniert │
│                                                        │
│  2. Agent „träumt" Situationen:                        │
│     → Stellt sich Glatteis vor                         │
│     → Probiert: Bremsen? Lenken? Gas?                  │
│     → World Model sagt: „Wenn du bremst → Schleudern"  │
│     → Agent lernt: „Bei Glatteis sanft lenken!"        │
│                                                        │
│  3. Millionen Träume → Agent wird besser               │
│     → OHNE jemals ein echtes Auto zu bewegen           │
└──────────────────────────────────────────────────────┘
```

### Compounding Errors: Das große Problem

Aber Vorsicht: Jede Vorhersage hat einen kleinen Fehler. Und diese Fehler summieren sich:

```
Schritt 1: 99% korrekt  → fast perfekt
Schritt 5: 99%^5 = 95%  → noch gut
Schritt 20: 99%^20 = 82% → merklich unscharf
Schritt 100: 99%^100 = 37% → Nonsens
```

Nach genug Schritten „halluziniert" das World Model — die simulierte Welt driftet von der Realität ab. Dieses Problem heißt **Compounding Error** und ist der Hauptgrund, warum World Models (noch) keine beliebig langen Simulationen erzeugen können.

**Gegenmaßnahmen:**
- **Kurze Träume:** Nur 10–50 Schritte simulieren, dann mit echten Daten korrigieren
- **Diffusion-basierte Vorhersage:** Produziert schärfere Einzelbilder → langsamere Fehlerakkumulation (DIAMOND)
- **Re-Encoding:** Vorhergesagtes Bild zurück durch den Encoder schicken → „Snap back to reality"

> **Bank-Analogie:** Das kennen Sie von Finanzprognosen: Eine Quartalsvorhersage ist meist brauchbar. Eine Jahresprognose hat Toleranzen. Eine 10-Jahres-Prognose ist Kaffeesatzlesen. Die Lösung ist dieselbe wie bei World Models: Regelmäßig mit **echten Daten** abgleichen (= Quartalsberichte lesen) und die Prognose korrigieren, statt blind in die Zukunft zu rechnen.

---

## Schritt 5: Planen statt Reagieren

Jetzt kommt das, was World Models wirklich von allen bisherigen KI-Systemen unterscheidet: **Planung**.

Ein LLM reagiert auf Ihren Prompt. Ein Bildgenerator reagiert auf Ihre Beschreibung. Aber ein World Model kann **vorausdenken**:

```
┌───────────────────────────────────────────────────────┐
│                    PLANUNG MIT WORLD MODEL              │
│                                                         │
│  Ziel: Roboter soll Tasse vom Tisch nehmen              │
│                                                         │
│  World Model simuliert 100 mögliche Aktionsfolgen:      │
│                                                         │
│  Plan A: Greife direkt → Tasse kippt um → ❌ Schlechte  │
│  Plan B: Fahre erst näher → Greife seitlich → ✅ Gut     │
│  Plan C: Greife von oben → Hand stößt gegen Regal → ❌  │
│  ...                                                    │
│  Plan K: Fahre links, drehe Hand, greife → ✅ Optimal    │
│                                                         │
│  → Agent wählt Plan K und führt ihn aus                 │
└───────────────────────────────────────────────────────┘
```

Das Verfahren heißt **Model Predictive Control (MPC)**: Bevor der Agent handelt, simuliert er viele mögliche Zukunftsverläufe im World Model und wählt den besten.

Das ist fundamental anders als bisherige KI:
- **Regelbasiert:** „Wenn Tasse sichtbar → Greifprogramm starten" (starr, keine Anpassung)
- **Reinforcement Learning (ohne World Model):** Tausende echte Versuche → langsam, teuer
- **World Model + Planung:** Tausende **simulierte** Versuche → schnell, kostenlos, sicher

> **Bank-Analogie:** Stellen Sie sich vor, Sie könnten vor jeder Kreditentscheidung 100 mögliche Zukunftsverläufe des Kunden simulieren: „Was passiert, wenn er seinen Job verliert? Was, wenn die Immobilienpreise fallen? Was, wenn er eine Gehaltserhöhung bekommt?" Genau das tut ein World Model — es spielt Szenarien durch und wählt die Aktion, die zum besten erwarteten Ergebnis führt. Das ist der Unterschied zwischen einer Kreditentscheidung nach Checkliste und einer strategischen Risikoanalyse.

---

## Schritt 6: Wie ein World Model gebaut wird — Schritt für Schritt

Jetzt kennen Sie die Einzelteile. Hier ist die komplette Pipeline:

### Phase 0: Sandbox definieren — die Welt eingrenzen

Kein Modell kann die gesamte Realität erfassen. Deshalb beginnt jedes World Model mit einer klaren Entscheidung: **Welche Welt soll es sich vorstellen?**

- „Dieses Modell wird sich vorstellen, was auf einer zweispurigen Straße mit Autos und Ampeln passiert"
- „Dieses Modell wird sich vorstellen, was in einem Minecraft-Level passiert"
- „Dieses Modell wird sich vorstellen, was in einer Bankfiliale passiert"

Je enger die Sandbox, desto genauer das Modell. Je weiter, desto mehr Daten und Rechenleistung braucht es. Genie 3 ist deshalb beeindruckend, weil es als erstes eine **allgemeine** Sandbox anstrebt — nicht auf eine Domäne beschränkt.

### Phase 1: Datensammlung — der Welt zusehen

Das World Model **sieht zu** — es beobachtet Tausende von Beispielen. Entscheidend: Es speichert nicht nur, was es **sieht**, sondern auch, was gleichzeitig **getan** wird.

Stellen Sie sich vor, Sie nehmen jemandem beim Spielen eines Videospiels zu: Sie speichern die **Bildschirmaufnahme** und **jeden Tastendruck**. Zusammen ergibt das tausende Beispiele der Form: „Wenn das Spiel SO aussah und der Spieler DAS drückte, dann sah das Spiel DANACH SO aus."

| Datenquelle | Was das Modell lernt | Gespeichert wird |
|-------------|---------------------|-----------------|
| **Videospiele** | Physik, Objekte, Aktionen und ihre Folgen | Bildschirm + Tastendrücke |
| **Dashcam-Videos** | Straßenverkehr, Verkehrsregeln, Wetter | Video + Lenkrad/Gas/Bremse |
| **Roboter-Sensoren** | Greifen, Bewegen, Objekteigenschaften | Kamera + Gelenkwinkel + Motorbefehle |
| **Simulatoren** | Kontrollierte Physik-Experimente | Alles (perfekte Daten möglich) |
| **Internet-Videos** | Allgemeine Weltphysik | Nur Video (keine Aktionen — schwieriger!) |

### Der Imagination Loop: Wie das Modell die Regeln lernt

Bevor wir die Einzelschritte durchgehen: Hier ist der **Kernzyklus**, der beim Training millionenfach durchlaufen wird. Wenn Sie nur eine Sache aus diesem Tutorial mitnehmen, dann diesen Loop:

```
┌─────────────────────────────────────────────────────┐
│              DER IMAGINATION LOOP                    │
│                                                      │
│   ① BEOBACHTEN: Echtes Bild (Frame 1) aufnehmen     │
│         │                                            │
│         ▼                                            │
│   ② KOMPRIMIEREN: Encoder → latenter Zustand z₁     │
│         │                                            │
│         ▼                                            │
│   ③ VORHERSAGEN: z₁ + Aktion → z₂ (vorhergesagt)   │
│         │                                            │
│         ▼                                            │
│   ④ SICHTBAR MACHEN: Decoder → vorhergesagtes Bild  │
│         │                                            │
│         ▼                                            │
│   ⑤ VERGLEICHEN: Vorhergesagtes Bild vs. echtes     │
│      Frame 2 aus den Trainingsdaten                  │
│         │                                            │
│         ▼                                            │
│   ⑥ LERNEN: Fehler berechnen → Modell anpassen      │
│         │                                            │
│         └──────────→ zurück zu ① (millionenfach)     │
└─────────────────────────────────────────────────────┘
```

**Nach dem Training** fällt Schritt ⑤ weg. Das Modell braucht keinen Vergleich mit der Realität mehr — es kann frei **tagträumen**: Startzustand + Aktionsfolge rein, und es imaginiert eine ganze Sequenz von Zukunftsbildern, jedes aufbauend auf dem vorherigen.

> **Bank-Analogie:** Das ist wie ein Azubi, der anfangs jede Kreditentscheidung mit dem erfahrenen Kollegen **vergleicht** (Schritt ⑤). „Ich hätte abgelehnt — was hast du entschieden?" Der Unterschied ist sein Lernsignal. Nach tausend Fällen braucht er den Vergleich nicht mehr — er hat ein inneres Modell, das gute Entscheidungen vorhersagt. Der Imagination Loop ist die Ausbildung; das fertige World Model ist der ausgelernte Berater.

### Phase 2: Encoder-Training (die Welt komprimieren)

```
Tausende Videoframes
         │
    [VAE / VQ-VAE Training]
         │
         ▼
Encoder: Kann jedes Bild → latenten Code z übersetzen
Decoder: Kann jeden Code z → Bild rekonstruieren
```

### Phase 3: Vorhersagemodell-Training (die Zukunft lernen)

```
Sequenzen von (z_t, Aktion_t, z_{t+1})
         │
    [Transformer / RNN / Diffusion Training]
         │
         ▼
Modell: Kann z_{t+1} = f(z_t, a_t) vorhersagen
        „Wenn die Welt SO aussieht und ich DAS tue,
         dann sieht sie DANACH SO aus"
```

### Phase 4: Agent-Training (im Traum üben)

```
┌──────────────────────────────────────────┐
│           DREAMLAND-TRAININGSLOOP         │
│                                           │
│  1. Agent startet in zufälligem Zustand   │
│  2. Agent wählt Aktion                    │
│  3. World Model sagt nächsten Zustand     │
│  4. Belohnung wird berechnet              │
│  5. Agent lernt → zurück zu Schritt 2     │
│                                           │
│  Millionen Durchläufe pro Stunde          │
│  (In der echten Welt: vielleicht 10)      │
└──────────────────────────────────────────┘
```

### Phase 5: Planung (in der echten Welt anwenden)

```
Echte Welt → Encoder → z_t
                         │
                    World Model simuliert
                    N mögliche Zukunftsverläufe
                         │
                    Beste Aktionsfolge auswählen
                         │
                    Aktion in echter Welt ausführen
                         │
                    Neuer Zustand → zurück zum Anfang
```

> **Bank-Analogie:** Die fünf Phasen sind wie die Ausbildung eines Kreditanalysten: **Phase 1** (Daten) = Hunderte vergangene Kreditfälle studieren. **Phase 2** (Encoder) = Lernen, was die wesentlichen Risikofaktoren sind (Einkommen, Sicherheiten, Branche — nicht die Schriftart des Antrags). **Phase 3** (Vorhersage) = Verstehen, wie sich Risikofaktoren über Zeit entwickeln. **Phase 4** (Traumtraining) = Dutzende hypothetische Szenarien durchspielen. **Phase 5** (Planung) = Beim echten Kunden die beste Strategie wählen.

---

## Schritt 7: Die große Vereinigung — Warum World Models alles verbinden

Hier wird es konzeptionell spannend. World Models sind nicht einfach „noch eine KI-Technologie" — sie sind die **Zusammenführung** von allem, was wir in den bisherigen Tutorials gelernt haben:

```
┌──────────────────────────────────────────────────────────┐
│           DIE GROSSE VEREINIGUNG                          │
│                                                           │
│  Tutorial 00-01 (LLMs):                                  │
│  → Transformer-Architektur + „Nächstes Token vorhersagen" │
│     ═══════════════════════════════╗                      │
│                                    ║                      │
│  Tutorial 00-02 (Diffusion):       ║                      │
│  → Entrauschen für scharfe Bilder  ║                      │
│     ════════════════════════╗      ║                      │
│                              ║     ║                      │
│  Tutorial 00-03 (Multimodal):║     ║                      │
│  → Verschiedene Modalitäten  ║     ║                      │
│    in einem Raum verbinden   ║     ║                      │
│     ═══════════════════╗     ║     ║                      │
│                         ║    ║     ║                      │
│  Tutorial 00-04 (Video): ║   ║     ║                      │
│  → Zeitliche Konsistenz  ║   ║     ║                      │
│     ══════════════╗      ║   ║     ║                      │
│                    ║     ║   ║     ║                      │
│  Tutorial 00-05   ║     ║   ║     ║                      │
│  (Audio):         ║     ║   ║     ║                      │
│  → Audio-Tokens   ║     ║   ║     ║                      │
│     ═══════╗      ║     ║   ║     ║                      │
│             ▼     ▼     ▼   ▼     ▼                      │
│         ┌──────────────────────────┐                      │
│         │      WORLD MODEL         │                      │
│         │  Versteht + Simuliert +  │                      │
│         │  Plant + Handelt         │                      │
│         └──────────────────────────┘                      │
└──────────────────────────────────────────────────────────┘
```

| Bisheriges Tutorial | Was World Models davon nutzen |
|---------------------|-------------------------------|
| **00-01: LLMs** | Transformer + „nächstes Token vorhersagen" → wird zu „nächsten Weltzustand vorhersagen" |
| **00-02: Diffusion** | Entrauschungsprozess → erzeugt visuell scharfe Vorhersagen (DIAMOND, GameNGen) |
| **00-03: Multimodal** | Gemeinsamer Repräsentationsraum → World Model verbindet Sehen, Hören, Fühlen |
| **00-04: Video** | Zeitliche Konsistenz → World Model erweitert das um Physik und Interaktivität |
| **00-05: Audio** | Audio-Tokens + Codecs → World Models können auch Klang der Umgebung simulieren (Veo 3) |

> **Bank-Analogie:** Stellen Sie sich vor, Ihre Bank hätte bisher getrennte Systeme: eines für Kontobewegungen, eines für Kreditrisiko, eines für Kundenverhalten, eines für Marktanalyse. Jedes funktioniert allein, aber keines kennt den Kontext der anderen. Ein World Model ist wie ein **integriertes Risikomanagement-System**, das alle Datenströme verbindet und ein kohärentes Gesamtbild der Kundenbeziehung hat — nicht fünf Einzelsichten, sondern eine Weltsicht.

---

## Die Modell-Landschaft: Wer baut World Models? (Stand: Februar 2026)

| Modell / Plattform | Entwickler | Besonderheit | Zugang |
|---------------------|-----------|--------------|--------|
| **Genie 3** | Google DeepMind | Erstes Echtzeit-Weltmodell: 24 fps, 720p, interaktiv, minutenlang konsistent | Forschungsvorschau |
| **NVIDIA Cosmos** | NVIDIA | Open-Source-Plattform für World Foundation Models. Fokus: Robotik + autonomes Fahren. 2 Mio. Downloads | Open Source (Hugging Face) |
| **Marble** | World Labs (Fei-Fei Li) | Kommerzielle 3D-Welten aus Text/Bild. Persistente Umgebungen | Kostenlos bis $95/Monat |
| **AMI Labs** | Yann LeCun | €500 Mio. Finanzierung. Baut auf I-JEPA/V-JEPA. Ziel: Physikverständnis statt Text-Pattern | Noch nicht veröffentlicht |
| **V-JEPA 2** | Meta | Visuelles World Model für Robotik. 65–80% Erfolgsrate bei Greifaufgaben | Open Source |
| **GWM-1** | Runway | Erstes „General World Model" eines Videogenerator-Unternehmens. Erkundbare Umgebungen | Kommerziell (API) |
| **Dreamer v3** | Danijar Hafner | Universelles RL-World-Model. Lernt Minecraft, Atari, Robotik mit gleichen Settings | Open Source |
| **DIAMOND** | Alonso et al. | Diffusions-World-Model. Übermenschliche Atari-Scores, trainiert rein im Traum | Open Source |
| **HY-World 1.5** | Tencent | Echtzeit-Weltsimulation, 24 fps | Kommerziell |

### Die drei Lager

```
┌──────────────────────────────────────────────────────────┐
│                 DIE WORLD-MODEL-LANDSCHAFT                │
│                                                           │
│  🎮 LAGER 1: Interaktive Welten (Consumer)               │
│     Genie 3, Marble, GWM-1                               │
│     → „Beschreibe eine Welt → Gehe hinein"               │
│     → Zielgruppe: Kreative, Gamer, Film/VFX              │
│                                                           │
│  🤖 LAGER 2: Physikalische KI (Industrie)                │
│     NVIDIA Cosmos, V-JEPA 2, Dreamer v3                   │
│     → „Trainiere Roboter und Autos im Traum"             │
│     → Zielgruppe: Robotik, Automotive, Fertigung          │
│                                                           │
│  🧠 LAGER 3: Fundamentale Intelligenz (Forschung)        │
│     AMI Labs, I-JEPA, DIAMOND                             │
│     → „Baue KI, die die Welt wirklich versteht"          │
│     → Zielgruppe: AGI-Forschung, langfristige Vision      │
└──────────────────────────────────────────────────────────┘
```

---

## Kosten-Vergleich: World-Model-Simulation vs. echte Welt

| Szenario | Echte Welt | World-Model-Simulation |
|----------|-----------|----------------------|
| **1.000 Fahrstunden für autonomes Auto** | ~€500.000 (Fahrzeug, Fahrer, Versicherung, Benzin) | ~€5.000 (GPU-Kosten für Simulation) |
| **Roboter-Greiftraining (10.000 Versuche)** | ~€50.000 (Roboter, Werkstück, Aufsicht, Reparaturen) | ~€500 (GPU-Stunden auf Cloud) |
| **Crash-Test (100 Szenarien)** | ~€2.000.000 (100 echte Autos zerstören) | ~€2.000 (100 simulierte Crashes) |
| **Architektur-Begehung (3D-Modell)** | ~€15.000 (VR-Studio, 3D-Künstler) | ~€50 (Marble/Genie-Prompt) |
| **Spieleentwicklung: Level-Prototyping** | ~€20.000 (Level Designer, 2 Wochen) | ~€200 (KI-generierte Levels, 2 Stunden) |

**Die Größenordnung:** World Models können die Kosten für Training und Prototyping um den **Faktor 100–1.000** senken. Der Haken: Die Simulation ist nur so gut wie das Modell — für sicherheitskritische Anwendungen braucht es immer noch echte Tests als letzte Validierung.

> **Bank-Analogie:** Das ist wie der Unterschied zwischen einem echten Stresstest (alle Kreditportfolios durchrechnen mit echten Marktdaten) und einem **simulierten** Stresstest (Szenarien am Computer durchspielen). Die Simulation ist 100x billiger und schneller — aber für die BaFin brauchen Sie trotzdem die echte Berechnung. World Models sind der Simulator, nicht der Ersatz für die Realität.

---

## Werkzeuge & Stellschrauben

Wenn Sie mit World Models arbeiten (oder Produkte evaluieren, die sie nutzen), sind das die wichtigsten Parameter:

| Parameter | Was er steuert | Empfehlung |
|-----------|---------------|------------|
| **Rollout-Länge** | Wie viele Schritte in die Zukunft simuliert werden | Kurz (10–50) für präzise Vorhersagen, lang (100+) für Exploration — aber Achtung: Compounding Error! |
| **Latente Dimension** | Größe des komprimierten Weltzustands (z. B. 256 vs. 4.096 Zahlen) | Größer = mehr Detail, aber mehr Rechenleistung. Sweet Spot: 512–2.048 für die meisten Anwendungen |
| **Aktionsraum** | Welche Aktionen der Agent ausführen kann | Diskret (links/rechts/springen) für Spiele, kontinuierlich (Lenkwinkel 0–360°) für Robotik |
| **Temperatur** | Wie deterministisch die Vorhersage ist | Niedrig: Vorhersagbar, wiederholbar. Hoch: Kreativer, überraschender — aber auch fehleranfälliger |
| **Ensemble-Größe** | Wie viele World Models parallel vorhersagen | Mehrere Modelle → robuster (wenn alle dasselbe sagen, stimmt es wahrscheinlich), aber teurer |

---

## Pipeline-Zusammenfassung

Die komplette World-Model-Pipeline auf einen Blick:

```
┌─────────────────────────────────────────────────────────────────────┐
│                  WORLD MODEL: END-TO-END PIPELINE                    │
│                                                                      │
│  PHASE 1: DATEN                                                      │
│  Videos/Spiele/Sensoren                                              │
│       │                                                              │
│       ▼                                                              │
│  PHASE 2: ENCODER (Welt → Latent)                                    │
│  [VAE / VQ-VAE / Vision Encoder]                                     │
│  Bild/Video → z (kompakter Code, z.B. 256-4096 Zahlen)              │
│       │                                                              │
│       ▼                                                              │
│  PHASE 3: VORHERSAGE (Latent + Aktion → nächstes Latent)            │
│  [Transformer / RNN / Diffusion]                                     │
│  (z_t, Aktion_t) → z_{t+1}                                          │
│  „Wenn die Welt SO aussieht und ich DAS tue → SO sieht sie aus"     │
│       │                                                              │
│       ├──→ PHASE 4: TRAUMTRAINING                                    │
│       │    Agent übt Millionen Durchläufe im simulierten Zustand     │
│       │    → Lernt Strategie OHNE echte Welt                         │
│       │                                                              │
│       └──→ PHASE 5: PLANUNG (MPC)                                    │
│            Simuliere N Zukunftsverläufe → Wähle beste Aktion         │
│                 │                                                     │
│                 ▼                                                     │
│  PHASE 6: DECODER (Latent → Welt)                                    │
│  [Decoder / Diffusion / Renderer]                                    │
│  z → Bild/Video/3D-Welt (sichtbare Ausgabe)                         │
│                 │                                                     │
│                 ▼                                                     │
│  AUSGABE: Interaktive 3D-Welt / Roboter-Steuerung / Simulation      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Was World Models (noch) nicht können — Limitationen

### 🔴 Langzeit-Konsistenz

Das Compounding-Error-Problem ist ungelöst. Selbst Genie 3, das fortschrittlichste System, bleibt nur **minutenlang** konsistent. Für manche Anwendungen reicht das — für andere nicht:

| Anforderung | Benötigte Konsistenz | World-Model-Simulation allein (2026) |
|-------------|---------------------|--------------------------------------|
| Roboter-Greifbewegung (5 Sek.) | Sekunden | ✅ Gelöst |
| Spielelevel erkunden (2 Min.) | Minuten | ⚠️ Grenzwertig (Genie 3) |
| Autonomes Fahren in der Stadt (30 Min.) | Halbe Stunde | ❌ Nicht ausreichend |
| Architekturbegehung eines Gebäudes (10 Min.) | 10+ Minuten | ❌ Driftet ab |

> **Wichtiger Kontext:** Autonomes Fahren existiert bereits — Waymo fährt seit 2024 in mehreren US-Städten ohne Fahrer. Aber Waymo nutzt **kein reines World Model**, sondern einen Mix aus LiDAR-Sensoren, hochauflösenden Karten, regelbasierter Logik und Machine-Learning-Komponenten. World Models werden dort als **ein Baustein** fürs Training eingesetzt (Szenarien simulieren), nicht als alleiniges Fahrsystem. Die Tabelle oben zeigt daher nicht „Kann ein Auto autonom fahren?", sondern „Kann ein World Model **allein** eine 30-minütige Stadtfahrt konsistent simulieren?" — und das kann es noch nicht.

### 🔴 Physikalische Exaktheit

World Models lernen **approximierte** Physik. Sie kennen keine Newton'schen Gesetze — sie haben Muster gelernt. Das führt zu subtilen Fehlern:

- Objekte haben manchmal das falsche Gewicht (ein Stein schwebt, ein Blatt fällt zu schnell)
- Kollisionen sind nicht immer korrekt (Objekte überlappen kurz)
- Flüssigkeiten und Stoffe (Textilien, Sand) sind besonders schwierig

**Für Bankkontext:** Ein KI-Berater, der auf einem World Model basiert, könnte den „Zustand" eines Kundenportfolios simulieren — aber die Simulation wäre eine Annäherung, keine exakte Berechnung. Für regulatorische Zwecke (BaFin, EBA-Stresstests) reicht das **nicht** als alleinige Grundlage.

### 🔴 Rechenkosten

World Models in Echtzeit zu betreiben ist extrem ressourcenintensiv:

| System | Benötigte Hardware | Geschätzter Cloud-Preis/Stunde |
|--------|-------------------|-------------------------------|
| Genie 3 (24 fps, 720p) | Mehrere TPU v5 | ~$50–100/h |
| NVIDIA Cosmos (Robotik) | A100/H100 GPU | ~$5–20/h |
| Dreamer v3 (einfache Umgebung) | Einzelne GPU | ~$1–3/h |

### 🟡 Kausalität vs. Korrelation

World Models lernen Korrelationen aus Daten: „Nach Blitz kommt Donner." Aber sie verstehen nicht immer die Kausalität: „Blitz **verursacht** Donner." Das kann zu subtilen Fehlern führen, wenn Situationen auftreten, die im Training selten waren.

### 🟡 Keine Abstraktion über Domänen hinweg

Ein World Model, das Straßenverkehr gelernt hat, kann nicht automatisch ein Lagerhaus navigieren. Jede neue Domäne braucht eigene Daten und Training. Die „eine KI, die alles versteht" gibt es noch nicht — auch wenn das das erklärte Ziel von AMI Labs ist.

> **Bank-Analogie:** Das ist wie ein Risikomodell, das perfekt für Immobilienkredite funktioniert, aber bei Unternehmenskrediten komplett versagt. Die Muster sind andere, die Variablen sind andere, die Dynamik ist eine andere. Übertragbarkeit zwischen Domänen ist das ungelöste Kernproblem — genau wie bei regulatorischen Modellen, die für jede Assetklasse neu kalibriert werden müssen.

---

## 🔬 Probieren Sie es selbst!

### Experiment 1: Genie — in ein Bild einsteigen

1. Besuchen Sie **genie.google** (Google Project Genie / Genie 3 Demo, falls verfügbar) oder schauen Sie sich die Demo-Videos auf der [DeepMind-Blogseite](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/) an
2. Beobachten Sie: Die KI generiert eine 3D-Welt aus einem einzigen Text-Prompt
3. Achten Sie auf:
   - Bleibt die Physik konsistent, wenn der Charakter sich bewegt?
   - Was passiert an den „Rändern" der generierten Welt?
   - Wie lange bleibt die Darstellung stabil, bevor Artefakte auftauchen?
4. **Reflexionsfrage:** Vergleichen Sie das mit einem Videogenerator (Sora, Kling). Was ist der fundamentale Unterschied?

### Experiment 2: World Labs Marble — 3D-Welten aus Text

1. Gehen Sie zu **worldlabs.ai** und erstellen Sie einen kostenlosen Account
2. Geben Sie einen Prompt ein, z. B.: „Ein sonniges Bankbüro mit Holzmöbeln und großen Fenstern"
3. Die KI generiert eine **begehbare 3D-Umgebung**
4. Navigieren Sie durch den Raum und beobachten Sie:
   - Bleiben die Möbel an ihrem Platz, wenn Sie sich umdrehen und zurückblicken?
   - Stimmen die Perspektiven? (Stichwort: Parallaxe)
   - Was passiert mit Details, die Sie zuerst nicht sehen konnten (Rückseite eines Schranks)?

### Experiment 3: Modellvergleich — Videogenerator vs. World Model

| Kriterium | Videogenerator (z.B. Sora/Kling) | World Model (z.B. Genie 3/Marble) |
|-----------|----------------------------------|-----------------------------------|
| Eingabe | Text-Prompt | Text-Prompt oder Bild |
| Ausgabe | Festes Video (nicht interaktiv) | Interaktive, begehbare Welt |
| Physik-Konsistenz | Variabel, oft Fehler bei >5 Sek. | Besser, aber nicht perfekt |
| Interaktion | ❌ Sie können nichts tun | ✅ Sie steuern die Bewegung |
| Kausales Verständnis | ❌ Reine Mustererkennung | ⚠️ Gelernte Approximation |

**Testen Sie:** Geben Sie **denselben Prompt** in einen Videogenerator und ein World Model ein. Wo sehen Sie Unterschiede in der Physik? Wo ist der Videogenerator besser (Bildqualität), wo das World Model (Konsistenz, Interaktion)?

---

## Das Wichtigste auf einen Blick

| Konzept | Was es bedeutet | Warum es wichtig ist |
|---------|----------------|---------------------|
| **World Model** | KI, die sich die Welt vorstellt und simuliert | Ermöglicht Planung, Vorausdenken, physikalisches Verständnis |
| **Latenter Raum** | Komprimierte Darstellung der Welt (256–4.096 Zahlen statt Millionen Pixel) | Macht Vorhersage erst rechenbar |
| **Aktionsbedingte Vorhersage** | „Wenn ich X tue, passiert Y" | Der Kern-Unterschied zu reinen Generatoren |
| **Imagination Training** | Agent trainiert in vorgestellter Welt | 100–1.000x billiger und sicherer als echtes Training |
| **Imagination Loop** | Beobachten → Komprimieren → Vorhersagen → Vergleichen → Lernen | Der Trainingszyklus, der das Modell Schritt für Schritt besser macht |
| **Compounding Error** | Kleine Fehler summieren sich über Zeit | Hauptlimitation: Simulationen werden nach Minuten ungenau |
| **Model Predictive Control** | Viele Zukunftsverläufe simulieren, besten wählen | Ermöglicht strategische Planung statt bloßer Reaktion |
| **Encoder/Decoder** | Übersetzer zwischen echter Welt und latentem Raum | Bestimmt, welche Details erhalten bleiben |
| **Große Vereinigung** | World Models verbinden LLM + Diffusion + Multimodal + Video + Audio | Der nächste Schritt nach einzelnen Modalitäten |

---

## Parallelen zu vorherigen Tutorials

| Tutorial | Verbindung zu World Models |
|----------|---------------------------|
| **00-01 (LLMs)** | „Nächstes Token vorhersagen" → wird zu „nächsten Weltzustand vorhersagen". Transformer-Architektur ist der Kern vieler World Models (Genie, Dreamer v3) |
| **00-02 (Diffusion)** | Entrauschen für scharfe Bilder → Diffusion erzeugt scharfe Weltvorhersagen (DIAMOND, GameNGen). Latenter Raum aus VAE wird wiederverwendet |
| **00-03 (Multimodal)** | Verschiedene Sinne in einem Raum verbinden → World Models gehen weiter: Nicht nur verbinden, sondern **simulieren**, wie Sinneseindrücke zusammenhängen |
| **00-04 (Video)** | Zeitliche Konsistenz bei Video → World Models erweitern das um **Interaktivität** (Aktion → Reaktion) und **physikalische Regeln** |
| **00-05 (Audio)** | Audio-Tokens als Sprache behandeln → World Models können auch Klang der Umgebung simulieren. Veo 3 generiert bereits Video + synchrones Audio |

**Der rote Faden:** Jedes Tutorial hat eine neue Dimension hinzugefügt: Text → Bild → Multimodal → Zeitliche Sequenz → Klang → **Komplette simulierte Welt**. World Models sind die Konvergenz — der Punkt, an dem alle Fäden zusammenlaufen.

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **World Model** | KI-System, das eine interne Repräsentation der Welt lernt und damit zukünftige Zustände vorhersagen kann — basierend auf dem aktuellen Zustand und einer Aktion |
| **Latenter Raum** | Komprimierter Darstellungsraum, in dem die wesentlichen Informationen der Welt als Zahlenvektoren gespeichert sind (vgl. Tutorial 00-02, 00-05) |
| **Encoder** | Netzwerk, das Rohbeobachtungen (Bilder, Sensordaten) in den latenten Raum komprimiert |
| **Decoder** | Netzwerk, das aus dem latenten Raum wieder beobachtbare Ausgaben (Bilder, Video) rekonstruiert |
| **VAE (Variational Autoencoder)** | Architektur mit Encoder + Decoder, die lernt, Daten in einen kompakten latenten Raum zu komprimieren und daraus zu rekonstruieren |
| **VQ-VAE (Vector Quantized VAE)** | Variante des VAE, die statt fließender Zahlen **diskrete Tokens** erzeugt — ähnlich wie Audio-Codecs (Tutorial 00-05) |
| **Aktionsbedingte Vorhersage** | Vorhersage des nächsten Zustands unter Berücksichtigung einer Aktion: z_{t+1} = f(z_t, a_t) |
| **Compounding Error** | Fehlerakkumulation bei mehrstufigen Vorhersagen — kleine Abweichungen pro Schritt summieren sich zu großen Fehlern |
| **Imagination Loop** | Der Kernzyklus beim Training: Beobachten → Komprimieren → Vorhersagen → Sichtbar machen → Vergleichen → Lernen. Wird millionenfach wiederholt, bis das Modell die Regeln der Welt verinnerlicht hat |
| **Imagination Training** | Trainingsverfahren, bei dem ein Agent in der simulierten Welt des World Models übt, statt in der echten Welt |
| **Model Predictive Control (MPC)** | Planungsverfahren: Simuliere viele mögliche Zukunftsverläufe, wähle die beste Aktionssequenz |
| **Dreamer** | Familie von World Models (v1–v3, Hafner et al.), die Reinforcement Learning komplett in gelernten Weltmodellen durchführen |
| **Genie** | Google DeepMinds World-Model-Reihe (1–3): generiert interaktive Welten, die man erkunden kann |
| **NVIDIA Cosmos** | Open-Source-Plattform für World Foundation Models, fokussiert auf Robotik und autonomes Fahren |
| **I-JEPA / V-JEPA** | Joint Embedding Predictive Architecture (Bild/Video) — lernt durch Vorhersage von Repräsentationen, nicht von Pixeln. Basis für AMI Labs |
| **DIAMOND** | Diffusion-basiertes World Model, das übermenschliche Atari-Scores erreicht (NeurIPS 2024 Spotlight) |
| **GameNGen** | Neuronales Netz, das DOOM in Echtzeit simuliert — ohne Game Engine, nur gelernte Physik |
| **Parallaxe** | Visuelles Phänomen: Nahe Objekte bewegen sich schneller durchs Blickfeld als entfernte. World Models lernen diesen Effekt, um konsistente 3D-Welten zu erzeugen |
| **Sandbox** | Die abgegrenzte Umgebung, die ein World Model simuliert — z.B. eine Straße, ein Spielelevel, ein Raum |
| **Temporale Konsistenz** | Die Eigenschaft, dass Ursache vor Wirkung eintritt und Ereignisse in einer logischen zeitlichen Reihenfolge stattfinden |
| **Rollout** | Eine Sequenz von Vorhersage-Schritten im World Model: Zustand → Aktion → nächster Zustand → ... |
| **Physical AI** | KI-Systeme, die in der physischen Welt agieren (Roboter, autonome Fahrzeuge) — Hauptanwendungsgebiet von World Models |
| **Foundation World Model** | Großes, vortrainiertes World Model, das für verschiedene spezifische Anwendungen angepasst werden kann (analog zu LLM Foundation Models) |
| **World Foundation Model** | Synonyme Bezeichnung (von NVIDIA geprägt) für Foundation World Model |
| **Marble** | World Labs' kommerzielles World Model, das begehbare 3D-Umgebungen aus Text/Bild generiert |
| **GWM (General World Model)** | Runways Bezeichnung für ihr World Model, das allgemeine Umgebungen simulieren kann |

---


## Quellen

- Ha, D. & Schmidhuber, J. (2018). „World Models." arXiv:1803.10122.
- Alonso, E. et al. (2024). „Diffusion for World Modeling: Visual Details Matter in Atari (DIAMOND)." NeurIPS 2024 Spotlight.
- Google DeepMind (2025). „Genie 3: A New Frontier for World Models." deepmind.google/blog.
- NVIDIA (2025). „Cosmos World Foundation Model Platform for Physical AI." research.nvidia.com.
- Hafner, D. et al. (2023). „Mastering Diverse Domains through World Models (Dreamer v3)." arXiv:2301.04104.
- Meta (2025). „V-JEPA 2: Self-Supervised Video Models Enable Understanding, Prediction and Planning." arXiv:2506.09985.
- World Labs (2025). „Marble: Persistent 3D Environments from Multimodal Prompts." worldlabs.ai.
- Runway (2025). „GWM-1: General World Model." runway.com.
- Introl Blog (2026). „World Models Race 2026: How LeCun, DeepMind, and World Labs Are Redefining the Path to AGI." introl.com.
