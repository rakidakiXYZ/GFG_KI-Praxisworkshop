# Tree-of-Thought: Komplexe Entscheidungen systematisch durchdenken

## Wozu dient dieser Prompt?

Bei einfachen Fragen reicht eine direkte Antwort. Aber bei **komplexen Entscheidungen** — Karrierewechsel, Produktstrategie, Architektur-Entscheidungen — gibt es selten den einen richtigen Weg. Hier hilft die **Tree-of-Thought-Methode** (ToT): Die KI denkt nicht linear, sondern erkundet mehrere Lösungspfade parallel, bewertet jeden einzelnen und wählt dann den besten aus.

Statt: „Hier ist meine Antwort" → bekommt man: „Hier sind 3–5 Wege, hier die Vor- und Nachteile, und hier ist der optimale Pfad — verfeinert."

Tree-of-Thought ist die Weiterentwicklung von **Chain-of-Thought** (ein linearer Denkpfad) — statt einem Weg werden mehrere parallel erkundet und gegeneinander bewertet.

## So verwenden Sie den Prompt

1. **Ihre Aufgabe formulieren:** Beschreiben Sie Ihre Entscheidung oder Ihr Problem in 1–3 Sätzen.
2. **Prompt anhängen:** Fügen Sie den Tree-of-Thought-Prompt direkt darunter ein.
3. **Ergebnis lesen:** Die KI liefert mehrere Pfade mit Bewertung und eine begründete Empfehlung.

### Beispiel

> *„Ich überlege, ob ich mein Beratungsunternehmen auf KI-Schulungen spezialisiere, eine Software-Plattform baue, oder beides parallel mache."*
>
> *[Prompt einfügen]*

### 💡 Tipps

- **Reasoning-Modelle nutzen:** Dieser Prompt entfaltet seine volle Wirkung mit Modellen, die „denken" können — sogenannte Reasoning-Modelle. In ChatGPT Plus wählen Sie dafür oben im Chat das Modell „o3" oder „GPT-5" aus. In Claude aktivieren Sie „Extended Thinking". Bei einfacheren Modellen funktioniert der Prompt auch, aber die Analyse wird oberflächlicher.
- **Anzahl anpassen:** Bei sehr komplexen Entscheidungen: „5–7 alternative Pfade". Bei einfacheren: „3 Pfade" reicht.
- **Nachbohren:** Nach der ersten Analyse können Sie gezielt nachfragen: *„Vertiefe Pfad 2 — was wären die ersten 5 konkreten Schritte?"*
- **Kombinieren:** Oft ist der beste Weg eine Kombination aus mehreren Pfaden. Bitten Sie die KI: *„Kombiniere die Stärken von Pfad 1 und 3 zu einem Hybrid-Ansatz."*
- **Eigene Kriterien ergänzen:** Die Bewertung im Prompt ist ein Startpunkt. Sie können eigene Kriterien hinzufügen, z.B.: *„Bewerte auch: Skalierbarkeit und Team-Akzeptanz"* — je nach Ihrer Situation.

> ⚠️ **Wichtig:** Tree-of-Thought ersetzt keine Expertise — es strukturiert Ihr Denken. Die KI kennt Ihre Branche, Ihre Ressourcen und Ihre Risikotoleranz nur so gut, wie Sie sie beschreiben. Je mehr Kontext Sie mitgeben, desto besser die Pfade.

---

## Der Prompt

```
<aufgabe>
[Hier Ihre konkrete Aufgabenstellung, Entscheidung oder Problemstellung einfügen]
</aufgabe>

<tree_of_thought>
Erkunde das via Tree-of-Thought:

1. Generiere 3–5 alternative Lösungspfade.
   Jeder Pfad soll ein eigenständiger, durchdachter Ansatz sein —
   nicht bloß Variationen desselben Gedankens.

2. Bewerte jeden Pfad:
   - Vorteile und Chancen
   - Nachteile und Risiken
   - Aufwand (Zeit, Geld, Komplexität)
   - Wahrscheinlichkeit des Erfolgs

3. Wähle den optimalen Pfad aus.
   Begründe, warum dieser die beste Balance aus
   Chancen, Risiken und Aufwand bietet.

4. Verfeinere den gewählten Pfad:
   - Konkrete erste Schritte
   - Mögliche Stolpersteine und wie man sie umgeht
   - Entscheidungspunkte, an denen man den Kurs korrigieren sollte
</tree_of_thought>
```

---

## Wann Tree-of-Thought einsetzen?

| Situation | Beispiel | ToT sinnvoll? |
|---|---|---|
| Strategische Entscheidung | „Welchen Markt erschließen wir zuerst?" | ✅ Ja |
| Architektur-Entscheidung | „Monolith oder Microservices?" | ✅ Ja |
| Karriere-Entscheidung | „Jobwechsel oder Selbstständigkeit?" | ✅ Ja |
| Faktenfrage | „Wie hoch ist der Eiffelturm?" | ❌ Nein — direkte Antwort reicht |
| Kreative Aufgabe | „Schreib mir ein Gedicht" | ❌ Nein — andere Methode besser |
| Optimierung mit vielen Variablen | „Wie strukturiere ich mein Team um?" | ✅ Ja |

---

