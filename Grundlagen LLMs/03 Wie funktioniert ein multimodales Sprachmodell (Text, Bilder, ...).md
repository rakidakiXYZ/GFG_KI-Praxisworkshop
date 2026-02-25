# Wie Multimodale Modelle funktionieren

**Wenn Text, Bild und mehr in einem KI-Gehirn zusammenkommen — verständlich erklärt**

---

## Warum dieses Tutorial?

In den letzten beiden Tutorials haben Sie zwei Spezialisten kennengelernt: LLMs, die Text verstehen und erzeugen, und Diffusion-Modelle, die Bilder aus Rauschen erschaffen. Beide sind beeindruckend — aber jeder kann nur *eine* Sache.

Sie kennen aber sicher auch KI-Systeme, die **beides gleichzeitig** können: Sie laden ein Foto hoch und die KI beschreibt, was darauf zu sehen ist. Oder Sie tippen eine Beschreibung ein und bekommen ein passendes Bild zurück. ChatGPT, Gemini und Claude können das alles in einem Gespräch.

Wie funktioniert das? Wie bringt man ein Text-Gehirn und ein Bild-Gehirn dazu, **zusammenzuarbeiten**?

Die überraschende Antwort: **Man nimmt zwei Spezialisten und verbindet sie mit etwas cleverem Klebstoff.**

**Was Sie nach diesem Tutorial wissen werden:**

- Was ein multimodales Modell ist und warum es funktioniert
- Wie man Text und Bilder in eine gemeinsame „Sprache" übersetzt
- Welche Rolle Text-Encoder, Vision-Encoder und Projektionsschichten spielen
- Wie Contrastive Learning die Brücke zwischen den Welten baut
- Wie Cross-Attention Text und Bild im selben Satz verarbeitet
- Wie das Ganze zum fertigen System zusammengebaut und trainiert wird
- Welche aktuellen multimodalen Modelle es gibt und was sie können

---

## Die Analogie: Das zweisprachige Kind

Stellen Sie sich ein Kind vor, das lesen, zeichnen und Musik hören kann — alles gleichzeitig. Zeigen Sie ihm ein Foto von einem Hund und es sagt „Hund." Sagen Sie „Hund" und es zeichnet einen. Es versteht, dass ein Foto von einem Hund, das Wort „Hund" und das Geräusch „Wuff" alle auf dasselbe Konzept zeigen.

**Das ist ein multimodales Modell in einem Satz.** Eine KI, die verschiedene Arten von Information — sogenannte **Modalitäten** — gleichzeitig verarbeiten kann. Text, Bilder, Audio, Video — jede Modalität hat ihr eigenes „Alphabet": Buchstaben für Text, Pixel für Bilder, Schallwellen für Audio.

Die meisten KI-Modelle sind Spezialisten: Eines liest Text, ein anderes betrachtet Bilder. Ein multimodales Modell ist ein **Generalist**, der mehrere Datensprachen spricht. Und das wirklich Beeindruckende: Es weiß, dass 🚗 (ein Bild eines Autos), „Auto" (das Wort) und *brumm* (das Geräusch) alle dasselbe meinen.

> **Bank-Analogie:** Stellen Sie sich eine erfahrene Sachbearbeiterin vor, die gleichzeitig einen Brief lesen, ein Foto des Absenders betrachten und eine Sprachnotiz abhören kann — und sofort versteht, dass alles zum selben Vorgang gehört. Das ist multimodal.

---

## Warum funktioniert das überhaupt? — Alles wird zu Zahlen

Hier kommt die Schlüsselerkenntnis, die multimodale KI überhaupt möglich macht:

**Unter der Haube können wir alles — Wörter, Bilder, Klänge — in dieselbe Art von numerischer Darstellung umwandeln.**

Sobald alles in **Vektoren** (Listen von Zahlen) umgewandelt ist, sieht das Modell nur noch Zahlen. Es ist ihm egal, ob diese Zahlen ursprünglich von einem Foto oder einem Satz stammen.

Stellen Sie sich einen **universellen Übersetzungsraum** vor. Jede Information, die hineinkommt, wird in ein gemeinsames Format konvertiert. In diesem Raum werden ein Foto einer Katze, das geschriebene Wort „Katze" und ein Miau-Geräusch alle in dieselbe Sprache übersetzt. Wie drei Menschen, die verschiedene Sprachen sprechen, aber alle ins Deutsche übersetzt wurden — jetzt stehen sie nebeneinander und stimmen überein, dass sie dasselbe meinen.

