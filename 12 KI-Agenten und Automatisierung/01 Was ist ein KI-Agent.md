# 01 Was ist ein KI-Agent?

**Vom Chatbot zum arbeitenden Kollegen — eine Begriffsklärung.**

---

## Warum dieses Tutorial?

„KI-Agent" ist 2026 eines der meistbenutzten und gleichzeitig unschärfsten Wörter der Branche. Jeder Anbieter nennt etwas anderes so — von einem simplen Chatbot mit ein paar zusätzlichen Buttons bis zu vollständig autonomen Systemen, die stundenlang ohne menschliche Aufsicht arbeiten. Wenn Sie einen Agenten bauen oder einsetzen wollen, müssen Sie erst einmal wissen, worüber Sie reden. Sonst kaufen Sie am Ende einen Chatbot, der sich Agent nennt, oder Sie fürchten sich vor einer Technik, die es so gar nicht gibt.

Dieses Tutorial klärt die Begriffe in einer Sprache, die ohne Vorwissen funktioniert. Am Ende verstehen Sie, was einen Agenten von einem Chatbot unterscheidet, welche Bausteine ein Agent braucht, warum „Loop" das wichtigste Wort im Agenten-Vokabular ist und wo die Grenzen der Autonomie heute liegen.

**Was Sie nach diesem Tutorial wissen werden:**

- Den Unterschied zwischen **Chatbot**, **assistierendem LLM** und **echtem Agent**.
- Die vier Bausteine eines Agenten: **Planner**, **Tools**, **Memory**, **Loop**.
- Warum ein Agent Aufgaben schafft, an denen ein Chatbot scheitert — und umgekehrt.
- Wo die Grenzen heutiger Agenten liegen und welche Risiken Sie kennen müssen.
- Ein Vokabular, mit dem Sie die restlichen Teile dieses Kapitels durcharbeiten können.

---

## Der Chatbot: Frage rein, Antwort raus

Ein klassischer **Chatbot** ist im Kern ein einstufiger Übersetzer. Sie tippen eine Frage, das Sprachmodell produziert eine Antwort, fertig. Die Unterhaltung läuft in einer einzigen Richtung: Sie → Modell → Sie. Das Modell hat keinen Zugriff auf Ihre Dateien, Ihre Mails, Ihren Kalender. Es kann weder nachschauen, wie spät es ist, noch etwas für Sie erledigen. Es antwortet nur.

Das ist nicht abwertend gemeint — ein gutes Chat-Erlebnis ist enorm wertvoll, und für viele Aufgaben (Text redigieren, Konzepte erklären, Ideen brainstormen) reicht es vollkommen aus. Aber es ist eben **eine Antwort auf eine Frage**, nichts weiter.

Beispiel: Sie schreiben „Fasse mir diesen Text zusammen" und fügen 3.000 Zeichen ein. Der Chatbot liefert eine Zusammenfassung. Damit ist die Aufgabe für ihn erledigt. Er weiß nicht, was Sie mit der Zusammenfassung vorhaben, und er kann sie auch nicht in Ihren Arbeitsordner speichern oder per Mail verschicken. Wenn Sie das wollen, müssen Sie es manuell tun.

---

## Das assistierende LLM: Chatbot mit Werkzeugen

Die nächste Stufe ist das **assistierende Sprachmodell**. Es kann Werkzeuge benutzen — Web-Suche, Rechner, Bildgenerierung, vielleicht Datei-Zugriff. Wenn Sie fragen „Wie ist das Wetter in Hamburg?", dann ruft es tatsächlich einen Wetterdienst auf, statt aus seinem Training zu raten.

Das ist der Zustand, den die meisten Menschen heute meinen, wenn sie „KI" sagen. ChatGPT mit Browsing, Claude mit Websuche und dem Cowork-Dateizugriff, Gemini mit Google-Integration — das sind alles assistierende LLMs. Sie können einzelne Werkzeuge pro Frage einsetzen.

Der entscheidende Punkt: Es bleibt **eine Runde**. Sie stellen eine Frage, das Modell wählt gegebenenfalls ein Werkzeug, benutzt es, und liefert die Antwort. Danach ist wieder Pause, bis Sie die nächste Frage stellen. Die Initiative liegt bei Ihnen.

