# Anthropic — Claude und die Claude-Familie

**Der analytische Denker unter den KI-Assistenten — besonders stark bei langen Texten, Code und Analyse**

---

## Warum dieses Tutorial?

Wenn ChatGPT der bekannte Allrounder ist, dann ist **Claude** der ruhige, sorgfältige Fachmann, den viele Profis inzwischen im Hintergrund benutzen. Claude wird von der Firma **Anthropic** gebaut, die 2021 von ehemaligen OpenAI-Mitarbeitern gegründet wurde. Der Claim des Unternehmens: „AI that is safe, beneficial, and understandable." Das klingt nach Marketing — in der Praxis merkt man den Unterschied aber tatsächlich am Verhalten des Modells. Claude widerspricht häufiger, erklärt mehr, erfindet weniger.

Für deutschsprachige Nutzer hat Claude in den letzten zwei Jahren enorm aufgeholt. Während in den ersten Versionen englischer Text deutlich besser war, ist Claude 2026 in deutscher Sprache ebenbürtig und in vielen Nuancen sogar besser — besonders beim Schreiben längerer, zusammenhängender Texte.

**Was Sie nach diesem Tutorial wissen werden:**

- Welche Claude-Modelle 2026 verfügbar sind und wann Sie welches nehmen
- Was Claude besonders gut kann (und wo ChatGPT besser ist)
- Welche Abos es gibt und für wen sie sich lohnen
- Was **Claude Code** ist und warum es für Nicht-Entwickler auch interessant sein kann
- Was **Projects** sind und wie Sie damit eine Art eigenes Claude-Gedächtnis aufbauen
- Wie die Datenschutz-Situation für europäische Nutzer aussieht

---

## Die Firma hinter Claude

**Anthropic** ist ein US-Unternehmen mit Hauptsitz in San Francisco. Die Gründer — darunter Dario und Daniela Amodei — kamen aus der Forschungsabteilung von OpenAI und wollten explizit einen Anbieter aufbauen, der Sicherheit und Verlässlichkeit stärker gewichtet als Marktanteile. Das Unternehmen ist unter anderem von Google, Amazon und verschiedenen Risikokapitalgebern finanziert.

Für Sie als Nutzer ist wichtig: Claude ist über drei Wege erreichbar:

1. **claude.ai** — die Web-Oberfläche, vergleichbar mit chatgpt.com
2. **Claude Desktop App** — die native Mac-/Windows-App, die auch den sogenannten **Cowork-Modus** enthält
3. **Claude Code** — ein Kommandozeilen-Tool (und eine Desktop-App) für Entwickler und fortgeschrittene Nutzer

Kapitel 10 dieses Tutorial-Repos behandelt die drei Zugänge im Detail. In diesem Kapitel konzentrieren wir uns auf das Modell, die Abos und die wichtigsten Funktionen.

---

## Die Claude-Familie 2026

Anthropic strukturiert seine Modelle in drei klar getrennte Klassen — das ist angenehm übersichtlich, besonders im Vergleich zu OpenAI:

### Claude Opus 4.6 — das Flaggschiff

Das stärkste verfügbare Claude-Modell. Zuständig für die schwierigsten Aufgaben:

- Komplexe Analysen, wissenschaftliches Schreiben, lange juristische Texte
- Aufwändige Coding-Aufgaben und Architektur-Entwürfe
- Recherche mit vielen Quellen und langen Argumentationsketten
- Alles, bei dem Sie die beste verfügbare Qualität brauchen

Opus ist das langsamste und teuerste Modell. Für den Alltag überdimensioniert — für schwierige Aufgaben aber oft konkurrenzlos. Wer das Claude-Pro-Abo hat, bekommt begrenzten Zugriff darauf.

### Claude Sonnet 4.6 — der Alltagspartner

Die mittlere Klasse und für die meisten Nutzer das wichtigste Modell. Sonnet ist etwa so schnell wie GPT-5, aber oft besser bei:

- Längeren Texten (es verliert weniger schnell den Faden)
- Nuancierten Umformulierungen und Stilwechseln
- Code-Reviews und Debugging
- Aufgaben, bei denen man schrittweise denken muss

Als Faustregel: **Wenn Sie nur ein Claude-Modell nutzen wollen — nehmen Sie Sonnet.** Es ist der beste Kompromiss aus Qualität, Geschwindigkeit und Verfügbarkeit.