Das ist ein **Shared Embedding Space** — ein gemeinsamer Einbettungsraum. Ein mathematischer Raum, in dem Daten aus verschiedenen Modalitäten als vergleichbare Vektoren nebeneinander existieren.

> **Erinnern Sie sich?** In Tutorial 00-01 haben wir gelernt, wie LLMs Wörter in Vektoren umwandeln (Embeddings). In Tutorial 00-02 haben wir gesehen, wie CLIP Text und Bilder in einen gemeinsamen Raum bringt. Genau dieses Prinzip wird hier zum Fundament des gesamten Systems.

---

## Die Bausteine: Schritt für Schritt zum multimodalen Modell

### Schritt 1: Die Modalitäten wählen — Klein anfangen

Bevor man ein multimodales Modell baut, entscheidet man: Welche Modalitäten sollen es sein? Wir starten mit den zwei häufigsten: **Text und Bilder**.

Stellen Sie sich das wie einen zweisprachigen Übersetzer vor. Wenn Sie irgendwann Englisch, Französisch und Spanisch beherrschen wollen, fangen Sie nicht mit allen drei gleichzeitig an. Sie meistern erst Englisch und Französisch, und fügen Spanisch später hinzu.

Genauso machen es multimodale Modelle: **Erst Text + Bild**, dann eventuell Audio, Video oder andere Modalitäten dazu. Der Grund ist auch praktisch — es gibt riesige Datensätze mit Bild-Text-Paaren (Millionen von Bildern mit Beschreibungen), die perfekt zum Training geeignet sind.

**Unser Plan:** Ein Modell bauen, das Bilder sehen und Text lesen kann — und beide Welten verbinden.

---

### Schritt 2: Das Text-Gehirn bauen — Der „Lese-Spezialist"

Wir brauchen eine Komponente, die Text versteht und in eine Form bringt, mit der der Rest des Modells arbeiten kann. Das ist der **Text-Encoder**.

Im Kern ist das ein Transformer-Sprachmodell (wie in Tutorial 00-01 beschrieben), das Wörter bzw. Tokens liest und sie in eine bedeutungsvolle Vektor-Darstellung umwandelt. In einfachen Worten: Es nimmt einen Satz wie „ein Hund jagt einen Ball" und gibt eine Liste von Zahlen aus (einen Embedding-Vektor), die den Kern dieses Satzes einfängt.

Das multimodale Gehirn kann nicht direkt mit Buchstaben arbeiten — es braucht Zahlen. Der Text-Encoder ist der **Übersetzer von Sprache in Mathematik**.

> **Analogie:** Stellen Sie sich ein deutschsprachiges Kind vor, das jede Geschichte, die Sie ihm erzählen, in ein paar Schlüsselideen zusammenfassen kann. Das ist unser Text-Encoder: Er hört Wörter und erstellt eine Vektor-Zusammenfassung.

In der Praxis nimmt man hier oft ein **vortrainiertes Sprachmodell** — etwa GPT, LLaMA oder Vicuna — und nutzt es als Text-Encoder. Warum das Rad neu erfinden, wenn das Modell bereits fließend „Text spricht"?

---

### Schritt 3: Das Bild-Gehirn bauen — Der „Seh-Spezialist"

Jetzt brauchen wir das Gegenstück für Bilder. Der **Vision-Encoder** betrachtet ein Bild und wandelt es in einen bedeutungsvollen Vektor (oder eine Reihe von Vektoren) um.

Aber es gibt ein Problem: Transformer erwarten **Sequenzen** als Eingabe — wie Sätze aus Tokens. Wie füttert man ein Bild (ein Raster aus Pixeln) in etwas, das eine Reihenfolge erwartet?

**Der Trick: Das Bild in Stücke schneiden und jedes Stück wie ein Token behandeln.**

Stellen Sie sich vor, Sie teilen ein Bild in ein 14×14-Raster aus Kacheln auf. Das ergibt 196 Kacheln. Jede Kachel ist ein kleines Stück, sagen wir 16×16 Pixel. Wir verwandeln jede Kachel in einen Vektor, und schon haben wir **196 „visuelle Tokens"** — genau wie 196 Wörter in einem Satz.