---

## Der Agent: Plan, Tools, Loop

Ein **Agent** fügt zwei Dinge hinzu, die alles verändern: einen **Plan** und eine **Schleife**.

Wenn Sie einem Agenten sagen „Bereite den Monatsreport für März vor", dann passiert nicht eine Runde mit einer Antwort. Der Agent:

1. **Plant** die Aufgabe in mehrere Schritte herunter. „Ich muss erst die März-CSV aus Google Drive holen, dann mit dem xlsx-Skill prüfen, ob sie vollständig ist, dann die Kernzahlen berechnen, dann ein Diagramm bauen, dann eine Kurzzusammenfassung schreiben, dann alles in ein Word-Dokument überführen und in den Reports-Ordner speichern."
2. **Führt** den ersten Schritt aus. Dabei wählt er ein passendes Werkzeug (MCP-Aufruf, Shell-Kommando, Skill).
3. **Prüft das Ergebnis.** Ist die Datei da? Ist sie vollständig? Stimmen die Spalten? Falls nicht: Plan anpassen.
4. **Entscheidet über den nächsten Schritt.** Manchmal ist es der geplante nächste Schritt. Manchmal ein unerwarteter Zwischenschritt, weil unterwegs etwas aufgefallen ist.
5. **Wiederholt das.** Bis die Aufgabe erledigt ist.

Dieser **Loop** ist der Kern. Ein Agent ist im Grunde ein Sprachmodell, das sich selbst immer wieder fragt: „Was ist jetzt der nächste sinnvolle Schritt?" — und bei jedem Zyklus ein Werkzeug benutzen darf. Das klingt unspektakulär, verändert aber das, was möglich ist, komplett. Aufgaben, die in der Chatbot-Welt viele manuelle Runden brauchen, erledigt der Agent in einer einzigen Beauftragung.

Sie sehen das in [`illustrations/12-01-chatbot-vs-agent.png`](./illustrations/12-01-chatbot-vs-agent.png) gegenübergestellt: links der einfache Einweg-Pfeil des Chatbots, rechts die Schleife des Agenten mit Planner, Tools und Loop.

---

## Die vier Bausteine eines Agenten

Jeder Agent, egal ob in Claude Code, in n8n oder in einem eigenen Python-Projekt, besteht aus vier Komponenten. Wenn Sie diese vier kennen, können Sie jedes Agenten-Framework in wenigen Minuten einordnen.

### 1. Planner

Der **Planner** entscheidet, was als Nächstes passiert. In den meisten Fällen **ist** der Planner einfach das Sprachmodell. Es bekommt den aktuellen Stand der Aufgabe, die Liste der verfügbaren Werkzeuge, die Historie der bisherigen Schritte — und entscheidet: „Jetzt rufe ich das Google-Drive-Tool mit folgenden Parametern auf."

Der Planner ist der eigentliche „Agent" im Agent. Die Planungs-Qualität entscheidet, ob Ihr Agent die Aufgabe schafft oder sich verrennt. Deshalb macht es einen Unterschied, welches Modell Sie als Planner einsetzen: Opus 4.6 plant besser als Sonnet 4.6, das wiederum besser plant als Haiku 4.5 — allerdings auf Kosten von Geschwindigkeit und Preis. Für komplexe Aufgaben lohnt sich Opus, für Routine-Aufgaben reicht Sonnet, für einfache Klassifikations-Subagents genügt Haiku.

### 2. Tools

**Tools** sind die Werkzeuge, die der Agent benutzen darf. Sie sind die einzige Möglichkeit, mit der Welt außerhalb des Modells zu interagieren. Ohne Tools ist ein Agent nur ein Chatbot mit gutem Plan, aber ohne Arme und Beine.

Im Claude-Ökosystem kommen Tools aus vier Quellen:

- **Eingebaute Tools** — Datei lesen und schreiben, Shell-Befehle, Web-Suche, Web-Fetch. Diese hat Claude Code und Cowork automatisch dabei.
- **MCP-Server** — externe Dienste wie Slack, Google Drive, GitHub, Notion, Gmail. Kapitel 10 Teil 03 hat die Grundlagen eingeführt; Teil 03 dieses Kapitels vertieft sie.
- **Skills** — strukturierte Anleitungen für komplexe Datei-Arbeiten (Word, Excel, PDF, PowerPoint). Ebenfalls aus Kapitel 10 Teil 03.
- **Subagents** — kleinere Agenten, die als Tool eines größeren Agenten auftauchen und Teilaufgaben übernehmen. Dazu mehr in Teil 04.

Je mehr Tools ein Agent hat, desto mehr Möglichkeiten hat er — aber auch desto größer ist die Chance, dass er sich für das falsche Werkzeug entscheidet oder in die falsche Richtung läuft. „So wenig Tools wie möglich, so viele wie nötig" ist eine gute Faustregel.

### 3. Memory

**Memory** ist das Gedächtnis des Agenten. Es hat drei Schichten, die Sie kennen sollten:

**Kurzfristiges Gedächtnis** ist der aktuelle Kontext: die laufende Konversation, die bisher benutzten Tools, die bisherigen Ergebnisse. Das hält so lange wie die Session. Wenn Sie Claude Code schließen, ist es weg.

**Mittelfristiges Gedächtnis** sind Dateien, die der Agent während seiner Arbeit anlegt und wieder liest. In Claude Code ist das typisch eine `CLAUDE.md` im Projektordner oder eine Notizen-Datei im Arbeitsverzeichnis. Der Agent kann dort Zwischenergebnisse ablegen, um sich selbst in späteren Schritten daran zu erinnern.

**Langfristiges Gedächtnis** gibt es in der aktuellen Generation von Agenten nur in Ansätzen. Claude kann sich in einer neuen Session nicht daran erinnern, was Sie in der letzten Woche gemacht haben — es sei denn, Sie haben es in eine Datei geschrieben, die er jetzt liest. Projekt-Speicher (Claude Projects, ChatGPT Memory) gehen in diese Richtung, sind aber noch lückenhaft. Wer Langzeit-Gedächtnis braucht, baut es in der Regel selbst: als Markdown-Dateien, die der Agent pflegt.

### 4. Loop

Der **Loop** ist der Mechanismus, der das Ganze zum Agenten macht. Er funktioniert so:

```
1. Zielaufgabe bekommen
2. Aktuellen Stand anschauen (Kontext + Memory)
3. Planner fragen: Was ist der nächste Schritt?
4. Tool auswählen und aufrufen
5. Ergebnis in den Kontext einbauen
6. Ist die Aufgabe erledigt? 
   Ja -> Abschlussbericht, Ende
   Nein -> zurück zu Schritt 2
```

Diese Schleife läuft so lange, bis der Planner sagt: „Ich bin fertig" — oder bis eine Sicherung greift (maximale Anzahl Schritte erreicht, bestimmter Fehler aufgetreten, Nutzer-Eingriff). Der Loop ist das, was unsichtbar im Hintergrund rattert, während Sie in Claude Code einen Fortschrittsbalken sehen. Er ist auch das, was unangenehm werden kann, wenn Sie keine Grenzen setzen — Teil 07 geht darauf ein.

Die Illustration [`illustrations/12-02-agent-anatomie.png`](./illustrations/12-02-agent-anatomie.png) zeigt die vier Bausteine als zusammenhängendes Schema.

---

## Der fundamentale Unterschied: Wer startet die Runde?

Wenn Sie nur einen Satz aus diesem Kapitel mitnehmen, dann diesen: **Beim Chatbot startet jede Runde der Mensch. Beim Agenten startet die nächste Runde das System.**

Das ändert alles. Ein Chatbot wartet, bis Sie ihm einen Schritt ansagen. Ein Agent bekommt ein Ziel und arbeitet selbst darauf hin. Daraus folgt:

- Agenten schaffen mehr pro Beauftragung — das ist der Gewinn.
- Agenten können mehr kaputtmachen pro Beauftragung — das ist das Risiko.
- Agenten sind schwerer zu debuggen, weil sie Schritte machen, die Sie nicht ausdrücklich angeordnet haben.
- Agenten brauchen andere Prompts als Chatbots. Sie beauftragen ein **Ziel**, keinen **Schritt**.

