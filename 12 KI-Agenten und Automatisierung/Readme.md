# 12 KI-Agenten und Automatisierung

Dieses Kapitel zeigt Ihnen, wie aus einem Chatfenster ein arbeitender Kollege wird. Ein **KI-Agent** ist mehr als ein Sprachmodell, das antwortet: Er plant eine Aufgabe, wählt selbst Werkzeuge aus, führt sie aus, prüft das Ergebnis und entscheidet, was als Nächstes dran ist — bis die Aufgabe erledigt ist. Das klingt nach Science-Fiction, ist es 2026 aber nicht mehr. Die Bausteine stehen bereit, und wenn Sie bis Kapitel 11 mitgekommen sind, haben Sie einen Großteil davon schon benutzt, ohne es zu wissen.

Wir konzentrieren uns in diesem Kapitel bewusst auf das **Claude-eigene Ökosystem**: **MCP-Server** als universelle Schnittstelle zu allem, was draußen ist, **Subagents** in Claude Code als spezialisierte Helfer, **Hooks** als automatische Auslöser und **Slash-Commands** als wiederverwendbare Workflows. Werkzeuge wie n8n, Make, Zapier oder OpenAI-GPT-Actions werden kurz eingeordnet, stehen aber nicht im Mittelpunkt — der Grund: Die Claude-eigene Welt ist inzwischen so gut, dass sie für die meisten Aufgaben ausreicht, und das Ganze bleibt dabei näher am eigenen Rechner und an Ihren Dateien. Wer später in die Welt der visuellen Workflow-Tools einsteigen möchte, findet am Ende dieses Kapitels Hinweise.

Das Kapitel ist **für Nicht-Entwicklerinnen und Nicht-Entwickler** geschrieben. Es enthält Code-Beispiele — aber nur als Anschauung, nicht als Lernziel. Sie werden keinen Python-Code schreiben müssen, um dieses Kapitel zu verstehen oder die vorgestellten Automatisierungen zu bauen. Alles, was wir hier machen, funktioniert über natürliche Sprache, Markdown-Dateien und ein paar gut verständliche Konfigurations-Snippets.

Dieses Kapitel baut direkt auf Kapitel 10 (Claude-Infrastruktur), Kapitel 11 (KI und Daten) und Kapitel 14 (Ethik, Sicherheit und Verantwortung) auf. Ohne die dort gelegten Grundlagen hängt das Thema Agenten in der Luft; mit ihnen wird es ein logischer nächster Schritt.

## Struktur

| Datei | Inhalt |
|-------|--------|
| [01 Was ist ein KI-Agent](./01%20Was%20ist%20ein%20KI-Agent.md) | Begriffsklärung, Abgrenzung Chatbot vs. Agent, Anatomie eines Agenten |
| [02 Die Agent-Landschaft 2026](./02%20Die%20Agent-Landschaft%202026.md) | Claude-nativer Fokus, kurze Einordnung von n8n, Make, GPT Actions |
| [03 MCP verstehen](./03%20MCP%20verstehen.md) | Das Protokoll im Detail, wichtige Server, Installation, Sicherheit |
| [04 Claude Code Subagents und Hooks](./04%20Claude%20Code%20Subagents%20und%20Hooks.md) | Eigene Subagents bauen, Hooks als Auslöser, Slash-Commands als Workflow |
| [04b Ihr erster Mini-Agent in 15 Minuten](./04b%20Ihr%20erster%20Mini-Agent%20in%2015%20Minuten.md) | Niedrigschwelliger Cowork-only-Einstieg ohne Terminal, Subagents oder Slash-Commands |
| [05 Praxis E-Mail-Triage und Meeting-Notes](./05%20Praxis%20E-Mail-Triage%20und%20Meeting-Notes.md) | Zwei Use-Cases Schritt für Schritt, mit fertigen Subagent-Vorlagen |
| [06 Praxis Recherche-Pipeline und Datenanalyse](./06%20Praxis%20Recherche-Pipeline%20und%20Datenanalyse.md) | Mehrstufige Web-Recherche, wiederkehrende Monatsreports |
| [07 Praxisleitfaden Grenzen und Sicherheit](./07%20Praxisleitfaden%20Grenzen%20und%20Sicherheit.md) | Wann Automatisierung lohnt, Vertrauen und Guardrails, Kosten, Monitoring |
| [08 Glossar](./08%20Glossar.md) | Nachschlagewerk zu den wichtigsten Begriffen des Kapitels |

