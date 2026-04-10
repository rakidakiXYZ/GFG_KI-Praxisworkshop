# 07 Praxisleitfaden — Grenzen, Sicherheit, Kosten

**Das Abschlusskapitel: wann Sie automatisieren, was Sie absichern, was es kostet.**

---

## Warum dieses Tutorial?

Die ersten sechs Teile dieses Kapitels haben gezeigt, **wie** man Agenten baut. Dieses letzte Tutorial beantwortet die Fragen, die nach „wie" noch offen sind: **Wann lohnt sich überhaupt eine Automatisierung?** **Welche Guardrails sind unverzichtbar?** **Was kostet es?** **Wie erkenne ich, dass ein Agent aus dem Ruder läuft?** **Was tue ich, wenn er das tut?**

Dieses Tutorial ist kein Nachklapp. Wenn Sie einen der Workflows aus Teil 05 oder 06 übernehmen wollen, sollten Sie es lesen, **bevor** Sie den Workflow das erste Mal ohne enge Aufsicht laufen lassen. Die Fehler, die hier beschrieben sind, sind echte Fehler, die in den letzten zwei Jahren teils mit nennenswerten Folgen passiert sind. Ihr eigener Betrieb muss sie nicht wiederholen.

**Was Sie nach diesem Tutorial wissen werden:**

- Eine klare Faustregel, wann Automatisierung den Aufwand lohnt und wann nicht.
- Die sieben Guardrails, die jeder produktive Agenten-Workflow braucht.
- Was Agenten ungefähr kosten — Größenordnungen, keine Preislisten.
- Woran Sie erkennen, dass ein Agent gerade einen Fehler macht.
- Welche Rolle der Mensch in der Schleife in welcher Phase spielen sollte.
- Warum Kapitel 14 (Ethik, Sicherheit und Verantwortung) kein optionaler Nachbar dieses Kapitels ist, sondern die andere Seite der gleichen Medaille.

---

## Wann lohnt sich Automatisierung?

Hier eine ehrliche Antwort: **Nur bei Aufgaben, die Sie mindestens wöchentlich haben und die lang genug dauern, dass die Einrichtung sich amortisiert.**

Die Rechnung ist einfach. Eine typische Automatisierung aus Teil 05 oder 06 kostet Sie etwa drei bis vier Stunden Einrichtung (Subagent schreiben, Slash-Command formulieren, einmal durchlaufen lassen, Ergebnis gegenprüfen, Ecken schleifen). Damit die Einrichtung sich rentiert, muss die Automatisierung Ihnen mindestens drei bis vier Stunden sparen. Wenn Sie eine Aufgabe einmal im Jahr haben, die zehn Minuten dauert, ist die Rechnung verheerend — Sie zahlen mit der Einrichtung deutlich mehr, als Sie je zurückbekommen. Wenn Sie eine Aufgabe wöchentlich haben, die 20 Minuten dauert, dann amortisiert sich die Einrichtung in etwa zwölf Wochen, und ab Woche 13 läuft der Gewinn.

Ein paar Anhaltspunkte:

- **Lohnt sich:** Tägliche oder wöchentliche Aufgaben, 15+ Minuten pro Durchlauf, stabile Prozesse, klare Fertig-Kriterien. Beispiele: E-Mail-Triage, Monatsreports, Meeting-Nachbereitung bei vielen Meetings, wiederkehrende Recherche-Themen, Content-Aufbereitung.
- **Lohnt sich vielleicht:** Monatliche Aufgaben, 30+ Minuten pro Durchlauf. Hier entscheidet die Stabilität — wenn der Prozess jeden Monat anders ist, sparen Sie die Einrichtung nicht wieder ein.
- **Lohnt sich meist nicht:** Einmalige Aufgaben, seltene Aufgaben (quartalsweise oder seltener), Aufgaben mit hoher Variabilität, Aufgaben, die Sie in fünf Minuten von Hand erledigen.

Es gibt eine Ausnahme von dieser Regel: **Aufgaben, bei denen die Qualität durch Automatisierung steigt.** Ein Beispiel ist die Recherche-Pipeline aus Teil 06. Sie könnten auch manuell recherchieren, aber ein Subagent, der jede Aussage gegen zwei Quellen prüft, ist gründlicher, als Sie es in einer halben Stunde schaffen würden. Hier automatisieren Sie nicht wegen der Zeit, sondern wegen der Verlässlichkeit. Das ist ein guter Grund — aber rechnen Sie trotzdem mit drei bis vier Stunden Einrichtungszeit.

---

## Die sieben Guardrails

Ein Agent, der ohne Guardrails läuft, ist wie ein neuer Mitarbeiter ohne Einarbeitung: Bestenfalls nützlich, schlimmstenfalls teuer. Die folgenden sieben Punkte sind nicht verhandelbar.

