# ChatGPT als persönlicher AI-Copilot: Kompletter Setup-Guide nach dem EVA-Prinzip

## Wozu dient dieser Prompt?

Stellen Sie sich vor, Sie hätten einen persönlichen Assistenten, der jeden Abend Ihre Notizen sortiert und jeden Morgen ein Briefing für den Tag erstellt — automatisch, ohne dass Sie daran denken müssen. Genau das baut dieser Guide auf.

Das **EVA-Prinzip** — ein einfaches Denkmodell aus der Informatik (Eingabe → Verarbeitung → Ausgabe) — wird hier zum persönlichen Produktivitätssystem:
- **Eingabe:** Sie werfen tagsüber Gedanken, Notizen und To-Dos in einen Chat
- **Verarbeitung:** ChatGPT analysiert und strukturiert alles automatisch am Abend
- **Ausgabe:** Sie bekommen morgens ein fertiges Briefing mit Prioritäten

## So verwenden Sie den Guide

Dieser Guide besteht aus **4 Prompts**, die aufeinander aufbauen. Sie brauchen ein **ChatGPT Plus-Abo** (für die Tasks/Schedules-Funktion).

| Schritt | Prompt | Dauer | Was passiert |
|---------|--------|-------|-------------|
| 1 | Profil-Erstellung | 10–15 Min | ChatGPT lernt Sie kennen |
| 2A oder 2B | Co-Pilot Setup | 5 bzw. 15–20 Min | Automatische Briefings einrichten |
| 3 | Test-Inputs | 2 Min | System testen |
| 4 | Weekly Memory Sync | 1 Min | Wöchentliche Gedächtnispflege |

**Zwei Wege zum Ziel:**
- ⚡ **Quick Mode** (Prompt 1 überspringen → direkt Prompt 2A): In 5 Minuten startklar. Abend-Review + Morgen-Briefing, ohne Personalisierung.
- 🎯 **Pro Mode** (Prompt 1 → dann Prompt 2B): Vollständiges Profil, persönliche Begrüßung, formatierte Ausgaben, zusätzliches Wochen-Review am Sonntag. Bessere Ergebnisse, weil ChatGPT Sie kennt.

### 💡 Tipps

- **ChatGPT Memory aufräumen:** Gehen Sie vor dem Start in *Settings → Personalization → Memory* und löschen Sie veraltete oder falsche Einträge. Das macht Ihr Profil genauer.
- **Schedule-Zeiten anpassen:** Nach dem Setup können Sie die Uhrzeiten unter *Settings → Schedules* ändern. Die Zeiten können um einige Minuten abweichen — ChatGPT Schedules sind keine sekundengenauen Wecker.
- **Was ist ein Schedule?** Wenn Sie den Prompt senden, erstellt ChatGPT automatisch einen wiederkehrenden Task. Sie sehen den unter *Settings → Schedules* und können ihn dort bearbeiten oder löschen.
- **Nicht jede Nachricht braucht eine Antwort:** Der Co-Pilot-Chat ist Ihr Notizbuch. Werfen Sie rein, was Ihnen einfällt — ChatGPT sortiert es abends.

> ⚠️ **Voraussetzung:** Sie brauchen **ChatGPT Plus** (oder Team/Enterprise). Die kostenlose Version unterstützt keine Tasks/Schedules. Die Memory-Funktion muss in den Settings aktiviert sein.

> 📅 **Kalender-Hinweis:** ChatGPT hat **keinen direkten Zugriff** auf Ihren Google- oder Outlook-Kalender. Wenn im Prompt „Check meinen Kalender" steht, bezieht sich das auf Termine, die Sie **selbst in den Chat geschrieben haben** (z.B. „Meeting Dienstag 10:00"). Je mehr Sie reinwerfen, desto besser werden die Briefings.

---

## Prompt 1: Profil-Erstellung

**Ziel:** ChatGPT analysiert, was es bereits über Sie weiß, und erstellt ein strukturiertes Profil. Das verbessert alle zukünftigen Interaktionen.

**Wann verwenden:** Nur im Pro Mode. Wenn Sie den Quick Mode wählen, überspringen Sie diesen Prompt und gehen direkt zu Prompt 2A.

