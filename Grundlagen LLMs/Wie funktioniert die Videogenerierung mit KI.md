# Wie KI Videos generiert

**Vom Einzelbild zum Film — wie KI das Konzept „Zeit" lernt, verständlich erklärt**

---

## Warum dieses Tutorial?

In den vorherigen Tutorials haben Sie drei Spezialisten kennengelernt: LLMs für Text (Tutorial 00-01), Diffusion-Modelle für Bilder (Tutorial 00-02) und multimodale Modelle, die beides verbinden (Tutorial 00-03). Jetzt machen wir den nächsten Schritt: **Wir bringen Bilder zum Laufen.**

Sie haben wahrscheinlich schon Sora, Veo oder Kling gesehen — Sie tippen „ein Golden Retriever rennt durch ein Sonnenblumenfeld" und Sekunden später schauen Sie einen Clip, der aussieht wie mit einer DSLR gefilmt. Im Februar 2026 ging ByteDances Seedance 2.0 viral, als Nutzer Brad Pitt gegen Tom Cruise kämpfen ließen — in einem Video, das rein aus Text generiert wurde. Es wirkt wie Magie.

Aber unter der Haube sind diese Systeme auf überraschend intuitiven Ideen aufgebaut. Und wenn Sie als Kind jemals ein **Daumenkino** gebastelt haben, verstehen Sie den Kern bereits.

**Was Sie nach diesem Tutorial wissen werden:**

- Warum Videogenerierung fundamental schwieriger ist als Bildgenerierung
- Was „temporale Konsistenz" bedeutet und warum sie alles entscheidet
- Wie man ein Bildmodell in ein Videomodell umbaut — Schritt für Schritt
- Was Raumzeit-Patches sind und warum sie das Problem handhabbar machen
- Wie temporale Attention-Layer dem Modell ein Gefühl für Bewegung geben
- Wie man aus Sekunden Minuten macht — ohne dass die GPUs schmelzen
- Was Veo 3.1, Sora 2, Kling, Wan 2.1 und Seedance 2.0 können — und wo ihre Grenzen liegen
- Wie dieses Wissen Ihnen hilft, bessere Video-Prompts zu schreiben

---

## Ein kurzer Blick zurück: Wie KI das Filmemachen lernte

Bevor wir in die Technik einsteigen, lohnt sich ein Blick auf die rasante Geschichte der KI-Videogenerierung:

| Jahr | Meilenstein | Was es konnte |
|------|------------|---------------|
| **2022** | **Make-A-Video** (Meta) | Erster großer Text-to-Video-Ansatz: Bildmodell + temporale Layer. Kurze, unscharfe Clips — aber der Beweis, dass es funktioniert |
| **2023** | **Gen-2** (Runway) | Erster kommerzieller Text-to-Video-Dienst für Kreative. 4 Sekunden, oft noch verzerrt |
| **2024 Feb** | **Sora Preview** (OpenAI) | Die Demos schockierten die Welt: 60 Sekunden, fotorealistisch, Kamerafahrten. Noch nicht öffentlich |
| **2024 Mai** | **Veo 1** (Google DeepMind) | Googles Antwort: 1080p, über 1 Minute. Angekündigt auf der Google I/O |
| **2024 Jun** | **Kling 1.0** (Kuaishou) | Chinas Überraschung: 2 Minuten bei 1080p und 30fps. Diffusion-Transformer-Architektur |
| **2024 Dez** | **Sora 1** (OpenAI) | Endlich öffentlich für ChatGPT Plus/Pro — aber nur in USA und Kanada |
| **2024 Dez** | **Veo 2** (Google) | 4K-Auflösung, verbessertes Physikverständnis |
| **2025 Feb** | **Wan 2.1** (Alibaba/Team Wan) | Open Source! 1.3B-Modell läuft auf Consumer-GPUs (8 GB VRAM). Text, Bild und Video |
| **2025 Mai** | **Veo 3** (Google) | Der Stummfilm ist vorbei: Generiert **synchronisierten Sound** — Dialoge, Soundeffekte, Ambient |
| **2025 Sep** | **Sora 2** (OpenAI) | Zweite Generation mit iOS/Android-App und Social-Media-Features |
| **2025 Okt** | **Veo 3.1** (Google) | Neueste stabile Version, verfügbar über Gemini und Google Flow |
| **2026 Feb** | **Seedance 2.0** (ByteDance) | Ging viral — ultra-realistische Clips, Hollywood schlägt Alarm. Disney schickt Cease-and-Desist |

**Das Tempo ist atemberaubend:** Von unscharfen 4-Sekunden-Clips (2023) zu minutenlangen, fotorealistischen Videos mit Sound (2025) in nur zwei Jahren. Kein anderes KI-Feld hat sich so schnell entwickelt.

> **Bank-Analogie:** Stellen Sie sich vor, die Digitalisierung von Papierakten wäre 2023 mit Schwarz-Weiß-Scans gestartet — und zwei Jahre später scannen Sie automatisch ganze Aktenordner in Farbe, mit OCR, Indexierung und automatischer Zusammenfassung. Das ist das Tempo der Video-KI.