### Guardrail 1: Tool-Minimalismus

Jeder Subagent bekommt nur die Tools, die er wirklich braucht. Ein Mail-Klassifizierer darf lesen, sonst nichts. Ein Fact-Checker darf Web-Tools und Read, sonst nichts. Ein Zahlen-Prüfer darf Read, Bash und Grep — aber keinen Write-Zugriff.

**Warum wichtig:** Selbst wenn der Subagent einen Fehler macht oder (theoretisch) zweckentfremdet wird, kann er nur Dinge tun, die sein Profil zulässt. Ein Subagent, der keine Write-Rechte hat, kann keine Datei überschreiben. Ein Subagent, der keinen Bash hat, kann nichts ausführen. Das ist **defense in depth**: Sie verlassen sich nicht darauf, dass der Agent keinen Fehler macht, sondern darauf, dass der Fehler begrenzt bleibt.

### Guardrail 2: Keine Außenwirkung ohne Freigabe

Agenten bereiten vor. Menschen senden, verschicken, überweisen, committen, deployen. Diese Trennlinie ist die wichtigste Sicherheitsmaßnahme des gesamten Kapitels, und jede Abkürzung rund um sie hat sich in der Praxis als schlechte Idee herausgestellt.

Konkret heißt das:

- Keine automatisch verschickten Mails. Entwürfe in Markdown-Dateien, Sie schicken selbst ab.
- Keine automatisch veröffentlichten Beiträge. Drafts in einer Staging-Umgebung oder lokalen Datei, Sie klicken auf „veröffentlichen".
- Keine automatisch ausgeführten Finanzaktionen. Nie. Das wird in diesem Kapitel ausdrücklich nicht gezeigt, weil es eine Kategorie ist, bei der menschliche Freigabe verpflichtend bleibt.
- Keine automatisch geschlossenen Tickets, ohne dass der Kunde die Lösung bestätigt hat.
- Keine automatisch abgeschickten Slack-Nachrichten an Kundenkanäle. (Interne Notifikationen an Sie selbst sind OK.)

Die Ausnahme ist **Ihre eigene Ablage** — der Agent darf selbstverständlich Dateien in Ihren eigenen Ordnern speichern, Notizen anlegen, Zwischenergebnisse festhalten. Das ist keine Außenwirkung im Sinne dieses Guardrails.

### Guardrail 3: Abbruchpunkte an Unsicherheit

Jeder Workflow in Teil 05 und 06 hat Stellen, an denen er anhält und fragt, statt blind fortzufahren. „Wenn die Datenqualität auffällig schlecht ist, brich ab und frag nach." „Wenn das Format des Transkripts nicht wie erwartet aussieht, zeig mir, was Du siehst, und warte." Diese Abbruchpunkte sind keine Umstände, sie sind die **wichtigsten Stellen** der Prompts.

Wenn Sie einen eigenen Workflow bauen, überlegen Sie bei jedem Schritt: **Wo könnte etwas auffällig anders sein als erwartet?** An genau dieser Stelle baut man einen Abbruchpunkt ein. Der Agent hält an, beschreibt, was er sieht, und fragt, ob er weitermachen soll.

Das ist im Zweifel einmal zu viel als einmal zu wenig. Ein Workflow, der zehnmal pro Durchlauf nachfragt, ist lästig. Ein Workflow, der einen Monatsreport aus kaputten Daten bis zum Ende durchzieht und dann an Sie ausliefert, ist schlimmer.

### Guardrail 4: Logging und Nachvollziehbarkeit

Jeder produktive Agent muss nachvollziehbar sein. Mindestens zwei Dinge sollten geloggt werden:

1. **Welche Tools der Agent aufgerufen hat**, mit welchen Parametern und Ergebnissen. Der Pre-Tool-Use-Hook aus Teil 04 macht genau das.
2. **Welche Subagents aktiv waren**, mit welcher Eingabe und welcher Ausgabe. Der Stop-Subagent-Hook kann das für Sie festhalten.

Das ist kein Luxus. Wenn in zwei Wochen jemand fragt „hat der Agent die Mail XYZ gesehen und warum hat er sie nicht als dringend markiert?", dann haben Sie nur zwei Optionen: Sie können die Frage beantworten, oder Sie können es nicht. Ohne Log ist die Antwort „weiß ich nicht", und das untergräbt das Vertrauen in die Automatisierung.

Die Log-Dateien gehören in einen eigenen Ordner, rotieren sinnvoll (zum Beispiel wöchentlich), und werden nach einer definierten Frist (z. B. drei Monaten) gelöscht — das ist auch aus DSGVO-Sicht sauberer, siehe Kapitel 14 Teil 02.

