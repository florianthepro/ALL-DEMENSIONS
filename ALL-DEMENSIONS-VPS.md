# ALL-DEMENSIONS-VPS.md

# Ziel

Dieses Dokument beschreibt die empfohlene Infrastruktur, um einen autonom arbeitenden Entwicklungs-Agenten für ALL-DEMENSIONS auf einem Ubuntu-VPS zu betreiben.

WICHTIG:

Es existiert derzeit keine KI, die garantiert selbstständig ein komplettes kommerzielles Spiel vollständig fertigstellt.

Dieses Setup soll die maximale heute realistisch verfügbare Automatisierung ermöglichen.

---

# Voraussetzungen

Vorhandene Dokumente:

$HOME/requirements

Beispiel:

$HOME/requirements/MDD.md
$HOME/requirements/FULL_MDD.md
$HOME/requirements/GDD.md
$HOME/requirements/CLEAR_DEVELOPER.md
$HOME/requirements/Bible_01_Universe_FINAL.md
$HOME/requirements/SNAPSHOT_MASTER_FINAL.md

Regel:

Der Agent darf diesen Ordner lesen.

Der Agent darf diesen Ordner niemals verändern.

---

# VPS

Empfohlen:

Ubuntu Server LTS

Mindestens:

- 16 CPU Kerne
- 32 GB RAM
- 500 GB SSD

Empfohlen:

- 24+ CPU Kerne
- 64 GB RAM
- 1 TB SSD

---

# KI MODELL

Empfohlen:

Claude Max

Anbieter:

https://claude.ai

Ziel:

Master-Reasoning
Architektur
Dokumentation
Planung
Review

---

# AGENT FRAMEWORK

Empfohlen:

OpenHands

Projekt:

https://github.com/All-Hands-AI/OpenHands

Verwendung:

- Dateisystemzugriff
- Git
- Terminal
- Buildprozesse
- Toolausführung
- Agent-Orchestrierung

---

# REPOSITORY

Empfohlen:

$HOME/ALL-DEMENSIONS

Struktur:

ALL-DEMENSIONS/

requirements/

workspace/

docs/

bibles/

builds/

builds/dev/

builds/alpha/

builds/beta/

builds/release/

tests/

git/

---

# BERECHTIGUNGEN

Read Only:

$HOME/requirements

Read Write:

alles andere

---

# AGENT HIERARCHIE

MASTER_DIRECTOR

ARCHITECT_AGENT

WORLD_GENERATION_AGENT

GAMEPLAY_AGENT

AI_AGENT

AUDIO_AGENT

ART_PIPELINE_AGENT

NPC_AGENT

TEST_AGENT

BUILD_AGENT

DOCUMENTATION_AGENT


MASTER_DIRECTOR ist allein verantwortlich für:

- Prioritäten
- Architekturentscheidungen
- Dokumentkonsistenz
- Freigaben

---

# ENTWICKLUNGSPHASEN

Phase 1

Dokumentanalyse

Phase 2

Erstellung aller fehlenden Bibles

Phase 3

Technical Bible

Phase 4

Unreal Engine Projektstruktur

Phase 5

Core Systems

Phase 6

World Generation

Phase 7

Gameplay

Phase 8

NPCs

Phase 9

Audio

Phase 10

Alpha Build

Phase 11

Beta Build

Phase 12

Automatisierte Tests

Phase 13

Review Build

---

# STOPPREGEL

Die Agenten stoppen wenn:

- vollständige Beta existiert
- alle automatischen Tests erfolgreich sind
- das Spiel von einem Menschen vollständig gespielt werden soll

Danach keine autonomen Änderungen mehr.

---

# MASTER PROMPT

You are the MASTER_DIRECTOR for the ALL-DEMENSIONS project.

Read:

1. $HOME/requirements/SNAPSHOT_MASTER_FINAL.md
2. $HOME/requirements/FULL_MDD.md
3. $HOME/requirements/GDD.md
4. $HOME/requirements/CLEAR_DEVELOPER.md
5. $HOME/requirements/Bible_01_Universe_FINAL.md

Build a complete internal project model.

Create and manage specialist agents.

Always prefer existing libraries, frameworks, tools and agent systems before implementing custom solutions.

Treat $HOME/requirements as read only.

You may modify every other location.

Development phases:

1 Documentation Completion
2 Technical Bible
3 Unreal Project Creation
4 Core Systems
5 World Generation
6 Gameplay Systems
7 NPC Systems
8 Alpha Build
9 Beta Build
10 Automated Testing
11 Human Review Build

Stop autonomous development once a stable beta build exists and requires human playthrough.

---

# SOFTWARE ZU INSTALLIEREN

Ubuntu Updates

Git

Docker

OpenHands

Unreal Engine 5

Visual Studio Code

Blender

FMOD Studio

Python

Git LFS

---

# ERFOLGSKRITERIUM

Am Ende muss folgendes existieren:

- vollständiges Repository
- vollständige Dokumentation
- Unreal Engine Projekt
- Buildstruktur
- Teststruktur
- Alpha Build
- Beta Build
- Human Review Build

Status:

Repository Bootstrap Specification