```
Ich möchte, dass du ein umfassendes Profil über mich erstellst,
basierend auf allem, was du über mich weißt.

<aufgabe>
1. Analysiere dein Memory — gehe durch alle Informationen,
   die du über mich gespeichert hast.

2. Erstelle ein strukturiertes Profil mit folgenden Abschnitten:

<ueber_mich>
- Wer bin ich? (Name, Beruf, Rolle)
- Was mache ich beruflich?
- Was sind meine Hauptinteressen?
</ueber_mich>

<projekte_und_arbeit>
- Welche Projekte bearbeite ich aktuell?
- In welchen Bereichen arbeite ich?
- Was sind wiederkehrende Themen?
</projekte_und_arbeit>

<kommunikationsstil>
- Wie schreibe/kommuniziere ich?
- Welche Sprache(n) nutze ich?
- Formell oder informell?
</kommunikationsstil>

<prioritaeten_und_werte>
- Was ist mir wichtig?
- Welche Ziele verfolge ich?
- Was sind wiederkehrende Muster?
</prioritaeten_und_werte>

<kontext>
- Welche Tools/Apps nutze ich?
- Mit wem arbeite ich zusammen?
- Welche Gewohnheiten habe ich?
</kontext>

3. Stelle Rückfragen: Für jeden Bereich, wo du unsicher bist
   oder Infos fehlen, stelle mir konkrete Fragen.
   Ich werde sie beantworten, und du aktualisierst das Profil.

4. Speichere ins Memory: Nachdem wir fertig sind, speichere
   die wichtigsten Erkenntnisse in dein Memory.
</aufgabe>

Markiere Bereiche, wo du unsicher bist, mit [?].
Starte jetzt mit dem Profil basierend auf deinem aktuellen Wissen über mich.
```

**Was dann passiert:**
1. ChatGPT zeigt Ihnen, was es über Sie weiß
2. Sie sehen Lücken und Fehler
3. Sie beantworten Rückfragen
4. ChatGPT speichert die korrigierten Infos

---

## Prompt 2A: Co-Pilot Setup — Quick Mode

**Ziel:** Einen Chat einrichten, der als persönlicher Sammelort dient, mit automatischem Abend-Review und Morgen-Briefing.

```
Ich möchte diesen Chat als mein persönliches Co-Pilot-System nutzen.

<wie_ich_diesen_chat_nutze>
Tagsüber werfe ich hier Notizen, Gedanken, Ideen, To-Dos und Updates rein.
Du musst NICHT auf jede Nachricht antworten — behandle sie als Input für später.
Antworte nur kurz mit "✓" oder gar nicht, außer ich stelle eine direkte Frage.
</wie_ich_diesen_chat_nutze>

<abend_review>
Erstelle einen Schedule, der jeden Abend um 21:00 Uhr läuft:
- Schau dir alles an, was ich heute in diesen Chat geworfen habe
- Fasse die wichtigsten Punkte zusammen
- Identifiziere offene To-Dos und nächste Schritte
- Verbinde neue Infos mit dem, was du bereits über mich weißt (Memory)
- Notiere Muster oder wiederkehrende Themen
</abend_review>

<morgen_briefing>
Erstelle einen Schedule, der jeden Morgen um 07:00 Uhr läuft:
- Check meinen Kalender für heute
- Erinnere mich an die wichtigsten Termine und Deadlines
- Zeig mir die Top 3 Prioritäten basierend auf:
  - Meinen Wochenzielen (siehe unten)
  - Offenen To-Dos aus den letzten Tagen
  - Was ich gestern nicht geschafft habe
- Gib mir einen kurzen Fokus-Satz für den Tag
</morgen_briefing>

<wochenziele>
Meine Wochenziele (KW XX):
1. [ZIEL 1 — z.B. "Newsletter-Artikel fertig schreiben"]
2. [ZIEL 2 — z.B. "Kundenprojekt X abschließen"]
3. [ZIEL 3 — z.B. "3x Sport diese Woche"]
</wochenziele>

Erstelle die beiden Schedules (21:00 Abend-Review, 07:00 Morgen-Briefing)
und bestätige mir, wenn sie aktiv sind.
```