```
┌────┬────┬────┬────┬─ ─ ─┬────┐
│ P1 │ P2 │ P3 │ P4 │     │P14 │   ← Zeile 1: 14 Patches
├────┼────┼────┼────┼─ ─ ─┼────┤
│P15 │P16 │P17 │P18 │     │P28 │   ← Zeile 2
├────┼────┼────┼────┼─ ─ ─┼────┤
│    │    │    │    │     │    │
┊    ┊    ┊    ┊    ┊     ┊    ┊   ... insgesamt 14×14
│    │    │    │    │     │    │
├────┼────┼────┼────┼─ ─ ─┼────┤
│    │    │    │    │     │P196│   ← Zeile 14
└────┴────┴────┴────┴─ ─ ─┴────┘

Jeder Patch → Vektor → „Visuelles Token"
= Sequenz von 196 Tokens für den Transformer
```

Eine Kachel zeigt vielleicht einen Teil einer Hundeschnauze, eine andere den Himmel im Hintergrund. Der **Vision Transformer (ViT)** verarbeitet diese Sequenz mit Self-Attention — genau wie ein LLM Wörter verarbeitet — und lernt die Beziehungen zwischen den Kacheln. Er erkennt: „Diese Kacheln mit Schnurrhaaren und jene Kacheln mit Spitzohren gehören zur selben Katze."

Am Ende erhalten wir ein **Image-Embedding** — einen Vektor, der den gesamten Bildinhalt repräsentiert. Das Bild-Gehirn kann keine Buchstaben lesen, aber es kann Bilder „lesen" und verstehen.

> **Die Parallele:** Der Text-Encoder wandelt Wörter in Vektoren um. Der Vision-Encoder wandelt Bildkacheln in Vektoren um. Beide sprechen am Ende dieselbe Sprache: **Zahlen**.

---

### Schritt 4: Die Projektionsschicht — Der Adapterstecker

Jetzt haben wir zwei separate Gehirne. Eines produziert Text-Vektoren, eines produziert Bild-Vektoren. Aber sprechen sie wirklich **exakt dieselbe Sprache**?

Nicht unbedingt. Der Text-Encoder könnte Vektoren einer bestimmten Größe oder Skalierung produzieren, und der Vision-Encoder Vektoren einer ganz anderen. Selbst wenn ein Konzept wie „Hund" in beiden vorkommt, landet es nicht automatisch an derselben Stelle im Zahlenraum.

Wir brauchen einen **Adapterstecker** — die **Projektionsschicht** (Projection Layer).

> **Analogie:** Wenn das Text-Gehirn mit „110 Volt" arbeitet und das Bild-Gehirn mit „220 Volt", dann ist die Projektionsschicht der Reiseadapter, der beide auf dieselbe Steckdose bringt.

Technisch ist das oft erstaunlich einfach: eine **lineare neuronale Schicht** (eine Matrixmultiplikation), die die Ausgabe des Vision-Encoders nimmt und in den Vektorraum des Text-Encoders abbildet.

Das **LLaVA-Modell** (2023) hat genau das gemacht: Es nahm einen vortrainierten CLIP-ViT-Bildencoder und ein vortrainiertes Vicuna-Sprachmodell und setzte dazwischen eine einfache lernbare lineare Projektion. Mehr nicht.

```
Bild-Vektor          Projektionsschicht         Text-Vektorraum
(Vision-Encoder)         (Adapter)              (gemeinsamer Raum)

[0.8, 0.2, ...]  ───→  W × v + b  ───→  [0.3, 0.7, 0.1, ...]
  (768 Dim.)         (lernbare Matrix)       (4096 Dim.)
```

Während des Trainings werden die Parameter dieser Schicht so angepasst, dass ein Bild eines Hundes, einmal projiziert, **sehr nah** am Embedding für das Wort „Hund" landet. Nicht-passende Paare sollen dagegen weit auseinander liegen.

---

### Schritt 5: Contrastive Learning — Das Magnetspiel

Jetzt kommt der spannende Teil: Wie bringt man dem System bei, dass ein Foto eines Hundes tatsächlich zum Wort „Hund" gehört?

Dafür nutzt man **Contrastive Learning** — kontrastives Lernen. Es funktioniert wie ein **Magnetspiel**:

1. **Sammle einen großen Datensatz** aus Bild-Text-Paaren (Fotos mit passenden Beschreibungen) — das sind die Lernkarten
2. **Verarbeite einen Stapel** von z.B. 1000 Paaren gleichzeitig
3. **Berechne die Ähnlichkeit** zwischen *jedem* Bild-Vektor und *jedem* Text-Vektor im Stapel
4. **Für echte Paare:** Ähnlichkeit soll hoch sein (Magnete ziehen sich an)
5. **Für falsche Kombinationen:** Ähnlichkeit soll niedrig sein (Magnete stoßen sich ab)
6. **Passe die Parameter an**, um in diese Richtung zu optimieren

