# Reverse Engineering: Jedes Bild in einen perfekten Prompt verwandeln

## Wozu dient dieser Prompt?

Sie sehen ein beeindruckendes Foto — eine Werbekampagne, ein Produktfoto, ein Social-Media-Post — und fragen sich: *„Wie wurde dieses Bild gemacht? Welcher Stil, welches Licht, welche Komposition?"*

**Reverse Engineering** dreht den normalen Prozess um: Statt der KI zu sagen, was sie erstellen soll, geben Sie ihr ein **bestehendes Bild** und lassen es analysieren. Das Ergebnis: eine detaillierte Beschreibung, die Sie als Prompt verwenden können, um ähnliche Bilder zu generieren.

Kurz: **Bild → Prompt → beliebig viele ähnliche Bilder.**

## So verwenden Sie den Prompt

1. **Bild auswählen:** Welches Bild wollen Sie „entschlüsseln"? (Produktfoto, Kampagnenbild, Kunstwerk, Foto aus Social Media…)
2. **Prompt + Bild zusammen senden:** Kopieren Sie den Prompt in ChatGPT oder Claude, laden Sie das Bild in derselben Nachricht hoch.
3. **Analyse erhalten:** Die KI liefert eine strukturierte Analyse (Stil, Licht, Farben, Kamera, Komposition) + einen fertigen Prompt.
4. **Prompt verwenden:** Kopieren Sie den generierten Prompt in einen Bildgenerator (DALL-E, Midjourney, Stable Diffusion, Leonardo AI) → ähnliches Bild erstellen.

### 💡 Tipps

- **Hochauflösende Bilder liefern bessere Analysen** — die KI erkennt mehr Details in einem 2000px-Bild als in einem 200px-Thumbnail.
- **Vergleichs-Analyse:** Laden Sie 2–3 Bilder gleichzeitig hoch und fragen Sie: *„Was haben diese Bilder stilistisch gemeinsam?"* — perfekt um einen Brand-Stil zu extrahieren.
- **Master-Prompt für Ihr Branding:** Analysieren Sie Ihre besten eigenen Bilder, um einen „Master-Prompt" zu erstellen, der Ihren visuellen Stil definiert. Diesen nutzen Sie dann für alle zukünftigen Bilder.
- **Wettbewerber-Analyse:** Analysieren Sie die Bilder Ihrer Konkurrenz — nicht um zu kopieren, sondern um zu verstehen, was funktioniert und was Sie anders (besser) machen können.

### Anwendungsbeispiele

| Situation | Was Sie tun | Ergebnis |
|-----------|------------|---------|
| Wettbewerber-Produktfoto sieht besser aus | Bild analysieren lassen | Verstehen warum (Licht, Winkel, Styling) und eigene Version erstellen |
| Konsistenter Bildstil für Ihre Marke | Ihre 5 besten Bilder analysieren | Master-Prompt für einheitlichen Brand-Look |
| Inspiration von Social Media | Viral gegangenes Bild analysieren | Prompt extrahieren und für eigenes Thema adaptieren |
| Präsentations-Visuals | Überzeugenden Stil aus einem Bild extrahieren | Komplette Präsentation im gleichen Stil |
| Stockfoto-Alternative | Bezahltes Stockfoto analysieren | Ähnliches Bild mit KI generieren (ohne Lizenzkosten) |

> ⚠️ **Hinweis:** Reverse Engineering ist ein Analyse-Werkzeug. Erstellen Sie keine 1:1-Kopien urheberrechtlich geschützter Bilder. Nutzen Sie die Analyse, um den **Stil** zu verstehen und eigene Variationen zu erstellen.

---

## Der Prompt