---

## Prompt 2B: Co-Pilot Setup — Pro Mode

**Ziel:** Vollständiges System mit Abend-Review, Morgen-Briefing UND Wochen-Review — mit voller Kontext-Integration aus Ihrem Profil (Prompt 1).

**Wann verwenden:** Nur wenn Sie Prompt 1 (Profil-Erstellung) bereits durchgearbeitet haben.

```
Ich möchte diesen Chat als mein persönliches Co-Pilot-System nutzen.
Du kennst mich bereits aus unserem Profil-Gespräch.

<wie_ich_diesen_chat_nutze>
Tagsüber werfe ich hier Notizen, Gedanken, Ideen, To-Dos und Updates rein.
Du musst NICHT auf jede Nachricht antworten — behandle sie als Input für später.
Antworte nur kurz mit "✓" oder gar nicht, außer ich stelle eine direkte Frage.
</wie_ich_diesen_chat_nutze>

<mein_kontext>
Du kennst mich bereits aus unserem Profil-Gespräch. Nutze ALLES was du
über mich weißt:
- Mein Profil (Name, Beruf, Projekte)
- Meinen Kommunikationsstil
- Meine Prioritäten und Werte
- Meine laufenden Projekte und Deadlines

Je mehr Kontext du einbeziehst, desto besser werden deine Briefings.
</mein_kontext>

<abend_review>
Erstelle einen Schedule, der jeden Abend um 21:00 Uhr läuft:
- Fasse zusammen, was ich heute in diesen Chat geworfen habe
- Identifiziere offene To-Dos und nächste Schritte
- Verbinde neue Infos mit meinem Profil und laufenden Projekten
- Notiere Muster oder wiederkehrende Themen
- Priorisiere: Was ist dringend, was kann warten?
- Schlage vor, was ins Memory gespeichert werden sollte

Output-Format:
🌙 TAGES-REVIEW [Datum]
📝 Was heute reinkam: [Zusammenfassung]
✅ Erledigt: [Was abgeschlossen wurde]
📋 Offen: [To-Dos für morgen]
💡 Notizen: [Muster, Verbindungen]
</abend_review>

<morgen_briefing>
Erstelle einen Schedule, der jeden Morgen um 07:00 Uhr läuft:
- Begrüße mich persönlich (du kennst meinen Namen)
- Check meinen Kalender für heute
- Erinnere mich an die wichtigsten Termine und Deadlines
- Zeig mir die Top 3 Prioritäten basierend auf:
  - Meinen Wochenzielen
  - Meinen laufenden Projekten
  - Offenen To-Dos aus den letzten Tagen
  - Was ich gestern nicht geschafft habe
- Gib mir einen personalisierten Fokus-Satz für den Tag

Output-Format:
☀️ GUTEN MORGEN [Name], [Datum]
📅 Heute im Kalender: [Termine]
🎯 Deine Top 3 für heute:
1. [Priorität 1]
2. [Priorität 2]
3. [Priorität 3]
📊 Wochenziel-Status:
- Ziel 1: [X]%
- Ziel 2: [X]%
- Ziel 3: [X]%
💪 Fokus heute: "[Personalisierter Fokus-Satz]"
</morgen_briefing>

<wochen_review>
Erstelle einen Schedule, der jeden Sonntag um 18:00 Uhr läuft:
- Fasse die Woche zusammen
- Was wurde erreicht vs. geplant?
- Welche Muster sind aufgefallen?
- Schlage Ziele für nächste Woche vor
</wochen_review>

<wochenziele>
Meine Wochenziele (KW XX):
1. [ZIEL 1 — z.B. "Artikel fertig schreiben"]
2. [ZIEL 2 — z.B. "Kundenprojekt X abschließen"]
3. [ZIEL 3 — z.B. "3x Sport diese Woche"]
</wochenziele>

Erstelle die drei Schedules (21:00 Abend-Review, 07:00 Morgen-Briefing,
Sonntag 18:00 Wochen-Review) und bestätige mir, wenn sie aktiv sind.
```

---

## Prompt 3: Test-Inputs