Der erste Prompt an einen Agenten sieht deshalb anders aus als an einen Chatbot. Ein guter Chatbot-Prompt lautet vielleicht „Fasse diesen Text in drei Sätzen zusammen". Ein guter Agent-Prompt lautet „Lies die drei neuesten Mails von Kunde Meier, ziehe die offenen Punkte heraus, prüfe in der Projektdatei im Ordner `projekte/meier/` was davon bereits adressiert ist, und schreibe mir eine To-do-Liste der verbleibenden Punkte in den Ordner `notizen/`. Frage mich nach, wenn etwas unklar ist." — mehrere Schritte, klares Ziel, expliziter Ausgabeort, ausdrückliche Aufforderung zum Nachfragen bei Unklarheiten.

---

## Wo die Grenzen heute liegen

Es ist 2026, nicht 2030. Was heute gut funktioniert und was noch nicht, sollten Sie realistisch einschätzen, damit Sie nicht enttäuscht werden:

**Was Agenten heute gut können:**

- Klar umrissene, wiederholbare Aufgaben, bei denen die Werkzeuge ausreichen (E-Mail-Triage, Monats­reports, Dokumentation, Code-Refactoring in kleinen Schritten).
- Zwei- bis fünfstufige Pläne, in denen jeder Schritt überprüfbar ist.
- Aufgaben unter Aufsicht: Sie starten den Agenten, schauen zu, greifen ein, wenn etwas abdriftet.

**Was Agenten heute noch schlecht können:**

- Wirklich lange, autonome Aufgaben über Stunden ohne Aufsicht. Je länger der Lauf, desto höher die Chance, dass sich Fehler akkumulieren.
- Aufgaben mit großer Ergebnis-Unschärfe — wenn niemand objektiv sagen kann „das ist richtig, das ist falsch", dann weiß der Agent am Ende auch nicht, ob er fertig ist.
- Aufgaben, die viel **Weltwissen** voraussetzen, das nicht in den Tools steckt. Der Planner ist nur so gut wie das Modell dahinter — wenn das Modell etwas nicht weiß, rät es.
- Aufgaben, die **unumkehrbare** Aktionen in der echten Welt auslösen (Geld überweisen, Verträge abschließen, produktive Systeme deployen). Das sollten Menschen bestätigen.

---

## Ein nützlicher Sanity-Check vor jeder Agenten-Automation

Bevor Sie einen Agenten für eine Aufgabe bauen, stellen Sie sich drei Fragen:

1. **Kann ich die Aufgabe in fünf oder weniger klaren Schritten beschreiben?** Wenn nein, brauchen Sie erst einmal einen klareren Prozess, nicht einen Agenten.
2. **Kann ich objektiv sagen, wann die Aufgabe erledigt ist?** Wenn nein, wird der Agent entweder zu früh abbrechen oder ewig weiterlaufen.
3. **Was ist das Schlimmste, das passieren kann, wenn der Agent einen Fehler macht?** Wenn die Antwort „eine vertane Stunde" ist: entspannter Einsatz. Wenn die Antwort „Kunde gekündigt" oder „Daten weg" ist: nur mit starken Guardrails, Menschen-im-Loop und kleinen Schritten.

---

## Wenn Sie bisher nur ChatGPT kannten — ein kleiner Übersetzungsschlüssel

Viele Leserinnen und Leser dieses Kapitels kommen aus der ChatGPT-Welt und haben die Claude-Begriffe (Subagent, MCP, Skill, Cowork, Claude Code) noch nicht sortiert. Die folgende Tabelle ist eine Orientierungshilfe, keine strenge Gleichung — die Konzepte ähneln sich, unterscheiden sich aber in Details. Sie ist trotzdem nützlich, weil sie Ihnen das Gefühl nimmt, bei null anzufangen.

