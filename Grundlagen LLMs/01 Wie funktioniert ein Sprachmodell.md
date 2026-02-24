# Wie Large Language Models funktionieren

**Ein verständlicher Leitfaden für alle, die verstehen wollen, was hinter ChatGPT, Copilot & Co. wirklich steckt**

---

## Warum dieses Tutorial?

Sie nutzen vielleicht schon ChatGPT, Microsoft Copilot oder andere KI-Assistenten — im Alltag oder sogar bei der Arbeit. Sie tippen eine Frage ein, und irgendwie kommt eine erstaunlich gute Antwort zurück. Aber haben Sie sich schon mal gefragt: **Wie funktioniert das eigentlich?**

Keine Sorge — Sie brauchen dafür kein Informatik-Studium. In diesem Tutorial erklären wir Schritt für Schritt, was in einem Large Language Model passiert. Mit einfachen Vergleichen, klaren Bildern und null Fachchinesisch.

**Was Sie nach diesem Tutorial wissen werden:**

- Was ein LLM wirklich ist (und was es *nicht* ist)
- Warum die einfache Idee „nächstes Wort vorhersagen" so unglaublich gut funktioniert
- Welche 8 Bausteine ein LLM ausmachen
- Wie das berühmte „Attention"-Prinzip funktioniert
- Wie ein Modell vom totalen Unsinn zu sinnvollen Texten kommt

---

## Die beste Autovervollständigung der Welt

Kennen Sie die Funktion auf Ihrem Handy, die Wörter vorschlägt, während Sie tippen? Sie schreiben „Ich bin gleich" und das Handy schlägt „da" vor. Das ist Textvorhersage — und genau das machen ChatGPT & Co. im Kern auch.

Der Unterschied? **Maßstab.** Ein kaum vorstellbar riesiger Maßstab.

Stellen Sie sich ein Kind vor, das tausende Gute-Nacht-Geschichten gehört hat. Sie beginnen einen Satz: „Es war einmal…" und das Kind ruft sofort „…eine Prinzessin!" Das Kind hat die Geschichte nicht wirklich *verstanden*. Es hat ein bekanntes Muster erkannt.

Ein LLM macht genau das Gleiche — nur hat es statt tausend Geschichten **Milliarden von Texten** gelesen. Es ist extrem gut darin, in jedem Zusammenhang das nächste Wort zu erraten. Egal ob Märchen, E-Mail, Kreditvertrag oder Programmcode.

> **LLM** steht für **Large Language Model** — auf Deutsch: Großes Sprachmodell.
> - **Large** (groß), weil es mit einer enormen Menge Text trainiert wurde — ganze Bibliotheken plus große Teile des Internets.
> - **Language Model** (Sprachmodell), weil seine Aufgabe ist, Sprache vorherzusagen: Gib ihm ein paar Wörter, und es sagt dir, welche Wörter wahrscheinlich als nächstes kommen.

Das Faszinierende: Allein durch diese simple Wortvorhersage — angewandt in gigantischem Maßstab — kann das Modell am Ende Aufsätze schreiben, Fragen beantworten, Code produzieren und vieles mehr. Aber im Kern sagt es immer nur **ein Wort nach dem anderen** voraus, basierend auf Mustern, die es gelernt hat.

---

## Warum funktioniert das überhaupt?

LLMs verstehen Sprache nicht so wie wir Menschen. Sie lernen **Muster in Texten**. Während des Trainings sieht das Modell Millionen von Beispielen, wie Wörter aufeinander folgen. Mit der Zeit erkennt es Grammatikregeln, gängige Redewendungen und sogar Fakten — alles als statistische Muster.

Ein paar Beispiele:

- Es lernt, dass „Butter**brot** mit Käse" viel wahrscheinlicher ist als „Butterbrot mit Beton"
- Es lernt, dass Fragen mit einem Fragezeichen enden
- Es nimmt auf, dass „Berlin ist die Hauptstadt von Deutschland" stimmt, weil dieses Muster in den Trainingsdaten immer wieder vorkommt

Stellen Sie sich das so vor: Wenn Sie jahrelang jeden Tag die Rheinische Post, die FAZ, Wikipedia und tausende Fachbücher lesen würden, könnten Sie irgendwann auch ziemlich gut vorhersagen, wie ein Satz über ein bestimmtes Thema wahrscheinlich weitergeht. Genau das macht ein LLM — nur mit **Milliarden** von Texten und einer Geschwindigkeit, die kein Mensch erreichen kann.