```
                    Text 1 ✓    Text 2 ✗    Text 3 ✗    Text 4 ✗
                   „Hund"     „Auto"     „Strand"    „Büro"
                 ┌──────────┬──────────┬──────────┬──────────┐
Bild 1 (Hund)   │  0.95 ✓  │  0.02    │  0.05    │  0.01    │
                 ├──────────┼──────────┼──────────┼──────────┤
Bild 2 (Auto)   │  0.03    │  0.93 ✓  │  0.08    │  0.04    │
                 ├──────────┼──────────┼──────────┼──────────┤
Bild 3 (Strand) │  0.06    │  0.04    │  0.91 ✓  │  0.02    │
                 ├──────────┼──────────┼──────────┼──────────┤
Bild 4 (Büro)   │  0.01    │  0.07    │  0.03    │  0.94 ✓  │
                 └──────────┴──────────┴──────────┴──────────┘

Ziel: Diagonale hoch (echte Paare), Rest niedrig (falsche Paare)
```

Am Anfang weiß das Modell nichts — es hält zufällige Kombinationen für richtig. Aber über Millionen von Trainingsrunden erkennt es Muster: Eine bestimmte Dimension im Bild-Vektor schlägt immer dann stark aus, wenn in der passenden Beschreibung das Wort „Hund" vorkommt. Das System passt sich an, um diese Signale besser auszurichten.

Am Ende entsteht ein echter **gemeinsamer Einbettungsraum** (Shared Embedding Space). Ein neues Bild einer Katze und das Wort „Katze" produzieren nahe beieinanderliegende Vektoren. Das Wort „Hund" liegt weit vom Katzen-Bild-Vektor entfernt.

> **Das ist genau das, was OpenAIs CLIP mit 400 Millionen Bild-Text-Paaren gelernt hat.** Und es funktioniert erstaunlich gut — CLIP kann Bilder klassifizieren, die es nie gesehen hat, einfach indem es prüft, welches Textetikett den ähnlichsten Vektor ergibt.

---

### Schritt 6: Anbindung ans LLM — Einen Comic lesen

Wir haben jetzt zwei aufeinander abgestimmte Encoder. Aber was, wenn wir wollen, dass unser Modell **Fragen über Bilder beantwortet** oder einen Dialog mit visuellem Kontext führt? Dann müssen wir unser visuelles Verständnis an einen **Textgenerator** anschließen — ein Large Language Model, das Bild-Embeddings aufnehmen und Text erzeugen kann.

**Der Ansatz:** Bild-Informationen dem Sprachmodell so zuführen, als wären sie einfach **weitere „Wörter" in einer Sequenz**.

> **Analogie:** Stellen Sie sich ein zweisprachiges Kind vor, das einen **Comic** liest. Statt nur Worte oder nur Bilder sieht es Bilder, Bildunterschriften, Sprechblasen — alles ineinander verwoben in einer Geschichte. Unser multimodales Modell macht genau das.

Eine Eingabe könnte so aussehen:

```
┌─────────────────────────────────────────────────────────────┐
│  <BildStart>  [Bild-Token 1] [Bild-Token 2] ... [Bild-     │
│   Token 196]  <BildEnde>                                     │
│                                                              │
│  „Was ist auf diesem Bild zu sehen?"                         │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
                    ┌──────────────┐
                    │     LLM      │
                    │  verarbeitet │
                    │  Bild-Tokens │
                    │  + Text-     │
                    │  Tokens      │
                    │  gemeinsam   │
                    └──────┬───────┘
                           │
                           ▼
            „Ein Hund jagt einen Ball auf
             einer grünen Wiese."
```

Das Bild wird durch den Vision-Encoder und die Projektionsschicht geschickt, um **visuelle Tokens** zu erhalten. Diese werden dem LLM als zusätzliche Tokens vorangestellt — vor der eigentlichen Textfrage. Das LLM verarbeitet diese gemischte Sequenz aus Bild-Tokens und Wort-Tokens zusammen.

#### Cross-Attention: Die Brücke zwischen Sehen und Lesen

Im Inneren des LLM geschieht die eigentliche Magie durch **Cross-Attention** — ein Mechanismus, den Sie bereits aus Tutorial 00-02 kennen (dort verbindet er Text mit der Bildgenerierung bei Diffusionsmodellen).

Cross-Attention lässt eine Sequenz eine andere nach relevanten Informationen **befragen**. Es ist, als würde der Text-Teil des Modells den Bild-Teil fragen:

*„Hey, ich lese gerade die Frage ‚Worauf sitzt die Katze?' — kannst du mir sagen, was unter der Katze im Bild ist?"*

Und der Bild-Teil antwortet, indem er die relevante Region hervorhebt: *„Ein Sofa."*

```
Text-Tokens:   „Worauf"  „sitzt"  „die"  „Katze"  „?"
                   │         │       │       │       │
                   └────┬────┘       └───┬───┘       │
                        │                │           │
              ┌─────────▼────────────────▼───────────▼─────────┐
              │              Cross-Attention                     │
              │   Text fragt Bild: „Was ist relevant?"          │
              └─────────┬───────────────────────────────────────┘
                        │
Bild-Tokens:  [Kachel  [Kachel  [Kachel  [Kachel  [Kachel
               Wand]    Katze]   Sofa]    Boden]   Fenster]
                                  ▲
                          Höchste Aufmerksamkeit!
                     → „Das Sofa ist unter der Katze"
```

> **Der Unterschied zu Self-Attention:** Bei Self-Attention (aus Tutorial 00-01) schauen Wörter auf *andere Wörter im selben Satz*. Bei Cross-Attention schauen Wörter auf *Bildkacheln in einer anderen Sequenz*. Gleicher Mechanismus, andere Perspektive.

#### Freeze the Experts — Nur die Verbindungen trainieren

Ein cleveres praktisches Detail: Die Gewichte des großen Sprachmodells werden oft **zuerst eingefroren**, damit es nicht vergisst, wie man liest, während es sehen lernt. Nur die neuen Komponenten (Projektionsschicht, Adapter-Module) werden zunächst trainiert.

DeepMinds **Flamingo**-Modell hat genau das gemacht: Es hielt sowohl den Vision-Encoder als auch das Sprachmodell weitgehend eingefroren und trainierte **nur die Verbindungsschichten**. Das bewahrt die Stärken der vortrainierten Spezialisten und lernt nur die Brücke dazwischen.

> **Bank-Analogie:** Stellen Sie sich vor, Sie stellen zwei erfahrene Sachbearbeiter zusammen — einen Experten für Textdokumente, einen für Bildanalyse. Sie würden nicht deren jahrelange Erfahrung löschen und neu schulen. Sie stellen einen Koordinator dazwischen, der lernt, die Ergebnisse beider Experten zusammenzuführen.

---

### Schritt 7: Fine-Tuning für echte Aufgaben — Die Übungsprüfung

Die Architektur steht. Das System wurde trainiert, Bilder und Text auszurichten und visuelle Tokens ins LLM einzuspeisen. Der letzte Schritt: **Fine-Tuning auf echten Aufgaben**, damit das System hochwertige Ergebnisse liefert.

Das ist, als würden Sie unserem nun zweisprachigen (Text + Bild) Kind **Übungsprüfungen** geben:

- *„Hier ist ein Bild — beschreibe es in einem ganzen Satz."*
- *„Schau dir dieses Bild an und beantworte die Frage."*
- *„Hier ist ein Dokument mit Bild und Text — fasse zusammen."*

Je nach gewünschter Fähigkeit wählt man passende Datensätze:

| Aufgabe | Trainingsdaten | Beispiel |
|---------|---------------|---------|
| **Bildbeschreibung** | Bild → Beschreibungstext | Foto → „Ein Hund spielt im Park" |
| **Visuelles Q&A** | (Bild, Frage, Antwort) | Foto + „Welche Farbe hat der Hund?" → „Braun" |
| **Instruktionsbefolgen** | Bild + Anweisung → hilfreiche Antwort | Grafik + „Erkläre diesen Chart" → Analyse |
| **Dokument-Verständnis** | Scan/PDF → strukturierte Daten | Rechnung → extrahierte Felder |

#### Zwei Trainingsphasen — Das bewährte Rezept

Die meisten erfolgreichen multimodalen Modelle (wie LLaVA) verwenden ein **zweistufiges Training**:

**Phase 1 — Alignment (Ausrichtung):**
Die Projektionsschicht wird mit Contrastive Learning oder Feature-Alignment trainiert. Das Ziel: Modalitäten ausrichten, mit einer relativ einfachen Aufgabe wie dem Zuordnen von Bildunterschriften. Das Sprachmodell bleibt eingefroren.

