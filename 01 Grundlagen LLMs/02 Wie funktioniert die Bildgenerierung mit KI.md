# Wie Diffusion-Modelle funktionieren

**Bildgenerierung mit KI verstehen — von reinem Rauschen zum fertigen Bild**

---

## Warum dieses Tutorial?

Sie haben wahrscheinlich schon Bilder gesehen, die komplett von einer KI erstellt wurden — fotorealistische Porträts, kunstvolle Illustrationen oder surreale Szenen. Vielleicht haben Sie sogar selbst schon mit Tools wie DALL·E, Midjourney oder dem Bildgenerator in ChatGPT experimentiert.

Aber wie funktioniert das eigentlich? Wie kann ein Computer aus ein paar Worten ein Bild erschaffen, das nie existiert hat?

Hier kommt die überraschende Antwort: **Diese Modelle zeichnen keine Bilder. Sie entfernen Rauschen.**

Und sobald Sie dieses eine Konzept verstanden haben, macht das gesamte System Sinn.

**Was Sie nach diesem Tutorial wissen werden:**

- Was Diffusion-Modelle sind und warum sie „rückwärts" arbeiten
- Wie das Training funktioniert — und warum es genial einfach ist
- Was eine U-Net-Architektur macht und warum sie so gut funktioniert
- Wie aus Text ein Bild wird (die Rolle von CLIP und Cross-Attention)
- Was CFG-Scale, Latent Space und VAE bedeuten
- Welche aktuellen Modelle es gibt und was sie unterscheidet

---

## Ein kurzer Blick zurück: Wie KI das Bildermachen lernte

Bevor wir in die Technik einsteigen, lohnt sich ein kurzer Blick auf die Geschichte — denn Diffusion-Modelle sind nicht vom Himmel gefallen. Sie sind das Ergebnis einer jahrzehntelangen Entwicklung:

### Die Vorgänger

| Zeitraum | Technologie | Was sie konnte |
|----------|------------|----------------|
| **1960er–2000er** | Regelbasierte Systeme (z.B. AARON) | Zeichnungen nach programmierten Regeln — wie ein Roboter, der Malen nach Zahlen macht |
| **2014** | **GANs** (Generative Adversarial Networks) | Zwei Netzwerke spielen gegeneinander: Eins erzeugt Bilder, eins bewertet sie. Wie ein Fälscher und ein Detektiv, die sich gegenseitig besser machen |
| **2015** | **DeepDream** (Google) | Verstärkte Muster in Bildern — die psychedelischen, traumartigen Bilder, die durchs Internet gingen |
| **2018** | **StyleGAN** | Erzeugte fotorealistische Gesichter von Menschen, die nicht existieren (thispersondoesnotexist.com) |
| **2021** | **DALL·E 1** (OpenAI) | Erster großer Text-zu-Bild-Generator, basierend auf der GPT-Architektur |
| **2021–2022** | **Diffusion-Modelle** | Überholten GANs in Bildqualität und wurden zum neuen Standard |
| **2022** | **Stable Diffusion, Midjourney, DALL·E 2** | Der Durchbruch — plötzlich konnte jeder KI-Bilder erstellen |

### Warum haben Diffusion-Modelle gewonnen?

GANs hatten ein grundlegendes Problem: Das Training war **instabil**. Die beiden Netzwerke (Fälscher und Detektiv) mussten perfekt ausbalanciert sein — zu oft brach das Training zusammen oder das Modell erzeugte immer wieder die gleichen wenigen Bilder.

Diffusion-Modelle sind dagegen **stabil und berechenbar**: Das Ziel ist klar definiert (Rauschen vorhersagen), das Training ist mathematisch robust, und die Ergebnisse werden mit mehr Training zuverlässig besser.

> **Übrigens:** 2018 wurde das KI-Kunstwerk *Edmond de Belamy* — erstellt mit einem GAN — bei Christie's für **432.500 US-Dollar** versteigert. Geschätzt war es auf 7.000–10.000 Dollar. Das war einer der Momente, in denen die Welt aufmerkte: KI kann Kunst.

---

## Die Analogie: Der Kunstrestaurator

