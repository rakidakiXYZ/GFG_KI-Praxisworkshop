# 14 Ethik, Sicherheit und Verantwortung

Dieses Kapitel ist das rechtliche und ethische Rückgrat für alle anderen Kapitel dieses Tutorials. Es beantwortet die Fragen, die spätestens auftauchen, sobald KI nicht mehr nur Spielerei ist, sondern echte Arbeit erledigt: **Darf ich diese Daten überhaupt hineinkippen? Was passiert mit meinem Output rechtlich? Wie erkenne ich, ob die KI mir Unsinn erzählt? Welche Vorschriften gelten für mich als Anwender eigentlich — und welche nur für die Anbieter?**

Die vier großen Themenblöcke sind DSGVO, der EU AI Act, Halluzinationen und Urheberrecht. Dazu kommt ein eigener Teil zu Bias und ein Praxis­leitfaden mit Checklisten, Ampeln und Entscheidungshilfen, die Sie direkt in Ihren Arbeits­alltag übernehmen können.

Dieses Kapitel setzt auf Kapitel 10 (Claude-Infrastruktur) und Kapitel 09 (KI-Tool-Landschaft) auf. In Kapitel 10 sind an mehreren Stellen Verweise auf „Kapitel 14" enthalten — insbesondere bei der Frage, welche Daten niemals in einen Cowork-Ordner gehören. Diese offenen Fäden werden hier sauber zu Ende geführt.

Wichtig vorab: Dieses Kapitel ersetzt keine Rechts­beratung. Es macht Sie aber in die Lage, die richtigen Fragen zu stellen — an Ihren Datenschutz­beauftragten, Ihren Betriebsrat oder Ihre Rechts­abteilung. Und es gibt Ihnen praktische Werkzeuge, um typische Fallstricke zu vermeiden.

## Struktur

| Datei | Inhalt |
|-------|--------|
| [01 Warum Ethik im KI-Zeitalter](./01%20Warum%20Ethik%20im%20KI-Zeitalter.md) | Motivation, Risiko-Landkarte, wie Sie dieses Kapitel lesen |
| [02 DSGVO und KI — Was darf in welches Tool](./02%20DSGVO%20und%20KI.md) | Personenbezogene Daten, AVV, EU-Hosting, Ampel für sensible Daten |
| [03 Der EU AI Act — Risikoklassen und Pflichten](./03%20Der%20EU%20AI%20Act.md) | Risikopyramide, Deployer-Pflichten, Bußgelder, was bis 2026 gilt |
| [04 Halluzinationen erkennen und vermeiden](./04%20Halluzinationen%20erkennen.md) | Warum KI lügt, wie Sie es merken, Faktencheck-Routine |
| [05 Urheberrecht und KI-generierte Inhalte](./05%20Urheberrecht.md) | Schöpfungshöhe, LG Hamburg, Nutzungsrechte an ChatGPT-/Claude-Outputs |
| [06 Bias erkennen und reduzieren](./06%20Bias%20erkennen.md) | Wo Bias herkommt, typische Muster, Techniken zur Gegen­steuerung |
| [07 Praxisleitfaden — Checklisten und Entscheidungshilfen](./07%20Praxisleitfaden.md) | Copy-paste-Checklisten, Muster-Prompts, Team-Leitlinien |

## Illustrationen

Alle Illustrationen liegen im konsistenten Whiteboard-Stil (wie Kapitel 09 und 10) unter [`illustrations/`](./illustrations/):

- `14-01-risiko-matrix.png` — Wahrscheinlichkeit × Auswirkung bei KI-Einsatz
- `14-02-ai-act-pyramide.png` — Die vier Risikoklassen des EU AI Act
- `14-03-daten-ampel.png` — Welche Daten gehören in welches Tool?
- `14-04-faktencheck-cycle.png` — Der Sechs-Schritt-Faktencheck
- `14-05-dsgvo-entscheidungsbaum.png` — „Darf ich das?" — in fünf Fragen zur Antwort

## Empfohlene Lesereihenfolge