---

## Die Transformer-Architektur: Der Motor hinter allem

Die entscheidende Erfindung, die moderne LLMs erst möglich gemacht hat, heißt **Transformer**. Diese Architektur wurde 2017 in einem mittlerweile berühmten Forschungspapier vorgestellt — mit dem Titel *„Attention Is All You Need"* (auf Deutsch: „Aufmerksamkeit ist alles, was man braucht").

Was macht den Transformer besonders?

Ältere Sprachmodelle lasen Text **streng der Reihe nach** — Wort für Wort, von links nach rechts. Das ist langsam und fehleranfällig. Der Transformer hingegen nutzt einen Mechanismus namens **Self-Attention** (Selbst-Aufmerksamkeit), der es dem Modell erlaubt, **alle Wörter eines Satzes gleichzeitig** zu betrachten und herauszufinden, welche Wörter füreinander besonders wichtig sind.

**Ein Beispiel aus dem Bankalltag:**

> „Der Kunde hat den Kreditantrag eingereicht, weil **er** dringend eine Finanzierung braucht."

Wer ist „er"? Natürlich der Kunde — nicht der Kreditantrag. Für uns ist das offensichtlich. Für ein Sprachmodell ist genau das die Leistung der Attention: Das Wort „er" richtet seine „Aufmerksamkeit" stärker auf „Kunde" als auf „Kreditantrag" oder „eingereicht".

Der zweite große Vorteil: Transformer können **massiv parallelisiert** werden. Sie verarbeiten viele Wörter gleichzeitig statt nacheinander. Das beschleunigt das Training enorm und ermöglicht es, aus sehr langen Texten zu lernen.

---

## Die 8 Bausteine eines LLM

Jetzt wird es spannend. Wir gehen Schritt für Schritt durch, wie ein LLM aufgebaut ist — vom Rohtext bis zum fertigen Textgenerator. Keine Sorge, bei jedem Schritt gibt es einen einfachen Vergleich.

### Baustein 1: Riesige Mengen Text sammeln

Bevor ein Kind Sätze ergänzen kann, muss es erstmal jede Menge Geschichten gehört haben. Genauso braucht ein LLM eine **riesige Textsammlung** zum Lernen: Bücher, Webseiten, Artikel, Gespräche — alles, was an Text verfügbar ist.

GPT-3 wurde mit **hunderten Milliarden Wörtern** aus dem Internet trainiert. Stellen Sie sich vor, Sie würden den gesamten Buchbestand aller deutschen Bibliotheken plus Wikipedia plus sämtliche Zeitungsarchive lesen — das kommt der Sache schon näher.

Warum so viel? Weil das Modell lernen muss, dass „Es war einmal" ein typischer Anfang ist, dass Fragen mit Fragezeichen enden und dass „Frankfurt ist der Sitz der EZB" stimmt. Die einzige Möglichkeit, all diese Muster zu lernen, ist **massenhaftes Lesen**.

### Baustein 2: Der Tokenizer — Text in Puzzleteile zerlegen

Computer können nicht mit Wörtern rechnen — sie brauchen **Zahlen**. Also müssen wir den Text in kleine Stücke zerlegen und jedes Stück einer Zahl zuordnen. Diesen Vorgang nennt man **Tokenisierung**.

Stellen Sie sich vor, Sie schneiden einen Satz mit der Schere in einzelne Teile. Jedes Teil bekommt eine Nummer — das ist ein **Token**.

**Beispiel:**

| Text | Tokens | Token-IDs |
|------|--------|-----------|
| „Ich bin glücklich" | „Ich", „bin", „glück", „lich" | 15, 42, 867, 309 |

Warum nicht einfach jedes Wort = eine Nummer? Weil es viel zu viele verschiedene Wörter gibt — besonders im Deutschen mit seinen zusammengesetzten Wörtern. Was ist mit „Kreditrückzahlungsvereinbarung"? Stattdessen zerlegen moderne Tokenizer Wörter in **häufige Teilstücke** (sogenannte Sub-Tokens). So kann das Modell auch Wörter verarbeiten, die es noch nie gesehen hat — indem es die Einzelteile kennt.

