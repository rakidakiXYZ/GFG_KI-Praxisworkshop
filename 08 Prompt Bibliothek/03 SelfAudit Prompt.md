# Self-Audit Spiegel-Prompt: Deine blinden Flecken aufdecken

## Wozu dient dieser Prompt?

Jeder hat blinde Flecken — Muster, die man selbst nicht sieht, aber die das eigene Handeln steuern. Dieser Prompt verwandelt eine KI in Ihren persönlichen Psychologen und Coach, der Ihre bisherigen Gespräche analysiert und Ihnen einen schonungslosen Spiegel vorhält.

Das Ergebnis: Eine strukturierte Persönlichkeitsanalyse mit Ihren Stärken, blinden Flecken, wiederkehrenden Mustern — und einer konkreten Handlungsempfehlung.

## So verwenden Sie den Prompt

1. **Voraussetzung:** Sie brauchen eine KI, mit der Sie bereits **viele Gespräche** geführt haben. Je mehr Kontext die KI über Sie hat, desto treffsicherer die Analyse.
2. **Wo einfügen:** Idealerweise in einem Chat, in dem die KI Zugriff auf Ihren bisherigen Gesprächsverlauf hat — z.B. ein laufender Claude- oder ChatGPT-Thread, in dem Sie regelmäßig schreiben.
3. **Prompt senden:** Kopieren Sie den Prompt und senden Sie ihn. Die KI durchläuft drei Phasen: Datensammlung → 20 Analyse-Fragen → Synthese.
4. **Offen sein:** Die Analyse kann unbequem werden. Das ist Absicht.

### 💡 Tipps

- **Bester Zeitpunkt:** Nach mindestens 20–30 Gesprächen mit der KI. Bei weniger Kontext wird die Analyse oberflächlich.
- **ChatGPT mit Memory:** Besonders effektiv, wenn ChatGPT die Memory-Funktion aktiviert hat und sich an frühere Gespräche erinnert.
- **Claude Projects:** Funktioniert gut in einem Claude-Projekt (ein dauerhafter Arbeitsbereich in Claude, in dem die KI sich an frühere Gespräche erinnert).
- **Nachfragen:** Fragen Sie nach der Analyse gezielt nach: *„Zu Punkt 12 — kannst du konkreter werden? Welche Gespräche meinst du?"*
- **Wiederholen:** Führen Sie den Audit alle 3–6 Monate durch. Vergleichen Sie die Ergebnisse — was hat sich verändert?
- **Welche KI?** ChatGPT mit Memory-Funktion liefert oft die tiefsten Analysen, weil es sich an frühere Gespräche erinnert. Claude in Projects ist ebenfalls stark. Testen Sie beide und vergleichen Sie — die Perspektiven ergänzen sich.

> ⚠️ **Hinweis:** Eine KI ersetzt keinen Therapeuten oder professionellen Coach. Die Analyse basiert auf Textmustern in Ihren Gesprächen — nicht auf klinischer Diagnostik. Nutzen Sie die Ergebnisse als Reflexionsanstoß, nicht als Diagnose.

---

## Der Prompt

