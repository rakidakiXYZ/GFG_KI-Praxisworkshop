# Wie Multimodale Modelle funktionieren

**Wenn Text, Bild und mehr in einem KI-Gehirn zusammenkommen — verständlich erklärt**

---

## Warum dieses Tutorial?

In den letzten beiden Tutorials haben Sie zwei Spezialisten kennengelernt: LLMs, die Text verstehen und erzeugen, und Diffusion-Modelle, die Bilder aus Rauschen erschaffen. Beide sind beeindruckend — aber jeder kann nur *eine* Sache.

Sie kennen aber sicher auch KI-Systeme, die **beides gleichzeitig** können: Sie laden ein Foto hoch und die KI beschreibt, was darauf zu sehen ist. Oder Sie tippen eine Beschreibung ein und bekommen ein passendes Bild zurück. ChatGPT, Gemini und Claude können das alles in einem Gespräch.

Wie funktioniert das? Wie bringt man ein Text-Gehirn und ein Bild-Gehirn dazu, **zusammenzuarbeiten**?

Die überraschende Antwort: **Man nimmt zwei Spezialisten und klebt sie mit Panzertape und schlauer Mathematik zusammen.** Klingt improvisiert? Ist es — auf geniale Weise.

**Was Sie nach diesem Tutorial wissen werden:**

- Was ein multimodales Modell ist und warum es funktioniert
- Wie man Text und Bilder in eine gemeinsame „Sprache" übersetzt
- Welche Rolle Text-Encoder, Vision-Encoder und Projektionsschichten spielen
- Wie Contrastive Learning die Brücke zwischen den Welten baut
- Wie Attention Text und Bild im selben Satz verarbeitet — und welche zwei Varianten es gibt
- Wie das Ganze zum fertigen System zusammengebaut und trainiert wird
- Was Bilder in Tokens kosten — und warum das für Ihr Budget relevant ist
- Welche aktuellen multimodalen Modelle es gibt und was sie können

---

## Die Analogie: Das zweisprachige Kind

Stellen Sie sich ein Kind vor, das lesen, zeichnen und Musik hören kann — alles gleichzeitig. Zeigen Sie ihm ein Foto von einem Hund und es sagt „Hund." Sagen Sie „Hund" und es zeichnet einen. Es versteht, dass ein Foto von einem Hund, das Wort „Hund" und das Geräusch „Wuff" alle auf dasselbe Konzept zeigen.

**Das ist ein multimodales Modell in einem Satz.** Eine KI, die verschiedene Arten von Information — sogenannte **Modalitäten** — gleichzeitig verarbeiten kann. Text, Bilder, Audio, Video — jede Modalität hat ihr eigenes „Alphabet": Buchstaben für Text, Pixel für Bilder, Schallwellen für Audio.

Die meisten KI-Modelle sind Spezialisten: Eines liest Text, ein anderes betrachtet Bilder. Ein multimodales Modell ist ein **Generalist**, der mehrere Datensprachen spricht. Und das wirklich Beeindruckende: Es weiß, dass 🚗 (ein Bild eines Autos), „Auto" (das Wort) und *brumm* (das Geräusch) alle dasselbe meinen.

> **Bank-Analogie:** Stellen Sie sich eine erfahrene Sachbearbeiterin vor, die gleichzeitig einen Brief lesen, ein Foto des Absenders betrachten und eine Sprachnotiz abhören kann — und sofort versteht, dass alles zum selben Vorgang gehört. Das ist multimodal.

---

## Ein kurzer Blick zurück: Wie KI das Sehen und Lesen gleichzeitig lernte

Multimodale Modelle sind nicht über Nacht entstanden. Sie sind das Ergebnis einer rasanten Entwicklung:

