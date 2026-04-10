# 08 Glossar

**Die wichtigsten Begriffe dieses Kapitels in zwei bis vier Sätzen.**

---

Dieses Glossar ist als Nachschlagewerk gedacht. Jeder Eintrag soll alleine stehen können — Sie müssen nicht erst einen anderen Eintrag lesen, um ihn zu verstehen. Wenn ein Begriff in mehreren Teilen dieses Kapitels auftaucht und Sie nach dem zweiten oder dritten Mal noch unsicher sind, schlagen Sie hier nach.

---

**Agent.** Ein Sprachmodell, das eine Aufgabe nicht in einer einzigen Antwort erledigt, sondern sie selbst plant, ein Werkzeug auswählt, das Ergebnis prüft und entscheidet, was als Nächstes zu tun ist — und das so oft wiederholt, bis die Aufgabe fertig ist. Die vier Bausteine eines Agenten sind **Planner**, **Tools**, **Memory** und **Loop** (siehe Teil 01).

**CLAUDE.md.** Eine Markdown-Datei, die Claude Code oder Cowork beim Start automatisch liest. Sie dient als permanentes Briefing: Stil, Präferenzen, Projekt-Spezifika, Regeln, die für alle Läufe in diesem Projekt gelten sollen. Es gibt sie in zwei Varianten: global unter `~/.claude/CLAUDE.md` und projektweit als `CLAUDE.md` im Projektordner. Die projektweite Datei überschreibt und ergänzt die globale.

**Claude Code.** Ein Kommandozeilen-Werkzeug, das Claude direkt im Terminal verfügbar macht. Es kennt Ihre Projektdateien, kann Shell-Befehle ausführen, hat Subagents, Hooks und Slash-Commands. Nicht zu verwechseln mit **Cowork**, das denselben Claude-Kern über eine Desktop-App mit visuellem Workspace anbietet — ohne Terminal.

**Connector.** Im Cowork-Kontext ein Oberbegriff für alles, was Cowork mit einem externen Dienst verbindet — meist ein MCP-Server, der über die Cowork-Oberfläche konfiguriert wurde. Connectors gibt es als **lokale** (laufen auf Ihrem Rechner) und als **Remote-Connectors** (laufen in der Cloud eines Anbieters und erreichen Claude per OAuth).

**Cowork.** Die Claude-Desktop-App in der Betriebsart für Nicht-Entwickler. Sie erlaubt Datei-Zugriff auf einen gewählten Arbeitsordner, installierbare MCP-Connectors, Skills und Plugins — alles über eine grafische Oberfläche statt ein Terminal. Cowork und Claude Code nutzen denselben Claude-Kern; die Unterschiede liegen in Bedienung und Zielgruppe.

**Hook.** Ein automatischer Auslöser in Claude Code. Ein Hook bindet einen Shell-Befehl an ein Ereignis — typisch „nach jedem Edit", „vor jedem Tool-Aufruf" oder „wenn der Lauf beendet ist". Hooks sind das, was Agenten-Ausgaben mit Ihrem bestehenden System verknüpft: Formatierer anstoßen, Benachrichtigung schicken, Ergebnis in ein Log schreiben. Hooks brauchen JSON-Konfiguration, lassen sich aber per Prompt in Claude Code erzeugen (siehe Teil 04).

**Loop.** Der Mechanismus, der einen Agenten zum Agenten macht: „Was ist der nächste Schritt? — Tool auswählen — ausführen — Ergebnis bewerten — fertig? Wenn nein, zurück zum Anfang." Der Loop läuft so lange, bis der Planner „fertig" sagt oder eine Sicherung greift. Ohne Loop ist ein Sprachmodell nur ein assistierender Chatbot.