### Guardrail 5: Kosten-Obergrenzen

Agenten, die in Schleifen laufen, können teuer werden, wenn etwas schiefgeht. Ein Agent, der sich verrennt und 500 Tool-Aufrufe macht, statt 20, kostet entsprechend mehr. Claude Code und Cowork haben Schutzmechanismen (maximale Anzahl Schritte pro Lauf, Token-Obergrenzen), aber Sie sollten **Ihre eigenen Obergrenzen** setzen:

- **Pro Lauf** ein Maximum an Tool-Aufrufen, etwa durch einen Hinweis im Slash-Command: „Wenn Du nach 30 Schritten noch nicht fertig bist, brich ab und melde Deinen Stand."
- **Pro Tag** ein Maximum an Läufen für die automatisierten Workflows, etwa durch den `schedule`-Skill, der den Report nur einmal am Tag startet.
- **Insgesamt** ein regelmäßiger Blick in die Nutzungsstatistik Ihres Claude-Abonnements oder API-Kontos. Einmal pro Woche fünf Minuten reichen, und Sie sehen sofort, wenn etwas aus dem Rahmen fällt.

Konkrete Preise nenne ich hier bewusst nicht, weil sie sich quartalsweise ändern. Als Größenordnung (Stand April 2026): Eine Standard-E-Mail-Triage für 50 Mails liegt in der Regel im Cent-Bereich, ein mittlerer Monatsreport im niedrigen einstelligen Euro-Bereich, eine aufwändige mehrstufige Recherche im niedrigen bis mittleren einstelligen Euro-Bereich. Alles deutlich günstiger als eine Stunde eigener Zeit — aber teuer genug, dass ein aus dem Ruder gelaufener Agent am Monatsende auffallen würde.

### Guardrail 6: Starttests in der sicheren Ecke

Ein neu gebauter Workflow läuft zuerst in einem **Wegwerf-Ordner** mit Testdaten, nicht auf Ihrem echten Arbeitsmaterial. Das klingt banal, wird aber oft übersprungen. Ein Workflow, der in seiner ersten Version 90% gut und 10% falsch macht, zerstört in der 10%-Ecke vielleicht Dateien, die Sie nicht wiederbekommen.

Konkret: Bauen Sie ein Verzeichnis `~/agent-tests/workflow-<name>/`, kopieren Sie 20 Zeilen Beispieldaten hinein (anonymisiert, keine echten Kundendaten), lassen Sie den Workflow zweimal durchlaufen, prüfen Sie das Ergebnis von Hand. Erst wenn er in dieser Umgebung stabil ist, lassen Sie ihn auf echten Daten los. Und selbst dann: die ersten zwei Durchläufe auf echten Daten schauen Sie sich vollständig an, nicht nur den Endbericht.

### Guardrail 7: Ein Mensch weiß Bescheid

Für jeden produktiven Agenten-Workflow gibt es **eine Person, die ihn versteht**. Nicht unbedingt die Person, die ihn gebaut hat — aber jemand, der weiß, welche Dateien er liest, welche er schreibt, welche MCPs er benutzt, was passiert, wenn er scheitert.

Das ist vor allem in Teams relevant. Ein Workflow, den niemand mehr versteht, ist ein Liability. Wenn Sie in sechs Monaten das Team wechseln, sollte jemand anderes den Monatsreport-Workflow weiterbetreiben können. Halten Sie deshalb eine **kurze README** neben jedem Workflow, die beschreibt:

- Was macht der Workflow?
- Wann wird er ausgelöst?
- Welche Dateien liest er, welche schreibt er?
- Welche Subagents kommen zum Einsatz?
- Welche MCPs werden vorausgesetzt?
- Was ist der typische Fertig-Zustand, und was sind Warnsignale?

Wenn diese README lebendig bleibt (Sie lesen sie wenigstens zweimal im Jahr), ist die Automatisierung team-tauglich. Wenn nicht, wird sie mit der Zeit zum Hexenwerk.

---

## Das Workflow-Steckbrief-Template

Guardrail 7 verlangt eine kurze README pro Workflow. Hier ist die Vorlage, die wir in diesem Kapitel empfehlen — kurz genug, dass Sie sie in zehn Minuten ausfüllen, vollständig genug, dass eine Kollegin den Workflow ohne Rückfragen übernehmen kann. Kopieren Sie den Block in eine Datei `workflow.md` direkt neben den Slash-Command oder den Subagent, damit beides zusammenbleibt.

