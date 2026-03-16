# KI-Videos szenenweise produzieren: Konsistente Clips mit Veo 3

## Wozu dient dieser Prompt?

KI-Videogeneratoren wie Google Veo 3 erzeugen beeindruckende Clips — aber nur maximal **8 Sekunden pro Clip**. Für ein längeres Video brauchen Sie mehrere Clips, die Sie zusammenschneiden. Das Problem: Jeder Clip wird **isoliert generiert**. Veo 3 weiß nicht, wie der vorherige Clip aussah — Charaktere ändern plötzlich ihr Aussehen, die Umgebung wechselt, die Stimmung bricht.

Dieser Meta-Prompt löst das: Sie geben Ihre Szenenliste ein, und die KI schreibt für jede Szene einen **eigenständigen, lückenlosen Prompt** — mit identischer Beschreibung von Charakteren, Kleidung, Umgebung und Stil. So bleibt die Konsistenz über alle Clips erhalten.

## So verwenden Sie den Prompt

1. **Szenenliste schreiben:** Notieren Sie Ihre Szenen in 1–2 Sätzen pro Szene (z.B. „Szene 1: Frau betritt ein Büro. Szene 2: Frau setzt sich an den Schreibtisch. Szene 3: Nahaufnahme ihrer Hände auf der Tastatur.")
2. **Prompt einfügen:** Kopieren Sie den Meta-Prompt in ChatGPT oder Claude. Ersetzen Sie den Platzhalter durch Ihre Szenenliste.
3. **Prompts erhalten:** Die KI denkt detailliert nach (`<thinking>`) und liefert dann nummerierte, Copy-Paste-fertige Prompts für Veo 3.
4. **Prompts in Veo 3 einfügen:** Jeden Prompt einzeln in Veo 3 eingeben → 8-Sekunden-Clip generieren.
5. **Zusammenschneiden:** Alle Clips in einem Videoeditor (CapCut, DaVinci Resolve, Premiere) zusammensetzen.

### 💡 Tipps

- **Englisch prompten:** Veo 3 liefert auf Englisch deutlich bessere Ergebnisse als auf Deutsch.
- **Kosten beachten:** KI-Videos sind nicht günstig — ca. 5 € pro 8-Sekunden-Clip (Stand 2025). Ein 2-Minuten-Video mit 15 Clips kostet ca. 75 €. Planen Sie vorher, welche Szenen Sie wirklich brauchen.
- **Konsistenz ist alles:** Der Schlüssel zu einem guten Ergebnis ist, dass Charakter-Beschreibungen, Kleidung, Licht und Stil in **jedem Prompt identisch** wiederholt werden.
- **Seed-ID nutzen (Fortgeschritten):** Bei Plattformen wie Replicate können Sie die Seed-ID eines generierten Videos weiterverwenden — das erhöht die visuelle Konsistenz zwischen Clips.
- **Weniger Szenen, mehr Qualität:** Lieber 8 perfekte Clips als 20 inkonsistente. Jeder Szenenwechsel ist eine Chance für Brüche.

> ⚠️ **Wichtig:** Veo 3 generiert auch Audio (Sprache, Soundeffekte). Wenn Sie den Ton selbst hinzufügen wollen, schreiben Sie in jeden Prompt: *„No dialogue, no sound effects, ambient silence only."*

---

## Der Meta-Prompt

```
<szenen_liste>
{Hier Ihre Szenenliste einfügen — eine Szene pro Zeile, z.B.:
Szene 1: Frau betritt ein modernes Büro
Szene 2: Frau setzt sich an den Schreibtisch
Szene 3: Nahaufnahme ihrer Hände auf der Tastatur
Szene 4: Bildschirm zeigt ein Dashboard mit steigenden Zahlen
Szene 5: Frau lehnt sich zurück und lächelt zufrieden}
</szenen_liste>

<auftrag>
Oben siehst du die Liste der Szenen für mein KI-generiertes Video.
Wir nutzen dafür Google Veo 3, das Video und Audio generiert.

Einschränkungen von Veo 3:
- Jedes Video maximal 8 Sekunden lang
- Jede Szene wird isoliert generiert — Veo 3 kennt die vorherige
  Szene NICHT (kein Gedächtnis zwischen Clips)

Deshalb musst du in JEDEM Prompt ALLE Details wiederholen:
- Aussehen der Charaktere (Gesicht, Haare, Alter, Körperbau)
- Kleidung (Farbe, Stil, Accessoires)
- Umgebung (Raum, Beleuchtung, Tageszeit, Wetter)
- Stimmung und Farbpalette
- Kamerawinkel und -bewegung
- Stil (z.B. cinematic, documentary, commercial)

Deine Aufgabe: Schreibe eine Serie von Prompts für Veo 3,
einen pro Szene, jeweils für einen 8-Sekunden-Clip.
Ich schneide die Clips später zusammen.
</auftrag>

<regeln>
- Alle Prompts auf Englisch
- Keine Mehrdeutigkeit — jedes Detail explizit beschreiben
- Keine offenen Interpretationen — nichts dem Zufall überlassen
- Jeder Prompt muss komplett eigenständig funktionieren
  (als wäre es der einzige Prompt, den Veo 3 je gesehen hat)
- Charakter-Beschreibungen WÖRTLICH wiederholen in jedem Prompt
- Einheitlicher visueller Stil über alle Prompts
</regeln>

<vorgehen>
Zuerst denkst du ausführlich (mindestens 25 Absätze) im Tag
<thinking> über die Umsetzung nach:
- Wie sehen die Charaktere genau aus?
- Welcher visuelle Stil passt zum Gesamtvideo?
- Welche Kamerawinkel erzählen die Geschichte am besten?
- Wo sind die kritischen Übergänge zwischen Szenen?
- Welche Details müssen konstant bleiben?

Dann gibst du die fertigen Prompts nummeriert im Tag <prompts> aus.
</vorgehen>
```

---

## Referenz: Nützliche Begriffe für Video-Prompts

| Kategorie | Begriffe (Englisch) |
|-----------|-------------------|
| **Bildkomposition** | close-up, medium shot, wide shot, two-shot, over-the-shoulder, establishing shot |
| **Objektiv & Fokus** | macro lens, shallow depth of field, wide-angle lens, 85mm portrait lens |
| **Kamerabewegung** | zoom in/out, dolly shot, tracking shot, pan left/right, tilt up/down, static shot |
| **Licht** | natural daylight, golden hour, rim light, soft diffuse light, dramatic shadows |
| **Stil** | cinematic, documentary, commercial, film noir, sci-fi, romantic comedy |
| **Atmosphäre** | moody, warm, cold, tense, peaceful, energetic, nostalgic |

---

## Beispiel: 3 Szenen, fertige Prompts

**Szenenliste:**
1. Beraterin betritt Konferenzraum
2. Beraterin präsentiert am Whiteboard
3. Team applaudiert

**So könnten die fertigen Prompts aussehen:**

**Szene 1:**
> *Cinematic 8-second clip. A confident woman in her early 40s with shoulder-length dark brown hair, wearing a tailored navy blue blazer over a white silk blouse, enters a modern glass-walled conference room. She carries a black leather portfolio. The room has a long oak table with 6 grey mesh chairs, a large wall-mounted display showing a blue gradient screensaver, and floor-to-ceiling windows with soft natural daylight streaming in. Warm color palette, slight golden tint. Camera: tracking shot from left, following her as she walks in. Shallow depth of field. No dialogue.*

**Szene 2:**
> *Cinematic 8-second clip. The same confident woman in her early 40s with shoulder-length dark brown hair, wearing a tailored navy blue blazer over a white silk blouse, stands at a whiteboard in the same modern glass-walled conference room. She draws a diagram with a blue marker. The whiteboard shows hand-drawn boxes connected by arrows. Behind her: the long oak table, 6 grey mesh chairs, floor-to-ceiling windows with soft natural daylight. Warm color palette, slight golden tint. Camera: medium shot, static, slight low angle to convey authority. No dialogue.*

**Szene 3:**
> *Cinematic 8-second clip. Same modern glass-walled conference room. Five professionals (3 men, 2 women, diverse, ages 30-50, business casual) sit at the long oak table and applaud with genuine smiles. At the front of the room, the same confident woman in her early 40s with shoulder-length dark brown hair, wearing a tailored navy blue blazer over a white silk blouse, smiles back warmly. Floor-to-ceiling windows with soft natural daylight. Warm color palette, slight golden tint. Camera: wide shot from the back of the room, capturing both the audience and the presenter. No dialogue.*

**Beachten Sie:** Die Charakterbeschreibung (*early 40s, shoulder-length dark brown hair, navy blue blazer, white silk blouse*) und die Raumbeschreibung (*glass-walled conference room, oak table, 6 grey mesh chairs, floor-to-ceiling windows*) sind in **jedem Prompt wörtlich identisch**.

---

## 5 Video-Prompt-Beispiele zum Ausprobieren

### 1. Produktvideo: Kaffeetasse in Szene setzen

```
Cinematic 8-second clip. A handcrafted ceramic coffee mug in matte
black with a thin gold rim sits on a rustic oak table. Steam rises
gently from the dark espresso inside. Morning sunlight streams through
a large window on the left, casting warm golden light and soft shadows
across the table. Background: a blurred minimalist kitchen with white
walls and green plants. Camera: slow dolly-in from medium shot to
close-up, focusing on the steam and the gold rim detail. Shallow depth
of field. Warm color palette. No dialogue, ambient silence with soft
natural room tone.
```

### 2. Recruiting-Video: Teamwork im Büro

```
Cinematic 8-second clip. A diverse team of four professionals
(two women, two men, ages 25-45, business casual attire) collaborates
around a standing desk with dual monitors showing colorful data
dashboards. One woman with curly red hair in a green cardigan points
at the screen while explaining something with an enthusiastic expression.
The others nod and smile. Modern open-plan office with exposed brick
walls, industrial pendant lights, and large windows with diffuse
afternoon daylight. Warm, inviting color palette with slight orange tint.
Camera: medium shot, slow arc movement from left to right. Shallow depth
of field on the group, background softly blurred. Natural office ambient
sound, no dialogue.
```

### 3. Immobilien-Video: Luxuswohnung präsentieren

```
Cinematic 8-second clip. Camera glides through the open front door
into a spacious modern apartment living room. Floor-to-ceiling windows
reveal a panoramic city skyline at golden hour. The room features
polished concrete floors, a large L-shaped charcoal grey sofa, a round
marble coffee table with a single orchid, and a minimalist fireplace
with a low flame. Walls are warm white with one accent wall in deep
forest green. Soft golden sunlight fills the space. Camera: smooth
steadicam tracking shot moving forward through the doorway into the room,
eye level, slow and elegant. Warm cinematic color grade. No people.
Ambient silence with very subtle city hum in the distance.
```

### 4. Food-Content: Pasta-Gericht anrichten

```
Cinematic 8-second clip. Top-down bird's eye view of two hands
plating fresh pasta on a white ceramic plate. The hands belong to a
chef wearing a crisp white chef's jacket with rolled-up sleeves,
visible forearm tattoo of a small olive branch. The pasta is tagliatelle
with a rich red tomato-basil sauce, topped with fresh basil leaves and
shaved parmesan. The wooden kitchen counter is dark walnut, surrounded
by ingredients: a bottle of olive oil, cherry tomatoes on a vine, a
block of parmesan, a mortar with crushed pepper. Warm overhead studio
lighting, slight steam rising from the pasta. Camera: static top-down,
then very slow zoom-in toward the plate. Warm, rich color palette.
Sound of gentle sizzling in background, no dialogue.
```

### 5. Storytelling: Einsamer Wanderer in den Bergen

```
Cinematic 8-second clip. A lone hiker, male, early 30s, athletic build,
wearing a dark green waterproof jacket, grey hiking pants, and a brown
leather backpack, stands on a rocky mountain ridge. He faces away from
the camera, looking out over a vast valley filled with morning fog.
Sharp mountain peaks frame the background under a dramatic sky with
broken clouds and rays of sunlight breaking through. The wind gently
moves his jacket and hair. Color palette: cool blues and greens with
warm golden accents from the sunlight. Camera: wide establishing shot,
static for 3 seconds, then very slow push-in toward the hiker.
Volumetric lighting through the clouds. Sound of mountain wind,
no dialogue, no music.
```

---