**MCP (Model Context Protocol).** Ein offener Standard, mit dem Sprachmodelle auf externe Werkzeuge und Daten zugreifen. Ein **MCP-Server** bietet ein oder mehrere Tools an (z. B. „lies Google Drive", „sende Slack-Nachricht", „erstelle PDF"); ein **MCP-Client** wie Claude Code oder Cowork ruft sie auf. Der Vorteil: Derselbe MCP-Server funktioniert in Claude, Cursor, Windsurf und vielen weiteren Clients, ohne dass Sie ihn jedes Mal neu bauen müssen (siehe Teil 03).

**Memory.** Das Gedächtnis eines Agenten in drei Schichten. **Kurzfristig** ist der aktuelle Session-Kontext (endet mit dem Schließen der Sitzung). **Mittelfristig** sind Dateien, die der Agent während eines Laufs anlegt und später wieder liest — Notizen, Zwischenergebnisse. **Langfristig** gibt es derzeit nur in Ansätzen; in der Praxis pflegt der Nutzer Markdown-Dateien, die Claude jedes Mal frisch liest (z. B. `CLAUDE.md`).

**Mini-Agent.** In diesem Kapitel ein kleiner, einzelner Cowork-Prompt, der wie ein Agent funktioniert, ohne ein volles Claude-Code-Setup zu brauchen — genau das, was Teil 04b baut. Ein Mini-Agent hat alle vier Agenten-Bausteine (Planner, Tools, Memory, Loop), aber in minimaler Ausprägung, und läuft komplett in Cowork.

**OAuth.** Ein Anmelde-Verfahren, bei dem Sie sich nicht mit Passwort beim Zieldienst anmelden, sondern ein Token generieren, das nur der Anwendung (hier: Claude) bestimmte Rechte gibt. Remote-MCP-Connectors benutzen fast ausnahmslos OAuth. Vorteil: Sie können Rechte einzeln vergeben und jederzeit wieder entziehen, ohne ein Passwort ändern zu müssen.

**Persona.** Eine Rollen-Beschreibung für ein Sprachmodell: „Du bist eine erfahrene Datenanalystin, die knapp und faktenbasiert arbeitet." Personas steuern Stil und Fokus einer Antwort. In der ChatGPT-Welt sind sie oft als Custom GPT oder Custom Instructions verpackt, im Claude-Ökosystem als **Subagent**, als **Claude Project** oder als Anweisungsblock in `CLAUDE.md`.

**Plan-Mode.** Ein Modus in Claude Code, in dem Claude erst einen Plan vorschlägt und auf Ihre Bestätigung wartet, bevor er ausführt. Nützlich, wenn Sie einem neuen oder komplexen Workflow nicht vollständig trauen: Sie lesen den Plan, korrigieren, stimmen zu — erst dann passiert etwas am System.

**Planner.** Die Komponente eines Agenten, die entscheidet, was als Nächstes passiert. In fast allen Fällen **ist** der Planner einfach das zugrunde liegende Sprachmodell (Claude Opus, Sonnet oder Haiku). Die Qualität des Planners entscheidet, ob Ihr Agent die Aufgabe schafft oder sich verrennt. Für komplexe Planung lohnt sich Opus, für Routine Sonnet, für enge Klassifikations-Subagents Haiku.

**Skill.** Eine strukturierte, wiederverwendbare Anleitung für eine bestimmte Art von Aufgabe, als Markdown-Datei mit klaren Schritten, Beispielen und oft einem kleinen Hilfs-Skript. Claude lädt passende Skills automatisch, wenn die Aufgabe das Auslöse-Wort trifft. Es gibt eingebaute Skills (z. B. für Word-, Excel-, PDF-, PowerPoint-Dokumente) und selbstgemachte Skills im Benutzerordner. Skills sind keine Magie, sondern dokumentiertes Handwerk.

**Slash-Command.** Ein mit `/` beginnender Befehl in Claude Code, der einen vorgefertigten Prompt oder eine Aktion ausführt — z. B. `/review`, `/test`, `/release`. Slash-Commands sind Markdown-Dateien im Projektordner und deshalb vom Team versionierbar und teilbar. In Cowork werden sie teilweise durch **Skills** ersetzt (siehe Teil 04b).

**Subagent.** Ein spezialisierter Helfer-Agent in Claude Code, der eine Teilaufgabe übernimmt und seinen eigenen, kleinen Kontext bekommt. Ein typisches Setup: Ein Haupt-Agent delegiert „E-Mails klassifizieren" an einen `email-klassifikator`-Subagent mit Haiku und „Antwortentwurf schreiben" an einen `antwort-entwurf`-Subagent mit Sonnet. Subagents sind Markdown-Dateien mit **YAML-Frontmatter** (siehe dort).

**Tool.** Alles, was ein Agent aufrufen kann, um mit der Welt außerhalb des Sprachmodells zu interagieren: Datei-Zugriff, Shell-Befehl, MCP-Aufruf, Skill, Subagent, Web-Suche. Ohne Tools ist ein Sprachmodell nur ein Erklär-Bot. Mit Tools kann es etwas tun. Faustregel: So wenige Tools wie möglich, so viele wie nötig.

**Workspace (Cowork).** Der Arbeitsordner, den Sie in Cowork ausgewählt haben und auf den Claude Lese- und Schreibzugriff bekommt. Alles außerhalb des Workspace ist für Claude unsichtbar. Das ist die wichtigste Sicherheitsgrenze in Cowork: Wer den Workspace klein und aufgeräumt hält, reduziert das Risiko, dass Claude in etwas hineinschreibt, was er nicht sollte.

**YAML-Frontmatter.** Ein kleiner Konfigurations-Block am Anfang einer Markdown-Datei, eingerahmt von drei Bindestrichen (`---`). Er enthält strukturierte Angaben wie Name, Beschreibung, erlaubte Tools oder Modell-Wahl — typisch für Subagent-Dateien in Claude Code. YAML ist empfindlich gegenüber Einrückung; Claude Code kann solche Blöcke in der Regel für Sie erzeugen, wenn Sie ihm die Felder in natürlicher Sprache nennen.

---

## Kernbotschaft

Das Vokabular dieses Kapitels ist überschaubar: **Agent** ist ein Sprachmodell mit **Loop**, **Planner**, **Tools** und **Memory**. **MCP** ist der Stecker für Tools, **Subagents** sind spezialisierte Helfer, **Hooks** sind automatische Auslöser, **Slash-Commands** sind wiederverwendbare Prompts, **Skills** sind dokumentiertes Handwerk. Wenn Ihnen diese acht Begriffe geläufig sind, können Sie jedes Agenten-Framework in wenigen Minuten einordnen — inklusive solcher, die dieses Kapitel gar nicht behandelt.

---

## Nächste Schritte

- Zurück zum Anfang des Kapitels: **[README](./README.md)**.
- Wenn Sie beim Lesen auf einen Begriff stoßen, der hier nicht erklärt ist, melden Sie ihn gerne — das Glossar wächst mit den Fragen, die im Leserkreis entstehen.
