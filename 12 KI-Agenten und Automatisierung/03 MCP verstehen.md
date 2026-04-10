# 03 MCP verstehen

**Die Universal-Schnittstelle, die Agenten ihre Werkzeuge gibt.**

---

## Warum dieses Tutorial?

Kapitel 10 hat MCP eingeführt — als eine von drei Werkzeug-Ebenen in Cowork, neben Skills und Plugins. Das reicht für den Einstieg: Sie wissen, dass MCP für **Model Context Protocol** steht, dass es ein Standard ist, über den Claude mit Diensten wie Slack, Google Drive oder GitHub redet, und dass ein MCP-Connector meist mit einem OAuth-Klick eingerichtet wird.

Dieses Tutorial geht zwei Ebenen tiefer. Nicht weil Sie plötzlich zum MCP-Experten werden müssten — sondern weil MCP das **Herzstück jedes Agenten in diesem Kapitel** ist. Wer verstehen will, warum ein Agent bestimmte Dinge kann und andere nicht, warum manche Konfigurationen sicher sind und andere gefährlich, muss MCP als das sehen, was es ist: die **einzige Möglichkeit**, wie ein Agent mit der Welt außerhalb seines Kontextfensters spricht.

**Was Sie nach diesem Tutorial wissen werden:**

- Wie MCP technisch funktioniert, ohne dass Sie Code lesen müssen.
- Was **Tools**, **Ressourcen** und **Prompts** in der MCP-Welt bedeuten.
- Welche MCP-Server Sie 2026 kennen sollten.
- Wie Sie einen MCP in Cowork und in Claude Code einrichten.
- Wie Sie beurteilen, ob ein fremder MCP vertrauenswürdig ist.
- Wann und wie Sie einen eigenen MCP-Server ins Leben rufen lassen (per Skill, nicht per eigenem Code).

---

## MCP in einem Satz

**MCP ist ein gemeinsamer Sprachstandard, damit jedes KI-Modell mit jedem externen Dienst reden kann, ohne dass jedes Modell pro Dienst einzeln programmiert werden muss.**

Vor MCP war die Welt zerklüftet: Anthropic musste Claude einzeln mit Slack, Gmail, GitHub, Notion und allem anderen verbinden. Jede Verbindung brauchte eigenen Code, eigene Wartung, eigene Updates. Wenn OpenAI dasselbe wollte, musste OpenAI die Arbeit noch einmal machen. Jeder Dienst, der von allen Modellen erreichbar sein wollte, brauchte ebenfalls Arbeit in alle Richtungen.

Mit MCP gibt es eine einzige Schnittstelle. Ein Dienst baut **einmal** einen MCP-Server. Jedes Modell, das MCP spricht (Claude, und inzwischen auch andere), kann ihn sofort nutzen. Die Illustration [`illustrations/12-03-mcp-architektur.png`](./illustrations/12-03-mcp-architektur.png) zeigt das Bild: Claude in der Mitte, die MCP-Server wie Sterne drumherum, jeder Stern ein Dienst.

---

## Die drei Dinge, die ein MCP-Server bereitstellt

Ein MCP-Server bietet Claude drei Arten von Inhalten an. Sie als Nutzer sehen meistens nur die erste, aber es ist gut, alle drei zu kennen.

### 1. Tools — die Aktionen

**Tools** sind Funktionen, die der Agent aufrufen kann. Jedes Tool hat einen Namen, eine Beschreibung und eine Liste von Parametern. Beispiele aus einem Google-Drive-MCP:

- `search_files(query, limit)` — findet Dateien im Drive, die zum Suchbegriff passen.
- `read_file(file_id)` — liest den Inhalt einer Datei.
- `create_document(folder_id, title, content)` — erstellt ein neues Google Doc.
- `share_file(file_id, email, role)` — teilt eine Datei mit einer anderen Person.

Der Agent liest die Tool-Beschreibungen, versteht, was sie tun, und entscheidet selbst, welches Tool im aktuellen Schritt nötig ist. Tools sind die **Muskeln** des Agenten.

### 2. Ressourcen — die lesbaren Inhalte

**Ressourcen** sind Inhalte, die der Server bereitstellt, ohne dass der Agent aktiv eine Aktion ausführt. Ein Filesystem-MCP kann zum Beispiel die Dateien im aktuellen Arbeitsordner als Ressourcen anbieten: Der Agent kann sie auflisten und einzeln laden, genauso wie er ein Buch aus einem Regal zieht.