Stellen Sie sich einen Kunstrestaurator vor, der so begabt ist, dass Sie ihm eine Leinwand geben könnten, die vollständig mit TV-Rauschen bedeckt ist — zufällige Pixel, nichts Erkennbares — und er würde vorsichtig das Rauschen wegpinseln, um darunter ein Gemälde freizulegen.

Kein Gemälde, das vorher existiert hat. Ein **völlig neues**.

Das ist ein Diffusion-Modell in einem Satz: **Eine KI, die gelernt hat, aus reinem Rauschen klare Bilder zu machen** — wie ein Restaurator, der ein Meisterwerk unter Schichten von Schmutz freilegt.

---

## Die zwei Phasen: Zerstören und Wiederherstellen

Das Prinzip funktioniert in zwei Richtungen:

### Phase 1: Vorwärts-Diffusion (das Bild zerstören)

Nehmen Sie ein schönes Foto und streuen Sie jede Sekunde ein bisschen Sand darauf. Mit der Zeit wird das Foto körniger, dann verschwommener, und irgendwann ist es nur noch zufälliges Rauschen — keine Spur mehr vom Original.

```
Schritt 1       Schritt 25      Schritt 50      Schritt 100
🖼️ Klares      🖼️ Leicht      🖼️ Stark       📺 Nur noch
   Foto           verrauscht     verrauscht      Rauschen
```

### Phase 2: Rückwärts-Diffusion (das Bild wiederherstellen)

Jetzt spulen Sie den Prozess zurück. Starten Sie bei reinem Rauschen und pinseln Sie vorsichtig ein bisschen Rauschen nach dem anderen weg — Sandkorn für Sandkorn — bis ein Bild erscheint.

```
Schritt 100     Schritt 75      Schritt 50      Schritt 1
📺 Nur noch    🖼️ Umrisse     🖼️ Details      🖼️ Klares
   Rauschen       erkennbar      erscheinen       Bild!
```

**Das Modell wird trainiert, genau diese Rückwärts-Phase auszuführen:** Rauschen Schritt für Schritt entfernen, bis ein stimmiges Bild entsteht. Nach genug Training können Sie ihm eine komplett „zerstörte" Leinwand aus purem Rauschen geben — und es „restauriert" ein Bild, das es vorher nie gab.

---

## Warum funktioniert das?

Der Erfolg von Diffusion-Modellen beruht auf zwei wunderbar einfachen Erkenntnissen:

### Erkenntnis 1: Trainingsdaten gibt es quasi unbegrenzt

Sie können **jedes beliebige Bild** nehmen und kontrolliert Rauschen hinzufügen. Und weil Sie das Rauschen selbst erzeugt haben, wissen Sie immer genau, wie viel Schaden Sie angerichtet haben. Das gibt Ihnen unendlich viele Trainingsbeispiele: „verrauschtes Bild + das bekannte Rauschen, das hinzugefügt wurde."

> **Bank-Analogie:** Es ist, als würden Sie hunderte Dokumente nehmen und absichtlich mit einem Kopierer in verschiedenen Qualitätsstufen kopieren — von „leicht unscharf" bis „komplett unleserlich". Weil Sie das Original haben, können Sie einem System beibringen, die Fehler zu korrigieren.

### Erkenntnis 2: Kleine Schritte statt großer Sprung

Von purem Rauschen direkt zu einem perfekten Bild zu springen ist unmöglich. Aber **ein kleines bisschen Rauschen entfernen**? Das ist ein viel einfacheres Problem. Durch das Verketten vieler kleiner Schritte erreicht das Modell eine dramatische Verwandlung.

Wenn ein Gemälde unter 100 Schichten Sand begraben ist, haben Sie viel bessere Chancen, es **Schicht für Schicht** freizulegen, als alle 100 Schichten auf einmal abzuschütteln.

---

## Wie das Training funktioniert

Der Trainingsablauf ist erstaunlich geradlinig:

1. **Nimm ein sauberes Bild** aus dem Datensatz
2. **Wähle eine zufällige Rauschstufe** (z.B. 30%, 50% oder 80%)
3. **Füge diese Menge Rauschen hinzu**
4. **Frage das Modell:** „Welches Rauschen wurde hier hinzugefügt?"
5. **Vergleiche** die Vorhersage des Modells mit dem echten Rauschen
6. **Passe die Parameter an**, damit die nächste Vorhersage besser wird

