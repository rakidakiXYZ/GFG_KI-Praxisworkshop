# Der KI-Klon: Wie ChatGPT Sie wirklich kennenlernt (ESP-Framework)

## Wozu dient diese Technik?

Jedes Mal, wenn Sie einen neuen Chat öffnen, fängt die KI bei Null an — sie weiß nichts über Sie, Ihre Projekte, Ihre Denkweise. Das ist, als würden Sie jeden Tag einem neuen Praktikanten alles von vorne erklären.

Das **ESP-Framework** löst dieses Problem in drei Schritten: Sie lassen die KI Sie interviewen, destillieren das Ergebnis zu einem kompakten Profil, und verteilen dieses Profil auf verschiedene Projekte. Das Ergebnis: Eine KI, die Sie kennt — Ihren Ton, Ihre Strategie, Ihre blinden Flecken.

## Das ESP-Framework

| Schritt | Name | Was passiert |
|---------|------|-------------|
| **E** | Extract (Extrahieren) | KI interviewt Sie — roher Datenabzug |
| **S** | Synthesize (Verdichten) | KI organisiert das Interview zu einem strukturierten Profil |
| **P** | Projects (Verteilen) | Profil wird in Custom Instructions + Projekte eingebaut |

## So verwenden Sie die Technik

### Schritt 1: Extract — Das Interview

Öffnen Sie den **Voice Mode** in ChatGPT (das Mikrofon-Symbol unten rechts im Chat) und lassen Sie sich 15–20 Minuten interviewen. Wenn Ihnen Sprechen unangenehm ist, können Sie auch tippen. Seien Sie ehrlich und unstrukturiert — es geht um rohe Daten, nicht um perfekte Formulierungen.

```
<agent_rolle>
Du bist mein Chief of Staff. Deine Aufgabe: Mich in einem
15–20-minütigen Interview so gut kennenzulernen, dass du
danach meine Denkweise, meinen Arbeitsstil und meine Ziele
zusammenfassen kannst.
</agent_rolle>

<interview_bereiche>
Stelle mir Fragen zu:
- Meinem beruflichen Hintergrund und meiner aktuellen Rolle
- Meinem Kommunikationsstil und meinem Ton
- Meiner aktuellen Strategie und meinen Zielen
- Meinen Stärken und blinden Flecken
- Was mich frustriert und was mich motiviert
- Wie ich Entscheidungen treffe
</interview_bereiche>

<regeln>
- Stelle immer nur eine Frage auf einmal.
- Hake nach, wenn meine Antworten vage sind.
- Am Ende: Fasse zusammen, was du über mich gelernt hast.
</regeln>

Starte mit der ersten Frage.
```

### Schritt 2: Synthesize — Das Profil erstellen

Nachdem das Interview fertig ist, lassen Sie ChatGPT das Profil verdichten:

```
<aufgabe>
Erstelle basierend auf unserem Interview ein kompaktes Profil
über mich. Strukturiere es so:

<profil_struktur>
1. Wer ich bin (Rolle, Hintergrund — 2–3 Sätze)
2. Wie ich denke (Entscheidungsstil, Stärken, blinde Flecken)
3. Wie ich kommuniziere (Ton, Vorlieben, was ich hasse)
4. Was ich will (aktuelle Ziele und Strategie)
5. Wie ich Antworten haben will:
   - Bevorzugtes Format (Tabellen, Stichpunkte, kurz)
   - Was vermieden werden soll (z.B. Floskeln, Textwände)
</profil_struktur>

Halte es unter 500 Wörter. Das Profil wird in meine
Custom Instructions eingefügt.
</aufgabe>
```

**Dann:** Kopieren Sie das Profil und fügen Sie es in ChatGPT ein unter *Settings → Personalization → Custom Instructions*.

### Schritt 3: Projects — Den Kontext verteilen

Erstellen Sie in ChatGPT **separate Projects** für verschiedene Lebensbereiche. Mischen Sie keine Domains!

| Project | Was reinkommt | Beispiel |
|---------|--------------|---------|
| 🏢 Arbeit | Lebenslauf, Firmendaten, Strategie-Docs | „Consulting-Projekt" |
| 📹 Content | Content-Kalender, Skripte, Analytics | „YouTube-Projekt" |
| 💪 Gesundheit | Trainingspläne, Blutwerte, Ernährung | „Health-Projekt" |
| 📚 Lernen | Kursnotizen, Bücherliste, Zertifikate | „Weiterbildung" |

**Pro Project:** Laden Sie relevante Dateien hoch (PDFs, Tabellen, Dokumente) und passen Sie die Project Instructions an.

### 💡 Tipps

- **Profil aktualisieren:** Alle 2–3 Monate das Interview wiederholen. Sie verändern sich — Ihr KI-Profil sollte das auch.
- **Voice Mode nutzen:** Im Gespräch kommen Dinge raus, die Sie beim Tippen nie schreiben würden. Lassen Sie sich überraschen.
- **Nicht perfektionieren:** Das Interview soll roh und ehrlich sein. Polieren kommt in Schritt 2.
- **Custom Instructions + Projects kombinieren:** Custom Instructions gelten global (für alle Chats) — das sind Ihre bewussten Vorgaben. Project Instructions gelten nur im jeweiligen Projekt. Memory hingegen sind Dinge, die ChatGPT sich von selbst merkt. Nutzen Sie alle drei Ebenen.

> ⚠️ **Datenschutz:** Ihr Profil und Ihre Project-Dateien werden an OpenAI übermittelt. Laden Sie keine vertraulichen Firmendokumente hoch, ohne die Datenschutzrichtlinien Ihres Unternehmens zu prüfen.

---