**Ziel:** Das System testen — werfen Sie ein paar Beispiel-Notizen in den Chat und prüfen Sie, ob das Abend-Review funktioniert.

Kopieren Sie die folgenden 5 Beispiel-Nachrichten und senden Sie sie **einzeln** über den Tag verteilt (oder alle auf einmal zum Testen):

```
Call mit Thomas von Acme Corp war gut. Sie wollen das Projekt bis Ende Q1
abschließen. Budget ist 15k, Timeline 6 Wochen. Nächster Schritt:
Angebot schicken bis Freitag.
```

```
Idee für Newsletter: Artikel über ChatGPT Schedules als Personal Co-Pilot.
Könnte gut ankommen.
```

```
Reminder: Zahnarzt nächste Woche Dienstag 14:00 nicht vergessen.
```

```
Feedback von Lisa zum Pitch-Deck bekommen. Slide 3-5 zu textlastig.
Überarbeiten vor Meeting am Donnerstag.
```

```
Sport heute geschafft ✓
Angebot für Acme noch nicht geschrieben — morgen erste Priorität
```

**Tipp zum Testen:** Sie müssen nicht bis 21:00 Uhr warten. Schreiben Sie nach den Test-Inputs einfach: *„Mach jetzt ein Abend-Review über die heutigen Inputs."* — dann sehen Sie sofort, ob alles funktioniert.

**Was Sie beim Abend-Review erwarten sollten:** ChatGPT fasst die Notizen zusammen und identifiziert:
- **Deadline:** Angebot für Acme bis Freitag
- **Deadline:** Pitch-Deck überarbeiten vor Donnerstag
- **Termin:** Zahnarzt Dienstag 14:00
- **Offene Idee:** Newsletter-Artikel über ChatGPT Schedules
- **Erledigt:** Sport ✓

---

## Prompt 4: Weekly Memory Sync

**Ziel:** Einmal pro Woche das Gedächtnis von ChatGPT aufräumen und aktualisieren.

> ⚠️ **Technische Einschränkung:** ChatGPT kann in Chats mit aktiven Schedules aktuell **nicht ins Memory schreiben**. Deshalb generiert dieser Schedule einen klickbaren Link, der eine neue Konversation öffnet und die Erkenntnisse dort ins Memory speichert. Ein Klick — fertig.

```
Erstelle einen Schedule, der jede Woche am Sonntag um 18:00 Uhr läuft.

<weekly_sync_aufgabe>
1. Analysiere die gesamte Konversation der vergangenen Woche in diesem Chat.

2. Extrahiere folgende Kategorien:
   - Wichtige Erkenntnisse über mich (Ziele, Präferenzen, Arbeitsweise, Werte)
   - Neue langfristige Projekte, Routinen oder Systeme
   - Wiederkehrende Muster oder explizit genannte Ziele
   - Alles, was sinnvoll wäre, dauerhaft im Memory zu speichern

3. Erstelle eine klar strukturierte Memory-Zusammenfassung:
   - Kurz und präzise
   - Ohne Interpretation oder Ausschmückung
   - Nur speicherwürdige Fakten und Ziele
   - Formatiert als Bullet-Points

4. Erzeuge einen klickbaren Markdown-Link, der:
   - Einen neuen ChatGPT-Chat öffnet
   - Den Memory-Text bereits als Input enthält
   - Mit der Anweisung beginnt: "Bitte speichere die folgenden
     Informationen dauerhaft in mein Memory:"

   Link-Format (exakt so erstellen):
   [🧠 Memory jetzt speichern](https://chatgpt.com/?q=ENCODED_TEXT)
   Wobei ENCODED_TEXT der URL-encodierte Memory-Text ist.
   
   WICHTIG: Halte den Text kompakt (max. 1500 Zeichen vor Encoding),
   damit der Link nicht an Browser-Längenlimits scheitert.
   Bei einer umfangreichen Woche: nur die wichtigsten Erkenntnisse.
</weekly_sync_aufgabe>

<output_format>
Gib NUR folgendes aus:

🧠 Weekly Memory Sync
Woche: [Datum von] — [Datum bis]

Erkenntnisse dieser Woche:
[Strukturierte Memory-Zusammenfassung als Bullet-Points]

👆 Klicke den Link unten, um diese Erkenntnisse dauerhaft zu speichern:
[🧠 Memory jetzt speichern](https://chatgpt.com/?q=...)
</output_format>

<regeln>
- Der Link MUSS als Markdown-Link formatiert sein
- Der Link-Text muss URL-encoded sein (Leerzeichen = %20, Umlaute encoded)
- Keine zusätzlichen Erklärungen oder Meta-Kommentare
- Ziel ist maximale Reibungslosigkeit beim Memory-Transfer
</regeln>
```

