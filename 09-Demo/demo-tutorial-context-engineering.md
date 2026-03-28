# Context Engineering — Wie Du KI wirklich zum Arbeiten bringst

> Vom einfachen Chat-Prompt zum strukturierten Kontext, der Ergebnisse liefert, die Du sofort nutzen kannst.

---

## Warum dieses Tutorial?

Die meisten Menschen tippen einen Satz in ChatGPT oder Claude und hoffen auf ein gutes Ergebnis. Manchmal klappt das — oft nicht. Der Unterschied zwischen "geht so" und "genau das, was ich brauche" liegt nicht in der KI, sondern im **Kontext**, den Du ihr gibst.

Context Engineering ist die Kunst, der KI **alles mitzugeben**, was sie braucht, um Deine Aufgabe wirklich zu verstehen. Nicht mehr, nicht weniger.

Dieses Tutorial zeigt Dir die 5 Ebenen des Context Engineering und wie Du sie in der Praxis einsetzt — mit Beispielen aus dem HR- und Marketing-Alltag der Agrarbank.

---

## Die 5 Ebenen auf einen Blick

![Die 5 Ebenen des Context Engineering](./images/demo-01-context-engineering-5-ebenen.png)

Das Diagramm zeigt die fünf Ebenen, die zusammen einen vollständigen Kontext ergeben. Jede Ebene beantwortet eine andere Frage — und je mehr Ebenen Du ausfüllst, desto besser wird das Ergebnis.

---

## Die Agrarbank-Analogie

Stell Dir vor, Du bist neu in der Agrarbank und bekommst am ersten Tag den Auftrag: *"Schreib mal was für unsere Azubi-Kampagne."*

Ohne weiteren Kontext würdest Du fragen:

- **Wer bin ich in dieser Aufgabe?** → Rolle (Ebene 1)
- **Was genau soll ich schreiben?** → Aufgabe (Ebene 2)
- **Was weiß ich über die Agrarbank und ihre Azubis?** → Wissen (Ebene 3)
- **Wie soll das Ergebnis aussehen?** → Format (Ebene 4)
- **Für wen ist das? Warum jetzt?** → Situation (Ebene 5)

Genau diese Fragen braucht auch die KI. Der Unterschied: Ein Mensch fragt nach — die KI arbeitet mit dem, was sie bekommt. Deshalb musst **Du** den Kontext liefern.

---

## Schritt 1 — System-Kontext (Die Rolle)

Wer soll die KI sein? Eine Rolle gibt der KI einen Rahmen für Tonalität, Fachwissen und Perspektive.

**Schwacher Prompt:**
```
Schreib eine Stellenanzeige für Azubis.
```

**Mit Rolle:**
```
Du bist ein erfahrener Employer-Branding-Experte, der sich auf die
Ansprache der Generation Z spezialisiert hat. Du kennst die Agrarbank
als regionalen Arbeitgeber im ländlichen Raum und weißt, was junge
Menschen an einer Bankausbildung begeistert.
```

> 💡 **Tipp:** Die Rolle muss nicht "echt" sein — sie muss relevant sein. "Erfahrener Employer-Branding-Experte" aktiviert anderes Wissen als "HR-Sachbearbeiter".

---

## Schritt 2 — Aufgaben-Kontext (Das Ziel)

Was genau soll die KI tun? Je präziser die Aufgabe, desto weniger muss die KI raten.

**Schwach:**
```
Schreib eine Stellenanzeige.
```

**Präzise:**
```
Erstelle eine Stellenanzeige für den Ausbildungsberuf
Bankkaufmann/-frau bei der Agrarbank. Die Anzeige soll:
- Maximal 300 Wörter lang sein
- Einen aufmerksamkeitsstarken Einstieg haben (kein "Wir suchen...")
- Benefits aus Azubi-Perspektive betonen
- Mit einem klaren Call-to-Action enden
```

---

## Schritt 3 — Wissens-Kontext (Die Daten)

Welche Informationen braucht die KI, die sie nicht aus ihrem Training kennt?