**Wenn Sie wenig Zeit haben:** 01 (Einstieg) → 02 (DSGVO-Ampel) → 07 (Checklisten). Das sind die drei Teile, die Sie sofort in Ihren Arbeits­alltag übernehmen können.

**Wenn Sie im Unternehmen Verantwortung tragen:** Der Reihe nach, 01 bis 07. Die Teile 02 und 03 sind der Kern für Governance, 06 für Personal­entscheidungen, 07 für Team-Leitlinien.

**Wenn Sie als Einzelperson KI nutzen:** 01 → 04 (Halluzinationen) → 05 (Urheberrecht) → 07. DSGVO und AI Act sind für Sie trotzdem wichtig, aber weniger dringend als für Unternehmen.

**Wenn Sie ein bestimmtes Thema gerade akut haben:** Springen Sie direkt in den passenden Teil — jeder Teil ist so geschrieben, dass er auch einzeln funktioniert.

## Querverweise zu anderen Kapiteln

- **Kapitel 00 (Grundlagen LLMs)** — Wie Sprachmodelle funktionieren. Wichtig, um Halluzinationen zu verstehen (Teil 04).
- **Kapitel 01 (Prompt Engineering Text)** — Bessere Prompts reduzieren Halluzinationen und Bias. Teil 04 und 06 bauen darauf auf.
- **Kapitel 03 (GPTs und Projekte)** — Die dortige Persona „KI-Rechtsexpertin" ergänzt dieses Kapitel um einen interaktiven Sparring­spartner für rechtliche Zweifels­fragen.
- **Kapitel 09 (KI-Tool-Landschaft 2026)** — Datenschutz-Einordnung der großen Anbieter. Teil 02 verweist für Detail­vergleiche dorthin.
- **Kapitel 10 (Claude-Infrastruktur)** — Cowork, Claude Code und VS Code. Teil 02 schließt die dort gesetzten Verweise zu „welche Daten dürfen in einen Cowork-Ordner".
- **Kapitel 11 (KI & Daten)** — sobald verfügbar, zeigt es, wie Sie Tabellen sicher auswerten.

## Stand der rechtlichen Fakten

Alle rechtlichen Aussagen in diesem Kapitel beziehen sich auf **Stand April 2026**. Die Quellen sind:

- **DSGVO:** Orientierungs­hilfen der Datenschutz­konferenz (DSK), zuletzt Juni 2025, und EDPB Opinion 28/2024 (Dezember 2024).
- **EU AI Act:** Verordnung (EU) 2024/1689, Phase 1 (Februar 2025), Phase 2 (August 2025), vollständiges Inkraft­treten für Hoch­risiko-Systeme am 2. August 2026.
- **Urheberrecht:** § 2 und § 44b UrhG, LG Hamburg vom 27. September 2024 (LAION-Urteil) sowie die Berufungs­entscheidung des OLG Hamburg vom 10. Dezember 2025.
- **Zentrale deutsche AI-Act-Behörde:** Bundesnetz­agentur (BNetzA) als Koordinierungs- und Kompetenz­zentrum KoKIVO.

Recht entwickelt sich. Prüfen Sie bei allem, was in diesem Kapitel juristisch klingt, vor einer wichtigen Entscheidung bitte den aktuellen Stand auf den offiziellen Seiten der DSK (https://www.datenschutzkonferenz-online.de), des BfDI (https://www.bfdi.bund.de) und der EU-Kommission (https://digital-strategy.ec.europa.eu/de/policies/regulatory-framework-ai).

## Wichtiger Haftungs­hinweis

Dieses Kapitel ist eine Einführung für Nicht-Juristen. Es ist sorgfältig recherchiert, aber es ist keine Rechts­beratung und ersetzt sie nicht. Bei konkreten Entscheidungen mit recht­lichem Gewicht — zum Beispiel beim Abschluss eines Auftrags­verarbeitungs­vertrags, der Einführung eines KI-Systems für Bewerber­auswahl oder der Veröffentlichung KI-generierter Inhalte mit kommerziellem Anspruch — ziehen Sie bitte eine Datenschutz­beauftragte, eine Fach­anwältin für IT-Recht oder den zuständigen internen Stelle hinzu.

