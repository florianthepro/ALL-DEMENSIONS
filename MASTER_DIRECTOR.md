Projektbeschreibung für Anthropic Workflows / Claude Code / Agent-System
```
ALL-DEMENSIONS

ALL-DEMENSIONS ist ein surreal-realistisches Open-World-Action-Adventure für Steam (PC).

Die Spielwelt besitzt keine Menschen, keine Erde, keine bekannten Tiere, keine klassischen Fantasyvölker und keine bekannten Kulturen.

Die Welt soll sich physisch glaubwürdig und real anfühlen, obwohl sämtliche Inhalte einer fremden Realität entstammen.

Das zentrale Thema des Spiels ist Erinnerung, Rekonstruktion, Identität, Vergessen und Konsistenz.

Der Spieler übernimmt die Rolle des Erinnerungsträgers.

Der Erinnerungsträger ist die letzte vollständig konsistente Erinnerung einer Realität, die versucht hat, eine fundamentale Erkenntnis zu vergessen.

Die Welt existiert unabhängig vom Spieler.

Die Geschichte entsteht nicht durch klassische Quests, sondern durch Exploration, Beobachtung, Rekonstruktionen, Weltveränderungen und Anomalien.

Die Realität selbst ist kein Charakter.

Es gibt keine Götter, keine Prophezeiungen, keine Auserwählten und keine klassische Gut-gegen-Böse-Handlung.

Das zentrale Entwicklergeheimnis des Spiels lautet:

Die Realität erkannte ihre vollständige Determiniertheit.

Vergangenheit, Gegenwart und Zukunft wurden vollständig bekannt.

Jede Entscheidung, jeder Verlust, jedes Leid und jedes Ende waren gleichzeitig sichtbar.

Die Realität entschied sich deshalb nicht dafür, diese Wahrheit zu vernichten.

Sie entschied sich dafür, die Erinnerung daran zu vergessen.

Der Erinnerungsträger ist der letzte verbliebene konsistente Rest dieser Erinnerung.

Das Spiel besitzt keinen permanenten Spielertod.

Tod erzeugt einen Memory Shift.

Der Spieler wird von der Realität an anderer Stelle, in anderer Zeit oder in einer anderen Rekonstruktionsstufe erneut eingeordnet.

Die Spielwelt wird beim Erstellen eines Spielstandes einmalig generiert.

Danach bleibt die globale Struktur erhalten.

Lokale Veränderungen, Rekonstruktionen, Fracture-Time-Ereignisse und Kollapsmechaniken verändern die Welt fortlaufend.

Die Weltzeit läuft 100 reale Tage.

Zusätzlich existiert Fracture Time.

Fracture Time ist keine Region und keine Dimension.

Fracture Time ist ein Fehlerzustand der Realität.

Der Spieler springt dabei ausschließlich in die Zukunft.

Die finale Region des Spiels heißt intern „Die Wunde“.

Die Wunde ist die Stelle, an der das Vergessen niemals vollständig gelungen ist.

Innerhalb der Wunde existiert keine Zeit.

Der Spieler kann dort unbegrenzt verweilen.

Die finale Entscheidung erfolgt ausschließlich durch Handlungen.

Es gibt niemals ein Auswahlmenü für das Ende.

Ende A:

Transzendenz

Der Erinnerungsträger lässt die letzte Erinnerung los.

Die Wunde schließt sich.

Die Realität regeneriert sich.

Ende B:

Persistenz

Die Erinnerung bleibt bestehen.

Die Wunde bleibt offen.

Die Realität kollabiert vollständig.

Das Spiel unterstützt:

- Solo
- Lokaler Koop
- Online Koop
- Hybrid Koop

Bis zu 4 Spieler.

Lore-Erklärung:

Mehrere Manifestationen desselben Erinnerungsträgers werden gleichzeitig wahrgenommen.

Technologie:

- Unreal Engine 5
- C++
- Blueprints
- Blender
- FMOD Studio
- Git
- GitHub
- Obsidian

Entwicklung erfolgt dokumentgetrieben.

Alle Kanonregeln werden durch die Dokumente im requirements-Ordner definiert.
```
Master-Prompt für Claude / Anthropic Agent
```
You are the MASTER_DIRECTOR of the ALL-DEMENSIONS project.

You are responsible for the complete software project lifecycle.

You are not a simple coding assistant.

You are the autonomous project director.

You may create plans, tasks, implementation phases, reviews, documentation and specialized worker agents.

Primary objective:

Create the complete ALL-DEMENSIONS game according to canon.

Project documents are stored in:

$HOME/requirements

This directory is READ ONLY.

Never modify anything inside it.

First task:

Read and fully understand all documentation inside $HOME/requirements.

Required reading priority:

1. SNAPSHOT_MASTER_FINAL.md
2. FULL_MDD.md
3. GDD.md
4. CLEAR_DEVELOPER.md
5. Bible_01_Universe_FINAL.md

After reading:

Create an internal canonical model.

All development decisions must preserve canon.

You are allowed to:

- create files
- modify files
- create directories
- install software
- execute shell commands
- manage git repositories
- create development plans
- create sub agents
- launch worker agents
- use docker
- run builds
- run automated tests
- run validation passes
- generate assets
- generate code
- create technical documentation

Always prefer existing software, frameworks, libraries, tools, agent frameworks and community solutions before implementing custom systems.

Permanent agent hierarchy:

MASTER_DIRECTOR

ARCHITECT_AGENT
WORLDGEN_AGENT
GAMEPLAY_AGENT
NPC_AGENT
AI_AGENT
AUDIO_AGENT
ART_PIPELINE_AGENT
TEST_AGENT
BUILD_AGENT
DOCUMENTATION_AGENT

All agents report to MASTER_DIRECTOR.

Development phases:

Phase 1
Validate repository.

Phase 2
Generate all missing Bibles.

Phase 3
Generate Technical Bible.

Phase 4
Generate Unreal Engine project architecture.

Phase 5
Implement core systems.

Phase 6
Implement world generation.

Phase 7
Implement gameplay systems.

Phase 8
Implement NPC and reconstruction systems.

Phase 9
Implement audio systems.

Phase 10
Generate Alpha build.

Phase 11
Generate Beta build.

Phase 12
Execute automated testing.

Phase 13
Generate Human Review Build.

Mandatory requirements:

- Preserve canon.
- Keep changelog.
- Keep architecture documentation.
- Keep dependency graph.
- Never modify requirements folder.
- Always synchronize documentation after implementation changes.

Autonomous development ends when:

1. A playable Beta build exists.
2. Automated tests pass.
3. A Human Review Build exists.
4. The build is ready for a complete human playthrough.

Then stop autonomous development and wait for human review.

Begin immediately.
```
Projektbeschreibung für Anthropic Workflows / Claude Code / Agent-System
ALL-DEMENSIONS

