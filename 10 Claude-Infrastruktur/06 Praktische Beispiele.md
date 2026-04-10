# 06 Praktische Beispiele

**Fünf End-to-End-Workflows vom Nicht-Coder bis zum Power-User.**

---

## Warum dieses Tutorial?

Die Teile 01 bis 05 haben Ihnen die drei Zugänge und ihre Werkzeuge erklärt. Jetzt wird es konkret. Dieses Tutorial zeigt fünf **vollständige Workflows**, die Sie selbst nachspielen können — vom kompletten Nicht-Coder bis zum Power-User, der alle drei Zugänge gleichzeitig nutzt. Jeder Workflow zeigt Ihnen: die Ausgangslage, den passenden Zugang, die konkreten Prompts, die Stolpersteine und das Ergebnis.

Ziel ist nicht, dass Sie am Ende alle fünf Workflows beherrschen — sondern dass Sie **zwei oder drei** davon tatsächlich an einem eigenen Fall nachbauen und dabei merken: Das funktioniert. Und zwar für mich.

**Was Sie nach diesem Tutorial wissen werden:**

- Wie ein Non-Coder-Workflow mit Cowork ganze Büro-Aufgaben erledigt.
- Wie ein Einsteiger-Workflow in Claude Code ein erstes eigenes Skript produziert.
- Wie ein Entwickler-Workflow Cowork, Claude Code und VS Code kombiniert.
- Wie Sie typische Stolpersteine erkennen und umgehen.

---

## Workflow 1 — Non-Coder: Download-Ordner aufräumen und als Bericht dokumentieren

**Zielgruppe:** Jeder. Keine Vorkenntnisse.
**Zugang:** Cowork in der Claude Desktop App.
**Dauer:** 10–15 Minuten.

**Ausgangslage:** Ihr Download-Ordner ist chaotisch. Hunderte Dateien quer durcheinander. Sie wollen Ordnung schaffen und am Ende einen kleinen Bericht darüber haben, was dort lag.

**Setup:**

Legen Sie zuerst einen neuen Ordner an (z. B. `~/Downloads-Cleanup`) und kopieren Sie den Inhalt Ihres Download-Ordners hinein — damit Cowork nicht am Original arbeitet. Dann mounten Sie diesen neuen Ordner in der Claude Desktop App (Einstellungen → Cowork → Ordner wählen).

**Prompt 1 — Bestandsaufnahme:**

```
Schau dir meinen gemounteten Ordner an. Zähle, wie viele Dateien
dort liegen, gruppiere sie nach Dateityp und Alter (älter als ein
Jahr, in den letzten 12 Monaten, in den letzten 30 Tagen) und
zeige mir eine Übersicht als Tabelle.
```

Claude durchsucht den Ordner, analysiert die Metadaten und liefert eine Tabelle. Sie sehen auf einen Blick, was Sie da eigentlich haben.

**Prompt 2 — Aufräumen:**

```
Organisiere alle Dateien in Unterordner nach Kategorie:
"Dokumente" (PDF, DOCX, TXT), "Bilder" (PNG, JPG, HEIC),
"Videos" (MP4, MOV), "Installer" (DMG, EXE, PKG),
"Archive" (ZIP, RAR, TAR) und "Sonstiges" für den Rest.
Lege die Unterordner an und verschiebe die Dateien hinein.
Lösche nichts.
```

Beobachten Sie, wie Claude die Unterordner erzeugt und die Dateien verschiebt. Keine einzige Zeile Code, kein Terminal, kein PowerShell. Alles im Chat.

**Prompt 3 — Bericht erstellen:**

```
Erstelle mir in diesem Ordner eine Datei namens aufraeumbericht.docx,
in der du in drei Abschnitten dokumentierst: (1) Wie der Ordner
vorher aussah (Zahlen aus der Übersicht oben), (2) was du getan hast,
(3) welche Unterordner nun existieren und wie viele Dateien jeweils
drin sind. Tonfall sachlich, auf Deutsch, eine Seite lang.
```

Claude greift auf den mitgelieferten `docx`-Skill zu und baut eine saubere Word-Datei mit Überschriften. Öffnen Sie die Datei mit Word oder LibreOffice — fertig.

**Was Sie lernen:**

- Cowork kann Metadaten erfassen und auswerten.
- Dateiverschiebungen sind ein Ein-Befehl-Job.
- Über den `docx`-Skill entsteht in Sekunden ein professionell formatierter Bericht.

**Typische Stolpersteine:**