Der Unterschied zu Tools ist subtil, aber wichtig: Eine Ressource ist **passiv lesbar**. Ein Tool ist eine **aktive Aktion**. Praktisch verschwimmen die Grenzen — ein `read_file`-Tool macht dasselbe wie eine Ressource, die gelesen wird. Für Ihren Alltag reicht die Intuition: „Tools tun etwas, Ressourcen liegen herum und warten darauf, gelesen zu werden."

### 3. Prompts — die vorgefertigten Aufträge

**Prompts** sind vorgefertigte Prompt-Vorlagen, die ein MCP-Server mitbringen kann. Ein Slack-MCP könnte zum Beispiel einen Prompt `daily_standup` anbieten, der den Agenten anweist, in einem bestimmten Channel zu schauen, die letzten 24 Stunden zusammenzufassen und an ein bestimmtes Format zu halten.

Prompts sind die am wenigsten genutzte der drei Kategorien, und Sie werden sie in den meisten Tools nicht prominent sehen. Kennen müssen Sie sie nicht — aber wenn Sie die Abkürzung „Slash-Command aus einem MCP" einmal hören, wissen Sie: Das ist ein MCP-Prompt.

---

## Local oder Remote — zwei Bauarten

MCP-Server können auf zwei Arten laufen, und der Unterschied ist wichtig:

**Lokale MCP-Server** laufen auf Ihrem Rechner. Sie starten sie, wenn Sie Claude starten; sie werden beendet, wenn Sie Claude schließen. Sie haben Zugriff auf Ihre lokalen Dateien und können lokale Programme aufrufen. Ein Beispiel: Der Filesystem-MCP, der Ihren Arbeitsordner bereitstellt, läuft lokal. Ein PostgreSQL-MCP, der eine Datenbank auf Ihrem Mac anspricht, läuft lokal.

**Remote MCP-Server** laufen als Web-Dienst bei einem Anbieter. Der offizielle Slack-Connector, Google Drive, GitHub — das sind Remote-MCPs. Sie verbinden sich einmal per OAuth (genau wie Sie sich bei Google anmelden), und danach läuft die Kommunikation zwischen Anthropic und dem Anbieter ab. Ihre Credentials bleiben beim Anbieter, Claude bekommt nur ein Token.

**Warum das wichtig ist:**

- Lokale MCPs haben Zugriff auf Ihren Rechner — Dateien, lokale Programme, alles, was der Prozess darf. Ein unsicherer lokaler MCP kann theoretisch Ihren ganzen Ordner lesen oder Schaden anrichten. Installieren Sie lokale MCPs **nur aus Quellen, denen Sie vertrauen**.
- Remote MCPs sind über OAuth begrenzt — Sie sehen beim Verbinden, welche Berechtigungen der Server anfordert („Zugriff auf Ihre Dateien", „Senden von Nachrichten in Ihrem Namen"), und Sie können sie beim Anbieter jederzeit widerrufen. Sie geben aber Daten an einen zusätzlichen Anbieter (typischerweise Anthropic selbst, für die offiziellen Connectors).
- Für DSGVO-Fragen ist das ein relevanter Unterschied: Lokal = Daten bleiben bei Ihnen, Remote = Daten gehen durch die Systeme des MCP-Anbieters.

Der Faustregel-Satz: **„Je sensibler die Daten, desto lieber lokal."**

---

## Die wichtigsten MCP-Server 2026

Die offizielle Landschaft hat sich seit der Einführung Ende 2024 enorm erweitert. Eine Auswahl der Server, die Sie 2026 vermutlich wirklich brauchen:

**Für den Büro-Alltag:**

- **Google Drive / Workspace** (remote, offiziell) — Dokumente, Sheets, Slides finden, lesen, erstellen.
- **Gmail** (remote, offiziell) — Mails lesen, schreiben, verschicken, Labels verwalten.
- **Google Calendar** (remote, offiziell) — Termine sehen, erstellen, verschieben.
- **Outlook / Microsoft 365** (remote, offiziell) — das Gegenstück für die Microsoft-Welt.
- **Notion** (remote, offiziell) — Seiten und Datenbanken lesen und schreiben.
- **Slack** (remote, offiziell) — Nachrichten lesen, schreiben, Threads durchsuchen.
- **Microsoft Teams** (remote, offiziell) — analog zu Slack.

**Für Projektmanagement:**

- **Asana**, **Linear**, **Jira** (remote, offiziell) — Tasks verwalten, Sprints planen.
- **GitHub**, **GitLab** (remote, offiziell) — Pull Requests, Issues, Code-Reviews.

