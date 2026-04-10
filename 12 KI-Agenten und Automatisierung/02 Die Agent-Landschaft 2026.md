# 02 Die Agent-Landschaft 2026

**Welche Werkzeuge es gibt — und warum wir uns auf wenige konzentrieren.**

---

## Warum dieses Tutorial?

Wenn Sie „AI Agent Framework" googeln, bekommen Sie im April 2026 mehrere Dutzend Ergebnisse auf die erste Seite. LangChain, LangGraph, AutoGen, CrewAI, Smolagents, Claude Code, OpenAI Agents SDK, Google ADK, n8n, Make, Zapier, Microsoft Copilot Studio — jedes Werkzeug nennt sich „Agent-Plattform", jedes behauptet, die beste Lösung zu sein. Die Wahrheit ist: Die meisten dieser Werkzeuge sind für Entwicklerinnen und Entwickler gebaut. Für jemanden, der Agenten **einsetzen**, nicht **programmieren** will, ist das Feld deutlich kleiner.

Dieses Tutorial gibt Ihnen eine nüchterne Landkarte. Am Ende wissen Sie, welche Werkzeuge für Nicht-Entwickler infrage kommen, warum dieses Kapitel auf **Claude Code**, **Cowork** und **MCP** setzt, und in welchen Fällen sich ein Blick auf n8n oder Make lohnt. Sie werden nicht jedes Tool im Detail kennen — das wäre 2027 ohnehin wieder überholt. Aber Sie werden die Kategorien auseinanderhalten können.

**Was Sie nach diesem Tutorial wissen werden:**

- Die vier Kategorien von Agent-Werkzeugen 2026.
- Welche Werkzeuge für Nicht-Entwickler geeignet sind — und welche (vorerst) nicht.
- Warum wir in diesem Kapitel auf die Claude-Welt setzen.
- Wann ein visuelles Workflow-Tool wie n8n die bessere Wahl ist.
- Eine einfache Entscheidungshilfe: „Welches Werkzeug für meine Aufgabe?"

---

## Die vier Kategorien

Wenn Sie einmal die Namen beiseitelassen und sich anschauen, **was** ein Werkzeug macht, dann fallen alle Agent-Tools 2026 in eine von vier Kategorien.

### Kategorie 1: Chat-App mit Agent-Fähigkeiten

Das sind die vertrauten Chat-Oberflächen — **claude.ai**, **ChatGPT**, **Gemini**, **Perplexity** — die inzwischen nicht mehr nur antworten, sondern auch selbst Schritte ausführen können. Web-Suche, Bildgenerierung, Code-Ausführung in einer Sandbox, seit Kurzem auch Datei-Zugriff und einfache Computer-Use-Funktionen.

Für einen großen Teil der Aufgaben, die Menschen mit „Agenten" meinen, reichen diese Apps bereits aus. Sie schreiben einen Prompt, das System erledigt mehrere Schritte, Sie bekommen ein Ergebnis. Der Unterschied zum „echten" Agenten aus Teil 01 ist vor allem: Die Schleife ist kürzer, die Autonomie kleiner, die Beaufsichtigung höher. Das ist für die meisten Anwender ein **Vorteil**, kein Nachteil.

**Wann diese Kategorie reicht:** Einzelne Recherche, Texterstellung mit Recherche im Hintergrund, einfache Datenanalyse, Dokumentenaufbereitung. Alles, was in zwei bis drei Schritten fertig ist und wo Sie selbst am Steuer bleiben wollen.

**Wann nicht:** Wiederkehrende Aufgaben (täglich, wöchentlich), Aufgaben mit Zugriff auf lokale Dateien in größerem Umfang, Aufgaben mit vielen Zwischenschritten.

### Kategorie 2: Desktop-Agent mit Dateizugriff

Hier liegt der Sprung. **Claude Cowork** in der Desktop-App ist das prominenteste Beispiel; **Claude Code** im Terminal ist der zweite Zugang. Beide haben Zugriff auf einen echten Arbeitsordner auf Ihrem Rechner, auf eine Shell, auf MCP-Server und auf Skills. Das macht sie zu echten Agenten im Sinne von Teil 01: Sie bekommen ein Ziel, sie planen, sie führen aus, sie schauen sich das Ergebnis an, und sie machen weiter.