**Phase 2 — Task Training (Aufgabentraining):**
Das gesamte Modell wird End-to-End auf anspruchsvolleren Aufgaben feingetunt — Bildbeschreibung, Q&A, Instruktionsbefolgen. In dieser Phase darf auch das Sprachmodell seine Parameter anpassen, damit es visuelle Informationen besser integriert.

```
Phase 1: Alignment                    Phase 2: Task Training
┌──────────────────────┐              ┌──────────────────────┐
│ Vision-Encoder  ❄️    │              │ Vision-Encoder  🔥*   │
│ (eingefroren)        │              │ (teilw. trainiert)   │
│         │            │              │         │            │
│    Projektion  🔥     │              │    Projektion  🔥     │
│    (wird trainiert)  │              │    (wird trainiert)  │
│         │            │              │         │            │
│       LLM  ❄️        │              │       LLM  🔥         │
│ (eingefroren)        │              │ (wird trainiert)     │
└──────────────────────┘              └──────────────────────┘

❄️ = eingefroren    🔥 = wird trainiert
```

Nach dem Fine-Tuning haben Sie ein funktionierendes multimodales Modell. Geben Sie ihm ein Bild und einen Text-Prompt, und es liefert nützlichen Text, der beides berücksichtigt.

---

## Die vollständige Pipeline auf einen Blick

```
                  Bild                              Text-Frage
                   │                                    │
                   ▼                                    ▼
          ┌────────────────┐                   ┌────────────────┐
          │ Vision-Encoder │                   │  Text-Encoder  │
          │    (ViT)       │                   │   (LLM)        │
          └───────┬────────┘                   └───────┬────────┘
                  │                                    │
                  ▼                                    │
          ┌────────────────┐                           │
          │  Projektions-  │                           │
          │   schicht      │                           │
          └───────┬────────┘                           │
                  │                                    │
                  │    Bild-Tokens    Text-Tokens      │
                  └──────────┐  ┌──────────────────────┘
                             ▼  ▼
                    ┌──────────────────┐
                    │       LLM        │
                    │  (Cross-Attention │
                    │   + Generation)   │
                    └────────┬─────────┘
                             │
                             ▼
                    📝 „Ein Hund jagt einen
                       Ball auf einer Wiese."
```

---

## Die aktuelle Modell-Landschaft (Stand: Februar 2026)

Multimodale Modelle haben sich rasant entwickelt. Hier ein Überblick über die wichtigsten Systeme:

### 🧠 Multimodale Sprachmodelle (Text + Bild → Text)

| Modell | Hersteller | Besonderheiten | Zugang |
|--------|-----------|----------------|--------|
| **GPT-4o / GPT-5** | OpenAI | Nativ multimodal (Text, Bild, Audio, Video in einem Modell), Echtzeit-Sprache | ChatGPT, API |
| **Claude Opus 4 / Sonnet 4** | Anthropic | Starke Bild- und Dokumentenanalyse, sehr gute Reasoning-Fähigkeiten | claude.ai, API |
| **Gemini 2.5 Pro** | Google DeepMind | Nativ multimodal, verarbeitet Text + Bild + Audio + Video, riesiges Kontextfenster (1M+ Tokens) | Gemini, Vertex AI |
| **LLaMA 4** | Meta | Open Source, multimodale Varianten verfügbar, starke Community | Lokal, API |
| **LLaVA 1.6+** | Open Source (Wisconsin/Microsoft) | Der Pionier des „einfachen" multimodalen Ansatzes (ViT + Projektion + LLM) | Lokal, Replicate |
| **Qwen 2.5 VL** | Alibaba | Open Source, starke Vision-Language-Fähigkeiten, mehrsprachig | Lokal, API |

### 🎬 Multimodale Generierungs-Modelle (Text → Bild/Video/Audio)

| Modell | Hersteller | Modalitäten | Besonderheiten |
|--------|-----------|-------------|----------------|
| **GPT Image (DALL·E 4)** | OpenAI | Text → Bild | In ChatGPT integriert, starke Text-Darstellung in Bildern |
| **Sora 2** | OpenAI | Text → Video (mit Audio) | Bis zu mehrere Minuten, synchroner Sound |
| **Seedance 2.0** | ByteDance | Text + Bild + Audio → Video | Multimodal-Input, vereinte Architektur |
| **Flux 2.0** | Black Forest Labs 🇩🇪 | Text → Bild | Open Source (teilw.), hervorragende Prompt-Treue |
| **Gemini + Veo 2** | Google | Text → Bild + Video | Integriert in Gemini-Ökosystem |

### 🔄 Der Trend: Von multimodal zu „omnimodal"