## Illustrationen

Alle Illustrationen liegen im konsistenten Whiteboard-Stil (wie Kapitel 09, 10, 11, 14) unter [`illustrations/`](./illustrations/):

- `12-01-chatbot-vs-agent.png` — Der fundamentale Unterschied auf einen Blick
- `12-02-agent-anatomie.png` — Die vier Bausteine eines Agenten: Planner, Tools, Memory, Loop
- `12-03-mcp-architektur.png` — Claude in der Mitte, MCP-Server wie Sterne drumherum
- `12-04-subagent-hierarchie.png` — Haupt-Agent delegiert an spezialisierte Helfer
- `12-05-email-triage-pipeline.png` — Fünfstufige E-Mail-Triage als Linear Flow
- `12-06-mein-erster-agent.png` — Annotierte Cowork-Sitzung des Mini-Agenten aus Teil 04b

## Empfohlene Lesereihenfolge

**Wenn Sie wenig Zeit haben:** 01 (Begriffe) → 02 (Landkarte) → 07 (Leitfaden). Damit wissen Sie, worum es geht, kennen die wichtigsten Werkzeuge und die Fallstricke. Praxis können Sie später nachholen.

**Wenn Sie konkret automatisieren wollen:** 01 → 03 (MCP) → 04 (Subagents/Hooks) → einer der beiden Praxis-Teile (05 oder 06, je nach Use-Case) → 07. Das ist der Hauptpfad für alle, die etwas Lauffähiges bauen wollen.

**Wenn Sie bisher nur ChatGPT oder Cowork kennen und noch nie ein Terminal offen hatten:** 01 → 02 → 03 → **04b** (Mini-Agent in 15 Minuten, komplett in Cowork) → 07. Der Zwischen-Teil 04b ist bewusst niedrigschwellig: ein erster, lauffähiger Agent ohne Claude Code, ohne YAML, ohne Slash-Commands. Wenn der läuft, trauen Sie sich anschließend an Teil 04.

**Wenn Sie Kapitel 11 frisch durchgearbeitet haben:** 01 → 06 (Datenanalyse-Automation) → 04 (Subagents). Hier schließen Sie direkt an Ihre wiederkehrenden Reports an.

**Wenn Sie Führungskraft sind und das Thema einordnen wollen:** 01 → 02 → 07. Die drei Teile geben Ihnen das Vokabular, die Werkzeug-Landschaft und die Risiken, ohne dass Sie selbst etwas bauen.

## Reifegrad-Selbsttest — wo stehen Sie gerade?

Beantworten Sie die folgenden fünf Fragen ehrlich, bevor Sie in das Kapitel einsteigen. Die Antworten zeigen, welcher Lesepfad für Sie am sinnvollsten ist — und was Sie sich vorher kurz anschauen sollten.

1. **Haben Sie Claude schon einmal mit einer Datei auf Ihrem Rechner arbeiten lassen?** (Cowork oder Claude Code)
2. **Haben Sie schon einmal einen MCP-Connector verbunden?** (Gmail, Drive, Slack, GitHub o. ä.)
3. **Haben Sie schon einmal ein Terminal geöffnet und ein Kommando ausgeführt?** (egal welches Betriebssystem, egal welches Kommando)
4. **Haben Sie schon einmal eine `CLAUDE.md` oder eine Markdown-Datei als Anweisung für Claude gepflegt?**
5. **Haben Sie schon einmal einen Subagent, Hook oder Slash-Command angelegt?**

**Auswertung:**

- **0–1 Ja:** Sie sind am Anfang. Starten Sie mit **Kapitel 10 Teil 02 (Cowork)** zur Auffrischung, dann lesen Sie in diesem Kapitel **Teil 01 → Teil 02 → Teil 03 → Teil 04b (Mini-Agent in Cowork) → Teil 07**. Lassen Sie Teil 04 (Subagents, Hooks, Slash-Commands in Claude Code) und Teile 05 und 06 zunächst außen vor — zurück kommen Sie, wenn 04b läuft.
- **2–3 Ja:** Sie haben den Einstieg. Lesen Sie **Teil 01 → Teil 02 → Teil 03 → Teil 04 → einer der beiden Praxis-Teile (05 oder 06) → Teil 07**. Teil 04b können Sie überspringen, wenn Sie ohne Umweg in Claude Code einsteigen wollen; wenn Sie Claude Code nicht mögen, ist 04b Ihr Hauptpfad und Teil 04 wird zur optionalen Vertiefung.
- **4–5 Ja:** Sie sind warm. Lesen Sie **Teil 01 (kurz) → Teil 04 (Vertiefung) → beide Praxis-Teile (05 und 06) → Teil 07**. Nehmen Sie aus Teil 02 und 03 nur das mit, was Sie noch nicht wussten. Das Glossar (Teil 08) brauchen Sie vermutlich nicht; das Troubleshooting am Ende von Teil 04 und 05 schon eher.