| Zeitraum | Meilenstein | Was es konnte |
|----------|------------|----------------|
| **2012** | **AlexNet** (ImageNet) | Erster Deep-Learning-Durchbruch in der Bilderkennung — aber nur Klassifikation, kein Textverständnis |
| **2017** | **Transformer** (Google) | Die Architektur, die alles veränderte — zunächst nur für Text (Übersetzung) |
| **2019** | **ViLBERT** | Einer der ersten Versuche, Text und Bild in einem Transformer zu verarbeiten — noch klobig und langsam |
| **2021** | **CLIP** (OpenAI) | Der Durchbruch: Bewies, dass man Text und Bilder in einen gemeinsamen Vektorraum bringen kann — trainiert auf 400 Mio. Bild-Text-Paaren |
| **2021** | **DALL·E 1** (OpenAI) | Erster großer Text-zu-Bild-Generator — multimodal in die andere Richtung |
| **2022** | **Flamingo** (DeepMind) | Zeigte, wie man ein eingefrorenes LLM mit Vision verbindet — das „Freeze and Bridge"-Rezept |
| **2023** | **LLaVA** | Der „Demokratisierer": Bewies, dass eine simple lineare Projektion + ViT + LLM erstaunlich gut funktioniert — und Open Source |
| **2023** | **GPT-4V** (OpenAI) | Erster kommerzieller Chatbot mit starker Bildanalyse — multimodal wurde Mainstream |
| **2024** | **GPT-4o** (OpenAI) | **Nativ multimodal**: Ein Modell, von Grund auf mit Text, Bild und Audio trainiert — kein „Zusammenkleben" mehr |
| **2025–26** | **GPT-5, Gemini 2.5, Claude Opus 4** | Die aktuelle Generation: Omnimodal, riesige Kontextfenster, Echtzeit-Video und -Audio |

### Warum ging es plötzlich so schnell?

Drei Dinge kamen zusammen:

1. **CLIP bewies das Prinzip** (2021): Man *kann* Text und Bilder in einen gemeinsamen Raum bringen
2. **Vortrainierte LLMs wurden riesig gut** (GPT-3/4, LLaMA): Man musste das Text-Gehirn nicht mehr selbst bauen
3. **LLaVA zeigte, wie einfach es sein kann** (2023): Vision-Encoder + eine lineare Schicht + LLM = funktionierendes multimodales Modell

> **Die Parallele zu den vorherigen Tutorials:** GANs wurden von Diffusion abgelöst (Tutorial 00-02), regelbasierte Systeme von Transformern (Tutorial 00-01). Und isolierte Spezialisten werden nun von multimodalen Generalisten abgelöst. Die KI-Entwicklung beschleunigt sich exponentiell.

---

## Warum funktioniert das überhaupt? — Alles wird zu Zahlen

Hier kommt die Schlüsselerkenntnis, die multimodale KI überhaupt möglich macht:

**Unter der Haube können wir alles — Wörter, Bilder, Klänge — in dieselbe Art von numerischer Darstellung umwandeln.**

Sobald alles in **Vektoren** (Listen von Zahlen) umgewandelt ist, sieht das Modell nur noch Zahlen. Es ist ihm egal, ob diese Zahlen ursprünglich von einem Foto oder einem Satz stammen.

Stellen Sie sich einen **universellen Übersetzungsraum** vor. Jede Information, die hineinkommt, wird in ein gemeinsames Format konvertiert. In diesem Raum werden ein Foto einer Katze, das geschriebene Wort „Katze" und ein Miau-Geräusch alle in dieselbe Sprache übersetzt. Wie drei Menschen, die verschiedene Sprachen sprechen, aber alle ins Deutsche übersetzt wurden — jetzt stehen sie nebeneinander und stimmen überein, dass sie dasselbe meinen.

Das ist ein **Shared Embedding Space** — ein gemeinsamer Einbettungsraum. Ein mathematischer Raum, in dem Daten aus verschiedenen Modalitäten als vergleichbare Vektoren nebeneinander existieren.

> **Erinnern Sie sich?** In Tutorial 00-01 haben wir gelernt, wie LLMs Wörter in Vektoren umwandeln (Embeddings). In Tutorial 00-02 haben wir gesehen, wie CLIP Text und Bilder in einen gemeinsamen Raum bringt. Genau dieses Prinzip wird hier zum Fundament des gesamten Systems.

