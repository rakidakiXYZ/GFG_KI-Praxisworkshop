# 04 Claude Code Subagents und Hooks

**Spezialisierte Helfer und automatische Auslöser — die Agent-Werkstatt in Claude Code.**

---

## Warum dieses Tutorial?

Wenn MCPs die **Werkzeuge** eines Agenten sind, dann sind Subagents seine **Kolleginnen und Kollegen**, und Hooks sind die **Routinen**, die automatisch greifen, ohne dass jemand etwas anstoßen muss. Alle drei zusammen verwandeln Claude Code von einem sehr guten Einzelarbeiter in einen kleinen, gut organisierten Betrieb.

Kapitel 10 Teil 04 hat Subagents, Hooks und den Plan-Mode kurz vorgestellt. Dieses Tutorial vertieft die beiden ersten Punkte und zeigt, wie Sie sie **konkret einsetzen**, ohne Python-Code zu schreiben. Am Ende wissen Sie, was ein Subagent ist, wie Sie einen erstellen, wie Sie ihn in Ihre Hauptarbeit einbinden, was Hooks sind, welche Sie sinnvoll einrichten können, und wie Subagents und Hooks zusammenspielen.

**Was Sie nach diesem Tutorial wissen werden:**

- Warum Subagents eine **andere** Lösung für Spezialaufgaben sind als Personas in GPTs oder Claude Projects.
- Wie Sie einen eigenen Subagent mit `/agents` in Claude Code anlegen — ohne Code.
- Was Hooks technisch sind und welche Ereignisse sie greifen lassen.
- Konkrete Beispielhooks: Pre-Tool, Post-Edit, Post-Answer.
- Wie Subagents und Hooks zusammen eine stabile Automatisierung ergeben.
- Was Slash-Commands sind und wann Sie sie bauen sollten.

---

## Was ist ein Subagent?

Ein **Subagent** ist ein kleiner, spezialisierter Claude, der in Claude Code lebt und für eine klar abgegrenzte Aufgabe zuständig ist. Sie können ihn sich wie einen Kollegen vorstellen, der ein enges Aufgabenprofil hat und sehr gut darin ist. Ein **Test-Runner**, der Tests ausführt und berichtet. Ein **Code-Reviewer**, der Pull Requests durchgeht. Ein **Dokumentations-Schreiber**, der zu jeder neuen Funktion die passende Markdown-Datei erzeugt.

Technisch ist ein Subagent eine **Markdown-Datei** mit einem YAML-Vorspann, die unter `.claude/agents/` im Projekt oder unter `~/.claude/agents/` global liegt. Der YAML-Vorspann legt fest, welche Tools der Subagent darf und welches Modell ihn antreibt. Der Markdown-Teil ist die **Systemprompt** — eine Anleitung in natürlicher Sprache, was der Subagent tut, wie er antwortet, welche Regeln er einhält.

Zwei Dinge an Subagents sind entscheidend, weil sie den Unterschied zu Personas ausmachen:

**Erstens: Jeder Subagent hat seinen eigenen Kontext.** Wenn der Hauptagent einen Subagent aufruft, bekommt der Subagent eine frische, saubere Unterhaltung. Das ist sehr nützlich, weil der Hauptagent seinen Kontext nicht mit Zwischenschritten überfüllen muss. Der Test-Runner berichtet „14 Tests grün, 2 rot, hier die Fehlermeldungen" — nicht „hier sind die 4.500 Zeilen Log-Output".

**Zweitens: Jeder Subagent darf nur die Tools, die Sie ihm erlauben.** Das ist kein Komfort-Feature, das ist ein **Sicherheits-Feature**. Ein „Read-only-Reviewer" darf nur lesen, nie schreiben. Ein „Test-Runner" darf Tests ausführen, aber keine Dateien ändern. Wenn der Hauptagent einen Subagent aufruft, kann dieser Subagent nur tun, was sein Profil erlaubt — egal, wie clever er im Kontext argumentiert.

