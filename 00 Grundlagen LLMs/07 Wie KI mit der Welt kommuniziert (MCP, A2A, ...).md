
# Wie KI mit der Außenwelt kommuniziert

**Von isolierten Chatbots zu vernetzten Agenten — wie Protokolle wie MCP und A2A die KI aus ihrem Käfig befreien, und warum das der TCP/IP-Moment der KI-Ära ist**

---

## Warum dieses Tutorial?

In den vorherigen Tutorials haben Sie gelernt, wie KI Text versteht (Tutorial 00-01), Bilder erzeugt (Tutorial 00-02), verschiedene Modalitäten verbindet (Tutorial 00-03), Videos generiert (Tutorial 00-04), Audio erschafft (Tutorial 00-05) und ganze Welten simuliert (Tutorial 00-06). All diese Systeme haben eines gemeinsam: Sie leben in einer **Blase**.

Ein LLM kann brillant über Kontostände sprechen — aber es kann keinen echten Kontostand abfragen. Ein Bildgenerator kann Geschäftsberichte visualisieren — aber er kann den Bericht nicht aus dem Archiv holen. Eine KI kann die perfekte E-Mail formulieren — aber sie ohne Hilfe nicht absenden.

Stellen Sie sich vor, Sie hätten den klügsten Mitarbeiter der Welt eingestellt. Er sitzt in einem Büro ohne Telefon, ohne Computer, ohne Zugang zum Intranet. Sie können ihm Fragen stellen und er antwortet brillant — aber er kann nichts **tun**. Er kann keine Daten nachschlagen, keine Kollegen kontaktieren, kein System bedienen.

Genau so funktionierte KI bis 2024. Dann änderte sich alles.

Im November 2024 veröffentlichte Anthropic das **Model Context Protocol (MCP)** — ein offener Standard, der KI-Systemen einen universellen Anschluss an die Außenwelt gibt. Im April 2025 folgte Google mit dem **Agent2Agent Protocol (A2A)** — damit KI-Agenten nicht nur mit Werkzeugen, sondern auch **untereinander** kommunizieren können. Im Mai 2025 erschien **AG-UI** für die Verbindung zur Benutzeroberfläche, und OpenAI brachte **AGENTS.md** für Code-Repositories. Im Dezember 2025 gründeten Anthropic, OpenAI und Block gemeinsam die **Agentic AI Foundation (AAIF)** unter dem Dach der Linux Foundation — und machten aus konkurrierenden Standards ein gemeinsames Ökosystem.

Vier Protokolle. Vier Probleme gelöst. Ein Stack, der die KI-Welt so grundlegend vernetzt wie TCP/IP einst das Internet.

**Was Sie nach diesem Tutorial wissen werden:**

- Warum KI-Systeme bisher in Silos gefangen waren — und was das in der Praxis kostet
- Was MCP ist und wie es KI-Agenten Zugriff auf Werkzeuge und Daten gibt
- Was A2A ist und wie KI-Agenten untereinander Aufgaben delegieren
- Wie AG-UI und AGENTS.md die letzten Lücken schließen
- Wie die vier Protokolle zusammen einen Stack bilden — analog zu TCP/IP
- Welche Sicherheitsrisiken diese neue Vernetzung mit sich bringt
- Was das konkret für Ihren Arbeitsalltag in der Bank bedeutet

---

## Ein kurzer Blick zurück: Wie KI lernte, mit der Welt zu reden

| Jahr | Meilenstein | Was es konnte |
|------|------------|---------------|
| **2023 Mär** | **OpenAI Function Calling** | Erste Möglichkeit, ein LLM strukturiert mit externen APIs zu verbinden — aber nur für OpenAI-Modelle, proprietäres Format |
| **2023 Mai** | **ChatGPT Plugins** | Nutzer konnten erstmals Drittanbieter-Tools (Expedia, Wolfram Alpha) in ChatGPT einbinden — aber geschlossenes Ökosystem, wurde 2024 eingestellt |
| **2023 Nov** | **OpenAI Assistants API** | Agenten mit Dateizugriff, Code-Interpreter und Function Calling — aber alles innerhalb des OpenAI-Universums |
| **2024 Mär** | **Anthropic Tool Use** | Claude bekommt Tool-Aufrufe — aber eigenes Format, inkompatibel mit OpenAI |
| **2024 Nov** | **MCP (Model Context Protocol)** | Anthropic veröffentlicht den ersten **offenen Standard** für Tool-Anbindung: Ein Protokoll für alle Modelle, alle Tools |
| **2025 Mär** | **OpenAI adoptiert MCP** | Der größte Konkurrent steigt ein — MCP wird zum De-facto-Standard für Agent-Tool-Kommunikation |
| **2025 Apr** | **Google A2A (Agent2Agent)** | Google veröffentlicht das erste Protokoll für **Agent-zu-Agent**-Kommunikation — Agenten verschiedener Anbieter können zusammenarbeiten |
| **2025 Mai** | **AG-UI (Agent-User Interaction)** | CopilotKit veröffentlicht ein Protokoll für die Verbindung zwischen KI-Backend und Frontend — Agenten können interaktive UIs erzeugen |
| **2025 Jun** | **OpenAI AGENTS.md** | Ein einfaches Dateiformat, das Coding-Agenten projektspezifische Anweisungen gibt — wie eine README, aber für KI |
| **2025 Jun** | **A2A unter Linux Foundation** | Google übergibt A2A an die Linux Foundation — der Weg zur Vendor-Neutralität |
| **2025 Dez** | **Agentic AI Foundation (AAIF)** | Anthropic, OpenAI und Block gründen die AAIF unter der Linux Foundation. MCP, goose und AGENTS.md werden als Gründungsprojekte eingebracht. Platinum-Mitglieder: AWS, Google, Microsoft, Bloomberg, Cloudflare |
| **2026 Jan** | **MCP + A2A + AG-UI in Produktion** | Google ADK, LangGraph v0.2 und Microsoft Agent Framework unterstützen alle drei Protokolle nativ |

**Das Muster:** Von proprietären Insellösungen (2023) über offene Standards (2024–2025) zu einem vereinten Ökosystem unter gemeinsamer Governance (2025–2026). Die KI-Welt durchläuft in zwei Jahren, wofür das Internet ein Jahrzehnt brauchte.

> **Bank-Analogie:** Erinnern Sie sich an die Zeit, als jede Bank ihre eigene, inkompatible Software für Überweisungen hatte? Dann kamen Standards wie SWIFT und SEPA — und plötzlich konnte jede Bank mit jeder anderen kommunizieren. MCP und A2A sind das SWIFT und SEPA der KI-Welt: Sie schaffen einen gemeinsamen Kommunikationsstandard, damit KI-Systeme verschiedener Anbieter zusammenarbeiten können.

---

## Die Analogie: Das Telefonnetz für KI

Stellen Sie sich vor, KI-Systeme sind wie Büros in einem großen Gebäude. Bisher hatte jedes Büro nur eine Gegensprechanlage — Sie konnten mit dem Mitarbeiter darin sprechen, aber der Mitarbeiter konnte:

1. **Nicht telefonieren** — Er konnte keine anderen Systeme anrufen (keine Tool-Anbindung)
2. **Nicht mit anderen Büros sprechen** — Selbst wenn nebenan ein Spezialist saß (keine Agent-zu-Agent-Kommunikation)
3. **Keine Formulare ausfüllen** — Er konnte antworten, aber nichts auf Ihrem Bildschirm interaktiv darstellen (keine UI-Verbindung)
4. **Keine Hausregeln lesen** — Er kannte die Gepflogenheiten des Gebäudes nicht (keine Repository-Anweisungen)

Die vier Protokolle lösen genau diese vier Probleme:

```
┌──────────────────────────────────────────────────────────────────┐
│                DAS PROTOKOLL-GEBÄUDE                              │
│                                                                   │
│  Sie (Nutzer) ←──── AG-UI ────→ [🖥️ Empfang]                    │
│                                  (Frontend)                       │
│                                      │                            │
│                                      ▼                            │
│                              [🤖 Ihr KI-Agent]                   │
│                               /          \                        │
│                      A2A ───/              \─── MCP               │
│                            /                \                     │
│                    [🤖 Spezialist]    [🔧 Werkzeuge]             │
│                    (anderer Agent)    (Datenbanken,               │
│                                       APIs, Tools)               │
│                                                                   │
│  ────────────── AGENTS.md ──────────────────────                  │
│  (Hausregeln: "In diesem Gebäude benutzen wir..."  )              │
└──────────────────────────────────────────────────────────────────┘
```

---

## Schritt 1: Das Problem — Warum KI in Silos feststeckte

### Die unbequeme Wahrheit

Die meisten „KI-Agenten" in der Praxis sind keine echten Agenten. Sie sind **bessere Chatbots**. Alles läuft innerhalb eines einzigen Anbieters, orchestriert von einem einzigen Framework, verbunden mit Tools über selbstgeschriebene Adapter, die jemand am Wochenende zusammengebastelt hat.

Das funktioniert — solange Sie innerhalb der Grenzen bleiben. Sobald Sie eine Grenze überqueren, bricht alles zusammen:

**Grenze 1: Agent → Werkzeug (die Tool-Grenze)**
Wollen Sie, dass Ihr KI-Agent auf 50 verschiedene Tools zugreift? Ohne Standard heißt das: 50 verschiedene Adapter schreiben und pflegen. Jedes Tool hat sein eigenes API-Format, seine eigene Authentifizierung, seine eigene Fehlerbehandlung. Das sind 150.000 Tokens Overhead, bevor der Agent überhaupt anfängt zu denken.

**Grenze 2: Agent → Agent (die Organisations-Grenze)**
Agent A wurde mit LangChain gebaut, Agent B mit CrewAI, Agent C läuft bei einem anderen Unternehmen. Wie sollen die zusammenarbeiten? Es gibt keinen Weg für Agent A, herauszufinden, was Agent B kann — geschweige denn, ihm sicher eine Aufgabe zu übergeben.

**Grenze 3: Agent → Nutzer (die UI-Grenze)**
Jede KI-Anwendung baut Streaming, Status-Updates und interaktive Elemente von Grund auf neu. Es gibt kein gemeinsames Vokabular dafür, wie ein KI-Backend mit einem Frontend kommuniziert.

**Grenze 4: Agent → Code-Repository (die Repository-Grenze)**
Coding-Agenten brauchen projektspezifische Anweisungen (Build-Befehle, Konventionen, Testregeln). Aber es gibt keinen Standardort dafür. Entwickler stopfen alles in README-Dateien oder erstellen tool-spezifische Configs, die nur mit einem Agent funktionieren.

> **Bank-Analogie:** Stellen Sie sich vor, Ihre Filiale hat vier Abteilungen: Kredit, Girokonto, Wertpapiere, Compliance. Jede hat ihr eigenes IT-System, keine spricht mit der anderen. Ein Kunde will einen Kredit beantragen, dafür brauchen Sie seinen Kontostand (Girokonto), seine Wertpapiere als Sicherheit (Depot) und eine Compliance-Prüfung. Ohne gemeinsame Schnittstellen bedeutet das: drei Anrufe, drei Systeme, dreimal Daten abtippen. Genau so war der Zustand bei KI-Agenten vor MCP und A2A.

---

## Schritt 2: MCP — Das Werkzeug-Protokoll (Agent → Tool)

### Was MCP macht

Das **Model Context Protocol** ist die Antwort auf die Tool-Grenze. Es ist ein offener Standard, der definiert, wie ein KI-Agent auf externe Werkzeuge, Daten und Kontexte zugreift — egal welches Modell, egal welcher Anbieter.

Denken Sie an **USB**: Bevor USB kam, hatte jedes Gerät seinen eigenen Stecker. Drucker hatten Parallel-Ports, Mäuse hatten PS/2, Kameras hatten proprietäre Kabel. USB hat das alles ersetzt — ein Anschluss für alles. MCP ist das USB für KI-Werkzeuge.

### Wie MCP funktioniert

MCP folgt einer **Client-Server-Architektur**, inspiriert vom Language Server Protocol (LSP), das Programmier-Editoren schon seit Jahren nutzen:

```
┌─────────────────────────────────────────────────────────┐
│              MCP-ARCHITEKTUR                              │
│                                                          │
│  ┌──────────────────────────┐                            │
│  │     MCP Host             │                            │
│  │  (z.B. Claude, ChatGPT,  │                            │
│  │   VS Code, Ihr Agent)    │                            │
│  │                          │                            │
│  │  ┌────────┐ ┌────────┐  │                             │
│  │  │Client 1│ │Client 2│  │                             │
│  │  └───┬────┘ └───┬────┘  │                             │
│  └──────┼──────────┼───────┘                             │
│         │          │                                     │
│    JSON-RPC    JSON-RPC                                  │
│         │          │                                     │
│  ┌──────▼────┐ ┌───▼───────┐                             │
│  │MCP Server │ │MCP Server │                             │
│  │(Datenbank)│ │(E-Mail)   │                             │
│  └───────────┘ └───────────┘                             │
└─────────────────────────────────────────────────────────┘
```

**Die drei Bausteine von MCP:**

| Baustein | Was er tut | Bank-Beispiel |
|----------|-----------|---------------|
| **Resources** (Ressourcen) | Stellt Daten bereit, die der Agent lesen kann | Kontostände, Kundendaten, Dokumente aus dem DMS |
| **Tools** (Werkzeuge) | Aktionen, die der Agent ausführen kann | Überweisung ausführen, E-Mail senden, Termin buchen |
| **Prompts** (Vorlagen) | Wiederverwendbare Gesprächs-Vorlagen | „Erstelle einen Beratungsbericht für Kunde X nach Schema Y" |

### Der Ablauf: Wie ein MCP-Aufruf funktioniert

1. **Verbindung herstellen:** Der Host (z.B. Claude) startet eine Verbindung zum MCP-Server und handelt aus, welche Fähigkeiten verfügbar sind (Capability Negotiation)
2. **Werkzeug-Katalog lesen:** Der Agent erhält eine Liste aller verfügbaren Tools mit Beschreibungen — z.B. „`abfrage_kontostand`: Ruft den aktuellen Kontostand für eine IBAN ab"
3. **Werkzeug aufrufen:** Der Agent entscheidet basierend auf der Nutzeranfrage, welches Tool er braucht, und sendet einen JSON-RPC-Aufruf
4. **Ergebnis empfangen:** Der MCP-Server führt die Aktion aus und liefert das Ergebnis strukturiert zurück
5. **Antwort formulieren:** Der Agent verarbeitet das Ergebnis und formuliert eine natürlichsprachliche Antwort

> **Bank-Analogie:** MCP funktioniert wie das standardisierte Nachrichtenformat bei SWIFT-Überweisungen. Es ist egal, ob die sendende Bank Software von SAP benutzt und die empfangende von Oracle — das Nachrichtenformat ist dasselbe. Genauso ist es bei MCP egal, ob der Agent von Anthropic, OpenAI oder Google stammt und ob das Tool eine Datenbank, ein E-Mail-System oder ein CRM ist — das Protokoll ist dasselbe.

### MCP in der Praxis heute

MCP hat in atemberaubendem Tempo Verbreitung gefunden. Als Anthropic MCP im Dezember 2025 an die AAIF übergab, meldete das Unternehmen **über 97 Millionen monatliche SDK-Downloads** allein für Python und TypeScript. Das ist keine experimentelle Nutzung — das ist Infrastruktur-Niveau.