Kapitel 10 hat beide ausführlich behandelt. An diesem Punkt sollten Sie wissen, dass **Cowork** eher für nicht-technische Aufgaben (Dateien organisieren, Dokumente erstellen, Datenanalyse, Präsentationen, Recherche in Dokumenten) gemacht ist, während **Claude Code** seine Stärke bei Code-Projekten entfaltet, aber auch für viele nicht-technische Workflows taugt, sobald man sich an das Terminal gewöhnt hat.

Für dieses Kapitel sind Cowork und Claude Code die **Hauptwerkzeuge**. Alles, was wir in den Praxis-Teilen 05 und 06 bauen, läuft in einem von beiden.

**Wann diese Kategorie die richtige ist:** Sobald Sie echten Dateizugriff brauchen, wiederkehrende Aufgaben in Ihrem Arbeitsumfeld automatisieren wollen, oder komplexere Pipelines bauen, die mehrere Tools koordinieren (z. B. Drive + Excel + Word + Slack).

### Kategorie 3: Visuelle Workflow-Tools

**n8n**, **Make** (ehemals Integromat) und **Zapier** sind keine „KI-Tools" im engen Sinn, sondern **Workflow-Automatisierer**. Sie bauen sich Ihren Ablauf mit Mausklicks zusammen: „Wenn eine neue E-Mail mit 'Rechnung' im Betreff ankommt, dann packe den Anhang in Drive-Ordner X, dann schreibe eine Zeile in Google Sheet Y, dann benachrichtige Slack-Channel Z." Viele dieser Tools haben inzwischen auch KI-Bausteine integriert — einen „OpenAI-Knoten" oder einen „Anthropic-Knoten", den Sie in den Ablauf einbauen können.

Das Ergebnis ist kein Agent im klassischen Sinn. Es ist ein fester Ablauf, den Sie vorab zeichnen. Der KI-Schritt in der Mitte ist nur ein Knoten unter vielen. Der Vorteil: Sie haben volle Kontrolle, volle Nachvollziehbarkeit, klare Fehlerbehandlung. Der Nachteil: Sie müssen jeden Schritt im Voraus wissen — die Autonomie eines echten Agenten fehlt.

**Wann n8n oder Make passt:**

- Wenn Sie **feste, vorhersehbare Abläufe** automatisieren wollen, die keine echte Entscheidung des Modells brauchen.
- Wenn Sie **viele verschiedene Dienste** miteinander verbinden wollen und es für diese Dienste fertige Knoten gibt (was in beiden Tools Hunderte sind).
- Wenn Sie **zuverlässige, dauerhafte Cron-artige Jobs** brauchen, die auch laufen, wenn Sie nicht am Rechner sitzen.
- Wenn Ihre Organisation bereits eine dieser Plattformen lizenziert hat.

**Wann eher nicht:**

- Wenn die Aufgabe echte Planung braucht und die nächsten Schritte von den bisherigen abhängen.
- Wenn Sie nicht jeden Schritt im Voraus zeichnen wollen.
- Wenn Sie hauptsächlich mit Dokumenten arbeiten und keinen komplexen Dienst-Zoo verbinden.

**Ehrliche Bewertung:** Für Ralfs Zielgruppe (Content-Arbeit, Dokumenten-Workflows, Datenanalyse, Recherche) gewinnt Claude Cowork heute in den meisten Fällen. Für Unternehmen mit vielen verbundenen SaaS-Diensten, die wiederkehrende Datenflüsse brauchen, ist n8n ein starkes Werkzeug. Beides hat seinen Platz — wir kommen zu n8n zurück, wenn es für eine konkrete Aufgabe die bessere Wahl ist.

### Kategorie 4: Developer-Frameworks

**LangChain**, **LangGraph**, **AutoGen**, **CrewAI**, **Smolagents**, **OpenAI Agents SDK**, **Google Agent Development Kit** — das sind Programmier-Bibliotheken für Leute, die Agenten **selbst bauen**. Sie bekommen kein Benutzer-Interface, sondern ein Set an Funktionen in Python oder TypeScript. Die Zielgruppe sind Softwareentwickler und Data Engineers.