---

## Die Analogie: Der Daumenkino-Künstler

Stellen Sie sich einen talentierten Künstler vor. Bisher kann er ein einziges, wunderschönes Bild zeichnen — unseren Kunstrestaurator aus Tutorial 00-02. Jetzt stellen wir ihm eine neue Aufgabe: **30 Bilder pro Sekunde zeichnen**, wobei sich jedes nur minimal vom vorherigen unterscheidet. Blättert man schnell durch, entsteht eine bewegte Szene — ein Daumenkino.

Das ist im Kern, was ein Video-Modell tut. Es zeichnet nicht *ein* Bild, sondern eine **ganze Serie** von Bildern, die nahtlos ineinander übergehen wie ein Filmstreifen.

**Das Problem ist nicht, ein einzelnes Bild zu zeichnen. Das Problem ist, sicherzustellen, dass Bild 15 zu Bild 14 und Bild 16 passt.** Wenn unser Daumenkino-Künstler in einem Bild den Hut der Figur vergisst und ihn im nächsten wieder hinzeichnet, sieht das Ganze aus wie ein Glitch.

> **Bank-Analogie:** Stellen Sie sich vor, Sie erstellen eine Akte mit 30 Seiten über denselben Erbfall. Jede Seite dokumentiert einen neuen Zeitpunkt — aber die Fakten müssen über alle Seiten hinweg konsistent bleiben. Wenn auf Seite 14 der Erbe in München wohnt, darf er auf Seite 15 nicht plötzlich in Hamburg sein, ohne dass ein Umzug dokumentiert wurde. Das ist **temporale Konsistenz** — das Konzept, das alles in diesem Tutorial zusammenhält.

---

## Warum Video so viel schwieriger ist als ein Bild

Ein Bild hat zwei Dimensionen: Breite und Höhe. Ein Video fügt eine dritte hinzu: **die Zeit**. Und diese eine zusätzliche Dimension macht alles exponentiell komplexer.

| | Bild | Video (3 Sekunden, 30fps) |
|---|---|---|
| **Frames** | 1 | 90 |
| **Datenmenge** | 1× | ~90× |
| **Rechenkosten** | 1× | ~30× |
| **Herausforderung** | Aussehen stimmt | Aussehen stimmt **UND** Bewegung ist flüssig |

Branchenexperten schätzen, dass Videogenerierung für nur wenige Sekunden Footage etwa **30-mal rechenintensiver** ist als Bildgenerierung. Und das liegt nicht nur an der schieren Datenmenge — das Modell muss zusätzlich eine ganze Reihe von Regeln einhalten:

- **Objekte dürfen nicht verschwinden und wieder auftauchen.** Wenn in Frame 10 ein roter Ball links im Bild ist, darf er in Frame 11 nicht plötzlich rechts sein, ohne sich dorthin bewegt zu haben.
- **Farben, Texturen und Beleuchtung müssen konsistent bleiben.** Kein plötzlicher Farbwechsel von Frame zu Frame.
- **Bewegungen müssen physikalisch plausibel sein.** Ohren, die in Frame 10 schlackern, sollten in Frame 11 immer noch schlackern — nicht steif abstehen.

All das fasst man unter dem Begriff **temporale Konsistenz** zusammen. Sie ist die zentrale Herausforderung und das Designziel jeder Komponente eines Video-Modells.

> **Token-Kosten in der Praxis:** In Tutorial 00-01 haben Sie gelernt, dass ein deutsches Wort etwa 1,5 Tokens kostet. Ein einzelnes Bild in einem multimodalen Modell kostet ~1.000 Tokens (Tutorial 00-03). Ein 3-Sekunden-Video? Das sind 90 Frames × ~1.000 Tokens = **~90.000 Tokens** — nur um es zu *verarbeiten*. Das erklärt, warum Videogenerierung so teuer ist und die meisten Dienste strenge Längenlimits setzen.

---

## Der Bauplan: In 7 Schritten vom Bildmodell zum Filmemacher

### Schritt 1: Starte mit dem, was du hast (Transfer Learning)

Wir fangen nicht bei null an. Wir nehmen das **Diffusion-Modell aus Tutorial 00-02** — unseren „Kunstrestaurator", der verrauschte Bilder in schöne Bilder verwandelt. Dieses Modell versteht bereits Komposition, Beleuchtung, Texturen und Objekte. Warum sollten wir all dieses Wissen wegwerfen?

Die meisten hochmodernen Video-KIs machen genau das: Sie nehmen einen **vortrainierten Bildgenerator** und bringen ihm das Konzept Zeit bei. Alibabas Wan 2.1 basiert auf einem vortrainierten Bildmodell. Metas Make-A-Video hat diesen Ansatz 2022 als erstes populär gemacht.