Der Selbsttest ist bewusst einfach. Er ersetzt kein echtes Urteil, aber er verhindert den häufigsten Fehler: Leute mit viel Vorerfahrung lesen Kapitel linear und langweilen sich; Leute ohne Vorerfahrung springen mitten hinein und geben nach zwanzig Minuten frustriert auf. Beides ist vermeidbar.

---

## Querverweise zu anderen Kapiteln

- **Kapitel 00 (Grundlagen LLMs)** — Wie ein Sprachmodell „denkt". Hilft zu verstehen, warum ein Agent im Kern auch nur ein Sprachmodell in einer Schleife ist (Teil 01).
- **Kapitel 01 (Prompt Engineering Text)** — Die Sechs-Bausteine-Struktur ist die Grundlage jeder Subagent-Beschreibung. Wer hier sicher ist, baut bessere Agenten.
- **Kapitel 03 (GPTs und Projekte)** — Die Persona-Logik aus Kapitel 03 ist die konzeptionelle Schwester der Subagents. Wer dort zu Hause ist, versteht Teil 04 schneller.
- **Kapitel 08 (Prompt Bibliothek)** — Viele Templates dort lassen sich direkt in Subagent-Anweisungen einbauen.
- **Kapitel 10 (Claude-Infrastruktur)** — Cowork, Claude Code, MCPs, Skills, Plugins. Die **Grundlage** dieses Kapitels. Ohne Kapitel 10 fehlt Ihnen das Vokabular.
- **Kapitel 11 (KI und Daten)** — Die wiederkehrende Analyse aus Teil 06 dieses Kapitels baut direkt auf den Daten-Workflows aus Kapitel 11 auf.
- **Kapitel 14 (Ethik, Sicherheit und Verantwortung)** — Agenten entscheiden selbst. Das macht sie leistungsfähig und riskant zugleich. Teil 07 knüpft an die Guardrails und Daten-Ampel aus Kapitel 14 an.

## Stand der Fakten

Dieses Kapitel bezieht sich auf **Stand April 2026**. Das Tempo im Agenten-Bereich ist hoch — speziell die Claude-Code-Features `/agents`, Hooks und Subagents verändern sich in jeder größeren Release schrittweise. Die **Prinzipien** in diesem Kapitel (Was ist ein Agent, wie plant er, welche Bausteine braucht er, welche Risiken gibt es) bleiben stabil. Die **konkreten Befehle** und **Dateipfade** prüfen Sie im Zweifel gegen die Claude-Code-Dokumentation unter https://docs.claude.com/claude-code.

Aktuelle Modellbezeichnungen zum Zeitpunkt des Schreibens: Claude Opus 4.6, Claude Sonnet 4.6, Claude Haiku 4.5. Für Agenten-Aufgaben empfehlen wir in diesem Kapitel meist Sonnet 4.6 als Standard (schnell, gründlich, kostengünstig), Opus 4.6 für komplexe Planung und mehrstufige Recherche, und Haiku 4.5 für Subagents mit engem, klarem Aufgabenprofil (z. B. Klassifikation).

## Ein Wort zu Verantwortung

Ein Agent handelt in Ihrem Namen. Wenn Sie ihm Schreibzugriff auf Ihre E-Mails, Ihre Dateien oder Ihren Kalender geben, dann tut er das auch — inklusive möglicher Fehler. Das ist kein Argument gegen Agenten, aber ein Argument für Sorgfalt bei der Einrichtung. Teil 07 ist deshalb kein optionaler Nachklapp, sondern ein Pflichtteil. Lesen Sie ihn, bevor Sie einen Agenten das erste Mal ohne Aufsicht laufen lassen.