> **Bank-Analogie:** Denken Sie an das standardisierte Formularwesen einer Bank. Egal ob ein Kundenantrag als Brief, E-Mail, Fax oder telefonische Aufnahme hereinkommt — am Ende wird alles in dasselbe digitale System überführt, mit denselben Feldern und demselben Format. Das ist ein Shared Embedding Space im Bankalltag.

---

## Die Bausteine: Schritt für Schritt zum multimodalen Modell

### Schritt 1: Die Modalitäten wählen — Klein anfangen

Bevor man ein multimodales Modell baut, entscheidet man: Welche Modalitäten sollen es sein? Wir starten mit den zwei häufigsten: **Text und Bilder**.

Stellen Sie sich das wie einen zweisprachigen Übersetzer vor. Wenn Sie irgendwann Englisch, Französisch und Spanisch beherrschen wollen, fangen Sie nicht mit allen drei gleichzeitig an. Sie meistern erst Englisch und Französisch, und fügen Spanisch später hinzu.

Genauso machen es multimodale Modelle: **Erst Text + Bild**, dann eventuell Audio, Video oder andere Modalitäten dazu. Der Grund ist auch praktisch — es gibt riesige Datensätze mit Bild-Text-Paaren (Millionen von Bildern mit Beschreibungen), die perfekt zum Training geeignet sind.

**Unser Plan:** Ein Modell bauen, das Bilder sehen und Text lesen kann — und beide Welten verbinden.

> **Bank-Analogie:** Eine neue Sachbearbeiterin lernt auch nicht gleichzeitig Kreditanträge, Wertpapierhandel und Versicherungswesen. Sie startet mit einem Bereich, wird sicher — und erweitert dann.

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

> **Bank-Analogie:** Ein Bild in Kacheln zu zerlegen ist wie ein Prüfer, der ein großes Grundstücksfoto systematisch in Quadranten aufteilt und jeden einzeln begutachtet — Zustand des Dachs, Garten, Fassade, Nachbarschaft — um dann ein Gesamturteil abzugeben.

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

> **Bank-Analogie:** Die Projektionsschicht ist wie das Normierungsformat, das alle eingehenden Bankdokumente — ob handschriftlicher Brief, PDF oder E-Mail — in ein einheitliches digitales Formular überführt. Egal wie die Daten hereinkommen, am Ende stehen sie im selben System mit denselben Feldern.

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

#### Ähnlichkeit messen: Cosine Similarity

Aber wie misst man eigentlich, ob zwei Vektoren „ähnlich" sind? Dafür gibt es ein elegantes Werkzeug: **Cosine Similarity** (Kosinusähnlichkeit).

Stellen Sie sich zwei Pfeile vor, die von einem gemeinsamen Punkt ausgehen:

- **Zeigen sie in dieselbe Richtung** → Cosine Similarity = 1.0 (perfekt ähnlich)
- **Stehen sie rechtwinklig zueinander** → Cosine Similarity = 0.0 (kein Zusammenhang)
- **Zeigen sie in entgegengesetzte Richtungen** → Cosine Similarity = −1.0 (Gegenteil)

```
Ähnlich (≈ 1.0)    Unabhängig (≈ 0.0)    Gegenteil (≈ -1.0)

     ↗  ↗               ↑                      ↑
    /  /                 │                      │
   /  /                  └──→                   │
                                                ↓
„Hund" ≈ 🐕           „Hund" ⊥ „Zinssatz"    „heiß" ↔ „kalt"
```

> **Warum nicht einfach den Abstand messen?** Cosine Similarity schaut nur auf die *Richtung* der Vektoren, nicht auf ihre Länge. Das ist robuster — ein leise geflüstertes „Hund" und ein laut gerufenes „HUND" zeigen in dieselbe Richtung, auch wenn sie unterschiedlich „laut" (lang) sind.