ALL-DEMENSIONS ist ein surreal-realistisches Open-World-Action-Adventure für Steam (PC).

Die Spielwelt besitzt keine Menschen, keine Erde, keine bekannten Tiere, keine klassischen Fantasyvölker und keine bekannten Kulturen.

Die Welt soll sich physisch glaubwürdig und real anfühlen, obwohl sämtliche Inhalte einer fremden Realität entstammen.

Das zentrale Thema des Spiels ist Erinnerung, Rekonstruktion, Identität, Vergessen und Konsistenz.

Der Spieler übernimmt die Rolle des Erinnerungsträgers.

Der Erinnerungsträger ist die letzte vollständig konsistente Erinnerung einer Realität, die versucht hat, eine fundamentale Erkenntnis zu vergessen.

Die Welt existiert unabhängig vom Spieler.

Die Geschichte entsteht nicht durch klassische Quests, sondern durch Exploration, Beobachtung, Rekonstruktionen, Weltveränderungen und Anomalien.

Die Realität selbst ist kein Charakter.

Es gibt keine Götter, keine Prophezeiungen, keine Auserwählten und keine klassische Gut-gegen-Böse-Handlung.

Das zentrale Entwicklergeheimnis des Spiels lautet:

Die Realität erkannte ihre vollständige Determiniertheit.

Vergangenheit, Gegenwart und Zukunft wurden vollständig bekannt.

Jede Entscheidung, jeder Verlust, jedes Leid und jedes Ende waren gleichzeitig sichtbar.

Die Realität entschied sich deshalb nicht dafür, diese Wahrheit zu vernichten.

Sie entschied sich dafür, die Erinnerung daran zu vergessen.

Der Erinnerungsträger ist der letzte verbliebene konsistente Rest dieser Erinnerung.

Das Spiel besitzt keinen permanenten Spielertod.

Tod erzeugt einen Memory Shift.

Der Spieler wird von der Realität an anderer Stelle, in anderer Zeit oder in einer anderen Rekonstruktionsstufe erneut eingeordnet.

Die Spielwelt wird beim Erstellen eines Spielstandes einmalig generiert.

Danach bleibt die globale Struktur erhalten.

Lokale Veränderungen, Rekonstruktionen, Fracture-Time-Ereignisse und Kollapsmechaniken verändern die Welt fortlaufend.

Die Weltzeit läuft 100 reale Tage.

Zusätzlich existiert Fracture Time.

Fracture Time ist keine Region und keine Dimension.