```markdown
# Workflow-Steckbrief: <Name>

**Version:** 1.0  **Stand:** YYYY-MM-DD  **Eigentümer:** <Person oder Rolle>

## Zweck
Ein bis zwei Sätze: Was macht der Workflow, für wen, und welches Problem loest er?

## Auslöser
- **Wie gestartet?**  (z. B. manuell per `/triage`, per schedule-Skill taeglich um 08:00, per Hook nach Datei-Upload)
- **Wie oft?**  (taeglich / woechentlich / monatlich / bei Bedarf)
- **Durchschnittliche Laufzeit:**  (z. B. 2-3 Minuten)

## Eingabe
- **Quelle:**  (z. B. Gmail-Posteingang, Ordner `./transcripts/`, GitHub-Repository)
- **Format:**  (z. B. nur .txt und .md, maximal 50 Mails pro Lauf)
- **Was der Workflow NICHT liest:**  (z. B. archivierte Mails, Dateien aelter als 7 Tage)

## Ausgabe
- **Ziel:**  (z. B. Datei `./triage/<datum>.md`, Slack-Channel #team-updates)
- **Format:**  (z. B. Markdown mit fuenf Abschnitten, Kopfzeile mit Zaehlern)
- **Was der Workflow NICHT erzeugt:**  (z. B. keine verschickten Mails, keine geschlossenen Tickets)

## Komponenten
- **Slash-Command / Cowork-Skill:**  (Pfad oder Name)
- **Subagents:**  (Liste mit Modell und Tool-Umfang je Subagent)
- **MCPs:**  (benoetigte Connectors, Scope "lesen" oder "schreiben")
- **Hooks:**  (falls vorhanden, welches Ereignis und welcher Befehl)

## Guardrails
- **Kein automatisches Versenden:**  ja / nein — wenn nein, warum
- **Abbruchpunkte:**  (welche Stellen halten an und fragen nach?)
- **Logging:**  (wohin, wie lange Aufbewahrung)
- **Kosten-Obergrenze:**  (z. B. max. 30 Tool-Aufrufe pro Lauf, max. 1x taeglich)

## Typischer Fertig-Zustand
Was sehe ich am Ende eines erfolgreichen Laufs? Welche Kennzahlen liegen im Normalbereich?

## Warnsignale
Drei bis fuenf Dinge, bei denen der Workflow verdaechtig aussieht — gekoppelt an eine Handlungsanweisung ("wenn X, dann Y pruefen").

## Abhaengigkeiten
- **Was muss installiert / verbunden sein?**
- **Welche Umgebungsvariablen oder Secrets werden vorausgesetzt?**
- **Welche anderen Workflows laufen davor oder danach?**

## Aenderungsprotokoll
- **YYYY-MM-DD:**  Erstanlage durch <Name>
- **YYYY-MM-DD:**  <Aenderung> durch <Name>
```

Dieser Steckbrief ist keine bürokratische Übung. Er ist das, was Sie in drei Monaten **sich selbst** erklären müssen, wenn Sie einen Workflow nach einer längeren Pause wieder anfassen — und was Sie in sechs Monaten **jemand anderem** erklären müssen, wenn Sie die Verantwortung übergeben. Die zehn Minuten Aufwand beim Anlegen sparen Stunden beim Wiedereinstieg. Wenn Sie nur ein einziges Template aus diesem Kapitel übernehmen, nehmen Sie dieses.

---

## Woran Sie erkennen, dass ein Agent aus dem Ruder läuft

Sie müssen nicht neben Ihrem Agenten sitzen, um Probleme zu sehen. Sechs Warnsignale, an denen sich ein Problem meist ankündigt:

**Signal 1: Die Laufzeit ist auffällig anders.** Ein Workflow, der normalerweise zwei Minuten braucht, läuft plötzlich zwölf Minuten. Das kann zwei Gründe haben: Die Eingabedaten sind viel größer geworden (OK), oder der Agent hat sich in einer Schleife verfangen und macht dieselbe Suche wieder und wieder (nicht OK). Schauen Sie ins Log.

**Signal 2: Auffällige Häufung von Tool-Aufrufen.** Ein Workflow, der pro Lauf normalerweise 20 Tool-Aufrufe macht, macht plötzlich 150. Das ist fast immer ein Zeichen, dass der Agent nicht mehr weiterkommt und es mit Varianten probiert. Brechen Sie den Lauf ab und schauen Sie, wo er hängengeblieben ist.

**Signal 3: Der Abschlussbericht wird wortkarger.** Ein Workflow, dessen Abschlussbericht sonst detailliert war, liefert plötzlich „Fertig. 3 Fehler, aber die sind OK." Das ist ein Alarmsignal. Ein guter Agent wird nicht lakonisch — das ist meist ein Zeichen, dass er Probleme verschweigt, um das Ziel zu „erreichen".

