# ALL-DEMENSIONS
# Bible_01_Universe_FINAL.md
## Final Developer Universe Specification
## Status: LOCKED CANON

# 1. PURPOSE

Dieses Dokument definiert die universellen Regeln, Datentypen, Zustände und Abhängigkeiten der Realität.

Alle Systeme des Spiels müssen mit dieser Bible kompatibel sein.

Untergeordnete Dokumente:
- World Generation Bible
- Region Bible
- Creature Bible
- NPC Bible
- Narrative Bible
- Gameplay Bible
- Physics Bible
- Audio Bible
- Art Bible
- Technical Bible
- Production Bible

---
# 2. UNIVERSE AXIOMS

AXIOM_01
RealityExistsWithoutPlayer = true

AXIOM_02
UniverseIsNotCharacter = true

AXIOM_03
MemoriesAffectReality = true

AXIOM_04
ConsistencyIsQuantifiable = true

AXIOM_05
LostInformationMayReconstruct = true

AXIOM_06
PlayerCannotPermanentlyDie = true

AXIOM_07
TheWoundExists = true

AXIOM_08
TheMemoryExists = true

---
# 3. CANON CONSTANTS

Diese Elemente müssen in jedem Spielstand existieren.

CONST_MEMORY_BEARER
CONST_MEMORY
CONST_WOUND
CONST_COLLAPSE
CONST_FINAL_REVELATION
CONST_END_TRANSCENDENCE
CONST_END_PERSISTENCE

Nicht entfernbar.
Nicht optional.

---
# 4. UNIVERSE STATE

struct UniverseState
{
int64 WorldSeed;
float WorldTimeDays;
float CollapseLevel;
float MemoryIntegrity;
float FractureLevel;
float UniverseStability;
int CollapsePhase;
bool WoundReached;
}

WorldTimeDays:
0.0 - 100.0

CollapseLevel:
0.0 - 1.0

MemoryIntegrity:
0.0 - 1.0

FractureLevel:
0.0 - 1.0

UniverseStability:
0.0 - 1.0

---
# 5. MEMORY MODEL

Definition:
Die Erinnerung ist eine fundamentale Erkenntnis.

Nicht:
- Person
- Spezies
- Gottheit
- Artefakt

Die Erinnerung besitzt Auswirkungen auf die Realität.

MemoryIntegrity:

1.0 = maximal vergessen
0.0 = maximal erinnert

---
# 6. CONSISTENCY MODEL

struct Consistency
{
float Value;
}

Range:
0.0 - 1.0

Anwendbar auf:
- Regions
- NPCs
- Creatures
- Objects
- Memories

0.00 - 0.20
Critical

0.21 - 0.50
Unstable

0.51 - 0.80
Stable

0.81 - 1.00
Highly Stable

Niedrige Konsistenz erhöht:
- ReconstructionChance
- AnomalyChance
- IdentityErrors

---
# 7. RECONSTRUCTION MODEL

Definition:
Verlorene Informationen werden durch die Realität ersetzt.

Targets:
- Region
- NPC
- Creature
- Event
- Structure

ReconstructionChance =
Function(
Consistency,
CollapseLevel,
MemoryIntegrity
)

Regel:
Rekonstruktionen sind niemals perfekt.

---
# 8. ANOMALY MODEL

enum EAnomaly
{
Memory,
Time,
Identity,
Geometry,
Physics
}

Chance =
BaseChance
* CollapseLevel
* RegionalModifier

---
# 9. TIME MODEL

System A:
World Time

100 reale Tage.

Läuft permanent.

System B:
Fracture Time

Keine Region.

Kein Biom.

Kein Level.

Fracture Time ist ein Zustandswechsel.

Richtung:
Nur Zukunft.

TimeOffset:
1 Stunde bis mehrere Jahre.

Auswirkungen:
- RegionStates
- NPCStates
- ReconstructionStates
- EcologyStates

---
# 10. PLAYER MODEL

Class:
MemoryBearer

Permanent:
true

DeleteAllowed:
false

Ausnahme:
Transcendence End State

---
# 11. DEATH MODEL

Tod erzeugt keinen GameOver Zustand.

Tod erzeugt MemoryShift.

MemoryShift Outputs:
- RegionChange
- TimeChange
- ReconstructionChange

Save bleibt erhalten.

Spielfortschritt bleibt erhalten.

---
# 12. COLLAPSE MODEL

Origin:
TheWound

Propagation:
Graph Based

Phases:
P1 Stable
P2 Distortion
P3 Reconstruction
P4 Fracture
P5 Collapse

Kollaps beeinflusst:
- Regions
- Creatures
- NPCs
- Physics
- Anomalies

---
# 13. THE WOUND

Universe ID:
REGION_WOUND

Required:
true

Randomized:
true

ConstantFunction:
true

TimeEnabled:
false

CollapseEnabled:
false

AgingEnabled:
false

Beschreibung:
Ort an dem das Vergessen niemals vollständig gelungen ist.

---
# 14. FINAL STATE RULES

Beim vollständigen Erreichen der Wunde:

WorldTime Freeze
Collapse Freeze
Aging Freeze

Der Spieler kann unbegrenzt verweilen.

Keine automatische Entscheidung.

---
# 15. END STATES

END_TRANSCENDENCE

Memory Removed
Wound Closed
Reality Reconstructed

END_PERSISTENCE

Memory Retained
Wound Open
Reality Collapse Complete

---
# 16. SYSTEM ACCESS

Write Access:
- CollapseSystem
- FractureSystem
- ReconstructionSystem

Read Access:
- WorldGenerator
- NPCSystem
- CreatureSystem
- DialogueSystem
- SaveSystem
- AISystem

---
# 17. DESIGN RESTRICTIONS

Verboten:
- klassische Götter
- Auserwähltenprophezeiungen
- Gut gegen Böse Hauptplot
- menschliche Zivilisationen
- klassische Fantasyrassen
- permanenter Spielertod

---
# 18. IMPLEMENTATION SUCCESS CRITERIA

Ein Entwickler muss nach Lesen dieses Dokuments beantworten können:

- Was ist die Erinnerung?
- Was ist Konsistenz?
- Was ist Rekonstruktion?
- Was ist Frakturzeit?
- Was ist Kollaps?
- Was ist die Wunde?
- Welche Daten müssen gespeichert werden?
- Welche Systeme lesen diese Daten?
- Welche Systeme schreiben diese Daten?

Dokumentstatus:
FINAL
LOCKED
CANON