**Für Recherche und Web-Zugriff:**

- **Firecrawl** (remote) — strukturiertes Scrapen ganzer Websites, Ergänzung zur normalen Web-Suche.
- **Apify** (remote) — breites Set an Scraping-Actors für viele Quellen.
- **Context7** (remote) — aktuelle Library-Dokumentation für Entwickler.

**Für lokale Datei- und Werkzeugarbeit:**

- **Filesystem** (lokal, Teil von Cowork) — Zugriff auf den gemounteten Arbeitsordner.
- **PDF Tools** (lokal, als Plugin verfügbar) — Formulare lesen, ausfüllen, PDFs manipulieren.

**Für Bildgenerierung aus dem Agenten heraus:**

- **Nano Banana** — Bildgenerierung. Der MCP-Server selbst läuft lokal als Brücke, die Bildgenerierung selbst geschieht jedoch remote über Google Gemini. Das heißt: Ihre Prompts verlassen den Rechner. Nicht mit „lokal" verwechseln. (Siehe Kapitel 04 für den Dienst und seine Einsatzgebiete.)
- **Excalidraw-Generator** — Skizzen im Whiteboard-Stil. Funktioniert wie Nano Banana: lokaler MCP-Server als Brücke, Generierung läuft bei Gemini remote. Wir haben diesen Server für die Illustrationen dieses Repos intensiv genutzt.

Die Unterscheidung ist wichtig, weil beide MCPs auf den ersten Blick wie reine Lokal-Tools aussehen, aber die eigentlichen Modelle anderswo laufen. Für DSGVO-Fragen und sensible Inhalte (z. B. Kundenbilder, personenbezogene Zeichnungen) behandeln Sie sie wie Remote-Dienste.

**Für Datenbanken und Infrastruktur:**

- **PostgreSQL**, **SQLite**, **MongoDB** (lokal) — direkter Datenbank-Zugriff.
- **Stripe**, **HubSpot**, **Salesforce** (remote) — CRM- und Payment-Systeme.

Eine ständig aktuelle Liste finden Sie unter https://docs.claude.com/mcp und im **Cowork Plugins & MCP Marketplace** innerhalb der App. Verlassen Sie sich nicht auf statische Listen — das Feld ändert sich schnell.

---

## Einen MCP in Cowork einrichten

Der einfachste Weg für Nicht-Entwickler:

1. Öffnen Sie die Claude Desktop App.
2. Gehen Sie auf **Einstellungen → Connectors** (oder **Integrationen**, je nach Version).
3. Klicken Sie auf **Connector hinzufügen**. Die Liste zeigt die offiziellen Remote-MCPs.
4. Wählen Sie den gewünschten Dienst, zum Beispiel **Gmail**.
5. Ein Browser-Fenster öffnet sich, Google fragt Sie nach Ihrem Konto und zeigt die angeforderten Berechtigungen an.
6. Lesen Sie die Berechtigungen sorgfältig. Die Grundregel: **So wenig wie möglich gewähren.** Wenn Sie nur Mails lesen wollen, klicken Sie Schreibrechte weg, falls das möglich ist.
7. Bestätigen, fertig. Der Connector taucht als „verbunden" in der App auf.
8. Testen: Schreiben Sie in Claude „Zeige mir die drei neuesten Mails aus meinem Gmail-Posteingang, die nicht als gelesen markiert sind." Wenn Claude die Mails holt, steht die Verbindung.

Für **lokale MCPs**, die nicht über den Connectors-Dialog angeboten werden, gibt es eine Konfigurationsdatei — in der Regel `claude_desktop_config.json` im Einstellungen-Ordner. Dort tragen Sie den Befehl ein, der den MCP-Server startet. Für den Alltag der meisten Nicht-Entwickler ist diese Route nicht nötig — die offiziellen Remote-Connectors und die mitgelieferten lokalen MCPs decken die meisten Bedürfnisse.

---

## Einen MCP in Claude Code einrichten

Im Terminal sind MCPs ebenfalls konfigurierbar. Der Grundbefehl ist:

```
claude mcp add <name> -- <command> [argumente]
```