> **Daumenkino-Analogie:** Unser Künstler kann bereits ein einzelnes wunderschönes Bild malen. Jetzt bringen wir ihm bei, einen ganzen Comic-Strip zu zeichnen. Er muss nicht neu lernen, wie man Hunde zeichnet — nur, wie sich ein laufender Hund von Frame zu Frame verändert.

Das nennt man **Transfer Learning** — vorhandenes Wissen übertragen und nur das Neue dazulernen. Es spart enorme Trainingszeit und ist der Grund, warum das Feld so schnell vorankommt.

> **Bank-Analogie:** Wenn ein neuer Sachbearbeiter in die Abteilung kommt, muss er nicht lernen, was ein Grundbuchauszug ist — das weiß er schon. Er muss nur lernen, wie die *Abläufe in dieser Bank* funktionieren. Vorwissen übertragen, nur das Neue dazulernen. Genau das ist Transfer Learning.

---

### Schritt 2: Die Datenpipeline auf Video erweitern

Unser Bildmodell hat mit einer Bibliothek einzelner Fotografien trainiert. Jetzt brauchen wir eine **Bibliothek von Filmrollen**.

Statt einzelner Bilder sammeln wir kurze Videoclips als Trainingsdaten:

- **Länge:** 2–5 Sekunden pro Clip (~60–150 Frames bei 30fps)
- **Format:** Statt einem Einzelbild liefert der Data Loader jetzt **Sequenzen** von Frames — z.B. Stapel von 8 oder 16 Frames auf einmal
- **Vielfalt:** Das Modell muss möglichst viele Arten von Bewegung sehen

Autos, die um Kurven fahren. Hunde, die rennen. Wolken, die ziehen. Wasser, das fließt. **Jedes Muster von Veränderung von Frame zu Frame wird zum Trainingssignal.** Das Modell lernt nicht einzelne Filme auswendig — es lernt die *Regeln* von Bewegung.

> **Daumenkino-Analogie:** Statt dem Künstler einzelne Gemälde zu zeigen, geben wir ihm jetzt hunderte fertige Daumenkinos zum Studieren. „Schau dir an, wie sich ein rennender Hund von Seite zu Seite verändert. Lerne das Muster."

> **Bank-Analogie:** Es ist wie Fallschulung für neue Mitarbeiter: Statt nur einzelne Dokumente zu lesen, bekommen sie **ganze Fallverläufe** — von der ersten Anfrage bis zum Abschluss. Jeder Fall zeigt, wie sich ein Vorgang über Zeit entwickelt. Genau so lernt das Videomodell Bewegung: aus ganzen Sequenzen, nicht aus Einzelbildern.

---

### Schritt 3: Raumzeit-Patches — das Video in handliche Stücke schneiden

Hier wird es clever. Wenn wir ein Video naiv als lange Liste einzelner Bilder behandeln würden, würde das Modell in Daten ertrinken. Eine Sekunde Video bei 30fps = 30 Bilder. Das sind 30-mal mehr Pixel als bei einem einzelnen Frame.

Die Lösung, populär gemacht durch OpenAIs Sora: **Das Video komprimieren und in „Raumzeit-Patches" zerschneiden.**

Statt dem Modell jeden Pixel jedes Frames zu füttern, schneiden wir das Video in kleine **3D-Würfel**:

```
Ein Raumzeit-Patch (Spacetime Patch):
┌─────────────────────────┐
│  16×16 Pixel-Region     │
│  über 4 aufeinander-    │
│  folgende Frames        │
│                         │
│  = ein kleiner 3D-Würfel│
│  aus Raum UND Zeit      │
└─────────────────────────┘
```

> **Brot-Analogie:** Stellen Sie sich einen Laib Brot vor. Statt ihn in Scheiben zu schneiden (= einzelne Frames), schneiden wir ihn in **Würfel** — jeder Würfel enthält ein Stückchen Raum UND ein Stückchen Zeit.

Diese Patches werden zu den **Tokens** (Bausteinen), mit denen das Modell arbeitet — genau wie die Text-Tokens aus Tutorial 00-01. Statt 100 riesige Seiten bekommt unser Daumenkino-Künstler einen ordentlichen Stapel kleiner **Karteikarten**, jede mit einem winzigen Ausschnitt der Handlung. Der Künstler kann diese Karten sortieren und anordnen, um das Gesamtbild zu rekonstruieren.

**Eleganter Nebeneffekt:** Da ein Bild einfach ein „Video mit einem Frame" ist, kann das Modell sowohl von Bildern als auch von Videos **einheitlich** lernen. Wan 2.1 nutzt genau diesen Ansatz: Ein einziges Modell für Text-to-Image, Image-to-Video und Text-to-Video.

> **Bank-Analogie:** Statt einen kompletten 200-Seiten-Erbfall auf einmal zu prüfen, zerlegen Sie ihn in handliche Teilakten: Grundbuch, Kontoauszüge, Stammbaumdaten, Korrespondenz. Jede Teilakte ist überschaubar. Zusammen ergeben sie das Gesamtbild. Genau so funktionieren Raumzeit-Patches.

---

### Schritt 4: Temporale Layer — die geheime Zutat