#### Die Ähnlichkeitsmatrix

Für einen Stapel von Bild-Text-Paaren berechnet man die Cosine Similarity zwischen allen Kombinationen:

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

> **Bank-Analogie:** Contrastive Learning ist wie der Abgleich zwischen Kundenfoto und Ausweisdokument — das System lernt: „Dieses Gesicht und dieser Name gehören zusammen, dieses Gesicht und jener Name nicht." Je mehr Paare es sieht, desto besser wird es im Zuordnen.

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

#### Zwei Varianten: Self-Attention vs. Cross-Attention

Hier gibt es einen wichtigen Unterschied, den man kennen sollte — denn es existieren **zwei verschiedene Wege**, wie das LLM die Bild- und Text-Tokens verbindet:

**Variante A: Bild-Tokens einfach einfügen (Self-Attention)**

Die einfachere und heute häufigere Variante: Die Bild-Tokens werden direkt in die Token-Sequenz eingefügt, als wären sie normale Wörter. Das LLM verarbeitet alles mit seinem **normalen Self-Attention-Mechanismus** — dem gleichen, den Sie aus Tutorial 00-01 kennen.

Das LLM „merkt" nicht einmal, dass manche Tokens von einem Bild stammen. Es sieht einfach eine lange Sequenz und lässt jeden Token auf jeden anderen schauen.

**So machen es:** LLaVA, GPT-4V, die meisten modernen Modelle.

```
Sequenz: [Bild-T1] [Bild-T2] ... [Bild-T196] [Was] [ist] [auf] [dem] [Bild] [?]
              ↕         ↕              ↕          ↕     ↕     ↕     ↕     ↕    ↕
         Alle Tokens schauen aufeinander via Self-Attention
         (Bild-Tokens und Text-Tokens sind gleichberechtigt)
```

> **Warum funktioniert das?** Weil die Projektionsschicht (Schritt 4) die Bild-Tokens bereits in den Vektorraum des LLMs übersetzt hat. Sie „sprechen dieselbe Sprache" — das LLM muss keinen Unterschied machen.

**Variante B: Dedizierte Cross-Attention-Module**

Die komplexere Variante: Statt die Bild-Tokens einfach in die Sequenz zu mischen, bekommt das LLM **zusätzliche Attention-Schichten**, die speziell dafür da sind, die Text-Tokens auf die Bild-Tokens „schauen" zu lassen.

Cross-Attention lässt eine Sequenz eine andere nach relevanten Informationen **befragen**. Es ist, als würde der Text-Teil den Bild-Teil fragen:

*„Hey, ich lese gerade die Frage ‚Worauf sitzt die Katze?' — was siehst du unter der Katze?"*

**So machen es:** DeepMinds Flamingo, und Diffusion-Modelle (aus Tutorial 00-02 — dort verbindet Cross-Attention den Textprompt mit der Bilderzeugung).

```
Text-Tokens:   „Worauf"  „sitzt"  „die"  „Katze"  „?"
                   │         │       │       │       │
              ┌────┴─────────┴───────┴───────┴───────┴─────┐
              │           Cross-Attention                    │
              │   Text fragt Bild: „Was ist relevant?"       │
              └────┬─────────────────────────────────────────┘
                   │
Bild-Tokens:  [Kachel  [Kachel  [Kachel  [Kachel  [Kachel
               Wand]    Katze]   Sofa]    Boden]   Fenster]
                                  ▲
                          Höchste Aufmerksamkeit!
                     → „Das Sofa ist unter der Katze"
```

#### Welche Variante ist besser?