Diese Kategorie lassen wir in diesem Kapitel bewusst außen vor. Nicht, weil sie nicht wichtig ist — sie ist für die tiefe Industrie-Adoption entscheidend — sondern, weil sie für Nicht-Entwickler nicht zugänglich ist. Wenn Sie später einmal eigene Python-Agenten bauen wollen, ist **LangGraph** 2026 der populärste Einstieg, und das **Claude Agent SDK** ist die dünnste, am wenigsten magische Bibliothek direkt von Anthropic. Für dieses Kapitel wäre das der falsche Abzweig.

---

## ChatGPT-Welt: GPTs, Tasks, Operator — eine faire Einordnung

Ein großer Teil der Leserinnen und Leser dieses Kapitels kommt nicht aus dem Claude-Ökosystem, sondern hat ChatGPT seit Monaten im Einsatz — für Texte, Recherche, einfache Dateianalysen. Für diese Gruppe ist das Wort „Agent" oft schon aus der ChatGPT-Welt vertraut, und es wäre unehrlich, diese Welt in einem Halbsatz abzufertigen. Deshalb ein eigener Abschnitt.

**Custom GPTs mit Actions.** Ein **Custom GPT** ist ein vorkonfigurierter Chat mit eigener Systemprompt, einer Wissens-Bibliothek und optional **Actions** — kleinen API-Aufrufen, die der GPT bei Bedarf auslöst. Wenn Sie einen GPT mit einer Action für Ihre Wetter-API, Ihre CRM-Datenbank oder Ihren Kalender bauen, erhalten Sie einen kleinen, wiederverwendbaren Mini-Agenten, den Sie auch mit anderen teilen können. Die Logik ist konzeptionell eng verwandt mit Claude Projects und mit den Subagents aus Teil 04 — nicht identisch, aber vergleichbar.

*Stärken:* sehr niedrige Einstiegshürde, keine eigene Infrastruktur, einmal gebaut und im Team oder öffentlich nutzbar, solide Persona-Logik.

*Schwächen:* an das ChatGPT-Konto gebunden, Dateizugriff auf den Wissens-Ordner beschränkt, komplexere Mehrschritt-Workflows mit eigener Planung sind schwieriger zu bauen als in Claude Code.