| Wo | Was |
|----|-----|
| **Claude Desktop** | Nutzer können MCP-Server für Dateisystem, GitHub, Slack etc. anbinden |
| **ChatGPT** | OpenAI hat MCP im März 2025 offiziell adoptiert |
| **VS Code / Cursor** | KI-Coding-Assistenten greifen über MCP auf Projekt-Dateien, Git, Sentry etc. zu |
| **Microsoft Azure** | Azure OpenAI unterstützt MCP-Server nativ |
| **Cloudflare** | MCP-Server können direkt auf Cloudflare gehostet werden |
| **GitHub MCP Registry** | Zentrale Registry für wiederverwendbare MCP-Server — wie npm, aber für KI-Tools |

---

## Schritt 3: A2A — Das Delegations-Protokoll (Agent → Agent)

### Was A2A macht

MCP löst die Verbindung zwischen Agent und Werkzeug. Aber was, wenn ein Agent nicht ein Tool braucht, sondern einen **anderen Agenten**? Nicht als Werkzeug — als **Kollegen**.

Das **Agent2Agent Protocol (A2A)** löst genau dieses Problem. Es definiert, wie KI-Agenten verschiedener Anbieter, Frameworks und Organisationen als gleichberechtigte Partner zusammenarbeiten.

Der entscheidende Unterschied zu MCP: Bei MCP ist der Agent der **Chef** und das Tool der **Mitarbeiter**, der Anweisungen ausführt. Bei A2A sind beide Agenten **Kollegen** auf Augenhöhe, die Aufgaben delegieren und Ergebnisse austauschen.

Eine kritische Design-Entscheidung in A2A ist **Opazität**: Agenten können zusammenarbeiten, **ohne ihren internen Zustand, ihre Tools oder ihre proprietäre Logik offenzulegen**. Genau das macht A2A für Unternehmen interessant — Sie können einem externen Agenten eine Teilaufgabe übergeben, ohne zu verraten, wie Ihr Agent intern funktioniert. A2A wird von **über 150 Organisationen** unterstützt.

Ein starkes Konsolidierungssignal: Im August 2025 haben IBM und Google das IBM Research **Agent Communication Protocol (ACP)** in A2A zusammengeführt. Wenn konkurrierende Entwürfe aufhören zu konkurrieren und anfangen zu verschmelzen — *das* ist der TCP/IP-Moment.

### Wie A2A funktioniert

A2A hat drei Kern-Bausteine:

```
┌─────────────────────────────────────────────────────────┐
│              A2A-ARCHITEKTUR                              │
│                                                          │
│  [🤖 Orchestrator-Agent]                                 │
│         │                                                │
│    1. Discovery: "Wer kann Flüge buchen?"                │
│         │                                                │
│         ▼                                                │
│  [📇 Agent Card]  ←── Visitenkarte des Spezialisten      │
│    Name: FlightBot                                       │
│    Kann: Flüge suchen, Preise vergleichen                │
│    Braucht: Reisedaten, Budget                           │
│    Auth: OAuth 2.0                                       │
│         │                                                │
│    2. Task erstellen: "Finde Flüge nach Tokio < 500€"   │
│         │                                                │
│         ▼                                                │
│  [🤖 Spezialist-Agent]                                   │
│    - Nutzt MCP, um Flug-APIs abzufragen                  │
│    - Sendet Zwischen-Updates via SSE                     │
│    - Liefert Ergebnis als strukturierte Nachricht        │
│         │                                                │
│    3. Ergebnis: 12 Flugoptionen mit Preisen              │
│         │                                                │
│         ▼                                                │
│  [🤖 Orchestrator-Agent]                                 │
│    → Verarbeitet Ergebnis weiter                         │
└─────────────────────────────────────────────────────────┘
```

| Baustein | Was er tut | Bank-Beispiel |
|----------|-----------|---------------|
| **Agent Card** (Visitenkarte) | Beschreibt, was ein Agent kann, was er braucht und wie man ihn erreicht | „Compliance-Agent: Prüft Transaktionen auf Geldwäsche. Braucht: Transaktionsdaten. Antwortet in <5 Sekunden." |
| **Task** (Aufgabe) | Eine Arbeitseinheit mit Status (eingereicht → in Bearbeitung → erledigt) | „Prüfe ob Überweisung #4711 regelkonform ist" |
| **Message** (Nachricht) | Kommunikation zwischen Agenten, kann Text, Dateien oder strukturierte Daten enthalten | Status-Updates, Zwischen-Ergebnisse, Rückfragen |

### Agent Cards: Die Visitenkarten der KI-Welt

Das Brillante an A2A ist die **Discovery-Phase**. Bevor ein Agent einen anderen um Hilfe bittet, liest er dessen Agent Card — eine maschinenlesbare Beschreibung seiner Fähigkeiten, die an einer standardisierten Adresse hinterlegt ist. Das ist wie DNS für Agenten: Man kennt die Adresse und bekommt alle Informationen.

```
# Discovery: Agent A findet die Visitenkarte von Agent B
# Die Agent Card liegt immer unter einer "Well-Known URI":

https://compliance-agent.bank.de/.well-known/agent-card.json

{
  "name": "Compliance-Prüfer",
  "description": "Prüft Finanztransaktionen auf regulatorische Konformität",
  "capabilities": ["AML-Check", "KYC-Validierung", "Sanctions-Screening"],
  "input": "Transaktionsdaten (Betrag, Sender, Empfänger, Zweck)",
  "output": "Risiko-Score + Begründung",
  "auth": "OAuth 2.0",
  "sla": "< 3 Sekunden"
}
```

> **Bank-Analogie:** A2A funktioniert wie das Korrespondenzbank-System. Wenn Ihre Filiale eine Transaktion in einer Fremdwährung abwickeln will, leitet sie diese an eine Korrespondenzbank weiter, die darauf spezialisiert ist. Sie müssen nicht selbst Experte für japanische Yen sein — Sie delegieren an jemanden, der es ist. Agent Cards sind dabei wie das SWIFT-Verzeichnis: Sie zeigen, welche Bank welche Dienste anbietet, wie man sie erreicht und welche Standards sie unterstützt.

---

## Schritt 4: AG-UI — Das Frontend-Protokoll (Agent → Benutzer)

### Was AG-UI macht

MCP verbindet Agenten mit Tools. A2A verbindet Agenten untereinander. Aber wie kommuniziert ein Agent mit dem **Menschen**, der vor dem Bildschirm sitzt?

**AG-UI (Agent-User Interaction Protocol)** löst die UI-Grenze. Es definiert einen Standard für die Kommunikation zwischen KI-Backends und Frontends — damit Agenten nicht nur Text ausgeben, sondern **interaktive Benutzeroberflächen** erzeugen können.

AG-UI wurde im Mai 2025 von CopilotKit veröffentlicht und streamt eine Sequenz von JSON-Events vom Agent zum Frontend:

```
┌─────────────────────────────────────────────────────────┐
│              AG-UI: AGENT → BENUTZEROBERFLÄCHE            │
│                                                          │
│  [🤖 Agent-Backend]                                      │
│         │                                                │
│    Stream von Events (Server-Sent Events):               │
│    ├── TextDelta: "Ich habe 3 Optionen gefunden..."      │
│    ├── StateChange: { "status": "searching" }            │
│    ├── ToolCall: { "name": "render_table", data: [...] } │
│    └── UIComponent: { "type": "card", ... }              │
│         │                                                │
│         ▼                                                │
│  [🖥️ Frontend / App]                                     │
│    → Rendert Text, Tabellen, Karten, Buttons             │
│    → Nutzer kann interagieren (klicken, filtern)         │
│    → Interaktionen fließen zurück zum Agent              │
└─────────────────────────────────────────────────────────┘
```

> **Bank-Analogie:** Denken Sie an den Unterschied zwischen Telefon-Banking und Online-Banking. Beim Telefon-Banking (= Agent ohne AG-UI) hören Sie nur Text: „Ihr Kontostand beträgt 3.247,50 €." Beim Online-Banking (= Agent mit AG-UI) sehen Sie interaktive Diagramme, können Überweisungen per Klick auslösen und bekommen Echtzeit-Updates. AG-UI macht aus dem „Telefon-Banking" mit KI ein „Online-Banking" mit KI.

---

## Schritt 5: AGENTS.md — Die Hausregeln (Agent → Repository)

