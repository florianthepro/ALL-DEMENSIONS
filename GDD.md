# ALL-DEMENSIONS
# GDD.md
## Game Design Document
## Version 1.0

# 1. ZWECK

Dieses Dokument definiert die vollständige Designarchitektur von ALL-DEMENSIONS.

Das GDD übersetzt die Vision aus dem MDD in konkrete Spielsysteme.

Zielgruppe:
- Game Director
- Lead Designer
- Gameplay Programmer
- World Programmer
- Narrative Designer
- Audio Designer
- Level Designer
- Technical Designer

---
# 2. SPIELÜBERSICHT

Genre:
- Open World
- Action Adventure
- Exploration
- Physikrätsel
- Koop

Perspektive:
- Third Person

Spieler:
- 1 bis 4

Plattform:
- Steam (PC)

---
# 3. SPIELERROLLE

Titel:
Erinnerungsträger

Der Erinnerungsträger stellt die stabilste bekannte Existenz der Realität dar.

Er kann nicht endgültig sterben.

Sterben führt zu Erinnerungsversatz.

---
# 4. CORE GAME LOOP

1. Erkunden
2. Regionen verstehen
3. Physikregeln lernen
4. Eigenschaften transportieren
5. Dissonanzen überwinden
6. Erinnerungsfragmente entdecken
7. Richtung Ursprung reisen
8. Rekonstruktionen beobachten
9. Finale Region erreichen
10. Endzustand auslösen

---
# 5. STORYSTRUKTUR

Keine klassische Questline.

Keine Kapitel.

Keine Missionsliste.

Story entsteht durch:
- Exploration
- Rekonstruktionen
- NPC-Veränderungen
- Anomalien
- Weltveränderungen

---
# 6. ZEITSYSTEM

System A:
Weltzeit

100 reale Tage pro Spielstand.

Zeit läuft auch außerhalb des Spiels.

System B:
Frakturzeit

Zeitfehlerzustände.

Spieler springt abschnittsweise in die Zukunft.

Folgen:
- Regionen ändern sich
- NPCs ändern sich
- Landschaften ändern sich
- Beziehungen ändern sich

---
# 7. TODSYSTEM

Tod erzeugt keine Neu-Ladung.

Tod erzeugt Erinnerungsversatz.

Mögliche Resultate:
- neue Region
- neue Zeitlage
- neue Rekonstruktionsstufe

---
# 8. KOOP

1-4 Spieler.

Unterstützt:
- Solo
- Lokaler Koop
- Online Koop
- Hybrid Koop

Lore:
Mehrere Manifestationen desselben Erinnerungsträgers.

---
# 9. WELTGENERIERUNG

Beim Erstellen eines Spielstands wird die Welt einmal erzeugt.

Danach bleibt die globale Struktur bestehen.

Lokale Mutationen bleiben möglich.

Generierungsschichten:

1. Weltgraph
2. Regionen
3. Physikfelder
4. Biome
5. Narrative Felder
6. Anomaliefelder

---
# 10. REGIONEN

Regionen bestehen aus:
- Physik
- Biom
- Stabilität
- Rekonstruktionsgrad
- Kollapsgrad
- Narrativdaten

Regionen können Varianten besitzen.

Keine Region muss exakt identisch erneut erscheinen.

---
# 11. PHYSIKFELDER

Persistenzfeld
Stillfeld
Resonanzfeld
Inversionsfeld
Spiegelfeld
Rekursionsfeld
Kompressionsfeld
Expansionsfeld
Superpositionsfeld

Physikfelder bilden die Grundlage der Rätsel.

---
# 12. INVENTAR UND AUSRÜSTUNG

Kein magisches Inventar.

Objekte existieren physisch.

Transport erfolgt sichtbar.

Ausrüstung wird am Körper getragen.

---
# 13. RÄTSELSYSTEM

Objekte können Eigenschaften übernehmen.

Eigenschaften können zwischen Regionen transportiert werden.

Rätsel entstehen aus der Kombination unterschiedlicher Physikfelder.

---
# 14. GEGNER

Bezeichnung:
Dissonanzen

Typen:
- Echoform
- Restform
- Hohlwesen
- Rekursion
- Fragmentkoloss
- Bruchform

---
# 15. NPC SYSTEM

NPC-Daten:
- Identität
- Stabilität
- Erinnerung
- Beziehungen

NPCs können rekonstruiert werden.

Dadurch entstehen unterschiedliche Varianten derselben Existenz.

---
# 16. KOLLAPSSYSTEM

Der Kollaps beginnt an der Wunde.

Je weiter die Weltzeit fortschreitet:

- mehr Anomalien
- mehr Rekonstruktionen
- mehr Physikfehler
- mehr Inkonsistenzen

---
# 17. DIE WUNDE

Finale Region.

Eigenschaften:
- zeitlos
- kollabierend
- fragmentiert

Die Wunde stoppt die Weltzeit.

Der Spieler kann unbegrenzt verweilen.

---
# 18. ENDEN

Transzendenz:
Erinnerung loslassen.

Persistenz:
Erinnerung festhalten.

Kein Auswahlbildschirm.

Nur Handlungen.

---
# 19. AUDIO

Technologie:
FMOD Studio

Audio dient als narratives Werkzeug.

Schwerpunkte:
- Erinnerungsfragmente
- räumliche Stimmen
- regionale Klangidentität
- Anomalieaudio

---
# 20. ART

Stil:
Surreal-realistisch.

Grundregeln:
- keine Menschen
- keine klassischen Fantasyvölker
- keine bekannten Tiere
- keine bekannte Flora

---
# 21. TECHNISCHE BASIS

Engine:
Unreal Engine 5

Sprache:
C++
Blueprints

3D:
Blender

Audio:
FMOD

Versionsverwaltung:
Git

Dokumentation:
Obsidian

---
# 22. ABHÄNGIGKEITEN

Dieses Dokument wird spezifiziert durch:

- Universe Bible
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
