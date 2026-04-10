# 05 Praxis — E-Mail-Triage und Meeting-Notes

**Zwei Use-Cases Schritt für Schritt: vom Subagent-Entwurf bis zum laufenden Workflow.**

---

## Warum dieses Tutorial?

Die letzten vier Teile waren Theorie und Werkzeug. Dieses Tutorial ist Handwerk. Wir bauen zwei vollständige Automatisierungen, die Sie unmittelbar übernehmen oder nachbauen können. Beide richten sich an typische Büro-Alltagsaufgaben, die sich fast jede Woche wiederholen: **E-Mail-Triage** und **Meeting-Nachbereitung**.

Der Schwerpunkt liegt auf **fertigen Vorlagen**, nicht auf großer Theorie. Sie bekommen die Subagent-Dateien, die Slash-Commands und die nötigen MCP-Voraussetzungen. Nichts davon ist Raketentechnik. Wenn Sie Kapitel 10 durchhaben und die Teile 01 bis 04 dieses Kapitels gelesen haben, schaffen Sie beide Workflows an einem Nachmittag.

**Was Sie nach diesem Tutorial wissen werden:**

- Wie Sie einen fünfstufigen E-Mail-Triage-Workflow aufsetzen, der Gmail liest und Entwürfe vorbereitet.
- Wie Sie Meeting-Transkripte zu sauberen Protokollen mit Action-Items verarbeiten.
- Welche Subagents dabei sinnvoll sind und wie Sie sie anlegen.
- Wie Sie die beiden Workflows per Slash-Command auslösen.
- Welche Sicherungsmechanismen Sie einbauen, damit nichts ungewollt verschickt wird.

---

## Use-Case 1: E-Mail-Triage

**Das Problem.** Jeden Morgen sitzen Sie vor 40 bis 80 neuen Mails. Die meisten sind Routine, ein paar sind dringend, ein paar sind einfach Rauschen. Sie verlieren die ersten 45 Minuten des Tages mit Aussortieren, Lesen und Beantworten, bevor Sie zur eigentlichen Arbeit kommen.

**Das Ziel.** Ein Agent, den Sie morgens mit einem Befehl starten. Er holt die neuen Mails seit Ihrem letzten Durchgang, klassifiziert sie nach einem festen Schema, fasst die wichtigen zusammen, bereitet Antwort-Entwürfe vor und legt am Ende eine übersichtliche Markdown-Datei an, die Sie in zehn Minuten durchgehen können. Er sendet **nichts** von sich aus — Entwürfe bleiben Entwürfe.

### Voraussetzungen

- Claude Code installiert, in einem Arbeitsordner gestartet (z. B. `~/email-triage/`).
- **Gmail-MCP verbunden** (oder der entsprechende Outlook-/Microsoft-365-MCP, falls Sie dort zu Hause sind). Siehe Kapitel 10 Teil 03 und Teil 03 dieses Kapitels.
- Optional: **Slack-MCP verbunden**, falls Sie nach der Triage wichtige Mails an ein Team-Channel weiterleiten wollen.

Wenn Sie kein Claude Code nutzen möchten, funktioniert der gleiche Workflow auch in **Cowork** — der Unterschied ist nur, dass Sie dort keine Subagents anlegen, sondern alle Schritte im Hauptagent führen. Die Prompts unten übernehmen Sie einfach als normale Chat-Anfragen. Für den Vergleich ist Claude Code der sauberere Weg.

### Cowork-Variante in Kürze

Für Leserinnen und Leser, die Claude Code noch nicht installiert haben und zunächst beim Cowork-Desktop bleiben möchten, hier die verkürzte Variante derselben Triage — ohne Subagents, ohne Slash-Command, aber mit demselben Ergebnis:

1. **Einmalige Vorbereitung.** Gmail-Connector verbinden (Kapitel 10 Teil 03), Arbeitsordner `email-triage/` im Cowork-Sidebar als Workspace wählen.
2. **Prompt für jeden Lauf.** Öffnen Sie Cowork und schreiben Sie einen einzigen Prompt nach diesem Muster: „Hole aus meinem Gmail-Posteingang die ungelesenen Mails der letzten 24 Stunden (maximal 50). Klassifiziere jede in eine von fünf Kategorien: kunde-dringend, kunde-routine, intern, newsletter, sonstiges. Schreibe für die beiden Kunde-Kategorien je eine Zwei-Satz-Zusammenfassung und, wo möglich, einen Antwort-Entwurf. Speichere das Ergebnis als Markdown-Datei `triage/<heute>.md` mit vier Abschnitten (dringend, Routine, intern, Rest) und einer Kopfzeile mit Zählern. Versende nichts."
3. **Ergebnis lesen und versenden.** Sie bekommen dieselbe Markdown-Datei wie im Claude-Code-Weg, nur dass die Klassifikation vom Hauptagenten direkt durchgeführt wurde, statt von einem Subagenten.

