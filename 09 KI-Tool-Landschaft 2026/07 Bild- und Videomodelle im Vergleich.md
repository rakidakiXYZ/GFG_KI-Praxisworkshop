# Bild- und Videomodelle im Vergleich

**Welches Modell für welchen visuellen Zweck — von Midjourney bis Veo**

---

## Warum dieses Tutorial?

Bild- und Videogenerierung ist ein eigenes Universum neben den Textmodellen. Während bei den Textassistenten „fünf große Namen" den Markt prägen, gibt es bei den visuellen Modellen deutlich mehr Player — und sie unterscheiden sich in der Charakteristik oft stärker als bei Textmodellen. Midjourney-Bilder sehen anders aus als Flux-Bilder. Veo-Videos haben ein anderes Gefühl als Runway-Clips.

Für Einsteiger ist das verwirrend. Dieses Kapitel räumt auf.

**Was Sie nach diesem Tutorial wissen werden:**

- Welche Bildmodelle 2026 relevant sind und wofür jedes besonders gut ist
- Welche Videomodelle aktuell am weitesten fortgeschritten sind
- Wann Sie welches Modell nehmen sollten
- Welche Preispläne für welche Zielgruppe passen
- Worauf Sie bei deutschen / europäischen Nutzungsfragen (Urheberrecht, Datenschutz) achten sollten

> **Hinweis:** Dieses Kapitel ergänzt die bestehenden Kapitel **04 (Prompt Engineering Bilder)** und **05 (Prompt Engineering Videos)**. Wenn Sie nach konkreten Prompts suchen, schauen Sie dort. Hier geht es nur um die Tool-Auswahl.

---

## Teil 1 — Bildmodelle

### Die großen Namen im Überblick

| Modell | Anbieter | Stärke in einem Satz |
|--------|----------|----------------------|
| **Midjourney** | Midjourney Inc. | Künstlerische Qualität, Atmosphäre, Stilgefühl |
| **Flux** (Pro / Dev / Schnell) | Black Forest Labs | Präzise Textbefolgung, Kontrolle, Geschwindigkeit |
| **Nano Banana** (Gemini Image) | Google | Günstig, schnell, sehr guter Allrounder |
| **DALL·E** (in ChatGPT) | OpenAI | Einfachster Zugang, in ChatGPT integriert |
| **Ideogram** | Ideogram | Bestes Modell für Text im Bild |
| **Leonardo AI** | Leonardo.ai | Großer Free-Tier, eigene Fine-Tunes |
| **Adobe Firefly** | Adobe | In Creative Cloud integriert, kommerziell sauber |
| **Stable Diffusion** (lokal) | Stability AI + Community | Kostenlos, offen, lokal betreibbar |

### Midjourney — der Künstler

Midjourney ist seit Jahren der Maßstab für **ästhetische Bildqualität**. Wenn Sie ein Bild mit starker Atmosphäre, dramatischem Licht, kunstvollem Stil brauchen — Midjourney ist bis heute schwer zu schlagen. Aktuelle Versionen (v6, v7) sind sehr gut darin, Prompts zu interpretieren und konsistent hochwertige Ergebnisse zu liefern.

**Stärken:**
- Überragende ästhetische Qualität
- Sehr gute Stil-Konsistenz
- Große Community mit vielen Beispielen