Die Illustration [`illustrations/12-04-subagent-hierarchie.png`](./illustrations/12-04-subagent-hierarchie.png) zeigt die Struktur: ein Hauptagent in der Mitte, der an spezialisierte Subagents delegiert, jeder mit seinem eigenen kleinen Werkzeugkasten.

---

## Abgrenzung: Subagent vs. Persona vs. Skill

Das Feld ist voller ähnlich klingender Begriffe. Ein kurzer Vergleich:

- **Persona (Custom GPT, Claude Project)** — eine Systemprompt, die in der Chat-Oberfläche wiederverwendbar ist. Keine eigenen Tools, kein Subprozess. Gut für Rollen wie „mein Lerntutor" oder „meine Redakteurin". Kapitel 03 hat das Thema behandelt.
- **Skill** — eine strukturierte Anleitung für eine Aufgabe (Word bearbeiten, Excel befüllen, Präsentation erstellen). Wird bei passender Aufgabe automatisch aktiviert, bringt eigene Hilfsskripte mit. Kapitel 10 Teil 03 hat das eingeführt.
- **Subagent** — ein eigener kleiner Claude in Claude Code, mit eigener Tool-Auswahl, eigener Systemprompt und eigenem frischen Kontext bei jedem Aufruf.

Die drei schließen sich nicht aus. Sie können in einem Subagent einen Skill aufrufen lassen. Eine Persona und ein Subagent können die gleiche Systemprompt haben — der Unterschied ist, wo sie lebt und welche Tools sie darf.

**Faustregel:** Wenn Sie eine wiederverwendbare **Rolle** im Gespräch brauchen → Persona oder Claude Project. Wenn Sie eine **Spezialfähigkeit** für ein Dateiformat brauchen → Skill. Wenn Sie eine **eigenständige Teilaufgabe** in einem Agenten-Workflow brauchen → Subagent.

---

## Einen Subagent anlegen — der `/agents`-Weg

Der offizielle und einfachste Weg, einen Subagent zu erstellen, geht im laufenden Claude Code:

1. Starten Sie Claude Code in einem Projektordner mit `claude`.
2. Tippen Sie im Chat `/agents`. Ein interaktives Menü erscheint.
3. Wählen Sie **Create New Agent** (oder **Neuen Agent anlegen**, je nach Version).
4. Claude Code fragt Sie in einem kleinen Dialog:
   - **Name** des Agents (Kleinbuchstaben, Bindestriche, z. B. `test-runner`).
   - **Beschreibung**, wann der Agent ausgelöst werden soll. Sehr wichtig — je klarer, desto besser erkennt der Hauptagent, wann er den Subagent ruft.
   - **Tools**, die der Subagent nutzen darf. Ein enger Werkzeugkasten ist besser als ein breiter.
   - **Modell**. Sonnet 4.6 ist meist die richtige Wahl. Für sehr einfache Klassifikationsaufgaben reicht Haiku 4.5. Für komplexe Planer-Subagents kann sich Opus 4.6 lohnen.
5. Claude Code legt eine Datei unter `.claude/agents/<name>.md` an und öffnet sie, damit Sie die Systemprompt verfeinern können.

Die Datei sieht ungefähr so aus (ein echtes Beispiel für einen Dokumenten-Reviewer):

```markdown
---
name: doc-reviewer
description: Use this agent proactively after any change to Markdown files 
  in the docs/ directory. The agent reviews the changed file for clarity, 
  consistency with the existing tone, broken internal links, and typos.
tools: Read, Grep, Glob
model: sonnet
---

You are a meticulous documentation reviewer for this repository.

Your job is to check Markdown files for four things, in this exact order:

1. **Clarity** — is each section written in plain language? Any jargon 
   that is not explained on first use?
2. **Tone consistency** — compare against other files in the same folder. 
   The tone should be consistent. Flag deviations.
3. **Internal links** — run a quick glob over the repo to verify that all 
   Markdown links and image paths actually exist.
4. **Typos and grammar** — obvious errors in German.

Report in four short sections, one per check. If a section is clean, 
say so in one line. Do not suggest changes that are not defensible.

You have read-only tools. You cannot write to files. If you want to 
propose a change, quote the line and describe the proposed new wording 
in your report.
```