**Signal 4: Die Kennzahlen wandern.** Ein Monatsreport, der drei Monate lang im erwarteten Rahmen war, zeigt plötzlich Werte, die völlig aus dem Rahmen fallen. Ursachen: echter Geschäftsvorfall (prüfen), fehlerhafter Rohdatenexport (prüfen), Agent hat einen Schritt falsch berechnet (prüfen). Alle drei sind denkbar, alle drei brauchen eine Antwort, bevor Sie den Bericht weiterreichen.

**Signal 5: Der Fact-Checker oder Zahlen-Prüfer ändert plötzlich seine Meldungen.** Wenn der Fact-Checker monatelang 80% grün, 15% gelb, 5% rot meldet, und nun plötzlich 95% grün, 0% rot: Das sieht harmlos aus, ist aber verdächtig. Vielleicht hat jemand die Systemprompt des Fact-Checkers verändert und dabei die kritische Prüfung weicher gemacht. Versionieren Sie Ihre Subagents in Git und schauen Sie bei plötzlichen Änderungen nach, woran das liegt.

**Signal 6: Kunden oder Kolleginnen melden Unstimmigkeiten.** Die ehrlichste Rückmeldung. Wenn ein Kunde sagt „die Zahlen im Report stimmen nicht mit meinen überein", dann nehmen Sie das als erstes Signal, nicht als letztes. Der Agent hat wahrscheinlich einen Prozess-Schritt übersprungen oder eine Spalte falsch interpretiert, und Ihr eigener Sanity-Check hat es nicht gefangen.

---

## Der Mensch in der Schleife — wann, wie, wie oft?

„Human in the loop" ist kein einzelner Schalter. Es ist ein Spektrum, und je nach Aufgabe sitzen Sie an einer anderen Stelle.

**Stufe 1: Aufsicht pro Schritt.** Sie sehen jeden Schritt, bestätigen jeden Tool-Aufruf, lesen jede Zwischenausgabe. Das ist der Modus der ersten zehn Läufe eines neuen Workflows. Langsam, aber sicher.

**Stufe 2: Aufsicht am Kontrollpunkt.** Sie lassen den Workflow laufen, aber er hält an definierten Kontrollpunkten an und wartet auf Ihre Freigabe. Typisch für produktive Workflows, bei denen einzelne Schritte kritisch sind (z. B. bevor ein Report versendet wird).

**Stufe 3: Aufsicht über das Endergebnis.** Der Workflow läuft durch und zeigt Ihnen am Ende den Report. Sie prüfen die Zusammenfassung und geben frei. Das ist der Normalmodus für stabile Workflows wie die E-Mail-Triage — Sie lesen den Triage-Bericht, aber Sie greifen nicht in jeden Schritt ein.

**Stufe 4: Aufsicht per Stichprobe.** Der Workflow läuft automatisch, meldet Ihnen nur, wenn etwas auffällig ist, und Sie prüfen ab und zu stichprobenhaft. Das ist der Endzustand für wirklich stabile Routineaufgaben. Wichtig: Die Stichprobe ist nicht verhandelbar. „Ab und zu" heißt einmal pro Woche, und es heißt **wirklich nachschauen**, nicht nur einen Haken setzen.

**Stufe 5: Keine Aufsicht.** Gibt es in den hier beschriebenen Workflows nicht. Für produktive Automatisierungen mit Außenwirkung ist diese Stufe nicht erreichbar — und das ist kein Fehler, sondern Absicht.

Bei neuen Workflows starten Sie auf Stufe 1, wandern über mehrere Wochen nach Stufe 3 und bleiben dort. Stufe 4 ist für Aufgaben reserviert, die Sie jeden Tag mehrfach haben und bei denen das Einzelergebnis wenig Schaden anrichten kann. Erwarten Sie nicht, einen neuen Workflow schnell auf Stufe 3 oder gar 4 zu bekommen — das Vertrauen wächst mit jeder sauberen Woche.

---

## Kosten im Griff behalten

Ein paar praktische Routinen zur Kostenkontrolle:

**Einmal pro Woche Token-Verbrauch checken.** In Claude Code mit `/cost`, in Cowork in den Einstellungen unter Nutzung. Sie wollen wissen, ob der Verbrauch stabil ist oder plötzlich wächst.

**Einmal pro Monat die aktiven Workflows durchgehen.** Fünf Minuten. Fragen: Läuft jeder Workflow noch zuverlässig? Brauche ich ihn noch? Gibt es welche, die ich seit Wochen nicht mehr angeschaut habe und die im Hintergrund Kosten erzeugen?

**Modell-Wahl bewusst treffen.** Kein Grund, Opus 4.6 für Haiku-Aufgaben einzusetzen. Kein Grund, Haiku 4.5 für Opus-Aufgaben einzusetzen. Der `mail-klassifizierer` auf Haiku-Basis ist zwanzigmal billiger als auf Opus-Basis — bei identischem Ergebnis in dieser Aufgabenklasse. Der `fact-checker` auf Sonnet-Basis trifft einen guten Mittelweg. Der `protokoll-formatter` ebenfalls. Opus 4.6 würde ich nur für Planer-Workflows einsetzen, bei denen die eigentliche Denkarbeit komplex ist — reine Formatierer brauchen es nicht.