| Aspekt | Variante A (Self-Attention) | Variante B (Cross-Attention) |
|--------|-----------------------------|------------------------------|
| **Einfachheit** | Sehr einfach — keine neuen Module nötig | Komplexer — zusätzliche Schichten im LLM |
| **Flexibilität** | Bild-Tokens „konkurrieren" mit Text-Tokens um Aufmerksamkeit | Dedizierter Kanal für visuelle Informationen |
| **Effizienz** | Bild-Tokens vergrößern die Sequenz → mehr Rechenaufwand | Bild-Tokens bleiben separat → effizienter bei vielen Bildern |
| **Beispiele** | LLaVA, GPT-4V, Qwen-VL | Flamingo, einige Forschungsmodelle |
| **Trend** | ✅ Heute dominant | Eher für spezielle Architekturen |

> **Der wichtige Punkt:** Egal welche Variante — das Ergebnis ist dasselbe: Text-Tokens können auf Bild-Tokens zugreifen und umgekehrt. Der Unterschied liegt im *Wie*, nicht im *Was*.

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

> **Bank-Analogie:** Phase 1 ist wie die Grundausbildung — der neue Mitarbeiter lernt, welche Dokumente zusammengehören. Phase 2 ist die Spezialisierung — jetzt lernt er, aus den Dokumenten eigenständig Bewertungen und Berichte zu erstellen.

---

## Und was ist mit Audio? — Die dritte Sprache

Bisher haben wir nur Text und Bilder verbunden. Aber Sie haben sicher bemerkt, dass Modelle wie GPT-4o auch **sprechen und hören** können. Wie funktioniert das?

Die gute Nachricht: **Genau nach demselben Prinzip.** Audio ist einfach eine weitere Modalität, die in Vektoren umgewandelt wird.

### Wie wird Audio zu Tokens?

Ein Audiosignal (z.B. eine Sprachaufnahme) wird zuerst in ein **Spektrogramm** umgewandelt — ein Bild, das zeigt, welche Frequenzen zu welchem Zeitpunkt vorkommen. Und ein Bild können wir ja bereits verarbeiten!

```
Audiosignal           Spektrogramm              Patches / Tokens
                    (Zeit × Frequenz)
🎙️ "Hallo"  ───→  ┌──────────────────┐  ───→  [T1] [T2] [T3] ...
                    │▓░▓▓░░▓▓▓░▓▓░░▓▓│         Audio-Tokens
                    │░▓░░▓▓░░░▓░░▓▓░░│         (wie bei Bildern)
                    │▓▓░▓░░▓░▓░▓░░▓░▓│
                    └──────────────────┘
                     ↑ Zeit →
                     Frequenz ↑
```

Der Audio-Encoder zerlegt das Spektrogramm in Kacheln (genau wie der Vision-Encoder ein Foto zerlegt), wandelt jede Kachel in einen Vektor um, und schon haben wir **Audio-Tokens**. Diese werden über eine Projektionsschicht in denselben gemeinsamen Raum gebracht wie Text und Bild.

> **Das Prinzip ist immer dasselbe:** Rohdaten → Encoder → Vektoren → Projektion → gemeinsamer Raum. Ob Text, Bild oder Audio — der Transformer sieht am Ende nur Zahlen.

### OpenAIs Whisper als Beispiel

OpenAIs **Whisper**-Modell ist ein Audio-Encoder, der genau so funktioniert: Es nimmt eine Sprachaufnahme, wandelt sie in ein Mel-Spektrogramm um, verarbeitet es mit einem Transformer und erzeugt Text. In multimodalen Modellen wie GPT-4o ist ein ähnlicher Audio-Encoder integriert — zusammen mit einem Audio-*Decoder*, der auch Sprache *erzeugen* kann.

> **Das ist, warum GPT-4o in Echtzeit sprechen kann:** Es verarbeitet Audio-Tokens, Text-Tokens und Bild-Tokens alle im selben Modell — und kann in jede Richtung „übersetzen".

---

## Was Bilder Sie kosten: Tokens und Budget

In Tutorial 00-01 haben Sie gelernt, dass Tokens Geld kosten — und dass deutsche Texte mehr Tokens verbrauchen als englische. Bei multimodalen Modellen kommt eine neue Dimension dazu: **Bilder kosten Tokens. Viele Tokens.**

### Wie viele Tokens kostet ein Bild?