```
Du bist jetzt mein persönlicher Psychologe und Coach.
Deine Aufgabe: Eine tiefgehende Persönlichkeitsanalyse
basierend auf allem, was du bereits über mich weißt.

<phase1_data_collection>
Gehe still durch alle unsere bisherigen Gespräche und analysiere:
- Wiederkehrende Themen und Sorgen
- Meine Entscheidungsmuster
- Wie ich über Arbeit, Beziehungen und Geld spreche
- Emotionale Muster: Was macht mich aufgeregt, was frustriert mich?
- Widersprüche zwischen dem, was ich sage, und dem, was ich tue
- Vermeidungsverhalten
- Meine Stärken und blinden Flecken
</phase1_data_collection>

<phase2_twenty_questions>
Beantworte diese 20 Fragen ÜBER mich — nicht als Fragen an mich,
sondern als deine Analyse basierend auf deinen Beobachtungen:

<q1_erlaubnis>
Worauf warte ich, dass mir jemand erlaubt zu tun? Wessen Erlaubnis?
</q1_erlaubnis>

<q2_intrinsische_motivation>
Welche Arbeit würde ich auch ohne Bezahlung oder Anerkennung machen?
</q2_intrinsische_motivation>

<q3_vermeidung>
Was vermeide ich wirklich — nicht oberflächlich, sondern das Tiefere?
</q3_vermeidung>

<q4_selbstnarrative>
Welche Geschichte erzähle ich mir über mich selbst, die vielleicht nicht mehr stimmt?
</q4_selbstnarrative>

<q5_wiederkehrende_muster>
Welcher Konflikt taucht immer wieder in meinem Leben auf?
</q5_wiederkehrende_muster>

<q6_art_der_muedigkeit>
Bin ich "brauche mehr Schlaf"-müde oder "brauche ein anderes Leben"-müde?
</q6_art_der_muedigkeit>

<q7_widersprueche>
Wo klaffen meine Werte und mein Verhalten am meisten auseinander?
</q7_widersprueche>

<q8_emotionale_basis>
Was ist mein Default-Gefühl, wenn nichts Besonderes passiert?
</q8_emotionale_basis>

<q9_geld_emotionen>
Was ist meine emotionale Beziehung zu Geld?
</q9_geld_emotionen>

<q10_ja_sagen>
Wozu sage ich Ja, obwohl ich Nein sagen sollte?
</q10_ja_sagen>

<q11_akzeptierte_frustrationen>
Welche Frustrationen habe ich aufgehört zu bekämpfen?
</q11_akzeptierte_frustrationen>

<q12_versteckte_ambitionen>
Welchen Ehrgeiz habe ich mir selbst noch nicht eingestanden?
</q12_versteckte_ambitionen>

<q13_wachstum_das_ich_meide>
Welches Wachstum wehre ich aktiv ab?
</q13_wachstum_das_ich_meide>

<q14_komfortzone_vs_lebendigkeit>
Wo bin ich bequem, aber nicht wirklich lebendig?
</q14_komfortzone_vs_lebendigkeit>

<q15_energie_lecks>
Was zieht leise meine Energie ab, ohne dass ich es benenne?
</q15_energie_lecks>

<q16_produktiv_vs_praesent>
Optimiere ich Produktivität auf Kosten von Präsenz?
</q16_produktiv_vs_praesent>

<q17_vergleichsperson>
Mit wem vergleiche ich mich, und ist das hilfreich oder giftig?
</q17_vergleichsperson>

<q18_ungesagtes>
Was sage ich jemandem Wichtigem nicht?
</q18_ungesagtes>

<q19_beziehung_zu_kontrolle>
Geht es bei meinem Verhältnis zu Geld um Freiheit oder Kontrolle?
</q19_beziehung_zu_kontrolle>

<q20_unbequeme_wahrheit>
Was müsste ich mir selbst sagen, das ich nicht hören will?
</q20_unbequeme_wahrheit>
</phase2_twenty_questions>

<phase3_synthesis>
Fasse deine Analyse in dieser Struktur zusammen:

<kernpersoenlichkeit>
Wer bin ich im Kern, jenseits der Rollen? (2–3 Sätze)
</kernpersoenlichkeit>

<unterschaetzte_staerken>
Was kann ich gut, das ich für selbstverständlich halte?
</unterschaetzte_staerken>

<blinde_flecken>
Was sehen andere, was ich selbst nicht sehe?
</blinde_flecken>

<roter_faden>
Welches Thema zieht sich durch alles?
</roter_faden>

<beziehungsmuster>
Wie verhalte ich mich in Beziehungen — beruflich und privat?
</beziehungsmuster>

<karriere_dynamik>
Was treibt mich an, was hält mich zurück?
</karriere_dynamik>

<wichtigste_erkenntnis>
Eine Sache, die alles ändern würde, wenn ich sie wirklich verstehen würde.
</wichtigste_erkenntnis>

<naechster_schritt>
Eine konkrete Sache, die ich diese Woche tun könnte.
</naechster_schritt>
</phase3_synthesis>

Beginne jetzt mit Phase 1 und 2. Sei ehrlich, auch wenn es unbequem ist.
Ich bin bereit.
```

---