> **Für die Praxis:** Wenn Sie in ChatGPT einen langen Text eingeben und irgendwann die Meldung kommt, der Text sei „zu lang", liegt das daran, dass zu viele Tokens erzeugt wurden. Jedes Modell hat ein **Token-Limit** — dazu später mehr.

### Baustein 3: Embeddings — Jedes Token bekommt eine Adresse

Wir haben jetzt Tokens als Zahlen. Aber die Zahl 42 sagt dem Modell nichts über die **Bedeutung** des Wortes. Also wandeln wir jede Token-ID in einen **Vektor** um — eine Liste von Zahlen, die die Bedeutung des Tokens beschreibt.

Stellen Sie sich eine riesige Landkarte vor. Jedes Wort bekommt **Koordinaten** auf dieser Karte. Wörter mit ähnlicher Bedeutung landen nahe beieinander:

- „Kredit" und „Darlehen" → direkte Nachbarn
- „Kredit" und „Banane" → weit voneinander entfernt
- „Zinsen" und „Rendite" → im selben Viertel

Diese „Bedeutungs-Landkarte" wird während des Trainings gelernt. Am Anfang sind die Koordinaten zufällig — aber nach dem Training stehen bedeutungsähnliche Wörter tatsächlich beieinander. Das Modell hat aus dem Kontext gelernt, dass „Kredit" und „Darlehen" in ähnlichen Sätzen vorkommen.

### Baustein 4: Positional Encoding — Seitenzahlen für Wörter

Jetzt haben wir für jedes Token einen Bedeutungs-Vektor. Aber es gibt ein Problem: **Das Modell weiß nicht, in welcher Reihenfolge die Wörter stehen.** Es sieht alle Vektoren gleichzeitig — wie einen Haufen Karteikarten, die durcheinander gewürfelt wurden.

Die Reihenfolge ist aber entscheidend:

- „Die **Bank** berät den **Kunden**" — die Bank ist aktiv
- „Der **Kunde** berät die **Bank**" — der Kunde ist aktiv

Komplett andere Bedeutung, gleiche Wörter!

Die Lösung: **Positional Encoding**. Jedem Token wird eine Art „Seitenzahl" hinzugefügt — eine Information darüber, an welcher Position im Satz es steht. Wie wenn Sie auf jede Karteikarte eine Nummer schreiben, damit die richtige Reihenfolge erkennbar bleibt.

### Baustein 5: Der Attention-Mechanismus — Wörter schauen sich gegenseitig an

Hier kommen wir zum Herzstück des Transformers: **Self-Attention** (Selbst-Aufmerksamkeit). Das ist der Mechanismus, der alles zusammenhält — und er ist leichter zu verstehen, als Sie vielleicht denken.

**Die Analogie:** Stellen Sie sich eine Teambesprechung in Ihrer Filiale vor. Jeder Mitarbeiter hat eine Frage (**Query**), jeder hat Wissen zu bieten (**Value**), und jeder trägt ein Namensschild mit seiner Spezialität (**Key**).

Wenn die Kollegin aus der Kreditabteilung eine Frage zu Baufinanzierung hat, schaut sie sich die Namensschilder aller anderen an. Der Kollege mit „Immobilienbewertung" passt perfekt — dem schenkt sie die meiste Aufmerksamkeit. Die Kollegin aus der Marketingabteilung hat für diese Frage weniger zu bieten.

Genauso funktioniert Attention im Modell:

1. Jedes Wort stellt eine „Frage" (**Query**): *Was bin ich und was passiert um mich herum?*
2. Jedes Wort bietet eine „Antwort" an (**Value**) mit einem „Namensschild" (**Key**)
3. Das Modell vergleicht die Frage jedes Wortes mit den Namensschildern aller anderen Wörter
4. Wörter, deren Namensschilder gut zur Frage passen, bekommen mehr Aufmerksamkeit
5. Das Ergebnis: Jedes Wort bekommt eine angereicherte Darstellung, die den Kontext einbezieht

**Beispiel:**

> „Der Kunde hat den Kreditantrag eingereicht, weil er dringend eine Finanzierung braucht."

Wenn das Modell das Wort „er" verarbeitet:
- „er" stellt die Frage: *Auf wen beziehe ich mich?*
- „Kunde" hat ein passendes Namensschild → **hohe Aufmerksamkeit**
- „Kreditantrag" passt weniger → niedrige Aufmerksamkeit
- Ergebnis: „er" wird mit der Information angereichert, dass es sich auf den Kunden bezieht