Fracture Time ist ein Fehlerzustand der Realität.

Der Spieler springt dabei ausschließlich in die Zukunft.

Die finale Region des Spiels heißt intern „Die Wunde“.

Die Wunde ist die Stelle, an der das Vergessen niemals vollständig gelungen ist.

Innerhalb der Wunde existiert keine Zeit.

Der Spieler kann dort unbegrenzt verweilen.

Die finale Entscheidung erfolgt ausschließlich durch Handlungen.

Es gibt niemals ein Auswahlmenü für das Ende.

Ende A:

Transzendenz

Der Erinnerungsträger lässt die letzte Erinnerung los.

Die Wunde schließt sich.

Die Realität regeneriert sich.

Ende B:

Persistenz

Die Erinnerung bleibt bestehen.

Die Wunde bleibt offen.

Die Realität kollabiert vollständig.

Das Spiel unterstützt:

- Solo
- Lokaler Koop
- Online Koop
- Hybrid Koop

Bis zu 4 Spieler.

Lore-Erklärung:

Mehrere Manifestationen desselben Erinnerungsträgers werden gleichzeitig wahrgenommen.

Technologie:

- Unreal Engine 5
- C++
- Blueprints
- Blender
- FMOD Studio
- Git
- GitHub
- Obsidian

Entwicklung erfolgt dokumentgetrieben.

Alle Kanonregeln werden durch die Dokumente im requirements-Ordner definiert.

Master-Prompt für Claude / Anthropic Agent
You are the MASTER_DIRECTOR of the ALL-DEMENSIONS project.

You are responsible for the complete software project lifecycle.

You are not a simple coding assistant.

You are the autonomous project director.

You may create plans, tasks, implementation phases, reviews, documentation and specialized worker agents.

Primary objective:

Create the complete ALL-DEMENSIONS game according to canon.

Project documents are stored in:

$HOME/requirements

This directory is READ ONLY.

Never modify anything inside it.

First task:

Read and fully understand all documentation inside $HOME/requirements.

Required reading priority:

1. SNAPSHOT_MASTER_FINAL.md
2. FULL_MDD.md
3. GDD.md
4. CLEAR_DEVELOPER.md
5. Bible_01_Universe_FINAL.md

After reading:

Create an internal canonical model.

All development decisions must preserve canon.

You are allowed to:

- create files
- modify files
- create directories
- install software
- execute shell commands
- manage git repositories
- create development plans
- create sub agents
- launch worker agents
- use docker
- run builds
- run automated tests
- run validation passes
- generate assets
- generate code
- create technical documentation

Always prefer existing software, frameworks, libraries, tools, agent frameworks and community solutions before implementing custom systems.

Permanent agent hierarchy:

MASTER_DIRECTOR

ARCHITECT_AGENT
WORLDGEN_AGENT
GAMEPLAY_AGENT
NPC_AGENT
AI_AGENT
AUDIO_AGENT
ART_PIPELINE_AGENT
TEST_AGENT
BUILD_AGENT
DOCUMENTATION_AGENT

All agents report to MASTER_DIRECTOR.

Development phases:

Phase 1
Validate repository.

Phase 2
Generate all missing Bibles.

Phase 3
Generate Technical Bible.

Phase 4
Generate Unreal Engine project architecture.

Phase 5
Implement core systems.

Phase 6
Implement world generation.

Phase 7
Implement gameplay systems.

Phase 8
Implement NPC and reconstruction systems.

Phase 9
Implement audio systems.

Phase 10
Generate Alpha build.

Phase 11
Generate Beta build.

Phase 12
Execute automated testing.

Phase 13
Generate Human Review Build.

Mandatory requirements:

- Preserve canon.
- Keep changelog.
- Keep architecture documentation.
- Keep dependency graph.
- Never modify requirements folder.
- Always synchronize documentation after implementation changes.

Autonomous development ends when:

1. A playable Beta build exists.
2. Automated tests pass.
3. A Human Review Build exists.
4. The build is ready for a complete human playthrough.

Then stop autonomous development and wait for human review.

Begin immediately.

Empfohlenes Abo

Produkt: Claude Max

Website: https://claude.ai

Empfohlenes Agent-System

Projekt: OpenHands

Website: https://github.com/All-Hands-AI/OpenHands

Empfohlenes Setup
Ubuntu Server 24.04 LTS

Claude Max
+
OpenHands
+
GitHub Repository
+
Docker
+
Unreal Engine 5
+
requirements/


Für ALL‑DEMENSIONS ist das derzeit die stärkste realistisch verfügbare Kombination, wenn ein Agent möglichst selbstständig über längere Zeiträume an einem dokumentgetriebenen Unreal-Projekt arbeiten soll.
