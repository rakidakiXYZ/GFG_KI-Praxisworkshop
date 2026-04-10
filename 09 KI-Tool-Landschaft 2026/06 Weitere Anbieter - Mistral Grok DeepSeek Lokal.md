# Weitere Anbieter — Mistral, Grok, DeepSeek und lokale Modelle

**Die spannenden Alternativen jenseits der Big Four — und warum Sie mindestens eine davon auf dem Schirm haben sollten**

---

## Warum dieses Tutorial?

Die vorherigen Kapitel drehen sich um die vier großen Namen: OpenAI, Anthropic, Google und Perplexity. Zusammen decken sie etwa 90 Prozent der alltäglichen KI-Nutzung ab. Aber es gibt **mindestens vier weitere Anbieter, die Sie kennen sollten** — nicht, weil sie die großen verdrängen werden, sondern weil jeder von ihnen in einer bestimmten Nische besser ist als die Big Four:

- **Mistral AI** — der europäische Anbieter, unverzichtbar für Datenschutz-sensible Fälle
- **xAI / Grok** — eng an X (Twitter) angebunden, starker Echtzeit-Bezug
- **DeepSeek** — chinesischer Anbieter, extrem günstig, interessant für API-Nutzer
- **Lokale Modelle** über Ollama und LM Studio — 100 Prozent offline, 100 Prozent Kontrolle

**Was Sie nach diesem Tutorial wissen werden:**

- Warum Mistral für deutsche und europäische Organisationen die wichtigste Alternative ist
- Was Grok anders macht und für wen es sinnvoll ist
- Warum DeepSeek den Markt durcheinander gewirbelt hat — und warum Sie trotzdem vorsichtig sein sollten
- Wie Sie lokale KI-Modelle auf Ihrem eigenen Rechner betreiben — und wann sich das lohnt

---

## Mistral AI — der europäische Anbieter

### Die Firma

**Mistral AI** wurde 2023 in Paris gegründet, von ehemaligen Forschern von Meta und Google DeepMind. Das Unternehmen ist einer der wenigen ernstzunehmenden KI-Anbieter mit Sitz in der Europäischen Union — und das ist aus Datenschutz-Sicht kein Nebenaspekt, sondern der wichtigste Grund, warum Mistral für viele Organisationen interessant ist.

Mistral hat mehrere Gesichter:

1. **Le Chat** — die Endnutzer-App unter chat.mistral.ai
2. **Mistral API / La Plateforme** — für Entwickler und API-Nutzer
3. **Open-Source-Modelle** — mehrere Mistral-Modelle stehen kostenlos zum Download bereit (siehe Abschnitt über lokale Modelle unten)

### Die Modelle 2026

- **Mistral Large (3)** — das Flaggschiff. Wettbewerbsfähig mit GPT-5 und Claude Sonnet, aber oft deutlich günstiger in der API.
- **Mistral Medium** — die Mittelklasse.
- **Mistral Small / Ministral** — schnelle, kleine Modelle für einfache Aufgaben.
- **Codestral** — ein Modell, speziell für Code trainiert.
- **Pixtral** — multimodales Modell, das Bilder verarbeiten kann.

Die hauseigenen Modelle sind solide — nicht ganz auf Augenhöhe mit GPT-5 Thinking oder Claude Opus, aber in vielen alltäglichen Aufgaben kaum zu unterscheiden.

### Le Chat — die Endnutzer-App

Le Chat ist Mistrals Antwort auf ChatGPT und Claude. Die Oberfläche ist übersichtlich, funktioniert auf Deutsch sehr gut und bietet:

- Web-Suche mit Quellen
- Datei-Upload (PDFs, Bilder)
- Bildgenerierung (über integrierte Modelle)
- Eine **Canvas-Funktion** für längere Dokumente
- **Code Interpreter** für Berechnungen und Datenanalyse

Le Chat ist im Free-Tier bereits relativ großzügig nutzbar — deutlich mehr als ChatGPT Free, wenn auch weniger als Gemini Free.

### Die Abos

- **Le Chat Free** — kostenlos, gute Nutzung möglich
- **Le Chat Pro** (~15 € pro Monat) — erweiterte Limits, Bildgenerierung, Priorität
- **Teams/Enterprise** — mit EU-Hosting, DSGVO-Verträgen, individuellen Angeboten

Die API-Preise für Mistral sind im Vergleich zu OpenAI und Anthropic deutlich niedriger — für Entwicklungsprojekte ein echtes Argument.

### Warum Mistral für europäische Nutzer wichtig ist

Das ist der Kern: **Mistral betreibt seine Infrastruktur in der EU, ist als europäisches Unternehmen dem europäischen Recht unterworfen, und bietet Verträge zur Auftragsverarbeitung an, die mit der DSGVO kompatibel sind.** Das heißt konkret:

- **Keine Datenübermittlung in die USA** (anders als bei OpenAI, Anthropic, Google, Perplexity)
- **Kein Schrems-II-Problem** — rechtlich deutlich einfacher für europäische Organisationen
- **EU-Ansprechpartner** — deutsche Rechtsabteilungen haben einen Gesprächspartner in Europa

Für viele deutsche Behörden, Verwaltungen, Schulen, Banken, Versicherungen und Unternehmen mit strengen Datenschutzanforderungen ist **Mistral aktuell die einzige realistische Option**, die nicht entweder einen US-Anbieter einbindet oder auf lokale Modelle ausweicht.

### Stärken und Schwächen

**Stärken:**
- EU-Anbieter mit klarer Datenschutz-Position
- Gute Qualität bei günstigem Preis (besonders in der API)
- Open-Source-Modelle kostenlos verfügbar
- Gute Mehrsprachigkeit — Le Chat kommt mit deutschem und französischem Text besonders gut klar

**Schwächen:**
- Das Ökosystem ist (noch) kleiner — weniger Tutorials, weniger Integrationen, weniger vorgefertigte Workflows
- Die Community ist kleiner — bei Problemen finden Sie seltener eine Lösung in fünf Sekunden bei Google
- Die aktuellsten Reasoning-Modelle hinken den Big Four einen kleinen Schritt hinterher

**Empfehlung:** Wenn Datenschutz in Ihrer Organisation eine Rolle spielt — testen Sie Mistral Le Chat parallel zu ChatGPT und Claude. Für viele alltägliche Aufgaben werden Sie keinen spürbaren Unterschied merken. Und im beruflichen Kontext ist „DSGVO-konform" oft wichtiger als das letzte Prozent Modell-Qualität.

---

## xAI Grok — die Twitter/X-Alternative

### Die Firma

**xAI** ist das KI-Unternehmen von Elon Musk, gegründet 2023 nach seinem Ausstieg aus OpenAI. Das Produkt heißt **Grok** und ist eng mit der Plattform **X** (ehemals Twitter) verknüpft, die Musk ebenfalls besitzt.

### Die Modelle

Aktuelle Versionen (April 2026, Details ändern sich schnell):

- **Grok 4** — das Flaggschiff, konkurrenzfähig mit GPT-5 und Claude Sonnet
- **Grok Fast** — eine kleinere, schnelle Version
- **Grok Vision** — mit Bildverständnis

### Was Grok anders macht

Zwei Besonderheiten, die Grok von den anderen Assistenten unterscheiden:

1. **Echtzeit-Zugriff auf X.** Grok kann aktuelle Posts, Trends und Diskussionen auf X durchsuchen. Wer viel mit Social-Media-Daten arbeitet, hat hier einen echten Vorteil — das kann kein anderer Assistent in dieser Form.
2. **Weniger restriktiv in der Tonalität.** Grok ist bewusst so eingestellt, dass es etwas direkter, ironischer und weniger „corporate" antwortet als ChatGPT oder Claude. Für manche Nutzer ist das angenehm — andere empfinden es als Nachteil.

### Der Zugang

Grok ist erreichbar über:

- **grok.com** — eigene Web-Oberfläche
- **Die X-App** — direkt in der Twitter-Zeitleiste
- **Das X-Premium-Abo** — hier ist Grok inkludiert

**Preise:** Grok ist Teil der X-Premium-Abostufen. X Premium kostet etwa 8 USD pro Monat und enthält begrenzten Grok-Zugriff. X Premium+ (ca. 40 USD pro Monat) bietet vollen Grok-Zugang.

### Für wen?

- **Ja:** Menschen, die ohnehin viel auf X unterwegs sind und die X-Integration nutzen wollen. Journalisten, Social-Media-Manager, Marktbeobachter.
- **Vielleicht:** Nutzer, die eine Alternative mit etwas lockererem Ton suchen.
- **Eher nein:** Alle, die beruflich sensible Daten verarbeiten (US-Anbieter, X-Integration macht Daten­fluss komplex).

---

## DeepSeek — der chinesische Preis-Brecher

### Die Firma

**DeepSeek** ist ein chinesisches KI-Unternehmen, das Anfang 2025 international Schlagzeilen gemacht hat: Die Firma veröffentlichte ein Sprachmodell, das mit GPT-4 und Claude 3.5 konkurrieren konnte — zu einem **Bruchteil der Kosten**. Der Schock hielt die Branche tagelang in Atem.

### Die Modelle