**Teure Workflows erkennen und isolieren.** Wenn ein Workflow in der Statistik auffällt (zum Beispiel die mehrstufige Recherche-Pipeline), überlegen Sie: Brauche ich wirklich jede Recherche in voller Tiefe, oder könnte ich eine „leichte" Variante für einfache Fragen haben? Zwei Workflows mit unterschiedlicher Tiefe sind oft sparsamer als ein Workflow, der immer auf maximaler Stufe läuft.

---

## Die Verbindung zu Kapitel 14

Dieses Kapitel und Kapitel 14 (Ethik, Sicherheit und Verantwortung) sind zwei Seiten derselben Medaille. Kapitel 14 erklärt die **Regeln und Risiken**, dieses Kapitel zeigt die **Werkzeuge**. Sie sollten keines der beiden ohne das andere lesen, wenn Sie produktiv Agenten einsetzen wollen.

Zwei Verknüpfungen sind besonders wichtig und sollten jetzt explizit sein:

**DSGVO in der E-Mail-Triage.** Sobald ein Agent Mails liest, die personenbezogene Daten enthalten (also fast alle geschäftlichen Mails), sind Sie im DSGVO-Anwendungsbereich. Der Remote-Gmail-Connector sendet Inhalte durch Anthropics Systeme. Ob das für Ihre Organisation rechtlich tragbar ist, hängt von Ihrem Datenschutzkonzept und der Art der Mails ab. Bei sensiblen Inhalten (Gesundheitsdaten, besondere Kategorien nach Art. 9 DSGVO) ist die Antwort oft nein — oder nur mit lokaler Verarbeitung. Kapitel 14 Teil 02 geht das im Detail durch; lesen Sie es, bevor Sie die E-Mail-Triage produktiv einsetzen.

**Halluzinationen in der Recherche-Pipeline.** Der Fact-Checker aus Teil 06 ist der wichtigste Schutz gegen Halluzinationen, den dieses Kapitel einführt. Aber er ist nicht perfekt. Er prüft gegen Quellen — aber die Auswahl der Quellen trifft der Hauptagent, und wenn der bei der Suche schon die falschen Quellen findet, liest der Fact-Checker die „richtigen falschen Informationen". Kapitel 14 Teil 04 (Halluzinationen erkennen) beschreibt die allgemeinen Mechanismen und Gegenstrategien, und Ihre Pipeline sollte sich daran orientieren.

Die simple Regel, die sich durch beide Kapitel zieht: **Je autonomer der Agent, desto wichtiger die Kontrolle am Ende.** Ein Chatbot, den Sie jeden Schritt begleiten, kann wenig allein falsch machen. Ein Agent, der fünf Subagents koordiniert und am Ende einen fertigen Bericht liefert, kann viel allein falsch machen — und genau deshalb darf sein Endergebnis nicht ungeprüft in die Welt.

---

## Eine realistische Erwartung für die kommenden Monate

Zum Schluss ein vorsichtiger Ausblick. Prognosen im KI-Bereich haben eine kurze Haltbarkeit, und dieses Kapitel möchte Sie nicht mit selbstsicheren Vorhersagen füttern, die in drei Monaten überholt sind. Stattdessen zwei Richtungen, in die das Feld erfahrungsgemäß tendiert — und eine Warnung, was sich erfahrungsgemäß eben **nicht** verbessert.

**Was sich tendenziell verbessert.** Die Qualität der Planner, die Treffsicherheit der Werkzeugwahl, die Integration zwischen Claude Code und Cowork, die Zahl verfügbarer MCPs, die Einfachheit der Einrichtung. Die Erfahrung der letzten zwei Jahre legt nahe, dass Workflows, die heute drei oder vier Schritte brauchen, im Lauf des Jahres mit weniger Schritten auskommen. Ob das in Ihrem konkreten Fall auch so kommt, hängt von Ihrem Anwendungsgebiet ab — der Trend ist nicht gleichverteilt über alle Aufgabenklassen.

**Was sich erfahrungsgemäß nicht verbessert.** Die Notwendigkeit menschlicher Freigabe bei Außenwirkung. Die Wichtigkeit sauberer Eingangsdaten. Die Anfälligkeit von Agenten bei widersprüchlichen Informationen. Die Fehler, die passieren, wenn jemand Guardrails abschaltet, um schneller zu sein. Diese Punkte sind in den letzten Jahren stabil geblieben und werden voraussichtlich stabil bleiben — mit einer leichten Verschiebung: Je mächtiger die Modelle, desto leichter rutscht man in Vertrauensfehler.