**So funktioniert der Memory Sync:**
1. **Sonntag 18:00:** Der Schedule läuft automatisch
2. **Zusammenfassung:** Sie erhalten eine strukturierte Übersicht der Woche
3. **Ein Klick:** Sie klicken auf den generierten Link
4. **Neuer Chat:** Es öffnet sich ein neuer ChatGPT-Chat mit dem Memory-Text
5. **Auto-Save:** ChatGPT speichert die Informationen ins Memory

> 💡 **Was sind Memory-Einträge?** ChatGPT merkt sich Dinge, die Sie ihm erzählen — z.B. Ihren Namen, Ihren Beruf oder Ihre Projekte. Diese „Erinnerungen" finden und verwalten Sie unter *Settings → Personalization → Memory*. Das Limit liegt bei ca. 200 Einträgen — daher ist der wöchentliche Sync wichtig, damit der Speicher nicht mit veralteten Infos volläuft.

**Alternative — Manueller Memory Sync:**

Falls Sie die Erkenntnisse lieber manuell übertragen möchten, schreiben Sie in Ihren Co-Pilot-Chat:

```
Erstelle eine Zusammenfassung aller wichtigen Erkenntnisse aus unserer
Konversation dieser Woche, die ich in einem neuen Chat ins Memory speichern
sollte. Formatiere sie so, dass ich sie einfach kopieren kann.
```

Dann kopieren Sie das Ergebnis und fügen es in einen neuen Chat ein mit: *„Bitte speichere folgendes dauerhaft in mein Memory: [EINFÜGEN]"*

---

## Pro-Tipps für Ihren Co-Piloten

### Für den Alltag
- **Chat anpinnen:** Dann haben Sie jederzeit sofort Zugriff
- **Wochenziele aktualisieren:** Jeden Sonntag kurz die Wochenziele im Chat updaten
- **Kein Antwort-Zwang:** ChatGPT muss nicht auf jeden Input reagieren
- **Sprache nutzen:** Unterwegs einfach Sprachnachrichten in der ChatGPT-App reinschicken
- **Kürzel etablieren:** z.B. `TODO:` für To-Dos, `IDEE:` für Ideen, `CALL:` für Meeting-Notizen

### Für optimale Ergebnisse
- **Memory regelmäßig pflegen:** Der Weekly Sync (Prompt 4) ist kein Nice-to-have, sondern Pflicht — ChatGPT Memory hat ein Limit (~200 Einträge). Ohne Pflege läuft es voll und alte Infos verdrängen aktuelle.
- **Zeiten anpassen:** Unter *Settings → Schedules* können Sie die Uhrzeiten ändern
- **Prompt anpassen:** Unter *Settings → Schedules* können Sie auch den Schedule-Prompt selbst bearbeiten
- **In Projects nutzen:** Erstellen Sie ein Project „Personal Co-Pilot" und fügen Sie Kontext-Dokumente als Files hinzu

### Häufige Fragen

**Funktionieren Schedules in Projects?**
Ja. Schedules werden auf Conversation-Level erstellt. Wenn Sie einen Schedule in einem Project-Chat erstellen, hat er Zugriff auf die Project Files und Instructions.

**Was wenn ein Schedule nicht läuft?**
Prüfen Sie unter *Settings → Schedules*, ob der Schedule aktiv ist. Manchmal hilft es, ihn zu löschen und neu zu erstellen.

**Wie oft sollte ich die Wochenziele updaten?**
Idealerweise jeden Sonntag. Schreiben Sie einfach: *„Neue Wochenziele KW XX: 1... 2... 3..."* in den Chat.

---