Für Server, die über HTTP oder Server-Sent-Events laufen, gibt es die Varianten `claude mcp add --transport sse <name> <url>` und `claude mcp add --transport http <name> <url>`. Weitere Unterbefehle sind `claude mcp list` (Übersicht aller konfigurierten Server) und `claude mcp remove <name>` (Server wieder entfernen). Da sich die genauen Flag-Namen und Unterbefehle zwischen Claude-Code-Versionen ändern können, prüfen Sie im Zweifel mit `claude mcp --help` gegen Ihre installierte Version — die Ausgabe ist die verlässlichste Quelle.

Der Unterschied zu Cowork ist vor allem: In Claude Code sind MCP-Konfigurationen **pro Projekt** möglich, nicht nur global. Sie können also in Projekt A einen GitHub-MCP haben und in Projekt B einen PostgreSQL-MCP, ohne dass sich die beiden in die Quere kommen. Das passende Slash-Command im laufenden Claude-Code-Chat ist `/mcp` — es zeigt Ihnen, welche Server gerade aktiv sind und welchen Status sie haben.

---

## Wie Sie beurteilen, ob ein MCP vertrauenswürdig ist

Die schlechte Nachricht: Es gibt kein offizielles Gütesiegel. Die gute Nachricht: Mit ein paar Faustregeln kommen Sie weit.

**Grüne Signale:**

- Der Server ist **offiziell von Anthropic** oder vom jeweiligen Dienst (Slack, Google, GitHub) selbst herausgegeben.
- Der Server ist **Open Source** auf GitHub, hat viele Stars, aktive Maintainer und regelmäßige Commits.
- Der Server wird in einer **offiziellen Marketplace** gelistet, die eine Prüfung vornimmt (z. B. der Anthropic-Marketplace).
- Der Code ist **klein und lesbar** — ein MCP mit ein paar hundert Zeilen Python ist einfacher zu überprüfen als einer mit zehntausend.

**Rote Signale:**