| Wenn Sie aus ChatGPT kommen …     | … dann ist das Claude-Äquivalent                                                               | Anmerkung                                                                                                         |
|----------------------------------|-----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| **Custom GPT** (eigene Persona)   | **Subagent** in Claude Code oder **Claude Project** in der Web-App                             | Custom GPT = Persona + Wissen + Tools in einem. Im Claude-Ökosystem ist das aufgeteilt: Persona und Tools per Subagent, Wissen per Datei-Zugriff. |
| **GPT Action** (Custom-GPT-API)   | **MCP-Tool**                                                                                  | Actions verbinden einen GPT mit einer externen API; MCP-Server tun dasselbe für Claude, aber offen und standardisiert. |
| **Wissens-Uploads** im GPT        | **Workspace-Ordner** in Cowork oder **Skills** in Claude Code                                  | In Claude legen Sie Dateien in einen Ordner, Claude liest sie bei Bedarf. Das ist transparenter als GPT-Wissen.    |
| **ChatGPT Memory** (Langzeit)     | **`CLAUDE.md`** im Projektordner, Markdown-Notizen, **Claude Projects**                         | Kein automatisches Langzeit-Gedächtnis — der Nutzer pflegt es als Dateien, die Claude jedes Mal frisch liest.     |
| **Custom Instructions** (Global)  | **`~/.claude/CLAUDE.md`** oder projektweite `CLAUDE.md`                                         | Gleicher Zweck (Stil, Präferenzen), liegt aber als sichtbare Datei auf Ihrem Rechner.                              |
| **ChatGPT Tasks** (geplant)       | **`schedule`-Skill** in Claude oder **Cron-Job** auf dem eigenen Rechner                        | Beide lösen wiederkehrende Aufgaben aus. Schedule-Skill ist direkt in Cowork verfügbar.                            |
| **ChatGPT Operator** (Browser-Agent) | **Claude in Chrome** (Browser-Erweiterung)                                                   | Beide steuern einen echten Browser. Claude in Chrome ist zum Zeitpunkt des Schreibens noch in Beta.                |
| **„System Prompt" im GPT-Builder** | **YAML-Frontmatter + Beschreibung** in einer Subagent-Markdown-Datei                          | Derselbe Zweck (Rolle und Leitplanken), nur als sichtbare Datei statt als Formular in einer Web-UI.                |

Ein paar Dinge, die in der Tabelle nicht stehen, aber beim Umstieg trotzdem helfen: Claude Code ist kein GPT-Builder mit GUI, sondern ein Terminal-Werkzeug — wer das nicht mag, bleibt komplett in **Cowork** (Teil 04b zeigt, dass das geht). **MCP** ist ein offener Standard, **GPT Actions** sind es nicht; Sie können denselben MCP-Server in Claude, in Cursor, in Windsurf oder in einem eigenen Projekt benutzen. Und im Claude-Ökosystem liegen Personas, Prompts und Konfiguration in der Regel als **Dateien auf Ihrem Rechner**, nicht in einer Cloud-Maske — das ist ungewohnt, wird aber schnell zum Vorteil, sobald Sie versionieren, teilen oder verbessern wollen.

---

## Kernbotschaft

Ein **Chatbot** antwortet auf eine Frage; ein **Agent** bekommt ein **Ziel** und arbeitet in einer **Schleife** selbst darauf hin — mit Planner, Tools, Memory und Loop als den vier Bausteinen. Der fundamentale Unterschied: Beim Chatbot startet der Mensch jede Runde, beim Agenten startet die nächste Runde das System. Daraus folgt Leistung und Risiko zugleich. Vor jeder Automation stellen Sie drei Fragen: klare Schritte, klares Fertig-Kriterium, Schaden im schlimmsten Fall.

---

## Nächste Schritte

- **[02 Die Agent-Landschaft 2026](./02%20Die%20Agent-Landschaft%202026.md)** — eine Landkarte der Werkzeuge, die Sie 2026 als Agent-Infrastruktur benutzen können.
- Wenn Sie gleich in den Kern einsteigen wollen: **[03 MCP verstehen](./03%20MCP%20verstehen.md)** — das Protokoll, das Agenten ihre Werkzeuge gibt.
- Querverweis: **Kapitel 10 Teil 04 (Claude Code im Terminal)** hat Subagents, Hooks und Plan-Mode bereits kurz eingeführt. Wenn das alles neu klingt, empfiehlt sich ein Blick zurück.