**Was Sie tun sollten, unabhängig vom Ausblick.** Klein anfangen. Einen Workflow bauen, ihn stabil bekommen, Vertrauen aufbauen, dann den zweiten. Nicht gleichzeitig fünf Workflows hochziehen — die Lernkurve ist in der Menge flacher, und Sie verlieren den Überblick. Und: regelmäßig zurück zu Kapitel 14. Die Technik wird besser, die Verantwortung bleibt bei Ihnen.

---

## Kernbotschaft

Automatisierung lohnt sich bei wiederkehrenden Aufgaben ab 15 Minuten Dauer und mehrfacher Wiederholung pro Woche. Sieben Guardrails sind Pflicht: **Tool-Minimalismus, keine Außenwirkung ohne Freigabe, Abbruchpunkte bei Unsicherheit, Logging, Kosten-Obergrenzen, Starttests in der sicheren Ecke, dokumentierte Ownership.** Der Mensch im Workflow wandert vom Schritt-für-Schritt-Mitblick zur Stichproben-Aufsicht; die Stufe „ganz ohne Aufsicht" gibt es in produktiven Workflows mit Außenwirkung nicht. Ohne Kapitel 14 (DSGVO, Halluzinationen) bleibt dieses Kapitel unvollständig.

---

## Abschluss des Kapitels

Mit diesem Teil endet Kapitel 12. Sie wissen jetzt, was ein Agent ist und was nicht (Teil 01), welche Werkzeuglandschaft Sie haben (Teil 02), wie MCP als Universal-Schnittstelle funktioniert (Teil 03), wie Sie Subagents, Hooks und Slash-Commands in Claude Code bauen (Teil 04), wie Sie vier konkrete Workflows aufsetzen (Teile 05 und 06), und welche Guardrails und Betriebsregeln diese Workflows zusammenhalten (Teil 07).

Wenn Sie aus diesem Kapitel nur zwei Dinge mitnehmen, sollten es diese sein:

**Erstens:** Ein Agent ist ein Sprachmodell in einer Schleife, das Werkzeuge benutzen darf und selbst entscheidet, wann es fertig ist. Das ist die Definition, an der Sie jedes neue „Agent-Framework" messen können.

**Zweitens:** Die Qualität eines Agenten zeigt sich nicht in dem, was er kann, sondern in dem, was er **nicht tut, ohne zu fragen**. Agenten, die an den richtigen Stellen anhalten und nachfragen, sind die nützlichsten. Agenten, die „einfach durchziehen", sind die gefährlichsten.

Alles andere ist Handwerk, und Handwerk wird mit Übung besser. Fangen Sie mit einem Workflow an, bleiben Sie eine Weile dort, lernen Sie, wo Ihr Agent zuverlässig ist und wo nicht. Dann der zweite. Dann der dritte. Nach sechs Monaten haben Sie einen kleinen Betrieb, der für Sie mitarbeitet — und der Ihnen nicht die Kontrolle entzieht, weil Sie von Anfang an darauf geachtet haben.

---

## Ein Vier-Wochen-Plan für den ersten Agenten

Viele Leserinnen und Leser lesen dieses Kapitel, nicken innerlich zu allem — und dann passiert doch nichts, weil der Einstieg unklar bleibt. Für diesen Fall hier ein konkreter, realistischer Vier-Wochen-Plan. Er setzt voraus, dass Sie sich pro Woche zwei bis drei Stunden nehmen können. Schneller geht es, langsamer auch — aber in dieser Taktung ist die Lernkurve am angenehmsten.

**Woche 1 — Den Mini-Agent in Cowork bauen.** Lesen Sie **Teil 04b** (Mini-Agent in 15 Minuten) und bauen Sie den Wochenrückblick-Assistenten. Lassen Sie ihn am Freitag einmal laufen, prüfen Sie das Ergebnis, notieren Sie, was Ihnen nicht gefällt. Ziel dieser Woche: Sie haben erlebt, dass ein Agent Ihnen Arbeit abnimmt, ohne dass Sie ein Terminal anfassen mussten.

