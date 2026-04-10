# 03 Cowork Skills, MCPs und Plugins

**Die drei Werkzeug-Ebenen, die Cowork von „nett" zu „unverzichtbar" machen.**

---

## Warum dieses Tutorial?

In Kapitel 02 haben Sie Cowork installiert, einen Ordner gemountet und die ersten drei Aufgaben erledigt. Das funktioniert schon gut — aber es ist erst die Hälfte der Geschichte. Die eigentliche Stärke von Cowork liegt in drei Werkzeug-Ebenen, die Claude zusätzlich bekommt: **Skills**, **MCPs** und **Plugins**. Sie erweitern Claude um Spezialwissen (Word, Excel, PDF, Präsentationen), um Verbindungen zu externen Diensten (Slack, Google Drive, Gmail, Asana) und um wiederverwendbare Pakete, die beides zusammenbringen.

Dieses Tutorial erklärt, was diese drei Ebenen genau sind, wie sie sich voneinander unterscheiden, wie Sie sie in Cowork aktivieren und welche Sie als Einstieg definitiv haben sollten. Am Ende kennen Sie die mitgelieferten Kern-Skills, haben mindestens eine MCP-Verbindung getestet und wissen, wie Sie ein Plugin aus einer Marketplace installieren.

**Was Sie nach diesem Tutorial wissen werden:**

- Was ein **Skill** ist und wofür die wichtigsten mitgelieferten Skills gedacht sind.
- Was ein **MCP** ist, warum der Standard so wichtig geworden ist und wie Sie eine Verbindung einrichten.
- Was ein **Plugin** ist und wie es Skills und MCPs bündelt.
- Welche Marketplaces es gibt und wie Sie Plugins installieren.
- Wie Sie Skills, MCPs und Plugins sicher wieder entfernen oder deaktivieren.

---

## Ebene 1: Skills — Claude mit Spezialwissen ausstatten

Ein **Skill** ist im Kern eine kleine, in Markdown geschriebene Anleitung, die Claude für eine bestimmte Aufgabe befolgt. Stellen Sie sich Skills wie kurze Fachbücher vor: „So bearbeitest du eine Word-Datei", „So erstellst du eine saubere PowerPoint", „So füllst du ein PDF-Formular korrekt aus". Claude liest diese Anleitung, wenn die entsprechende Aufgabe ansteht, und befolgt sie Schritt für Schritt.

**Warum Skills überhaupt nötig sind:**

Ein großes Sprachmodell wie Claude „weiß" zwar theoretisch, wie eine `.xlsx`-Datei aufgebaut ist — aber in der Praxis gibt es viele Details, die leicht schiefgehen: Formeln werden beim Speichern kaputtgeschrieben, Formatierungen gehen verloren, Spezialzeichen landen an der falschen Stelle. Ein Skill sammelt die Best Practices für genau diese Fälle und legt sie Claude wie eine Checkliste vor die Nase. Das Ergebnis ist deutlich zuverlässiger als „rohes" Sprachmodell-Wissen.

**Die mitgelieferten Kern-Skills (Stand April 2026):**

Die Claude Desktop App bringt im Cowork-Modus einen Satz Standard-Skills mit, die für Büro-Arbeit unmittelbar nützlich sind:

- **`docx`** — Erstellt, liest und bearbeitet Word-Dokumente mit Formatierung, Kopf-/Fußzeilen, Tabellen, Inhaltsverzeichnissen und Bildern. Nutzt die `python-docx`-Bibliothek.
- **`xlsx`** — Erstellt und bearbeitet Excel-Dateien mit Formeln, Formatierung, mehreren Blättern und Diagrammen.
- **`pptx`** — Erstellt PowerPoint-Präsentationen mit Layouts, Master-Slides, Bildern und Notizen.
- **`pdf`** — Liest PDFs, extrahiert Text und Tabellen, füllt Formulare aus, führt PDFs zusammen, teilt sie auf.
- **`canvas-design`** — Visuelle Layouts wie Poster, Flyer und One-Pager direkt als Bild oder PDF.
- **`web-artifacts-builder`** — Interaktive HTML-/React-Artefakte für Prototypen und Dashboards.
- **`theme-factory`** — Konsistente Farben, Fonts und Themes für Slides, Docs und HTML.
- **`algorithmic-art`** — Generative Kunst mit p5.js für visuelle Experimente.
- **`schedule`** — Wiederkehrende Aufgaben planen, die Claude zu festen Zeiten ausführt.
- **`setup-cowork`** — Geführtes Onboarding, wenn Sie Cowork frisch einrichten.

Je nach Version Ihrer App können zusätzliche Skills dabei sein. Schauen Sie in der App unter **Einstellungen → Skills** oder im Chat mit der Frage „Welche Skills sind verfügbar?" nach.