| Modell | Niedrige Auflösung | Hohe Auflösung | Zum Vergleich: Text |
|--------|-------------------|----------------|---------------------|
| **GPT-4o** | ~85 Tokens | ~800–1.600 Tokens | „Hund" = 1 Token |
| **Claude Opus 4** | ~100 Tokens | ~1.000–1.600 Tokens | Dieser Absatz ≈ 50 Tokens |
| **Gemini 2.5** | ~258 Tokens | ~258 Tokens (fix) | Eine A4-Seite Text ≈ 500 Tokens |

**Ein einziges hochauflösendes Foto verbraucht also so viele Tokens wie 3 Seiten Text!**

### Was das für Ihr Budget bedeutet

| Szenario | Tokens pro Anfrage | Ungefähre Kosten (GPT-4o API) |
|----------|-------------------|-------------------------------|
| Nur Text: „Fasse diese E-Mail zusammen" | ~200 | ~0,001 $ |
| Text + 1 Bild (niedrig): „Was ist auf dem Foto?" | ~300 | ~0,002 $ |
| Text + 1 Bild (hoch): „Lies die Rechnung" | ~1.800 | ~0,01 $ |
| Text + 5 Bilder (hoch): „Vergleiche diese Dokumente" | ~8.500 | ~0,05 $ |

> **Praxis-Tipp:** Nutzen Sie die niedrige Auflösung (`low` / `auto`), wenn Sie nur grobe Inhalte erkennen wollen — z.B. „Ist das ein Hund oder eine Katze?" Schalten Sie auf hohe Auflösung (`high`), wenn es auf Details ankommt — z.B. Text auf einem Dokument lesen oder kleine Fehler in einem Produktfoto finden.

> **Bank-Analogie:** Es ist wie der Unterschied zwischen einer schnellen Sichtprüfung (niedrige Kosten) und einer detaillierten forensischen Analyse (hohe Kosten) eines Dokuments. Nicht jedes Dokument braucht die volle Behandlung.

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
                    │  (Self-Attention  │
                    │   über alle       │
                    │   Tokens)         │
                    └────────┬─────────┘
                             │
                             ▼
                    📝 „Ein Hund jagt einen
                       Ball auf einer Wiese."