Dies ist die **große architektonische Veränderung**, die ein Videomodell von einem Bildmodell unterscheidet. Wir modifizieren unser Diffusion-Netzwerk so, dass es nicht nur schaut, **was** in jedem Frame ist (räumlicher Kontext), sondern auch, **wie sich Dinge über Frames hinweg verändern** (temporaler Kontext).

Konkret fügen wir zwei neue Arten von Schichten in das Netzwerk ein:

**1. Temporale Attention-Layer**
- Reguläre Attention in einem Bildmodell scannt nur *innerhalb* eines Frames: „Wie verhält sich der Hut zum Ball in *diesem* Bild?"
- Temporale Attention scannt *über die Zeit*: „Wie verhält sich der Hut in Frame 14 zum Hut in Frame 15?"

Erinnern Sie sich an das **Attention-Prinzip** aus Tutorial 00-01? Dort richtete das LLM seine Aufmerksamkeit auf verschiedene Wörter in einem Satz, um zu verstehen, wer mit „er" gemeint ist. Hier funktioniert es genauso — nur richtet das Videomodell seine Aufmerksamkeit auf denselben Bildbereich **über verschiedene Zeitpunkte** hinweg.

**2. 3D-Convolutional Layer (3D-Faltungsschichten)**
- Statt 2D-Filtern (Breite × Höhe) verwenden wir 3D-Filter (Breite × Höhe × Zeit)
- Diese Filter erkennen Muster, die sich über mehrere Frames erstrecken — also **Bewegungsmuster**

```
Bildmodell (nur räumlich):          Videomodell (räumlich + temporal):

Frame 14: 🎩 ← → ⚽                Frame 14: 🎩 ← → ⚽
                                         ↕         ↕
                                    Frame 15: 🎩 ← → ⚽

"Wo ist der Hut                     "Wo ist der Hut relativ zum Ball
 relativ zum Ball?"                  UND hat er sich seit letztem
                                     Frame bewegt?"
```

Durch das Hinzufügen temporaler Layer sagen wir dem Modell explizit: **„Achte darauf, was Objekte über die Zeit tun — nicht nur in einem einzelnen Schnappschuss."**

Meta AIs **Make-A-Video**-System (2022) hat genau diesen Ansatz bewiesen: Sie nahmen einen erstklassigen Bildgenerator und fügten temporale Konvolutions- und Attention-Module ein, um ihm ein Gefühl für Bewegung zu geben. Kuaishous Kling setzt auf eine **Diffusion-Transformer-Architektur**, die räumliche und temporale Attention in einem einzigen Transformer-Block vereint — statt sie als getrennte Module aufzustecken.

> **Daumenkino-Analogie:** Unser Künstler lernt jetzt nicht nur, was auf jeder Seite steht, sondern auch die **Übergänge** zwischen den Seiten. Er hat ein Auge für Kontinuität entwickelt — wie ein guter Filmcutter, der auf Anschlussfehler achtet.

> **Bank-Analogie:** Es ist wie der Unterschied zwischen einem Sachbearbeiter, der nur Einzeldokumente prüft, und einem, der den **gesamten Fallverlauf** im Blick hat. Letzterer bemerkt, wenn auf Seite 14 der Kontostand plötzlich nicht mehr zu Seite 13 passt. Temporale Attention ist diese Art von Fallüberblick — über die Zeit hinweg.

---

### Schritt 5: Training mit verrauschten Videoclips

Das Training folgt demselben **Diffusion-Paradigma** aus Tutorial 00-02 — nur erweitert über die Zeit.

**Der Prozess:**
1. Wir nehmen Videoclips
2. Wir fügen **zufälliges Rauschen zu jedem Frame** hinzu (wie einen Filmstreifen, der mit Sandpapier zerkratzt wurde)
3. Das Modell soll den **sauberen Videoclip vorhersagen**

Der entscheidende Unterschied: Dank der temporalen Layer entrauscht das Modell die Frames **nicht unabhängig voneinander**. Es lernt, die gesamte Sequenz **koordiniert** zu säubern.

```
Noisy Input:    ░░░  ░░░  ░░░  ░░░  ░░░  ░░░
                 ↓    ↓    ↓    ↓    ↓    ↓
Modell:         [═══════ koordiniertes Denoising ═══════]
                 ↓    ↓    ↓    ↓    ↓    ↓
Clean Output:   🐕💨  🐕💨  🐕💨  🐕💨  🐕💨  🐕💨
                Frame 1 → 2 → 3 → 4 → 5 → 6
                    (flüssige Bewegung)
```

Über viele Iterationen hinweg verinnerlicht das Modell die Regeln realistischer Bewegung:
- Hüte verschwinden nicht und tauchen wieder auf
- Bälle teleportieren sich nicht
- Ohren, die in Frame 10 schlackern, schlackern auch in Frame 11

Am Ende des Trainings: Füttern Sie das Modell mit zufälligem Rauschen für eine Sequenz von Frames — und es generiert einen **flüssigen, kohärenten Mini-Film**.