**Wie Skills ausgelöst werden:**

Sie müssen Skills nicht explizit aufrufen. Claude erkennt anhand Ihrer Aufgabe automatisch, welcher Skill passt, und lädt ihn. Wenn Sie sagen „Erstelle mir eine Word-Datei mit …", dann greift Claude zum `docx`-Skill. Wenn Sie sagen „Mach aus diesen Bildern ein PDF", dann kommt der `pdf`-Skill zum Zug. Sie können Skills aber auch explizit ansprechen („Nutze den `pptx`-Skill, um …"), wenn Sie sichergehen wollen.

**Eigene Skills erstellen:**

Sie können eigene Skills schreiben — oder mit Hilfe von Claude schreiben lassen. Der mitgelieferte `skill-creator`-Skill führt Sie Schritt für Schritt durch den Prozess. Das Thema vertieft Kapitel 12 (KI-Agenten und Automatisierung); für den Anfang reichen die mitgelieferten Skills vollkommen.

---

## Ebene 2: MCPs — Claude mit der Außenwelt verbinden

**MCP** steht für **Model Context Protocol**. Es ist ein offener Standard, den Anthropic Ende 2024 vorgestellt hat und der sich seitdem in der gesamten KI-Branche durchgesetzt hat. Die Idee ist einfach: Anstatt jedes KI-Tool direkt an jeden externen Dienst anzubinden (Claude mit Slack, Claude mit Gmail, Claude mit Jira, und das dann noch für ChatGPT, Gemini und alle anderen …), gibt es **eine gemeinsame Sprache**, über die Modelle und Dienste miteinander reden. Jeder Dienst stellt einen kleinen „MCP-Server" bereit, jedes Modell spricht „MCP-Client", und die beiden verstehen sich.

**Was ein MCP-Server konkret tut:**

Ein MCP-Server liegt entweder auf Ihrem Computer (lokal) oder läuft als Web-Service (remote). Er stellt **Tools** und **Ressourcen** bereit, die Claude nutzen kann. Beispiele:

- Ein **Slack-MCP** stellt Tools bereit wie `post_message`, `search_channels`, `list_threads`.
- Ein **Google-Drive-MCP** stellt Tools bereit wie `search_files`, `download_file`, `create_doc`.
- Ein **GitHub-MCP** stellt Tools bereit wie `list_pull_requests`, `review_pr`, `create_issue`.
- Ein **PostgreSQL-MCP** stellt Tools bereit wie `run_query`, `describe_schema`.

Claude sieht diese Tools wie jedes andere Werkzeug (analog zu den Datei-Werkzeugen im Cowork-Ordner) und kann sie bei passenden Aufgaben aufrufen.

**Die wichtigsten MCPs für Cowork-Nutzer (Stand April 2026):**

- **Slack** — Nachrichten lesen, posten, Threads durchsuchen, Reminder setzen.
- **Google Drive / Workspace** — Dokumente finden, lesen, erstellen, teilen.
- **Gmail** — E-Mails lesen, schreiben, beantworten, filtern.
- **Google Calendar** — Termine sehen, erstellen, verschieben.
- **Notion** — Seiten und Datenbanken lesen und schreiben.
- **Asana / Linear / Jira** — Aufgaben verwalten, Sprints planen.
- **GitHub** — Pull Requests, Issues, Code-Reviews.
- **Figma** — Designs lesen, Komponenten abfragen.
- **Firecrawl** — strukturiertes Web-Scraping als Ergänzung zur normalen Web-Suche.
- **Apify** — Datenextraktion aus vielen Quellen.
- **Context7** — Zugriff auf aktuelle Library-Dokumentationen für Entwickler.

Die Liste wächst ständig. Eine aktuelle Übersicht finden Sie in der App unter **Einstellungen → Connectors** oder in der Anthropic-Dokumentation unter https://docs.claude.com/mcp.

**Eine MCP-Verbindung einrichten — am Beispiel Google Drive:**

1. Öffnen Sie die Claude Desktop App.
2. Gehen Sie zu **Einstellungen → Connectors** (je nach Version auch „Integrationen").
3. Suchen Sie **Google Drive** und klicken Sie auf **Verbinden**.
4. Es öffnet sich ein Browser-Fenster mit dem üblichen Google-Login. Melden Sie sich an.
5. Google fragt, welche Berechtigungen Sie erteilen möchten. Lesen Sie den Umfang sorgfältig — in der Regel reicht Lesezugriff, falls Sie keine Dateien verändern wollen. Bestätigen.
6. Zurück in der App erscheint der Connector als „verbunden" markiert.
7. Probieren Sie im nächsten Chat: „Suche in meinem Google Drive nach Dateien, die 'Budget 2026' enthalten, und fasse die beiden aktuellsten zusammen."

**Sicherheitshinweis zu MCPs:**

Ein MCP, den Sie installieren, kann alles tun, wofür seine Tools gebaut sind. Das ist im Alltag ein Vorteil (mehr Möglichkeiten!), im Sicherheitskontext aber ein Risiko. Installieren Sie nur MCPs von Quellen, denen Sie vertrauen — offizielle Anthropic-Connectors oder etablierte Open-Source-Projekte. Ein MCP von einer unbekannten Website einzubinden, entspricht dem Installieren einer Browser-Extension: Sie vertrauen dem Anbieter Ihren Zugang an.

---

## Ebene 3: Plugins — Pakete, die alles mitbringen

Ein **Plugin** ist im Cowork-Kontext ein vorgefertigtes Paket, das **mehrere Skills, MCPs und Commands** zusammen ausliefert. Statt Dinge einzeln zu installieren, installieren Sie ein Plugin, und Cowork bekommt auf einen Schlag alles, was für eine bestimmte Arbeit nötig ist.

**Ein Beispiel:**

Stellen Sie sich vor, Sie sind Content-Marketer. Sie brauchen regelmäßig:

- Einen Skill, der LinkedIn-Posts im Stil Ihrer Marke schreibt.
- Einen Skill, der passende Bilder generiert.
- Eine MCP-Verbindung zu Ihrer Asset-Bibliothek in Google Drive.
- Einen Slash-Command `/post`, der den ganzen Workflow startet.

Statt diese vier Dinge einzeln zu suchen und einzurichten, installieren Sie ein **Content-Marketing-Plugin**, das alles mitbringt — und Sie sind in drei Klicks einsatzbereit.

**Marketplaces:**

Plugins werden in **Marketplaces** gelistet, ähnlich wie Apps im App Store. Im Frühjahr 2026 gibt es mehrere:

- Die **offizielle Anthropic-Marketplace**, erreichbar über die Claude-Website und die Desktop-App.
- Die **Cowork-Plugin-Marketplace**, die spezifisch auf Cowork-Anwendungen zugeschnitten ist.
- **Private oder Team-interne Marketplaces**, die Unternehmen für ihre Mitarbeiter bereitstellen können.

In der Desktop-App finden Sie die Marketplaces unter **Einstellungen → Plugins → Marketplace** oder über den Befehl „Plugin installieren" im Chat.

**Ein Plugin installieren — Schritt für Schritt:**

1. Öffnen Sie **Einstellungen → Plugins**.
2. Wählen Sie die Marketplace (z. B. „Anthropic Marketplace").
3. Durchsuchen Sie die Kategorien oder suchen Sie gezielt nach einem Namen.
4. Klicken Sie auf ein Plugin, um die Details zu sehen: welche Skills und MCPs enthalten sind, wer es veröffentlicht hat, wie viele Bewertungen es hat.
5. Klicken Sie auf **Installieren**. Cowork lädt das Plugin herunter, aktiviert die enthaltenen Skills und MCPs und fragt bei Bedarf nach weiteren Berechtigungen (z. B. für neue Connectors).
6. Probieren Sie das Plugin direkt aus — im Chat oder über den mitgelieferten Slash-Command.

**Plugin-Commands:**

Viele Plugins bringen eigene Slash-Commands mit. Sie erscheinen, wenn Sie im Chat `/` tippen, und Sie können sie wie Tastatur-Kürzel nutzen. Beispiele:

- `/post` — startet den Content-Marketing-Workflow
- `/commit` — erzeugt eine konsistente Commit-Nachricht für ein Code-Projekt
- `/weekly` — baut einen wöchentlichen Status-Report aus Asana und Gmail

Welche Commands ein Plugin mitbringt, steht in seiner Beschreibung.

---

## Das Zusammenspiel auf einen Blick

| Ebene | Was ist es? | Typische Beispiele | Installation |
|-------|-------------|---------------------|--------------|
| **Skill** | Markdown-Anleitung für eine Aufgabe | `docx`, `xlsx`, `pptx`, `pdf` | Oft schon enthalten; eigene in `skills/`-Ordner |
| **MCP** | Protokoll-Server für einen externen Dienst | Slack, Google Drive, Gmail, GitHub | Einmalige OAuth-Verbindung |
| **Plugin** | Bündel aus Skills, MCPs und Commands | Content-Marketing-Paket, Team-Onboarding | Ein Klick in der Marketplace |

**Die wichtigste Intuition:**

- **Skills** sagen Claude, **wie** etwas gemacht wird.
- **MCPs** sagen Claude, **wo** etwas gemacht wird.
- **Plugins** sagen Claude, **was** für eine bestimmte Rolle alles zusammengehört.

---

## Empfehlungen für den Start

Wenn Sie Cowork frisch eingerichtet haben, lohnen sich aus unserer Erfahrung diese ersten Schritte:

1. **Keine neuen Skills installieren** — die mitgelieferten reichen für die ersten Wochen komplett aus. Lernen Sie sie erst einmal kennen.
2. **Einen MCP verbinden, den Sie ohnehin täglich nutzen.** Für die meisten ist das Google Drive oder Gmail. Die Hürde ist minimal, der Nutzen sofort spürbar.
3. **Ein Plugin für Ihre Hauptaufgabe installieren.** Wenn Sie Content erstellen, ein Content-Plugin. Wenn Sie in einem Dev-Team arbeiten, ein Coding-Plugin. Wenn Sie Projekte managen, ein PM-Plugin. Gehen Sie die Marketplace durch und suchen Sie etwas, das Ihre Rolle spiegelt.
4. **Nicht zu viel auf einmal.** Cowork wird unübersichtlich, wenn Sie zehn Plugins gleichzeitig installieren. Zwei bis drei sind für die meisten Menschen genug.

---

## Wieder entfernen und aufräumen

Alles, was Sie installieren, können Sie auch wieder entfernen:

- **Skills deaktivieren:** in **Einstellungen → Skills**. Der Skill bleibt lokal vorhanden, wird aber nicht mehr angewendet.
- **MCPs trennen:** in **Einstellungen → Connectors** auf **Verbindung trennen** klicken. OAuth-Token werden widerrufen.
- **Plugins deinstallieren:** in **Einstellungen → Plugins** auf **Deinstallieren**. Alle zugehörigen Skills, MCPs und Commands werden entfernt.

Bei MCPs, die Sie mit externen Diensten verbunden haben, lohnt es sich zusätzlich, **auch beim Anbieter** die Berechtigung zu widerrufen (z. B. unter „Angemeldete Apps" bei Google oder Slack). So stellen Sie sicher, dass wirklich keine Token übrig bleiben.

---

## Stärken und Schwächen auf einen Blick

**Stärken:**

- Skills machen Claude in Alltags-Aufgaben (Office, PDFs, Präsentationen) deutlich zuverlässiger.
- MCPs eröffnen den Zugriff auf alle Dienste, die Sie ohnehin nutzen.
- Plugins bringen ganze Workflows in einem Klick.
- Offener Standard — die gleichen MCPs funktionieren auch in Claude Code und zunehmend in anderen Tools.

**Schwächen:**

- Qualität der MCPs und Plugins schwankt — Marketplace-Einträge prüfen, nicht blind installieren.
- Jedes zusätzliche Plugin erhöht die Angriffsfläche für fehlerhafte oder bösartige Tools.
- Verbindungen zu externen Diensten erzeugen neue Datenschutz-Fragen (wer darf was sehen?).
- Skills und Plugins brauchen eine gewisse Pflege — bei API-Änderungen muss nachgebessert werden.

---

## Zusammenfassung in 60 Sekunden

Cowork gewinnt seine Stärke aus drei Werkzeug-Ebenen. **Skills** sind kurze Markdown-Anleitungen, die Claude für wiederkehrende Aufgaben wie Word, Excel, PDF oder Präsentationen befolgt — die wichtigsten sind schon mitgeliefert. **MCPs** sind Verbindungen zu externen Diensten (Slack, Google Drive, Gmail, GitHub, Notion …), die über einen offenen Standard laufen und meist mit einem OAuth-Klick eingerichtet sind. **Plugins** sind Pakete, die Skills, MCPs und Slash-Commands für eine bestimmte Rolle oder Aufgabe bündeln und über Marketplaces verteilt werden. Für den Start empfiehlt sich: bei den mitgelieferten Skills bleiben, einen MCP für den Hauptdienst Ihres Alltags verbinden, und ein Plugin aus der Anthropic-Marketplace installieren, das zu Ihrer Rolle passt. Alles lässt sich jederzeit wieder entfernen.

---

## Nächste Schritte

- **[04 Claude Code im Terminal](./04%20Claude%20Code%20im%20Terminal.md)** — der zweite Haupt-Zugang, speziell für Menschen, die mit Code arbeiten (oder damit anfangen wollen).
- Wenn Sie Cowork erst einmal in der Praxis sehen möchten, springen Sie zu **[06 Praktische Beispiele](./06%20Praktische%20Beispiele.md)**.
- Querverweis: **Kapitel 12 (KI-Agenten und Automatisierung)** vertieft eigene Skills, Plugin-Entwicklung und Agent-Architekturen.