Weil Sie das Rauschen selbst erzeugt haben, kennen Sie immer die richtige Antwort. Das Modell wird mit jeder Runde besser darin, Rauschen in verrauschten Bildern zu erkennen.

> **Der Schlüssel:** Das Modell **merkt sich keine Bilder auswendig**. Es lernt eine allgemeine Fähigkeit: „Gegeben ein teilweise verrauschtes Bild — wie könnte das Original ausgesehen haben?" Und weil Rauschen zufällig ist, lernt das Modell, Details **kreativ** zu ergänzen. So entstehen bei der Bildgenerierung völlig neue Bilder.

Vergleichen Sie das mit dem LLM-Training aus dem vorherigen Tutorial: Dort war es „Wort vorhersagen, vergleichen, korrigieren". Hier ist es „Rauschen vorhersagen, vergleichen, korrigieren." Das gleiche Prinzip — nur in der Bildwelt.

---

## Die U-Net-Architektur: Gleichzeitig Wald und Bäume sehen

Für die komplexe Aufgabe der Rauschentfernung nutzen Diffusion-Modelle eine spezielle Netzwerk-Architektur namens **U-Net**. Der Name kommt von der U-förmigen Struktur.

Stellen Sie sich das U-Net wie einen Kunstrestaurator mit Gleitsichtbrille vor: Er kann gleichzeitig das **gesamte Bild** überblicken und die **einzelnen Pinselstriche** erkennen.

### Wie funktioniert das?

**Komprimieren (Encoder — die linke Seite des U):**
Das Netzwerk „zoomt heraus" — es komprimiert das verrauschte Bild in eine kleinere, einfachere Form. So erkennt es die groben Strukturen: „Da ist ungefähr ein Gesicht, oben ist Himmel."

**Expandieren (Decoder — die rechte Seite des U):**
Dann „zoomt" es wieder hinein — es vergrößert die komprimierte Darstellung zurück zur Originalgröße und fügt dabei Details hinzu.

**Skip Connections (die Brücken im U):**
Das Geheimnis sind die Querverbindungen zwischen Encoder und Decoder. Sie sorgen dafür, dass feine Details aus den frühen Schichten direkt an die späten Schichten weitergegeben werden. So „vergisst" das Netzwerk nie die Detailinformationen, während es die Gesamtstruktur analysiert.

```
Eingabe                                     Ausgabe
(verrauscht)                            (Rauschen-Vorhersage)
    │                                         ▲
    ▼                                         │
┌─────────┐  ──── Skip Connection ────→ ┌─────────┐
│ Detail-  │                             │ Detail-  │
│ Schicht  │                             │ Schicht  │
└────┬─────┘  ──── Skip Connection ────→ └────▲─────┘
     ▼                                        │
  ┌──────┐   ──── Skip Connection ────→  ┌──────┐
  │Mittel │                               │Mittel │
  └───┬───┘                               └───▲───┘
      ▼                                       │
    ┌────┐                                 ┌────┐
    │Kern│ ─────────────────────────────→  │Kern│
    └────┘    (Gesamtstruktur erkannt)     └────┘
```

> **Warum ist das wichtig?** Dieses Design erlaubt es dem Netzwerk, **gleichzeitig** darüber nachzudenken, wie ein Objekt insgesamt aussehen sollte (die Form eines Hundes) **und** welches Rauschen an einer bestimmten Stelle entfernt werden muss (die Fellstruktur genau dort).

---

## Die vollständige Pipeline: Vom Rauschen zum Bild

### Schritt 1–4: Trainingsbilder → Rausch-Maschine → U-Net → Training

Die ersten vier Schritte haben wir schon kennengelernt: Bilder sammeln, Rauschen hinzufügen können, U-Net bauen, trainieren. Nach Millionen von Durchläufen ist das Modell ein Experte im Rauschen-Vorhersagen.

### Schritt 5: Bilder erzeugen durch Rückwärts-Entrauschung

Jetzt wird es spannend. Starten Sie mit einer Leinwand aus purem Zufallsrauschen:

1. Gib das aktuelle Rauschbild ins trainierte U-Net
2. Das U-Net sagt vorher: „Dieses Rauschen muss entfernt werden"
3. Ziehe das vorhergesagte Rauschen ab
4. Wiederhole — Schritt für Schritt wird das Bild klarer