```
<reverse_engineering>

<auftrag>
Analysiere das hochgeladene Bild im Detail und erstelle daraus
einen vollständigen, reproduzierbaren Prompt für einen
KI-Bildgenerator.
</auftrag>

<analyse_dimensionen>

<subject>
- Was ist das Hauptmotiv? (Person, Objekt, Szene, abstrakt)
- Position im Bild (zentriert, Drittelregel, asymmetrisch)
- Zustand und Aktion (statisch, in Bewegung, interagierend)
- Details: Kleidung, Materialien, Texturen, Alter, Ausdruck
</subject>

<environment>
- Wo spielt die Szene? (Studio, Natur, Urban, Innenraum, abstrakt)
- Tageszeit und Wetter (falls erkennbar)
- Hintergrund: scharf/unscharf, Elemente, Tiefe
- Atmosphäre: Stimmung, die der Ort transportiert
</environment>

<style>
- Übergeordneter Stil (Fotografie, Illustration, 3D-Render, Mixed Media)
- Spezifischer Substil (Editorial, Commercial, Fine Art, Documentary)
- Epoche/Referenz (modern, vintage, retro-futuristisch)
- Textur und Finish (glatt, körnig, Film Grain, HDR)
</style>

<composition>
- Bildausschnitt (Totale, Halbtotale, Nahaufnahme, Makro)
- Perspektive (Augenhöhe, Vogelperspektive, Frosch, Dutch Angle)
- Führungslinien und visuelle Hierarchie
- Symmetrie vs. Asymmetrie
- Negativraum (Weißraum)
</composition>

<lighting>
- Hauptlichtquelle (Richtung, Härte, Farbe)
- Fülllicht und Aufheller
- Rim Light / Kantenlicht
- Schatten (hart/weich, Richtung)
- Lichttemperatur (warm/kalt/neutral)
- Besondere Effekte (volumetrisch, Lens Flare, Bokeh)
</lighting>

<color>
- Dominante Farbpalette (3–5 Hauptfarben als Hex-Codes)
- Farbharmonie (komplementär, analog, monochromatisch, triadisch)
- Sättigung (lebendig, gedämpft, entsättigt)
- Color Grading / Postproduction-Look
- Kontrast (hoch/niedrig/mittel)
</color>

<technical>
- Geschätzte Brennweite (Weitwinkel, Normal, Tele, Makro)
- Geschätzte Blende (Schärfentiefe)
- Bildformat und Seitenverhältnis
- Auflösung und Detailgrad
- Postproduction-Hinweise (Retusche, Compositing, Filter)
</technical>

<mood>
- Emotionale Wirkung (was fühlt der Betrachter?)
- Narrative Elemente (erzählt das Bild eine Geschichte?)
- Zielgruppe (für wen wurde dieses Bild gemacht?)
- Marken-/Werbe-Wirkung (falls erkennbar)
</mood>

</analyse_dimensionen>

<output>
Liefere zwei Ergebnisse:

1. STRUKTURIERTE ANALYSE:
   Gehe jede Dimension systematisch durch.
   Sei präzise — keine vagen Beschreibungen.
   Nenne konkrete Werte (Hex-Farben, geschätzte mm, Lichtstärke).

2. REPRODUKTIONS-PROMPT:
   Erstelle einen einzigen, zusammenhängenden Prompt
   (im Code-Block), der alle analysierten Elemente enthält
   und in einem KI-Bildgenerator (Midjourney, DALL-E,
   Stable Diffusion) ein visuell ähnliches Bild erzeugen würde.
   Der Prompt muss eigenständig funktionieren —
   ohne das Originalbild gesehen zu haben.
</output>

</reverse_engineering>

[BILD HIER HOCHLADEN]
```

---

## Was Sie zurückbekommen — Beispiel

Wenn Sie z.B. ein professionelles Produktfoto hochladen, liefert die KI:

**1. Strukturierte Analyse (Auszug):**
- **Style:** Cinematic product photography, dramatic lighting, high-contrast
- **Composition:** Low-angle shot, rule of thirds
- **Lighting:** Key light from the side, subtle blue rim light, creating sharp reflections on metal surfaces
- **Mood:** High-tech, powerful, precise, innovative
- **Colors:** #1A1A2E (Dunkelblau-Schwarz), #00B4D8 (Cyan-Akzent), #E0E0E0 (Silber)

**2. Reproduktions-Prompt:**
> *„Cinematic product photography of a futuristic device, low-angle shot, placed according to the rule of thirds. Dramatic lighting with a strong key light from the side and a subtle blue rim light, creating sharp reflections on the brushed metal texture. Dark background with subtle gradient. High contrast, professional commercial look. 8K detail."*

→ Diesen Prompt kopieren Sie in DALL-E oder Midjourney und erhalten ein Bild im selben Stil — aber mit Ihrem eigenen Produkt.

---

## Erweiterte Nutzung

### Brand-Stil extrahieren (mehrere Bilder)

```
<auftrag>
Ich lade 3–5 Bilder hoch, die unseren gewünschten Markenstil
repräsentieren.

Analysiere alle Bilder und identifiziere:
1. Was haben sie stilistisch GEMEINSAM?
   (Farben, Licht, Komposition, Mood)
2. Was sind die UNTERSCHIEDE?
3. Erstelle einen MASTER-PROMPT, der den gemeinsamen Stil
   einfängt und für beliebige neue Motive anwendbar ist.

Der Master-Prompt soll so formuliert sein, dass ich nur noch
das Motiv austauschen muss — der Stil bleibt konstant.
</auftrag>

[BILDER HIER HOCHLADEN]
```

### Stil-Transfer: Analyse auf neues Thema anwenden

Nachdem Sie eine Analyse erhalten haben:

```
Nutze den Reproduktions-Prompt von eben, aber ersetze das Motiv:
Statt [ORIGINAL-MOTIV] zeige [NEUES MOTIV].
Behalte exakt den gleichen Stil, die gleiche Farbpalette,
das gleiche Licht und die gleiche Komposition bei.
```

---