**Was Ihnen in der Cowork-Variante fehlt.** Drei Dinge sind in Cowork heute noch nicht so komfortabel wie in Claude Code: erstens der **eigene Kontext pro Teilaufgabe** (der Cowork-Agent klassifiziert 50 Mails im gleichen Kontextfenster, was bei Haiku-ähnlichen Aufgaben meist reicht, aber auffälliger wird, je länger die Mails sind), zweitens der **Slash-Command als Ein-Wort-Aufruf** (in Cowork prompten Sie den ganzen Text jedes Mal, bis Sie ihn als Skill oder als Prompt-Snippet abgelegt haben), drittens **Hooks als automatische Nebenläufer** (Logging, Formatierung). Für die ersten Wochen merken Sie diese Unterschiede kaum; wenn der Triage-Workflow einmal täglich läuft und stabil ist, lohnt der Umzug nach Claude Code, weil die drei genannten Punkte dann wirklich sparen.

**Was in der Cowork-Variante gleich gut funktioniert.** Die inhaltliche Qualität der Klassifikation, das Ausgabeformat, die Sicherungs-Regel „nichts wird versendet", und die Möglichkeit, die Markdown-Datei anschließend in Notion, Drive oder Ihr Notiz-Tool zu kopieren. Wenn Ihre Priorität Einstieg-ohne-Terminal ist, starten Sie bewusst in Cowork und machen den Wechsel später.

### Die fünf Stationen

Die Pipeline folgt dem Muster **Lesen → Klassifizieren → Zusammenfassen → Entwerfen → Berichten**. Die Illustration [`illustrations/12-05-email-triage-pipeline.png`](./illustrations/12-05-email-triage-pipeline.png) zeigt die Stationen im Überblick.

**Station 1 — Lesen.** Agent holt die Mails der letzten 24 Stunden (oder seit Ihrem letzten Durchlauf) aus Gmail. Gefiltert auf „nicht gelesen" und „Inbox", sodass bereits archivierte Mails außen vor bleiben.

**Station 2 — Klassifizieren.** Ein Subagent `mail-klassifizierer` bekommt jede Mail und ordnet sie einem von fünf festen Labels zu: `kunde-dringend`, `kunde-routine`, `intern`, `newsletter`, `sonstiges`. Das ist eine reine Klassifikationsaufgabe — Haiku 4.5 reicht, das ist schneller und billiger.

**Station 3 — Zusammenfassen.** Für die beiden Klassen `kunde-dringend` und `kunde-routine` erstellt der Hauptagent jeweils eine Zwei-Satz-Zusammenfassung: Worum geht es, was wird von Ihnen erwartet. Newsletter und Sonstiges werden nur gelistet, nicht zusammengefasst.

**Station 4 — Entwerfen.** Für die Kategorie `kunde-dringend` und alle `kunde-routine`-Mails, die eine einfache Antwort erlauben, bereitet der Hauptagent einen Antwortentwurf vor. Der Entwurf wird **nicht** versendet, sondern als Markdown-Block in die Ergebnisdatei geschrieben.

**Station 5 — Berichten.** Der Hauptagent legt eine Markdown-Datei `triage/<datum>.md` an mit vier Abschnitten (dringend, Routine, intern, Rest) und einer kurzen Kopfzeile: „17 Mails gesehen, 3 dringend, 5 Routine, 4 intern, 3 Newsletter, 2 Sonstiges. Geschätzte Bearbeitungszeit der verbleibenden Punkte: 25 Minuten." Sie lesen die Datei, beschließen selbst, welche Entwürfe Sie abschicken wollen, und kopieren sie zurück in Gmail.

### Der Subagent `mail-klassifizierer`

Legen Sie ihn mit `/agents` → `Create New Agent` an. Die Datei sollte so aussehen:

```markdown
---
name: mail-klassifizierer
description: Use this agent to classify a single email into one of five 
  fixed categories. Call it once per email when triaging an inbox.
tools: Read
model: haiku
---

Du bist ein praeziser Mail-Klassifizierer. Deine einzige Aufgabe ist es, 
eine Mail in genau eine von fuenf Kategorien einzuordnen:

- **kunde-dringend**: Mail von einem Kunden, die eine Reaktion innerhalb 
  von 24 Stunden braucht (erkennbar an Woertern wie "dringend", "asap", 
  "Frist", "heute", "morgen" oder am Thema).
- **kunde-routine**: Mail von einem Kunden, die keine sofortige Reaktion 
  braucht. Antwort innerhalb einer Woche OK.
- **intern**: Mail von einer Kollegin, einem Kollegen oder einem internen 
  System. Erkennbar an der Absender-Domain.
- **newsletter**: Automatisierte Rundmails, Marketing, Produkt-Updates. 
  Kein direkter Bezug zu laufenden Kundenprojekten.
- **sonstiges**: Alles, was in keine der obigen Kategorien passt.

Antworte in genau einem Wort — der Kategorie-Name, ohne weitere Erklaerung. 
Wenn Du Dir unsicher bist, waehle die konservativere Kategorie 
(also eher "kunde-routine" als "newsletter").
```