**ChatGPT Tasks.** Seit Anfang 2025 kennt ChatGPT **geplante Aufgaben** — Sie können ChatGPT beauftragen, etwas zu einer bestimmten Zeit zu tun oder zu wiederholen („Jeden Morgen um 8 Uhr eine Übersicht meiner Termine in der Antwort schicken"). Das ist für wiederkehrende, einfache Informationsaufgaben praktisch und ersetzt für viele kleine Anwendungsfälle den `schedule`-Skill, den wir in Kapitel 10 und in Teil 06 dieses Kapitels nutzen.

**ChatGPT Operator.** Operator ist der Versuch, einen Browser-Agenten in die ChatGPT-Welt zu bringen: Das System steuert einen eigenen Browser, klickt durch Oberflächen, füllt Formulare aus. Für Aufgaben, die außerhalb eigener Dateien stattfinden (Buchungsseiten, Behörden-Portale, Web-Formulare ohne API), ist das der passendere Werkzeugtyp als alles, was dieses Kapitel zeigt. Claude hat mit **Claude in Chrome** einen inhaltlich ähnlichen Weg — auch das ist in diesem Kapitel nicht unser Schwerpunkt, aber es existiert parallel.

**Wann die ChatGPT-Werkzeuge passen.** Wenn Sie ChatGPT-Plus ohnehin zahlen, wenn Ihre Automatisierung eine vorkonfigurierte Persona mit ein, zwei externen Abfragen sein soll, oder wenn Sie regelmäßige, einfache Erinnerungen brauchen, dann sind Custom GPTs und Tasks ein sauberer Einstieg ohne Umweg über ein neues Ökosystem. Wenn Ihr Ziel darin besteht, einen Browser halbautomatisch bedienen zu lassen, ist Operator das passendere Werkzeug als ein Claude-Code-Workflow.

**Wann dieses Kapitel für Sie passt.** Sobald Sie **wiederkehrende Dateiarbeit** in einem lokalen Ordner automatisieren, **mehrere Subagents** mit unterschiedlichen Zuständigkeiten koordinieren, **eigene Slash-Commands** als Workflow-Rezepte ablegen oder **Hooks** als Automatisierungs-Auslöser nutzen wollen, gewinnt die Claude-Welt an Ausdrucksstärke. Und die Kernkonzepte (Persona ≈ Subagent-Systemprompt, Action ≈ MCP-Tool, Wissen ≈ Projektordner, Tasks ≈ schedule-Skill) lassen sich fast immer von der einen Welt in die andere übersetzen. Wer also aus ChatGPT kommt, muss nicht bei Null anfangen — die Begriffe ändern sich, die Ideen weniger.

---

## Claude Projects — der niedrigschwellige Einstieg in der Claude-Welt

Bevor Sie zu Cowork oder Claude Code greifen, lohnt ein Blick auf eine Zwischenstufe, die dieses Kapitel an anderer Stelle nur am Rand erwähnt: **Claude Projects** in der Claude-Web-App und in der Mobile-App. Ein Project ist im Kern eine wiederverwendbare Persona mit einem eigenen **Wissens-Ordner** — Dateien, die Claude bei jedem Gespräch in diesem Project automatisch mitliest, ohne dass Sie sie jedes Mal hochladen müssen. Dazu kommt eine projektweite Systemprompt, in der Sie Stil, Rolle und Regeln hinterlegen, die für alle Gespräche im Project gelten.

Claude Projects sind **kein voller Agent** im Sinne von Teil 01. Sie haben keinen Loop, keinen automatischen Tool-Aufruf über externe Dienste hinweg, keine Schleifen, die sich selbst weiterbringen. Aber sie decken einen erstaunlich großen Teil der Aufgaben ab, die viele Nutzerinnen und Nutzer zunächst meinen, wenn sie „Agent" sagen — vor allem dann, wenn die Aufgabe keinen Zugriff auf aktive Systeme braucht und im Wesentlichen aus „immer wieder dieselbe Art Frage, auf dieselben Dokumente, in demselben Stil" besteht.

**Wann Claude Projects reichen:** Sie haben eine feste Dokumenten-Sammlung (z. B. Produktdokumentation, interne Richtlinien, Rechercheberichte) und wollen sie immer wieder befragen. Sie wollen eine Persona („Meine Fachlektorin für Wissenschafts­kommunikation"), die Sie täglich konsultieren. Sie arbeiten überwiegend mobil oder in der Web-App und wollen ohne Desktop-App auskommen. In all diesen Fällen ist Claude Projects der direkte, niedrigschwellige Einstieg — und in den meisten Organisationen bereits Teil des bestehenden Claude-Abos.

**Wann Claude Projects nicht reichen:** Sobald Sie **lokale Datei-Schreibrechte** brauchen (Cowork), **Shell-Befehle** ausführen wollen (Claude Code), **automatisch ausgelöste Läufe** planen (Cowork + schedule-Skill), **mehrere Subagents** mit unterschiedlichen Zuständigkeiten koordinieren (Claude Code) oder **externe Dienste über MCP** anbinden (Cowork/Claude Code). Das ist der Moment, in dem Sie von Projects nach Cowork oder Claude Code wechseln.

**Das nützliche mentale Modell:** Claude Projects ist für den Übergang gemacht. Viele Nutzerinnen und Nutzer starten dort, weil es ohne Installation funktioniert, bleiben drei bis vier Wochen, merken an einer konkreten Aufgabe („ich will, dass das Ergebnis als Word-Datei in meinem Arbeitsordner landet") die Grenze, und wechseln dann bewusst nach Cowork. Dieser Weg ist gut, nicht schlecht — er ist sogar der empfohlene. Dieses Kapitel setzt bei Cowork und Claude Code an, weil das unsere Zielplattform ist. Wenn Sie vorher eine Weile in Projects leben wollen, ist das kein Umweg.

---

## Warum dieses Kapitel im Claude-Ökosystem bleibt

Vorab eine Offenlegung: Dieses Repo begleitet Sie seit Kapitel 00 im Claude-Ökosystem, und Kapitel 12 bleibt diesem Pfad treu. Das ist eine didaktische Entscheidung, keine Behauptung, dass andere Werkzeuge schlechter seien. Sie werden auf dem Weg mehrfach lesen, wo die Grenzen dieser Entscheidung liegen.

Vier Gründe haben den Ausschlag gegeben:

**Konsistenz mit dem bisherigen Kursverlauf.** Kapitel 10 hat die Claude-Infrastruktur eingeführt, Kapitel 11 die Datenanalyse darauf aufgebaut. Wenn Kapitel 12 in eine ganz andere Werkzeug-Welt springt, wird der Kurs für Einsteigerinnen und Einsteiger schwerer zu folgen. Ein durchgehender Werkzeugkasten spart Vokabular und Einrichtungszeit.

**Lokaler Dateizugriff.** Cowork und Claude Code arbeiten direkt auf dem gemounteten Ordner Ihres Rechners. Datei-Inhalte bleiben zunächst lokal — was über Remote-Connectors wie Gmail oder Google Drive in die Cloud wandert, sehen wir in Teil 03 gesondert. Für Dokumentenworkflows, bei denen die Dateien gar nicht erst hochgeladen werden müssen, ist das ein praktischer Vorteil. Für DSGVO-Fragen ersetzt dieser Umstand aber keine konkrete Bewertung; siehe Kapitel 14 Teil 02.

**Echte Planungs-Schleifen.** In Claude Code plant das Modell selbst, welche Werkzeuge als nächstes dran sind. In einem n8n- oder Make-Flow zeichnen Sie die Schritte vorab. Beide Ansätze haben ihren Platz — für dieses Kapitel passt der planende Ansatz besser zur Agenten-Definition aus Teil 01.

**MCP als offener Standard.** Der Model Context Protocol-Standard, den wir in Teil 03 vertiefen, verbreitet sich 2026 über das Claude-Ökosystem hinaus. Auch n8n, Make und andere bauen MCP-Unterstützung ein. Wer MCP lernt, lernt deshalb keine reine Anthropic-Technik, sondern eine Schnittstelle, die zunehmend portabel ist.

**Was das nicht heißt.** Es heißt nicht, dass n8n, Make, OpenAI-GPTs oder LangChain schlechtere Werkzeuge wären. Für viele Aufgaben — vor allem für feste Abläufe zwischen vielen SaaS-Diensten oder für programmierte Agenten im Team — sind sie die bessere Wahl. Wenn Sie nach diesem Kapitel merken, dass Ihre Aufgabe besser bei n8n aufgehoben ist, ist das kein Scheitern, sondern der Zweck einer ehrlichen Landkarte.

---

## Entscheidungshilfe: Welches Werkzeug für meine Aufgabe?

Hier eine schnelle Orientierung — nicht als dogmatisches Regelwerk, sondern als Startpunkt:

**„Ich will einmal eine Rechercheaufgabe erledigt haben."**

→ **claude.ai** oder **ChatGPT** mit Browsing. Kategorie 1 reicht. Kein Agent nötig.

**„Ich will Dateien in meinem Arbeitsordner regelmäßig organisieren oder auswerten."**

→ **Claude Cowork** (Desktop-App). Kategorie 2. Direkter Dateizugriff, keine Cloud-Zwischenschritte.

**„Ich will einen Monatsreport aus mehreren Datenquellen automatisch bauen."**

→ **Claude Code** mit passenden MCPs oder **Cowork** mit xlsx-Skill. Siehe Teil 06. Kategorie 2.

**„Ich will, dass eingehende Mails automatisch in Drive-Ordner sortiert und an den richtigen Slack-Channel weitergeleitet werden, 24/7."**

→ Hier wird es interessant. Zwei Varianten kommen infrage:

- **Cowork + Schedule-Skill** — wenn der Job einmal am Tag laufen darf und Sie Ihren Rechner ohnehin anhaben. Einfacher einzurichten.
- **n8n oder Make** — wenn der Job **sofort** bei jedem eingehenden Mail laufen muss und das System **nie** offline sein darf. Diese Tools laufen in der Cloud und reagieren auf Webhook-Trigger.

**„Ich will ein Refactoring in meinem Code-Projekt durchführen lassen."**

→ **Claude Code** im Terminal oder in VS Code. Kategorie 2. Keine Alternative schlägt Claude Code für diese Aufgabe.

**„Ich will einen Chatbot für meine Kundinnen und Kunden bauen, den sie auf meiner Website nutzen können."**

→ Keine dieser Optionen direkt. Sie brauchen einen **Hosting-Layer** (eigenes Web-Frontend, Claude API im Backend). Das ist Entwickler-Territorium. Dieses Kapitel hilft Ihnen nicht, so etwas zu bauen, aber es hilft Ihnen, es von einem Dienstleister zu beauftragen und die Struktur zu verstehen.

**„Ich will eine wiederverwendbare Persona bauen, die im Team alle nutzen können."**

→ **Claude Projects** (in der Claude App) oder **Custom GPTs** (wenn das Team auf ChatGPT ist). Kapitel 03 hat die Logik behandelt. Für das Team-Setup ist eher Kapitel 15 zuständig.

---

## Was Sie für den Rest dieses Kapitels brauchen

Der Rest des Kapitels setzt voraus:

- **Claude Desktop App installiert** und im Cowork-Modus lauffähig, mit mindestens einem Arbeitsordner gemountet. (Kapitel 10 Teil 02)
- **Claude Code installiert** (npm oder Homebrew) und in einem Test-Ordner mit `claude` gestartet. (Kapitel 10 Teil 04)
- **Mindestens einen MCP verbunden** — Google Drive, Gmail oder Slack genügt. (Kapitel 10 Teil 03)

Wenn eines davon fehlt, springen Sie kurz zurück und holen es nach. Es lohnt sich — ohne diese Grundlagen sind die Praxis-Teile 05 und 06 schwer nachvollziehbar.

---

## Stärken und Schwächen der gewählten Werkzeuge

**Claude Cowork:**

- Stark bei: Dokument-Workflows, Datenanalyse, Recherche in Dateien, allem, was in einem Arbeitsordner passiert.
- Schwach bei: Unbeaufsichtigten Dauerläufen, echten Cron-Jobs, Integrationen in Firmen-SaaS-Zoos.

**Claude Code:**

- Stark bei: Code-Projekten, wiederkehrenden Aufgaben in definierten Projektordnern, Subagents und Hooks, mehrstufigen technischen Workflows.
- Schwach bei: Anfängern mit Terminal-Angst — die Lernkurve ist höher als bei Cowork. Cowork ist oft der bessere Einstieg, Claude Code das Werkzeug, wenn Sie Feuer gefangen haben.

**MCP-Server:**

- Stark bei: Wiederverwendbaren Anbindungen, die in Cowork **und** Claude Code funktionieren. Ein einmal eingerichteter Slack-MCP spart Ihnen beim nächsten Projekt Zeit.
- Schwach bei: Qualität schwankt zwischen den Servern. Die offiziellen sind gut, Community-MCPs sind Lotterie — mehr dazu in Teil 03.

---

## Kernbotschaft

Die Agent-Landschaft 2026 zerfällt in vier Kategorien: **Chat-Apps** (Einmal-Aufgaben), **Desktop-Agenten wie Cowork und Claude Code** (wiederkehrende Datei-Arbeit), **visuelle Workflow-Tools wie n8n oder Make** (feste 24/7-Abläufe zwischen Diensten) und **Developer-Frameworks wie LangGraph** (für Entwickler). Dieses Kapitel bleibt in der Claude-Welt — als didaktische Entscheidung, nicht als Werturteil gegen die anderen. Die ChatGPT-Welt mit GPTs, Tasks und Operator ist ein legitimer Parallelweg, besonders wenn Sie dort schon zu Hause sind.

---

## Nächste Schritte

- **[03 MCP verstehen](./03%20MCP%20verstehen.md)** — der offene Standard, der Agenten ihre Werkzeuge gibt. Das Herzstück der Claude-Agent-Welt.
- Zurück zur Übersicht: **[README](./README.md)**.
- Querverweis: **Kapitel 10 Teil 01 (Die drei Zugänge im Überblick)** hilft, wenn Sie zwischen Cowork und Claude Code noch unsicher sind.