> **Bank-Analogie:** Stellen Sie sich einen Revisor vor, der nicht nur einzelne Buchungen prüft, sondern den **gesamten Kontoverlauf** auf einmal analysiert. Er erkennt sofort, wenn eine Zahlung nicht zur vorherigen und nächsten Buchung passt. Das koordinierte Denoising arbeitet genauso — es prüft alle Frames gleichzeitig auf Konsistenz.

---

### Schritt 6: Text-Conditioning — dem Filmemacher ein Drehbuch geben

Genau wie DALL-E Text nimmt, um die Bildgenerierung zu steuern (Tutorial 00-02, Abschnitt Cross-Attention), erweitern wir dieselbe Idee auf Video. Aber das Conditioning ist **reichhaltiger**: Der Text beschreibt nicht nur eine Szene, sondern eine **Handlung**.

| Bild-Prompt | Video-Prompt |
|---|---|
| „Ein Hund auf einer Wiese" | „Ein Hund **rennt** durch eine Wiese" |
| „Ein roter Ball auf einem Tisch" | „Ein roter Ball **springt** auf einem Tisch" |
| „Wellen am Strand" | „Wellen **brechen** sich an Felsen bei Sonnenuntergang" |

**So funktioniert das Training:**
1. Jeder Trainings-Videoclip wird mit einer **Beschreibung der Handlung** gepaart
2. Ein Text-Embedding (→ Tutorial 00-01, Baustein 3) wird dem Modell bei jedem Denoising-Schritt **mitgefüttert**
3. Das Modell lernt, Wörter mit **visueller Dynamik** zu verknüpfen

Wenn der Prompt „ein Hund rennt" sagt, soll das Modell keinen Hund produzieren, der in einem Frame steht und im nächsten verschwunden ist. Es soll die **vollständige Laufsequenz** erzeugen — mit Beinen in Bewegung und Boden, der unter den Pfoten vorbeigleitet.

**Kreative Datenstrategien der großen Anbieter:**
- **OpenAI (Sora):** Generierte Beschreibungen für unbeschriftete Videos mithilfe eines KI-Captioners
- **Meta (Make-A-Video):** Trainierte auf Bild-Text-Paaren für Inhaltsverständnis UND auf unbeschrifteten Videos für Bewegungsverständnis — dann wurden beide Fähigkeiten kombiniert
- **Google (Veo 3):** Ging noch weiter und trainierte gleichzeitig auf Audio — so dass das Modell nicht nur passende Bilder, sondern auch **passenden Sound** zu einem Prompt erzeugt

> **Bank-Analogie:** Es ist wie der Unterschied zwischen „Erstellen Sie ein Kontoblatt" und „Erstellen Sie die Kontohistorie für Q1 2026 mit allen Ein- und Ausgängen, chronologisch sortiert". Der Video-Prompt liefert dem Modell ein **Drehbuch** — mit Handlung, Bewegung und zeitlichem Ablauf.

---

### Schritt 7: Auf längere Videos skalieren

Bis hierhin generiert unser Modell ein paar Sekunden Video. Aber was ist mit einem **30-Sekunden-Clip bei 60fps**? Das wären 1.800 kohärente Frames auf einmal — absurd teuer.

Zwei Strategien machen längere Videos praktikabel:

#### Strategie A: Autoregressive Chunking (Kapitelweise)

```
Chunk 1          Chunk 2          Chunk 3
[Frame 1-90]  →  [Frame 85-180] →  [Frame 175-270]
                  ↑                  ↑
            letzte Frames      letzte Frames
            als Kontext        als Kontext
```

Das Video wird **stückweise** generiert. Erst 3 Sekunden. Dann werden die letzten Frames als Startkontext verwendet, um die nächsten 3 Sekunden zu erzeugen. Die Segmente werden wie **Kapitel eines Daumenkinos** aneinandergekettet. Das Modell „erinnert sich" an den Zustand, indem es das Ende des vorherigen Segments als Ausgangspunkt nimmt.

#### Strategie B: Hierarchische Generierung (Keyframes + Interpolation)

```
Schritt 1: Keyframes generieren (1 pro Sekunde)
[K1]─────────[K2]─────────[K3]─────────[K4]

Schritt 2: Lücken interpolieren
[K1]▸▸▸▸▸▸▸▸[K2]▸▸▸▸▸▸▸▸[K3]▸▸▸▸▸▸▸▸[K4]
    29 Frames     29 Frames     29 Frames
```

Erst werden **sparse Keyframes** für das gesamte Video generiert — ein Frame pro Sekunde. Diese Anker-Frames erfassen die großen Veränderungen. Dann füllt ein **Interpolationsmodell** die Lücken zwischen den Keyframes mit flüssigen Übergängen.

Metas Make-A-Video nutzte genau diesen Ansatz: Erst ein Video in niedriger Auflösung und Frame-Rate generieren, dann spezialisierte Modelle für temporale Interpolation und räumliches Upscaling. **Durch die Aufteilung des Problems bleibt jede Teilaufgabe handhabbar.**