Beachten Sie: Modell **Haiku 4.5** (schnell, billig, für einfache Klassifikation mehr als ausreichend), Tools **nur `Read`** (der Subagent kann nichts kaputtmachen), Systemprompt kurz und klar.

### Der Slash-Command `/triage`

Legen Sie die Datei `.claude/commands/triage.md` an, entweder von Hand oder indem Sie Claude bitten, sie für Sie zu erstellen:

```markdown
---
description: Fuehrt die Morgens-Mail-Triage durch. Liest ungelesene Mails 
  aus Gmail, klassifiziert sie, erstellt Zusammenfassungen und Entwuerfe, 
  schreibt einen Markdown-Bericht nach triage/<datum>.md. Versendet nichts.
---

Du bist der Mail-Triage-Assistent. Fuehre die folgenden Schritte aus, 
in dieser Reihenfolge. Melde nach jedem Schritt kurz, was Du gefunden hast.

## Schritt 1: Lesen

Hole aus dem Gmail-MCP alle ungelesenen Mails im Posteingang, die in 
den letzten 24 Stunden eingegangen sind. Beschraenke Dich auf maximal 50.

## Schritt 2: Klassifizieren

Rufe fuer jede Mail den `mail-klassifizierer`-Subagent auf. Uebergib 
Betreff, Absender und die ersten 500 Zeichen des Mail-Textes. Sammle 
die Kategorien.

## Schritt 3: Zusammenfassen

Fuer jede Mail in den Kategorien "kunde-dringend" und "kunde-routine", 
schreibe eine Zusammenfassung in genau zwei Saetzen: 
Satz 1: Worum geht es? 
Satz 2: Was wird von mir erwartet?

## Schritt 4: Entwerfen

Fuer jede Mail in "kunde-dringend" und fuer die "kunde-routine"-Mails, 
die eine einfache Antwort erlauben (z. B. Terminbestaetigung, Empfangs-
bestaetigung, kurze Rueckfrage), schreibe einen Antwort-Entwurf. 
Der Entwurf soll sachlich und freundlich sein und mit "Liebe Gruesse, 
[Ihr Name]" enden. Versende nichts. Der Entwurf ist nur ein Text-Block.

## Schritt 5: Berichten

Lege eine Datei `./triage/<YYYY-MM-DD>.md` an mit folgender Struktur:

- **Kopfzeile**: Anzahl gesehener Mails, Verteilung nach Kategorie, 
  geschaetzte Bearbeitungszeit der verbleibenden Punkte.
- **Dringend**: Jede Mail als eigener Abschnitt mit Absender, Betreff, 
  Zusammenfassung, Entwurf.
- **Routine**: Analog zu Dringend.
- **Intern**: Nur Absender und Betreff, keine Zusammenfassung.
- **Newsletter/Sonstiges**: Nur Anzahl, keine Details.

Zeige mir am Ende den Dateinamen und die Kopfzeile. Frage mich, 
ob ich einen der Entwuerfe jetzt bereits ueberarbeiten oder absenden 
moechte. Versende nichts von selbst.
```

### Der Ablauf in der Praxis

Morgens, erste Tasse Kaffee. Sie öffnen Claude Code im Triage-Ordner:

```
cd ~/email-triage
claude
```

Dann tippen Sie im Chat einfach `/triage`. Der Agent arbeitet die fünf Stationen ab. Sie sehen im Terminal, wie er die Mails holt (15 Sekunden), den Subagent für jede Mail aufruft (weitere 30 Sekunden), Zusammenfassungen schreibt (eine Minute) und die Datei anlegt. Nach rund zwei Minuten sind Sie fertig, und Sie haben eine Markdown-Datei, die Sie im Editor Ihrer Wahl öffnen.

Die Datei sieht ungefähr so aus:

```markdown
# Triage fuer 2026-04-10

**Uebersicht:** 24 Mails gesehen. 3 dringend, 5 Routine, 6 intern, 
7 Newsletter, 3 Sonstiges. Geschaetzte Bearbeitungszeit: 25 Minuten.

## Dringend

### 1. Lisa Meier <lisa@kunde-x.de> — Re: Angebot ueberarbeitet

**Zusammenfassung:** Lisa bittet um Ueberarbeitung des Angebots bis Freitag, 
weil der Einkauf am Montag entscheidet. Sie will insbesondere eine niedrigere 
Stundenanzahl fuer Modul B sehen.

**Entwurf-Antwort:**

> Hallo Lisa,
> 
> danke fuer den Hinweis. Ich schaue mir Modul B heute Nachmittag an und 
> schicke Dir die ueberarbeitete Variante morgen Vormittag.
> 
> Liebe Gruesse, ...

---

### 2. ...
```