### Claude Haiku 4.5 — der schnelle Helfer

Das kleinste und schnellste Modell. Haiku ist für Aufgaben gedacht, bei denen es auf Tempo und Kosten ankommt:

- Kurze Zusammenfassungen
- Einfache Klassifikationen („Ist diese E-Mail wichtig?")
- Auto-Vervollständigungen
- Hintergrund-Tasks in Agenten-Systemen

Sie werden Haiku in der normalen Claude.ai-Oberfläche selten explizit auswählen — aber es läuft im Hintergrund, wenn Claude schnelle Zwischenschritte braucht.

### 1-Million-Token-Kontextfenster

Ein technisches Detail, das in der Praxis aber sehr wichtig ist: **Claude Opus und Sonnet können inzwischen bis zu einer Million Tokens auf einmal verarbeiten.** Das entspricht grob einem Text von 700.000–750.000 deutschen Wörtern — oder umgerechnet ein ganzes Buch plus umfangreiche Hintergrund-Dokumente in einem einzigen Prompt.

Was Sie damit praktisch machen können:

- Ein komplettes Manuskript hochladen und Fragen dazu stellen
- Ein ganzes Handbuch oder ein umfangreiches Vertragswerk analysieren
- Einen Code-Basis-Dump hochladen und besprechen lassen
- Lange Konversationen führen, ohne dass Claude „vergisst", was am Anfang gesagt wurde

Das ist einer der wichtigsten Gründe, warum Profis bei langen Aufgaben zu Claude wechseln — ChatGPT hat hier aktuell noch ein kleineres Kontextfenster.

---

## Die Abos 2026

Anthropic ist bei den Abo-Stufen deutlich simpler als OpenAI. Die Preise sind hier ungefähre Angaben für April 2026 — prüfen Sie vor Abschluss direkt auf claude.ai.

### Free (0 €)

- Begrenzte Nutzung von Claude Sonnet (kein Opus)
- Nachrichten-Limit pro Zeitfenster
- Zugriff auf die wichtigsten Basis-Funktionen
- Kein Claude Code, keine Projects

**Für wen?** Wer Claude erstmal kennenlernen will oder nur gelegentlich etwas nachfragt.

### Claude Pro (~20 USD / ca. 23 € pro Monat)

Der Standard-Plan für Einzelnutzer. Enthält:

- 5-mal höhere Nutzung als Free
- Zugriff auf Claude Sonnet ohne Einschränkungen im Rahmen der Quota
- Begrenzter Zugriff auf Claude Opus (das Flaggschiff)
- **Projects** (siehe weiter unten)
- **Claude Code** als Kommandozeilen-Werkzeug
- Datei-Uploads in großem Umfang
- Extended Thinking Mode (Claude denkt explizit länger nach)

**Für wen?** Für alle, die regelmäßig mit KI arbeiten und besonders viel mit längeren Texten, Analyse oder Code zu tun haben. Wenn Sie schon ein ChatGPT-Plus-Abo haben und zwischen den beiden wechseln wollen — Claude Pro ist das direkte Gegenstück.

### Claude Max (ab ~100 USD / ca. 115 € pro Monat)

Ein Vielnutzer-Abo, vergleichbar mit ChatGPT Pro. Gibt deutlich höhere Limits, mehr Opus-Zugang und bessere Verfügbarkeit in Stoßzeiten. Es gibt mehrere Stufen von Max — je nachdem, wie viel Sie nutzen.

**Für wen?** Entwickler, Researcher, Autorinnen und Autoren, die Claude viele Stunden pro Tag verwenden.

### Claude Team (ab ~25 € pro Nutzer pro Monat, Mindest­teamgröße)

Der Team-Plan. Enthält alles aus Pro, zusätzlich:

- Gemeinsame **Projects** (mehrere Personen können am selben Projekt arbeiten)
- Zentrale Nutzerverwaltung, Admin-Features
- **Datenschutz-Zusage:** Ihre Eingaben werden nicht zum Training verwendet
- Bessere Rechnungsstellung für Teams

**Für wen?** Teams, die ernsthaft mit Claude arbeiten und dabei Datenschutz ein Thema ist.

### Claude Enterprise

Individuelles Pricing. Für Unternehmen mit besonderen Compliance-Anforderungen, sehr vielen Nutzern oder speziellen Integrationen.

---

## Die wichtigsten Funktionen — ein kleiner Rundgang

### 1. Der normale Chat

Auf claude.ai sieht das Chat-Interface sehr ähnlich aus wie bei ChatGPT. Ein paar Besonderheiten:

- **Datei-Upload direkt per Drag & Drop** — PDFs, Word, Excel, Bilder, Code-Dateien. Claude verarbeitet auch sehr lange Dateien zuverlässig.
- **Artifacts** — wenn Claude etwas längeres erzeugt (ein Dokument, eine Tabelle, Code, eine kleine Web-App), erscheint das in einem separaten Panel rechts neben dem Chat. Sie können es dort direkt anschauen und bearbeiten.
- **Extended Thinking** — in den Einstellungen zum Chat können Sie Claude explizit sagen: „Denke länger nach." Das Modell schreibt dann zuerst einen sichtbaren Denk-Monolog, bevor es antwortet. Besonders hilfreich bei komplexen Aufgaben.

### 2. Projects

Ein **Project** ist im Prinzip ein thematischer Arbeitsbereich. Sie geben ihm einen Namen („Buch-Manuskript Kapitel 4", „Kundenprojekt Müller", „Steuererklärung 2025"), laden relevante Dateien und Hintergrund-Informationen hoch und hinterlegen eine kurze Beschreibung, wofür das Projekt ist.

Immer, wenn Sie dann in diesem Projekt einen neuen Chat starten, hat Claude automatisch den Kontext parat: die Dateien, die Beschreibung, die wichtigsten Instruktionen. Sie müssen sich nicht jedes Mal neu erklären.

Das ist der größte Unterschied zu ChatGPTs „Memory" — Projects sind **thematisch getrennt** und **explizit kuratiert**. Sie wissen genau, welches Wissen Claude in welchem Kontext hat. Das ist besonders für berufliche Arbeit sehr wertvoll.

Kapitel 03 dieses Tutorial-Repos zeigt praktische Beispiele für Projects (teilweise auch für ChatGPT-GPTs umsetzbar).

### 3. Claude Code

**Claude Code** ist ein eigenes Tool, das über die Kommandozeile läuft — und inzwischen auch als Desktop-Anwendung. Ursprünglich für Entwickler gedacht, lohnt es sich aber auch für ambitionierte Nicht-Entwickler:

- Claude Code liest Ihren lokalen Ordner (z.B. einen Projekt-Ordner auf Ihrem Rechner)
- Es bearbeitet Dateien direkt dort, wo sie liegen
- Es kann lange Arbeitsschritte selbstständig ausführen

Beispiele, wie Nicht-Entwickler Claude Code nutzen:

- Ein Ordner mit hundert Word-Dateien soll umbenannt und sortiert werden
- Eine Excel-Tabelle soll in zehn kleinere Tabellen aufgeteilt werden
- Ein längeres Buchmanuskript soll kapitelweise lektoriert werden

Ausführliche Anleitung dazu finden Sie in **Kapitel 10** dieses Tutorial-Repos.

### 4. Cowork-Modus in der Desktop-App

In der Claude-Desktop-App gibt es einen **Cowork-Modus** — ein Modus, in dem Claude direkt Dateien auf Ihrem Rechner lesen, bearbeiten und erstellen kann, plus Zugriff auf sogenannte **Skills** und **MCPs** (kleine Werkzeuge, die zusätzliche Funktionen bringen). Das ist der spannendste Zugangsweg für Nicht-Entwickler, weil Sie Claude hier wie einen echten Assistenten im Dateisystem benutzen.

Dieses Tutorial selbst wurde übrigens im Cowork-Modus geschrieben — es ist nicht nur Theorie.

Auch hier: Details in Kapitel 10.

### 5. Web-Suche

Claude hat inzwischen einen eingebauten Web-Such-Modus. Sie aktivieren ihn über ein kleines Symbol unter dem Eingabefeld oder Claude erkennt selbständig, wann Web-Recherche sinnvoll ist. Die Qualität ist gut, aber für reine Recherche-Aufgaben greifen Profis meist zu Perplexity (siehe Kapitel 05).

---

## Stärken und Schwächen auf einen Blick

### Was Claude besonders gut kann

- **Sehr lange Texte:** Das 1-Million-Token-Kontextfenster ist aktuell einzigartig in dieser Kombination aus Qualität und Verfügbarkeit.
- **Sprachgefühl:** Claude schreibt — das ist Geschmackssache — oft ein gutes Stück geschmeidigerer, nuancierter auf Deutsch als ChatGPT. Wer Lektorat oder Stilarbeit macht, merkt den Unterschied schnell.
- **Code:** Viele professionelle Entwicklerinnen und Entwickler nutzen Claude inzwischen als Haupt-Werkzeug.
- **Analyse und Argumentation:** Claude neigt weniger dazu, Dinge zu erfinden oder zu übertreiben, und verweigert eher eine Aussage, als sie zu improvisieren.
- **Projects:** Ein wirklich gutes System, um wiederkehrende Arbeit zu organisieren.
- **Cowork-Modus und Claude Code:** Der direkte Zugriff auf das Dateisystem ist für viele Aufgaben ein Game-Changer — mehr dazu in Kapitel 10.

### Was Claude nicht so gut kann

- **Bildgenerierung:** Claude erzeugt selbst keine Bilder. Dafür braucht es ein anderes Tool (DALL·E, Midjourney, Flux, Nano Banana — siehe Kapitel 07).
- **Video:** Gleiche Situation. Kein eigenes Videomodell.
- **Kostenloser Plan ist knapp bemessen:** Wer Claude ernsthaft nutzen will, kommt am Pro-Abo kaum vorbei. Der Free-Plan fühlt sich schneller eng an als bei ChatGPT.
- **Voice Mode noch weniger ausgebaut** als bei ChatGPT. Für gesprochene Dialoge ist ChatGPT aktuell bequemer.
- **Kleineres Ökosystem an Custom-GPT-ähnlichen Shared Assistants:** Projects sind gut, aber weniger spielerisch und weniger öffentlich auffindbar als die GPT-Store-Welt bei OpenAI.

---

## Für deutsche und europäische Nutzer

Anthropic ist wie OpenAI ein US-Anbieter — der Datenschutz-Rahmen ist also ähnlich. Ein paar Unterschiede, die für viele Nutzer wichtig sind:

1. **Claude verwendet Eingaben standardmäßig nicht zum Training.** Das ist der wichtigste Unterschied zu ChatGPTs Free- und Plus-Plan. Schon als Einzelnutzer bekommen Sie bei Claude eine explizite Zusage, dass Ihre Chats nicht zum Modell-Training verwendet werden. Ausnahme: Sie melden ausdrücklich Inhalte als „darf für Verbesserung genutzt werden".

2. **Team- und Enterprise-Pläne** bieten zusätzliche Datenschutz-Garantien und können in europäischen Rechenzentren gehostet werden (je nach Vertrag).

3. **Praktische Regel:** Wer ohnehin mit amerikanischen Cloud-Anbietern arbeitet (Google Workspace, Microsoft 365), für den ist Claude aus Datenschutz-Sicht ähnlich einzustufen wie ChatGPT. Wer einen reinen EU-Anbieter braucht, schaut in Kapitel 06 — dort finden Sie **Mistral Le Chat**.

---

## Zusammenfassung in 30 Sekunden

Claude ist der beste Partner für lange, anspruchsvolle Denkarbeit — Texte, Code, Analyse. Das **Claude-Pro-Abo** lohnt sich fast immer für Menschen, die beruflich mit Schreiben oder Code zu tun haben. Wer ohnehin schon ChatGPT-Plus hat und die Datei-Analyse-Arbeit nicht zufriedenstellend findet, sollte Claude zusätzlich ausprobieren — die monatlichen Kosten sind identisch, und viele Profis kommen am Ende mit beiden Abos zur besseren Arbeit als mit nur einem. Für wirklich tiefen Einstieg ins Dateisystem und lokale Arbeit unbedingt auch **Kapitel 10 (Claude-Infrastruktur)** lesen.

---

## Nächste Schritte

**Weiter mit:** [04 Google — Gemini, Imagen, Veo und NotebookLM](./04%20Google%20-%20Gemini%20und%20die%20Google-Familie.md)

**Oder direkt zu den praktischen Themen:**
- **Kapitel 10 (neu)** — Claude Desktop, Cowork und Claude Code im Detail
- **Kapitel 03** — GPTs und Projekte (viele Beispiele lassen sich direkt als Claude-Projects umsetzen)