Beachten Sie drei Dinge:

- Der **Name** ist eindeutig, kein Leerzeichen, gut zu tippen.
- Die **Beschreibung** enthält das Wort „proactively" — das signalisiert dem Hauptagenten, dass er den Subagent **automatisch** rufen soll, wenn die Situation passt, nicht erst wenn Sie es ausdrücklich sagen.
- Die **Tool-Auswahl** ist eng: `Read`, `Grep`, `Glob`. Kein `Write`, kein `Edit`, kein `Bash`. Dadurch kann der Subagent gar keine Änderungen anrichten, selbst wenn er wollte.

Sie können den Subagent jederzeit bearbeiten, indem Sie die Datei in Ihrem Editor öffnen, oder mit `/agents` wieder in die Verwaltung gehen.

---

## Einen Subagent aufrufen

Im Normalfall rufen Sie Subagents **nicht** ausdrücklich auf. Der Hauptagent liest die Beschreibungen aller verfügbaren Subagents, und wenn Ihre Anfrage dazu passt, delegiert er automatisch. Beispiel:

> Sie: „Ich habe gerade `docs/12-ki-agenten.md` überarbeitet. Schau einmal drüber."

Der Hauptagent erkennt: Hier wurde eine Markdown-Datei in `docs/` geändert → der `doc-reviewer`-Subagent ist zuständig. Er ruft ihn auf, übergibt die Datei und bekommt den Report zurück. Sie sehen in der Ausgabe, dass ein Subagent aktiv war (meist mit einem kleinen Label wie `[doc-reviewer]`).

Wenn Sie es **ausdrücklich** wollen, können Sie auch formulieren „Nutze den doc-reviewer für …" — das funktioniert ebenfalls.

Wichtig für Ihr mentales Modell: Der Subagent bekommt **nur die Information, die der Hauptagent ihm weitergibt**. Er sieht nicht Ihre gesamte Unterhaltung. Wenn der Subagent unerwartet wenig Kontext hat, dann haben Sie dem Hauptagenten entweder zu wenig gesagt, oder die Beschreibung des Subagents hat ihn nicht klar genug erreicht. Beides lässt sich nachbessern.

---

## Die wichtigsten Subagents für den Alltag

Ein paar Subagents, die Sie in fast jedem größeren Projekt sinnvoll einsetzen können — und die wir in den Praxis-Teilen dieses Kapitels wiedersehen:

**`doc-reviewer`** — Liest Markdown-Dateien, prüft Klarheit, Konsistenz, tote Links, Tippfehler. Nur Lese-Tools. Beispiel oben.

**`mail-klassifizierer`** — Schaut sich eingehende Mails (oder einen Mail-Snapshot) an und kategorisiert sie nach einem festen Schema: „Kunde-dringend", „Kunde-Routine", „Intern", „Werbung", „Sonstiges". Nur Lese-Tools. Sehr nützlich für die E-Mail-Triage in Teil 05.

**`fact-checker`** — Bekommt eine Behauptung oder einen Absatz, sucht mit Web-Tools nach Belegen, prüft die Quellen und meldet Treffer oder Zweifel. Websuche-Tools plus Read. Zentraler Baustein für die Recherche-Pipeline in Teil 06.

**`zahlen-pruefer`** — Bekommt einen Bericht mit Kennzahlen und die Rohdatei, prüft jede Zahl stichprobenartig gegen die Quelldaten, meldet Abweichungen. Xlsx-Skill plus Read. Das Pendant zum Sanity-Check aus Kapitel 11 Teil 07, aber als Subagent.