Die neueste Generation — allen voran **GPT-4o** und **Gemini 2.5** — ist nicht mehr einfach „multimodal" im Sinne von „zwei Spezialisten zusammengeklebt". Sie sind **nativ multimodal**: Ein einziges Modell, das von Grund auf mit allen Modalitäten gleichzeitig trainiert wurde.

| Generation | Architektur | Beispiel |
|-----------|-------------|---------|
| **Gen 1** (2023) | Encoder + Projektion + LLM (zusammengesteckt) | LLaVA, Flamingo |
| **Gen 2** (2024) | Tiefere Integration, teilweise gemeinsames Training | GPT-4V, Gemini 1.5 |
| **Gen 3** (2025–26) | Nativ multimodal, ein Modell für alles | GPT-4o/5, Gemini 2.5 |

> **Die Richtung ist klar:** Weg von „Spezialisten zusammenkleben" hin zu „ein Gehirn, das alles von Anfang an zusammen lernt." Aber das Grundprinzip — alles in einen gemeinsamen Vektorraum bringen und Cross-Attention für die Verbindung nutzen — bleibt dasselbe.

---

## Werkzeuge und Stellschrauben: Was Sie als Anwender wissen sollten

### Wann multimodal nutzen?

| Aufgabe | Warum multimodal besser ist | Beispiel |
|---------|---------------------------|---------|
| **Dokumenten-Analyse** | Modell sieht Layout, Tabellen, Logos — nicht nur OCR-Text | Rechnung fotografieren → alle Felder extrahiert |
| **Bild-Fragen** | Natürliche Fragen über visuelle Inhalte | „Was zeigt dieses Diagramm?" → Erklärung |
| **Barrierefreiheit** | Bildbeschreibungen für Sehbehinderte | Foto → „Eine Gruppe Menschen steht vor einem Gebäude" |
| **Qualitätskontrolle** | Visuelle Inspektion + textuelle Bewertung | Produktfoto → „Kratzer am oberen Rand erkannt" |
| **Recherche** | Bilder und Text gleichzeitig auswerten | Zeitungsartikel mit Grafiken → Zusammenfassung |

### Typische Einstellungen

| Parameter | Was er bewirkt | Empfehlung |
|-----------|---------------|------------|
| **Detail-Level** | Wie genau das Modell das Bild analysiert (z.B. OpenAI: `low` / `high`) | `high` für komplexe Bilder, `low` für einfache oder wenn Kosten relevant |
| **Max Tokens** | Maximale Länge der Textantwort | Je nach Aufgabe — kurze Fragen: 100–300, Analyse: 500–1000 |
| **Temperature** | Kreativität der Textantwort (wie bei reinen LLMs) | 0–0.3 für faktische Analyse, 0.7+ für kreative Beschreibungen |
| **Bildauflösung** | Höhere Auflösung = mehr Details, aber mehr Tokens/Kosten | Für Text in Bildern: hohe Auflösung; für grobe Erkennung: niedrig reicht |

### Was multimodale Modelle (noch) nicht gut können

| Limitation | Erklärung |
|-----------|-----------|
| **Exaktes Zählen** | „Wie viele Äpfel sind auf dem Bild?" — oft ungenau bei >5 Objekten |
| **Räumliche Beziehungen** | „Ist der Stuhl links oder rechts vom Tisch?" — manchmal fehlerhaft |
| **Text in Bildern lesen** | Besser geworden, aber kleine oder gedrehte Schrift bleibt schwierig |
| **Halluzinationen** | Das Modell „sieht" manchmal Dinge, die nicht im Bild sind |
| **Echtzeit-Video** | Echte Video-Verarbeitung (nicht nur Einzelframes) ist noch in den Anfängen |

> **Praxis-Tipp:** Wenn Sie ein multimodales Modell für die Arbeit nutzen (z.B. Dokumentenanalyse bei der Bank), testen Sie immer mit ein paar bekannten Beispielen, bevor Sie den Ergebnissen blind vertrauen. Besonders bei Zahlen und räumlichen Angaben lohnt sich eine Gegenprüfung.

---

## Das Wichtigste auf einen Blick

