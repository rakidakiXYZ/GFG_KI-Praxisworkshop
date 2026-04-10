# 10 Claude-Infrastruktur: Cowork, Claude Code Desktop und VS Code

Dieses Kapitel bringt Sie von „Ich kenne nur den Browser" auf „Ich nutze Claude produktiv im Dateisystem und im Editor". Es zeigt die drei Haupt­zugänge zu Claude auf dem Desktop, wie sie sich unterscheiden, wie Sie sie installieren und wie Sie für jede Arbeitssituation den passenden Zugang wählen.

Dieses Kapitel setzt auf Kapitel 09 (KI-Tool-Landschaft 2026) auf. Wenn Sie dort noch nicht waren, empfehlen wir zumindest einen Blick in das Anthropic-Kapitel (`03 Anthropic - Claude und die Claude-Familie.md`), damit Sie die Begriffe kennen.

## Struktur

| Datei | Inhalt |
|-------|--------|
| [01 Die drei Zugaenge im Ueberblick](./01%20Die%20drei%20Zugaenge%20im%20Ueberblick.md) | Browser, Cowork, Claude Code — was ist der Unterschied? |
| [02 Cowork-Modus Grundlagen](./02%20Cowork-Modus%20Grundlagen.md) | Installation, Ordner-Mount, Privacy, erste Schritte |
| [03 Cowork Skills MCPs und Plugins](./03%20Cowork%20Skills%20MCPs%20und%20Plugins.md) | Skills entdecken, Connectors, Plugin-Marketplaces |
| [04 Claude Code im Terminal](./04%20Claude%20Code%20im%20Terminal.md) | Installation, Slash Commands, CLAUDE.md, Subagents, Hooks |
| [05 Claude Code in VS Code](./05%20Claude%20Code%20in%20VS%20Code.md) | Extension, Inline-Diffs, Sidebar-Chat, Selection-to-Claude |
| [06 Praktische Beispiele](./06%20Praktische%20Beispiele.md) | Fünf End-to-End-Workflows vom Non-Coder bis zum Power-User |
| [07 Troubleshooting Kosten und FAQ](./07%20Troubleshooting%20Kosten%20und%20FAQ.md) | Häufige Probleme, Abo-Übersicht April 2026, Datenschutz |

## Illustrationen

Alle Illustrationen liegen im konsistenten Excalidraw-/Whiteboard-Stil unter [`illustrations/`](./illustrations/):

- `10-01-drei-zugaenge.png` — Triptychon: Browser, Cowork, Claude Code nebeneinander
- `10-02-cowork-architecture.png` — Cowork mit Skills, MCPs, Plugins und Ordner-Mount
- `10-03-claude-code-flow.png` — Terminal-Flow: Frage → Diff → Approve → Commit
- `10-04-vscode-integration.png` — VS-Code-Layout mit Claude-Sidebar
- `10-05-entscheidungsbaum-zugang.png` — „Welcher Zugang für welche Aufgabe?"

## Empfohlene Lesereihenfolge

**Wenn Sie Non-Coder sind:** 01 → 02 → 03 → 06 → 07. Die Teile 04 und 05 sind optional und richten sich an Einsteiger im Coding.

**Wenn Sie Entwickler sind oder werden wollen:** Der Reihe nach, 01 bis 07. Teil 02 und 03 zeigen Ihnen auch, warum Cowork für Nicht-Code-Aufgaben die bessere Wahl ist.

**Wenn Sie in Eile sind:** 01 (Einstieg) → 07 (Entscheidungsbaum und Kosten) und dann gezielt den Teil Ihres Lieblings-Zugangs lesen.

## Querverweise zu anderen Kapiteln

- **Kapitel 00 (Grundlagen LLMs)** — Begriffe wie „Kontextfenster", „Token", „Tool Use", „MCP"
- **Kapitel 01 (Prompt Engineering Text)** — bessere Eingaben, die in allen drei Zugängen funktionieren
- **Kapitel 02 (Strukturierte Prompts)** — Markdown-Struktur, die in `CLAUDE.md` und Skill-Definitionen zentral ist
- **Kapitel 03 (GPTs und Projekte)** — die Persona-Idee aus Kapitel 03 lässt sich als Cowork-Skill oder Claude-Code-Subagent „auf den Desktop" holen
- **Kapitel 09 (KI-Tool-Landschaft 2026)** — Gesamteinordnung und Preisvergleich mit anderen Anbietern

## Für wen ist welcher Teil?

| Teil | Non-Coder | Coding-Einsteiger | Power-User |
|------|:---------:|:-----------------:|:----------:|
| 01 Überblick | ✅ | ✅ | ✅ |
| 02 Cowork Grundlagen | ✅ | ✅ | ✅ |
| 03 Cowork Skills/MCPs/Plugins | ✅ | ✅ | ✅ |
| 04 Claude Code Terminal | optional | ✅ | ✅ |
| 05 Claude Code in VS Code | optional | ✅ | ✅ |
| 06 Praktische Beispiele | ✅ | ✅ | ✅ |
| 07 Troubleshooting, Kosten, FAQ | ✅ | ✅ | ✅ |

## Stand

Alle Versions-, Preis- und Feature-Angaben beziehen sich auf **April 2026**. Der Markt bewegt sich schnell — überprüfen Sie vor einer Installation oder Kaufentscheidung bitte direkt auf https://claude.com sowie in der Anthropic-Dokumentation unter https://docs.claude.com.