**`datei-organisator`** — Bekommt einen Ordner, schlägt eine Ordnung vor (Struktur, Umbenennung), erklärt die Vorschläge, wartet auf Freigabe, setzt um. Hier darf der Subagent schreiben — mit bewusst gesetzter Freigabestelle.

Diese fünf sind keine Pflicht, aber ein guter Startkatalog. Sie bauen sie einmal, verfeinern sie über ein paar Wochen, und haben dann ein kleines Team, das Ihnen wirklich zuarbeitet.

---

## Hooks — Claude Code auf bestimmte Ereignisse reagieren lassen

**Hooks** sind Shell-Befehle, die Claude Code automatisch an bestimmten Stellen ausführt. Sie werden nicht als eigene Dateien abgelegt, sondern zentral in der Einstellungs-Datei **`.claude/settings.json`** (projektweit) oder **`~/.claude/settings.json`** (global) deklariert. Jeder Hook ist an ein **Ereignis** gebunden, und wenn das Ereignis eintritt, läuft der hinterlegte Befehl, bevor oder nachdem Claude seine normale Aktion ausführt.

Die wichtigsten Ereignisse in Claude Code 2026:

- **PreToolUse** — läuft, bevor Claude ein Tool aufruft. Sie können den Aufruf beobachten, loggen oder sogar blockieren.
- **PostToolUse** — läuft, nachdem ein Tool ausgeführt wurde. Ideal für Aufräumarbeiten, Formatierung oder Tests.
- **UserPromptSubmit** — läuft, wenn Sie einen Prompt absenden. Kann den Prompt anreichern (z. B. den aktuellen Git-Branch anhängen) oder ablehnen.
- **Notification** — läuft, wenn Claude eine Benachrichtigung zeigt. Gut für Desktop-Pop-ups, damit Sie nicht ständig aufs Terminal schauen müssen.
- **Stop** — läuft, wenn Claude die Antwort beendet. Gut für Statistik, Audio-Signale, Logs.
- **SubagentStop** — läuft, wenn ein Subagent fertig ist. Gut für detaillierte Protokollierung der Subagent-Arbeit.

Ein Hook wird in einer Konfigurationsdatei gespeichert, und zwar in `~/.claude/settings.json` (global, für alle Projekte) oder `.claude/settings.json` (nur für das aktuelle Projekt). Das ist eine JSON-Datei mit einer festen Struktur. Sie **müssen** sie nicht von Hand schreiben — und wir empfehlen das ausdrücklich nicht. Der bequeme Weg für Nicht-Entwickler ist folgender:

**Hook einrichten per Prompt (empfohlener Weg).**

1. Starten Sie Claude Code im Projektordner, in dem der Hook gelten soll.
2. Formulieren Sie die Anweisung natursprachlich, zum Beispiel: „Ich möchte einen PostToolUse-Hook einrichten, der nach jeder Datei-Änderung den Formatter `prettier --write` auf die geänderte Datei anwendet. Trage den Hook in die lokale `.claude/settings.json` ein. Zeig mir den Eintrag, bevor du ihn speicherst, und erkläre kurz, was er tut."
3. Claude bereitet den Eintrag vor, zeigt Ihnen den Diff und eine Erklärung, Sie bestätigen oder korrigieren.