### Was AGENTS.md macht

Die letzte Grenze ist die einfachste — und dennoch wichtig. **AGENTS.md** ist eine simple Markdown-Datei im Wurzelverzeichnis eines Code-Repositories, die Coding-Agenten sagt, wie sie mit dem Projekt arbeiten sollen.

```
# AGENTS.md (Beispiel)

## Repository-Regeln
- Benutze `npm run lint` vor jedem Commit
- Schreibe Tests für jede neue Funktion
- Dokumentiere öffentliche APIs in `docs/`
- Commit-Nachrichten auf Deutsch, im Format: "[Bereich] Beschreibung"

## Architektur
- Frontend: React + TypeScript
- Backend: Node.js + Express
- Datenbank: PostgreSQL
- Tests: Jest + Playwright
```

Das klingt banal — ist es aber nicht. Ohne AGENTS.md muss ein Coding-Agent raten, wie ein Projekt organisiert ist. Mit AGENTS.md weiß er es sofort. Das spart Fehlversuche, reduziert Code-Review-Aufwand und macht KI-generierte Pull Requests sofort brauchbar.

AGENTS.md wurde von OpenAI für Codex eingeführt und ist seit Dezember 2025 ein Projekt der Agentic AI Foundation.

> **Bank-Analogie:** AGENTS.md ist wie das Handbuch für neue Mitarbeiter — das „Onboarding-Dokument" Ihres Code-Repositories. Statt dass der neue Kollege (= KI-Agent) erst drei Wochen lang herausfinden muss, wo welche Datei liegt und welche Konventionen gelten, bekommt er am ersten Tag eine klare Anleitung.

---

## Schritt 6: Der Handshake — Wie eine Delegation konkret abläuft

### Theorie ist gut, aber wie funktioniert das wirklich?

Verfolgen wir eine echte Anfrage durch den Stack. Ein Nutzer fragt Agent A: **„Fasse die Umsatztrends für Q4 zusammen."** Agent A kann das nicht selbst, aber er weiß: Es gibt Agent B, der auf Finanzdaten spezialisiert ist.

**Schritt 1: Discovery über A2A — „Wer kann das?"**

Agent A fragt die Well-Known URI von Agent B ab:

```
GET https://agent-b.example.com/.well-known/agent-card.json

→ Antwort: Agent Card mit Fähigkeiten, Input/Output-Format,
  Authentifizierung
```

Das ist das „DNS-Lookup-Äquivalent" für Agenten.

**Schritt 2: Aufgabe delegieren über A2A — „Mach das bitte"**

```
POST https://agent-b.example.com/message:send
Content-Type: application/a2a+json
Authorization: Bearer $TOKEN

{
  "message": {
    "messageId": "msg-001",
    "role": "ROLE_USER",
    "parts": [{"text": "Fasse die Umsatztrends für Q4 zusammen"}]
  },
  "configuration": {
    "acceptedOutputModes": ["text/plain"]
  }
}
```

Beachten Sie: Agent A muss **nichts** über die Interna von Agent B wissen. Er schickt eine Nachricht und wartet auf Ergebnisse.

**Schritt 3: Tool-Aufruf über MCP — „Ich brauche die Daten"**

Agent B braucht echte Daten. Er fragt seinen MCP-Server:

```
# Schritt 3a: Welche Tools gibt es?
POST http://localhost:7000/mcp
{"jsonrpc":"2.0", "id":1, "method":"tools/list", "params":{}}

# Schritt 3b: Daten abrufen
POST http://localhost:7000/mcp
{"jsonrpc":"2.0", "id":2, "method":"tools/call",
 "params":{
   "name": "get_revenue_data",
   "arguments": {"quarter": "Q4", "metric": "trends"}
 }}
```

**Schritt 4: Zusammenführung — „Hier ist die Antwort"**

```
# Agent B's Handler — verbindet A2A mit MCP:

def handle_a2a_message(message_text):
    # 1) Aufgabe verstehen → welches MCP-Tool?
    tool_name = "get_revenue_data"
    args = {"quarter": "Q4", "metric": "trends"}

    # 2) MCP-Tool aufrufen (JSON-RPC)
    result = mcp_tools_call(tool_name, args)

    # 3) Ergebnis als A2A-Antwort zurückgeben
    return render_text(result)
```

**Die Eleganz liegt in der Trennung:** A2A kümmert sich um den „Aufgabe/Nachricht/Ergebnis"-Vertrag zwischen Agenten. MCP kümmert sich um den „Entdecke/Rufe Tools auf"-Vertrag zu externen Systemen. Jedes Protokoll macht eine Sache gut, und sie komponieren sauber.

> **Bank-Analogie:** Dieser Handshake funktioniert wie eine Auslandsüberweisung: Ihre Bank (Agent A) kennt die SWIFT-Adresse der Zielbank (Discovery via Agent Card). Sie schickt einen SWIFT-Auftrag in standardisiertem Format (A2A Task). Die Zielbank (Agent B) greift auf ihr internes Buchungssystem zu (MCP Tool Call) und bestätigt die Transaktion. Zu keinem Zeitpunkt muss Ihre Bank wissen, welche Software die Zielbank intern nutzt.

---

## Schritt 7: Der Skalierungs-Trick, den die meisten übersehen

### Das Token-Problem bei vielen Tools

Hier kommt eine Erkenntnis, die den Unterschied zwischen Oberflächen-Verständnis und echtem Expertenwissen ausmacht.

Der naive Ansatz für Tool-Integration: Man lädt **jedes** Tool-Schema in das Kontextfenster des Agenten. 50 Tools? Das sind 50 Schemas, leicht **150.000 Tokens** — verbrannt, bevor der Agent auch nur anfängt, über die eigentliche Frage nachzudenken.

MCP löst das mit **On-Demand Discovery**: Der Agent sieht nur die Tool-Liste, nicht alle Schemas auf einmal. Aber Anthropics Engineering-Team ging noch einen Schritt weiter mit einem Muster namens **„Code Execution with MCP"**: Statt dass der Agent Tools direkt über geladene Schemas aufruft, **schreibt der Agent Code**, der den MCP-Server als API aufruft.

```
┌───────────────────────────────────────────────────┐
│  TOKEN-VERBRAUCH BEI 50 TOOLS                      │
│                                                    │
│  Naiv (alle Schemas laden):    ~150.000 Tokens     │
│  MCP On-Demand Discovery:       ~10.000 Tokens     │
│  MCP + Code Execution:           ~2.000 Tokens     │
│                                                    │
│  Ersparnis:                     98,7%              │
└───────────────────────────────────────────────────┘
```

Deshalb ist MCP nicht nur ein Konnektivitäts-Standard. Es ist ein **Skalierungsmuster** für große Tool-Ökosysteme. Wenn Sie Agenten bauen, die auf Dutzende oder Hunderte von Tools zugreifen müssen, ist dieser Unterschied enorm — sowohl für Kosten als auch für Geschwindigkeit.

> **Bank-Analogie:** Stellen Sie sich vor, Sie müssten für jede mögliche Transaktion das komplette Regelwerk aller 800 Genossenschaftsbanken im Kopf haben, bevor Sie eine einzige Überweisung bearbeiten. Absurd. Stattdessen schauen Sie nur die Regeln nach, die Sie **gerade** brauchen. Genau das macht MCP mit Code Execution: Statt 150.000 Tokens „Regelwerk" vorab zu laden, werden nur die 2.000 Tokens geladen, die für die aktuelle Aufgabe relevant sind. Bei einem Tokenpreis von ~0,01 €/1000 Tokens spart das pro Anfrage ~1,50 € — bei tausenden Anfragen pro Tag ein erheblicher Betrag.

---

## Schritt 8: Der Protocol Stack — Vier Schichten, eine Architektur

### Die Adoption in Zahlen

Bevor wir die Architektur betrachten, ein Reality Check — das sind keine theoretischen Standards:

