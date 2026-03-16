# Wissen extrahieren: Podcasts, Bücher und Artikel in Minuten destillieren

## Wozu dient diese Technik?

Sie hören einen 2-Stunden-Podcast, lesen einen langen Artikel oder arbeiten ein Buch durch. Es ist gut, es ist interessant — aber in einer Woche haben Sie 90% vergessen. Das ist passive Konsumption: Informationen fließen rein und wieder raus.

Diese Technik verwandelt **passive Konsumption in aktives Lernen**. Sie lassen die KI das Gehörte/Gelesene destillieren, in actionable Schritte übersetzen und auf Ihre Situation anwenden. Das Ergebnis: ein kompaktes Dokument, das Sie tatsächlich nutzen — statt vager Erinnerungen an „irgendwas Interessantes".

## So verwenden Sie die Technik

1. **Quelle bereitstellen:** Transkript hochladen, URL einfügen, oder Text kopieren.
2. **Destillations-Prompt nutzen:** Je nach Ziel (Zusammenfassung, Action Items, Lehrmaterial).
3. **Ergebnis speichern:** In einem Projekt, einer Notiz-App, oder als PDF exportieren.

### Was können Sie destillieren?

| Quelle | Wie bereitstellen |
|--------|-------------------|
| Podcast | Transkript hochladen (viele Podcast-Apps bieten das an) oder YouTube-URL |
| YouTube-Video | URL einfügen (ChatGPT kann viele Videos direkt lesen) |
| Buch | Kapitel fotografieren und als Bilder hochladen, oder E-Book-Auszüge kopieren |
| Artikel | URL einfügen oder Text kopieren |
| Kurs / Weiterbildung | Notizen oder Folien hochladen |

### 💡 Tipps

- **Sofort destillieren:** Je schneller Sie nach dem Konsum destillieren, desto besser. Nicht warten — „Ich mach das später" heißt meistens „Nie".
- **Transkript finden:** Viele Podcast-Apps zeigen Transkripte an (Apple Podcasts, Spotify). YouTube-Videos haben automatische Untertitel, die Sie als Text kopieren können. Alternativ: URL in ChatGPT einfügen — bei vielen Quellen kann die KI den Inhalt direkt lesen.
- **Auf sich selbst beziehen:** Die wichtigste Frage ist nicht „Was wurde gesagt?" sondern „Was bedeutet das für mich?"
- **Sammlung aufbauen:** Speichern Sie alle Destillate in einem ChatGPT-Projekt „Wissensbibliothek". Über die Zeit entsteht eine persönliche Knowledge Base.
- **Weiterverarbeiten:** Aus einem Podcast-Destillat können Sie einen LinkedIn-Post, einen Newsletter-Absatz oder eine Präsentationsfolie machen.
- **Für Power-User:** Tools wie Readwise oder Zotero sammeln Ihre Highlights automatisch und lassen sich als Textdatei in ChatGPT füttern — perfekt für Vielleser.

---

## Prompt 1: Podcast / Video destillieren

```
<quelle>
[Transkript einfügen / URL / Datei hochladen]
</quelle>

<aufgabe>
Extrahiere die 10 wichtigsten Erkenntnisse aus dieser Quelle.

Für jede Erkenntnis:
1. Ein-Satz-Zusammenfassung — was ist der Kernpunkt?
2. Warum ist das relevant? — in einem Satz
3. Konkreter nächster Schritt — was kann ich diese Woche
   damit anfangen?
</aufgabe>

<format>
Nummerierte Liste. Knapp und actionable.
Keine Nacherzählung — nur destillierte Essenz.
</format>
```

---

## Prompt 2: Buch in 5 Minuten erfassen

```
<quelle>
[Buchtext / Kapitel / Zusammenfassung einfügen]
</quelle>

<aufgabe>
Erstelle eine kompakte Buch-Zusammenfassung:

<kernthese>
Was ist die zentrale Aussage des Buches in 1–2 Sätzen?
</kernthese>

<top5_ideen>
Die 5 wichtigsten Ideen — jeweils in 2–3 Sätzen.
Keine Nacherzählung, sondern die destillierte Erkenntnis.
</top5_ideen>

<anwendung>
Für jede Idee: Ein konkretes Beispiel, wie ich das
in meinem Alltag / Beruf anwenden kann.
</anwendung>

<zitate>
Die 3 stärksten Zitate aus dem Buch — die, die hängenbleiben.
</zitate>

<bewertung>
Für wen ist dieses Buch wertvoll? Für wen nicht?
Was fehlt oder wird überbewertet?
</bewertung>
</aufgabe>
```

---

## Prompt 3: Artikel für die eigene Situation auswerten

```
<quelle>
[Artikel-Text oder URL einfügen]
</quelle>

<kontext>
Meine Situation: [z.B. "Ich bin Berater im Bankensektor und
evaluiere KI-Tools für meine Kunden"]
</kontext>

<aufgabe>
Lies den Artikel und beantworte:
1. Was ist die Kernaussage in einem Satz?
2. Welche 3 Punkte sind für MEINE Situation relevant?
3. Was sollte ich basierend darauf konkret tun?
4. Gibt es etwas, dem ich widersprechen sollte?
5. Welche Fragen wirft der Artikel auf, die ich weiter
   recherchieren sollte?
</aufgabe>
```

---

## Von der Destillation zur Weiterverarbeitung

Ein destilliertes Podcast-Ergebnis können Sie sofort weiterverwenden:

| Weiterverarbeitung | Follow-up Prompt |
|-------------------|-----------------|
| LinkedIn-Post | *„Mach aus Erkenntnis Nr. 3 einen LinkedIn-Post (max. 200 Wörter)"* |
| Newsletter-Absatz | *„Schreibe Erkenntnis Nr. 5 als Newsletter-Absatz für Bankmitarbeiter"* |
| Präsentationsfolie | *„Erstelle aus den Top 5 eine Folie mit Stichpunkten + einer Kernaussage"* |
| Team-Briefing | *„Fasse die 3 relevantesten Erkenntnisse für mein Team zusammen (max. 100 Wörter)"* |

---

> 💡 **Die Denkweise:** Information ist wertlos, wenn sie nicht angewendet wird. Die Frage ist nie „Was habe ich gelesen?" sondern „Was habe ich daraus gemacht?" Destillation schließt diese Lücke.

---