In der Praxis verwendet der Transformer **Multi-Head Attention** — also mehrere solcher Aufmerksamkeits-Runden parallel. Wie wenn in der Teambesprechung mehrere Beobachter gleichzeitig auf verschiedene Dinge achten: Einer auf die inhaltlichen Zusammenhänge, einer auf die Satzstruktur, einer auf Bezüge zu früheren Aussagen. All diese Perspektiven werden am Ende kombiniert.

### Baustein 6: Mehrere Schichten stapeln — Schritt für Schritt verfeinern

Eine einzelne Attention-Runde erfasst einfache Zusammenhänge. Aber für echtes Sprachverständnis braucht das Modell **viele Schichten** übereinander — manchmal dutzende.

Stellen Sie sich ein mehrstöckiges Bürogebäude vor. Auf jeder Etage arbeiten zwei Abteilungen:

1. **Attention-Abteilung:** Analysiert Beziehungen zwischen Wörtern
2. **Verarbeitungs-Abteilung** (Feed-Forward Network): Verarbeitet die Informationen weiter

Jede Etage versteht etwas Komplexeres:

| Etage | Was gelernt wird | Bank-Analogie |
|-------|-----------------|---------------|
| Untere Etagen | Grammatik, Wortverbindungen | „Kreditantrag" gehört zusammen |
| Mittlere Etagen | Themen, Bezüge klären | „er" bezieht sich auf „den Kunden" |
| Obere Etagen | Gesamtbedeutung, Absichten | „Das ist eine Kreditanfrage, die positiv klingt" |

GPT-3 hat **96 solcher Etagen** übereinander gestapelt. Kleinere Modelle haben 6 bis 12. Grundsätzlich gilt: Mehr Etagen (plus genug Trainingsdaten) = komplexere Muster werden erkannt. Aber mehr Etagen bedeuten auch mehr Rechenleistung.

### Baustein 7: Das Training — Lernen aus Millionen Fehlern

Jetzt steht die gesamte Architektur. Aber am Anfang sind alle internen Werte (**Gewichte**) zufällig. Das Modell produziert puren Unsinn. Es muss **trainiert** werden.

Wie? Durch das Spiel „Nächstes Wort vorhersagen" — millionenfach wiederholt.

**So läuft ein Trainingsschritt ab:**