```
Schritt T:   📺 Reines Rauschen
Schritt T-1: 📺 Etwas weniger Rauschen (kaum sichtbar)
    ...
Schritt 50:  🖼️ Grobe Formen erkennbar
    ...
Schritt 10:  🖼️ Klares Bild mit Details
Schritt 1:   🖼️ Fertiges Bild!
```

Das Modell versucht nie, direkt von Rauschen zu einem perfekten Bild zu springen. Es geht immer **ein Körnchen Rauschen nach dem anderen**.

### Schritt 6: Latent Space — Der Turbo-Trick

Auf Bildern in voller Auflösung zu arbeiten ist quälend langsam. Die Lösung (verwendet z.B. von Stable Diffusion und Flux): Die Diffusion findet auf einer **komprimierten Darstellung** statt.

Stellen Sie sich vor: Statt ein riesiges Wandgemälde zu restaurieren, schrumpfen Sie es erst auf eine Skizze im Notizbuch, restaurieren die Skizze, und vergrößern sie dann wieder.

In der Praxis macht das ein **VAE** (Variational Autoencoder):
- **Encoder:** Komprimiert ein 512×512-Bild auf ein 64×64-Gitter (ca. 64× weniger Daten)
- Alle Diffusionsschritte passieren auf diesem kompakten Gitter
- **Decoder:** Am Ende wird das Ergebnis zurück auf volle Auflösung hochgerechnet

> **Das macht Diffusion-Modelle alltagstauglich.** Ohne Latent Space bräuchte man Supercomputer. Mit Latent Space läuft es auf einer normalen Grafikkarte.

### Schritt 7: Textsteuerung mit CLIP — Aus Worten werden Bilder

Bis hierhin kann das Modell zwar Bilder erzeugen — aber **welches** Bild, das ist zufällig. Damit Sie per Text steuern können, was entsteht, kommt **CLIP** ins Spiel.

**CLIP** (Contrastive Language-Image Pre-training) wurde mit Millionen von Bild-Text-Paaren trainiert. Es versteht die Beziehung zwischen Wörtern und visuellen Merkmalen: Es weiß, dass „Sonnenuntergang" zu Orangetönen gehört und „Ozean" zu blauen Wellenmustern.

**So funktioniert die Textsteuerung:**

1. Sie schreiben: *„Eine Volksbank-Filiale bei Sonnenuntergang, im Stil eines Ölgemäldes"*
2. CLIP wandelt diesen Text in einen **numerischen Vektor** um (wie die Embeddings bei LLMs!)
3. Dieser Vektor wird dem U-Net bei **jedem Entrauschungsschritt** mitgegeben
4. Das U-Net nutzt **Cross-Attention**, um den Text-Vektor mit der Bildbearbeitung zu verknüpfen

> **Cross-Attention** funktioniert wie das Self-Attention aus dem LLM-Tutorial — nur dass hier nicht Wörter auf andere Wörter schauen, sondern **Bildbereiche auf Textwörter schauen**. Der Bildbereich „oberer Hintergrund" richtet seine Aufmerksamkeit auf „Sonnenuntergang" und wird entsprechend orange eingefärbt.

Es ist, als hätte der Restaurator einen Übersetzer neben sich, der ihm bei jedem Pinselstrich zuflüstert: *„Hier mehr Orange für den Sonnenuntergang… dort eine Horizontlinie…"*

---

## Der CFG-Scale-Trick: Wie stark soll der Text wirken?

Moderne Systeme verwenden einen Trick namens **Classifier-Free Guidance (CFG)**. Er verstärkt den Einfluss Ihres Textprompts auf das erzeugte Bild.

**Die Analogie:** Die KI malt zwei Versionen des Bildes — eine **mit** Ihren Anweisungen und eine **ohne**. Dann vergleicht sie beide und schiebt das Endergebnis extra weit in Richtung der Version mit Anweisungen.

| CFG-Scale | Wirkung | Praxis |
|-----------|---------|--------|
| **1–3** | Modell ignoriert den Prompt fast — sehr freie, oft abstrakte Ergebnisse | Selten nützlich |
| **5–7** | Gute Balance zwischen Kreativität und Prompt-Treue | **Empfohlen für die meisten Aufgaben** |
| **8–12** | Strikte Prompt-Befolgung, weniger künstlerische Freiheit | Wenn das Bild genau dem Prompt entsprechen soll |
| **15+** | Übertrieben — Bilder werden oft übersättigt oder verzerrt | Nur für Experimente |

