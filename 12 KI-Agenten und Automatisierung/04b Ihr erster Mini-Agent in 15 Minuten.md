# 04b Ihr erster Mini-Agent in 15 Minuten

**Ein praktischer Kurz-Einstieg — ausschließlich mit Cowork, ohne Claude Code, ohne Subagents, ohne Slash-Commands.**

---

## Warum dieses Zwischen-Tutorial?

Teil 04 hat Subagents, Hooks und Slash-Commands in Claude Code eingeführt. Das ist der saubere, ausbaubare Weg — aber er setzt voraus, dass Sie ein Terminal offen haben, einen Projektordner angelegt haben und die Logik hinter YAML-Vorspänden und Markdown-Systemprompts verstehen.

Für viele Leserinnen und Leser, die bisher hauptsächlich mit ChatGPT gearbeitet haben, ist das ein größerer Sprung als nötig. Dieses Zwischen-Tutorial ist der kleinere, niedrigschwellige Einstieg: **ein erster Mini-Agent, den Sie in einer Viertelstunde bauen, komplett in Cowork, ohne ein Terminal anzufassen**. Er ersetzt Teil 04 nicht, er geht ihm voraus. Wenn dieser Mini-Agent bei Ihnen läuft, sind Sie bereit für Teil 04, und der Sprung dahin fühlt sich dann weniger wild an.

**Was Sie nach diesem Tutorial gebaut haben werden:** einen kleinen, wiederverwendbaren Wochenrückblick-Assistenten in Cowork, der Dokumente in einem Ordner durchgeht und Ihnen jeden Freitag eine Ein-Seiten-Übersicht schreibt. Ohne Subagents. Ohne Slash-Commands. Ohne JSON-Konfiguration.

---

## Was Sie brauchen

- **Claude Desktop App** mit aktivem Cowork-Modus (Kapitel 10 Teil 02).
- **Einen Arbeitsordner**, den Sie in Cowork als Workspace gemountet haben — am besten ein Ordner, in dem Sie Wochen-Notizen oder Projekt-Dateien ablegen. Für den ersten Lauf reicht ein Test-Ordner mit ein paar Markdown- oder Textdateien.
- **Fünf bis sieben ruhige Minuten** am Stück — besser als unterbrochen arbeiten.

Nicht nötig: Claude Code, ein Terminal, MCP-Connectors über die Standard-Einrichtung hinaus, Programmier-Vorkenntnisse.

---

## Der Bauplan — in drei Schritten

Das Ziel ist ein Mini-Agent, der jede Woche dieselbe Aufgabe erledigt: In einen Ordner schauen, den Inhalt zusammenfassen, das Ergebnis als neue Datei ablegen. Das ist bewusst klein gewählt. Wenn Sie diesen Minimalfall einmal gesehen haben, sind alle größeren Agenten nur Variationen davon.

### Schritt 1 — Den Agent im Kopf definieren (2 Minuten)

Bevor Sie Cowork öffnen, beantworten Sie drei Fragen auf einem Notizzettel:

1. **Welcher Ordner wird gelesen?** Zum Beispiel `Wochen-Notizen/`, `projekte/aktuell/` oder `Meeting-Protokolle/2026/`.
2. **Was soll am Ende herauskommen?** Zum Beispiel eine Datei `wochenrueckblick-<datum>.md` mit drei Abschnitten (Was ist passiert, offene Punkte, nächste Woche).
3. **Was soll der Agent auf keinen Fall tun?** Zum Beispiel: keine Datei im Quell-Ordner ändern, nichts an Dritte verschicken, keine Namen aus den Notizen in einer Zusammenfassung anonymisieren, die vielleicht weitergereicht wird.

Schreiben Sie diese drei Punkte kurz auf. Sie sind Ihr **Agenten-Briefing**. Bei jedem nachfolgenden Workflow werden Sie dieselben drei Fragen stellen.

### Schritt 2 — Cowork einmal beauftragen (8 Minuten)

Öffnen Sie Cowork. Wählen Sie den Arbeitsordner im Sidebar. Schreiben Sie einen einzigen, klaren Prompt nach diesem Muster — passen Sie die eingeklammerten Stellen an:

> Sei mein Wochenrückblick-Assistent. Ich möchte, dass du folgende Arbeit erledigst und nichts darüber hinaus:
>
> **Lesen.** Schau in den Ordner `[Wochen-Notizen/]` und lies alle Dateien, die in dieser Woche (Montag bis heute) geändert wurden. Ignoriere ältere Dateien und Dateien, die nicht Markdown (`.md`) oder Text (`.txt`) sind.
>
> **Verdichten.** Schreibe eine Zusammenfassung mit genau drei Abschnitten:
>
> 1. *Was ist diese Woche passiert?* — vier bis sechs Sätze.
> 2. *Offene Punkte.* — als kurze Liste. Nur Punkte, die in den Notizen explizit stehen, keine Vermutungen.
> 3. *Vorschlag für nächste Woche.* — ein Absatz mit höchstens drei Sätzen, in dem du sagst, worauf ich in der kommenden Woche die Aufmerksamkeit legen sollte. Kennzeichne diesen Abschnitt ausdrücklich als Vorschlag, nicht als Faktenaussage.
>
> **Speichern.** Lege das Ergebnis als neue Datei unter `[rueckblicke/wochenrueckblick-<YYYY-MM-DD>.md]` an. Überschreibe nichts. Wenn die Datei schon existiert, hänge `-v2` an.
>
> **Nicht tun.** Ändere keine Datei im Quell-Ordner. Lösche nichts. Verschicke nichts. Verwende in der Zusammenfassung keine Namen von Personen aus den Notizen — ersetze sie durch ihre Rolle (z. B. "Projektleitung statt Lisa").
>
> **Rückmeldung.** Zeig mir am Ende den vollständigen Pfad der neuen Datei und die drei Abschnitte im Chat, damit ich sie prüfen kann.

Drücken Sie Senden. Cowork liest die Dateien, schreibt die Zusammenfassung, legt die neue Datei an. Wenn Sie etwas an der Zusammenfassung anpassen wollen, antworten Sie im selben Chat — Cowork bleibt in derselben Sitzung, kennt den Kontext und korrigiert.

### Schritt 3 — Den Prompt wiederverwendbar machen (5 Minuten)

Bis hierher haben Sie einen einmaligen Auftrag gebaut. Für einen **echten** Mini-Agenten brauchen Sie den gleichen Auftrag jede Woche, ohne dass Sie ihn neu formulieren. In Cowork geht das am einfachsten so:

- **Variante A — Prompt-Snippet im Markdown-Notiz-Ordner.** Legen Sie eine Datei `agenten/wochenrueckblick.md` an und speichern Sie den obigen Prompt darin. Jeden Freitag kopieren Sie ihn von dort in Cowork und senden ihn.
- **Variante B — Cowork-Skill.** Wenn Sie es sauberer wollen, bitten Sie Cowork einmalig: "Lege aus dem obigen Prompt einen wiederverwendbaren Skill unter dem Namen `wochenrueckblick` an. Wenn ich dich beim nächsten Mal auffordere, den Wochenrückblick zu machen, soll Cowork diesen Skill automatisch laden und die oben genannten Schritte abarbeiten." Cowork wird den Skill anlegen und bestätigen. Ab dem nächsten Mal genügt "mach mir den Wochenrückblick" als Prompt, der Skill übernimmt die Details.

Beide Wege funktionieren. Variante A ist transparenter — Sie sehen den Prompt jedes Mal — Variante B ist bequemer. Für den Einstieg empfehlen wir A für die ersten drei Wochen und dann den Umstieg auf B, sobald Sie wissen, dass der Prompt stabil ist.

---

Die Illustration [`illustrations/12-06-mein-erster-agent.png`](./illustrations/12-06-mein-erster-agent.png) zeigt dieselbe Idee auf einen Blick: der Cowork-Chat links, der Arbeitsordner in der Mitte, die vier Bausteine eines Agenten rechts.

---

## Warum das schon ein Agent ist

Dieser Wochenrückblick-Assistent ist klein, aber er erfüllt alle vier Kriterien aus Teil 01:

- **Planner:** Das Sprachmodell liest den Prompt und entscheidet, in welcher Reihenfolge es liest, verdichtet, speichert.
- **Tools:** Dateisystem-Zugriff (lesen und schreiben im gemounteten Ordner), geliefert durch Cowork selbst.
- **Memory:** Der Inhalt der aktuellen Sitzung, inklusive der Dateien, die er gerade gelesen hat.
- **Loop:** Eher schwach ausgeprägt — der Agent macht in der Regel einen Durchlauf und stoppt. Aber wenn eine Datei unerwartet ist oder fehlt, nimmt er eine zweite Runde, um das zu melden.

Im Vergleich zu den Claude-Code-Workflows aus Teil 04 fehlen: **Subagents** (hier wäre ein `notizen-leser` oder ein `anonymisierer` denkbar), **Hooks** (hier gäbe es einen Post-Write-Hook, der die Datei automatisch formatiert), **Slash-Commands** (in Cowork erfüllt die Skill-Variante B einen ähnlichen Zweck). Für den ersten Agenten brauchen Sie diese Feinheiten nicht. Die Kernidee — **ein klarer Auftrag, ein Ordner, ein Ausgabeformat, eine Regel "was nicht passieren darf"** — ist schon alles.