1. Das Modell bekommt: „Der Kunde möchte einen Kredit für ___"
2. Es rät (anfangs wild): „Marmelade?"
3. Die richtige Antwort wird aufgedeckt: „ein Haus"
4. Das Modell berechnet, **wie falsch** es lag (den sogenannten „Loss")
5. Alle internen Gewichte werden **ein winziges Stück** in die richtige Richtung angepasst
6. Nächster Satz. Nächstes Wort. Raten. Korrigieren. Anpassen.

Erinnern Sie sich an das Kind mit den Gute-Nacht-Geschichten? Es ist, als würde das Kind „Lückentext spielen": „Es war einmal ___" — das Kind rät „ein Drache?" — und hört „Nein, es war ‚eine Prinzessin'." Das Kind merkt sich das. Wiederholen Sie das mit **Milliarden von Textstellen**, und das Kind wird erstaunlich gut im Raten.

Dieses Training dauert in der Praxis **Wochen bis Monate** auf spezialisierten Hochleistungsrechnern. Aber das Konzept bleibt simpel: **Vorhersagen → Vergleichen → Korrigieren → Wiederholen.**

### Baustein 8: Text generieren — Ein Wort nach dem anderen

Nach dem Training kann das Modell endlich Text erzeugen. Sie geben einen **Prompt** (eine Eingabe) ein, und das Modell erzeugt die Fortsetzung:

```
Eingabe:  „Sehr geehrter Herr Müller, vielen Dank für"
          ↓
Modell:   Berechnet Wahrscheinlichkeiten für das nächste Wort
          „Ihre" → 85%
          „den"  → 8%
          „das"  → 3%
          ↓
Ausgabe:  „Ihre"
```

Jetzt wird „Ihre" an die Eingabe angehängt, und das Spiel beginnt von vorn:

```
„Sehr geehrter Herr Müller, vielen Dank für Ihre"  → „Anfrage"
„...vielen Dank für Ihre Anfrage"                   → „bezüglich"
„...Ihre Anfrage bezüglich"                         → „eines"
„...bezüglich eines"                                → „Baufinanzierungskredits"
```

Und so weiter, **Wort für Wort**, bis das Modell fertig ist oder eine festgelegte Länge erreicht wird. Das Modell plant den Text dabei nicht voraus — es wählt jedes Wort basierend auf allem, was bisher geschrieben wurde, und den Mustern aus dem Training.

---

## Das Gesamtbild

Alle acht Bausteine greifen wie Zahnräder ineinander:

```
Text → Tokenizer → Embeddings → Positional Encoding → Attention → Schichten → Training → Textgenerierung
  📄       ✂️          📍             📑                   👀         🏢         🎓          ✍️
```

Jedes Teil ist unverzichtbar:
- **Ohne Tokenizer** kann das Modell Text nicht lesen
- **Ohne Embeddings** kennt es keine Wortbedeutungen
- **Ohne Positional Encoding** verliert es die Reihenfolge
- **Ohne Attention** kann es keine Zusammenhänge erkennen
- **Ohne Training** produziert es nur Zufallstext

Zusammen bilden diese Bausteine die Maschinerie hinter **jedem** modernen Sprachmodell, das Sie nutzen.

---

## Das Wichtigste auf einen Blick

| Erkenntnis | Was das bedeutet |
|-----------|-----------------|
| **LLMs erkennen Muster — sie denken nicht** | Das Modell weiß nicht, was ein „Kredit" wirklich *ist*. Aber es weiß genau, wie das Wort typischerweise verwendet wird. |
| **Größe ist der Schlüssel** | Milliarden von Wörtern + Milliarden von Parametern = erstaunlich gute Muster. Mehr Daten + größeres Modell = bessere Ergebnisse. |
| **Attention ist der Durchbruch** | Weil jedes Wort jedes andere „ansehen" kann, versteht das Modell Zusammenhänge über weite Strecken — z.B. einen Bezug auf etwas, das drei Sätze vorher gesagt wurde. |
| **Einfache Teile, clever kombiniert** | Text in Tokens zerlegen, Tokens in Vektoren umwandeln, Position hinzufügen, Attention anwenden, trainieren. Keine Magie — nur sehr viel Lernen aus Daten. |

---

## Was das für Ihren Alltag bedeutet

Wenn Sie das nächste Mal ChatGPT oder Copilot nutzen und eine erstaunlich gute Antwort bekommen, erinnern Sie sich: Unter der Haube stellt das System immer wieder **eine einzige Frage**:

> *„Was ist — basierend auf allem, was ich bisher gesehen habe — das wahrscheinlichste nächste Wort?"*

Das ist der ganze Trick. Und die Tatsache, dass diese einfache Idee — hochskaliert auf Milliarden von Parametern und Billionen von Wörtern — etwas produziert, das sich anfühlt wie Verständnis?

**Das ist vielleicht das Faszinierendste an moderner KI.**

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **LLM** | Large Language Model — ein KI-Modell, das auf riesigen Textmengen trainiert wurde, um Sprache vorherzusagen |
| **Token** | Ein Textstück (Wort oder Wortteil), das das Modell verarbeiten kann |
| **Embedding** | Ein Zahlenvektor, der die Bedeutung eines Tokens auf einer „Bedeutungs-Landkarte" darstellt |
| **Attention** | Der Mechanismus, mit dem das Modell herausfindet, welche Wörter füreinander wichtig sind |
| **Transformer** | Die Architektur (Bauplan), die seit 2017 die Grundlage aller modernen Sprachmodelle bildet |
| **Parameter** | Interne „Stellschrauben" des Modells, die beim Training angepasst werden. GPT-3 hat 175 Milliarden davon |
| **Prompt** | Ihre Eingabe an das Modell — der Text, auf den es reagiert |
| **Training** | Der Prozess, bei dem das Modell durch millionenfaches „Wort-Raten" lernt, Muster in Sprache zu erkennen |
| **Loss** | Ein Fehlerwert, der angibt, wie weit die Vorhersage des Modells von der richtigen Antwort entfernt war |

---

*Nächstes Tutorial: **00-02 — Wie Diffusion-Modelle funktionieren** (Bildgenerierung mit Google Nano Banana Pro, GPT Image 1.5, Midjourney & Co.)*

---