> **Praxis-Tipp:** Wenn Sie in einem Bildgenerator einen Schieberegler für „Guidance Scale" oder „CFG" sehen, wissen Sie jetzt, was dahintersteckt. Für die meisten Aufgaben ist ein Wert von **5–7** ein guter Startpunkt.

---

## Die aktuelle Modell-Landschaft (Stand: Februar 2026)

Die Welt der Bildgenerierung hat sich in den letzten Jahren rasant entwickelt. Hier ein Überblick über die wichtigsten Modelle und ihre Besonderheiten:

### 🖼️ Reine Bildgenerierung

| Modell | Hersteller | Besonderheiten | Zugang |
|--------|-----------|----------------|--------|
| **DALL·E 3 / GPT Image** | OpenAI | Integriert in ChatGPT, starke Text-im-Bild-Fähigkeit, einfachste Bedienung | ChatGPT, API |
| **Midjourney V7** | Midjourney Inc. | Führend bei Ästhetik und künstlerischem Stil, extrem beliebtes Community-Tool | Web-App, Discord |
| **Flux 1.1 / 2.0** | Black Forest Labs (🇩🇪 Freiburg!) | Open Source (teilweise), hervorragende Textdarstellung, bis 4 Megapixel, sehr gute Prompt-Treue | API, Replicate, lokal |
| **Imagen 4** | Google DeepMind | Ultra-schneller Modus (10× schneller), bis 2K Auflösung, in Gemini integriert | Gemini, Vertex AI |
| **Nano Banana Pro** | Community/Open Source | Leichtgewichtiges Modell, gut für schnelle Generierung und agentenbasierte Workflows | Replicate, lokal |
| **Stable Diffusion 3.5** | Stability AI | Der Open-Source-Pionier, riesige Community, unzählige Fine-Tunings und LoRAs | Lokal, API |

### 🎬 Video-Generierung (Diffusion + Temporal)

Die gleiche Diffusion-Technik wird mittlerweile auch für **Videos** eingesetzt — mit einer zusätzlichen zeitlichen Dimension:

| Modell | Hersteller | Besonderheiten |
|--------|-----------|----------------|
| **Sora 2** | OpenAI | Text-zu-Video mit synchronem Audio, bis zu mehrere Minuten |
| **Kling** | Kuaishou (🇨🇳) | Starke Bewegungsqualität, Text-zu-Video und Bild-zu-Video |
| **Seedance 2.0** | ByteDance (🇨🇳) | Neuester Hype (Feb. 2026): Multimodal (Text + Bild + Audio → Video), vereinte Architektur, virale Clips mit realistischen Schauspielern |
| **Veo 2** | Google DeepMind | Hochauflösende Videos, in Gemini integriert |

> **Wie funktionieren Video-Modelle?** Im Kern nutzen sie dasselbe Diffusion-Prinzip — aber statt eines einzelnen Bildes wird ein **ganzer Stapel von Bildern** (Frames) gleichzeitig entrauscht. Eine zusätzliche **temporale Attention** sorgt dafür, dass aufeinanderfolgende Frames konsistent bleiben und Bewegungen flüssig aussehen. Mehr dazu im späteren Tutorial zu Video-Modellen.

### Was unterscheidet die Modelle?

Alle modernen Bildgeneratoren basieren auf Diffusion — aber sie unterscheiden sich in wichtigen Details:

| Aspekt | Unterschiede |
|--------|-------------|
| **Architektur** | Klassisches U-Net (Stable Diffusion) vs. DiT/Transformer-basiert (Flux, neuere Modelle) |
| **Text-Encoder** | CLIP allein vs. T5 + CLIP kombiniert (Flux) vs. integrierte LLM-Encoder (Imagen, DALL·E 3) |
| **Latent Space** | Unterschiedliche VAE-Qualität beeinflusst Schärfe und Details |
| **Training** | Welche und wie viele Bilder, welche Auflösungen, wie lange trainiert |
| **Ästhetik** | Midjourney → künstlerisch/warm; Flux → scharf/prompt-treu; DALL·E → natürlich/sicher |
| **Open Source** | Flux (teilweise), Stable Diffusion (ja) vs. Midjourney, DALL·E (nein) |