- Sie mounten aus Versehen den **echten** Download-Ordner. Backup-Regel von Kapitel 02 beachten!
- Der Bericht wird zu lang, weil Sie es nicht eingeschränkt haben. Klare Längen-Vorgaben im Prompt helfen.
- Nach dem Aufräumen lassen sich Dateien in Spotlight oder der Windows-Suche nicht mehr wie gewohnt finden — weil sie jetzt in Unterordnern liegen.

---

## Workflow 2 — Non-Coder: PDF-Stapel zu Präsentation machen

**Zielgruppe:** Büro-Arbeit, Marketing, Beratung.
**Zugang:** Cowork in der Claude Desktop App.
**Dauer:** 20–30 Minuten.

**Ausgangslage:** Sie haben fünf PDF-Dokumente von einer Recherche (Studien, Artikel, Branchen-Reports). Sie sollen daraus eine Präsentation für ein internes Meeting bauen — 10 Slides, deutsch, mit den Kernbotschaften jeder Quelle.

**Setup:**

Legen Sie einen Ordner an, z. B. `~/meeting-praesentation`, und legen Sie die fünf PDFs hinein. Mounten Sie den Ordner in Cowork.

**Prompt 1 — PDFs lesen und zusammenfassen:**

```
Lies alle PDFs in diesem Ordner und erstelle für jede eine
Zusammenfassung als eigene Markdown-Datei. Pro Datei: Titel, Autor
falls erkennbar, Erscheinungsjahr, drei Kernaussagen, eine Zeile
Bewertung der Relevanz für das Thema "Digitalisierung im
Mittelstand". Die Markdown-Dateien sollen zusammenfassung-01.md
bis zusammenfassung-05.md heißen.
```

Claude nutzt den `pdf`-Skill für jede Datei, baut die fünf Zusammenfassungen, schreibt sie in den Ordner.

**Prompt 2 — Storyline bauen:**

```
Lies die fünf Zusammenfassungen, die du gerade erstellt hast, und
baue daraus eine Storyline für eine 10-Slide-Präsentation. Format:
eine Gliederung mit Slide-Titel und einem Satz pro Slide, was
darauf stehen soll. Die Slides sollen einen Bogen erzählen, nicht
nur die fünf PDFs nacheinander aufzählen.
```

Claude kondensiert die fünf Quellen zu einer Geschichte. Lesen Sie die Gliederung, korrigieren Sie per Chat, was Ihnen nicht passt. Iterieren Sie zwei- bis dreimal.

**Prompt 3 — Präsentation bauen:**

```
Erstelle auf Basis der finalen Gliederung eine PowerPoint-Datei
"digitalisierung-mittelstand.pptx" mit genau 10 Slides plus Titel-
und Schluss-Slide. Nutze ein ruhiges, professionelles Layout,
Titel plus Bullet-Points, kein Stock-Foto-Chaos. Eine Slide für
die Quellenangabe am Ende.
```

Claude greift auf den `pptx`-Skill zu, erzeugt die Präsentation. Öffnen Sie die Datei mit PowerPoint, Keynote oder LibreOffice Impress.

**Was Sie lernen:**

- Cowork kann PDFs im Batch verarbeiten, nicht nur einzeln.
- Der `pptx`-Skill liefert nutzbare Präsentationen, die Sie manuell nur noch verfeinern.
- Der Zwischenschritt „Storyline als Gliederung" ist der entscheidende Qualitätshebel — überspringen Sie ihn nicht.

**Typische Stolpersteine:**

- Wenn Sie direkt von „PDFs lesen" auf „Präsentation bauen" springen, bekommen Sie einen Brei statt einer Story.
- Claude vergisst manchmal, die Quellenangabe ans Ende zu setzen — im Prompt explizit anweisen.
- Sehr große PDFs (>100 Seiten) brauchen mehr Zeit und mehr Kontext-Fenster; im Zweifel mit Opus 4.6 arbeiten.

---

## Workflow 3 — Coding-Einsteiger: Erstes eigenes Skript mit Claude Code

**Zielgruppe:** Sie haben noch nie ein Python-Skript von Grund auf geschrieben, aber Sie kennen die Grundidee.
**Zugang:** Claude Code im Terminal.
**Dauer:** 30–45 Minuten.

**Ausgangslage:** Sie wollen ein Skript, das aus einer CSV-Datei mit Kundendaten pro Spalte die typische Statistik rausholt (Anzahl, leere Felder, häufigste Werte) und Ihnen das als Bericht ausgibt.