```
Über die Agrarbank:
- Genossenschaftsbank mit Fokus auf Landwirtschaft und ländlichen Raum
- 12 Filialen, 280 Mitarbeitende
- Ausbildungsstart: 1. August 2027
- Benefits: Übernahmegarantie, Tablet für alle Azubis,
  Weiterbildungsbudget 2.000€/Jahr, flexible Arbeitszeiten,
  30 Tage Urlaub, Azubi-Projekte mit echten Kunden
```

> 💡 **Tipp:** Du kannst in Claude Projects oder ChatGPT-GPTs ganze Dokumente als Wissens-Kontext hochladen — z.B. die Azubi-Broschüre, den Ausbildungsrahmenplan oder die Karriereseite.

---

## Schritt 4 — Interaktions-Kontext (Das Format)

Wie soll das Ergebnis aussehen? Format, Stil, Struktur.

```
Format und Stil:
- Sprache: Du-Ansprache, locker aber professionell
- Kein Bankerdeutsch, keine Floskeln wie "dynamisches Team"
- Aufbau: Headline → Einstieg → Was Dich erwartet →
  Was Du mitbringst → Warum Agrarbank → Call-to-Action
- Emojis sparsam einsetzen (maximal 3)
```

---

## Schritt 5 — Situations-Kontext (Das Warum)

Wer liest das? In welcher Situation? Warum jetzt?

```
Kontext der Veröffentlichung:
- Zielgruppe: 16-20-Jährige in der Region, die gerade ihren
  Schulabschluss machen oder planen
- Kanal: Instagram-Post + Story + Karriereseite
- Timing: Veröffentlichung im April 2027, wenn Bewerbungsphase
  für August-Start beginnt
- Problem: Bisherige Anzeigen klingen zu formal und erreichen
  die Zielgruppe nicht
```

---

## Vom Einzelprompt zum vollständigen Kontext

![Vom schwachen Prompt zum vollständigen Kontext](./images/demo-02-prompt-vergleich-vorher-nachher.png)

Das Diagramm oben zeigt den Unterschied: Links ein typischer Einzeiler-Prompt, rechts derselbe Auftrag mit allen 5 Kontext-Ebenen. Der Aufwand für den vollständigen Prompt beträgt vielleicht 3 Minuten mehr — aber das Ergebnis spart Dir 30 Minuten Nachbearbeitung.

---

## Das Wichtigste auf einen Blick

| Ebene | Frage | Beispiel Agrarbank |
|---|---|---|
| 1. System-Kontext | Wer bist Du? | Employer-Branding-Experte für GenZ |
| 2. Aufgaben-Kontext | Was genau? | Stellenanzeige, 300 Wörter, mit CTA |
| 3. Wissens-Kontext | Was weißt Du? | Benefits, Fakten, Ausbildungsdetails |
| 4. Interaktions-Kontext | Wie soll's aussehen? | Du-Ansprache, locker, mit Struktur |
| 5. Situations-Kontext | Für wen, warum, wann? | GenZ, Instagram, April 2027 |

---

## Glossar

| Begriff | Erklärung |
|---|---|
| **Context Engineering** | Die systematische Gestaltung aller Informationen, die einer KI für eine Aufgabe übergeben werden — über den reinen Prompt hinaus. |
| **System-Prompt** | Der erste Instruktionsblock, der die Rolle und Grundregeln der KI festlegt. In ChatGPT-GPTs und Claude Projects ist das der "Instructions"-Bereich. |
| **Few-Shot** | Eine Technik, bei der Du der KI 2-3 Beispiele für das gewünschte Ergebnis mitgibst, damit sie das Muster erkennt. |
| **Token** | Die kleinste Einheit, in der KI Text verarbeitet. Ein deutsches Wort besteht aus ca. 1,5-2 Tokens. Mehr Kontext = mehr Tokens = präzisere Ergebnisse (bis zum Kontextlimit). |
| **Kontextfenster** | Die maximale Menge an Text, die eine KI gleichzeitig "sehen" kann. GPT-4o: 128.000 Tokens. Claude Opus: 200.000 Tokens. |

---

> 📎 **Nächstes Tutorial:** Strukturierte Prompts mit Markdown und XML — wie Du den Kontext so formatierst, dass die KI ihn optimal verarbeitet.