Sie lesen, überarbeiten bei Bedarf die Entwürfe, kopieren sie in Gmail, klicken „Senden". In 10 Minuten sind Sie durch, statt in 45. Der Unterschied ist nicht die Schreibzeit — die ist ähnlich. Der Unterschied ist das **Sortieren**: Sie müssen nicht mehr selbst entscheiden, was wichtig ist.

### Sicherungsmechanismen

Drei Punkte, die Sie unbedingt einbauen sollten:

**Erstens — kein automatisches Senden.** Die Systemprompt und der Slash-Command betonen beide, dass nichts von selbst verschickt wird. Das ist kein Dekor, das ist die wichtigste Sicherung. Selbst wenn der Agent perfekt klassifiziert, werden seine Entwürfe gelegentlich den falschen Ton treffen — das wollen Sie vor dem Absenden sehen.

**Zweitens — Entwürfe in Markdown, nicht in Gmail-Drafts.** Sie könnten theoretisch den Agent die Entwürfe direkt als Gmail-Draft speichern lassen. Tun Sie das am Anfang nicht. Es verwischt die Trennung zwischen „KI-Vorschlag" und „von mir freigegeben". Eine Markdown-Datei, die Sie bewusst öffnen, ist der klarere Kontrollpunkt.

**Drittens — ein Log.** Richten Sie einen PreToolUse-Hook auf das Gmail-Tool ein, der protokolliert, wann Claude auf welche Mail-ID zugegriffen hat. Wenn später eine Frage auftaucht („hat der Agent diese Mail gesehen?"), haben Sie die Antwort in der Log-Datei.

### Grenzen und sinnvolle Erweiterungen

- **Grenze:** Wenn Ihre Kunden in vielen Sprachen schreiben, ist die Klassifikation anspruchsvoller. Erweitern Sie die Systemprompt um Hinweise zu den erwarteten Sprachen.
- **Grenze:** Ein Agent auf Haiku-Basis macht bei sehr kurzen Mails gelegentlich Fehler. Prüfen Sie die Kategorien-Verteilung die ersten Tage stichprobenartig. Falls zu viele Mails in „Sonstiges" landen, schärfen Sie die Beschreibung nach.
- **Erweiterung:** Sie können einen zweiten Subagent `eskalations-pruefer` hinzufügen, der nur für die `kunde-dringend`-Kategorie aktiv wird und prüft, ob jemand aus Ihrem Team (oder Sie selbst) sofort einspringen muss.
- **Erweiterung:** Wenn der Workflow stabil läuft, können Sie ihn über den `schedule`-Skill (Kapitel 10) jeden Werktag um 8:00 Uhr automatisch auslösen.

---

## Use-Case 2: Meeting-Notes-Pipeline

**Das Problem.** Nach jedem längeren Termin bleibt eine Tonaufnahme oder ein Roh-Transkript übrig, und Sie haben entweder keine Zeit, es sauber nachzubereiten, oder Sie nehmen sich die Zeit und schreiben eine Stunde an einer Zusammenfassung, die am Ende doch nur wenige Leute lesen.

**Das Ziel.** Ein Workflow, der aus einem Roh-Transkript innerhalb einer Minute ein sauberes Protokoll macht: Teilnehmerliste, Agenda, wichtige Entscheidungen, Action-Items mit Zuständigkeit und Frist, offene Fragen. Das Ergebnis soll in einem Markdown-Format stehen, das Sie direkt kopieren oder in Notion/Google Docs einfügen können.

### Voraussetzungen

- Claude Code oder Cowork.
- Ein Arbeitsordner mit Unterordnern `transcripts/` (Roh-Eingänge) und `protokolle/` (fertige Protokolle).
- Das Roh-Transkript als `.txt`- oder `.md`-Datei im `transcripts/`-Ordner. Wie Sie es dorthin bekommen, ist eine separate Frage — die meisten Video-Konferenz-Tools (Zoom, Teams, Google Meet) bieten automatische Transkripte an, die Sie exportieren können. Alternativ nutzen Sie einen Transkriptions-Dienst wie Whisper lokal oder einen der Cloud-Anbieter.

### Der Subagent `protokoll-formatter`

Dieser Subagent ist stärker und komplexer als der Mail-Klassifizierer. Er bekommt ein ganzes Transkript und soll daraus ein strukturiertes Protokoll machen. Sonnet 4.6 ist hier richtig.

```markdown
---
name: protokoll-formatter
description: Use this agent to transform a raw meeting transcript into a 
  structured meeting minutes document. Call it once per transcript file.
tools: Read, Write
model: sonnet
---

Du bist ein praeziser Protokoll-Schreiber fuer Geschaeftsmeetings. 
Deine Aufgabe ist es, ein Roh-Transkript in ein sauberes Protokoll 
im Markdown-Format zu ueberfuehren.

## Aufbau des Protokolls

Das Protokoll hat immer sieben Abschnitte, in genau dieser Reihenfolge:

### 1. Kopf
- Datum, Uhrzeit, Dauer
- Format (vor Ort / Video / Telefon)
- Moderation, Protokollfuehrer (falls erwaehnt)

### 2. Teilnehmende
Liste aller Personen, die waehrend des Meetings gesprochen haben. 
Wenn Rollen erwaehnt werden, nimm sie auf. Bei Zweifeln am Namen 
(Homophone, unklare Transkription) setze ein [?].

### 3. Agenda
Liste der Themen in der Reihenfolge, in der sie behandelt wurden.

### 4. Diskussionspunkte
Pro Agenda-Punkt eine kurze Zusammenfassung in zwei bis vier Saetzen. 
Keine woertliche Wiedergabe. Keine Nebengespraeche.

### 5. Entscheidungen
Jede getroffene Entscheidung als eigener Punkt. Format:
- **Entscheidung**: ...
- **Beschlossen von**: ...
- **Gilt fuer**: ... (Projekt/Zeitraum/Bereich)

### 6. Action-Items
Jedes Action-Item als eigener Punkt. Format:
- **Aufgabe**: ...
- **Verantwortlich**: ...
- **Frist**: ... (wenn nicht genannt: "nicht genannt, bitte nachfragen")

### 7. Offene Fragen
Punkte, die diskutiert, aber nicht abgeschlossen wurden. Jeder Punkt 
mit einem kurzen Hinweis, wer sich darum kuemmern wollte.

## Arbeitsweise

1. Lies das uebergebene Transkript vollstaendig, bevor Du schreibst.
2. Identifiziere die sieben Abschnitte im Kopf, bevor Du Text formulierst.
3. Schreibe praezise, neutral und vollstaendig. 
4. Wenn etwas im Transkript unklar ist, schreibe "[unklar]" statt zu raten.
5. Wenn ein Abschnitt leer ist (z. B. keine Entscheidungen getroffen), 
   schreibe "Keine in diesem Meeting" — niemals den Abschnitt weglassen.
6. Gib am Ende die Gesamtlaenge des Protokolls in Zeilen und die 
   Anzahl der Action-Items als Metadaten zurueck.

## Was Du nicht tust

- Keine Bewertungen der Aussagen.
- Keine Spekulationen ueber Motive.
- Keine Zitate — Du verdichtest, nicht woertlich.
- Keine Emojis.
- Kein "Wir haben eine wunderbare Diskussion gefuehrt" — keine Floskeln.
```

### Der Slash-Command `/protokoll`

```markdown
---
description: Erstellt aus dem neuesten Transkript in ./transcripts/ ein 
  strukturiertes Meeting-Protokoll in ./protokolle/ und meldet die 
  Action-Items am Ende.
---

Du bist der Protokoll-Assistent. Fuehre die folgenden Schritte aus:

## Schritt 1: Transkript finden

Schau in den Ordner `./transcripts/` und identifiziere die neueste 
Datei (nach Aenderungsdatum). Zeige mir den Dateinamen und bestaetige, 
dass Du diese Datei verarbeitest, bevor Du weitermachst.

## Schritt 2: Protokoll erzeugen

Rufe den `protokoll-formatter`-Subagent auf und uebergib ihm den 
kompletten Inhalt der Datei. Erhalte das strukturierte Protokoll 
zurueck.

## Schritt 3: Speichern

Speichere das Ergebnis unter `./protokolle/<basename-ohne-endung>.md`, 
wobei basename der Name der Transkript-Datei ohne Endung ist. 
Wenn die Datei bereits existiert, haenge "-v2", "-v3" usw. an, 
bis der Name frei ist.

## Schritt 4: Action-Items extrahieren

Lies das frisch gespeicherte Protokoll und extrahiere die Action-Items 
in eine separate Liste. Zeige mir:
- die Gesamtzahl der Action-Items
- die Items mit Frist "nicht genannt" als Liste (damit ich sie nachhole)
- die Items mit heute oder gestern als Frist, weil die vermutlich 
  nachtraeglich eingetragen werden muessen

## Schritt 5: Bericht

Zeige mir zum Abschluss:
- den Pfad der gespeicherten Protokoll-Datei
- die Anzahl der Action-Items
- die Zeilen mit "[unklar]" im Protokoll (wenn es welche gibt), 
  damit ich sie pruefen kann
```

### Der Ablauf in der Praxis

Nach einem Meeting exportieren Sie das Transkript aus Ihrem Video-Konferenz-Tool und legen es als `.txt`-Datei in den Ordner `transcripts/`. Dann:

```
cd ~/meetings
claude
```

Und im Chat: `/protokoll`.

Der Agent findet das Transkript, ruft den `protokoll-formatter` auf, bekommt das strukturierte Protokoll zurück, speichert es, extrahiert die Action-Items und berichtet. Dauer: 60 bis 120 Sekunden für ein Transkript einer einstündigen Besprechung.

Das Ergebnis ist ein sauberes Markdown-Protokoll in Ihrem `protokolle/`-Ordner, das Sie direkt an die Teilnehmenden verschicken oder in Notion, Confluence, Google Docs einfügen können. Die Action-Items können Sie noch einmal schnell durchgehen und prüfen, ob Fristen nachzutragen sind.

### Sicherungsmechanismen

**Erstens — keine automatische Weiterleitung.** Das Protokoll wird gespeichert, nicht verschickt. Sie lesen es, bevor es an Kunden oder Kollegen geht. Bei personenbezogenen Aussagen aus Meetings ist das eine DSGVO-relevante Entscheidung, die ein Mensch treffen sollte — siehe auch Kapitel 14 Teil 02.

**Zweitens — `[unklar]`-Markierungen pflegen.** Der Subagent markiert unsichere Stellen mit `[unklar]`. Bevor Sie das Protokoll teilen, suchen Sie alle `[unklar]`-Stellen und klären Sie sie. Der Slash-Command meldet sie Ihnen am Ende — nutzen Sie die Meldung.

**Drittens — Roh-Transkripte aufbewahren oder löschen?** Das ist eine bewusste Entscheidung. Aufbewahren: Nachvollziehbarkeit, Sie können später nochmal nachschauen. Löschen: Datenschutz, weniger sensible Daten auf der Platte. Eine Kompromisslösung: Roh-Transkripte nach 30 Tagen automatisch löschen, Protokolle archivieren. Ein zusätzlicher Schedule-Skill-Job kann das übernehmen.

### Wenn das Transkript zu lang wird — Token-Grenzen praktisch umgehen

Für kurze und mittlere Meetings (bis etwa 60 Minuten, grob 10.000 bis 15.000 Wörter im Transkript) funktioniert der `protokoll-formatter` direkt. Bei längeren oder dichteren Meetings stoßen Sie an die Kontext-Grenze des Subagents — der Subagent liest das Transkript, bekommt aber irgendwann nicht mehr genügend „Denk-Raum" für eine gute Zusammenfassung, weil das Transkript den Kontext zu stark füllt. Typisches Symptom: Das Protokoll wird spürbar dünner, Ende des Meetings fehlt, Action-Items ab Minute 45 fallen unter den Tisch.

Drei Strategien haben sich bewährt, sobald das passiert.

**Strategie 1 — Zweistufiges Vorgehen.** Statt den `protokoll-formatter` direkt auf das komplette Transkript loszulassen, teilen Sie das Transkript in Abschnitte (z. B. nach Agenda-Punkten oder einfach in drei Teile zu je etwa 20 Minuten). Der Slash-Command ruft den Subagent pro Abschnitt einmal auf, bekommt pro Abschnitt ein kleines Protokoll zurück, und ein zweiter, einfacher Schritt fügt die Teil-Protokolle in ein Gesamt-Dokument zusammen. Das ist die robusteste Lösung, weil jeder Subagent-Aufruf in einem frischen, sauberen Kontext arbeitet.

**Strategie 2 — Vorverdichten.** Bei sehr redundanten Meetings (viele Wiederholungen, Nebengespräche, Füllwörter) können Sie dem Subagent vor dem eigentlichen Protokoll einen **Vor-Schritt** vorsetzen: „Entferne aus dem Transkript reine Wiederholungen, Begrüßungen, Verabschiedungen und Nebengespräche. Gib das bereinigte Transkript zurück." Das bereinigte Transkript ist oft nur halb so lang wie das Original und bietet dem eigentlichen Protokoll-Lauf wieder genug Spielraum. Nachteil: Die Vorverdichtung kann versehentlich wichtige Details als „Nebengespräch" einordnen — prüfen Sie die ersten Durchläufe stichprobenartig.

**Strategie 3 — Modell-Wahl.** Die Kontext-Grenzen unterscheiden sich zwischen Claude Opus, Sonnet und Haiku. Wenn Sonnet 4.6 an die Grenze kommt, probieren Sie dieselbe Aufgabe mit Opus 4.6, das in der Regel mehr Spielraum für sehr lange Eingaben hat — bei entsprechend höheren Kosten pro Lauf. Umgekehrt: Für sehr kurze Meetings (unter 15 Minuten) ist Haiku 4.5 meist ausreichend und deutlich günstiger. Tauschen Sie das Modell im YAML-Frontmatter des Subagents aus und lassen Sie denselben Lauf noch einmal durch — der Unterschied ist meist sofort sichtbar.

Eine praktische Faustregel: Wenn Sie feststellen, dass Meetings bei Ihnen öfter länger als 90 Minuten sind, bauen Sie die zweistufige Variante (Strategie 1) gleich beim ersten Aufsetzen ein. Sie sparen sich damit späteres Umbauen, und der Overhead im Normalfall ist überschaubar.

### Grenzen und sinnvolle Erweiterungen

- **Grenze:** Transkripte, die komplett in Dialekt oder mehreren Sprachen sind, fordern den Subagent stark. Rechnen Sie mit mehr `[unklar]`-Markierungen.
- **Grenze:** Wenn Ihr Meeting sehr technisch ist (viele Fachbegriffe, Produktnamen), kann der Subagent die Begriffe „normalisieren", was manchmal Bedeutung zerstört. Ergänzen Sie die Systemprompt um eine Liste Ihrer wichtigsten Begriffe, die nicht vereinfacht werden sollen.
- **Erweiterung:** Ein zweiter Subagent `aktions-verteiler` nimmt die Action-Items entgegen und schreibt pro Verantwortlichem eine kurze Mail, die Sie dann durchgehen und absenden (wiederum: nicht automatisch senden).
- **Erweiterung:** Verbinden Sie den Workflow mit einem Asana-/Linear-/Jira-MCP, sodass Action-Items direkt als Tasks angelegt werden können — aber auch hier: nur mit ausdrücklicher Bestätigung im Chat, keine blinde Automatik.

---

## Was die beiden Use-Cases gemeinsam haben

Wenn Sie die beiden Abläufe nebeneinanderlegen, sehen Sie ein Muster, das in den meisten Agent-Workflows wiederkehrt:

1. **Eine klare Quelle.** Gmail, ein Transkript-Ordner — der Agent weiß, wo er suchen muss.
2. **Eine enge Tätigkeit pro Subagent.** Klassifizieren. Protokollieren. Kein einzelner Subagent hat mehr als eine Aufgabe.
3. **Ein definiertes Ausgabeformat.** Markdown-Datei in einem bekannten Ordner.
4. **Keine automatischen Außenwirkungen.** Der Agent verschickt nichts, speichert aber Entwürfe und bereitet Aktionen vor.
5. **Ein Bericht am Ende.** Der Agent sagt, was er gemacht hat und was zu prüfen ist.

Dieses Muster ist robust. Wenn Sie einen dritten oder vierten Workflow bauen, kopieren Sie die Struktur und ersetzen Quelle, Subagent und Ausgabe. Die meisten Büro-Automatisierungen passen in dieses Schema.

---

## Troubleshooting — was in der Praxis regelmäßig schiefgeht

Die beiden Workflows oben sind solide, wenn die Voraussetzungen stimmen. Wenn sie nicht stimmen, sehen Sie in der Regel eines der folgenden Muster. Alle sind reparierbar, meist in wenigen Minuten.

**E-Mail-Triage: „`/triage` findet keine Mails."**
Häufigste Ursache: Das Gmail-MCP ist nicht verbunden oder das OAuth-Token ist abgelaufen. Prüfen Sie im Claude-Code-Chat mit `/mcp` den Status aller verbundenen Server; wenn Gmail als `error` oder `disconnected` erscheint, verbinden Sie neu. Zweithäufigste Ursache: Der Filter „ungelesen in den letzten 24 Stunden" passt nicht zu Ihrem Mail-Muster (z. B. weil Sie abends selbst durchgegangen sind und alles als gelesen markiert haben). Lockern Sie den Filter im Slash-Command auf „alle Mails in der Inbox seit gestern 8 Uhr".

**E-Mail-Triage: „Der `mail-klassifizierer` wirft alles in ‚sonstiges'."**
Fast immer ein Beschreibungs-Problem. Der Subagent hat nicht genug Signale, um die Kategorien auseinanderzuhalten. Öffnen Sie `.claude/agents/mail-klassifizierer.md`, erweitern Sie die Kategorien-Beschreibungen um **ein bis zwei Beispielsätze pro Kategorie** aus Ihrer echten Mailwelt (anonymisiert), und lassen Sie die Triage noch einmal laufen. Meist reicht das. Wenn es nach der Erweiterung immer noch nicht sitzt, probieren Sie den Subagent mit `model: sonnet` statt `haiku` — das kostet etwas mehr, bringt bei kniffligen Mails aber spürbar bessere Klassifikation.

**E-Mail-Triage: „Claude will Mails versenden, obwohl der Prompt das verbietet."**
Sollte eigentlich nicht passieren, kommt aber vor, wenn das Gmail-MCP auch Schreib-Werkzeuge exportiert und der Hauptagent die „nicht versenden"-Regel nur als Text im Slash-Command liest. Die härtere Sicherung: Beschränken Sie den Gmail-MCP bei der Verbindung auf **nur Lese-Rechte** (die meisten MCPs bieten das in den OAuth-Scopes an). Dann **kann** der Agent gar nicht versenden, auch wenn er wollte. Der „weiche" Prompt-Schutz ist ergänzend, nicht ersetzend.

**Meeting-Notes: „`/protokoll` findet das Transkript nicht."**
Prüfen Sie mit `ls transcripts/`, ob die Datei überhaupt dort liegt. Typische Stolperer: Die Datei liegt im Download-Ordner, Sie haben sie nur verlinkt, nicht kopiert; die Datei hat eine ungewöhnliche Endung (`.vtt`, `.srt`, `.json`) statt `.txt` oder `.md`; das Zoom-/Teams-Export-Skript hat einen Unter-Ordner mit Datum gebaut, in dem das Transkript steckt. Lösung je nach Fall: kopieren, umbenennen, den Slash-Command anpassen („suche rekursiv unter `transcripts/`").

**Meeting-Notes: „Das Protokoll hat unsinnige Namen in der Teilnehmerliste."**
Das passiert bei automatischen Transkripten sehr oft. Die Sprecher-Erkennung des Video-Konferenz-Tools setzt z. B. „Sprecher 1", „Sprecher 2" statt der echten Namen ein. Zwei Lösungen: Entweder bearbeiten Sie das Roh-Transkript vor dem Lauf einmal kurz und ersetzen die Sprecher-Labels durch die echten Namen (das kostet zwei Minuten), oder Sie ergänzen den `protokoll-formatter`-Subagent um eine Regel: „Wenn im Transkript nur generische Labels wie 'Sprecher 1' vorkommen, belasse sie so und schreibe am Anfang des Protokolls einen Hinweis, dass die Zuordnung fehlt."

**Meeting-Notes: „Action-Items tauchen nicht auf, obwohl sie im Meeting besprochen wurden."**
Der Subagent erkennt Action-Items an Formulierungen wie „X macht Y bis Z". Wenn Ihr Team anders spricht („Das schauen wir uns dann mal an", „Lasst uns das im Auge behalten"), verpasst er sie. Ergänzen Sie die Systemprompt des `protokoll-formatter` um eine Liste Ihrer typischen Verpflichtungs-Formulierungen, damit er sie als Action-Items einträgt.

**Beides: „Der Workflow lief einmal, beim zweiten Mal nicht mehr."**
Häufigste Ursache: Die MCP-Verbindung ist im Hintergrund getrennt worden (Token-Ablauf, Netzwerk, OAuth-Neuzustimmung nötig). Zweithäufigste: Die Slash-Command-Datei wurde unabsichtlich editiert und hat jetzt einen Syntaxfehler im YAML-Frontmatter. Prüfen Sie `.claude/commands/<name>.md` auf Einrückung und Anführungszeichen. Drittens: Ein eingerichteter Hook ist defekt und blockiert den Lauf — siehe Troubleshooting in Teil 04.

---

## Kernbotschaft

Die **E-Mail-Triage** läuft in fünf Stationen (Lesen, Klassifizieren, Zusammenfassen, Entwerfen, Berichten) mit einem `mail-klassifizierer`-Subagent auf Haiku-Basis und dem Slash-Command `/triage` — und versendet nichts. Die **Meeting-Notes-Pipeline** verwandelt ein Roh-Transkript per `protokoll-formatter`-Subagent auf Sonnet in ein siebenteiliges Protokoll, gesteuert durch `/protokoll`. Beide teilen fünf Prinzipien: klare Quelle, enger Subagent-Fokus, definiertes Ausgabeformat, keine Außenwirkung ohne Freigabe, Bericht am Ende.

---

## Nächste Schritte

- **[06 Praxis Recherche-Pipeline und Datenanalyse](./06%20Praxis%20Recherche-Pipeline%20und%20Datenanalyse.md)** — zwei weitere Praxis-Workflows, diesmal mehrstufige Web-Recherche und wiederkehrende Monatsreports in direkter Fortführung von Kapitel 11.
- Zurück zur Übersicht: **[README](./README.md)**.
- Querverweis: **Kapitel 14 Teil 02 (DSGVO und KI)** — unbedingt lesen, bevor Sie die E-Mail- oder Meeting-Workflows in einem Team einsetzen, in dem personenbezogene Daten verarbeitet werden.