---

## Die drei typischen Stolperstellen

Wenn Ihr erster Lauf nicht wie erwartet läuft, liegt es fast immer an einem dieser drei Punkte:

**Stolperstelle 1 — Cowork sieht den Ordner nicht.** Der häufigste Fehler. Wenn Cowork im Chat sagt "Ich habe keinen Zugriff auf den Ordner", dann ist der Ordner nicht als Workspace gemountet. Klicken Sie im Sidebar auf das Ordner-Symbol, wählen Sie den richtigen Ordner aus, laden Sie neu. Dann den Prompt erneut senden.

**Stolperstelle 2 — Der Agent liest zu viele oder zu wenige Dateien.** Wenn er auch alte Dateien einbezieht, präzisieren Sie den Zeitraum ("nur Dateien, die in den letzten sieben Tagen geändert wurden"). Wenn er zu wenige sieht, prüfen Sie, ob die Datei-Änderungszeiten stimmen — manche Editoren setzen das Änderungsdatum neu, wenn Sie nur scrollen, andere nicht.

**Stolperstelle 3 — Die Zusammenfassung wird zu blumig.** Wenn der Agent anfängt zu interpretieren ("eine sehr spannende Woche mit vielen Fortschritten"), ergänzen Sie in Ihrem Prompt: "Neutrale, sachliche Sprache. Keine Wertungen. Keine Adjektive wie 'spannend', 'wichtig', 'erfolgreich'." Das wirkt Wunder.

Alle drei Stolperstellen sind **Prompt-Probleme**, nicht Agent-Probleme. Das ist eine gute Nachricht: Sie müssen keinen Code debuggen, nur den Text anpassen. Das ist der Grund, warum wir Cowork als ersten Einstieg empfehlen — die Lernkurve liegt vollständig im Formulieren.

---

## Was der nächste Schritt wäre

Wenn der Wochenrückblick-Assistent zwei oder drei Wochen stabil läuft, haben Sie zwei sinnvolle Erweiterungen zur Auswahl:

- **Spezialisierung vertiefen.** Mehr Prompts nach demselben Muster für andere wiederkehrende Aufgaben: Recherche-Notizen sortieren, Meeting-Mitschriften in ein einheitliches Format bringen, Lese-Notizen zu einem Thema bündeln. Jeder neue Auftrag braucht dieselben drei Notizzettel-Fragen (welcher Ordner, welches Ergebnis, was darf nicht passieren).
- **In die Claude-Code-Welt wechseln.** Sobald Sie mehr als zwei oder drei solcher Mini-Agenten haben, lohnt sich der Umstieg auf Teil 04. Dort werden die Prompts zu Subagents (die ihren eigenen Kontext bekommen), die Wiederholung zu Slash-Commands, und die Nebenläufer — Formatierung, Logging, Benachrichtigung — laufen automatisch über Hooks. Der Sprung ist dann kein Sprung ins Dunkle mehr, sondern ein bewusstes Upgrade, weil Ihre bestehenden Cowork-Prompts sich fast eins-zu-eins übersetzen lassen.

---

## Kernbotschaft

Ein erster Agent braucht keine Subagents, keine Hooks, keinen Slash-Command — nur einen klaren Prompt in Cowork mit drei Zutaten: einem definierten Quell-Ordner, einem definierten Ausgabeformat und einer ausdrücklichen "Das darfst du nicht"-Liste. Wenn dieser Mini-Agent eine Woche lang stabil läuft, sind Sie bereit für Teil 04 und den Umstieg auf die Claude-Code-Werkstatt. Die inhaltliche Denkweise ist in beiden Welten dieselbe, nur die Werkzeuge werden reicher.

---

## Nächste Schritte

- **[04 Claude Code Subagents und Hooks](./04%20Claude%20Code%20Subagents%20und%20Hooks.md)** — wenn Sie jetzt einen Schritt weitergehen wollen, ist dort die volle Werkstatt beschrieben.
- **[05 Praxis E-Mail-Triage und Meeting-Notes](./05%20Praxis%20E-Mail-Triage%20und%20Meeting-Notes.md)** — der erste echte Use-Case, in dem Ihr Mini-Agent-Prinzip auf einen konkreten Büroalltag angewandt wird.
- Zurück zur Übersicht: **[README](./README.md)**.