| Erkenntnis | Was das bedeutet |
|-----------|-----------------|
| **Spezialisten + cleverer Klebstoff** | Ein multimodales Modell ist kein einzelnes Universalgenie. Es verbindet spezialisierte Komponenten (Text-Encoder, Vision-Encoder) über Projektionsschichten und Cross-Attention. Die Magie passiert an den Verbindungen. |
| **Alles wird zu Vektoren** | Verschiedene Datentypen (Wörter, Pixel, Klänge) können alle in dieselbe numerische Darstellung umgewandelt werden. In einem gemeinsamen Einbettungsraum behandelt ein Transformer Bilddaten nicht anders als Text. |
| **Cross-Attention ist die Brücke** | Cross-Attention lässt eine Sequenz eine andere nach relevanten Informationen befragen. So fragt der Text-Teil den Bild-Teil „Was siehst du?" und bekommt eine sinnvolle Antwort. |
| **Freeze the Experts, Train the Connectors** | Man nutzt vortrainierte Modelle für jede Modalität, friert sie ein und trainiert nur die Verbindungsmodule. Das spart enorm Rechenzeit und Daten, weil die Schwerstarbeit (Text und Bilder einzeln verstehen) bereits erledigt ist. |
| **Contrastive Learning richtet die Welten aus** | Durch das „Magnetspiel" lernt das System, dass zusammengehörige Bild-Text-Paare nahe beieinander liegen — die Grundlage für alles Weitere. |

---

## Die Parallelen zu den vorherigen Tutorials

Es gibt schöne Verbindungslinien:

- **Tutorial 00-01 (LLMs):** Das Text-Gehirn in einem multimodalen Modell *ist* ein LLM. Attention, Tokens, Embeddings — alles kommt hier wieder zum Einsatz.
- **Tutorial 00-02 (Diffusion):** CLIP, das dort den Textprompt in visuelle Anweisungen übersetzt, ist ein frühes Beispiel für multimodales Alignment. Cross-Attention, die dort Text mit Bilderzeugung verbindet, ist derselbe Mechanismus, der hier Text mit Bildverständnis verbindet.

Die drei Tutorials zusammen erzählen eine Geschichte:
1. **LLMs** brachten Maschinen das Lesen und Schreiben bei
2. **Diffusion-Modelle** brachten ihnen das Sehen und Malen bei
3. **Multimodale Modelle** verbinden beides — und schaffen KI, die lesen, schreiben, sehen und beschreiben kann

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Modalität** | Eine Art von Daten — Text, Bild, Audio und Video sind die gängigsten Modalitäten |
| **Multimodal** | Ein Modell, das mehrere Modalitäten gleichzeitig verarbeiten kann |
| **Shared Embedding Space** | Ein gemeinsamer mathematischer Raum, in dem Daten aus verschiedenen Modalitäten als vergleichbare Vektoren koexistieren |
| **Text-Encoder** | Komponente, die Text in bedeutungsvolle Vektoren umwandelt (meist ein Transformer/LLM) |
| **Vision-Encoder** | Komponente, die Bilder in bedeutungsvolle Vektoren umwandelt (meist ein Vision Transformer) |
| **Vision Transformer (ViT)** | Ein Transformer, der Bilder verarbeitet, indem er sie in Kacheln (Patches) zerlegt und als Token-Sequenz behandelt |
| **Patch** | Ein kleines Teilstück eines Bildes (z.B. 16×16 Pixel), das als visuelles Token dient |
| **Projektionsschicht** | Eine lernbare lineare Schicht, die Vektoren einer Modalität in den Raum einer anderen abbildet — der „Adapterstecker" |
| **Contrastive Learning** | Trainingsmethode, bei der passende Paare zusammengezogen und nicht-passende auseinandergedrückt werden — das „Magnetspiel" |
| **Cross-Attention** | Mechanismus, bei dem eine Sequenz (z.B. Text) eine andere Sequenz (z.B. Bild) nach relevanten Informationen befragt |
| **CLIP** | OpenAIs Modell, das durch Contrastive Learning einen gemeinsamen Raum für Text und Bilder gelernt hat — trainiert auf 400 Mio. Bild-Text-Paaren |
| **LLaVA** | Einflussreiches Open-Source-Modell (2023), das den einfachen Ansatz „ViT + Projektion + LLM" popularisierte |
| **Flamingo** | DeepMinds multimodales Modell, das die „Freeze and Bridge"-Strategie demonstrierte |
| **Nativ multimodal** | Modelle der neuesten Generation, die von Grund auf mit allen Modalitäten trainiert werden (statt nachträglicher Verbindung) |
| **Feature Alignment** | Der Prozess, bei dem die Darstellungen verschiedener Modalitäten in einen gemeinsamen Raum gebracht werden |
| **Visual Tokens** | Bild-Kacheln, die als Token-Embedding in einen Transformer eingespeist werden — das Bild wird zur „Sequenz" |

---



