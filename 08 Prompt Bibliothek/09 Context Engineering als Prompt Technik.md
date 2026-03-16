# Context Engineering: Mit 5 Ebenen zu besseren KI-Antworten

## Wozu dient diese Technik?

„Garbage in, garbage out" — das gilt auch für KI. Obwohl uns versprochen wurde, dass die Formulierung irgendwann egal ist, hat die Qualität der Eingabe Stand heute einen **Rieseneinfluss** auf die Qualität der Ausgabe.

**Context Engineering** geht einen Schritt weiter als klassisches Prompt Engineering: Statt nur die Frage zu optimieren, gestalten Sie den **gesamten Rahmen**, in dem die KI arbeitet. Eine klar definierte Rolle, ein eindeutiges Ziel, die richtigen Daten, der gewünschte Stil und Ihr persönlicher Kontext — zusammen sorgen diese fünf Ebenen dafür, dass die KI nicht raten muss, sondern genau weiß, was Sie brauchen.

## Die 5 Ebenen des Kontextrahmens

| Ebene | Was sie definiert | Leitfrage |
|-------|------------------|-----------|
| 🎭 **Systemkontext** | Rolle und Leitplanken der KI (Fortgeschrittene kennen das als „System Prompt") | *Wer bist du?* |
| 🎯 **Aufgabenkontext** | Zweck und Ziel der Interaktion | *Was soll erreicht werden — und warum?* |
| 📚 **Wissenskontext** | Verfügbare Daten, Dokumente, Regeln | *Worauf basierst du deine Antwort?* |
| 💬 **Interaktionskontext** | Format, Tonfall, Kommunikationsstil | *Wie soll die Antwort aussehen?* |
| 👤 **Situationskontext** | Nutzer, Umgebung, Vorgeschichte | *Für wen und in welcher Situation?* |

**Wichtig:** Es müssen nicht immer alle fünf Ebenen gefüllt sein. Schon zwei oder drei machen einen spürbaren Unterschied. Die 5 Ebenen sind ein Ideal — kein Zwang.

### So funktioniert's

Statt einen flachen Prompt zu schreiben wie *„Fasse die Quartalszahlen zusammen"*, bauen Sie einen Rahmen:

1. **Systemkontext:** Wer soll die KI sein? (Analyst, Coach, Texter…)
2. **Aufgabenkontext:** Was ist die Aufgabe — und was ist das übergeordnete Ziel dahinter?
3. **Wissenskontext:** Welche Daten oder Dokumente soll die KI nutzen? (Dateien anhängen, Fakten mitliefern)
4. **Interaktionskontext:** Wie soll das Ergebnis aussehen? (Tabelle, Stichpunkte, locker, formal…)
5. **Situationskontext:** Wer sind Sie, was ist der Hintergrund? (Branche, Vorwissen, vorherige Schritte)

### 💡 Tipps

- **Schrittweise aufbauen:** Starten Sie mit Systemkontext + Aufgabenkontext. Ergänzen Sie die anderen Ebenen nach Bedarf.
- **XML-Tags nutzen:** Trennen Sie die Ebenen mit spitzen Klammern wie `<systemkontext>` — das hilft der KI, die Abschnitte zu erkennen. Sie müssen nicht wissen, was XML ist — einfach die Klammern aus den Beispielen unten kopieren.
- **Wissenskontext ist der Hebel:** Je spezifischer die Daten, desto besser das Ergebnis. „Nutze die angehängte Datei" schlägt „Nutze dein Wissen" fast immer.
- **Iterieren über Interaktionskontext:** Wenn die Antwort inhaltlich stimmt aber das Format nicht passt, ändern Sie nur den Interaktionskontext — nicht den ganzen Prompt.

---

## Die Vorlage zum Kopieren

Dieses Template können Sie für jede Aufgabe nutzen — einfach die Platzhalter `[...]` ausfüllen:

```
<systemkontext>
Du bist [Rolle oder Persona], spezialisiert auf [Fachgebiet].
Deine Aufgabe ist es, [Ziel oder Nutzen].
Halte dich an folgende Prinzipien: [Regeln, Ethik, Stil].
</systemkontext>

<aufgabenkontext>
Deine aktuelle Aufgabe lautet: [konkrete Aufgabe].
Ziel: [Was soll am Ende herauskommen — und warum].
</aufgabenkontext>

<wissenskontext>
Hier sind relevante Informationen:
[Dokumente, Daten, Fakten, Beispiele einfügen]
</wissenskontext>

<interaktionskontext>
Formatiere deine Antwort als [Tabelle / Text / JSON / Stichpunkte].
Sprich in einem [Ton: sachlich, kreativ, lehrend, beratend].
Vermeide [z.B. Fachbegriffe, Spekulationen, Floskeln].
</interaktionskontext>

<situationskontext>
Der Nutzer ist [z.B. Marketing-Manager], hat [Vorwissen/Absicht].
Berücksichtige vorherige Schritte: [Zusammenfassung falls vorhanden].
</situationskontext>

Führe jetzt die Aufgabe aus.
```

> 💡 **Die letzte Zeile „Führe jetzt die Aufgabe aus"** ist besonders dann wichtig, wenn die Aufgabe mehrere Schritte hat und Sie sich zunächst auf den ersten konzentrieren möchten. Bei einfachen Aufgaben können Sie sie weglassen.

---

## Beispiel 1: Verkaufszahlen analysieren

**Ohne Context Engineering:**
```
Fasse die Quartalszahlen zusammen.
```

**Mit Context Engineering (alle 5 Ebenen):**
```
<systemkontext>
Du bist ein erfahrener Datenanalyst für den Bankensektor.
Antworte sachlich, präzise und datengetrieben.
</systemkontext>

<aufgabenkontext>
Analysiere die Verkaufszahlen aus Q3, um Trends zu erkennen.
Ziel: Ich muss dem Vorstand eine Empfehlung geben, welche
Produktlinien wir in Q4 priorisieren sollen.
</aufgabenkontext>

<wissenskontext>
Nutze ausschließlich die angehängte Excel-Datei mit den Q3-Daten.
Wenn du Annahmen triffst, kennzeichne sie als solche.
Beziehe dich nicht auf externe Marktdaten.
</wissenskontext>

<interaktionskontext>
Format: Executive Summary (max. 1 Seite), dann Detail-Tabelle.
Sprache: Deutsch, kein Fachjargon — der Vorstand ist nicht
technisch. Nutze Prozentangaben statt absoluter Zahlen.
</interaktionskontext>

<situationskontext>
Ich bin Vertriebsleiter einer Regionalbank mit 12 Filialen.
Letztes Quartal hatten wir einen Rückgang bei Bauspar-Produkten.
Der Vorstand erwartet konkrete Handlungsempfehlungen, nicht nur Zahlen.
</situationskontext>
```

**Warum das besser ist:** Die KI weiß jetzt: wer sie ist (Analyst), was das Ziel ist (Vorstandsempfehlung, nicht nur Zusammenfassung), worauf sie sich stützen soll (nur die Datei), wie die Antwort aussehen soll (Executive Summary, kein Jargon), und für wen (Vertriebsleiter, Regionalbank).

---

## Beispiel 2: Kundenkommunikation verbessern

**Ohne Context Engineering:**
```
Schreib mir eine E-Mail an einen unzufriedenen Kunden.
```

**Mit Context Engineering:**
```
<systemkontext>
Du bist ein erfahrener Kundenberater in einer Volksbank.
Dein Ton ist empathisch, lösungsorientiert und verbindlich.
Du duzt Kunden nicht.
</systemkontext>

<aufgabenkontext>
Schreibe eine Antwort-E-Mail an einen Kunden, der sich über
lange Wartezeiten bei der Kreditbearbeitung beschwert hat.
Ziel: Den Kunden halten und Vertrauen wiederherstellen.
</aufgabenkontext>

<wissenskontext>
- Unsere durchschnittliche Bearbeitungszeit für Kredite: 5 Werktage
- Dieser Kunde wartet seit 12 Werktagen (technisches Problem im System)
- Wir können als Entschädigung die Bearbeitungsgebühr erlassen
</wissenskontext>

<interaktionskontext>
Format: Fertige E-Mail, direkt versendbar.
Länge: Max. 150 Wörter. Keine Floskeln wie "Wir bedauern
etwaige Unannehmlichkeiten" — stattdessen konkret und ehrlich.
</interaktionskontext>

<situationskontext>
Der Kunde ist seit 15 Jahren bei uns und hat 3 Produkte.
Er hat seine Beschwerde auch auf Google Reviews gepostet.
Schnelle, gute Reaktion ist daher besonders wichtig.
</situationskontext>
```

**Warum das besser ist:** Statt einer generischen Entschuldigungs-Mail bekommt die KI den vollen Kontext: was schiefging, was wir anbieten können, wie wichtig der Kunde ist, und dass Öffentlichkeit im Spiel ist.

---

## Beispiel 3: Meeting-Protokoll erstellen

**Ohne Context Engineering:**
```
Fasse das Meeting zusammen.
```

**Mit Context Engineering:**
```
<systemkontext>
Du bist eine präzise Protokoll-Assistenz.
Du unterscheidest klar zwischen Fakten, Entscheidungen und offenen Punkten.
</systemkontext>

<aufgabenkontext>
Erstelle ein strukturiertes Meeting-Protokoll aus meinen Notizen.
Ziel: Das Protokoll geht an alle Teilnehmer und dient als
verbindliche Dokumentation der Entscheidungen.
</aufgabenkontext>

<wissenskontext>
Meine Meeting-Notizen:
- Projektbudget auf 50k erhöht (einstimmig)
- Deadline verschoben auf 15. April (Müller dagegen, überstimmt)
- Neuer Praktikant startet am 1.4., Einarbeitung durch Team B
- Nächstes Meeting: 22.3., 10:00 Uhr
- Weber macht Entwurf bis Freitag
- Offene Frage: Brauchen wir externen Berater?
</wissenskontext>

<interaktionskontext>
Format:
1. Teilnehmer und Datum (lasse ich ergänzen: [ERGÄNZEN])
2. Entscheidungen (mit Ergebnis: einstimmig/Mehrheit)
3. Aufgaben (Wer | Was | Bis wann)
4. Offene Punkte
5. Nächster Termin

Sprache: Formal, kurze Sätze, keine Prosa.
</interaktionskontext>

<situationskontext>
Wöchentliches Projektmeeting, Team von 6 Personen.
Müller ist bekannt dafür, Entscheidungen nachträglich
in Frage zu stellen — daher ist klare Dokumentation wichtig.
</situationskontext>
```

**Warum das besser ist:** Der Situationskontext „Müller stellt Entscheidungen in Frage" sorgt dafür, dass die KI bei der Deadline-Verschiebung besonders klar dokumentiert, dass es eine Mehrheitsentscheidung war. Ohne diesen Kontext wäre das ein Detail, das untergehen könnte.

---

## Context Engineering vs. Prompt Engineering

| | Prompt Engineering | Context Engineering |
|---|---|---|
| **Fokus** | Die einzelne Anweisung | Der gesamte Rahmen |
| **Frage** | „Wie formuliere ich die Frage?" | „In welchem Kontext stelle ich die Frage?" |
| **Ergebnis** | Bessere Einzelantworten | Konstantere, relevantere Ergebnisse über mehrere Interaktionen |
| **Aufwand** | Gering (1 Satz optimieren) | Mittel (5 Ebenen durchdenken) |
| **Wann nutzen** | Schnelle Fragen, einfache Aufgaben | Wichtige Analysen, wiederkehrende Workflows, Teamnutzung |

Context Engineering ersetzt Prompt Engineering nicht — es **erweitert** es. Denken Sie an Prompt Engineering als das Schreiben einer guten Frage, und Context Engineering als das Einrichten des ganzen Raums, in dem diese Frage gestellt wird.

**Ein oft unterschätzter Vorteil: Konstanz.** KI-Tools liefern bei identischen Prompts nicht immer identische Ergebnisse. Durch einen klar definierten Kontextrahmen reduzieren Sie diese Schwankungen erheblich — die Ergebnisse werden reproduzierbarer und gleichmäßiger in der Qualität. Das ist besonders im beruflichen Umfeld entscheidend, wo Sie sich auf die Ausgabe verlassen müssen.

> 💡 **Warum nicht einfach Memories nutzen?** Im beruflichen Kontext sind Funktionen wie ChatGPT Memory oft nicht freigegeben. Deshalb sollten Sie bei jeder wichtigen Anfrage den Kontext explizit mitliefern — die KI kennt Ihre Situation und Vorarbeit nicht von allein.

---

## Auf einen Blick: Die 5 Ebenen als Checkliste

Bevor Sie Ihren nächsten wichtigen Prompt schreiben, gehen Sie diese Fragen durch:

- [ ] 🎭 **Wer soll die KI sein?** (Rolle, Ton, Grenzen)
- [ ] 🎯 **Was ist das Ziel — und warum?** (Aufgabe + übergeordneter Zweck)
- [ ] 📚 **Welche Daten hat die KI?** (Dateien, Fakten, Einschränkungen)
- [ ] 💬 **Wie soll die Antwort aussehen?** (Format, Länge, Stil)
- [ ] 👤 **Wer bin ich und was ist mein Kontext?** (Rolle, Vorgeschichte, Umgebung)

Je mehr Ebenen Sie füllen, desto weniger muss die KI raten — und desto besser wird das Ergebnis.

---