Wan 2.1 bietet sogar einen **First-Last-Frame-to-Video-Modus (FLF2V)**: Sie geben dem Modell das erste und letzte Bild, und es generiert alle Frames dazwischen. Das ist hierarchische Generierung auf die Spitze getrieben.

> **Bank-Analogie:** Denken Sie an die Quartalsberichte einer großen Akte. Sie können nicht 365 Tagesberichte auf einmal erstellen — aber Sie können erst die **4 Quartalsberichte** als Ankerpunkte schreiben (= Keyframes) und dann die Monats- und Tagesberichte dazwischen ausfüllen (= Interpolation). So bleibt jede Teilaufgabe überschaubar, und das Gesamtbild ist konsistent.

---

## Sonderfall: Audio-Generierung (Veo 3 und das Ende des Stummfilms)

Ein Meilenstein, der besondere Erwähnung verdient: **Google Veo 3** (Mai 2025) war das erste große Modell, das nicht nur Video, sondern gleichzeitig **synchronisierten Sound** generiert — Dialoge, Soundeffekte und Hintergrundgeräusche, passend zur Szene.

Google-DeepMind-CEO Demis Hassabis beschrieb es so: *„Dies ist der Moment, in dem die KI-Videogenerierung die Ära des Stummfilms verlässt."*

Technisch funktioniert das ähnlich wie bei multimodalen Modellen (Tutorial 00-03): Das Modell lernt gleichzeitig die Beziehung zwischen Text, Bild, Bewegung und Ton. Wenn eine Tür zuschlägt, weiß es, dass ein „Bumm" dazugehört — weil es tausende Videos gesehen hat, in denen das passiert.

> **Warum das wichtig ist:** Für die Praxis bedeutet das, dass Sie bei Diensten wie Veo 3 nicht mehr separat einen Soundtrack erstellen müssen. Ein Prompt wie „ein Pianist spielt Chopin in einem leeren Saal" erzeugt sowohl die Szene als auch die Musik.

---

## Die aktuelle Modell-Landschaft (Stand: Februar 2026)

| Modell | Hersteller | Max. Länge | Auflösung | Besonderheit | Zugang |
|--------|-----------|------------|-----------|--------------|--------|
| **Sora 2** | OpenAI | ~1 min | bis 1080p | Social-Media-Integration, iOS/Android-App | ChatGPT Plus/Pro (USA + Kanada) |
| **Veo 3.1** | Google DeepMind | ~8 sec/Clip | bis 4K | Audio-Generierung, Google Flow als Video-Editor | Gemini-Abo, Google Flow |
| **Kling** | Kuaishou | ~2 min | 1080p, 30fps | Diffusion-Transformer, sehr lange Clips | klingai.com (kostenlos + Abo) |
| **Wan 2.1** | Alibaba / Team Wan | ~5 sec (lokal) | bis 1080p | **Open Source**, läuft auf RTX 4090 (8 GB VRAM), Bild+Video+Audio+Text | Hugging Face, ComfyUI |
| **Seedance 2.0** | ByteDance | ~8 sec | 1080p+ | Ultra-realistisch, Image-to-Video, ging viral Feb 2026 | CapCut/Jianying (Douyin-ID nötig) |

### Was unterscheidet die Modelle?

**Sora 2** setzt auf maximale Länge und eine Social-Media-Plattform — OpenAI will, dass Nutzer Sora-Videos direkt teilen.

**Veo 3.1** ist der einzige große Dienst mit **synchronem Audio** — und Googles Flow-Editor ermöglicht es, mehrere Clips zu einem längeren Projekt mit konsistenten Charakteren zusammenzusetzen.

**Kling** punktet mit der längsten Clip-Dauer (bis zu 2 Minuten) und nutzt eine **Diffusion-Transformer-Architektur**, die räumliche und temporale Attention elegant verschmilzt.

**Wan 2.1** ist der **Open-Source-Champion**: Das 1.3B-Modell läuft auf Consumer-Hardware und kann sogar chinesischen und englischen Text im Video generieren. Es ist das erste Videomodell, das wirklich auf „normalen" Grafikkarten funktioniert.

**Seedance 2.0** von ByteDance ist das jüngste Modell und hat im Februar 2026 für Aufsehen gesorgt. Die Qualität ist beeindruckend, aber die Verfügbarkeit ist eingeschränkt (aktuell nur über die chinesische Plattform Jianying/CapCut). Disney und Paramount haben bereits Urheberrechtsklagen angekündigt.

---

## Limitationen: Was Video-KI (noch) nicht kann

Trotz der beeindruckenden Fortschritte haben alle aktuellen Modelle gemeinsame Schwächen:

### Physik und Logik
- **Hände und Finger** werden oft falsch dargestellt — zu viele, zu wenige, oder unnatürlich verdreht
- **Texteinblendungen** im Video sind meist unleserlich oder unsinnig (Wan 2.1 ist hier die Ausnahme)
- **Komplexe Physik** wie Flüssigkeiten, Rauch oder Haare gelingen nicht immer konsistent
- **Ursache und Wirkung** werden oft ignoriert — ein Ball, der aufprallt, erzeugt nicht immer eine plausible Reaktion

