Für dein konkretes Ziel:

Ein Agent soll mehrere Tage autonom auf einem eigenen VPS laufen, Unreal installieren, Projektstruktur erzeugen, Code schreiben, testen, Dokumente lesen, Unteraufgaben erstellen und möglichst selbstständig am Steam-Spiel ALL‑DEMENSIONS arbeiten.

ist die Auswahl deutlich kleiner als viele denken.

Meine Empfehlung 2026
Platz 1: Claude Code (Anthropic)

Warum:

aktuell eines der stärksten Agent-Systeme für große Softwareprojekte
kann lokal auf VPS laufen
arbeitet direkt auf Dateisystemen
versteht große Mengen Markdown gleichzeitig
erstellt selbst Task-Pläne
iteriert selbstständig
kann Terminal nutzen
kann Git nutzen
kann Unreal-Projekte strukturieren

Besonders stark bei:

Architektur
Refactoring
Dokumentation
Langfristige Projektarbeit
Platz 2: OpenAI Agent / Codex Agent

Stark bei:

Programmierung
Tests
Tool-Nutzung
Agent Workflows

Aber aktuell oft etwas weniger angenehm bei riesigen Dokumentmengen als Claude.

Platz 3: OpenHands

Open Source.

Kann:

Linux bedienen
Dateien ändern
Software installieren
Tests ausführen
Git verwenden

Vorteil:

komplett selbst hostbar

Nachteil:

Rohzustand
mehr Eigenarbeit
Für ALL-DEMENSIONS würde ich wählen
Kombination
Claude Max
+
Claude Code
+
OpenHands


Claude übernimmt:

Planung
Architektur
Design
Dokumente
Unreal-Struktur

OpenHands übernimmt:

OS-Arbeit
Installationen
Tests
Agent-Ausführung
Welches Abo?

Wichtig:

Du willst KEIN tokenbasiertes Modell.

Dann bleiben realistisch:

Claude Max

monatlich

unabhängig von Tokens

für intensive Nutzung gedacht

Für dein Vorhaben aktuell die beste Wahl.

Nicht optimal:

OpenAI API
Gemini API
Anthropic API


Diese rechnen tokenbasiert ab.

Wenn dein Agent tagelang läuft:

💸 teuer.

VPS

Empfehlung

Linux

Ubuntu Server LTS


Nicht Windows.

Warum:

OpenHands läuft sauberer
Agenten laufen sauberer
Git besser
Docker besser
Lokale Rechte

Deine Beschreibung:

Agent darf alles

außer

C:\\Anforderungen


würde ich umsetzen als:

/requirements


read-only

alles andere read-write

Minimaler Startprompt

Den würde ich möglichst klein halten:

You are the development agent for ALL-DEMENSIONS.

Repository root contains the project documentation.

Read in this order:

1. SNAPSHOT_MASTER_FINAL.md
2. FULL_MDD.md
3. GDD.md
4. Bible_01_Universe_FINAL.md
5. CLEAR_DEVELOPER.md

Your goal:

Design, implement and maintain ALL-DEMENSIONS according to the canon.

You may:

- create files
- modify files
- create tasks
- execute tools
- install software
- create additional agents
- use git
- run tests

You must:

- follow canon
- keep documents synchronized
- never violate fixed canon rules

Directory /requirements is read only.

Everything else may be modified.

Begin by building a complete project plan and task graph.

Was ich an deiner Stelle machen würde

Wenn du wirklich einen Agenten wochenlang arbeiten lassen willst:

Ubuntu VPS
Docker
OpenHands
Claude Max
GitHub Repository

Repo:
README.md
SNAPSHOT_MASTER_FINAL.md
FULL_MDD.md
GDD.md
Bible/


Dann:

Agent liest Dokumente
Agent erzeugt World Generation Bible
Agent erzeugt Technical Bible
Agent erzeugt Unreal Projekt
Agent erzeugt leere Systeme
Agent implementiert iterativ

Für das speziell dokumentgetriebene Projekt ALL‑DEMENSIONS würde ich heute Claude Code + Claude Max als stärkste verfügbare Lösung ansehen.