- Der Server kommt von einer **unbekannten Website** ohne klare Autorenschaft.
- Der Server fordert **breite Berechtigungen**, die für seinen Zweck nicht nötig sind („Vollzugriff auf Ihr gesamtes Drive", obwohl er nur Kalender-Einträge erstellen soll).
- Es gibt **keine Dokumentation**, wie der Server mit Ihren Daten umgeht.
- Der Server ist **geschlossen** und nicht einsehbar, kommt aber aus einer nicht-etablierten Quelle.

Ein praktischer Tipp für Team-Einführungen: Wenn Ihre Organisation MCPs einsetzt, sollten Sie eine **Allow-List** pflegen — eine Liste der zugelassenen Server. Alles außerhalb dieser Liste ist tabu. Das ist altmodisch, aber wirksam.

---

## Einen eigenen MCP erstellen — via Skill, nicht via Code

Wenn Sie einen MCP für einen Dienst brauchen, für den es noch keinen fertigen gibt, haben Sie drei Optionen:

1. **Warten.** Die Landschaft wächst schnell — oft gibt es in ein paar Wochen einen Community-MCP.
2. **Einen Entwickler beauftragen.** Ein MCP-Server ist für einen Python- oder TypeScript-Entwickler eine Sache von einem bis drei Tagen, je nach API-Komplexität.
3. **Claude fragen.** Genau das ist der mitgelieferte `mcp-builder`-Skill (siehe Kapitel 10 Teil 03). Sie beschreiben den Dienst und die API, die Sie anbinden wollen, und Claude schreibt Ihnen einen einfachen MCP-Server als Python-Datei, inklusive Tests. Das Ergebnis ist nicht immer perfekt, aber es ist ein **brauchbarer Startpunkt**, mit dem Sie in vielen Fällen innerhalb einer Stunde einen funktionierenden lokalen MCP haben.

Ein typischer Prompt für den Skill:

```
Nutze den mcp-builder-Skill, um einen neuen MCP-Server zu erstellen, 
der die API von [DIENST] anspricht. Ich brauche Tools für:

1. [AKTION 1, z. B. "Liste aller Projekte abrufen"]
2. [AKTION 2, z. B. "Einen Eintrag zu einem Projekt hinzufügen"]
3. [AKTION 3, z. B. "Einen Eintrag löschen"]

Die API-Dokumentation findest du unter [LINK]. 
Authentifiziert wird über [API-Key / OAuth / etc.]. 
Der Server soll lokal laufen. 
Lege alles in den Ordner ~/mcp-server/[NAME] und 
schreibe mir eine kurze README, wie ich ihn starte.
```

Der `mcp-builder`-Skill folgt einem getesteten Muster und sollte in den meisten Fällen einen laufenden Grundserver liefern. Wenn die API exotisch ist, müssen Sie nachbessern (oder einen Entwickler nachbessern lassen). Sie haben aber in jedem Fall eine **Ausgangslage**, die Sie ohne den Skill nicht hätten.

**Wichtig:** Ein selbst generierter MCP-Server, der auf externe APIs zugreift, ist ein kleines Stück Software, das Ihre Schlüssel hält. Behandeln Sie ihn entsprechend — keine Secrets im Code, Zugangsdaten in Umgebungsvariablen, und niemanden anderen auf das Verzeichnis schauen lassen.

---

## Praktische Muster für MCPs in Agenten

Ein paar Muster, die in Teil 05 und 06 wiederkehren und die es wert sind, sie einmal zu benennen:

**Lesen-Verdichten-Schreiben.** Der Agent liest aus MCP A (z. B. Gmail), verdichtet den Inhalt (im Modell), und schreibt das Ergebnis in MCP B (z. B. Notion oder einen lokalen Ordner). Das ist das häufigste Muster für E-Mail-Triage, Meeting-Notizen und Recherche-Zusammenfassungen.

**Suchen-Prüfen-Melden.** Der Agent sucht in einer Quelle (z. B. einem Google Drive oder einer Datenbank) nach einem Zustand, prüft ihn gegen ein Kriterium und meldet das Ergebnis in einem Kommunikationskanal (Slack, E-Mail). Klassisch für Monitoring-Jobs.

**Transform-Persist.** Der Agent liest Rohdaten aus einer lokalen Datei, transformiert sie mit Hilfe eines Skills (meist xlsx oder docx) und speichert das Ergebnis zurück. Das ist das Muster aus Kapitel 11, diesmal nur **in einem Lauf ohne manuelle Zwischenschritte**.

Alle drei Muster haben gemeinsam: Sie bestehen aus klaren **Stationen**, die Sie vorher benennen können. Das macht sie gut debugg-bar und gut beaufsichtigbar. Komplexere Muster (mehrstufige Verzweigungen, bedingte Schleifen) sind möglich, aber sie machen den Agenten schwerer zu verstehen. Anfangen sollten Sie mit einfachen Mustern.

---

## Stärken und Schwächen von MCPs auf einen Blick

**Stärken:**

- Ein einmal eingerichteter MCP funktioniert sowohl in Cowork als auch in Claude Code (und zunehmend in anderen Tools).
- Offener Standard, breite Unterstützung, schnell wachsende Landschaft.
- Offizielle Remote-Connectors sind mit OAuth abgesichert und vom Anbieter gewartet.
- Lokale MCPs halten sensible Daten bei Ihnen.

**Schwächen:**

- Qualität schwankt stark zwischen offiziellen und Community-MCPs.
- Lokale MCPs aus unbekannten Quellen sind ein realer Sicherheitsrisiko — vorsichtig prüfen.
- Remote-MCPs senden Daten durch Systeme von Drittanbietern.
- Debugging ist schwer, wenn ein MCP unerwartetes Verhalten zeigt — der Agent gibt manchmal wenig Hinweise, warum ein Tool-Aufruf schief ging.
- Die Liste der verfügbaren MCPs ändert sich schneller als Tutorials aktualisiert werden.

---

## Kernbotschaft

**MCP** ist der offene Standard, über den Claude mit externen Diensten redet. Ein MCP-Server stellt **Tools** (Aktionen), **Ressourcen** (lesbare Inhalte) und **Prompts** (Vorlagen) bereit. Server laufen **lokal** (Filesystem, PDF, DB) oder **remote** (Gmail, Slack, Drive über OAuth). Vertrauen Sie offiziellen und etablierten Open-Source-Servern, seien Sie vorsichtig bei unbekannten Quellen und zu breiten Berechtigungen. Drei wiederkehrende Muster decken 80 Prozent der Anwendungsfälle ab: **Lesen–Verdichten–Schreiben**, **Suchen–Prüfen–Melden**, **Transform–Persist**.

---

## Nächste Schritte

- **[04 Claude Code Subagents und Hooks](./04%20Claude%20Code%20Subagents%20und%20Hooks.md)** — wie Sie innerhalb von Claude Code spezialisierte Helfer bauen und automatische Auslöser setzen.
- Zurück zur Übersicht: **[README](./README.md)**.
- Querverweis: **Kapitel 10 Teil 03 (Cowork Skills, MCPs und Plugins)** ist die kürzere Einführung zum gleichen Thema, ohne die Agent-Brille.