**Schwächen:**
- Kein Free-Tier — Sie müssen zahlen, um überhaupt zu starten
- Weniger präzise bei genauen Vorgaben („links drei Äpfel, rechts ein Glas Wasser" wird nicht perfekt)
- Text im Bild ist eine Schwäche
- Der Zugang lief lange über Discord — 2026 gibt es eine Web-App, aber die Bedienung bleibt gewöhnungsbedürftig

**Preise:** Basic ab ca. 10 USD pro Monat, Standard ab ca. 30 USD, Pro ab ca. 60 USD. Die Preise sind im Laufe des Jahres 2025/2026 leicht gestiegen.

**Für wen?** Kreative, Designer, Illustratoren, alle die Bildästhetik als Produkt brauchen.

### Flux — der präzise Techniker

**Flux** kommt von Black Forest Labs, einem deutschen Unternehmen, das 2024 aus dem Stable-Diffusion-Umfeld hervorging. Die Flux-Modelle haben einen wichtigen Unterschied zu Midjourney: **Sie folgen Prompts sehr viel präziser.**

Es gibt drei Varianten:

- **Flux Schnell** — schnell, günstig, gute Qualität für den Alltag
- **Flux Dev** — offenes Modell für Entwickler und lokale Nutzung
- **Flux Pro** — das Flaggschiff, höchste Qualität

Flux ist besonders stark, wenn Sie **konkrete Anweisungen** haben („Ein Ingenieur in Latzhose steht vor einem roten Traktor, im Hintergrund ein Bauernhof mit blauen Toren, Nachmittagslicht") — die Ergebnisse folgen der Beschreibung ungewöhnlich genau.

**Für wen?** Entwickler, Profis, die in einen Workflow einbauen wollen, alle die präzise Kontrolle über ihre Bilder brauchen. Flux ist auch über viele Drittanbieter-Plattformen zugänglich (Replicate, fal.ai, Leonardo AI, Poe).

**Besonderheit:** Da Black Forest Labs deutsch ist, gibt es für europäische Nutzer ein paar datenschutzrechtliche Argumente. Und Flux Dev lässt sich lokal betreiben — siehe Kapitel 06.

### Nano Banana — das Preis-Leistungs-Wunder

**Nano Banana** ist der inoffizielle Name für Googles Gemini-Bildmodell, das 2025 als extrem günstige, schnelle und gut qualitative Alternative eingeschlagen ist. Sie erreichen es entweder über die Gemini-App, über Google AI Studio, über die Gemini-API — oder eingebettet in andere Tools.

**Stärken:**
- Extrem günstig (oft Bruchteile eines Cents pro Bild in der API)
- Sehr schnell (wenige Sekunden pro Bild)
- Sehr gute Text-Treue (es befolgt Anweisungen zuverlässig)
- Gut im Verarbeiten von bestehenden Bildern („Ändere die Hintergrundfarbe zu Blau")
- Multimodal: nimmt Text und Bild als Input

**Schwächen:**
- Die rein ästhetische Qualität ist nicht ganz auf Midjourney-Niveau — bei „künstlerischen" Aufgaben sieht man den Unterschied
- Manche Stile (Aquarell, abstrakte Kunst, bestimmte Fotostile) sind nicht die Stärke
- Weniger Kontrolle über Feinheiten als bei Flux Pro

**Für wen?** Absolut jeder, der viele Bilder in solider Qualität zu kleinen Kosten braucht. Tutorials, Präsentationen, Social-Media, Blog-Beiträge, interne Mockups.

**Hinweis:** Die Illustrationen in diesem Tutorial-Repo werden über Nano Banana generiert — Sie sehen also selbst ein Beispiel für das, was machbar ist.

### DALL·E — der bequeme Einsteiger

**DALL·E** ist OpenAIs Bildmodell. Sie brauchen es nicht als eigenes Tool zu starten — es ist in ChatGPT eingebaut. Sie schreiben einfach „Erstelle mir ein Bild von …" und ChatGPT ruft DALL·E im Hintergrund auf.

**Stärken:**
- Maximale Bequemlichkeit — kein zusätzliches Tool, keine zusätzlichen Kosten, wenn Sie ohnehin ChatGPT Plus haben
- Gut integriert mit dem Chat — Sie können über mehrere Runden hinweg verfeinern („Mach den Himmel dunkler", „Füge einen Hund hinzu")

**Schwächen:**
- Qualitativ 2026 nicht mehr führend — Midjourney, Flux und Nano Banana sind in verschiedenen Dimensionen besser
- Weniger Kontrollmöglichkeiten

**Für wen?** Gelegenheitsnutzer, die ein Bild wollen, ohne ein zusätzliches Tool zu lernen.

### Ideogram — der Typograf

**Ideogram** hat eine ganz spezielle Stärke: **Text im Bild.** Wenn Sie ein Poster, ein Logo-Konzept, ein Social-Media-Bild mit eingebettetem Text (eine Schlagzeile, ein Zitat, einen Slogan) brauchen, ist Ideogram 2026 noch immer die beste Wahl. Die anderen Modelle haben aufgeholt, aber Ideogram bleibt bei Typografie präzise.

**Preise:** Free-Tier (begrenzt), Pro ab ca. 10 USD pro Monat.

**Für wen?** Marketing, Social-Media-Creator, alle die Bilder mit Text produzieren.

### Leonardo AI — der Free-Tier-Champion

**Leonardo AI** bietet eines der großzügigsten kostenlosen Kontingente am Markt: je nach Stand etwa 150 Bilder pro Tag im Free-Tier. Dazu kommen viele Fine-Tune-Modelle für spezielle Stile (Fantasy, Anime, Fotorealismus, etc.) und eine benutzerfreundliche Oberfläche.

**Für wen?** Einsteiger, die ohne Ausgabe einen ernsthaften Eindruck bekommen wollen. Bastler, die viel experimentieren wollen.

### Adobe Firefly — die saubere kommerzielle Option

**Adobe Firefly** ist in Creative Cloud (Photoshop, Illustrator, Express) integriert und hat ein wichtiges Alleinstellungsmerkmal: **Adobe garantiert, dass die Trainingsdaten kommerziell unproblematisch sind** (nur Stock-Fotos aus Adobe Stock, gemeinfrei, etc.). Wer Bilder für kommerzielle Projekte braucht und Rechtssicherheit will, landet deshalb oft bei Firefly.

**Für wen?** Agenturen, Marketing-Abteilungen, alle die rechtlich unbedenkliche Bilder brauchen und ohnehin Adobe-Abonnenten sind.

### Stable Diffusion (lokal)

**Stable Diffusion** ist das wichtigste offene Bildmodell. Sie können es kostenlos auf Ihrem eigenen Rechner laufen lassen — ähnlich wie Ollama für Text. Dafür gibt es Tools wie **ComfyUI**, **Automatic1111** oder **InvokeAI**. Die Einrichtung ist etwas aufwändiger, aber dafür bekommen Sie volle Kontrolle, kein Limit und vollständige Privatsphäre.

**Für wen?** Bastler, Entwickler, Datenschutz-Sensible, alle die tief in die Möglichkeiten einsteigen wollen.

---

## Teil 2 — Videomodelle

Videogenerierung ist 2026 noch stärker in Bewegung als Bildgenerierung. Jedes halbe Jahr kommt ein neues Modell, das die Messlatte verschiebt. Hier der Stand April 2026:

### Die wichtigsten Videomodelle

| Modell | Anbieter | Stärke |
|--------|----------|--------|
| **Google Veo 3** | Google | Beste Gesamtqualität, native Audio-Generierung |
| **Runway Gen-4** | Runway | Profi-Tool, beste Character-Konsistenz |
| **Luma Dream Machine** | Luma AI | Schnell, günstig, schöne Bewegungen |
| **Kling** | Kuaishou | Sehr gute Qualität, aus China |
| **Pika** | Pika Labs | Kreativ, kontrollierbar, gute Effekte |
| **Hunyuan Video** | Tencent | Open-Source, lokal betreibbar |

### Google Veo 3 — aktueller Qualitätsführer

**Veo 3** ist Googles Videomodell und gilt im Frühjahr 2026 als eines der qualitativ stärksten verfügbaren Modelle. Die Besonderheit: **Veo generiert nicht nur Bild, sondern auch passenden Ton — Stimmen, Umgebungsgeräusche, Musik.** Das ist ein großer Unterschied zu anderen Anbietern, die nur stumme Clips liefern.

**Zugang:** Über Google AI Pro und Google AI Ultra (siehe Kapitel 04 zum Google-Ökosystem).

**Für wen?** Alle, die ernsthaft kurze Video-Clips (bis 10 Sekunden) generieren wollen und dabei auf Audio-Qualität Wert legen. Besonders praktisch für Social-Media-Creator, Werbespots, Konzept-Entwürfe.

### Runway Gen-4 — das Profi-Werkzeug

**Runway** ist der bekannteste Video-Anbieter der ersten Stunde und hat sich auf den Profi-Bereich spezialisiert. Runway Gen-4 bietet:

- Gute Character-Konsistenz (Figuren bleiben über mehrere Clips ähnlich)
- Image-to-Video (ein existierendes Bild animieren)
- Video-to-Video (einen Clip in einen anderen Stil überführen)
- Eine umfangreiche Editing-Oberfläche mit vielen Profi-Funktionen

**Preise:** Standard ab ca. 15 USD pro Monat, Pro ab ca. 35 USD pro Monat, Unlimited ab ca. 95 USD pro Monat.

**Für wen?** Creator, Video-Professionals, Werbeagenturen.

### Luma Dream Machine — der günstige Allrounder

**Luma** hat eine einfache, schnelle Oberfläche und liefert erstaunlich gute Ergebnisse zu moderatem Preis. Die Clip-Qualität ist hoch, die Bewegungen sind meist natürlich, und der Einstieg ist einfach.

**Preise:** Free-Tier vorhanden, Pro ab ca. 10 USD pro Monat.

**Für wen?** Einsteiger, die mit Video experimentieren wollen, ohne direkt ein Premium-Abo zu zahlen.

### Kling — der chinesische Player

**Kling** kommt von der chinesischen Firma Kuaishou und bietet 2026 eine Qualität, die mit westlichen Anbietern mithalten kann. Besonders bei bestimmten Bewegungsarten (schnelle Kamerafahrten, Kampfszenen) ist Kling überraschend stark. Der Zugang ist für europäische Nutzer aber etwas umständlich, und die Datenschutz-Überlegungen ähneln denen von DeepSeek: Vorsicht bei sensiblen Inhalten.

### Pika — der kreative Spieler

**Pika** ist als verspielter, kreativer Video-Generator bekannt. Weniger „filmische Qualität" als Veo oder Runway, aber mit vielen kreativen Effekten und Modi. Gute Wahl für experimentelle Projekte.

### Lokale Video-Modelle

Es gibt offene Video-Modelle wie **Hunyuan Video** (Tencent), die sich theoretisch lokal betreiben lassen. In der Praxis ist das 2026 noch nichts für Otto-Normal-Nutzer: Die Hardware-Anforderungen sind sehr hoch (24 GB VRAM aufwärts), die Qualität ist nicht auf Cloud-Niveau, und die Einrichtung ist aufwändig. Für Bastler und Entwickler interessant, für alle anderen: warten.

---

## Teil 3 — Welches Modell für welchen Zweck?

Ein kleiner, praktischer Entscheidungsbaum:

### Bildgenerierung

**Ich will schnell ein gutes Bild für eine Präsentation / Blog / Social Media.**
→ **Nano Banana** (über Gemini oder API) oder **DALL·E** (in ChatGPT)

**Ich brauche ein besonders schönes, atmosphärisches Bild — es soll aussehen wie Kunst.**
→ **Midjourney**

**Ich brauche ein Bild, das einem sehr genauen, detaillierten Prompt folgen muss.**
→ **Flux Pro** oder **Flux Dev**

**Ich brauche ein Bild mit Text darin (Poster, Logo-Idee, Zitat).**
→ **Ideogram**

**Ich will kommerziell rechtssicher arbeiten und bin Adobe-Kunde.**
→ **Adobe Firefly**

**Ich habe Datenschutz-Bedenken oder will kostenlos arbeiten.**
→ **Stable Diffusion lokal** (über ComfyUI, LM Studio für Bilder, oder ähnliche Tools) oder **Flux Dev lokal**

**Ich bin Einsteiger und will erstmal ausprobieren.**
→ **Leonardo AI** (großer Free-Tier) oder **Gemini Free** (für Nano Banana)

### Videogenerierung

**Ich will das beste aktuell verfügbare Modell.**
→ **Google Veo 3** (über Google AI Pro)

**Ich arbeite professionell und brauche Kontrolle und Character-Konsistenz.**
→ **Runway Gen-4**

**Ich will günstig und schnell experimentieren.**
→ **Luma Dream Machine**

**Ich will kreative Effekte und Experimente.**
→ **Pika**

**Ich will ein bestehendes Bild animieren.**
→ **Runway Gen-4** oder **Luma Dream Machine**

---

## Für deutsche und europäische Nutzer

### Urheberrecht

Bei allen Bild- und Videomodellen gilt 2026: **Die Rechtslage zu KI-generierten Inhalten ist international im Umbruch.** Das Wichtigste, was Sie wissen sollten:

- In Deutschland sind **rein KI-generierte Werke** aktuell **nicht urheberrechtlich geschützt** — es fehlt der „menschliche Schöpfer". Sie können sie aber trotzdem nutzen und verbreiten, solange das Trainingsmaterial rechtssauber war.
- **Adobe Firefly** ist aktuell der Anbieter mit den klarsten kommerziellen Garantien (weil die Trainingsdaten gemeinfrei oder aus Adobe Stock kommen).
- Bei anderen Anbietern (Midjourney, Flux, DALL·E, Nano Banana, Runway, Veo) ist die Trainingsdaten-Situation komplexer. Rechtsstreite mit Künstlerinnen, Fotografen und Medienhäusern laufen. Für interne Nutzung meist unproblematisch, für große kommerzielle Kampagnen sollten Sie mit einer Anwältin sprechen.
- **Prompts mit echten Personennamen** („Erstelle ein Bild im Stil von Banksy") sind heikel. Die meisten Anbieter blocken das inzwischen oder liefern bewusst unähnliche Ergebnisse. Bei lokalen Modellen liegt die Verantwortung bei Ihnen.

### Datenschutz

- **Cloud-basierte Modelle** verarbeiten Ihre Prompts (und bei Image-to-Image Ihre Input-Bilder) auf den Servern des Anbieters. Wenn Sie Fotos von echten Personen hochladen, ist das ein datenschutzrelevanter Vorgang.
- **Lokale Modelle** (Stable Diffusion, Flux Dev) sind aus Datenschutz-Sicht die sicherste Variante — nichts verlässt Ihren Rechner.

---

## Zusammenfassung in 60 Sekunden

Bei Bildmodellen 2026 gibt es vier Hauptspieler: **Midjourney** (Kunst), **Flux** (Präzision), **Nano Banana** (Preis-Leistung) und **Ideogram** (Text im Bild). Für Einsteiger ist Nano Banana (über Gemini) oder DALL·E (über ChatGPT) meist der bequemste Start. Wer ernsthaft damit arbeitet, landet oft bei Midjourney oder Flux. Bei Videomodellen führt **Google Veo 3** aktuell die Qualitäts-Rangliste an, **Runway** ist das Profi-Tool und **Luma** ist der günstige Einstieg. Für Adobe-Kunden und kommerzielle Rechtssicherheit ist **Firefly** eine eigene Liga. Wer experimentieren will, fängt mit den Free-Tiers von **Leonardo AI**, **Gemini** oder **Luma** an — dort kostet nichts, und Sie sehen schnell, was geht.

---

## Nächste Schritte

**Weiter mit:** [08 Entscheidungsbaum — Welches Tool wofür?](./08%20Entscheidungsbaum%20-%20Welches%20Tool%20wofuer.md)

Für tiefere Prompt-Arbeit bei Bildern und Videos lesen Sie bitte die bestehenden Kapitel:
- **Kapitel 04** — Prompt Engineering Bilder
- **Kapitel 05** — Prompt Engineering Videos
