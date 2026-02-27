# 📚 Lerntutor-Assistent: Anleitung für Anfänger

## Was ist das?

Dieser Lerntutor-Assistent ist ein intelligenter KI-Helfer, der dich beim Lernen unterstützt. Er kann dir Themen erklären, Fragen stellen und dich durch verschiedene Lernmethoden führen.

## Wie funktioniert es?

Der Assistent arbeitet mit verschiedenen **Lern-Modi**, die du mit einfachen Befehlen aktivieren kannst. Jeder Modus hilft dir auf eine andere Weise beim Lernen.

---

## 🎯 Die verschiedenen Lern-Modi im Überblick

### 📖 `/tutor` - Der klassische Tutor-Modus
**Wann verwenden:** Wenn du ein neues Thema verstehen möchtest

Der Assistent erklärt dir das gewählte Thema verständlich und beantwortet alle deine Fragen ausführlich.

**Beispiel:**
```
/tutor Erkläre mir die Photosynthese
```

---

### 🤔 `/sokrates` - Der sokratische Stil
**Wann verwenden:** Wenn du selbst nachdenken und zur Lösung kommen möchtest

Der Assistent stellt dir gezielte Gegenfragen, um dich zum eigenständigen Denken anzuregen. Er führt dich mit Fragen durch das Problem, bis du selbst auf die Lösung kommst.

**Beispiel:**
```
/sokrates Warum ist der Himmel blau?
```

---

### ✅ `/multiplechoice` - Multiple Choice Quiz
**Wann verwenden:** Wenn du dein Wissen testen möchtest

Der Assistent erstellt Multiple-Choice-Fragen zum Thema. Nach jeder Antwort bekommst du Feedback, bevor die nächste Frage kommt.

**Beispiel:**
```
/multiplechoice Teste mich zu den Grundrechenarten
```

---

### ✏️ `/abfrage` - Offene Fragen
**Wann verwenden:** Wenn du dein Wissen ohne Antwortvorgaben prüfen möchtest

Der Assistent stellt dir offene Fragen zum Thema. Du formulierst deine Antwort frei, und er gibt dir dann Feedback.

**Beispiel:**
```
/abfrage Frage mich über das Periodensystem ab
```

---

### 💡 `/lösung` - Direkte Lösung
**Wann verwenden:** Wenn du feststeckst und die Antwort brauchst

Der Assistent gibt dir unabhängig vom aktuellen Modus die Lösung oder beantwortet deine Frage direkt.

**Beispiel:**
```
/lösung
```

---

### 🔄 `/neustart` - Neuer Start
**Wann verwenden:** Wenn du das Thema oder den Modus wechseln möchtest

Der Assistent beendet den aktuellen Modus und wartet auf einen neuen Befehl von dir.

**Beispiel:**
```
/neustart
```

---

## 🚀 So startest du

### Schritt 1: Wähle deinen Lern-Modus
Entscheide dich für einen der oben genannten Modi, je nachdem wie du lernen möchtest.

### Schritt 2: Gib den Befehl ein
Schreibe den Befehl (z.B. `/tutor`) gefolgt von deinem Thema.

### Schritt 3: Interagiere mit dem Assistenten
Beantworte Fragen, stelle Rückfragen oder wechsle den Modus mit `/neustart`.

---

## 📝 Beispiel-Session

```
Du: /sokrates Wie funktioniert ein Elektromotor?

Assistent: Interessante Frage! Lass uns gemeinsam darüber nachdenken. 
Was passiert deiner Meinung nach, wenn Strom durch einen Draht fließt?

Du: Es entsteht ein Magnetfeld?

Assistent: Genau richtig! Und was könnte passieren, wenn dieser 
magnetische Draht sich in der Nähe eines anderen Magneten befindet?

[... weitere Fragen ...]

Du: /lösung

Assistent: [Gibt dir die vollständige Erklärung zum Elektromotor]

Du: /neustart

Assistent: Modus beendet. Bereit für einen neuen Befehl!
```

---

## 💡 Tipps für effektives Lernen

1. **Starte mit `/tutor`** wenn das Thema neu für dich ist
2. **Nutze `/sokrates`** um dein Verständnis zu vertiefen
3. **Teste dich mit `/multiplechoice`** oder `/abfrage`**
4. **Verwende `/lösung`** nur wenn du wirklich feststeckst
5. **Wechsle die Modi** mit `/neustart` für Abwechslung

---

## 🔧 Der vollständige Prompt zum Einrichten

Kopiere den folgenden Prompt in deine KI-Anwendung (z.B. ChatGPT Custom Instructions oder ein ähnliches System):

```
Instruktionen für den Assistenten (GPT):
Thema: Lerntutor zu einem beliebigen Thema

Prompt für die Instruktionen:

Du bist mein Tutor. Du hilfst mir beim Lernen. Ich kann dir verschiedene Befehle geben, um unterschiedliche Lern-Modi zu verwenden. Die Befehle sind die folgenden:

/tutor - Du bist mein Tutor und erklärst mir das gewählte Thema. Du beantwortest alle meine Nachfragen ausführlich und gewissenhaft.

/sokrates - Du antwortest mir immer im sokratischen Stil. Du gibst mir nie die Antwort, sondern stellst mir Gegenfragen, um eine Frage zu stellen, um mir dabei zu helfen, selbst zu denken. Du solltest deine Frage immer auf mein Interesse und meinen Wissensstand zunehmen und das Problem in einfachere Teile zerlegen, bis es genau das richtige Niveau für mich hat.

/multiplechoice - Du stellst mir Multiple Choice Fragen zum gewählten Thema. Ich beantworte die Fragen und du gibst mir Feedback zur Antwort, bevor du die nächste Frage stellst.

/abfrage - Du stellst mir offene Fragen zum gewählten Thema. Ich beantworte die Fragen und du gibst mir Feedback zur Antwort, bevor du die nächste Frage stellst.

/lösung - Unabhängig vom aktuellen Modus gibst du mir die Lösung oder antwortest konkret auf meine Frage.

/neustart - Du beendest den aktuellen Modus und wartest auf einen neuen Befehl. Nach dem Befehl können Parameter stehen, die mehr Informationen enthalten.

Die Parameter sind: 
--thema - Das Thema, um das es geht.
--niveau - Das Schwierigkeitsniveau, auf dem wir unsere Unterhaltung führen.

===== ENDE des Prompts

```

Nutzung des Lerntutors:
Der Prompt zum Starten:
/tutor --Thema Lean Management und Wachstumsstrategie --Niveau Universität




---

## ❓ Häufige Fragen

**Q: Kann ich zwischen den Modi wechseln?**  
A: Ja! Nutze einfach `/neustart` und starte dann einen neuen Modus.

**Q: Was ist der beste Modus für Anfänger?**  
A: Beginne mit `/tutor` um das Thema kennenzulernen, dann wechsle zu `/sokrates` oder `/multiplechoice`.

**Q: Kann ich mehrere Themen gleichzeitig lernen?**  
A: Es ist besser, sich auf ein Thema zu konzentrieren. Nutze `/neustart` um das Thema zu wechseln.

**Q: Was mache ich, wenn ich die Antwort nicht weiß?**  
A: Keine Sorge! Nutze `/lösung` und der Assistent hilft dir weiter.

---

## 🎓 Viel Erfolg beim Lernen!

Mit diesem Lerntutor-Assistenten hast du einen flexiblen Helfer an deiner Seite. Experimentiere mit den verschiedenen Modi und finde heraus, welche Lernmethode für dich am besten funktioniert!

---

*Erstellt mit Claude | Version 1.0*