Das ist der beste Weg aus drei Gründen: Claude prüft die Syntax, Sie sehen den Eintrag, bevor er landet, und wenn Sie die Formulierung später ändern wollen („der Hook soll nur auf Markdown-Dateien laufen"), sagen Sie das einfach.

**Wie der erzeugte JSON-Eintrag aussieht (zur Information, nicht zum Abtippen).**

Damit Sie wissen, was nach einem solchen Prompt in Ihrer `.claude/settings.json` landet, hier der Eintrag, den Claude typischerweise erzeugt:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "echo \"[$(date +%T)] Bash tool wird ausgefuehrt\" >> ~/.claude/tool-log.txt"
          }
        ]
      }
    ],
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "prettier --write $CLAUDE_FILE_PATHS 2>/dev/null || true"
          }
        ]
      }
    ]
  }
}
```

Im Klartext: Der erste Hook schreibt bei jedem Bash-Aufruf eine Zeile mit Zeitstempel in eine Log-Datei. Der zweite Hook formatiert mit `prettier` jede Datei, die Claude gerade mit Edit oder Write bearbeitet hat, sodass Ihr Code automatisch sauber bleibt. `$CLAUDE_FILE_PATHS` steht in diesem Beispiel stellvertretend für die Information, welche Datei gerade betroffen war — je nach Claude-Code-Version wird diese Information entweder als Umgebungsvariable bereitgestellt oder als JSON-Nutzlast auf `stdin` an den Hook übergeben. Welche Variante bei Ihnen gilt, verrät `claude --version` in Kombination mit der offiziellen Hooks-Dokumentation; lassen Sie sich den Hook im Zweifel von Claude selbst für Ihre Version erzeugen, statt ihn aus diesem Tutorial zu kopieren.

Sie können diesen Block bei Bedarf in Ihrem Editor nachsehen, wenn Sie verstehen wollen, was Ihr Prompt bewirkt hat, oder wenn Sie später etwas manuell anpassen möchten. Die Strukturen sind schnell lesbar, auch ohne Programmiererfahrung: **welches Ereignis** (`PreToolUse`, `PostToolUse`), **für welches Tool** (`matcher`), **welcher Shell-Befehl** (`command`). Mehr Bausteine braucht ein einfacher Hook nicht.

---

## Sinnvolle Hooks für den Alltag

Nicht jeder Hook ist eine gute Idee. Je mehr Hooks Sie installieren, desto schwerer wird nachzuvollziehen, was im Hintergrund passiert. Die folgenden drei sind meist ihr Gewicht wert:

**Hook 1: Post-Edit-Formatierung.**

Nach jeder Änderung an Code- oder Markdown-Dateien läuft automatisch ein Formatter (z. B. `prettier`, `ruff format`, `mdformat`). So bleibt Ihr Projekt konsistent formatiert, ganz ohne dass Sie oder Claude daran denken müssen. Der Hook ist oben schon gezeigt.

**Hook 2: Pre-Bash-Log.**

Jeder Bash-Aufruf wird mit Zeitstempel in eine lokale Log-Datei geschrieben. Das hilft enorm, wenn Sie später nachvollziehen wollen, was Claude eigentlich alles ausgeführt hat. Gerade in längeren Agent-Läufen ist das Gold wert.

**Hook 3: Stop-Benachrichtigung.**

Wenn Claude mit einer längeren Aufgabe fertig ist, piept oder blinkt Ihr System. So müssen Sie nicht ständig aufs Terminal schauen. Der Befehl ist je nach Betriebssystem unterschiedlich:

- **macOS:** `say "fertig"` (gesprochene Ansage) oder `osascript -e 'display notification "Claude ist fertig" with title "Claude Code"'` (Desktop-Benachrichtigung).
- **Linux (GNOME/KDE):** `notify-send "Claude Code" "Claude ist fertig"` — setzt voraus, dass `libnotify-bin` installiert ist.
- **Windows (PowerShell):** `powershell -Command "[System.Reflection.Assembly]::LoadWithPartialName('System.Windows.Forms'); [System.Windows.Forms.MessageBox]::Show('Claude ist fertig','Claude Code')"` als einfachste Variante; wer es eleganter will, installiert das Modul `BurntToast` und ruft `New-BurntToastNotification -Text 'Claude ist fertig'` auf.

In allen drei Fällen prüfen Sie nach dem Einrichten einmal, ob der Befehl in einem gewöhnlichen Terminal funktioniert, bevor Sie ihn in die Hook-Konfiguration eintragen. Wenn der nackte Befehl keinen Ton und keine Benachrichtigung auslöst, wird der Hook es auch nicht tun.

**Ein Wort zur Vorsicht:** Hooks laufen mit den Rechten Ihres Nutzers. Ein falsch gesetzter Hook, der bei jeder Datei-Änderung etwas Falsches macht, kann schnell Schaden anrichten. Testen Sie neue Hooks immer erst in einem Wegwerf-Projekt, bevor Sie sie global aktivieren.

---

## Slash-Commands — wiederverwendbare Workflows

Als dritter Baustein dieser Werkstatt verdienen **Slash-Commands** eine kurze Erwähnung. Ein Slash-Command ist ein fertiger Arbeitsauftrag, den Sie im Claude-Code-Chat mit `/name` aufrufen. Er lebt als Markdown-Datei unter `.claude/commands/<name>.md` (oder global unter `~/.claude/commands/`).

Ein Beispiel — der `/wochenreport`-Command, der einen Wochenbericht aus Ihrem Arbeitsordner zusammenstellt:

```markdown
---
description: Erstellt einen Wochenreport aus den Mails, Dateien und Commit-Logs 
  der laufenden Woche.