### Temporale Probleme
- **Gesichter morphen** bei längeren Clips — eine Person sieht in Sekunde 3 anders aus als in Sekunde 1
- **Objekte teleportieren** sich gelegentlich — der berüchtigte „Glitch"
- **Konsistenz über Szenen hinweg** ist das größte ungelöste Problem: Wenn Sie einen Charakter in mehreren Szenen wollen, sieht er jedes Mal anders aus

### Praktische Grenzen
- **Generierungszeit:** Ein 5-Sekunden-Clip dauert Minuten bis Stunden — weit von Echtzeit entfernt
- **Kosten:** Professionelle Nutzung schlägt schnell mit 50–200 € pro Monat zu Buche
- **Prompt-Verständnis:** Die Modelle verstehen komplexe Prompts oft falsch — je einfacher und spezifischer, desto besser
- **Inhaltsbeschränkungen:** Alle kommerziellen Dienste haben strenge Content-Filter (Google Veo ist besonders restriktiv)

> **Bank-Analogie:** Stellen Sie sich vor, Sie hätten einen KI-Assistenten, der automatisch Kundenanschreiben formuliert. Er macht 95% richtig — aber gelegentlich taucht der falsche Kundenname auf, oder der Kontostand stimmt nicht. Würden Sie das ohne Prüfung rausschicken? Natürlich nicht. Genauso sollten Sie KI-generierte Videos immer **überprüfen und nachbearbeiten**, bevor Sie sie verwenden.

---

## Wie das Ihr Prompting beeinflusst

Auch wenn Sie selbst kein Video-Modell bauen, hilft dieses Wissen beim **Schreiben besserer Video-Prompts:**

### 1. Beschreiben Sie Handlungen, nicht nur Szenen
Ein Video-Prompt braucht **Verben**: „rennt", „springt", „dreht sich". Das Modell wurde darauf trainiert, Wörter mit Bewegungsdynamik zu verknüpfen. „Ein Hund auf einer Wiese" ergibt ein Standbild. „Ein Hund rennt durch eine Wiese" ergibt ein Video.

### 2. Nutzen Sie Kamera-Sprache
Die Modelle wurden mit Filmclips trainiert, die Kamerabeschreibungen enthielten. Nutzen Sie Begriffe wie:
- **„Slow-motion"** — für verlangsamte Bewegungen
- **„Kamerafahrt von links nach rechts"** — für Schwenks
- **„Nahaufnahme"** / **„Totale"** — für Bildausschnitte
- **„Drohnenaufnahme"** — für Luftperspektiven

### 3. Halten Sie lange Clips einfach
Autoregressive Chunking kann zu **Drift** führen — je länger das Video, desto wahrscheinlicher weichen Details ab. Bei langen Prompts: Konzentrieren Sie sich auf eine klare Handlung statt auf viele Details.

### 4. Denken Sie in Keyframes
Wenn Sie beschreiben, was am Anfang, in der Mitte und am Ende passieren soll, geben Sie dem Modell natürliche **Ankerpunkte** — ähnlich wie bei der hierarchischen Generierung.

### 5. Iterieren Sie
Alle aktuellen Dienste brauchen oft 2–3 Versuche, bis das Ergebnis passt. Das ist normal. **Trial-and-Error** ist kein Zeichen von Inkompetenz, sondern die aktuelle Realität der Technologie.

---

## 🔬 Probieren Sie es selbst!

**Übung 1: Bildprompt vs. Videoprompt (5 Minuten)**

Öffnen Sie einen der kostenlosen Video-Generatoren (z.B. klingai.com oder den Gemini-Bildgenerator mit Video-Option).

1. Geben Sie zuerst einen **statischen** Prompt ein: *„Ein Bankangestellter sitzt an einem Schreibtisch"*
2. Dann einen **dynamischen** Prompt: *„Ein Bankangestellter steht von seinem Schreibtisch auf, nimmt eine Akte aus dem Regal und legt sie auf den Tisch"*

Vergleichen Sie die Ergebnisse. Sehen Sie, wie Verben das Modell zum Filmemachen bringen?

**Übung 2: Kamera-Sprache ausprobieren (5 Minuten)**

Nehmen Sie denselben dynamischen Prompt und fügen Sie Kameraanweisungen hinzu:

- Version A: *„...Nahaufnahme, weiches Licht"*
- Version B: *„...Totale, Kamerafahrt folgt der Person"*

Beobachten Sie, wie die Kamerabeschreibung den Stil des Videos komplett verändert.

**Übung 3: Temporale Konsistenz testen (5 Minuten)**