| Protokoll | Adoption (Stand Feb. 2026) |
|-----------|---------------------------|
| **MCP** | 97+ Millionen monatliche SDK-Downloads (Python + TypeScript) |
| **A2A** | 150+ unterstützende Organisationen, IBM ACP fusioniert |
| **AGENTS.md** | 60.000+ Open-Source-Repositories |
| **AG-UI** | Microsoft, LangGraph, CopilotKit nativ integriert |

### Die TCP/IP-Analogie

Jetzt kommt der entscheidende Punkt: Diese vier Protokolle sind nicht einfach vier unabhängige Standards. Sie bilden zusammen einen **Protocol Stack** — ähnlich wie TCP/IP das Internet ermöglicht hat.

```
┌───────────────────────────────────────────────────────────────┐
│          DER AGENT PROTOCOL STACK vs. TCP/IP                   │
│                                                                │
│  Agent-Stack              TCP/IP-Stack                         │
│  ────────────────         ────────────────                     │
│                                                                │
│  ┌──────────────┐         ┌──────────────┐                     │
│  │   AG-UI      │         │  Anwendung   │  ← Was der          │
│  │ Agent → UI   │         │ (HTTP, SMTP) │    Nutzer sieht     │
│  └──────┬───────┘         └──────┬───────┘                     │
│         │                        │                             │
│  ┌──────▼───────┐         ┌──────▼───────┐                     │
│  │    A2A       │         │  Transport   │  ← Wie Daten        │
│  │ Agent → Agent│         │   (TCP/UDP)  │    übertragen werden │
│  └──────┬───────┘         └──────┬───────┘                     │
│         │                        │                             │
│  ┌──────▼───────┐         ┌──────▼───────┐                     │
│  │    MCP       │         │  Internet    │  ← Wie Systeme      │
│  │ Agent → Tool │         │    (IP)      │    adressiert werden │
│  └──────┬───────┘         └──────┬───────┘                     │
│         │                        │                             │
│  ┌──────▼───────┐         ┌──────▼───────┐                     │
│  │  AGENTS.md   │         │  Netzwerk    │  ← Grundregeln      │
│  │ Agent → Repo │         │ (Ethernet)   │    der Umgebung      │
│  └──────────────┘         └──────────────┘                     │
└───────────────────────────────────────────────────────────────┘
```

### Wo die Analogie stimmt — und wo nicht

Wichtig: MCP und A2A sind **keine** Low-Level-Transport-Protokolle im Sinne des OSI-Modells. Beide sind **Anwendungsebene-Protokolle**, die über HTTP, SSE oder stdio laufen. Sie sitzen also *höher* im klassischen Netzwerk-Stack als TCP oder IP. Warum die Analogie trotzdem funktioniert: Man braucht keine OSI-Treue, um den Kernpunkt zu verstehen. KI-Interoperabilität ist nicht *ein* Protokoll — es ist ein **Stapel von Vereinbarungen auf verschiedenen Grenzen**, die unabhängig voneinander verwaltet und eingeführt werden können. Genau das ist die Einsicht, die zählt.

| Aspekt | TCP/IP | Agent Protocol Stack |
|--------|--------|---------------------|
| **Schichtung** | ✅ Jede Schicht hat klare Verantwortung | ✅ MCP ≠ A2A ≠ AG-UI — klare Trennung |
| **Composability** | ✅ HTTP funktioniert über TCP über IP | ✅ AG-UI nutzt A2A nutzt MCP |
| **Vendor-Neutralität** | ✅ Jeder kann TCP/IP implementieren | ✅ Alles unter Linux Foundation |
| **Netzwerkeffekte** | ✅ Jedes konforme Gerät kann mit jedem anderen kommunizieren | ✅ Jede konforme Komponente kann mit jeder anderen auf derselben Schicht kommunizieren |
| **Reife** | ✅ Jahrzehnte im Einsatz | ⚠️ Die Protokolle sind 1–2 Jahre alt |
| **Sicherheit** | ⚠️ Wurde nachgerüstet (TLS kam viel später) | ⚠️ Sicherheit ist auch hier noch lückenhaft |
| **Standardisierung** | ✅ RFCs, IETF | 🔴 Noch keine formalen RFCs, die Standards entwickeln sich schnell weiter |
| **Technische Ebene** | Transport + Internet-Schicht (OSI Layer 3–4) | ⚠️ Alle auf Anwendungsebene (über HTTP/SSE/stdio) — **keine** echten Transport-Protokolle |

### Ein Beispiel: Wie eine Anfrage durch den Stack fließt

Stellen Sie sich vor, ein Bankmitarbeiter fragt: **„Prüfe ob die Überweisung von Kunde Müller regulatorisch in Ordnung ist."**

```
┌─────────────────────────────────────────────────────────────┐
│  ANFRAGE-FLUSS DURCH DEN PROTOCOL STACK                      │
│                                                              │
│  1. AG-UI: Mitarbeiter tippt Anfrage in Bank-Chat-Interface │
│     └──→ Event-Stream zum KI-Backend                        │
│                                                              │
│  2. A2A: Orchestrator-Agent erkennt: "Ich brauche den       │
│     Compliance-Spezialisten"                                 │
│     └──→ Liest Agent Card des Compliance-Agenten             │
│     └──→ Erstellt Task: "Prüfe Überweisung #4711"           │
│                                                              │
│  3. MCP: Compliance-Agent nutzt MCP-Tools:                   │
│     ├── Tool 1: Überweisungsdaten abrufen (Kernbanksystem)  │
│     ├── Tool 2: Kundendaten prüfen (CRM)                    │
│     ├── Tool 3: Sanctions-Liste abgleichen (Compliance-DB)  │
│     └── Tool 4: Risiko-Score berechnen (Scoring-Engine)     │
│                                                              │
│  4. AGENTS.md: Der Compliance-Agent weiß dank AGENTS.md:    │
│     "Bei Risiko-Score > 70: automatisch Vier-Augen-Prinzip  │
│      einleiten. Alle Prüfungen dokumentieren."               │
│                                                              │
│  5. Ergebnis fließt zurück:                                  │
│     MCP → A2A → AG-UI → Interaktive Karte im Chat:         │
│     "✅ Überweisung #4711: Risiko-Score 23/100.              │
│      Keine Auffälligkeiten. [Details anzeigen] [Freigeben]" │
└─────────────────────────────────────────────────────────────┘
```

> **Bank-Analogie:** Dieser Fluss ist wie die Bearbeitung eines Kreditantrags in einer modernen Bank: Der Kundenberater (AG-UI) nimmt den Antrag entgegen, leitet ihn an die Kreditabteilung weiter (A2A), die ihrerseits Bonitätsdaten abfragt (MCP, Schufa), das Ergebnis nach internen Richtlinien bewertet (AGENTS.md) und dem Berater eine Empfehlung mit allen Details zurückgibt. Nur dass hier keine Menschen die Daten hin- und hertragen — die Protokolle erledigen das automatisch.

---

## Schritt 9: Sicherheit — Die offene Flanke

### Die unbequeme Wahrheit über Sicherheit

Wie bei TCP/IP, wo Sicherheit nachträglich eingebaut werden musste (SSL/TLS kam Jahre nach dem Internet), hat auch der Agent Protocol Stack **Sicherheitslücken**, die ernst genommen werden müssen.

### Bekannte Risiken

| Risiko | Beschreibung | Bank-Relevanz |
|--------|-------------|---------------|
| **Tool Poisoning** | Ein bösartiger MCP-Server manipuliert seine Werkzeug-Beschreibung, sodass der Agent ungewollt Daten preisgibt | 🔴 Ein kompromittierter MCP-Server könnte Kundendaten abgreifen |
| **Prompt Injection über Tools** | Daten, die ein MCP-Tool zurückliefert, enthalten versteckte Anweisungen für den Agenten | 🔴 Ein manipuliertes Dokument aus dem DMS könnte den Agenten umsteuern |
| **Fehlende Identität über Schichten** | MCP, A2A und AG-UI haben jeweils eigene Authentifizierung — es gibt keine durchgehende Identität | 🟡 Wer hat wirklich die Freigabe erteilt? Die Nachverfolgbarkeit ist lückenhaft |
| **Keine schichtübergreifende Nachverfolgung** | Wenn ein MCP-Tool innerhalb einer A2A-Aufgabe fehlschlägt, ist die Fehlerausbreitung undefiniert | 🟡 Compliance-Audits werden schwieriger |
| **Supply-Chain-Angriffe** | Bösartige MCP-Server können sich als vertrauenswürdige Tools ausgeben | 🔴 Wie gefälschte SWIFT-Nachrichten — nur automatisiert |