---

Du bist der Wochenreport-Assistent. Tu folgendes, in dieser Reihenfolge:

1. Ermittle den Beginn der aktuellen Kalenderwoche (Montag, 00:00).
2. Durchsuche den Ordner `./notizen/` nach Dateien, die diese Woche geaendert wurden.
3. Durchsuche die Gmail-Inbox (MCP) nach Mails der Woche, die mit "Projekt" im Betreff beginnen.
4. Fasse die Aktivitaeten pro Projekt in einem Abschnitt zusammen.
5. Formatiere das Ergebnis als Markdown mit drei Ebenen: Projekt -> Tag -> Aktivitaet.
6. Speichere das Ergebnis unter `./reports/woche-<KW>.md`.
7. Zeige mir das Ergebnis zum Gegenlesen.

Frage nach, wenn die Gmail-Verbindung nicht steht oder der Ordner /notizen fehlt.
```

Sobald die Datei existiert, können Sie im Chat einfach `/wochenreport` tippen, und der Agent arbeitet die Schritte ab. Das ist die Form, in der Sie in Teil 05 und 06 die Praxis-Workflows nutzen werden.

**Der Unterschied zwischen einem Slash-Command und einem Subagent:** Ein Subagent ist ein eigener kleiner Claude, den der Hauptagent bei Bedarf **aufruft**. Ein Slash-Command ist eine Prompt-Vorlage, die der Hauptagent selbst **ausführt**. Beide sind nützlich, für unterschiedliche Zwecke: Subagents für spezialisierte Teilaufgaben, Slash-Commands für wiederverwendbare Komplettabläufe.

---

## Zusammenspiel in einer echten Arbeitssitzung

Hier ist eine typische Claude-Code-Sitzung, die Subagents, Hooks und Slash-Commands kombiniert. Lesen Sie es als Demonstration, nicht als Kochrezept:

**9:15 Uhr.** Sie öffnen den Projektordner und starten Claude Code. Beim Start greift der UserPromptSubmit-Hook und hängt den aktuellen Git-Branch an jeden Prompt an, damit Claude immer weiß, wo Sie gerade sind.

**9:17 Uhr.** Sie tippen `/wochenreport`. Der Slash-Command startet. Claude prüft die Gmail-Verbindung (steht), durchsucht den Notizen-Ordner, sucht die Mails der Woche, verdichtet pro Projekt, formatiert das Ergebnis.

**9:22 Uhr.** Claude speichert den Bericht unter `./reports/woche-15.md`. Durch den Post-Write-Hook läuft automatisch `mdformat` über die Datei.

**9:23 Uhr.** Claude ruft den `doc-reviewer`-Subagent auf, der den frisch geschriebenen Bericht einmal durchsieht und vier kurze Abschnitte zurückmeldet: „Klarheit OK. Tone OK. Ein interner Link nach `../notizen/kunde-x.md` ist tot (Datei wurde letzte Woche umbenannt). Keine Tippfehler gefunden."

**9:24 Uhr.** Claude bittet Sie, den toten Link zu korrigieren, schlägt den korrekten Pfad vor, Sie bestätigen. Claude korrigiert, der Post-Edit-Hook formatiert neu.

**9:25 Uhr.** Claude meldet „fertig". Der Stop-Hook löst die Desktop-Benachrichtigung aus. Sie wissen es, ohne auf das Terminal zu schauen.

Das ist realistisch, kein Idealbild. Die Summe aus Slash-Command, Subagent und drei Hooks macht aus einer 30-Minuten-Aufgabe eine 10-Minuten-Aufgabe — und die 10 Minuten sind vor allem **Beaufsichtigung**, nicht manuelle Arbeit.

---

## Stärken und Schwächen auf einen Blick

**Stärken:**

- Subagents trennen Zuständigkeiten sauber und schonen den Kontext des Hauptagenten.
- Hooks bringen Verlässlichkeit in wiederkehrende Nebenaufgaben (Formatierung, Logging, Benachrichtigung).
- Slash-Commands machen komplette Workflows mit einem einzigen Wort aufrufbar.
- Alle drei sind **in Textdateien** versioniert und in Git ablegbar — ideal für Team-Umgebungen.

**Schwächen:**

- Die Einrichtung ist fummelig, wenn Sie zum ersten Mal damit anfangen — es lohnt sich, Claude selbst bei der Einrichtung zu nutzen.
- Zu viele Subagents machen den Hauptagenten unsicher, welcher gerade gemeint ist — weniger ist oft mehr.
- Hooks, die Fehler haben, können ganze Sitzungen blockieren — testen Sie sie isoliert.
- Das Feature-Set ändert sich mit Claude-Code-Versionen schneller als die Dokumentation hinterherkommt — prüfen Sie `claude --version` und die offizielle Doku, wenn etwas nicht wie erwartet funktioniert.

---

## Troubleshooting — die häufigsten Stolperstellen

Wenn Sie zum ersten Mal mit Subagents und Hooks arbeiten, werden Sie sehr wahrscheinlich in eine der folgenden Fallen laufen. Alle sind harmlos, wenn Sie wissen, wo sie sitzen.

**Problem: `/agents` zeigt den neu angelegten Subagent nicht an.**
Meist haben Sie Claude Code aus einem Elternordner gestartet, während die Datei unter `./projekt/.claude/agents/` liegt. Claude Code liest `.claude/agents/` aus dem **aktuellen Arbeitsverzeichnis** und zusätzlich aus `~/.claude/agents/`. Prüfen Sie mit `pwd`, wo Sie stehen, und starten Sie Claude Code aus dem richtigen Projektordner — oder verschieben Sie den Subagent nach `~/.claude/agents/`, wenn er überall verfügbar sein soll.

**Problem: Der Hauptagent ruft den Subagent nicht automatisch auf.**
Fast immer ein **Beschreibungs-Problem**, kein Code-Problem. Die `description` im YAML-Vorspann ist zu vage oder zu allgemein. Schreiben Sie sie so, dass der Hauptagent aus der Formulierung heraus schließen kann, wann der Subagent zuständig ist — inklusive des Worts „proactively" für automatisches Delegieren. Testen Sie es anschließend mit einem bewusst klar formulierten Prompt, der die Schlüsselwörter der Beschreibung aufgreift.

**Problem: Der Hook läuft, aber nichts passiert.**
Der zweithäufigste Fehler. Der eingetragene Shell-Befehl funktioniert nicht im nackten Terminal. Kopieren Sie den Befehl aus der `command`-Zeile 1:1 in ein normales Terminal und führen Sie ihn aus. Wenn er dort schweigt oder einen Fehler wirft, wird der Hook es auch tun. Typische Ursachen: ein fehlendes Programm (`prettier` nicht installiert), ein falscher Pfad, ein fehlendes Modul (`BurntToast` unter Windows nicht installiert), eine falsche Umgebungsvariable.

**Problem: Der Hook soll einen Datei-Pfad verarbeiten, bekommt aber nichts.**
Datei-Pfade stehen einem Hook nur bei bestimmten Ereignissen zur Verfügung — typisch bei `PostToolUse` nach `Edit` oder `Write`. Bei `Stop`, `Notification` oder `UserPromptSubmit` gibt es keine Datei-Pfade, weil die zugehörige Aktion gar keine Datei betrifft. Außerdem ändert sich zwischen Claude-Code-Versionen, *wie* der Pfad übergeben wird (Umgebungsvariable oder JSON auf `stdin`). Prüfen Sie erstens, ob das gewählte Ereignis überhaupt mit Datei-Pfaden arbeiten kann, und zweitens, welche Übergabeform Ihre Version verwendet — im Zweifel erzeugen Sie den Hook per Prompt von Claude selbst, statt ihn aus einem Tutorial zu kopieren.

**Problem: Ein Hook blockiert die gesamte Sitzung.**
Wenn ein Hook sehr lange läuft (Minuten) oder hängt, wartet Claude Code auf sein Ende. Das macht Sitzungen im schlimmsten Fall unbenutzbar. Zwei Gegenmittel: Erstens, den Befehl in den Hintergrund schicken (`& disown` unter Unix) oder auf ein kurzes Timeout setzen (`timeout 5s …`). Zweitens, den Hook in einem **Wegwerf-Projekt** testen, bevor Sie ihn global in `~/.claude/settings.json` aktivieren — ein kaputter globaler Hook betrifft alle Projekte gleichzeitig.

**Problem: Der Subagent hat zu wenig Kontext.**
Der Subagent sieht nicht die gesamte Haupt-Unterhaltung, sondern nur das, was der Hauptagent ihm beim Aufruf explizit weitergibt. Wenn der Subagent sich beschwert, er wisse nicht, welche Datei gemeint sei, liegt das in der Regel daran, dass der Hauptagent zu wenig Briefing geliefert hat. Formulieren Sie Ihren ursprünglichen Prompt so, dass die wichtigen Informationen klar benannt sind (Dateinamen, Ziel, Randbedingungen), oder ergänzen Sie die Systemprompt des Subagents um einen ausdrücklichen Hinweis, welche Informationen er vom Hauptagenten erwartet.

---

## Kernbotschaft

Claude Code hat drei Werkstatt-Werkzeuge: **Subagents** (spezialisierte kleine Claudes mit eigenem Kontext und engem Werkzeugkasten, angelegt per `/agents`), **Hooks** (Befehle, die an Ereignissen wie PreToolUse, PostToolUse oder Stop automatisch greifen) und **Slash-Commands** (wiederverwendbare Prompt-Vorlagen für komplette Workflows, abgelegt unter `.claude/commands/`). Zusammen machen sie aus einem Sprachmodell eine organisierte Arbeitsumgebung. Fangen Sie klein an: ein Subagent, zwei Hooks, ein Slash-Command — der Rest wächst mit.

---

## Nächste Schritte

- **[05 Praxis E-Mail-Triage und Meeting-Notes](./05%20Praxis%20E-Mail-Triage%20und%20Meeting-Notes.md)** — die ersten beiden Use-Cases, in denen Sie Subagents und Slash-Commands ganz konkret bauen.
- Zurück zur Übersicht: **[README](./README.md)**.
- Querverweis: **Kapitel 10 Teil 04 (Claude Code im Terminal)** für den Basis-Einstieg, wenn Ihnen `/agents` oder `.claude/settings.json` noch fremd vorkommen.
