# KI-Icon-Erstellung: Professionelle Icons und Symbole mit KI generieren

## Wozu dient dieser Prompt?

Icons und Symbole braucht man ständig — für Websites, Präsentationen, Apps, Infografiken, Schulungsunterlagen. Ein Icon-Set vom Designer kostet schnell 200–500 €. Mit diesem Prompt generieren Sie professionelle Icons in Ihren **Markenfarben** und einem **einheitlichen Stil** — direkt in ChatGPT (DALL-E), Midjourney, Adobe Firefly oder Leonardo AI.

Das Besondere: Der Prompt ist so strukturiert, dass alle Icons **konsistent** aussehen — gleicher Stil, gleiche Linienbreite, gleiche Farbpalette. Perfekt für ein ganzes Icon-Set.

## So verwenden Sie den Prompt

1. **Markenfarben bereithalten:** Ihre Primärfarbe, Sekundärfarbe und Linienfarbe als Hex-Codes (z.B. #007AB8). Fragen Sie Ihre Marketing-Abteilung oder schauen Sie in Ihren Brand Guidelines nach.
2. **Icon-Bedarf definieren:** Was soll dargestellt werden? Wo wird es eingesetzt?
3. **Prompt ausfüllen:** Ersetzen Sie die Platzhalter im Prompt mit Ihren Angaben.
4. **An KI übergeben:** Prompt kopieren und in den Bildgenerator einfügen.
5. **Iterieren:** Wenn der Stil stimmt aber Details nicht passen → gezielt nachprompten.

### 💡 Tipps

- **Ein Stil für alle:** Generieren Sie das erste Icon, und beschreiben Sie danach bei allen weiteren: *„Im exakt gleichen Stil wie das vorherige Icon."*
- **Transparenter Hintergrund:** Nicht alle KI-Tools unterstützen echte Transparenz. DALL-E und Leonardo AI können es, Midjourney nicht nativ. Bei Bedarf: Hintergrund nachträglich entfernen (z.B. mit remove.bg).
- **Quadratisch arbeiten:** Icons immer im Format 1:1 generieren — skalieren geht immer, Zuschneiden ist Qualitätsverlust.
- **Batch-Erstellung:** Definieren Sie einmal Stil und Farben, dann listen Sie 5–10 Icon-Themen auf einmal auf (→ Batch Processing, Tutorial 08-18).
- **SVG statt PNG:** Wenn Sie Vektor-Icons brauchen, bitten Sie ChatGPT, den Icon als SVG-Code zu generieren statt als Bild — der lässt sich verlustfrei skalieren.

### Auflösung wählen

| Einsatzbereich | Empfohlene Auflösung |
|---------------|---------------------|
| Website / Digital | 512×512 px |
| Präsentationen / Print | 1024×1024 px (empfohlen) |
| Großformate / Banner | 2048×2048 px |

### Barrierefreiheit beachten
- **Kontrast:** Mindestens 4.5:1 (Farbe zu Hintergrund)
- **Graustufen-Test:** Icons sollten auch ohne Farbe erkennbar sein
- **Linienbreite:** Mindestens 2px für Lesbarkeit
- **Kleinstgröße:** Icons müssen auch bei 32×32px noch erkennbar sein

### Rechtliches
- Prüfen Sie die **Lizenzrechte** Ihres KI-Tools für kommerzielle Nutzung
- Keine geschützten Symbole verwenden (z.B. bestimmte medizinische Zeichen)
- Bei kommerzieller Nutzung: Business-Lizenz des Tools erforderlich

---

## Der Prompt

```
<icon_erstellung>

<thema>
[WAS SOLL DARGESTELLT WERDEN — z.B. "Laptop mit Videoanruf-Symbol
und Arzt" / "Stilisierte Familie unter Schutzdach" / "Zahnrad mit
Glühbirne für Innovation"]
</thema>

<stil>
Stiltyp: [flach / minimalistisch / isometrisch / Outline / 3D]
Detailgrad: [niedrig / mittel / hoch]
Gesamtästhetik: [modern, klar, freundlich / technisch, präzise /
warm, einladend]
</stil>

<farben>
Primärfarbe (Füllung): [HEX-CODE — z.B. #007AB8]
Sekundärfarbe (Akzent): [HEX-CODE — z.B. #00A3E0]
Linienfarbe (Umriss): [HEX-CODE — z.B. #003D5C]
Linienbreite: 2px
Linienverbindung: rund
Füllstil: einfarbig
</farben>

<layout>
Seitenverhältnis: 1:1 (quadratisch)
Eckenradius: 4px
Hintergrund: transparent
Rand/Padding: gleichmäßig, Icon zentriert mit etwas Luft
</layout>

<technisch>
Ausgabeformat: PNG mit transparentem Hintergrund
Auflösung: 1024×1024px
Kein Text im Icon
Keine Schatten, kein Gradient (außer explizit gewünscht)
</technisch>

</icon_erstellung>
```

---

## 5 fertige Beispiel-Prompts

### 1. Online-Beratung / Videosprechstunde

```
<icon_erstellung>
<thema>Laptop mit Videoanruf-Symbol und Person</thema>
<stil>Stiltyp: flach. Detailgrad: mittel.
Gesamtästhetik: modern, vertrauensvoll, klar.</stil>
<farben>Primärfarbe: #007AB8. Sekundärfarbe: #00A3E0.
Linienfarbe: #003D5C. Linienbreite: 2px. Füllstil: einfarbig.</farben>
<layout>1:1, transparent, zentriert.</layout>
<technisch>PNG, 1024×1024px, kein Text, keine Schatten.</technisch>
</icon_erstellung>
```

### 2. Familie & Schutz

```
<icon_erstellung>
<thema>Stilisierte Familie (2 Erwachsene, 1 Kind) unter einem
schützenden Dach</thema>
<stil>Stiltyp: minimalistisch. Detailgrad: niedrig.
Gesamtästhetik: warm, einladend.</stil>
<farben>Primärfarbe: #00A3E0. Sekundärfarbe: #007AB8.
Linienfarbe: #003D5C. Linienbreite: 2px. Füllstil: einfarbig.</farben>
<layout>1:1, transparent, zentriert.</layout>
<technisch>PNG, 1024×1024px, kein Text, keine Schatten.</technisch>
</icon_erstellung>
```

### 3. Digitale Services / App

```
<icon_erstellung>
<thema>Smartphone mit App-Interface und Checkmark</thema>
<stil>Stiltyp: flach. Detailgrad: mittel.
Gesamtästhetik: modern, technisch, klar.</stil>
<farben>Primärfarbe: #007AB8. Sekundärfarbe: #FFFFFF.
Linienfarbe: #003D5C. Linienbreite: 2px. Füllstil: einfarbig.</farben>
<layout>1:1, transparent, zentriert.</layout>
<technisch>PNG, 1024×1024px, kein Text, keine Schatten.</technisch>
</icon_erstellung>
```

### 4. Fitness & Prävention

```
<icon_erstellung>
<thema>Person beim Joggen mit Herzsymbol</thema>
<stil>Stiltyp: minimalistisch. Detailgrad: niedrig.
Gesamtästhetik: energisch, gesund, positiv.</stil>
<farben>Primärfarbe: #00A3E0. Sekundärfarbe: #007AB8.
Linienfarbe: #003D5C. Linienbreite: 2px. Füllstil: einfarbig.</farben>
<layout>1:1, transparent, zentriert.</layout>
<technisch>PNG, 1024×1024px, kein Text, keine Schatten.</technisch>
</icon_erstellung>
```

### 5. Zahnrad — Outline-Stil

```
<icon_erstellung>
<thema>Zahnrad — Symbol für Einstellungen und Prozesse</thema>
<stil>Stiltyp: Outline. Detailgrad: einfach.
Gesamtästhetik: clean, technisch.</stil>
<farben>Primärfarbe: keine Füllung. Sekundärfarbe: keine.
Linienfarbe: #000000. Linienbreite: 2px. Füllstil: keine Füllung.</farben>
<layout>1:1, transparent, zentriert.</layout>
<technisch>PNG, 1024×1024px, kein Text, keine Schatten.</technisch>
</icon_erstellung>
```

### 6. Rakete — Futuristischer Stil

```
<icon_erstellung>
<thema>Rakete beim Start — Symbol für Launch und Wachstum</thema>
<stil>Stiltyp: futuristisch. Detailgrad: mittel.
Gesamtästhetik: energisch, modern, mutig.</stil>
<farben>Primärfarbe: #FF4500. Sekundärfarbe: #00FFFF.
Linienfarbe: #222222. Linienbreite: 3px. Füllstil: Farbverlauf.</farben>
<layout>1:1, transparent, zentriert.</layout>
<technisch>PNG, 1024×1024px, kein Text.</technisch>
</icon_erstellung>
```

### 7. Offenes Buch — Handgezeichneter Stil

```
<icon_erstellung>
<thema>Offenes Buch — Symbol für Wissen und Lernen</thema>
<stil>Stiltyp: handgezeichnet. Detailgrad: hoch.
Gesamtästhetik: warm, organisch, persönlich.</stil>
<farben>Primärfarbe: #F5F5DC. Sekundärfarbe: #8B4513.
Linienfarbe: #000000. Linienbreite: 1px. Füllstil: einfarbig.</farben>
<layout>1:1, transparent, zentriert.</layout>
<technisch>PNG, 1024×1024px, kein Text, keine Schatten.</technisch>
</icon_erstellung>
```

### 8. Innovation / Weiterbildung

```
<icon_erstellung>
<thema>Glühbirne mit Zahnrad — Symbol für innovative Ideen
und systematisches Lernen</thema>
<stil>Stiltyp: Outline. Detailgrad: mittel.
Gesamtästhetik: modern, intellektuell, klar.</stil>
<farben>Primärfarbe: #FF8C00. Sekundärfarbe: #FFB347.
Linienfarbe: #333333. Linienbreite: 2px. Füllstil: einfarbig.</farben>
<layout>1:1, transparent, zentriert.</layout>
<technisch>PNG, 1024×1024px, kein Text, keine Schatten.</technisch>
</icon_erstellung>
```

---

## Batch-Erstellung: 10 Icons auf einmal

Wenn Sie ein ganzes Icon-Set brauchen, definieren Sie Stil und Farben einmal und listen dann alle Themen auf:

```
Erstelle 10 Icons im exakt gleichen Stil.

<stil_fuer_alle>
Stiltyp: flach, minimalistisch
Primärfarbe: [IHR HEX-CODE]
Sekundärfarbe: [IHR HEX-CODE]
Linienfarbe: [IHR HEX-CODE]
Linienbreite: 2px
Hintergrund: transparent, 1024×1024px, kein Text
</stil_fuer_alle>

<icon_liste>
1. Telefon-Hotline
2. E-Mail / Briefumschlag
3. Chat-Blase mit Punkten
4. Kalender mit Checkmark
5. Dokument mit Stift
6. Schild mit Checkmark (Sicherheit)
7. Zahnrad (Einstellungen)
8. Lupe (Suche)
9. Person mit Plus-Zeichen (Neuer Kontakt)
10. Herz mit Puls-Linie (Gesundheit)
</icon_liste>

Generiere jedes Icon einzeln, aber im identischen Stil.
Bitte nur das PNG-Bild ausgeben — keine zusätzliche Beschreibung.
```

---

## Checkliste vor der Icon-Erstellung

- [ ] Icon-Zweck definiert (was soll dargestellt werden?)
- [ ] Einsatzort klar (Website, App, Print, Präsentation)
- [ ] Markenfarben als Hex-Codes bereit
- [ ] Stil gewählt (flach, Outline, minimalistisch, 3D, handgezeichnet, futuristisch, pixelig)
- [ ] Auflösung für Verwendungszweck gewählt
- [ ] Transparenter Hintergrund gewünscht? (Tool-Kompatibilität prüfen)
- [ ] Barrierefreiheit beachtet (Kontrast, Graustufen, Mindestgröße)
- [ ] Lizenzrechte des KI-Tools geprüft

---