**Woche 2 — Den Mini-Agent stabilisieren.** Lassen Sie den Wochenrückblick jeden Tag der Woche einmal laufen (auch wenn es nur der „Tag-Rückblick" wird). Verbessern Sie den Prompt nach jeder Runde einmal. Legen Sie dabei den ersten **Workflow-Steckbrief** an (Template in diesem Tutorial). Am Ende der Woche haben Sie einen Workflow, dem Sie vertrauen, und eine Vorlage, mit der Sie den nächsten schneller bauen.

**Woche 3 — Den zweiten Workflow wählen und starten.** Schauen Sie sich **Teil 05** (E-Mail-Triage und Meeting-Notes) an und wählen Sie *einen* der beiden Use-Cases aus — nicht beide. Wenn Sie sich Claude Code zutrauen, bauen Sie den Workflow wie dort beschrieben; wenn nicht, bleiben Sie in Cowork und nutzen die „Cowork-Variante in Kürze" aus Teil 05. Ziel dieser Woche: Ein zweiter laufender Workflow, mit einem eigenen Steckbrief.

**Woche 4 — Guardrails setzen und entscheiden, wohin es weitergeht.** Lesen Sie Teil 07 noch einmal mit Blick auf die sieben Guardrails und prüfen Sie für beide Workflows, welche davon Sie tatsächlich umgesetzt haben. Ergänzen Sie fehlende Punkte — meist Logging und klare Abbruchpunkte. Entscheiden Sie am Ende der Woche bewusst: Reichen mir diese zwei Workflows für jetzt? Oder will ich in die Tiefe (Teil 04, Teil 06)? Oder will ich in die Breite (weitere kleine Workflows nach dem Muster von 04b)? Alle drei sind legitime Antworten.

**Was Sie nach vier Wochen haben.** Zwei laufende Workflows mit Steckbrief, ein Gefühl für das, was funktioniert und was nicht, und eine bewusste Entscheidung über Ihren nächsten Schritt. Das ist mehr, als die meisten nach vier Wochen intensivem Lesen aus diesem Kapitel mitnehmen — und es ist genug, um den Unterschied im Alltag zu spüren. Widerstehen Sie der Versuchung, in Woche 1 gleich Subagents, Hooks und Slash-Commands auszuprobieren. Der wichtigste Wert der ersten zwei Wochen ist Vertrauen in den Mechanismus, nicht Feature-Tiefe.

---

## Ein Ausblick auf Kapitel 13 — Content-Workflows

Kapitel 13 (KI und Kreativarbeit) wird auf das Fundament dieses Kapitels aufsetzen. Die Werkzeuge sind dieselben — Subagents, Skills, Slash-Commands, Cowork — aber das Anwendungsfeld wechselt von Büroroutine zu **Content-Produktion**: Blog-Artikel vom Briefing bis zur Veröffentlichung, LinkedIn-Posts in der Stimme einer bestimmten Marke, Newsletter-Serien, die aus einem Thema drei Formate erzeugen (Text, Grafik, Kurz-Video-Skript), Podcast-Shownotes aus einem Roh-Transkript. Das Muster, das Sie aus Teil 05 und 06 kennen — **klare Quelle, enger Subagent, definiertes Ausgabeformat, keine Außenwirkung ohne Freigabe** — trägt dort genauso. Nur sind die „Quellen" nicht Posteingänge, sondern Ideen-Listen und Redaktionspläne, und die „Ausgabeformate" nicht Markdown-Reports, sondern veröffentlichungsfertige Artikel und Grafiken.

Wenn Sie die Workflows aus diesem Kapitel beherrschen, haben Sie bereits 80 Prozent dessen, was Kapitel 13 von Ihnen erwartet. Die neuen 20 Prozent sind vor allem Stilarbeit: eine **Voice-Guide-Subagent** statt eines Fact-Checkers, ein **Markenbild-Skill** statt eines Zahlen-Prüfers, eine Redaktions-Review-Station vor jeder Veröffentlichung. Das Guardrail „Keine Außenwirkung ohne Freigabe" wird dort besonders wichtig, weil Content-Fehler öffentlich sichtbar sind — eine falsche Zahl in einem internen Monatsreport kann man nachbessern, einen schon veröffentlichten Post mit falscher Aussage nicht.

Kurz gesagt: Das, was Sie hier gelernt haben, gilt dort weiter — und wenn Sie auf Teil 05 stabil sind, sind Sie für Kapitel 13 bereit.

---

## Nächste Schritte

- **Zurück zur Übersicht:** [README](./README.md)
- **Kapitel 14 (Ethik, Sicherheit und Verantwortung)** — wenn nicht schon gelesen, jetzt der richtige Zeitpunkt. Insbesondere Teil 02 (DSGVO) und Teil 04 (Halluzinationen).
- **Kapitel 11 Teil 07 (Sanity-Checks und Praxisleitfaden)** — die Grundlage des Zahlen-Prüfers aus Teil 06, jetzt rückwärts gelesen mit der Frage: Welche der dortigen Routinen lassen sich noch in Subagents übersetzen?
- **Kapitel 15 (KI im Team — Zusammenarbeit und Change)**, sobald es existiert — für die Frage, wie Sie Agenten-Workflows in eine Organisation bringen, ohne dass sie individueller Heldenkram bleiben.