> **Besonders interessant:** Flux kommt aus **Freiburg** — die Gründer von Black Forest Labs haben vorher an der LMU München an Stable Diffusion geforscht. Ein deutsches Spitzenprodukt in der KI-Welt! 🇩🇪

---

## Die vollständige Pipeline auf einen Blick

```
    Ihr Prompt                          CLIP
„Volksbank bei                    (Text → Vektor)
 Sonnenuntergang"                      │
                                       ▼
                              ┌─────────────────┐
 Zufälliges    ──────────→    │     U-Net        │    ──────→  Entrauschtes
 Rauschen                     │  (mit Cross-     │              Latent-Bild
 (Latent)                     │   Attention)     │              (Latent)
                              └─────────────────┘
                                       │
                              (Wiederholen: T Schritte)
                                       │
                                       ▼
                              ┌─────────────────┐
                              │   VAE Decoder    │    ──────→  🖼️ Fertiges
                              │ (Latent → Pixel) │              Bild!
                              └─────────────────┘
```

---

## Das Wichtigste auf einen Blick

| Erkenntnis | Was das bedeutet |
|-----------|-----------------|
| **Diffusion-Modelle „ent-zeichnen" Rauschen** | Sie zeichnen keine Bilder — sie entfernen Schritt für Schritt Rauschen, bis ein Bild erscheint. Zerstörung rückwärts. |
| **Vorwärts-Rauschen ist einfach, Rückwärts-Entrauschen wird gelernt** | Unbegrenzte Trainingsdaten durch kontrolliertes Hinzufügen von Rauschen. Das Modell lernt die Umkehrung. |
| **U-Nets sehen Wald und Bäume gleichzeitig** | Die U-förmige Architektur mit Skip Connections erfasst grobe Strukturen und feine Details in einem Durchgang. |
| **Latent Space macht es praktisch** | Komprimierung vor der Diffusion reduziert den Rechenaufwand um das 64-Fache. |
| **Text ist nur ein Steuerungssystem** | Das Kernmodell erzeugt Bilder. CLIP übersetzt Ihre Worte in visuelle Anweisungen, die das U-Net bei jedem Schritt leiten. |

---

## Werkzeuge und Stellschrauben: Was Sie als Anwender beeinflussen können

Wenn Sie mit einem Bildgenerator arbeiten, haben Sie — je nach Tool — verschiedene Einstellungen zur Verfügung. Hier die wichtigsten:

### Die wichtigsten Parameter

| Parameter | Was er bewirkt | Empfehlung |
|-----------|---------------|------------|
| **Prompt** (positiv) | Beschreibt, was im Bild sein soll | So präzise wie möglich: Stil, Inhalt, Stimmung, Perspektive |
| **Negative Prompt** | Beschreibt, was **nicht** im Bild sein soll | Z.B. „blurry, low quality, text, watermark" — filtert unerwünschte Elemente |
| **CFG-Scale / Guidance** | Wie stark der Prompt das Bild beeinflusst (siehe oben) | 5–7 für die meisten Aufgaben |
| **Steps** | Wie viele Entrauschungsschritte durchgeführt werden | 20–30 ist meist optimal; mehr = langsamer, aber nicht immer besser |
| **Seed** | Startwert für den Zufall — gleicher Seed = gleiches Bild | Nützlich zum Reproduzieren oder Variieren eines guten Ergebnisses |
| **Sampler** | Mathematische Methode für die Entrauschung (Euler, DPM++, etc.) | Voreinstellung reicht meist; Fortgeschrittene können experimentieren |
| **Auflösung** | Bildgröße in Pixeln | Modellabhängig; typisch: 512×512, 768×768, 1024×1024 |

### Erweiterte Werkzeuge (für Fortgeschrittene)