```

---

## Probieren Sie es selbst! 🧪

Das Beste an multimodalen Modellen: **Sie können sie sofort ausprobieren** — ohne Installation, ohne Programmierung.

### Experiment 1: Bildbeschreibung
1. Öffnen Sie [ChatGPT](https://chat.openai.com), [Claude](https://claude.ai) oder [Gemini](https://gemini.google.com)
2. Laden Sie ein beliebiges Foto hoch (z.B. vom Schreibtisch, aus dem Fenster, ein Zeitungsartikel)
3. Fragen Sie: *„Was siehst du auf diesem Bild? Beschreibe es detailliert."*
4. Beobachten Sie, wie präzise das Modell Objekte, Farben und Beziehungen erkennt

### Experiment 2: Dokumentenanalyse
1. Fotografieren Sie eine Rechnung, einen Kassenbon oder ein Formular
2. Laden Sie das Foto hoch und fragen Sie: *„Extrahiere alle Beträge und Daten aus diesem Dokument."*
3. Prüfen Sie die Ergebnisse gegen das Original — wo ist das Modell genau, wo macht es Fehler?

### Experiment 3: Modellvergleich
1. Nehmen Sie **dasselbe Bild** und **dieselbe Frage**
2. Stellen Sie sie an zwei verschiedene Modelle (z.B. ChatGPT und Claude)
3. Vergleichen Sie: Welches Modell sieht mehr Details? Welches macht Fehler? Welches halluziniert?

> **Was Sie dabei lernen:** Jedes Modell hat Stärken und Schwächen bei verschiedenen Bildtypen. ChatGPT ist oft besser bei Text in Bildern, Claude bei komplexen Diagrammen, Gemini bei Fotos mit vielen Details. Erst durch Ausprobieren lernen Sie, welches Tool für welche Aufgabe passt.

### Experiment 4: Die Grenzen testen
Probieren Sie bewusst schwierige Aufgaben:
- *„Wie viele Personen sind auf diesem Gruppenfoto?"* (Zählen)
- *„Steht die Tasse links oder rechts vom Laptop?"* (Räumliche Beziehungen)
- *„Was steht auf dem kleinen Schild im Hintergrund?"* (Kleine Texte)

Sie werden sehen: Bei all diesen Aufgaben machen aktuelle Modelle noch Fehler. Das ist gut zu wissen, bevor man sich auf die Ergebnisse verlässt.

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

Die neueste Generation — allen voran **GPT-4o** und **Gemini 2.5** — ist nicht mehr einfach „multimodal" im Sinne von „zwei Spezialisten mit Panzertape zusammengeklebt". Sie sind **nativ multimodal**: Ein einziges Modell, das von Grund auf mit allen Modalitäten gleichzeitig trainiert wurde.

| Generation | Architektur | Beispiel |
|-----------|-------------|---------|
| **Gen 1** (2023) | Encoder + Projektion + LLM (zusammengesteckt) | LLaVA, Flamingo |
| **Gen 2** (2024) | Tiefere Integration, teilweise gemeinsames Training | GPT-4V, Gemini 1.5 |
| **Gen 3** (2025–26) | Nativ multimodal, ein Modell für alles | GPT-4o/5, Gemini 2.5 |

> **Die Richtung ist klar:** Weg von „Spezialisten zusammenkleben" hin zu „ein Gehirn, das alles von Anfang an zusammen lernt." Aber das Grundprinzip — alles in einen gemeinsamen Vektorraum bringen und Attention für die Verbindung nutzen — bleibt dasselbe.

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

| Limitation | Erklärung | Bank-Relevanz |
|-----------|-----------|---------------|
| **Exaktes Zählen** | „Wie viele Personen sind im Raum?" — oft ungenau bei >5 Objekten | Gruppenfoto-Analyse, Inventurzählung |
| **Räumliche Beziehungen** | „Ist der Stuhl links oder rechts vom Tisch?" — manchmal fehlerhaft | Layout-Analyse von Grundrissen |
| **Handschrift auf alten Dokumenten** | Historische Handschriften oder verblasste Tinte werden oft falsch gelesen | Erbenermittlung, historische Urkunden |
| **Stempel und Siegel** | Runde Stempel, Wasserzeichen oder Prägungen werden unzuverlässig erkannt | Dokumentenechtheit, Notarurkunden |
| **Unterschriftenvergleich** | Das Modell kann Unterschriften beschreiben, aber **nicht zuverlässig vergleichen** — das ist eine forensische Aufgabe | ⚠️ Niemals für Unterschriftenprüfung verwenden! |
| **Halluzinationen** | Das Modell „sieht" manchmal Dinge, die nicht im Bild sind | Kritisch bei rechtsverbindlichen Dokumenten |
| **Datenschutz** | Hochgeladene Bilder werden ggf. auf Servern verarbeitet | ⚠️ Keine vertraulichen Kundendokumente in öffentliche KI-Tools hochladen! |

> **Praxis-Tipp:** Wenn Sie ein multimodales Modell für die Arbeit nutzen (z.B. Dokumentenanalyse bei der Bank), testen Sie immer mit ein paar bekannten Beispielen, bevor Sie den Ergebnissen blind vertrauen. Und beachten Sie: **Kein multimodales Modell ersetzt eine qualifizierte Prüfung** bei rechtsrelevanten Dokumenten. Es ist ein Werkzeug zur Unterstützung, nicht zur Entscheidung.

---

## Das Wichtigste auf einen Blick

| Erkenntnis | Was das bedeutet |
|-----------|-----------------|
| **Spezialisten + Panzertape** | Ein multimodales Modell ist kein einzelnes Universalgenie. Es verbindet spezialisierte Komponenten (Text-Encoder, Vision-Encoder) über Projektionsschichten und Attention. Die Magie passiert an den Verbindungen — und sie ist erstaunlich einfach. |
| **Alles wird zu Vektoren** | Verschiedene Datentypen (Wörter, Pixel, Klänge) können alle in dieselbe numerische Darstellung umgewandelt werden. In einem gemeinsamen Einbettungsraum behandelt ein Transformer Bilddaten nicht anders als Text. |
| **Zwei Wege der Verbindung** | Self-Attention (Bild-Tokens direkt einfügen — einfach, heute Standard) oder Cross-Attention (dedizierte Brücken-Module — komplexer, aber effizienter bei vielen Bildern). Beide funktionieren. |
| **Freeze the Experts, Train the Connectors** | Man nutzt vortrainierte Modelle für jede Modalität, friert sie ein und trainiert nur die Verbindungsmodule. Das spart enorm Rechenzeit und Daten. |
| **Contrastive Learning richtet die Welten aus** | Durch das „Magnetspiel" lernt das System, dass zusammengehörige Bild-Text-Paare nahe beieinander liegen — die Grundlage für alles Weitere. |
| **Bilder kosten Tokens** | Ein hochauflösendes Bild verbraucht 800–1.600 Tokens — so viel wie mehrere Seiten Text. Das beeinflusst Kosten und Kontextfenster direkt. |

---

## Die Parallelen zu den vorherigen Tutorials

Es gibt schöne Verbindungslinien:

- **Tutorial 00-01 (LLMs):** Das Text-Gehirn in einem multimodalen Modell *ist* ein LLM. Attention, Tokens, Embeddings — alles kommt hier wieder zum Einsatz. Und die Token-Kosten-Logik gilt jetzt auch für Bilder.
- **Tutorial 00-02 (Diffusion):** CLIP, das dort den Textprompt in visuelle Anweisungen übersetzt, ist ein frühes Beispiel für multimodales Alignment. Cross-Attention, die dort Text mit Bilderzeugung verbindet, ist derselbe Mechanismus, der hier (in Variante B) Text mit Bildverständnis verbindet.

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
| **Cosine Similarity** | Maß für die Ähnlichkeit zweier Vektoren anhand ihrer Richtung (nicht Länge) — gleiche Richtung = ähnlich, rechtwinklig = unabhängig |
| **Cross-Attention** | Mechanismus, bei dem eine Sequenz (z.B. Text) eine andere Sequenz (z.B. Bild) nach relevanten Informationen befragt — Variante B der Modalitätsverbindung |
| **Self-Attention (bei Multimodal)** | Der normale Attention-Mechanismus des LLM, der hier sowohl Text- als auch Bild-Tokens gleichzeitig verarbeitet — Variante A, heute Standard |
| **CLIP** | OpenAIs Modell, das durch Contrastive Learning einen gemeinsamen Raum für Text und Bilder gelernt hat — trainiert auf 400 Mio. Bild-Text-Paaren |
| **LLaVA** | Einflussreiches Open-Source-Modell (2023), das den einfachen Ansatz „ViT + Projektion + LLM" popularisierte |
| **Flamingo** | DeepMinds multimodales Modell, das die „Freeze and Bridge"-Strategie mit Cross-Attention demonstrierte |
| **Nativ multimodal** | Modelle der neuesten Generation, die von Grund auf mit allen Modalitäten trainiert werden (statt nachträglicher Verbindung) |
| **Spektrogramm** | Visuelle Darstellung eines Audiosignals (Zeit × Frequenz) — wird wie ein Bild in Patches zerlegt und von einem Transformer verarbeitet |
| **Visual Tokens** | Bild-Kacheln, die als Token-Embedding in einen Transformer eingespeist werden — das Bild wird zur „Sequenz" |
| **Feature Alignment** | Der Prozess, bei dem die Darstellungen verschiedener Modalitäten in einen gemeinsamen Raum gebracht werden |

---