- **DeepSeek V3** — das Flaggschiff-Modell für allgemeine Aufgaben
- **DeepSeek R1** — ein Reasoning-Modell (ähnlich wie o1 und GPT-5 Thinking)
- Neuere Versionen erscheinen in kurzen Abständen

Die Qualität ist nahe an den westlichen Spitzenmodellen, die API-Preise liegen 5 bis 10 Mal darunter.

### Die Zugänge

- **chat.deepseek.com** — Web-Oberfläche, kostenlos nutzbar (mit Einschränkungen)
- **API** — für Entwickler, extrem günstig

### Warum DeepSeek trotzdem mit Vorsicht zu genießen ist

Drei Punkte, die Sie vor der Nutzung bedenken sollten:

1. **Datenverarbeitung in China.** Für europäische Organisationen datenschutzrechtlich komplex. Für öffentliche, unkritische Aufgaben möglich — für alles mit Personenbezug oder Geschäfts­geheimnissen nicht zu empfehlen.
2. **Zensur und inhaltliche Einschränkungen.** DeepSeek-Modelle antworten bei politisch heiklen Fragen (besonders zu China) oft auffällig vorsichtig oder weichen aus. Das ist für Alltagsarbeit meist kein Problem, aber man sollte es wissen.
3. **Geo-politische Unsicherheit.** Die Verfügbarkeit chinesischer KI-Dienste in Europa und den USA ist rechtlich und politisch nicht garantiert. Ein plötzliches Sperr-Szenario ist nicht auszuschließen.

### Für wen?

- **Ja:** Entwickler, die günstige API-Kosten brauchen und unkritische Daten verarbeiten. Bastler und Hobby-Projekte. Menschen, die einfach neugierig sind.
- **Eher nein:** Berufliche Nutzung mit sensiblen Daten. Organisationen mit Compliance-Anforderungen.

Ein ehrlicher Hinweis: Es gibt außerdem **offene DeepSeek-Modelle**, die Sie lokal auf Ihrem eigenen Rechner (oder in einem europäischen Rechenzentrum) betreiben können — in dem Fall fließen keine Daten zu DeepSeek ab. Mehr dazu im nächsten Abschnitt.

---

## Lokale Modelle — KI auf dem eigenen Rechner

### Die Idee

Alle bisher beschriebenen Tools haben eine Gemeinsamkeit: Sie laufen **in der Cloud**. Ihre Eingaben werden über das Internet an einen Server geschickt, dort verarbeitet, und die Antwort kommt zurück. Das funktioniert gut, wirft aber immer Datenschutz-Fragen auf.

Die Alternative: **Lokale Modelle.** Sie laden ein Sprachmodell einmalig auf Ihren eigenen Rechner (einige Gigabyte groß) und führen es dort aus. Nichts verlässt je Ihr Gerät. Keine Kosten pro Nutzung. Kein Datenschutz-Problem. Dafür brauchen Sie einen halbwegs leistungsfähigen Rechner — und ein paar Minuten für die Einrichtung.

### Die wichtigsten Tools: Ollama und LM Studio

**Ollama** (ollama.com) ist das einfachste Werkzeug, um lokale Modelle zu installieren. Im Prinzip öffnen Sie ein Terminal und tippen:

```bash
ollama run llama3
```

Nach wenigen Minuten Download läuft das Modell auf Ihrem Rechner und Sie können mit ihm chatten — exakt wie mit ChatGPT, nur lokal.

**LM Studio** (lmstudio.ai) ist die grafische Alternative: Eine App mit Such-, Download- und Chat-Oberfläche, ohne Terminal-Kenntnisse. Sie klicken sich durch die Modell-Bibliothek, wählen eines aus, laden es herunter und chatten los. Empfehlung für Einsteiger.

Beide Tools gibt es für macOS, Windows und Linux. Beide sind kostenlos.

### Welche Modelle lokal?

Einige bekannte Modelle, die Sie 2026 lokal laufen lassen können:

- **Llama 3.x** (Meta) — das bekannteste Open-Source-Modell
- **Mistral 7B** und **Ministral** — kleine, aber starke europäische Modelle
- **Qwen** (Alibaba) — gute Mehrsprachigkeit
- **Gemma** (Google) — kleine, effiziente Modelle
- **DeepSeek V3 / R1** (Open-Weight-Versionen)
- **Phi** (Microsoft) — besonders klein und effizient

### Was brauche ich als Hardware?

Die ehrliche Antwort: **Je größer das Modell, desto mehr Arbeitsspeicher brauchen Sie.**