| Werkzeug | Was es tut |
|----------|-----------|
| **LoRA** (Low-Rank Adaptation) | Kleines Feintuning-Modul, das einem Modell einen bestimmten Stil oder ein Gesicht beibringt — ohne das ganze Modell neu zu trainieren |
| **Inpainting** | Einen bestimmten Bereich im Bild markieren und nur dort neu generieren — z.B. ein Objekt ersetzen |
| **Outpainting** | Das Bild über seinen Rand hinaus erweitern — die KI „malt weiter" |
| **Image-to-Image** | Ein bestehendes Bild (Foto, Skizze) als Ausgangspunkt nehmen und per Prompt transformieren |
| **ControlNet** | Zusätzliche Steuerung über Kanten, Tiefe oder Pose — die KI folgt einer Vorlage |
| **Upscaling** | Ein kleines Bild mit KI-Unterstützung auf höhere Auflösung vergrößern |

> **Für den Bankalltag:** Die meisten dieser Parameter müssen Sie nicht kennen, wenn Sie ChatGPT oder Gemini zum Bilderzeugen nutzen — die sind im Hintergrund voreingestellt. Aber wenn Sie verstehen, was dahintersteckt, können Sie gezielter prompten und bessere Ergebnisse erzielen.

### Verschiedene Wege zum Bild

Moderne KI-Bildgenerierung bietet verschiedene Eingangswege:

| Methode | Beschreibung | Beispiel |
|---------|-------------|---------|
| **Text-zu-Bild** | Beschreibung eingeben → Bild entsteht | „Ein modernes Bankgebäude im Bauhaus-Stil" |
| **Bild-zu-Bild** | Bestehendes Bild + Prompt → verändertes Bild | Foto der Filiale → im Stil eines Aquarells |
| **Bild-zu-Video** | Ein Standbild wird animiert | Teamfoto → kurzes Video mit subtiler Bewegung |
| **Text-zu-Video** | Beschreibung eingeben → Video entsteht | „Ein Spaziergang durch eine sonnige Kleinstadt" |

---

## Die Parallele zu LLMs

Es gibt eine schöne Verbindung zum vorherigen Tutorial:

- **LLMs** generieren Text, indem sie das **nächste Wort** vorhersagen
- **Diffusion-Modelle** generieren Bilder, indem sie das **nächste Rauschen** vorhersagen

Beide zerlegen eine komplexe Generierungsaufgabe in eine Reihe **kleiner Vorhersageschritte**. Und beide produzieren Ergebnisse, die erstaunlich intelligent wirken — obwohl der zugrundeliegende Mechanismus überraschend einfach ist.

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **Diffusion** | Der Prozess, bei dem schrittweise Rauschen zu einem Bild hinzugefügt (vorwärts) oder entfernt (rückwärts) wird |
| **U-Net** | Die U-förmige Netzwerk-Architektur, die gleichzeitig grobe Strukturen und feine Details verarbeitet |
| **Skip Connection** | Querverbindung im U-Net, die Detailinformationen direkt an spätere Schichten weitergibt |
| **VAE** | Variational Autoencoder — komprimiert Bilder in einen kleineren Latent Space und wieder zurück |
| **Latent Space** | Der komprimierte „Skizzen-Raum", in dem die eigentliche Diffusion stattfindet |
| **CLIP** | Das Modell, das die Beziehung zwischen Text und Bildern versteht und als Übersetzer dient |
| **Cross-Attention** | Mechanismus, bei dem Bildbereiche auf Textwörter „schauen", um die Generierung zu steuern |
| **CFG-Scale** | Classifier-Free Guidance — bestimmt, wie stark der Textprompt die Bildgenerierung beeinflusst |
| **Denoising** | Der Prozess des Rauschentfernens — der Kernvorgang der Bildgenerierung |
| **DiT** | Diffusion Transformer — neuere Architektur, die das U-Net durch Transformer ersetzt (z.B. in Flux) |
| **LoRA** | Low-Rank Adaptation — Methode zum Feintuning eines Modells auf einen bestimmten Stil mit wenig Rechenaufwand |
| **GAN** | Generative Adversarial Network — Vorgänger-Technologie: zwei Netzwerke (Fälscher + Detektiv) trainieren sich gegenseitig |
| **Seed** | Startwert für den Zufallsgenerator — gleicher Seed erzeugt bei gleichen Einstellungen dasselbe Bild |
| **Negative Prompt** | Text, der beschreibt, was im Bild **nicht** erscheinen soll |
| **Inpainting** | Gezieltes Neuerstellen eines markierten Bildbereichs bei unverändertem Rest |
| **ControlNet** | Zusatzmodul zur Steuerung der Bildgenerierung über Kanten, Tiefe oder Pose |

---