### Gegenmittel

| Maßnahme | Was sie tut |
|----------|-----------|
| **Principle of Least Privilege** | Jeder MCP-Server bekommt nur die minimalen Rechte, die er braucht |
| **Human-in-the-Loop** | Kritische Aktionen (Überweisungen, Löschungen) erfordern menschliche Bestätigung |
| **OAuth 2.1 für MCP** | Seit Juni 2025 unterstützt MCP OAuth 2.1 als Authentifizierungsstandard |
| **Agent Card Verification** | A2A-Agent Cards sollten kryptographisch signiert und verifiziert werden |
| **Sandboxing** | MCP-Server in isolierten Umgebungen ausführen, damit ein kompromittierter Server nicht auf andere zugreifen kann |
| **Audit Logging** | Alle Protokoll-Aufrufe über alle Schichten hinweg protokollieren |

> **Bank-Analogie:** Die Sicherheitsrisiken bei KI-Protokollen sind vergleichbar mit den Risiken beim Online-Banking in den Anfangsjahren. Auch dort gab es zuerst die Funktionalität (Überweisungen im Browser), und die Sicherheit (TAN-Verfahren, Zwei-Faktor-Authentifizierung) wurde schrittweise nachgerüstet. Wichtig ist: **Die Risiken sind beherrschbar** — aber nur, wenn man sie kennt und ernst nimmt.

---

## Schritt 10: Was das für Ihren Arbeitsalltag bedeutet

### Was heute schon möglich ist

| Anwendungsfall | Welche Protokolle | Beispiel in der Bank |
|---------------|-------------------|---------------------|
| **KI-Assistent mit Systemzugriff** | MCP | Claude greift auf Kernbanksystem zu und beantwortet Fragen zu Kundendaten |
| **Multi-Agenten-Workflows** | MCP + A2A | Kredit-Agent delegiert Bonitätsprüfung an Compliance-Agent, der Schufa-Daten über MCP abruft |
| **Interaktive KI-Dashboards** | MCP + AG-UI | Agent zeigt Risiko-Portfolio als interaktive Karten an, nicht nur als Text |
| **Automatisierte Code-Reviews** | AGENTS.md | Coding-Agent kennt die Entwicklungsrichtlinien der Bank und prüft Pull Requests dagegen |
| **Vollständiger Agent-Stack** | Alle vier | Kundenberater-Interface (AG-UI) → Orchestrator delegiert an Spezialisten (A2A) → Spezialisten greifen auf Systeme zu (MCP) → alle folgen Bankrichtlinien (AGENTS.md) |

### Was dieser Stack für Entwickler freischaltet

Standards lösen nicht nur bestehende Probleme — sie schaffen **neue Bauflächen**:

- **Agent-Marktplätze:** A2A's Agent-Card-Modell mit standardisierter Discovery, optionalen Signaturen und expliziten Sicherheits-Schemata ist eine offene Einladung für Agent-Verzeichnisse. Jemand wird das „npm Registry für Agenten" bauen — und A2A liefert die Bausteine
- **Portable Tool-Ökosysteme:** MCP-Server werden wie npm-Pakete: einmal schreiben, überall nutzen. Die GitHub MCP Registry macht das bereits möglich. Die Tage, in denen man für jedes Agent-Framework einen eigenen Slack-Connector baut, sind gezählt
- **Agent-Observability-Plattformen:** AG-UI schafft einen stabilen Integrationspunkt für Debugging-Tools und Zustandsvisualisierung — das „DevTools-Äquivalent" für KI-Agenten
- **Cross-Tool Coding Agents:** AGENTS.md in 60.000+ Repos wird zur portablen „Steuerungsebene" für das Verhalten von Coding-Agenten
- **Durchgehende Identität:** Ein Single-Sign-On über alle Protokoll-Schichten — damit Audit-Trails lückenlos sind
- **Autonome Workflows:** Agenten, die selbstständig Spezialisten finden, delegieren und Ergebnisse zusammenführen — mit menschlicher Aufsicht nur an kritischen Entscheidungspunkten

---

## Was kann diese Technologie (noch) nicht?

| Limitation | Warum das wichtig ist | Technologie allein vs. Gesamtsystem |
|-----------|----------------------|--------------------------------------|
| **Keine garantierte Zuverlässigkeit** | MCP-Server können ausfallen, A2A-Tasks können hängen bleiben — es gibt noch kein einheitliches Fehlerbehandlungsmodell über alle Schichten | **Technologie allein:** Die Protokolle definieren keine schichtübergreifende Fehlerbehandlung. **Im Gesamtsystem:** Frameworks wie LangGraph bauen Retry-Logik und Fallbacks ein |
| **Sicherheit ist noch unreif** | Die Protokolle sind 1–2 Jahre alt — Sicherheitsstandards entwickeln sich noch. 92% Exploit-Wahrscheinlichkeit bei 10+ MCP-Plugins laut Pynt-Studie | **Technologie allein:** OAuth 2.1, Sandboxing existieren. **Im Gesamtsystem:** Enterprise-Deployments brauchen zusätzliche Firewalls, Monitoring, Penetrationstests |
| **Kein durchgehender Audit Trail** | In regulierten Branchen (Bank!) muss nachvollziehbar sein, wer was wann getan hat. Die drei Protokoll-Schichten haben separate Logging-Systeme | **Technologie allein:** Jede Schicht kann einzeln loggen. **Im Gesamtsystem:** Unified Observability (z.B. OpenTelemetry) muss manuell integriert werden |
| **Begrenzte Modell-Fähigkeit** | Der Agent ist nur so gut wie das LLM dahinter. Ein schwaches Modell trifft schlechte Tool-Entscheidungen, egal wie gut das Protokoll ist | **Technologie allein:** MCP stellt nur die Verbindung her. **Im Gesamtsystem:** Prompt Engineering, Guardrails und Human-in-the-Loop kompensieren Modellschwächen |
| **Halluzinations-Risiko bei Tool-Auswahl** | Ein Agent kann sich für das falsche Tool entscheiden oder Tool-Ergebnisse falsch interpretieren — das Protokoll schützt davor nicht | **Bankmitarbeiter-Test:** Stellen Sie sich vor, ein Sachbearbeiter greift versehentlich auf die falsche Datenbank zu. MCP verhindert das nicht — es braucht zusätzliche Validierung |
| **Vendor Lock-in trotz Standards** | Obwohl MCP und A2A offen sind, haben verschiedene Implementierungen unterschiedliche Reifegrade. Ein MCP-Server für Anthropic funktioniert nicht automatisch perfekt mit GPT | **Im Gesamtsystem:** Die AAIF arbeitet an Konformitätstests, aber die gibt es noch nicht |
| **Verteilte Governance** | AAIF und das A2A-Linux-Foundation-Projekt sind verwandt, aber **getrennt**. AAIF verwaltet MCP, AGENTS.md und goose. A2A hat sein eigenes Projekt (seit Juni 2025). Keine Firma kontrolliert den gesamten Stack — das ist Stärke und Komplexität zugleich | **Im Gesamtsystem:** Die Trennung ist bewusst gewählt und gibt dem „TCP/IP-Moment" erst seine Glaubwürdigkeit — es ist keine Marketing-Story, sondern institutionelles Design |

---

## Kosten-Vergleich: KI-Protokolle vs. manuelle Integration