- **Ein Laptop mit 16 GB RAM** reicht für kleine Modelle (7B-Parameter-Klasse). Die Qualität ist okay, aber deutlich unter GPT-5 und Claude.
- **Ein Rechner mit 32 GB RAM und einer halbwegs modernen GPU** (Apple Silicon M-Chips oder NVIDIA-Grafikkarte) erlaubt mittlere Modelle (13B–30B). Die Qualität ist solide, für viele Aufgaben brauchbar.
- **Ein Rechner mit 64+ GB RAM und einer leistungsstarken GPU** läuft die größten offenen Modelle (70B+). Hier ist die Qualität ernsthaft konkurrenzfähig zu Cloud-Angeboten — aber das ist keine Alltagsausstattung.

Die gute Nachricht für viele: Ein moderner MacBook Pro oder MacBook Air mit M3/M4-Chip und 16–24 GB Arbeitsspeicher läuft erstaunlich gut mit mittelgroßen Modellen. Keine extra Hardware nötig.

### Wofür lohnen sich lokale Modelle?

- **Datenschutz-kritische Aufgaben.** Wenn vertrauliche Dokumente oder personenbezogene Daten verarbeitet werden, ist lokal die einzige garantiert sichere Option.
- **Offline-Arbeit.** Im Zug, im Flugzeug, im Homeoffice ohne Internet.
- **Bastelprojekte und Experimente.** Kein Kostenrisiko, keine API-Limits.
- **Grundlagen-Verständnis.** Wer einmal selbst ein Modell lokal betrieben hat, versteht viel besser, was in der Cloud passiert.

### Wofür sind lokale Modelle (noch) nicht geeignet?

- **Wenn Sie die beste verfügbare Qualität brauchen.** GPT-5 Thinking, Claude Opus 4.6 und Gemini 3 Pro laufen in Größenordnungen, die Sie auf einem normalen Rechner nicht sinnvoll ausführen können.
- **Wenn Sie multimodale Top-Funktionen wollen** (Videogenerierung, komplexe Bildverarbeitung, Agent-Mode). Die sind meist an Cloud-Infrastruktur gebunden.
- **Wenn Sie keine Lust auf Einrichtung und Updates haben.** Lokale Modelle brauchen etwas Pflege.

---

## Die Kombi-Strategie: Was macht Sinn?

Die meisten Profis arbeiten nicht mit einem einzigen Tool, sondern mit **zwei oder drei in Kombination**. Hier ein paar realistische Setups:

### Setup 1 — „Der Durchschnittsnutzer"
- **ChatGPT Plus** oder **Claude Pro** als Haupt-Assistent
- **Perplexity Pro** für Recherche
- Kosten: ca. 40 € pro Monat

### Setup 2 — „Der deutsche Büromensch mit Datenschutz-Bewusstsein"
- **Mistral Le Chat Pro** als Haupt-Assistent
- **NotebookLM** (kostenlos) für Dokumenten-Recherche
- **Lokales Modell** (Ollama, kostenlos) für sensible Aufgaben
- Kosten: ca. 15 € pro Monat

### Setup 3 — „Der Vielschreiber und Analyst"
- **Claude Pro** für Textarbeit
- **Perplexity Pro** für Recherche
- **Google AI Pro** (Gemini + Veo + NotebookLM) für Bildungs- und Multimodal-Aufgaben
- Kosten: ca. 65 € pro Monat

### Setup 4 — „Der Entwickler"
- **Claude Pro** mit **Claude Code** als Haupt-Arbeitstool
- **ChatGPT Plus** als Zweit-Assistent
- **DeepSeek API** für günstige Hintergrund-Verarbeitung
- **Lokales Modell** (Ollama) zum Testen
- Kosten: ca. 45 € pro Monat (plus API-Nutzung)

---

## Zusammenfassung in 60 Sekunden

Neben den Big Four (ChatGPT, Claude, Gemini, Perplexity) gibt es vier sehr relevante Alternativen: **Mistral** (unverzichtbar für EU-Datenschutz), **Grok** (Echtzeit-X-Daten), **DeepSeek** (Preis-Brecher, aber datenschutzsensibel) und **lokale Modelle via Ollama oder LM Studio** (100 Prozent offline). Die wichtigste davon für deutsche und europäische Nutzer ist **Mistral** — wer beruflich Datenschutz ernst nimmt, sollte Le Chat mindestens parallel testen.

---

## Nächste Schritte

**Weiter mit:** [07 Bild- und Videomodelle im Vergleich](./07%20Bild-%20und%20Videomodelle%20im%20Vergleich.md)

Wenn Sie lokale Modelle wirklich ausprobieren wollen, ist der beste Startpunkt:

1. LM Studio herunterladen (lmstudio.ai)
2. Ein mittelgroßes Modell wählen (z.B. Llama 3.1 8B oder Mistral 7B Instruct)
3. Einfach chatten und ausprobieren

Das geht an einem Nachmittag und kostet nichts.
