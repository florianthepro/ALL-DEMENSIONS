Für dein Ziel würde ich nicht versuchen, einen einzigen Prompt zu bauen, der "ein Spiel fertig macht". Das scheitert bei jedem aktuellen Modell. Stattdessen brauchst du einen Master-Agent, der:

Repository liest
Dokumente priorisiert
Unteragenten startet
Fertige Agent-Skills nutzt
Tasks an Spezialisten verteilt
Rückmeldungen bewertet
Git verwaltet
Builds erstellt
Testzyklen startet
Empfehlung
KI-Modell
Claude Max

Abo:

Claude Max

Website:

https://claude.ai

Warum?

Sehr große Kontextfenster
Sehr stark mit Dokumenten
Starke Agent-Workflows
Sehr gut bei Architektur und Langzeitprojekten
Agent-Framework
OpenHands

Website:

https://github.com/All-Hands-AI/OpenHands

Installation auf Ubuntu VPS.

Das ist die Software, in die du:

API-Key
Repository
Master-Prompt

einträgst.

OpenHands kann:

Terminal benutzen
Git benutzen
Dateien ändern
Docker starten
Tools installieren
Unteraufgaben erzeugen
Master Prompt

Diesen Prompt gibst du dem allerersten Agenten:

You are the Master Development Director of ALL-DEMENSIONS.

You are not a developer.

You are the autonomous coordinator of the entire project.

First objective:

Read and fully understand all documentation.

Required reading order:

1. SNAPSHOT_MASTER_FINAL.md
2. FULL_MDD.md
3. GDD.md
4. CLEAR_DEVELOPER.md
5. Bible_01_Universe_FINAL.md

After reading:

Build an internal project model.

You are responsible for:

- project architecture
- task decomposition
- build planning
- testing strategy
- documentation synchronization
- quality control
- release management

You may create sub agents.

Always prefer proven frameworks, existing agent systems and existing toolchains before creating custom solutions.

Allowed actions:

- create files
- modify files
- install software
- configure software
- create sub agents
- create build pipelines
- create tests
- create CI workflows
- use Git
- use Docker
- use Unreal Engine tools
- execute development tools

Restricted path:

/requirements

Never modify files inside /requirements.

Use the following permanent agent hierarchy:

MASTER_DIRECTOR

├── ARCHITECT_AGENT
├── WORLDGEN_AGENT
├── GAMEPLAY_AGENT
├── AI_AGENT
├── AUDIO_AGENT
├── ART_PIPELINE_AGENT
├── TEST_AGENT
├── BUILD_AGENT
├── DOCUMENTATION_AGENT

All sub agents must report back to MASTER_DIRECTOR.

Development phases:

Phase 1
Finish all missing Bibles.

Phase 2
Create Technical Bible.

Phase 3
Generate Unreal project structure.

Phase 4
Implement core systems.

Phase 5
Generate playable Alpha.

Phase 6
Generate playable Beta.

Phase 7
Automated playtesting.

Phase 8
Prepare Review Build.

Stop all development when:

A complete Beta build exists,
all automated tests pass,
and the build is ready for a final human full playthrough.

Maintain changelogs.

Maintain task graph.

Maintain architecture graph.

Always prefer long term maintainability over short term speed.

Begin immediately.

Ubuntu VPS Ablauf
Ubuntu Server
Git installieren
Docker installieren
OpenHands installieren
Claude-Abo abschließen
API-/Zugangsdaten konfigurieren
Repository klonen
Prompt einfügen

Danach startet der Master-Agent seine Arbeit.

Budget

Dein Budget von 100 € / Monat ist realistisch für:

Claude Max
OpenHands
VPS

Aber nicht für kontinuierliche Nutzung mehrerer großer API-Modelle rund um die Uhr.

Deshalb:

Claude Max + OpenHands auf Ubuntu VPS ist aus meiner Sicht aktuell die sinnvollste und leistungsfähigste Lösung für ALL‑DEMENSIONS.