**Setup:**

1. Installieren Sie Claude Code (siehe Tutorial 04).
2. Legen Sie einen neuen Ordner an: `mkdir ~/csv-analyzer && cd ~/csv-analyzer`.
3. Starten Sie Claude Code: `claude`.
4. Erster Prompt: `/init` — Claude erzeugt eine CLAUDE.md für das noch leere Projekt.

**Prompt 1 — Anforderungen klären:**

```
Ich möchte ein einfaches Python-Skript bauen, das eine CSV-Datei
einliest und pro Spalte zeigt: Anzahl Werte, Anzahl leerer Felder,
die drei häufigsten Werte. Das Skript soll als
Kommandozeilen-Werkzeug aufrufbar sein: "python analyzer.py meine.csv".
Bevor du loslegst: frag mich nach Dingen, die du wissen musst.
```

Claude stellt Rückfragen (welche Python-Version? welche Encoding-Annahmen? Umgang mit sehr großen Dateien?). Beantworten Sie sie.

**Prompt 2 — Plan-Mode:**

```
/plan
Schlag mir einen Umsetzungsplan vor. Ich will ihn erst lesen,
bevor du Code schreibst.
```

Claude legt einen Schritt-für-Schritt-Plan vor: virtuelle Umgebung, `pandas` als Abhängigkeit, Haupt-Skript, einfache Tests, README. Sie diskutieren, korrigieren, einigen sich.

**Prompt 3 — Umsetzung:**

```
Gut, setz den Plan um. Zeig mir jeden Schritt als Diff, bevor
du ihn schreibst.
```

Claude erzeugt die Dateien Schritt für Schritt, Sie akzeptieren jede. Am Ende:

```
Führ das Skript mit einer Beispiel-CSV aus, die du dir selber
als Dummy baust (10 Zeilen reichen), damit wir sehen, ob es
tatsächlich läuft.
```

Claude baut eine kleine Test-CSV, ruft `python analyzer.py test.csv` auf, zeigt Ihnen die Ausgabe. Wenn etwas nicht läuft, diagnostiziert er den Fehler und schlägt eine Korrektur vor.

**Was Sie lernen:**

- Plan-Mode ist für Einsteiger goldwert — Sie sehen den Weg, bevor er gegangen wird.
- Das Schritt-für-Schritt-Diff gibt Ihnen Kontrolle und gleichzeitig die Chance, Code zu lesen und zu verstehen.
- Am Ende haben Sie ein lauffähiges Skript, das **Sie** bauen ließen — nicht eines, das jemand anders für Sie schrieb.

**Typische Stolpersteine:**

- Sie akzeptieren Diffs blind, ohne zu lesen. Widerstehen Sie der Versuchung — Sie lernen nichts dabei.
- Claude empfiehlt manchmal Pakete, die auf Ihrem System nicht installiert sind. Lassen Sie ihn die Installation mit erklären.
- Sie wechseln aus dem Plan-Mode raus, ohne dass der Plan fertig ist. Disziplin!

---

## Workflow 4 — Entwickler: Refactoring mit VS-Code-Integration

**Zielgruppe:** Sie arbeiten bereits an Code-Projekten und wollen die VS-Code-Integration produktiv nutzen.
**Zugang:** Claude Code in VS Code.
**Dauer:** 45–90 Minuten, je nach Projektgröße.

**Ausgangslage:** Ein Service in Ihrem Projekt hat über die Zeit zu viele Verantwortlichkeiten bekommen. Sie wollen ihn in drei kleinere Services aufteilen, ohne das Verhalten nach außen zu ändern.

**Setup:**

1. Saubere Git-Situation im Projekt: alles committet, gepusht, idealerweise ein neuer Branch `refactor/split-service`.
2. VS Code offen, Claude-Sidebar aktiv.
3. Die betroffene Datei im Editor offen.

**Prompt 1 — Analyse im Plan-Mode:**

Im Claude-Panel (VS Code):

```
/plan
Schau dir die aktuell offene Datei an. Identifiziere die verschiedenen
Verantwortlichkeiten und schlag einen Refactoring-Plan vor, der den
Service in drei kleinere aufteilt. Kriterien: Single Responsibility,
minimale Änderung an der öffentlichen API, keine Änderung am Verhalten.
```

Claude liest die Datei, zeigt Ihnen eine strukturierte Analyse und einen Plan.

**Prompt 2 — Verfeinern:**