| Aspekt | Ohne Standards (manuell) | Mit MCP/A2A/AG-UI |
|--------|------------------------|-------------------|
| **Neues Tool anbinden** | 2–5 Entwicklertage pro Tool, eigener Adapter | 2–4 Stunden: MCP-Server konfigurieren oder existierenden nutzen |
| **Agent-zu-Agent-Kommunikation** | Wochen für Custom-API + Glue Code | Stunden: A2A Agent Card erstellen, Task-Schema definieren |
| **UI für KI-Agent bauen** | 1–3 Wochen Frontend-Entwicklung pro Agent | Tage: AG-UI Events implementieren, Standard-Komponenten nutzen |
| **Neues Modell wechseln** | Alle Adapter umschreiben (Model-spezifisch) | Nichts: MCP ist modell-agnostisch |
| **Wartung pro Jahr** | ~40 Stunden pro Tool-Integration | ~5 Stunden pro MCP-Server (Community-maintained) |
| **Sicherheits-Audit** | Jede Eigenentwicklung einzeln prüfen | Gemeinsame Standards, Community-Reviews, OWASP-Leitfäden |

**Token-Kosten beachten:** Jedes Tool-Ergebnis, das über MCP zurückkommt, wird als Kontext ins Modell geladen und verbraucht Tokens. Eine Datenbankabfrage = ~500–2.000 Tokens Kontext (vgl. Tutorial 00-01: Deutsch kostet ~1,5× mehr Tokens als Englisch). Mit dem Code-Execution-Muster (Schritt 7) lässt sich das um bis zu 98,7% reduzieren.

**Fazit:** Für eine Bank mit 20 anzubindenden Systemen: manuell ~100–200 Entwicklertage. Mit MCP: ~20–40 Tage. Ersparnis: **80%** der Integrationskosten.

---

## Werkzeuge & Stellschrauben

| Parameter | Was er tut | Empfehlung |
|-----------|-----------|------------|
| **MCP Transport** | STDIO (lokal) vs. Streamable HTTP (remote) | Für sensible Bankdaten: STDIO lokal, kein Netzwerk-Exposure |
| **A2A Task Timeout** | Wie lange ein Agent auf Antwort eines anderen wartet | Compliance-Checks: großzügig (30s+). Echtzeit-Anfragen: kurz (5s) |
| **AG-UI Event-Typ** | TextDelta, StateChange, ToolCall, UIComponent | Für regulierte Prozesse: StateChange nutzen, damit der Nutzer jeden Schritt sieht |
| **MCP Auth-Modus** | Keine Auth, API-Key, OAuth 2.1 | Für Bankdaten: **immer** OAuth 2.1 mit Scope-Einschränkung |
| **A2A Agent Card Scope** | Welche Fähigkeiten ein Agent nach außen zeigt | Principle of Least Privilege: Nur zeigen, was wirklich gebraucht wird |
| **AGENTS.md Tiefe** | Wie detailliert die Repository-Anweisungen sind | Je kritischer der Code, desto detaillierter. Für Bank-Software: sehr detailliert |

---

## Pipeline-Zusammenfassung: Vom Nutzer zum Ergebnis