Generieren Sie einen Clip einer Person, die einen bestimmten Gegenstand hält (z.B. „eine Frau hält ein rotes Buch und geht durch einen Flur"). Achten Sie darauf:
- Bleibt das Buch rot?
- Bleibt es in der Hand?
- Verändert sich das Gesicht der Person?

Sie werden wahrscheinlich mindestens einen dieser Fehler sehen — und jetzt wissen Sie, warum: **temporale Konsistenz** ist die härteste Herausforderung.

---

## Parallelen zu vorherigen Tutorials

| Konzept | Tutorial | Verbindung |
|---------|----------|------------|
| **Tokens** | 00-01 (LLMs) | Raumzeit-Patches sind die Video-Tokens — analog zu Wort-Tokens bei LLMs |
| **Attention** | 00-01 (LLMs) | Temporale Attention funktioniert genau wie Self-Attention, nur über die Zeitachse |
| **Diffusion / Denoising** | 00-02 (Diffusion) | Exakt dasselbe Prinzip — nur auf Videosequenzen statt Einzelbilder angewandt |
| **Cross-Attention / CLIP** | 00-02 (Diffusion) | Text-Conditioning im Video funktioniert identisch wie bei Text-to-Image |
| **Multimodalität** | 00-03 (Multimodal) | Veo 3 verbindet Text + Bild + Bewegung + Audio in einem Modell — Multimodalität in Reinform |
| **Token-Kosten** | 00-01 (LLMs) | Video = ~90.000 Tokens pro 3 Sekunden, daher die enormen Rechenkosten |

**Der rote Faden:** Jede Technologie baut auf der vorherigen auf. LLMs lernten Text vorherzusagen. Diffusion-Modelle lernten Bilder zu entrauschen. Multimodale Modelle verbanden beides. Und Videomodelle nehmen all das und fügen die Zeitdimension hinzu. **Die Grundprinzipien — Attention, Tokens, Diffusion — sind immer dieselben.** Nur der Canvas wird größer.

---

## Das Wichtigste auf einen Blick

| Erkenntnis | Details |
|---|---|
| **Video = Bild + Zeit** | Die eine zusätzliche Dimension macht alles ~30× teurer und schwieriger |
| **Temporale Konsistenz ist alles** | Das gesamte Design — von temporalen Layern bis zu Raumzeit-Patches — dreht sich darum |
| **Baue auf Bestehendem auf** | Vortrainierte Bildmodelle + temporale Erweiterungen = Transfer Learning |
| **Das Diffusion-Paradigma skaliert** | Noise → Denoise funktioniert identisch, nur über die Zeit erweitert |
| **Audio kommt dazu** | Veo 3 markiert das Ende des KI-Stummfilms — Sound wird Teil des Modells |
| **Open Source holt auf** | Wan 2.1 bringt State-of-the-Art auf Consumer-Hardware |
| **Rechenkosten sind der Flaschenhals** | Spacetime-Patches und hierarchische Generierung existieren genau deshalb |
| **Prompting ist eine Fertigkeit** | Verben, Kamera-Sprache und Einfachheit machen den Unterschied |

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Temporale Konsistenz** | Die Eigenschaft, dass Objekte, Farben und Physik über alle Frames eines Videos hinweg stimmig bleiben — kein Flackern, kein Teleportieren |
| **Raumzeit-Patch (Spacetime Patch)** | Ein kleiner 3D-Würfel aus Pixeln (z.B. 16×16 Pixel über 4 Frames), der als Token für das Videomodell dient |
| **Temporale Attention** | Ein Attention-Mechanismus, der nicht nur innerhalb eines Frames schaut, sondern über die Zeitachse hinweg — „Was macht dieses Objekt über mehrere Frames?" |
| **3D-Convolution (3D-Faltung)** | Ein Filter, der Muster in drei Dimensionen erkennt (Breite × Höhe × Zeit) — spezialisiert auf Bewegungserkennung |
| **Transfer Learning** | Ein vortrainiertes Modell (z.B. Bildgenerator) als Basis nehmen und nur die neuen Fähigkeiten (z.B. Bewegung) dazulernen |
| **Autoregressive Chunking** | Video in kurzen Abschnitten generieren, wobei das Ende des vorherigen Abschnitts als Kontext für den nächsten dient |
| **Hierarchische Generierung** | Erst wenige Keyframes generieren, dann die Lücken interpolieren — teile und herrsche |
| **Keyframe** | Ein einzelner Anker-Frame, der den Zustand des Videos zu einem bestimmten Zeitpunkt definiert |
| **Interpolation** | Das Auffüllen der Frames zwischen Keyframes mit flüssigen Übergängen |
| **Text-Conditioning** | Die Steuerung der Videogenerierung durch einen Text-Prompt, der als Embedding in den Denoising-Prozess einfließt |
| **Diffusion-Transformer (DiT)** | Eine neuere Architektur (genutzt von Sora, Kling), die den Transformer aus Tutorial 00-01 direkt als Backbone des Diffusion-Modells verwendet |
| **FLF2V (First-Last-Frame-to-Video)** | Ein Modus bei Wan 2.1, bei dem erstes und letztes Bild vorgegeben werden und das Modell alle Frames dazwischen generiert |

---