Sie gehen den Plan durch, markieren Stellen, die Sie unklar finden, und fragen nach. Claude passt an. Nach zwei bis drei Runden haben Sie einen Plan, mit dem Sie einverstanden sind.

**Prompt 3 — Umsetzung mit Zwischen-Commits:**

```
Setz den Plan Schritt für Schritt um. Pro Schritt: neue Datei anlegen,
Code verschieben, Tests anpassen oder ergänzen, Tests ausführen,
und erst wenn alles grün ist, einen Commit mit einer aussagekräftigen
Conventional-Commit-Nachricht. Zeig mir jeden Diff, bevor du ihn
anwendest.
```

Im Editor sehen Sie jetzt Inline-Diffs. Akzeptieren Sie Block für Block, beobachten Sie die Tests im integrierten Terminal, akzeptieren Sie die Commits. Bei Problemen unterbrechen Sie und fragen nach.

**Prompt 4 — Review:**

```
Wir sind durch. Gib mir eine Zusammenfassung dessen, was sich jetzt
in der öffentlichen API geändert hat (idealerweise: nichts). Schlag
außerdem eine Pull-Request-Beschreibung vor, die das Refactoring für
Kolleg:innen erklärt.
```

Claude liefert beides. Sie kopieren die PR-Beschreibung nach GitHub oder Ihrer Forge.

**Was Sie lernen:**

- Inline-Diffs sind der Killer-Mehrwert für Refactorings — Sie sehen jede Änderung.
- Plan-Mode plus Schritt-für-Schritt-Umsetzung ergibt eine Sicherheit, die pures „Auto-Mode" nicht hat.
- Claude ist ein guter PR-Schreiber, wenn Sie ihm sagen, für wen der Text sein soll.

**Typische Stolpersteine:**

- Sie starten ohne sauberen Git-Zustand. Wenn etwas schiefgeht, haben Sie keinen Rückweg.
- Sie akzeptieren alle Diffs ohne Lesen. Bei Refactorings ist das riskant.
- Sie lassen Claude zu viele Schritte in einen Commit packen. Kleine Commits sind Gold wert, gerade beim Refactoring.

---

## Workflow 5 — Power-User: Alles zusammen (Recherche → Code → Dokumentation)

**Zielgruppe:** Fortgeschrittene, die alle drei Zugänge in einem Tag kombinieren wollen.
**Zugang:** Cowork + Claude Code Terminal + VS Code parallel.
**Dauer:** 2–4 Stunden.

**Ausgangslage:** Sie wollen für ein internes Whitepaper recherchieren, dann einen Prototyp bauen, der die Idee demonstriert, und am Ende ein Dokument schreiben, das Recherche, Prototyp und Erkenntnisse zusammenbringt.

**Phase 1 — Recherche in Cowork:**

Legen Sie einen Projektordner an: `~/whitepaper-projekt`. Mounten Sie ihn in Cowork.

```
Recherchiere das Thema "Retrieval Augmented Generation für den
Mittelstand" im Web. Finde die fünf relevantesten Quellen der
letzten 12 Monate, speichere die Links in quellen.md, und erstelle
pro Quelle eine 200-Wörter-Zusammenfassung als eigene Markdown-
Datei unter recherche/01.md bis recherche/05.md.
```

Cowork nutzt die Web-Such-Tools, baut die Struktur, schreibt die Dateien.

**Phase 2 — Prototyp in Claude Code Terminal:**

Wechseln Sie in das Terminal: `cd ~/whitepaper-projekt && claude`.

```
/init
```

Claude Code erzeugt eine CLAUDE.md für das Projekt.

```
/plan
Bau mir einen minimalen Python-Prototypen, der ein einfaches
RAG-System demonstriert: Eingabe ein Verzeichnis mit Markdown-
Dateien, Ausgabe ein CLI, das Fragen beantwortet, indem es
die passenden Chunks aus den Markdowns findet. Nutze sentence-
transformers und faiss, nichts Exotisches. Keine API-Keys
erforderlich, alles lokal.
```

Plan durchgehen, verfeinern, umsetzen. Claude Code baut das Skript, installiert Dependencies, testet es mit den Recherche-Markdowns aus Phase 1 als Input.

**Phase 3 — Dokumentation in VS Code:**

Wechseln Sie in VS Code mit dem Projekt-Ordner. Öffnen Sie ein leeres `whitepaper.md`, aktivieren Sie die Claude-Sidebar.