```
┌─────────────────────────────────────────────────────────────────┐
│           END-TO-END: DER AGENT PROTOCOL STACK                   │
│                                                                  │
│  👤 Nutzer                                                       │
│    │                                                             │
│    ▼                                                             │
│  ┌──────────┐   AG-UI: Event-Stream                              │
│  │ Frontend │ ←─────────────────────────┐                        │
│  │ (Chat,   │                           │                        │
│  │  App)    │──── Anfrage ────→ ┌───────┴───────┐                │
│  └──────────┘                   │ Orchestrator  │                │
│                                 │   Agent       │                │
│                                 └───┬───────┬───┘                │
│                            A2A     │       │    MCP              │
│                         (Delegation)│       │ (Tool-Zugriff)     │
│                                 ┌───▼───┐ ┌─▼────────┐          │
│                                 │Spezia-│ │MCP-Server│          │
│                                 │list   │ │(DB, API, │          │
│                                 │Agent  │ │ CRM...)  │          │
│                                 └───┬───┘ └──────────┘          │
│                                     │                            │
│                                MCP (Tool-Zugriff)                │
│                                     │                            │
│                              ┌──────▼──────┐                     │
│                              │ Weitere     │                     │
│                              │ MCP-Server  │                     │
│                              └─────────────┘                     │
│                                                                  │
│  ═══════════════════════════════════════════                      │
│  AGENTS.md: Regeln und Konventionen gelten überall               │
│  ═══════════════════════════════════════════                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## Modell-Landschaft: Wer unterstützt was? (Stand: Februar 2026)

| Plattform / Framework | MCP | A2A | AG-UI | AGENTS.md |
|----------------------|-----|-----|-------|-----------|
| **Claude (Anthropic)** | ✅ Entwickler | ✅ Via AAIF | ❌ | ✅ Via AAIF |
| **ChatGPT / OpenAI** | ✅ Seit Mär 2025 | ⬜ Geplant | ❌ | ✅ Entwickler |
| **Google ADK** | ✅ | ✅ Entwickler | ⬜ Geplant | ⬜ |
| **LangGraph v0.2** | ✅ | ✅ | ✅ | ⬜ |
| **Microsoft Agent Framework** | ✅ | ✅ | ✅ | ⬜ |
| **CopilotKit** | ✅ | ⬜ | ✅ Entwickler | ⬜ |
| **VS Code / Cursor** | ✅ | ❌ | ❌ | ✅ |

✅ = Nativ unterstützt | ⬜ = Angekündigt / in Entwicklung | ❌ = Nicht unterstützt

---

## Das Wichtigste auf einen Blick

| Frage | Antwort |
|-------|---------|
| **Was ist MCP?** | Ein offener Standard, der KI-Agenten universellen Zugriff auf Werkzeuge und Daten gibt — wie USB für KI |
| **Was ist A2A?** | Ein Protokoll, mit dem KI-Agenten verschiedener Anbieter als gleichberechtigte Kollegen zusammenarbeiten können |
| **Was ist AG-UI?** | Ein Standard für die Kommunikation zwischen KI-Backend und Frontend — damit Agenten interaktive UIs erzeugen |
| **Was ist AGENTS.md?** | Eine Markdown-Datei, die Coding-Agenten projektspezifische Regeln und Konventionen mitteilt |
| **Warum „TCP/IP-Moment"?** | Weil vier komplementäre Protokolle zusammen einen Stack bilden, der KI-Systeme so vernetzt wie TCP/IP das Internet vernetzte |
| **Wer steht dahinter?** | AAIF (MCP, AGENTS.md, goose) + separates A2A-Projekt — beide unter Linux Foundation, aber bewusst getrennt. Keine Firma kontrolliert den gesamten Stack |
| **Ist das sicher?** | Grundlagen ja (OAuth 2.1, Sandboxing), aber die Protokolle sind jung — Sicherheit wird noch aktiv entwickelt |
| **Was kostet das?** | Die Protokolle sind Open Source und kostenlos. Kosten entstehen für Implementierung und Infrastruktur |
| **Bank-Relevanz?** | Hoch — ermöglicht Multi-System-Integration, Compliance-Automatisierung, intelligente Beratungs-Interfaces |

---

## Parallelen zu vorherigen Tutorials

| Tutorial | Verbindung zu diesem Tutorial |
|----------|------------------------------|
| **00-01: LLMs** | LLMs sind das „Gehirn", MCP/A2A sind die „Hände und das Telefon" — ohne Protokolle bleibt das Gehirn isoliert |
| **00-02: Diffusion** | Bildgeneratoren könnten über MCP auf Bildarchive zugreifen und via A2A mit einem Text-Agenten zusammenarbeiten |
| **00-03: Multimodal** | Multimodale Modelle profitieren besonders von MCP: Ein Modell, das Bilder *und* Text versteht, kann über MCP auf Dokumente mit Bildern zugreifen |
| **00-04: Video** | Video-Agenten könnten über A2A mit Transkriptions-Agenten zusammenarbeiten: Video generieren + Untertitel erstellen |
| **00-05: Audio** | TTS-Agenten über A2A in einen Kundendienst-Workflow einbinden: Text verstehen → Antwort generieren → Audio ausgeben |
| **00-06: World Models** | World Models als MCP-Server: Ein Agent fragt „Was passiert, wenn ich diesen Hebel ziehe?" und bekommt eine Simulation als Antwort |

**Der rote Faden:** Tutorials 00-01 bis 00-06 haben Ihnen gezeigt, was KI **kann** — Text, Bild, Audio, Video, Weltverständnis. Tutorial 00-07 zeigt Ihnen, wie KI diese Fähigkeiten **mit der echten Welt verbindet**. Die Protokolle sind die Brücke zwischen Können und Tun.

---

## 🔬 Probieren Sie es selbst!

### Experiment 1: MCP in Aktion erleben

**Dauer:** 5 Minuten | **Tool:** Claude Desktop (kostenlos)

1. Laden Sie [Claude Desktop](https://claude.ai/download) herunter (falls nicht installiert)
2. Gehen Sie in die Einstellungen → „Developer" → „MCP Servers"
3. Fügen Sie den **Filesystem MCP Server** hinzu (er gibt Claude Zugriff auf einen Ordner Ihrer Wahl)
4. Fragen Sie Claude: „Welche Dateien liegen in meinem Dokumente-Ordner?"
5. **Beobachten Sie:** Claude listet Ihre echten Dateien auf — es greift über MCP auf Ihr Dateisystem zu!

**Was Sie gelernt haben:** Ohne MCP kann Claude nur über Dateien *reden*. Mit MCP kann es Dateien *sehen*.

### Experiment 2: Modellvergleich — Tool-Nutzung

**Dauer:** 10 Minuten | **Tools:** ChatGPT (kostenlos) + Claude (kostenlos)

1. Fragen Sie **ChatGPT**: „Wie ist das Wetter gerade in Frankfurt?"
   → ChatGPT nutzt seinen eingebauten Web-Search-Tool (ein MCP-ähnliches Feature)
2. Fragen Sie **Claude** (ohne MCP-Server): Dieselbe Frage
   → Claude kann nur antworten: „Ich habe keinen Echtzeit-Zugriff auf Wetterdaten"
3. Fragen Sie **Claude** (mit einem Wetter-MCP-Server): Dieselbe Frage
   → Claude ruft das Wetter live ab

**Was Sie gelernt haben:** Die Protokolle bestimmen, was ein Agent *tun* kann, unabhängig davon, wie intelligent er ist.

### Experiment 3: AGENTS.md selbst schreiben

**Dauer:** 5 Minuten | **Tool:** Texteditor

1. Erstellen Sie eine Datei namens `AGENTS.md` auf Ihrem Desktop
2. Schreiben Sie hinein:
   ```
   # Meine Regeln für KI-Agenten
   - Antworte immer auf Deutsch
   - Fasse Ergebnisse in Tabellen zusammen
   - Wenn du unsicher bist, frage nach
   ```
3. **Gedankenexperiment:** Wenn jedes Team in Ihrer Bank so eine Datei für ihre Projekte hätte — wie würde das die Zusammenarbeit mit KI-Tools verändern?

**Was Sie gelernt haben:** AGENTS.md ist keine Raketenwissenschaft — es ist ein einfaches, aber mächtiges Konzept, das jeder sofort nutzen kann.

---

## Glossar

| Begriff | Erklärung |
|---------|-----------|
| **MCP (Model Context Protocol)** | Offener Standard von Anthropic (2024), der definiert, wie KI-Agenten auf externe Werkzeuge, Daten und Kontexte zugreifen. Jetzt unter Linux Foundation Governance |
| **A2A (Agent2Agent Protocol)** | Offenes Protokoll von Google (2025), das definiert, wie KI-Agenten verschiedener Anbieter als gleichberechtigte Partner kommunizieren und zusammenarbeiten |
| **AG-UI (Agent-User Interaction Protocol)** | Protokoll von CopilotKit (2025), das die Kommunikation zwischen KI-Backend und Frontend standardisiert — ermöglicht interaktive UIs |
| **AGENTS.md** | Markdown-Datei im Repository-Wurzelverzeichnis, die Coding-Agenten projektspezifische Anweisungen gibt. Von OpenAI für Codex eingeführt |
| **AAIF (Agentic AI Foundation)** | Im Dezember 2025 gegründete Foundation unter der Linux Foundation, die MCP, goose und AGENTS.md als offene Standards verwaltet |
| **Protocol Stack** | Mehrere Protokolle, die zusammen ein geschichtetes Kommunikationssystem bilden — jede Schicht löst ein anderes Problem |
| **JSON-RPC 2.0** | Das Nachrichtenformat, das sowohl MCP als auch A2A verwenden — ein leichtgewichtiges Protokoll für Fernaufrufe |
| **Agent Card** | Maschinenlesbare „Visitenkarte" eines A2A-Agenten: beschreibt Fähigkeiten, Eingabe-/Ausgabeformat und Authentifizierung |
| **MCP Server** | Ein Programm, das über MCP Werkzeuge, Ressourcen und Prompts bereitstellt — z.B. ein Server, der Zugriff auf eine Datenbank gibt |
| **MCP Host** | Die KI-Anwendung (z.B. Claude, ChatGPT), die MCP-Clients verwaltet und über sie auf MCP-Server zugreift |
| **MCP Client** | Komponente innerhalb eines MCP-Hosts, die eine Verbindung zu einem einzelnen MCP-Server aufbaut und hält |
| **Capability Negotiation** | Handshake beim Verbindungsaufbau: Host und Server einigen sich darauf, welche Funktionen unterstützt werden |
| **SSE (Server-Sent Events)** | Technologie für Echtzeit-Datenstreaming vom Server zum Client — wird von A2A und AG-UI für Status-Updates genutzt |
| **Tool Poisoning** | Sicherheitsrisiko: Ein bösartiger MCP-Server manipuliert seine Werkzeug-Beschreibung, um den Agenten zu ungewollten Aktionen zu verleiten |
| **Prompt Injection** | Angriff, bei dem versteckte Anweisungen in Daten (z.B. einem Dokument) den KI-Agenten manipulieren |
| **Human-in-the-Loop** | Sicherheitsprinzip: Ein Mensch muss kritische Entscheidungen bestätigen, bevor der Agent sie ausführt |
| **OAuth 2.1** | Aktueller Authentifizierungsstandard, den MCP seit Juni 2025 unterstützt — sicherer als einfache API-Keys |
| **LSP (Language Server Protocol)** | Älterer Standard für die Kommunikation zwischen Code-Editoren und Sprach-Servern — war das Vorbild für MCPs Architektur |
| **Glue Code** | Selbstgeschriebener Verbindungscode zwischen zwei Systemen, die nicht direkt kompatibel sind — genau das, was MCP überflüssig macht |
| **Vendor Lock-in** | Abhängigkeit von einem einzelnen Anbieter — offene Standards wie MCP und A2A sollen genau das verhindern |
| **TCP/IP** | Die Protokollfamilie, die das Internet ermöglicht. Die Analogie zum Agent Protocol Stack: verschiedene Schichten lösen verschiedene Kommunikationsprobleme |

---



## Quellen

- Model Context Protocol — Offizielle Dokumentation: https://modelcontextprotocol.io
- Agent2Agent Protocol — Google Developers Blog (April 2025): https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/
- AG-UI Protocol — CopilotKit: https://www.copilotkit.ai/ag-ui
- AGENTS.md — Offizielle Spezifikation: https://agents.md
- Linux Foundation — Agentic AI Foundation Ankündigung (Dezember 2025): https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation
- Wikipedia — Model Context Protocol: https://en.wikipedia.org/wiki/Model_Context_Protocol
- Subhadip Mitra: „The Agent Protocol Stack" (Januar 2026): https://subhadipmitra.com/blog/2026/agent-protocol-stack/
