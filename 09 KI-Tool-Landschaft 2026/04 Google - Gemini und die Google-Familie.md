# Google — Gemini, NotebookLM, Imagen und Veo

**Der tief in Google Workspace integrierte KI-Assistent — plus die besten Tools für Recherche und Videogenerierung**

---

## Warum dieses Tutorial?

Google hatte einen schwierigen Start im KI-Wettrennen. Während OpenAI 2022 mit ChatGPT die Welt überraschte, kam Googles erste Antwort („Bard") eher zögerlich und mit peinlichen Fehlern in die Schlagzeilen. Das ist vorbei. **Gemini** ist seit der Version 2.5 eine ernstzunehmende Alternative zu ChatGPT und Claude, und in einigen Bereichen — besonders bei multimodalen Aufgaben und in der Integration mit Google Workspace — sogar konkurrenzlos.

Noch wichtiger: Google bietet 2026 mehrere Tools an, die außerhalb von Gemini laufen, aber trotzdem enorm nützlich sind. **NotebookLM** ist für viele Einsteiger das beste Recherche-Tool überhaupt. **Veo** ist aktuell eines der stärksten Videomodelle am Markt. Und **Nano Banana** (das Google-Bildmodell) hat sich als günstige, schnelle Alternative zu Midjourney etabliert.

**Was Sie nach diesem Tutorial wissen werden:**

- Welche Gemini-Modelle 2026 verfügbar sind und wann welches sinnvoll ist
- Wie Gemini mit Gmail, Google Docs und Drive zusammenarbeitet
- Was NotebookLM ist und warum es das beste Tool für „Recherche in eigenen Dokumenten" ist
- Wofür Sie Imagen, Nano Banana und Veo brauchen
- Welches Google-Abo für welche Zielgruppe passt
- Wie die Datenschutz-Situation gegenüber OpenAI und Anthropic aussieht

---

## Die Firma und das Ökosystem

Google braucht man nicht lang vorzustellen. Wichtig ist nur: Die KI-Produkte bei Google sind über **mehrere Marken und Websites** verteilt, und das verwirrt Einsteiger. Hier die Übersicht:

| Produkt | URL / Zugang | Zweck |
|---------|--------------|-------|
| **Gemini** | gemini.google.com | Der Chat-Assistent, vergleichbar mit ChatGPT |
| **NotebookLM** | notebooklm.google.com | Recherche auf Basis eigener Dokumente |
| **Google AI Studio** | aistudio.google.com | Entwickler-Oberfläche für Modelltests |
| **Google Workspace** | innerhalb von Docs, Gmail, Sheets, Slides | Eingebettete KI-Funktionen |
| **Veo** | Über Gemini-Abos bzw. über Vertex AI | Videomodell |
| **Imagen / Nano Banana** | Über Gemini-Abos bzw. API | Bildmodelle |

Fast alle Modelle laufen unter der Haube mit **Gemini 3** (oder einer Variante davon). Was sich unterscheidet, ist die Oberfläche und die spezifischen Features.

---

## Die Gemini-Modell-Familie 2026

Google strukturiert die Gemini-Familie ähnlich wie Anthropic in mehrere Größen:

### Gemini 3 Pro — das Flaggschiff

Das stärkste allgemein verfügbare Modell. Besonders gut in:

- Multimodalen Aufgaben (Bild, Text, Audio, Video in einer Anfrage)
- Langen Kontexten (aktuell mehrere Millionen Tokens im Top-Tarif)
- Integration mit Google-eigenen Daten (Gmail, Drive, Calendar)

### Gemini 3 Flash — der schnelle Alltagsarbeiter

Ein bewusst schnelleres und günstigeres Modell, das trotzdem nah an der Pro-Qualität bleibt. In den meisten Abos nehmen Sie Flash für schnelle Fragen und Pro für anspruchsvolle Aufgaben.

### Gemini 3 Thinking / Deep Think

Eine Variante mit explizitem „Nachdenken" vor der Antwort — analog zu ChatGPTs Thinking-Modus und Claudes Extended Thinking. Für Mathe, Logik, komplexe Analysen.

### Gemini Ultra (bei manchen Tarifen)

Ein experimenteller Höchstleistungs-Modus, der für den Ultra-Tarif angeboten wird.

### Bildmodelle: Imagen und Nano Banana

- **Imagen** — das „klassische" Google-Bildmodell, eher im Hintergrund.
- **Nano Banana** — der inoffizielle, aber breit genutzte Name für das neueste Gemini-Bildmodell. Extrem schnell, qualitativ sehr gut, sehr günstig in der API. Wird in vielen Tools als Standard-Bildgenerator genutzt (auch die Illustrationen in diesem Tutorial entstehen über Nano Banana).

### Videomodell: Veo 3

Googles Videomodell, aktuell in Version 3 (manche Quellen nennen 3.1). Generiert kurze Clips mit Ton. Gilt Stand Frühjahr 2026 als eines der qualitativ stärksten Videomodelle am Markt.

---

## Die Abos 2026

Google bietet mehrere Wege, Gemini zu abonnieren — und diese Wege überschneiden sich mit dem Google-One-Speicherabo. Das ist verwirrend. Hier der Überblick:

### Gemini Free

- Zugriff auf Gemini 3 Flash
- Begrenzte Nutzung von Gemini 3 Pro
- Einfache Bildgenerierung
- Begrenzter Zugriff auf NotebookLM
- Keine Veo-Nutzung

**Für wen?** Gelegenheitsnutzer, alle die Google-Produkte sowieso täglich nutzen und ab und zu schnell etwas fragen.

### Google AI Pro (früher „Google One AI Premium", ~20 € pro Monat)

- Voller Gemini-3-Pro-Zugang
- Deep Research-Modus
- Veo-Videogenerierung mit Quoten
- Mehr Speicher in Google Drive (meist 2 TB)
- Integration in Google Workspace (Gemini direkt in Docs, Gmail, Sheets, Slides)
- Priorität bei neuen Features

**Für wen?** Alle, die bereits Google Workspace oder Google Drive intensiv nutzen und KI in ihrer bestehenden Umgebung verwenden wollen. Und alle, die ernsthaft mit Video generieren wollen (Veo-Zugang ist ein starker Grund).

### Google AI Ultra (~125 € pro Monat, zum Teil vergünstigt für die ersten drei Monate)

- Priorisierter Zugang zu Gemini Ultra / Deep Think
- Sehr großzügige Veo-Quoten
- 30 TB Speicher
- Deutlich höhere Limits

**Für wen?** Vielnutzer, die intensiv mit Video arbeiten oder den absoluten Höchstzugriff brauchen. Für die meisten Einzelpersonen zu teuer und zu groß.

### Gemini for Workspace (Business-Tarife, ab ca. 25 € pro Nutzer pro Monat)

Der Team-/Unternehmens-Tarif. Gemini ist damit **direkt in Gmail, Google Docs, Sheets, Slides und Meet** eingebettet. Zusätzlich gibt es:

- Datenschutz-Zusage, dass Unternehmens-Daten nicht zum Training verwendet werden
- Enterprise-Admin-Funktionen
- DSGVO-Konformität (Google Workspace ist für die EU in der Regel passend zertifiziert)
- Integration mit Google Meet (automatische Protokolle, Zusammenfassungen, Übersetzungen)

**Für wen?** Jede Organisation, die bereits Google Workspace als Mail- und Office-Umgebung nutzt. Wer ohnehin im Google-Ökosystem arbeitet, bekommt hier den mit Abstand reibungslosesten KI-Zugang.

---

## Die wichtigsten Funktionen — ein kleiner Rundgang

### 1. Der Gemini-Chat

Die Web-Oberfläche ist klar und schnell. Ein paar praktische Hinweise:

- **„@" für Google-Dienste:** In Gemini können Sie @Gmail, @Drive, @Calendar, @YouTube schreiben, und Gemini greift auf die entsprechenden Dienste zu. „Zeige mir alle E-Mails von meiner Chefin in dieser Woche und fasse sie zusammen" ist ein realistisches Beispiel.
- **Bild- und Videoanalyse:** Gemini ist multimodal von Anfang an gebaut — Bilder und kurze Videos hochzuladen funktioniert besonders zuverlässig.
- **Live-Modus:** Über die Gemini-App auf dem Smartphone können Sie Gemini live durch die Kamera schauen lassen und in Echtzeit Fragen stellen („Was steht auf diesem Schild?" — mitten im Urlaub sehr praktisch).

### 2. Integration in Google Workspace

Das ist der größte Unterschied zu OpenAI und Anthropic: **Wenn Sie in Google Docs schreiben, ist Gemini direkt im Seitenbereich oder über eine Taste erreichbar.** Beispiele:

- **In Gmail:** „Schreibe eine höfliche Absage auf diese Einladung" — Gemini liest die Mail, schlägt eine Antwort vor.
- **In Google Docs:** Markieren Sie einen Absatz, klicken Sie auf das Gemini-Symbol, lassen Sie ihn umformulieren, kürzen oder übersetzen.
- **In Sheets:** Gemini kann aus natürlichsprachigen Anweisungen Formeln generieren oder Zellen ausfüllen.
- **In Slides:** Bildvorschläge, Layout-Generierung, automatische Umwandlung von Text in Folien.
- **In Meet:** Automatische Besprechungsnotizen, Zusammenfassungen, Echtzeit-Übersetzungen.

Wer Google Workspace ohnehin nutzt, spart mit Gemini schlicht Klicks. Das klingt banal, ist aber im Alltag ein echter Produktivitätsgewinn.

### 3. NotebookLM — das Recherche-Kraftwerk

**NotebookLM** (notebooklm.google.com) ist ein eigenständiges Google-Produkt, das vielen Einsteigern unbekannt ist — obwohl es eines der besten Tools für Recherche-Aufgaben ist.

Die Idee: Sie legen ein „Notebook" an und laden dort **Quellen** hoch — PDFs, Webseiten, YouTube-Videos, Google Docs, Tonaufnahmen, eingescannte Dokumente. NotebookLM indexiert diese Quellen und beantwortet dann Ihre Fragen **ausschließlich auf Basis dieser Dokumente**, mit exakten Zitaten und Quellenangaben.

Das heißt: Kein „Halluzinieren" mit Fantasiewissen. Wenn etwas nicht in den hochgeladenen Dokumenten steht, sagt NotebookLM das ehrlich.

Typische Einsatzgebiete:

- Einen Stapel wissenschaftlicher Papers durcharbeiten
- Ein Forschungsprojekt mit vielen PDFs organisieren
- Ein Schulbuch oder Lehrbuch in eine Lernhilfe verwandeln
- Interview-Transkripte auswerten
- Eine Produktdokumentation zu einer befragbaren Wissensbasis machen

Besonderes Feature: **„Audio-Übersicht"**. NotebookLM kann aus Ihren Dokumenten automatisch einen kleinen Podcast generieren — zwei KI-Stimmen unterhalten sich über den Inhalt. Das klingt wie eine Spielerei, ist aber für Lernende erstaunlich nützlich.

NotebookLM gibt es in einer kostenlosen und einer bezahlten Version. Der Free-Tier reicht für viele Zwecke schon weit.

### 4. Deep Research / Deep Search

Ähnlich wie bei ChatGPT und Perplexity gibt es in Gemini einen **Deep Research** Modus. Sie stellen eine Frage, und Gemini recherchiert 5–20 Minuten lang im Web, bevor es einen strukturierten Bericht liefert. Mit Zitaten.

Qualität: gut, aber Perplexity ist beim reinen Quellenfokus meist noch einen Tick treffsicherer. Gemini-Deep-Research ist besonders praktisch, wenn Sie ohnehin schon mit Gemini arbeiten und keinen Tool-Wechsel wollen.

### 5. Imagen / Nano Banana (Bilder)

Die Bildmodelle von Google rufen Sie entweder direkt in Gemini auf („Erstelle mir ein Bild von …") oder über die API bzw. Google AI Studio.

**Nano Banana** hat sich 2025/2026 zum heimlichen Standard für schnelle, günstige, hochwertige Bildgenerierung entwickelt. Die Stärken:

- Extrem schnell (wenige Sekunden pro Bild)
- Sehr günstig pro Bild (im Bruchteil eines Cents)
- Gute Text-Treue (deutlich besser als die meisten anderen Modelle bei Anweisungen)
- Foto-realistische und illustrative Stile möglich
- Bilder lassen sich gut nachbearbeiten (Bestehende Bilder per Prompt verändern)

Für professionelle Kunstrichtungs-Arbeit (Magazin-Cover, Buchillustrationen) ist Midjourney weiterhin erste Wahl. Für alles andere — inklusive Tutorial-Illustrationen, Präsentationsbilder, Social-Media-Grafiken — ist Nano Banana 2026 der pragmatischste Weg.

### 6. Veo 3 (Video)

**Veo** ist Googles Videomodell. Version 3 kann:

- Kurze Clips (aktuell bis ca. 10 Sekunden, je nach Tarif) aus Textbeschreibungen generieren
- **Native Audio-Generierung:** Stimmen, Umgebungsgeräusche, Musik — alles passend zum Video
- Existierende Bilder animieren („Bild-zu-Video")
- Kamerabewegungen und Übergänge respektieren

Im Vergleich zu Runway, Luma und Kling ist Veo 3 Stand Frühjahr 2026 in vielen Benchmarks vorne — vor allem durch die integrierte Audio-Generierung. Der Haken: Veo ist nur über die kostenpflichtigen Gemini-Abos zugänglich, und auch dort mit Quoten.

---

## Stärken und Schwächen auf einen Blick

### Was Gemini und Googles KI-Suite besonders gut können

- **Integration in Google Workspace** — unschlagbar, wenn Sie ohnehin im Google-Ökosystem arbeiten.
- **Multimodal:** Text, Bild, Audio, Video — alles aus einer Hand.
- **NotebookLM** — das beste Recherche-Tool für eigene Dokumente.
- **Veo 3** — aktuell eines der stärksten Videomodelle.
- **Nano Banana** — bestes Preis-Leistungs-Verhältnis bei Bildgenerierung.
- **Großer Kontext** — Gemini 3 Pro kann sehr lange Dokumente verarbeiten.
- **Datenschutz in Workspace-Tarifen** ist für viele europäische Unternehmen akzeptabel, weil Google Workspace bereits DSGVO-zertifizierte Verträge anbietet.

### Was Gemini nicht so gut kann

- **Reine Chat-Qualität im Alltag:** Viele Profis berichten, dass die „Gesprächsführung" bei Gemini weniger nuanciert wirkt als bei Claude oder ChatGPT. Das ist subjektiv, aber wiederkehrend.
- **Produkt-Verwirrung:** Wer sich neu orientiert, versteht oft nicht, welches Gemini-Produkt er in welcher Oberfläche bekommt — Google AI Studio vs. Gemini App vs. Workspace-Integration vs. NotebookLM.
- **Ökosystem an Custom-Assistenten** ist kleiner als bei OpenAI.
- **Nicht-Google-Nutzer profitieren weniger** — wer mit Microsoft 365 arbeitet, verliert den größten Vorteil (die Workspace-Integration).

---

## Für deutsche und europäische Nutzer

Hier wird es interessant: **Google Workspace ist in Europa seit Jahren als DSGVO-konform nutzbar**, und zwar mit Auftragsverarbeitungsverträgen, die viele deutsche Rechtsabteilungen akzeptieren. Das heißt in der Praxis:

- Wenn Ihre Organisation ohnehin Google Workspace nutzt und dafür einen passenden Vertrag hat, ist **Gemini for Workspace** datenschutzrechtlich meist unproblematisch nutzbar — zumindest nicht problematischer als die bisherige Google-Nutzung.
- Die **private Gemini-App mit Free-Tarif** fällt unter Googles Standard-Nutzungsbedingungen und ist in dem Sinne vergleichbar mit ChatGPT Free. Für berufliche Nutzung sensibler Daten nicht geeignet.
- **NotebookLM** ist ein Graubereich: Google macht Zusagen, aber die Datenverarbeitung ist auf Google-Servern. Für öffentliche Quellen völlig in Ordnung, für vertrauliche interne Dokumente sollten Sie das mit Ihrer Datenschutz-Verantwortlichen klären.

Eine einfache Faustregel: **Wer Google Workspace beruflich nutzt, nutzt Gemini beruflich. Wer Google ohnehin meidet, für den ist Gemini auch nicht die richtige erste KI.**

---

## Zusammenfassung in 30 Sekunden

Gemini ist die richtige Wahl für alle, die im Google-Ökosystem leben. **NotebookLM** ist unabhängig vom KI-Hintergrund eines der besten Recherche-Werkzeuge überhaupt und sollte in jedem KI-Werkzeugkasten sein. **Veo** ist für ernsthafte Videogenerierung aktuell die stärkste Option. **Nano Banana** ist das beste Preis-Leistungs-Verhältnis für Bildgenerierung. Und wer beruflich mit Google Workspace arbeitet, bekommt mit **Gemini for Workspace** einen der bequemsten KI-Zugänge, die es 2026 gibt.

---

## Nächste Schritte

**Weiter mit:** [05 Perplexity — Der Recherche-Spezialist](./05%20Perplexity%20-%20Der%20Recherche-Spezialist.md)

**Oder tiefer ins Thema:**
- **Kapitel 04 (bestehend)** — Prompt Engineering für Bilder, inkl. Hinweisen zu Nano Banana
- **Kapitel 05 (bestehend)** — Prompt Engineering für Videos, inkl. Veo