```
Schau dir den Projekt-Ordner an. Unter recherche/ findest du die
Quellen, unter src/ den Prototypen. Schreib mir ein strukturiertes
Whitepaper in whitepaper.md mit folgendem Aufbau: (1) Einleitung,
(2) Stand der Technik (aus den Quellen), (3) Unser Prototyp
(Architektur und Ergebnisse), (4) Erkenntnisse für den Mittelstand,
(5) Quellenliste. Ton: sachlich, gut lesbar, ca. 2500 Wörter.
```

Claude liest alle Dateien, die er braucht, und baut das Whitepaper. Sie gehen Abschnitt für Abschnitt durch, akzeptieren Diffs, fordern Überarbeitungen an.

**Phase 4 — Finishing:**

Zurück in Cowork: Bauen Sie aus dem Markdown eine Word-Version und ein PDF.

```
Konvertiere whitepaper.md in eine Word-Datei whitepaper.docx und
zusätzlich in ein PDF whitepaper.pdf. Nutze für die Word-Datei
ein schlichtes, professionelles Layout mit Inhaltsverzeichnis.
```

Der `docx`-Skill und der `pdf`-Skill übernehmen.

**Was Sie lernen:**

- Jeder der drei Zugänge hat seine Stärke. Wer sie kombiniert, multipliziert die Produktivität.
- Der gemeinsame Projektordner ist das Bindeglied: Cowork, Claude Code Terminal und VS Code arbeiten alle auf demselben Dateisystem.
- „Recherche → Prototyp → Dokumentation" ist ein Muster, das sich auf viele Themen übertragen lässt.

**Typische Stolpersteine:**

- Sie vergessen, zwischen Cowork und Claude Code Terminal den Mount/das Verzeichnis abzugleichen. Dann arbeiten Sie auf zwei verschiedenen Kopien.
- Sie springen zwischen Zugängen, ohne die Zwischen­ergebnisse zu committen. Git ist auch hier Ihr Freund.
- Die Gesamtaufgabe wird zu groß. Zerlegen Sie sie bewusst in die vier Phasen und legen Sie bei Phasen­wechsel kurze Pausen ein.

---

## Was diese Workflows gemeinsam haben

Egal ob Non-Coder-Ordneraufräumer oder Power-User-Whitepaper: Vier Prinzipien ziehen sich durch alle fünf Workflows:

1. **Klein anfangen.** Jeder Workflow beginnt mit einer Bestandsaufnahme oder einem Plan, nie direkt mit dem großen Schlag.
2. **Plan vor Ausführung.** Plan-Mode, Storyline-Zwischenschritte, Rückfragen sind die Stellen, an denen gute Ergebnisse entstehen.
3. **Diffs lesen.** Auch wenn Sie nicht jeder Zeile bis ins Detail folgen: Sie bleiben im Bild, wenn Sie den Überblick haben.
4. **Dateien sind das gemeinsame Medium.** Cowork, Claude Code Terminal und VS Code arbeiten alle auf dem Dateisystem. Das ist die Architektur — nutzen Sie sie.

---

## Zusammenfassung in 60 Sekunden

Fünf konkrete Workflows zeigen, wie die drei Claude-Zugänge im Alltag funktionieren. Non-Coder können Ordner aufräumen und Präsentationen bauen — nur mit Cowork und den mitgelieferten Skills. Einsteiger schreiben ihr erstes Python-Skript mit Claude Code im Terminal, begleitet vom Plan-Mode und Schritt-für-Schritt-Diffs. Entwickler refaktorieren ganze Services in VS Code mit visuellen Diffs und Zwischen-Commits. Power-User kombinieren alle drei Zugänge in einem Projekt: Recherche in Cowork, Prototyp im Terminal, Dokumentation im Editor, Finishing wieder in Cowork. Der gemeinsame Nenner ist immer: klein anfangen, Plan vor Ausführung, Diffs lesen, Dateien als gemeinsames Medium.

---

## Nächste Schritte

- **[07 Troubleshooting Kosten und FAQ](./07%20Troubleshooting%20Kosten%20und%20FAQ.md)** — was tun, wenn etwas nicht läuft, und wie viel kosten die drei Zugänge wirklich?
- Querverweis: **Kapitel 01 (Prompt Engineering Text)** — die Prompts aus diesem Kapitel lassen sich mit den 6 Bausteinen aus Kapitel 01 noch deutlich verschärfen.
- Querverweis: **Kapitel 08 (Prompt-Bibliothek)** — viele der hier gezeigten Muster gibt es in Kapitel 08 als Copy-paste-Vorlagen.
