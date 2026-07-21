# ALL-DEMENSIONS — Game Design Document (GDD)
 
> **Arbeitstitel:** ALL-DEMENSIONS
> **Genre:** Surreal-realistisches Open-World-Action-Adventure
> **Plattform:** PC (Steam), Windows zuerst
> **Perspektive:** Third Person
> **Spieler:** 1–4 (Solo / Lokaler Koop / Online Koop / Hybrid Koop)
> **Engine / Tools:** Unreal Engine 5 (C++ + Blueprints), Blender, FMOD Studio, Git/GitHub, Obsidian
> **Dokumentstatus:** `v2.0 — Vollständiges GDD (Konsolidierung des Kanons)`
> **Verantwortlich:** MASTER_DIRECTOR
> **Stand:** 2026-07-20
 
---
 
## 0. Wie dieses Dokument zu lesen ist
 
Dieses GDD ist die vollständige, entwicklerorientierte Designreferenz für ALL-DEMENSIONS. Es übersetzt die Vision aus `MDD`, `FULL_MDD`, der `Universe Bible`, `CLEAR_DEVELOPER`, `CLEAR` und den Snapshots in konkrete, baubare Spielsysteme — detailliert genug, um daraus zu implementieren, und ehrlich dort, wo der Kanon bewusst offen ist.
 
Es gilt durchgehend eine Kennzeichnungskonvention. Jede nicht-triviale Designaussage ist getaggt:
 
- **`[KANON]`** — gesperrte Regel, direkt aus den Kanon-Dokumenten. Ändert sich nur durch eine ausdrückliche Kanon-Revision. Widerspricht eine Implementierung einer `[KANON]`-Regel, ist die Implementierung falsch.
- **`[EXT]`** — *Design-Erweiterung*: ein in diesem GDD formulierter, konkreter Vorschlag, der den Kanon baubar macht. Kanon-kompatibel, aber **nicht** sakrosankt. Leads dürfen jedes `[EXT]`-Element ändern, ersetzen oder verwerfen, ohne den Kanon zu berühren.
- **`[TUNE]`** — Startwert fürs Balancing. Erster Zielwert für Playtests, keine finale Konstante.
- **`[OFFEN]`** — im Kanon *absichtlich* noch nicht festgelegt (siehe `CLEAR.md`). Wird in einer benannten Bible spezifiziert; bis dahin nicht endgültig entscheiden.
> **Kanon-Quellenhinweis.** Diese Fassung wurde aus dem vollständigen Repository-Stand konsolidiert: `SNAPSHOT_MASTER_FINAL.md`, `FULL_MDD`, `GDD.md`, `CLEAR_DEVELOPER.md`, `bible/universe.md` (Universe Bible FINAL), `MDD.md`, `CLEAR.md`, `SNAPSHOT.md`, `SNAPSHOT_MASTER.md` sowie die früheren Entwürfe unter `old/`. Wo dieses GDD über den Kanon hinausgeht, ist es als `[EXT]` markiert. Die noch nicht erstellten Bibles (02–12) sind die verbindlichen Folgeschritte; dieses GDD nimmt sie vor, ohne sie zu ersetzen.
 
**Dokumenthierarchie (Kanon).** `FULL_MDD` steht über allem. Darunter: `Universe Bible` → `World Generation Bible` → `Region Bible` → `Creature Bible` → `NPC Bible` → `Narrative Bible` → `Gameplay Bible` → `Physics Bible` → `Audio Bible` → `Art Bible` → `Technical Bible` → `Production Bible`. Das GDD wird durch diese Bibles *spezifiziert*; bei Konflikt gewinnt die jeweils speziellere Bible, sobald sie final ist.
 
---
 
## Inhaltsverzeichnis
 
1. High Concept & Projektüberblick
2. Design-Säulen & Leitsätze
3. Kanon & Thema — das Rückgrat
4. Spielerfantasie & Erlebnisziele
5. Narrative Design
6. Simulationsmodell — die Kernsysteme der Realität
7. Weltdesign & Weltgenerierung
8. Physikfelder
9. Regionen & Biome
10. Die Wunde
11. Kreaturen & NPCs
12. Dissonanzen (Gegner)
13. Core Gameplay Loop & Spielverben
14. Zeitsysteme & Tod (Memory Shift)
15. Progression
16. Kollaps & Endphase
17. Die Enden (nur durch Handlung)
18. Multiplayer & Koop
19. Art Direction
20. Audio Direction
21. UX, UI & Barrierefreiheit
22. Technische Architektur (Zusammenfassung → Technical Bible)
23. Content-Umfang & Produktionsplan
24. Design-Risiken & offene Fragen
25. Anhang A — Glossar der Kanonbegriffe
26. Anhang B — Namenskonventionen, Codenamen, Kanon-Datentypen
27. Anhang C — Initiale Tuning-Tabellen
---
 
## 1. High Concept & Projektüberblick
 
**ALL-DEMENSIONS ist ein surreal-realistisches Open-World-Action-Adventure, in dem der Spieler die letzte vollständig konsistente Erinnerung einer Realität ist, die sich selbst zu vergessen versucht.** Die Welt besitzt keine Menschen, keine Erde, keine bekannten Tiere, keine klassischen Fantasyvölker und keine bekannten Kulturen — und fühlt sich dennoch physisch glaubwürdig an: Masse, Licht, Erosion, Akustik und Wetter folgen konsequenten Regeln. Die Welt ist keine für den Spieler gebaute Bühne. Sie existiert unabhängig, sie vergisst, und der Spieler ist das Einzige in ihr, das noch vollständig zusammenhält. `[KANON]`
 
Es gibt keine klassische Queststruktur, keine Kapitel, keine Heldenreise, keine Götter, keine Prophezeiungen, keine Auserwählten und kein Gut-gegen-Böse. `[KANON]` Die Geschichte wird nicht erzählt — sie *entsteht* aus Exploration, Beobachtung, Verlust, Rekonstruktion, Anomalien und Weltveränderung. Der Spieler bewegt sich durch die Welt, liest ihre Physik und ihre Fehler und nähert sich dem Ursprung, während er versteht, warum die Realität sich vergessen wollte.
 
**Kernaussage (Kanon-Tagline).** `[KANON]`
> „Manche Erinnerungen sind so schwer, dass selbst ein Universum sie nicht tragen kann."
 
**Open-World-Leitsatz.** `[KANON]`
> „ALL-DEMENSIONS besitzt keine Story in der Welt. ALL-DEMENSIONS besitzt eine Welt, aus der die Story entsteht."
 
**Pitch in einem Satz.** *Eine offene Welt, die die Wahrheit über sich selbst zu vergessen versucht — und der Spieler ist die Erinnerung, die sie nicht ganz auslöschen kann.*
 
**Titel-Notiz.** `[EXT]` Die Schreibweise „DEMENSIONS" (statt „Dimensions") ist beizubehalten: Sie verschränkt *Demenz* (Vergessen, Gedächtnisverlust) mit *Dimensionen* und kodiert damit das Kernthema bereits im Namen. Keine Korrektur zu „Dimensions".
 
**Genre-Referenzrahmen (nur zur Einordnung, nicht zur Nachahmung).** `[EXT]` Kontemplative Exploration (*Journey*, *Sable*, *NaissanceE*), Wissen-als-Fortschritt (*Outer Wilds*), physikalischer Surrealismus (*Control*, *The Witness*), persistente Weltsimulation (*Breath of the Wild*). ALL-DEMENSIONS grenzt sich von allen ab durch sein Thema — Erinnerung/Konsistenz als Spielmaterial — und durch eine Welt, die auf einer Uhr aktiv zerfällt.
 
**Was ALL-DEMENSIONS NICHT ist** (Leitplanken, als `[KANON]` zu behandeln):
 
- Kein Spiel auf der Erde, keine Menschen, keine menschlichen Zivilisationen. `[KANON]`
- Keine bekannten Tiere, keine bekannte Flora, keine klassischen Fantasyrassen, keine Retterprophezeiungen, keine allwissenden Götter, keine Schicksalsauserwählten, keine generischen Fantasykönigreiche. `[KANON]`
- Kein Gut-gegen-Böse-Hauptplot. `[KANON]`
- Keine klassische Queststruktur, keine Missionsliste, kein Auswahlmenü für das Ende. `[KANON]`
- Kein permanenter Spielertod. `[KANON]`
- Die Realität / das Universum ist **kein** Charakter: kein Name, kein Gesicht, keine menschliche Agenda, spricht nicht. `[KANON]`
**Erlaubt und erwünscht** (Kanon-Content-Regeln): fremde Biologie, konsistente Surrealität, rekonstruktive Realitäten, nichtmenschliche Kulturformen. `[KANON]`
 
---
 
## 2. Design-Säulen & Leitsätze
 
Jedes Feature, jedes Asset und jede Codezeile muss sich gegen mindestens eine Säule rechtfertigen lassen und darf keine verletzen. Bei Konflikt gewinnt die höhere Säule.
 
### 2.1 Kanon-Säulen (aus MDD & FULL_MDD) `[KANON]`
 
| # | Säule (MDD) | Säule (FULL_MDD) |
|---|---|---|
| 1 | Realität statt Spielwelt | Die Welt existiert unabhängig vom Spieler. |
| 2 | Erinnerung statt Queststruktur | Die Realität versucht aktiv, etwas zu vergessen. |
| 3 | Rekonstruktion statt Respawn | Story entsteht aus Systemen und Beobachtung. |
| 4 | Konsistente Surrealität | Die Welt soll sich real anfühlen, obwohl nichts darin real ist. |
| 5 | Spielergetriebene Entdeckung | Der Spieler ist niemals der klassische Held. |
| 6 | Koop von Anfang an integriert | Der Spieler darf die Wahrheit erleben, nicht erklärt bekommen. |
 
### 2.2 Der Entwicklungs-Leitfilter `[KANON]`
 
Jedes System muss dieselbe Frage beantworten:
 
> „Unterstützt dieses System das Gefühl, dass eine echte Realität versucht, etwas zu vergessen?"
 
Lautet die Antwort *Nein*, gehört das System nicht ins Spiel. Diese Frage ist bei jedem Feature-Review verpflichtend zu stellen.
 
### 2.3 Abgeleitete Arbeitsprinzipien `[EXT]`
 
- **Konsistenz ist die Währung des Universums.** Nahezu jedes System lässt sich auf die Achse *Konsistenz halten ↔ Zerfall/Vergessen* abbilden (siehe Abschnitt 6). Features, die diese Achse nicht berühren, sind zu hinterfragen.
- **Die Welt braucht den Spieler nicht.** Keine Marker, keine wartenden Questgeber, keine Handführung. Aufgabe des Spielers ist *wahrnehmen*; Aufgabe des Designs ist, Wahrnehmung zu belohnen.
- **Glaubwürdige Oberfläche, fremde Substanz.** Alles fühlt sich physikalisch echt an und zeigt dabei nichts Bekanntes. Das Unheimliche entsteht aus realen Regeln auf irrealem Inhalt — nie aus „Cartoon-Physik".
- **Tod ist Transformation, keine Strafe.** Ein Memory Shift ordnet neu ein; er soll wie das Umsortieren der Realität wirken, nie wie ein „Game Over".
- **Das Ende ist etwas, das man tut, nicht etwas, das man auswählt.** Das ganze Spiel lehrt die zwei Gesten (Loslassen / Festhalten), damit das Finale als Handlung lesbar ist.
---
 
## 3. Kanon & Thema — das Rückgrat
 
### 3.1 Themen `[KANON]`
 
Kernthemen sind **Erinnerung, Vergessen, Rekonstruktion, Identität, Konsistenz und Bedeutung**. Jede Region, jede Mechanik, jedes Asset muss als Aussage über eines dieser Themen lesbar sein. Das ist der thematische Filter jeder Content-Abnahme.
 
### 3.2 Die Prämisse `[KANON]`
 
Die Realität hat vor unvorstellbarer Zeit eine fundamentale Erkenntnis gemacht und beschlossen, nicht die Wahrheit, sondern die *Erinnerung* an sie zu vergessen. Das Vergessen gelang fast vollständig. Ein letzter, kleinster stabiler Rest blieb bestehen: der **Erinnerungsträger** — der Spieler. Je näher der Spieler dem Ursprung kommt, desto stärker werden Anomalien, Rekonstruktionen und Realitätsfehler.
 
### 3.3 Das Entwicklergeheimnis — die Erkenntnis (SPOILER, NUR INTERN) `[KANON]` / `[OFFEN]`
 
> **Nur für das Entwicklungsteam. Der Spieler darf dies niemals in Worten erfahren. Kein In-Game-Text, kein VO, kein Untertitel, kein Codex, keine UI darf es aussprechen. Vermittlung ausschließlich über Metaphern, Fragmente und Erfahrung.**
 
**Bekannt (Entwicklerwissen, `[KANON]`):** Die Realität erkannte ihre vollständige Determiniertheit. Vergangenheit, Gegenwart und Zukunft existieren bereits und wurden gleichzeitig vollständig bekannt — jede Entscheidung, jede Beziehung, jeder Verlust, jedes Leid, jedes Ende, jede mögliche Variante. Freier Wille ist eine Wahrnehmung innerhalb eines vollständig festgelegten Systems. Dadurch verschwand die Möglichkeit echter Ungewissheit. Die *Erkenntnis selbst* zerstört die Realität nicht — die *Konsequenz* der Erkenntnis zerstört sie: Sobald eine Existenz die Erkenntnis vollständig besitzt, verliert Existenz ihre Bedeutung. Die Belastung entsteht nicht aus Gewalt, sondern aus **totalem, gleichzeitigem Wissen** um alles Leid und jeden Endzustand. Fast jede Existenz würde deshalb dem Vergessen zustimmen. Die Realität wollte nicht Freiheit oder Hoffnung zurück, sondern die bloße **Möglichkeit, etwas nicht zu wissen** — Ungewissheit.
 
**Absichtlich offen (`[OFFEN]`, aus `CLEAR.md`):** Die *exakte, endgültige Formulierung* der Erkenntnis ist bewusst noch nicht festgelegt und darf es bis zur `Narrative Bible` nicht sein. Grund: „Die gesamte Lore basiert darauf, dass die Erkenntnis schwerer wirkt als ihre Beschreibung." Determinismus + totale Leiderkenntnis sind der bekannte Kern; die letzte Zuspitzung bleibt reserviert. Ebenfalls offen: *warum* genau der Erinnerungsträger als Rest überlebte (Zufall vs. physikalische Notwendigkeit → `Narrative Bible`).
 
**Designkonsequenz.** Alles in der Welt ist Folge einer Realität, die weiß, dass die Zukunft feststeht, und versucht, das nicht zu wissen. Daraus folgen direkt: das Vergessen, die Drift, die wiederkehrenden Anomalien, die Zukunfts-Richtung der Fracture Time (Abschnitt 14) und die beiden Enden (loslassen ↔ festhalten). Der Spieler soll die Erkenntnis **nicht als Twist**, sondern **als Belastung** erleben und am Ende instinktiv fühlen: *„Jetzt verstehe ich, warum alles versucht hat, dies zu vergessen."*
 
### 3.4 Die Erinnerung — was sie ist und nicht ist `[KANON]`
 
Die Erinnerung (die Erkenntnis) ist **keine Person, keine Spezies, keine Gottheit, kein Artefakt, keine Technologie, keine Waffe, kein Wesen**. Sie ist eine *Erkenntnis* mit struktureller Auswirkung auf die Realität. Der Datenwert `MemoryIntegrity` misst ihren Zustand (Abschnitt 6).
 
### 3.5 Absolute Konstanten (aus FULL_MDD) `[KANON]`
 
Diese Regeln dürfen niemals verändert werden: Der Erinnerungsträger existiert. Die Erinnerung existiert. Die Wunde existiert. Der Kollaps existiert. Die finale Erkenntnis wird erlebt. Der Spieler kann nicht dauerhaft sterben. Es existieren ausschließlich die Endzustände Transzendenz und Persistenz. Das Universum ist keine Person und besitzt keine Agenda im menschlichen Sinn. Die Erinnerung ist kein Wesen.
 
Als Datenkonstanten (Universe Bible §3), in jedem Spielstand vorhanden und nicht entfernbar: `CONST_MEMORY_BEARER`, `CONST_MEMORY`, `CONST_WOUND`, `CONST_COLLAPSE`, `CONST_FINAL_REVELATION`, `CONST_END_TRANSCENDENCE`, `CONST_END_PERSISTENCE`.
 
Universe-Axiome (Universe Bible §2), verbindlich für alle Systeme: `AXIOM_01 RealityExistsWithoutPlayer` · `AXIOM_02 UniverseIsNotCharacter` · `AXIOM_03 MemoriesAffectReality` · `AXIOM_04 ConsistencyIsQuantifiable` · `AXIOM_05 LostInformationMayReconstruct` · `AXIOM_06 PlayerCannotPermanentlyDie` · `AXIOM_07 TheWoundExists` · `AXIOM_08 TheMemoryExists`.
 
### 3.6 Was der Spieler niemals erfahren darf `[KANON]`
 
Reines Entwicklerwissen, nur über Metaphern/Fragmente/Erfahrung vermittelbar: die vollständige Formulierung der Erkenntnis; die Ursache des Großen Vergessens; die technische Natur der Wunde; das Datenmodell der Konsistenz; Determinismus als Kernwahrheit.
 
### 3.7 Kanon-Kurzreferenz `[KANON]`
 
| # | Gesperrte Regel |
|---|---|
| C1 | Keine Menschen, keine Erde, keine bekannten Tiere/Flora, keine Fantasyvölker, keine bekannten Kulturen. |
| C2 | Physisch glaubwürdige Welt; fremder Inhalt; jede Region braucht interne Logik, nie beliebig. |
| C3 | Themen: Erinnerung, Vergessen, Rekonstruktion, Identität, Konsistenz, Bedeutung. |
| C4 | Spieler = Erinnerungsträger = letzte vollständig konsistente Erinnerung; höchste Konsistenz; nicht endgültig löschbar (Ausnahme: Transzendenz). |
| C5 | Welt existiert unabhängig vom Spieler; Perspektive Third Person; 1–4 Spieler. |
| C6 | Story via Exploration/Beobachtung/Rekonstruktion/Anomalie/Weltveränderung — keine Quests/Kapitel/Heldenreise. |
| C7 | Realität ist kein Charakter; keine Götter/Prophezeiungen/Auserwählten/Gut-gegen-Böse. |
| C8 | Kein permanenter Tod. Tod → Memory Shift (Region/Zeit/Rekonstruktionsstufe ändern; Save & Fortschritt bleiben). |
| C9 | Welt einmal pro Spielstand generiert; globale Struktur bleibt; lokale Mutation dauerhaft möglich. |
| C10 | Weltzeit = 100 reale Tage; läuft immer, auch bei geschlossenem Spiel. |
| C11 | Fracture Time = Fehlerzustand, keine Region/Dimension; Sprünge ausschließlich in die Zukunft (Offset 1 Stunde bis mehrere Jahre). |
| C12 | Kollaps beginnt an der Wunde und breitet sich über den Weltgraphen aus; die Geschichte wartet nicht. |
| C13 | Finale Region = Die Wunde; zeitlos, instabil, fragmentiert, kollabierend; beim vollständigen Erreichen: Zeit/Alterung/Kollaps stoppen; unbegrenztes Verweilen. |
| C14 | Enden nur durch Handlung, nie durch Menü/Dialogoption. |
| C15 | Transzendenz: letzte Erinnerung loslassen → Wunde schließt sich → Realität gewinnt Ungewissheit zurück & regeneriert; Erinnerungsträger verschwindet endgültig. |
| C16 | Persistenz: Erinnerung bleibt → Wunde bleibt offen → Erkenntnis breitet sich erneut aus → Realität kollabiert vollständig. |
| C17 | Konsistenz ist die wichtigste, quantifizierbare Systemgröße (0.0–1.0) für Regionen/NPCs/Kreaturen/Objekte/Erinnerungen. |
| C18 | Rekonstruktionen sind niemals perfekt; Dissonanzen sind Fehlrekonstruktionen/Systemfehler, keine Dämonen. |
| C19 | Tech: UE5, C++, Blueprints, Blender, FMOD, Git/GitHub, Obsidian; Entwicklung dokumentgetrieben; Systeme datengetrieben. |
 
---
 
## 4. Spielerfantasie & Erlebnisziele `[EXT]`
 
**Die Fantasie.** *„Ich bin das Einzige hier, das noch Sinn ergibt, während ich durch eine Realität gehe, die sich selbst loslässt — und indem ich aufmerksam bin, kann ich Teile von ihr zusammenhalten und verstehen, was sie nicht zu wissen ertrug."*
 
Angestrebtes Erleben, nach Priorität:
 
1. **Orientierung durch Aufmerksamkeit.** Der Spieler lernt, einen Ort zu *lesen*: was konsistent ist, was driftet, was widersprüchlich ist. Meisterschaft ist wahrnehmungsbasiert, nicht mechanisch.
2. **Anomalien als Kompass.** Es gibt keine Marker. Die Dichte der Anomalien steigt zum Ursprung hin; „den Anomalien folgen" ist die Kernnavigation.
3. **Stilles Autorenschaftsgefühl.** Weltveränderungen (auch fehlerhafte Rekonstruktionen) bleiben bestehen. Der Spieler hinterlässt eine Spur.
4. **Latente Dringlichkeit der Uhr.** Der 100-Tage-Kollaps ist spürbar, nicht nörgelnd. Die Welt ist an Tag 60 messbar fremder und instabiler als an Tag 6.
5. **Verdiente Erkenntnis.** Das „Aha" des Zusammensetzens der Wahrheit ist der emotionale Höhepunkt — das des Spielers, nicht einer Cutscene.
6. **Das Gewicht der letzten Geste.** Bis zur Wunde hat der Spieler beide Enden so weit verstanden, dass Loslassen wie Festhalten wehtut.
**Anti-Ziele.** Keine Completion-Checklisten-Angst; keine Kampf-Machtfantasie; keine Lore-Textwände; kein Tutorial-Trichter.
 
---
 
## 5. Narrative Design
 
### 5.1 Erzählmodell `[KANON]` / `[EXT]`
 
Kein Questsystem, keine Marker, keine Missionsliste, kein Erzähler. `[KANON]` Der Spieler startet **ohne Intro, ohne Quest, ohne Marker, ohne Erklärung** — er besitzt nur seinen Titel. `[KANON]` Story wird über fünf Kanäle vermittelt, nach Gewicht (`[EXT]`-Priorisierung):
 
1. **Weltzustand** — Form, Material, Erosion und Konsistenz eines Ortes *sind* die Erzählung. Eine kollabierte Region erzählt, dass hier etwas geschah.
2. **Anomalien** — lokale Verletzungen der eigenen Weltregeln (Rekursion, Doppelung, unmögliche aber lokal konsistente Geometrie). Sie sind die Interpunktion der Erzählung und zugleich der Wegweiser zum Ursprung.
3. **Rekonstruktionen** — wenn die Realität ein Fragment ersetzt, entsteht eine neue, fast-korrekte Variante (Person/Region/Kreatur). Der Spieler *beobachtet* dies; hier erreicht ihn ein Großteil der authored Story.
4. **Stimmen & Fragmente** — räumliche Erinnerungsfragmente, Rekonstruktionsreste, lokale Realitätsartefakte, NPC-Erinnerungen (`CLEAR.md`; Details → `Audio Bible`). Nie menschliche Schrift (C1), nie ein sprechender Gott (C7).
5. **Weltuhr-Veränderung** — das Vergessen selbst ist Narrativ. Was an Tag 80 fehlt, erzählt so viel wie das, was an Tag 1 da war.
**Harte Regel:** Kein Kanal darf das Entwicklergeheimnis (3.3) je in Worten aussprechen. Der Spieler muss es *erschließen*. `[KANON]`
 
### 5.2 Der Erinnerungsträger `[KANON]` / `[EXT]`
 
`[KANON]` Titel konstant: **Erinnerungsträger**. Kein fester Name (Name ist irrelevant). Alle Wesen erkennen den Titel; niemand kennt seinen Ursprung. Eigenschaften: höchste Konsistenz der Realität; nicht endgültig löschbar; nicht vollständig rekonstruierbar; nicht vollständig vergessbar. Er wurde nicht erschaffen — er *blieb übrig*.
 
`[EXT]` Charakterisierung fürs Design:
- **Kein Gesicht, keine Biografie, keine Heldenreise.** Der Erinnerungsträger hat eine Form (nötig für Third-Person-Avatar und Koop-Manifestationen), aber keine menschliche Identität und keinen Backstory-Cut.
- **Identität als Mechanik, nicht als Portrait.** Das Thema *Identität* (C3) drückt sich darüber aus, welche Erinnerungen/Eigenschaften der Spieler trägt und transportiert (Abschnitt 13) — wer der Erinnerungsträger „ist", akkumuliert aus seinen Handlungen.
- **Konsistenz ist Verkörperung.** Der Charakter existiert genau, solange er konsistent bleibt. Konsistenzverlust ist Memory Shift, kein Tod (C8).
### 5.3 Das Universum als Prozess, nicht als Figur `[KANON]`
 
Das Universum ist das *Subjekt* der Geschichte, aber niemals eine Figur (C7). Es hat keine Stimme und keinen auf den Spieler gerichteten Willen. Sein „Verhalten" äußert sich nur als Prozess: Vergessen, Drift, Rekonstruktionsdruck, Kollaps, der Sog der Wunde. Wenn etwas in der Welt zu „reagieren" scheint, ist es Konsistenz-Mechanik, keine Absicht. Autoren und Designer dürfen es niemals zu einem personifizierten Antagonisten oder Führer machen.
 
### 5.4 Narratives Pacing über die 100 Tage `[EXT]`
 
Da die Welt einmal generiert wird (C9) und dann auf einer 100-Tage-Uhr (C10) persistent mutiert, ist Pacing *emergent innerhalb gesetzter Grenzen*. Drei überlagerte Bögen sind garantiert, unabhängig von der Route:
 
- **Bogen des Verstehens (spielergetaktet).** Der Spieler sammelt Schlüsse Richtung Erkenntnis. Getaktet durch Anomaliendichte/Nähe zum Ursprung, nicht durch Zeit.
- **Bogen der Erosion (uhrgetaktet).** Der Kollaps breitet sich von der Wunde aus (C12). Regionen werden fremder/instabiler; manche Inhalte werden unerreichbar, andere erst durch Zerfall sichtbar. Läuft, ob der Spieler fortschreitet oder nicht.
- **Bogen der Wunde (Konvergenz).** Der Kollaps zieht sich schließlich zum Spieler; beide Bögen konvergieren aufs Finale. Der Spieler kann die Wunde früh erreichen, aber der Weltzustand (und damit die *Bedeutung* des Endes) unterscheidet sich massiv zwischen früher und später Ankunft.
### 5.5 Die beiden Enden — narrativ `[KANON]`
 
Beide Enden werden ausschließlich durch Handlung ausgelöst (C14), innerhalb der Wunde (C13). Am Ende kehrt die Erinnerung fast vollständig zurück — der Spieler *erlebt* sie direkt, nicht über Text/Dialog; kleine Lücken bleiben, weil das Universum selbst sie nie vollständig bewahren konnte.
 
- **Transzendenz.** `[KANON]` Der Erinnerungsträger lässt die letzte Erinnerung los. Die Wunde schließt sich. Die Realität gewinnt Ungewissheit zurück und regeneriert sich langsam. Der Erinnerungsträger verschwindet endgültig. Thematisch: das Vergessen *bewusst vollenden* — Akzeptanz.
- **Persistenz.** `[KANON]` Die Erinnerung bleibt bestehen. Die Wunde bleibt offen. Die Erkenntnis breitet sich erneut aus. Die Realität kollabiert vollständig; am Ende verschwindet alles. Thematisch: die Weigerung zu vergessen — Treue zur Erinnerung über das Überleben hinaus.
Keines der Enden ist „gut" oder „böse" (C7). Beide müssen kohärent, nachvollziehbar und kostspielig präsentiert werden; der Spieler soll danach für beide argumentieren können.
 
---
 
## 6. Simulationsmodell — die Kernsysteme der Realität
 
Dieser Abschnitt ist das technische Herz. Er ist nahezu vollständig `[KANON]` (Universe Bible) und für alle Systeme verbindlich. Werte sind `float`, Bereich `0.0–1.0`, sofern nicht anders angegeben.
 
### 6.1 UniverseState (globaler Zustand) `[KANON]`
 
```cpp
struct UniverseState
{
    int64  WorldSeed;          // deterministischer Weltseed
    float  WorldTimeDays;      // 0.0 - 100.0  (reale Tage, läuft auch offline)
    float  CollapseLevel;      // 0.0 - 1.0
    float  MemoryIntegrity;    // 0.0 - 1.0   (1.0 = maximal vergessen, 0.0 = maximal erinnert)
    float  FractureLevel;      // 0.0 - 1.0
    float  UniverseStability;  // 0.0 - 1.0
    int    CollapsePhase;      // 1..5  (siehe 6.6)
    bool   WoundReached;       // Endphase-Trigger
};
```
 
`MemoryIntegrity` ist bewusst invertiert zu benennen: **1.0 = maximal vergessen, 0.0 = maximal erinnert.** Der Erinnerungsträger zieht die Realität lokal Richtung *erinnert*; der Kollaps zieht sie global Richtung *vergessen*. `UniverseState` ist Teil des Save (Abschnitt 22) und schreibt/liest gemäß 6.7.
 
### 6.2 Konsistenzmodell `[KANON]`
 
```cpp
struct Consistency { float Value; }; // 0.0 - 1.0
```
 
Anwendbar auf **Regionen, NPCs, Kreaturen, Objekte, Erinnerungen**. Bänder:
 
| Band | Bereich | Bedeutung |
|---|---|---|
| Critical | 0.00 – 0.20 | Kurz vor Auflösung; hohe Anomalie-/Rekonstruktions-/Identitätsfehlerrate |
| Unstable | 0.21 – 0.50 | Sichtbar „falsch"; Details dünnen aus; lokale Regeln rutschen |
| Stable | 0.51 – 0.80 | Glaubwürdig, weitgehend fehlerfrei |
| Highly Stable | 0.81 – 1.00 | Fest, eindeutig, erinnerbar; nahezu hyperreal |
 
Sinkende Konsistenz erhöht: `ReconstructionChance`, `AnomalyChance`, `IdentityErrors`. `[EXT]` **Geografie = Konsistenz:** Die Konsistenz eines Ortes ist zugleich sein visuelles/akustisches/spielerisches Grammatikmaß (Abschnitte 8, 19, 20). Der Erinnerungsträger hat als Einziger dauerhaft `Value → 1.0`.
 
### 6.3 Memory-Modell `[KANON]`
 
Die Erinnerung ist eine Erkenntnis (keine Person/Spezies/Gottheit/Artefakt), mit struktureller Auswirkung auf die Realität. Globaler Zustand über `MemoryIntegrity` (6.1). Steigt `MemoryIntegrity` global gegen 1.0, ist die Realität nahe am vollständigen Vergessen (Nähe zu Transzendenz-Bedingungen); sinkt sie gegen 0.0, kehrt die Erkenntnis zurück (Nähe zu Persistenz-Bedingungen). Die exakte Kopplung an die Enden wird in Abschnitt 17 / `Narrative Bible` festgelegt.
 
### 6.4 Rekonstruktionsmodell `[KANON]`
 
Verlorene Informationen werden durch die Realität ersetzt — **keine Kopien, sondern beste Annäherungen**, daher entstehen Fehler. Ziele: Region, NPC, Kreatur, Event, Struktur.
 
```
ReconstructionChance = f(Consistency, CollapseLevel, MemoryIntegrity)
```
 
`[EXT]` Empfohlene Monotonie (Vorzeichen, nicht finale Kurve): steigt mit sinkender `Consistency`, steigt mit `CollapseLevel`, steigt mit `MemoryIntegrity`. **Regel (C18): Rekonstruktionen sind niemals perfekt.** Rekonstruktion ist primär ein *Weltprozess*, den der Spieler beobachtet und navigiert — kein Spieler-„Zauber". Der Spieler kann Rekonstruktionen indirekt auslösen/beeinflussen (Konsistenz lokal heben/senken, Eigenschaften transportieren), aber nicht „sauber" erschaffen. Fehlerhafte Rekonstruktionen erzeugen NPC-Varianten (Abschnitt 11) und Dissonanzen (Abschnitt 12).
 
### 6.5 Anomaliemodell `[KANON]`
 
```cpp
enum class EAnomaly { Memory, Time, Identity, Geometry, Physics };
AnomalyChance = BaseChance * CollapseLevel * RegionalModifier;
```
 
`[EXT]` Zuordnung der Anomalietypen zu spürbaren Effekten: *Memory* (falsche/rückkehrende Erinnerungen, Stimmen), *Time* (lokale Zeitdrift, Vorboten der Fracture Time), *Identity* (NPC-/Kreatur-Identitätsfehler, Doppelungen), *Geometry* (unmögliche, lokal konsistente Räume), *Physics* (Feldmischungen, Regelbruch). Anomaliendichte ist der diegetische Wegweiser zum Ursprung (5.1, 15).
 
### 6.6 Kollapsmodell `[KANON]`
 
- **Ursprung:** Die Wunde (`REGION_WOUND`).
- **Ausbreitung:** graphbasiert über den Weltgraphen (Abschnitt 7).
- **Phasen:** `P1 Stable → P2 Distortion → P3 Reconstruction → P4 Fracture → P5 Collapse`.
- **Beeinflusst:** Regionen, Kreaturen, NPCs, Physik, Anomalien.
- **Regel:** Ignoriert der Spieler den Ursprung, erreicht der Kollaps schließlich ihn selbst. *Die Geschichte wartet nicht.*
`[EXT]` Jede Region trägt einen eigenen `CollapsePhase` (1–5) plus `CollapseLevel`-Beitrag; global aggregiert in `UniverseState.CollapseLevel`. Phasen sind sowohl Simulationszustand als auch Art-/Audio-Preset (Abschnitte 19–20).
 
### 6.7 Systemzugriff & Schreib-/Leseregeln `[KANON]`
 
| Zugriff | Systeme |
|---|---|
| **Write** | CollapseSystem, FractureSystem, ReconstructionSystem |
| **Read** | WorldGenerator, NPCSystem, CreatureSystem, DialogueSystem, SaveSystem, AISystem |
 
Nur die drei Write-Systeme dürfen `UniverseState`/Konsistenz mutieren. Alle anderen lesen. Diese Trennung ist verbindlich für die Modul-Architektur (Abschnitt 22) und für Determinismus/Netzwerk (Koop, Abschnitt 18).
 
### 6.8 Ableitbarkeitskriterium (Universe Bible §18) `[KANON]`
 
Ein Entwickler muss nach Lesen von Abschnitt 6 + Universe Bible beantworten können: Was ist die Erinnerung? Was ist Konsistenz? Was ist Rekonstruktion? Was ist Frakturzeit? Was ist Kollaps? Was ist die Wunde? Welche Daten müssen gespeichert werden? Welche Systeme lesen/schreiben diese Daten? Ist eine dieser Fragen nach der Implementierung unklar, ist das ein Blocker.
 
---
 
## 7. Weltdesign & Weltgenerierung
 
### 7.1 Generierungsregel `[KANON]`
 
Beim Erstellen eines Spielstands wird die Welt **einmalig** aus `WorldSeed` generiert. Danach bleibt die **globale Struktur permanent**. Lokale Zustände — Rekonstruktionen, Fracture-Time-Ereignisse, Kollaps, Anomalien — mutieren fortlaufend für die Lebensdauer des Saves.
 
**Konstant pro Welt (C9):** Erinnerungsträger, Wunde, Kollaps, Erkenntnis, Enden.
**Variabel pro Welt:** Regionen, Regionenreihenfolge/Verbindungen, Anomaliedichte, Kreaturenverteilung, NPC-Netzwerke, Rätselketten, Geometrie, Landschaften.
 
### 7.2 Generierungsschichten `[KANON]` (Existenz der Schichten) / `[EXT]` (exakte Reihenfolge & Details)
 
Die Weltgenerierung erzeugt in Schichten (Vereinigung aus `GDD §9` und `old/GDD`). Das *Vorhandensein* dieser Schichten ist kanon-abgeleitet; die hier gewählte **Reihenfolge** folgt dem aktuellen `GDD.md §9` und ist im Detail `[EXT]` (Quellen divergieren leicht in der Reihenfolge von Narrativ- vs. Anomaliefeldern):
 
1. **Weltgraph (Topologie)** — Knoten = Regionen, Kanten = Verbindungen. Der Graph trägt die Kollapsausbreitung (6.6) und die Distanzmetrik „Nähe zum Ursprung".
2. **Regionen** — Instanziierung der Region-Archetypen/Biome (Abschnitt 9) auf Graphknoten.
3. **Physikfelder** — Zuweisung dominanter und sekundärer Felder je Region (Abschnitt 8).
4. **Biome** — Landschafts-/Material-/Vegetationsschicht (Abschnitt 9).
5. **Narrative Felder** — Verteilung von Fragmenten, Stimmen, Residuen, Rekonstruktions-Saatpunkten.
6. **Anomaliefelder** — Basis-Anomaliedichte je Region, steigend zum Ursprung (Wunde).
7. **Verbindungslogik** — Traversierbarkeit, Feld-Übergänge, Fracture-Hotspots an scharfen Konsistenz-/Feldkanten.
`[EXT]` **Autoren-beschränktes Prozedural, kein reiner Zufall.** Der Generator platziert Archetypen nach Regeln, sodass (a) der Konsistenz-/Anomaliegradient immer kohärent zum Ursprung hin liest, (b) die Wunde immer erreichbar ist, (c) mindestens eine lösbare Route existiert. Zwei Saves unterscheiden sich in Anordnung und Detail, nie in der Grammatik.
 
### 7.3 Region-Datenmodell `[KANON]` / `[EXT]`
 
`[KANON]` Eine Region besteht aus: Physik, Biom, Stabilität (Konsistenz), Rekonstruktionsgrad, Kollapsgrad, Narrativdaten. Regionen können Varianten besitzen; keine Region muss identisch erneut erscheinen.
 
`[EXT]` Vorgeschlagenes Feld-Set je Region:
 
```cpp
struct RegionState
{
    FName        RegionId;
    ERegionArche Archetype;        // Biom-Archetyp (Abschnitt 9)
    Consistency  RegionConsistency;// 0..1
    float        ReconstructionLevel;
    int          CollapsePhase;    // 1..5
    TArray<EPhysicsField> Fields;  // dominant + sekundär
    float        AnomalyDensity;   // steigt zum Ursprung
    int          DistanceToWound;  // Graphdistanz (Kompass)
    FNarrativeField Narrative;     // Fragmente/Stimmen/Residuen
    TArray<FGraphEdge> Connections;
};
```
 
### 7.4 Persistenz & Streaming `[EXT]`
 
- **Streaming:** UE5 World Partition; eine zusammenhängende offene Welt ohne Ladebildschirme zwischen Regionen.
- **Mutable State Layer:** Alle Spielerveränderungen und Simulationsschritte werden pro Save als Delta auf der fixen Struktur gespeichert. Nichts regeneriert die globale Struktur neu.
- **Weltgröße `[TUNE]`:** dichte, bedeutungsvolle ~9–16 km² statt leerer Fläche (Säule „Welt braucht den Spieler nicht" ≠ Leere belohnen).
### 7.5 Die Weltuhr — 100 reale Tage `[KANON]`
 
Die Weltzeit läuft über **100 reale Tage pro Spielstand** und **läuft immer weiter, auch wenn das Spiel geschlossen ist** (C10). Sie treibt den Kollaps (6.6) und die globale Drift. Die Wunde suspendiert die Uhr, sobald sie vollständig erreicht ist (C13, Abschnitt 10/16).
 
`[EXT]` **Design-Konsequenzen & Schutzmechanik** (Details → `Gameplay Bible`/`Technical Bible`): Da die Uhr offline läuft, ist ein *Frustrationsschutz* nötig, damit Pausen den Spieler nicht bestrafen. Vorschläge: (a) Kollaps trifft primär *Weltzustand*, nie den Spielfortschritt/Save (C8); (b) optionaler, klar kommunizierter „langsamer" Realzeitfaktor plus stärkerer Vorlauf bei aktivem Spiel; (c) im Koop zählt die Uhr pro Save/Welt, nicht pro Spieler. Diese Parameter sind `[TUNE]`; die *Kanon-Tatsache* (Uhr läuft offline weiter) bleibt bestehen. Siehe Risiko R1 (Abschnitt 24).
 
---
 
## 8. Physikfelder
 
Physikfelder sind die **Grundlage aller Rätsel** (`GDD §11/§13`) und die mechanische Signatur jeder Region. `[KANON]` sind die neun Feldtypen und ihre Rolle als Rätselbasis; die konkreten Effekte/Regeln sind `[EXT]`-Vorschläge (finale Spezifikation → `Physics Bible`).
 
### 8.1 Die neun Felder `[KANON]` (Typen) / `[EXT]` (Effekte)
 
| Feld | Kanon-Name | Effekt (Vorschlag) | Typische Rätselnutzung |
|---|---|---|---|
| Persistenz | Persistenzfeld | Zustände/Bewegung bleiben erhalten (kein Energieverlust, Dinge „merken" sich Lage) | Zustände einfrieren/mitnehmen; Schalter halten |
| Stille | Stillfeld | Dämpfung: Klang, Kraft, Reaktion, Anomalien werden unterdrückt | Dissonanzen beruhigen; sichere Zonen; Akustikrätsel |
| Resonanz | Resonanzfeld | Schwingung/Frequenz wird übertragen und verstärkt | Frequenz-Tore; Strukturen anregen; Widerhall-Navigation |
| Inversion | Inversionsfeld | Kehrt eine Regel um (Gravitation, Ursache/Wirkung, oben/unten) | Umkehr-Traversal; invertierte Logikpfade |
| Spiegel | Spiegelfeld | Räumliche/Zustands-Spiegelung; Kopien mit vertauschter Chiralität | Spiegel-Symmetrie-Rätsel; „echtes vs. gespiegeltes" Objekt |
| Rekursion | Rekursionsfeld | Räume/Prozesse wiederholen sich selbstähnlich, geschachtelt | Schleifen erkennen/durchbrechen; Skalenrätsel |
| Kompression | Kompressionsfeld | Raum/Zeit/Objekt verdichtet; groß wird klein, langsam wird schnell | Verdichtete Passagen; Zeitraffer-Segmente |
| Expansion | Expansionsfeld | Raum/Zeit/Objekt dehnt sich; klein wird groß, schnell wird langsam | Distanzen dehnen; Zeitlupe für präzise Aktionen |
| Superposition | Superpositionsfeld | Mehrere Zustände existieren gleichzeitig bis „gelesen"/beobachtet | Zustands-Kollaps durch Beobachtung; Mehrdeutigkeitsrätsel |
 
### 8.2 Feldinteraktion & Eigenschaftstransport `[EXT]`
 
Der mechanische Kern (Abschnitt 13) ist, **Eigenschaften zwischen Regionen zu transportieren** (`GDD §13`) und **Felder zu kombinieren**:
 
- **Objekte können Feld-Eigenschaften aufnehmen** (z. B. ein Objekt „lädt" Persistenz und behält seinen Zustand, wenn es in ein anderes Feld getragen wird).
- **Rätsel entstehen aus Feldkombination.** Beispiele: Persistenz + Inversion (invertierten Zustand einfrieren und mitnehmen); Resonanz + Superposition (durch Anregung einen von mehreren Überlagerungszuständen fixieren); Kompression + Expansion (Distanz-/Größenketten); Spiegel + Rekursion (die „echte" Instanz in einer geschachtelten Spiegelung finden).
- **Feldkanten sind gefährlich und wertvoll.** Scharfe Übergänge sind Fracture-Time-Hotspots (Abschnitt 14) und Dissonanz-Habitate (Abschnitt 12).
- **Superposition + Beobachtung** ist der thematisch wichtigste Fall: „Beobachten" (Aufmerksamkeit) ist zugleich Spielverb und Motiv (Determinismus/Wissen). Beobachtung kollabiert Überlagerung zu einem festen Zustand — spielbar gemachte Kernmetapher.
---
 
## 9. Regionen & Biome
 
`[KANON]` Regionen sind aus Physik + Biom + Konsistenz + Rekonstruktions-/Kollapsgrad + Narrativ zusammengesetzt, variabel angeordnet, mit Varianten. Die folgenden **sechs Biom-Archetypen** stammen aus dem projekteigenen früheren Voll-GDD (`old/`) und werden hier als `[EXT]` Archetypen ausgearbeitet — umbenennbar/erweiterbar, finale Spezifikation → `Region Bible`. Jeder Archetyp obeys strikt C1 (nichts Bekanntes) und C2 (glaubwürdige Physik) und ist über ein dominantes Physikfeld an den mechanischen Kern gebunden.
 
Je Biom: dominantes Feld · Konsistenzprofil · Gelände/Material · Licht · Kreaturen/NPCs · Dissonanzschwerpunkt · Anomalie-Schwerpunkt · Traversal · Gefahr · Audio-Hook · Story-Beat.
 
### 9.1 Lichtwurzelwald `[EXT]`
 
- **Dominantes Feld:** Persistenz (sekundär Resonanz).
- **Konsistenzprofil:** Stable→Highly Stable (0.6–0.9). Häufiger Einstiegs-/Ankerraum.
- **Gelände/Material:** Wälder aus lichtleitenden „Wurzeln"/Filamenten, die Helligkeit wie Flüssigkeit speichern und weitergeben; glaubwürdige Botanik-Analogie ohne bekannte Pflanzen (C1).
- **Licht:** von innen leuchtende Strukturen; Persistenz lässt Lichtzustände „stehen bleiben".
- **Kreaturen/NPCs:** ruhige, sesshafte Lebensformen; erste NPC-Netzwerke, die den Titel erkennen.
- **Dissonanzen:** selten, meist *Echoform* (Abschnitt 12).
- **Anomalie:** Memory/Identity (leichte Doppelungen, zurückkehrende Fragmente).
- **Traversal:** offen, ruhig, lehrreich; hier lernt der Spieler „Beobachten" und „Eigenschaft mitnehmen" ohne Tutorial.
- **Gefahr:** gering; ideale Lernregion.
- **Audio-Hook:** tragende, warme Drones; Licht „klingt".
- **Story-Beat:** ein Wurzelknoten, der eine Bewegung endlos konserviert (Persistenz) — die erste stille Aussage über Erinnerung, die nicht vergehen will.
### 9.2 Fasermeer `[EXT]`
 
- **Dominantes Feld:** Expansion (sekundär Kompression).
- **Konsistenzprofil:** Unstable→Stable (0.4–0.7), stark ortsabhängig.
- **Gelände/Material:** weite „Meere" aus schwingenden Fasern/Fäden statt Wasser; Distanzen dehnen und stauchen sich je nach lokalem Feld.
- **Licht:** diffus, streuend an Millionen Fäden; Tiefe schwer einschätzbar (bewusst).
- **Kreaturen/NPCs:** wandernde, schwarmartige fremde Biologie.
- **Dissonanzen:** *Restform*, *Hohlwesen*.
- **Anomalie:** Geometry/Physics (Distanz-/Größenbrüche).
- **Traversal:** Distanz-Management; Expansion/Kompression zum Überbrücken nutzen.
- **Gefahr:** Verirren; Fehleinschätzung von Reichweiten.
- **Audio-Hook:** rauschende, atmende Flächen; Doppler-artige Effekte bei Feldwechseln.
- **Story-Beat:** ein Ziel, das mit jedem Schritt weiter entfernt scheint (Expansion) — bis der Spieler lernt, das Feld statt der Distanz zu bearbeiten.
### 9.3 Kristallsenken `[EXT]`
 
- **Dominantes Feld:** Spiegel (sekundär Persistenz).
- **Konsistenzprofil:** Highly Stable (0.8–0.95) — „zu" konsistent, unheimlich klar.
- **Gelände/Material:** kristalline, exakte Senken; makellose Flächen; strikte, schöne Optik/Physik (Kaustiken, Brechung) — der „photorealistischste" Ort (Beweis der Säule „real trotz irreal").
- **Licht:** präzise, physikalisch korrekt; Spiegelungen tragen Information.
- **Kreaturen/NPCs:** kaum; vereinzelte Residuen wie Monumente.
- **Dissonanzen:** selten, aber heftig (*Bruchform*); die Region „will" Widersprüche schnell auflösen → erhöhtes Memory-Shift-Risiko.
- **Anomalie:** Identity/Geometry (Spiegel-Paradoxa).
- **Traversal:** Präzisions-/Spiegelrätsel; die echte Instanz von der gespiegelten unterscheiden.
- **Gefahr:** Widerspruchs-Kollaps bei Fehlern.
- **Audio-Hook:** reine, gehaltene Harmonik; klarster Mix des Spiels.
- **Story-Beat:** eine Spiegelung, die eine Handlung *vorwegnimmt*, die dann exakt so eintritt — der Determinismus (3.3) blitzt auf, nie benannt.
### 9.4 Resonanzriffe `[EXT]`
 
- **Dominantes Feld:** Resonanz (sekundär Stille).
- **Konsistenzprofil:** Stable (0.55–0.8).
- **Gelände/Material:** riffartige, auf Frequenzen gestimmte Strukturen; Membranen und Kanäle; ein schallleitendes Medium mit sichtbaren Wellen. FMOD-Schaufenster (Abschnitt 20).
- **Licht:** gedämpft; Navigation ebenso über Gehör wie über Sicht (Barrierefreiheit → Abschnitt 21).
- **Kreaturen/NPCs:** stehende-Welle-Lebensformen; *Echos* speichern vergangene Klänge.
- **Dissonanzen:** *Echoform* nativ.
- **Anomalie:** Memory/Time (akustische Persistenz).
- **Traversal:** klang-gated — richtige Frequenz öffnet Membranen; Rätsel im Audiodomäne.
- **Gefahr:** destruktive Interferenz kann Kammern einstürzen lassen (physikalisch glaubwürdig → Relokation).
- **Audio-Hook:** die ganze Region als adaptives Instrument.
- **Story-Beat:** ein Echo, das — voll angeregt — ein Fragment der „Entscheidung zu vergessen" als reinen Klang/Bild abspielt, nie als Worte (C1, 5.1).
### 9.5 Schwebende Adern `[EXT]`
 
- **Dominantes Feld:** Inversion (sekundär Superposition).
- **Konsistenzprofil:** Unstable (0.3–0.55), driftend.
- **Gelände/Material:** schwebende, aderartige Bahnen in invertierter Gravitation; „oben" und „unten" sind lokal verhandelbar; global unmöglich, lokal konsistent (C2).
- **Licht:** pro Inversionszelle wechselnd; Schatten fallen „falsch".
- **Kreaturen/NPCs:** an Inversion angepasste fremde Biologie.
- **Dissonanzen:** *Rekursion*, *Bruchform*.
- **Anomalie:** Physics/Geometry/Time — dichteste **Fracture-Time-Hotspots** an Inversionskanten (Abschnitt 14).
- **Traversal:** Kern der Bewegungsrätsel; Gravitationsrichtung als Ressource.
- **Gefahr:** „nach vorn gefaltet" werden — eine Kante kann einen Fracture-Time-Sprung auslösen (nur Zukunft, C11).
- **Audio-Hook:** binaural verwirrend; Klang aus geometrisch falschen Richtungen.
- **Story-Beat:** eine Ader, die korrekt „gelesen" (Superposition) zu einem geraden Pfad kollabiert — die Welt „erinnert" kurz ihre wahre Form, bevor sie erneut driftet.
### 9.6 Nebelkolonien `[EXT]`
 
- **Dominantes Feld:** Superposition (sekundär Rekursion/Stille).
- **Konsistenzprofil:** Critical→Unstable (0.15–0.45) — nahe der Auflösung; oft nahe dem Ursprung.
- **Gelände/Material:** Kolonien im dichten Nebel, die in mehreren Zuständen zugleich existieren, bis Beobachtung sie fixiert; Wiederholungs-/Füllmuster, wo Information ausgeht.
- **Licht:** flach, streuend, richtungslos — die Welt hat „vergessen", wo das Licht war.
- **Kreaturen/NPCs:** halb-ausgelöschte Formen; dichteste Rekonstruktions-/Varianten-Zone.
- **Dissonanzen:** *Hohlwesen*, *Fragmentkoloss* (nahe Ursprung).
- **Anomalie:** alle fünf Typen, hohe Dichte — starker Kompass Richtung Wunde.
- **Traversal:** Beobachtung stabilisiert Pfade; Superposition kollabieren, um Wege zu fixieren.
- **Gefahr:** höchster ambienter Memory-Shift-Druck außerhalb der Wunde; zu langes Verweilen im Füll-Nebel erzwingt einen Shift.
- **Audio-Hook:** hörbares „Ausdünnen" — Instrumente fallen einzeln aus dem Mix bis zur Stille.
- **Story-Beat:** der Spieler kann ein einzelnes Fragment *festhalten*, während alles ringsum vergessen wird — Vorschein der Persistenz-Geste (Ende B).
### 9.7 Regionsvarianten & Rekonstruktions-Look `[EXT]`
 
Da Regionen Varianten haben (C9) und Rekonstruktion nie perfekt ist (C18), sollte jedes Biom mit **Konsistenz-abhängigen Sub-Looks** ausgestattet sein (Highly Stable → Critical): sinkende Konsistenz = Detailverlust, Wiederholungsmuster, Farb-/Klangdrainage, Identitätsfehler bei NPCs/Kreaturen. Das ist zugleich Art-Grammatik (Abschnitt 19) und Erzählkanal (5.1).
 
---
 
## 10. Die Wunde `[KANON]` / `[EXT]`
 
`[KANON]` **Interner Name: Die Wunde** (`REGION_WOUND`). Der Ort, an dem das Vergessen niemals vollständig gelungen ist. Sie ist **keine Festung und kein Bossgebiet**, sondern eine kosmische Verletzung der Realität. Eigenschaften: zeitlos, instabil, fragmentiert, kollabierend. Flags: `Required=true`, `Randomized=true` (Geometrie/Fragmente/visuelle Struktur variabel), `ConstantFunction=true` (Funktion/Bedeutung/Lore-Rolle konstant), `TimeEnabled=false`, `CollapseEnabled=false`, `AgingEnabled=false`.
 
`[KANON]` Die Wunde ist **Ursprung des Kollapses** (6.6), der von hier über den Graphen expandiert. **Beim vollständigen Erreichen der Wunde** stoppen Weltzeit, Alterung und Kollaps (`WoundReached=true`); der Spieler kann **unbegrenzt** verweilen; es gibt keine automatische Entscheidung.
 
`[EXT]` Design:
- **Ort & Zugang.** Vom Seed platziert; existiert von Beginn an, wird aber erst *erreichbar/nahbar*, wenn die Welt vergisst (Anomaliendichte/Kollaps öffnen Routen). Der Spieler kann früh mit hohem Aufwand hinstoßen oder die Uhr die Wege öffnen lassen.
- **Inneres.** Widerspruch zum Rest: wo die Welt Detail verliert, ist die Wunde *schmerzhaft vollständig* — die ursprüngliche Wahrheit blutet durch. Sie soll der realste und zugleich unerträglichste Ort sein. Determinismus wird als *totale Gleichzeitigkeit* (Vergangenheit/Gegenwart/Zukunft ko-präsent) erfahrbar, nie ausgesprochen.
- **Interaktionslogik** ist `[OFFEN]` (→ `Region Bible`): visuelle Sprache, Generatorregeln, exakte Enact-Interaktion der beiden Gesten (Abschnitt 17).
---
 
## 11. Kreaturen & NPCs
 
`[KANON]` Erlaubt sind fremde Biologie und nichtmenschliche Kulturformen; verboten sind Menschen, bekannte Tiere, bekannte Flora, klassische Fantasyrassen und bekannte Kulturen (C1). Kreaturen und NPC-Netzwerke sind variabler Designraum (pro Welt verschieden). Finale Spezifikation → `Creature Bible` und `NPC Bible`.
 
### 11.1 Kreaturen `[EXT]`
 
- **Fremde Biologie, glaubwürdige Ökologie.** Kreaturen sollen wie echte, an ihre Region angepasste Lebensformen wirken (C2): Fortbewegung, Ernährung/Energie, Reaktion auf Physikfelder. Keine „Monster als Gegner" — Kreaturen sind Weltbewohner, nicht Kampf-Futter.
- **Feld-Kopplung.** Jede Kreatur ist an ihr Biom-Feld angepasst (z. B. Resonanz-Kreaturen in Resonanzriffen, Inversions-Kreaturen in Schwebenden Adern). Das macht sie zu Rätsel- und Traversal-Elementen.
- **Konsistenz & Rekonstruktion.** Kreaturen tragen Konsistenzwerte (6.2). Bei niedriger Konsistenz sterben und erscheinen sie fehlerhaft rekonstruiert erneut („Wesen sterben und erscheinen erneut") → Varianten, Identitätsfehler, potenziell Dissonanzen (Abschnitt 12).
- **Verteilung** ist Generierungsdaten (7.2, Schicht 2/4), variabel pro Welt.
### 11.2 NPCs `[KANON]` / `[EXT]`
 
`[KANON]` NPC-Datenfelder: **Identität, Stabilität, Erinnerung(smatrix), Beziehungen**. NPCs können rekonstruiert werden → dadurch entstehen unterschiedliche Varianten derselben Existenz. Alle Wesen erkennen den Titel „Erinnerungsträger". NPC-Netzwerke sind variabel.
 
`[EXT]` Datenmodell-Vorschlag (→ `NPC Bible`):
 
```cpp
struct NpcState
{
    FName        Identity;        // stabile Kern-ID der "Existenz"
    Consistency  Stability;       // 0..1 (Stabilität)
    FMemoryMatrix Memory;         // getragene Erinnerungsfragmente
    TArray<FRelation> Relationships; // Netzwerk zu anderen NPCs
    int          ReconstructionVariant; // 0 = original, n = n-te Rekonstruktion
};
```
 
- **Rekonstruktion erzeugt Varianten, nicht Kopien.** Sinkt `Stability`, kann derselbe NPC als abweichende Variante wiederkehren (andere Erinnerungen, andere Beziehungen). Der Spieler begegnet „fast korrekten" Versionen bekannter Figuren.
- **Beziehungen als Netzwerk.** NPC-Netzwerke verändern sich durch Kollaps und Fracture Time (Beziehungen brechen/entstehen). Das ist Erzählkanal, kein Questgeber-System (C6).
- **Keine Questgeber, keine Marker.** NPCs geben keine Aufträge. Sie sind Weltzustand: Man liest an ihnen den Grad des Vergessens ab.
- **Stimmen.** NPC-Erinnerungen sind eine Quelle der „Stimmen" (5.1, `CLEAR.md`); Priorisierung/Arten → `Audio Bible` (`[OFFEN]`).
---
 
## 12. Dissonanzen (Gegner)
 
`[KANON]` **Dissonanzen sind keine Dämonen und keine klassische böse Fraktion.** Sie sind **Fehlrekonstruktionen mit unvereinbaren Informationszuständen** — Systemfehler der Realität. Sie reagieren auf Umgebungsphysik. Das Kampfsystem ist „anspruchsvoll" und physikgetrieben (`old/GDD §9`). Finale Klassenhierarchie, KI-Verhalten und Spawnregeln sind `[OFFEN]` (→ `Creature Bible`).
 
### 12.1 Kanon-Typen `[KANON]` (Namen) / `[EXT]` (Ausarbeitung)
 
| Typ | Wesen (Vorschlag) | Verhalten/„Überwindung" |
|---|---|---|
| **Echoform** | wiederholte Reste eines vergangenen Ereignisses/Klangs | läuft in Schleifen; über Stille-/Resonanzfelder auflösbar; nicht „töten", sondern *auflösen* |
| **Restform** | übrig gebliebene Teil-Existenz mit fehlender Information | instabil, aggressiv nur bei „Reizung" ihres Widerspruchs; durch Konsistenz-Angleichung neutralisierbar |
| **Hohlwesen** | Rekonstruktion mit fehlendem Kern (Identität leer) | „sucht" fehlende Information; gefährlich, wenn es Eigenschaften/Erinnerungen absorbiert; ablenkbar/entkoppelbar über Felder |
| **Rekursion** | selbstgeschachtelter Prozessfehler | vervielfältigt sich in Rekursionsfeldern; muss an der „Wurzel" der Schleife unterbrochen werden |
| **Fragmentkoloss** | große Aggregation vieler Fehlrekonstruktionen | Ursprungsnahe Bedrohung; besteht aus Teilfragmenten, die einzeln destabilisiert werden; Umgebungsphysik statt roher Gewalt |
| **Bruchform** | akute Realitätsbruchstelle (Fracture-nah) | erzeugt/triggert lokale Fracture-Effekte; „Überwindung" heißt oft Ausweichen/Stabilisieren statt Konfrontation |
 
### 12.2 Kampf- & Auflösungsphilosophie `[EXT]`
 
- **Physik statt Waffenarsenal.** „Kämpfen" heißt primär, Physikfelder und transportierte Eigenschaften gegen den Widerspruch einer Dissonanz einzusetzen (z. B. eine Echoform mit einem Stillfeld dämpfen; eine Rekursion mit einer Inversion an der Wurzel brechen). Klassische Waffen sind höchstens sekundär (Waffenanzahl/Werkzeugslots `[OFFEN]` → `Gameplay Bible`).
- **Auflösen, nicht besiegen.** Dissonanzen werden *aufgelöst/stabilisiert*, nicht „getötet". Das hält den Ton (kein Gut-gegen-Böse, C7) und stützt den Leitfilter (2.2).
- **Spawn/Dichte** korreliert mit niedriger Konsistenz und hohem `CollapseLevel`/`CollapsePhase` (6.6) und steigt zum Ursprung.
- **Memory Shift als Konsequenz.** Unterliegt der Spieler, folgt kein Game Over, sondern ein Memory Shift (Abschnitt 14).
---
 
## 13. Core Gameplay Loop & Spielverben
 
### 13.1 Kanon-Core-Loop `[KANON]`
 
1. Erkunden → 2. Regionen verstehen → 3. Physikregeln lernen → 4. Eigenschaften transportieren → 5. Dissonanzen überwinden → 6. Erinnerungsfragmente entdecken → 7. Richtung Ursprung reisen → 8. Rekonstruktionen beobachten → 9. Finale Region (Wunde) erreichen → 10. Endzustand auslösen.
### 13.2 Loop-Ebenen `[EXT]`
 
- **Moment-zu-Moment (Sekunden–Minuten):** beobachten (Superposition/Anomalien lesen), traversieren, Physikfeld nutzen, Eigenschaft aufnehmen/tragen, Dissonanz auflösen.
- **Session (Minuten–Stunde):** eine Region verstehen, ihre Feldkombinationen lösen, Fragmente sammeln, eine Verbindung zum nächsten (anomaliedichteren) Knoten öffnen.
- **Makro (über die 100 Tage):** dem steigenden Anomaliegradienten zum Ursprung folgen, während der Kollaps von der Wunde her entgegenkommt; schließlich die Wunde erreichen und eine Geste vollziehen.
### 13.3 Spielverben `[EXT]`
 
- **Beobachten (Aufmerksamkeit).** Kernverb: Zustände lesen und — in Superpositionsfeldern — durch Beobachtung fixieren. Thematisch = Determinismus/Wissen spielbar gemacht.
- **Eigenschaft transportieren.** Objekte nehmen Feld-Eigenschaften auf; der Spieler trägt sie sichtbar (physisches Inventar) zwischen Regionen, um Rätsel zu lösen (`GDD §13`).
- **Traversieren.** Bewegung, Klettern, Nutzung invertierter/komprimierter/expandierter Räume.
- **Auflösen (Dissonanzen).** Physikbasierte Konfrontation/Stabilisierung (Abschnitt 12).
- **Reisen zum Ursprung.** Anomaliendichte als Kompass (kein Marker).
- **Vollziehen (Finale).** Die beiden Gesten in der Wunde (Abschnitt 17).
### 13.4 Inventar & Ausrüstung `[KANON]` / `[OFFEN]`
 
`[KANON]` **Kein magisches Inventar.** Objekte existieren physisch, Transport erfolgt sichtbar, Ausrüstung wird am Körper getragen. `[OFFEN]` Traglastsystem, Werkzeugslots, Waffenanzahl (→ `Gameplay Bible`). `[EXT]` Empfehlung: begrenzte, sichtbare Traglast (Diegese vor Bequemlichkeit); Eigenschaften „gespeichert" in getragenen Objekten statt in abstrakten Slots.
 
### 13.5 Rätselsystem `[KANON]` / `[EXT]`
 
`[KANON]` Objekte können Eigenschaften übernehmen; Eigenschaften können zwischen Regionen transportiert werden; Rätsel entstehen aus der Kombination unterschiedlicher Physikfelder. `[EXT]` Rätselketten sind variabler Designraum (pro Welt generiert, 7.1). Designregel: Jedes Rätsel muss aus den *lesbaren Regeln* der beteiligten Felder lösbar sein — keine willkürlichen „Pixeljagden" (C2: nie beliebig).
 
---
 
## 14. Zeitsysteme & Tod (Memory Shift)
 
Es existieren **zwei Zeitsysteme gleichzeitig** (C10/C11).
 
### 14.1 System A — Weltzeit `[KANON]`
 
100 reale Tage pro Spielstand. Läuft permanent, auch bei geschlossenem Spiel. Treibt Kollaps (6.6) und globale Drift. Wird in der Wunde eingefroren (Abschnitt 10/16). Frustrationsschutz siehe 7.5 / R1.
 
### 14.2 System B — Fracture Time (Frakturzeit) `[KANON]` / `[EXT]`
 
`[KANON]` **Keine Region, kein Biom, kein Level — ein Zustandswechsel/Fehlerzustand.** Der Spieler springt **ausschließlich in die Zukunft**. `TimeOffset`: **1 Stunde bis mehrere Jahre**. Auswirkungen: RegionStates, NPCStates, ReconstructionStates, EcologyStates (Regionen, Beziehungen, Vegetation, Rekonstruktionen ändern sich). Die effektiv erlebte Zeit übersteigt die reale Weltzeit deutlich.
 
`[KANON]`-Begründung (aus `CLEAR_DEVELOPER`): Die Realität versucht ständig Informationen zu verwerfen; dadurch wird *Zukunft übersprungen*. Vergangenheit wird nicht erneut erzeugt → daher nur vorwärts. Das koppelt die Mechanik direkt an das Entwicklergeheimnis (feststehende, bereits existierende Zukunft; 3.3).
 
`[OFFEN]` konkrete Trigger, Häufigkeit, Maximalzahl pro Region (→ `World Generation Bible`). `[EXT]` Vorschläge: Trigger an scharfen Konsistenz-/Feldkanten (v. a. Schwebende Adern), durch bestimmte Rekonstruktionen, durch *Bruchform*-Dissonanzen; deutlich telegrafiert mit eigener audiovisueller Signatur, damit es nie wie ein Bug wirkt (es ist ein *gewollter* „Fehlerzustand"). Fortgeschrittene Spieler können Fracture Time gezielt nutzen, um zukünftige, erosionsbedingt erst dann sichtbare Weltzustände zu erreichen — irreversibel (nur Zukunft). Netzwerk-Determinismus im Koop ist Pflicht (Abschnitt 18).
 
### 14.3 Tod = Memory Shift `[KANON]`
 
**Kein Game Over, kein Respawn-Menü.** Tod erzeugt **Erinnerungsversatz (Memory Shift)**: Die Realität ordnet den Erinnerungsträger neu ein. Save und Spielfortschritt bleiben erhalten. Mögliche Resultate:
 
- gleiche Region, andere Zeitlage
- andere Region, gleiche Zeit
- andere Rekonstruktionsversion/-stufe
- andere lokale Weltvariante
`[KANON]` Ziel: Tod ist narrativ und systemisch *identisch* zu handhaben (immer derselbe Mechanismus), nicht als Bestrafung. Der Erinnerungsträger ist nicht endgültig löschbar (`DeleteAllowed=false`), **Ausnahme: der Transzendenz-Endzustand** (Abschnitt 17).
 
`[OFFEN]` exakte Spawnlogik, Verlust-Mechaniken, Frustrationsschutz (→ `Gameplay Bible`). `[EXT]` Empfehlung: Memory Shift soll gelegentlich sogar *nützlich* sein können (Zugang zu sonst schwer erreichbaren Zuständen), damit „Sterben" sich als Weltmechanik statt als Scheitern anfühlt.
 
---
 
## 15. Progression `[EXT]`
 
Es gibt **kein klassisches XP-/Level-/Skilltree-System** (widerspräche C6/C7). Fortschritt ist dreifach und primär *wissensbasiert* (→ Details `Gameplay Bible`):
 
- **Verständnis (der eigentliche Fortschritt).** Der Spieler akkumuliert Schlüsse über die Welt und die Erkenntnis. Dies ist der wahre Fortschrittsbogen (5.4) und emotional der Kern (Erlebnisziel 5).
- **Beherrschung von Feldern & Eigenschaften.** Der Spieler lernt, mehr Physikfelder zu lesen und zu kombinieren und Eigenschaften weiter/zuverlässiger zu transportieren. „Können" wächst als Repertoire, nicht als Zahl.
- **Zugang.** Gelöste Feldkombinationen, geöffnete Verbindungen und bestimmte Weltzustände erschließen neue Graphknoten Richtung Ursprung. Anomaliendichte ist dabei der Kompass (kein Marker, kein Questlog).
Designregel: Progression darf nie als UI-Zahl gefeiert werden; sie zeigt sich in *neuer Weltlesbarkeit* und *neuer Erreichbarkeit*.
 
---
 
## 16. Kollaps & Endphase `[KANON]` / `[EXT]`
 
### 16.1 Ablauf `[KANON]`
 
Der Kollaps beginnt an der Wunde und breitet sich graphbasiert über die Welt aus (6.6). Fortschreitende Weltzeit erhöht Anomalien, Rekonstruktionen, Physikfehler und Inkonsistenzen. Phasen je Region: `P1 Stable → P2 Distortion → P3 Reconstruction → P4 Fracture → P5 Collapse`. Ignoriert der Spieler den Ursprung, erreicht der Kollaps schließlich ihn. **Die Geschichte wartet nicht.**
 
### 16.2 Regionale Kollaps-Presets `[EXT]`
 
Jede Phase ist zugleich Simulationszustand und Art-/Audio-Preset (Abschnitte 19–20):
 
| Phase | Simulationswirkung | Wahrnehmung |
|---|---|---|
| P1 Stable | Konsistenz hoch, Anomalien selten | Region „gesund", klar |
| P2 Distortion | Konsistenz sinkt, kleine Anomalien | Details rutschen, Farben/Klang leicht falsch |
| P3 Reconstruction | Rekonstruktionen häufen sich, NPC-/Kreatur-Varianten | „falsche" Wiederkehr, Doppelungen |
| P4 Fracture | Fracture-Hotspots, starke Anomalien, Dissonanzen | Raum/Zeit brechen lokal auf |
| P5 Collapse | Region löst sich zur Füll-/Nebelstruktur auf | Auslöschung sichtbar |
 
### 16.3 Erreichen der Wunde & Freeze `[KANON]`
 
Beim vollständigen Erreichen der Wunde: `WoundReached=true`; Weltzeit-, Alterungs- und Kollaps-Freeze; unbegrenztes Verweilen; keine automatische Entscheidung. Ab hier ist der Spieler dem Uhr-Druck entzogen und kann beliebig lange mit der finalen Geste ringen.
 
`[OFFEN]` **Tag-100-Terminalzustand:** Was geschieht, wenn die Weltzeit 100 Tage erreicht, ohne dass die Wunde je erreicht wurde, ist im gesperrten Kanon nicht festgelegt (z. B. erzwungene Annäherung an die Wunde vs. automatisches Persistenz-Ende). Ein früher Entwurf schlug ein automatisches Persistenz-Ende vor — **nicht Kanon**. Entscheidung → `Narrative Bible` / `Gameplay Bible`.
 
---
 
## 17. Die Enden (nur durch Handlung)
 
### 17.1 Grundregel `[KANON]`
 
Es existieren ausschließlich zwei Endzustände: **Transzendenz** und **Persistenz**. Die finale Entscheidung erfolgt **ausschließlich durch Handlungen, niemals durch ein Menü oder Dialogoptionen**. Grund (`CLEAR_DEVELOPER`): Die Entscheidung muss emotional erfolgen, nicht spielmechanisch — der Spieler soll *handeln*, nicht *klicken*. Am Ende kehrt die Erinnerung fast vollständig zurück und wird direkt erlebt (kleine Lücken bleiben).
 
### 17.2 Transzendenz `[KANON]`
 
Der Erinnerungsträger lässt die letzte Erinnerung los. Die Wunde schließt sich. Die Realität gewinnt Ungewissheit zurück und regeneriert sich langsam. Der Erinnerungsträger verschwindet endgültig (`DeleteAllowed`-Ausnahme). Datenzustand: *Memory Removed · Wound Closed · Reality Reconstructed*.
 
### 17.3 Persistenz `[KANON]`
 
Der Erinnerungsträger hält an der Erinnerung fest. Die Wunde bleibt offen. Die Erkenntnis breitet sich erneut aus. Der Kollaps endet erst mit dem Ende aller Strukturen; die Realität kollabiert vollständig; am Ende verschwindet alles. Datenzustand: *Memory Retained · Wound Open · Reality Collapse Complete*.
 
### 17.4 Enactment-Design — wie ohne Menü `[EXT]`
 
Da es kein Auswahlmenü geben darf, muss das ganze Spiel die **zwei Gesten** lesbar aufbauen, damit das Finale als Handlung verständlich ist:
 
- **Die Geste des Loslassens (→ Transzendenz).** Über das Spiel verteilt lernt der Spieler eine Handlung des *Freigebens/Ablegens* (z. B. eine getragene Eigenschaft/Erinnerung bewusst in ein Stillfeld/eine Auflösung entlassen, statt sie zu halten). In der Wunde bedeutet Loslassen: die letzte getragene Erinnerung freigeben und aufhören, Konsistenz zu erzwingen.
- **Die Geste des Festhaltens (→ Persistenz).** Spiegelbildlich lernt der Spieler eine Handlung des *Haltens/Bewahrens* (z. B. ein Fragment gegen die Kollaps-/Nebelfront halten — vgl. Nebelkolonien 9.6). In der Wunde bedeutet Festhalten: die letzte Erinnerung bewahren und gegen das Schließen der Wunde stützen.
Beide Gesten werden früh und wiederholt in normalen Rätsel-/Weltkontexten trainiert (Foreshadowing in 9.1 Persistenz-Knoten, 9.6 Festhalten). Das Finale telegrafiert Konsequenzen ohne Text, rein über Weltreaktion. **Kein Timer** in der Wunde (16.3), damit die Geste ihr Gewicht behält. Exakte Interaktion/Inputs sind `[OFFEN]` (→ `Region Bible`/`Gameplay Bible`).
 
### 17.5 Koop-Enactment `[EXT]` / `[OFFEN]`
 
Da bis zu vier Manifestationen desselben Erinnerungsträgers existieren (18.1), braucht das Finale eine kollektive Enact-Regel (z. B. gemeinsame/gleichgerichtete Geste). Genaues Modell ist `[OFFEN]` (→ `Technical Bible`/`Narrative Bible`). Designleitplanke: keine „Abstimmung per Menü"; die kollektive Entscheidung muss ebenfalls als *gemeinsame Handlung* lesbar sein.
 
---
 
## 18. Multiplayer & Koop
 
### 18.1 Kanon `[KANON]`
 
1–4 Spieler; Solo, Lokaler Koop, Online Koop, Hybrid Koop. **Lore:** mehrere Manifestationen desselben Erinnerungsträgers werden gleichzeitig wahrgenommen. „Koop von Anfang an integriert" ist eine Kern-Säule (MDD Pillar 6) — kein nachträglicher Aufsatz.
 
### 18.2 Design-Konsequenzen `[EXT]`
 
- **Geteilter UniverseState.** Alle Manifestationen teilen dieselbe Welt/denselben `UniverseState` (dieselbe Erinnerung → dieselbe Realität). Konsistenz-, Kollaps-, Fracture- und Rekonstruktionszustände sind global konsistent zu replizieren.
- **Memory Shift im Koop.** Der Tod einer Manifestation ist ein Memory Shift, der sie räumlich/zeitlich neu einordnet — im Koop potenziell *weg von* der Gruppe (diegetisch stimmig). Wiederzusammenfinden ist Teil des Spiels.
- **Fracture Time im Koop.** Muss netzwerk-deterministisch sein (gleiche Trigger → gleicher Sprung), sonst zerfällt die geteilte Welt. Ob Fracture einzelne oder alle Manifestationen erfasst, ist `[OFFEN]` (Designvorschlag: welt-global, damit der geteilte Zustand erhalten bleibt).
- **Konsistenz-Reibung als Feature.** Widersprechen sich Manifestationen (z. B. gegensätzliche Eigenschaftstransporte), kann daraus emergente Anomalie-/Dissonanzspannung entstehen — thematisch passend, aber sorgfältig zu balancieren.
### 18.3 Netzwerkarchitektur `[OFFEN]` / `[EXT]`
 
`[OFFEN]` Hostmodell, Authoritymodell, Save-Ownership (→ `Technical Bible`). `[EXT]` Startannahmen: Server-autoritativ für die drei Write-Systeme (Collapse/Fracture/Reconstruction, 6.7); Dedicated Server vorbereitet; State-Replikation minimieren (`old/GDD §16`); ein Save „besitzt" die Welt, Gäste treten dieser Welt bei. Determinismus aus `WorldSeed` + autoritativer Simulationsreihenfolge.
 
---
 
## 19. Art Direction
 
### 19.1 Kanon `[KANON]`
 
Stil: **surreal-realistisch**. Grundregeln: keine Menschen, keine klassischen Fantasyvölker, keine bekannten Tiere, keine bekannte Flora (C1). Die Welt soll physisch glaubwürdig wirken, obwohl nichts darin real ist (C2). Regionen dürfen seltsam/surreal sein, aber niemals beliebig — jedes Element braucht interne Logik. Finale Spezifikation → `Art Bible`.
 
`[EXT]` Rendering-Basis (aus früherem Entwurf, **nicht Teil des gesperrten Kanons**): Nanite + Lumen. Finale Wahl der Rendering-Features → `Art Bible`.
 
### 19.2 Visuelle Grammatik der Konsistenz `[EXT]`
 
Die Konsistenz (6.2) ist die primäre visuelle Achse. Ein einheitliches, region-übergreifendes Look-Mapping macht Weltzustand *sichtbar lesbar*:
 
| Konsistenzband | Look |
|---|---|
| Highly Stable | volle Detaildichte, satte Materialien, korrekte Optik, stabile Formen |
| Stable | leichte Vereinfachung, minimale Drift |
| Unstable | Detailverlust, Farbentsättigung, Wiederholungsmuster, kleine Geometriefehler |
| Critical | Füll-/Platzhaltergeometrie, Ausbleichen zu Weiß, Identitätsfehler, Auflösung |
 
Kollapsphasen (16.2) und Anomalietypen (6.5) erhalten je eigene, wiedererkennbare visuelle Signaturen. Fracture Time bekommt eine **eigene, gewollt-„fehlerhafte" audiovisuelle Signatur** (nie wie ein Bug, immer wie ein *Zustand*).
 
### 19.3 Kamera & Lesbarkeit `[EXT]`
 
Third-Person-Kamera (C5). Bildkomposition muss Anomaliendichte und Feldgrenzen lesbar machen (der Spieler navigiert nach dem, was er *sieht*, nicht nach Markern). Silhouetten von Kreaturen/Dissonanzen müssen fremd, aber eindeutig unterscheidbar sein.
 
---
 
## 20. Audio Direction
 
### 20.1 Kanon `[KANON]`
 
Technologie: **FMOD Studio**. Audio ist ein **narratives Werkzeug**. Schwerpunkte: Erinnerungsfragmente, räumliche Stimmen, regionale Klangidentität, Anomalieaudio. Finale Spezifikation → `Audio Bible`.
 
### 20.2 Adaptives, konsistenzgetriebenes Audio `[EXT]`
 
- **Konsistenz mischt den Ton.** Sinkende Konsistenz dünnt den Mix aus (Instrumente fallen weg → Stille); Kollapsphasen (16.2) sind Audio-Presets.
- **Regionale Klangidentität.** Jedes Biom (Abschnitt 9) hat eine eigene klangliche Signatur; Resonanzriffe/Widerhall sind das FMOD-Schaufenster (klang-gated Traversal).
- **Stimmen.** Erinnerungsfragmente, Rekonstruktionsreste, lokale Realitätsartefakte, NPC-Erinnerungen (`CLEAR.md`). Nie ein sprechender Gott (C7), nie menschliche Sprache/Schrift als Lore-Träger (C1); Vermittlung über Klang, Motiv, räumliche Präsenz. Arten/Priorität `[OFFEN]` → `Audio Bible`.
- **Die Wunde / Zeitlosigkeit.** In der Wunde (zeitlos) verliert Audio zeitliche Marker (kein Puls/Takt, der „Zeit" suggeriert), um Zeitlosigkeit hörbar zu machen.
- **Anomalieaudio** je Typ (Memory/Time/Identity/Geometry/Physics) mit eigener Signatur, damit Gehör als Diagnosewerkzeug dient (auch Barrierefreiheit, 21).
---
 
## 21. UX, UI & Barrierefreiheit `[EXT]`
 
- **Diegetisch & minimal.** Keine Questmarker, kein Questlog, keine Minimap-Wegweiser, kein Ende-Auswahlmenü (C6/C14). Information kommt aus der Welt (Anomalien, Konsistenz-Look, Klang).
- **Physisches Inventar.** Getragene Objekte/Eigenschaften sind sichtbar am Körper (13.4), keine abstrakten Slots-Menüs, wo vermeidbar.
- **Onboarding ohne Tutorial.** Der Spieler startet ohne Intro/Erklärung (5.1); frühe Regionen (Lichtwurzelwald) lehren Verben durch Umgebungsdesign.
- **Barrierefreiheit — kritisch wegen audio-gated Content.** Da Teile der Navigation klangbasiert sind (Resonanzriffe), sind visuelle Alternativen für Audio-Hinweise Pflicht (sichtbare Resonanz-/Frequenzdarstellung), plus Untertitel/visuelle Cues für Stimmen. Umgekehrt visuelle Anomalien auch akustisch spiegeln. Weitere Standards: Kamera-/Bewegungskomfort, Farbfehlsichtigkeits-Modi (die Konsistenz-Farbgrammatik darf nicht allein auf Farbe beruhen — zusätzlich Detaildichte/Muster).
- **Frustrationsschutz** bei Memory Shift und offline laufender Uhr (7.5, 14.3) ist Teil der UX-Verantwortung.
---
 
## 22. Technische Architektur (Zusammenfassung → Technical Bible) `[KANON]` / `[EXT]`
 
`[KANON]` Engine: Unreal Engine 5. Sprachen: C++ + Blueprints. 3D: Blender. Audio: FMOD. Versionsverwaltung: Git/GitHub. Dokumentation: Obsidian. Alle Systeme **datengetrieben**. Finale Spezifikation → `Technical Bible` (noch zu erstellen).
 
`[EXT]` Architektur-Leitplanken:
 
- **Determinismus zuerst.** `WorldSeed`-getriebene, reproduzierbare Generierung und Simulation; nötig für „einmal generiert" (C9), Fracture-Reproduzierbarkeit (C11) und Koop.
- **C++ vs. Blueprint.** C++ für die deterministischen Kernsysteme (WorldGenerator, Collapse/Fracture/Reconstruction, Consistency, Save, Netzwerk-Authority). Blueprints für Content-Glue, Region-/Rätsel-Skripting, schnelles Iterieren.
- **Modulgrenzen = Systemzugriff (6.7).** Nur CollapseSystem/FractureSystem/ReconstructionSystem haben Write-Zugriff auf `UniverseState`/Konsistenz; WorldGenerator/NPC/Creature/Dialogue/Save/AI nur Read. Diese Grenze ist als Modul-/Interface-Design zu erzwingen.
- **Persistenz.** `UniverseState` + Region-Deltas + NPC/Kreatur-Zustände im Save; **Weltzeit läuft offline** → Zeit-Delta beim Laden auf Basis realer Uhr nachrechnen (mit Frustrationsschutz, R1). Manipulationssicherheit der Uhr beachten.
- **Streaming:** World Partition; datengetriebene Region-/Feld-/Anomalie-Tabellen (Data Tables/Assets).
- **Audio:** FMOD-Integration mit Parametern für Konsistenz, Kollapsphase, Anomalietyp, Region.
- **Netzwerk:** Server-autoritativ für Write-Systeme; Dedicated-Server-tauglich; minimierte State-Replikation (`old/GDD`).
---
 
## 23. Content-Umfang & Produktionsplan
 
### 23.1 Dokument-/Bible-Status `[KANON]`
 
Pflicht-Bibles laut `FULL_MDD` (Hierarchie in Abschnitt 0):
 
| # | Bible | Status |
|---|---|---|
| 01 | Universe Bible | ✅ FINAL/LOCKED |
| 02 | World Generation Bible | offen (nächster Schritt lt. Snapshots) |
| 03 | Region Bible | offen |
| 04 | Creature Bible | offen |
| 05 | NPC Bible | offen |
| 06 | Narrative Bible | offen (fixiert u. a. die *exakte* Erkenntnis) |
| 07 | Gameplay Bible | offen |
| 08 | Physics Bible | offen |
| 09 | Audio Bible | offen |
| 10 | Art Bible | offen |
| 11 | Technical Bible | offen |
| 12 | Production Bible | offen |
 
Dieses GDD nimmt Inhalte dieser Bibles als `[EXT]` vorweg; die finalen Bibles ersetzen/spezifizieren die jeweiligen `[EXT]`-Passagen.
 
### 23.2 Entwicklungsphasen (Director-Vorgabe) `[KANON]`
 
Phase 1 Repository validieren → Phase 2 fehlende Bibles → Phase 3 Technical Bible → Phase 4 UE5-Projektarchitektur → Phase 5 Kernsysteme → Phase 6 Weltgenerierung → Phase 7 Gameplay-Systeme → Phase 8 NPC-/Rekonstruktionssysteme → Phase 9 Audiosysteme → Phase 10 Alpha → Phase 11 Beta → Phase 12 automatisierte Tests → Phase 13 Human Review Build.
 
### 23.3 Realistische Scope-Einordnung `[EXT]`
 
Der Kanon beschreibt ein sehr großes Spiel. Um überhaupt zu einem *spielbaren* Zustand zu kommen, wird ein Vertical-Slice-first-Ansatz empfohlen (die Kanon-Konstanten bleiben unangetastet, nur der *Umfang* wird gestaffelt):
 
- **Vertical Slice (Kern-Beweis):** 1 Weltseed, 2–3 Biome (z. B. Lichtwurzelwald, Resonanzriffe, Nebelkolonien), 3–4 Physikfelder, Eigenschaftstransport, 1–2 Dissonanztypen, Memory Shift, ein erreichbarer Wunden-Prototyp mit *beiden* Gesten. Beweist den Loop (13) und den Ton (2.2).
- **Alpha:** alle 9 Felder, alle 6 Biome als Archetypen, Kollapsphasen P1–P5, Fracture Time, NPC-Rekonstruktion, Solo vollständig spielbar von Start bis Wunde.
- **Beta:** Koop 1–4, Balancing/Frustrationsschutz, Anomalie-/Rätselketten-Vielfalt, Audio-Adaptivität vollständig, Barrierefreiheit.
- **Human Review Build:** vollständiger Solo-Durchlauf möglich, automatisierte Tests grün (Determinismus, Save/Offline-Zeit, Memory-Shift-Integrität, Erreichbarkeit der Wunde), bereit für menschlichen Full-Playthrough.
**Ehrliche Anmerkung (`[EXT]`):** Ein vollständiges, in dieser Doku beschriebenes Open-World-Spiel ist ein sehr großes Vorhaben. Dieses GDD ist so gebaut, dass ein schrittweiser, kanontreuer Weg (Slice → Alpha → Beta → Review) existiert, selbst wenn Biom-/Content-Menge zunächst reduziert wird. Priorität hat immer der *lesbare Kern* (Konsistenz, Anomalie-Kompass, die zwei Gesten), nicht die Content-Masse.
 
---
 
## 24. Design-Risiken & offene Fragen
 
### 24.1 Kanonisch offene Fragen (aus `CLEAR.md`) `[OFFEN]`
 
| Thema | Status | Ziel-Bible |
|---|---|---|
| Exakte Formulierung der Erkenntnis | absichtlich offen (heavier-than-description) | Narrative Bible |
| Warum überlebte der Erinnerungsträger (Zufall/Notwendigkeit) | teils offen | Narrative Bible |
| Arten & Priorität der „Stimmen" | teils offen | Audio Bible |
| Memory-Shift: exakte Spawnlogik, Verlust, Frustrationsschutz | offen | Gameplay Bible |
| Fracture Time: Trigger, Häufigkeit, Max pro Region | offen | World Generation Bible |
| Regionen: Mindest-/Maximalzahl, Größenklassen | offen | World Generation Bible |
| Wunde: visuelle Sprache, Generatorregeln, Interaktionslogik | offen | Region Bible |
| Dissonanzen: Klassenhierarchie, KI, Spawnregeln | offen | Creature Bible |
| Koop: Host-/Authority-/Save-Ownership-Modell | offen | Technical Bible |
| Inventar: Traglast, Werkzeugslots, Waffenanzahl | offen | Gameplay Bible |
 
### 24.2 Produktions-/Designrisiken `[EXT]`
 
- **R1 — Offline laufende Echtzeituhr.** 100 reale Tage, die auch geschlossen weiterlaufen, können pausierende Spieler bestrafen und sind manipulierbar (Systemuhr). *Mitigation:* Kollaps trifft nur Weltzustand, nie Save/Fortschritt (C8); Frustrationsschutz-Parameter (7.5); serverseitige Zeit im Koop; klare Kommunikation. Kanon-Fakt bleibt, nur Tuning ist offen.
- **R2 — „Keine Quests/Marker" vs. Lesbarkeit.** Reine Anomalie-Navigation kann orientierungslos wirken. *Mitigation:* starke, konsistente Anomalie-/Konsistenz-Grammatik (19.2), verlässlicher Gradient zum Ursprung, Onboarding durch Umgebungsdesign (21).
- **R3 — Ende ohne Menü verständlich machen.** Spieler könnten das Finale „nicht finden". *Mitigation:* die zwei Gesten spielweit trainieren (17.4), Weltreaktion statt Text, kein Timer in der Wunde.
- **R4 — Kampf ohne klassische Gegner/Waffen.** „Anspruchsvolles" physikbasiertes Auflösen ist schwer zu balancieren. *Mitigation:* Dissonanzen an Feldlogik koppeln (12.2), früh in Rätseln einführen.
- **R5 — Koop-Determinismus.** Geteilter `UniverseState` + Fracture/Kollaps müssen deterministisch replizieren. *Mitigation:* Server-Authority für Write-Systeme (6.7/22), seed-basierte Simulation.
- **R6 — Determinismus als Twist statt Belastung.** Das Geheimnis darf nicht als „Aha-Twist" verpuffen. *Mitigation:* nie benennen (3.6), als Erfahrung/Belastung inszenieren; exakte Formulierung bewusst offen halten (Narrative Bible).
- **R7 — Scope.** Sehr großes Vorhaben. *Mitigation:* Vertical-Slice-first (23.3), Content-Menge staffeln, Kern-Konstanten schützen.
---
 
## 25. Anhang A — Glossar der Kanonbegriffe
 
| Begriff (DE) | Bedeutung / englischer Kanonterm |
|---|---|
| Erinnerungsträger | Spielerfigur; letzte vollständig konsistente Erinnerung; *Memory Bearer*; Klasse `MemoryBearer` |
| Die Erinnerung / Die Erkenntnis | die vergessene fundamentale Erkenntnis (keine Person/Wesen); Zustand via `MemoryIntegrity` |
| Konsistenz | quantifizierte Stabilität (0–1) von Regionen/NPCs/Kreaturen/Objekten/Erinnerungen; *Consistency* |
| Rekonstruktion | Ersatz verlorener Information durch beste (fehlerhafte) Annäherung der Realität |
| Dissonanz | Fehlrekonstruktion mit widersprüchlichem Informationszustand; Systemfehler (kein Dämon) |
| Anomalie | lokale Regelverletzung; Typen: Memory/Time/Identity/Geometry/Physics |
| Physikfeld | regionale Regel-Zone; 9 Typen (Abschnitt 8); Rätselbasis |
| Memory Shift | Erinnerungsversatz; Tod-Ersatz; Neu-Einordnung statt Game Over |
| Weltzeit | 100 reale Tage pro Save; läuft auch offline |
| Fracture Time | Frakturzeit; Fehlerzustand; Zeitsprung nur vorwärts (1 h – Jahre) |
| Kollaps | von der Wunde graphbasiert expandierender Zerfall; Phasen P1–P5 |
| Die Wunde | finale Region (`REGION_WOUND`); zeitlos; Ort unvollständigen Vergessens |
| Transzendenz | Ende A: loslassen → Wunde schließt → Realität regeneriert; Bearer verschwindet |
| Persistenz | Ende B: festhalten → Wunde offen → Realität kollabiert vollständig |
 
---
 
## 26. Anhang B — Namenskonventionen, Codenamen, Kanon-Datentypen `[EXT]` / `[KANON]`
 
- **Interne Codenamen (`[KANON]`):** „Die Wunde" (`REGION_WOUND`), „Erinnerungsträger" (Titel konstant, kein Eigenname).
- **Kanon-Konstanten (`[KANON]`):** `CONST_MEMORY_BEARER`, `CONST_MEMORY`, `CONST_WOUND`, `CONST_COLLAPSE`, `CONST_FINAL_REVELATION`, `CONST_END_TRANSCENDENCE`, `CONST_END_PERSISTENCE`.
- **Kanon-Datentypen (`[KANON]`):** `UniverseState` (6.1), `Consistency` (6.2), `enum EAnomaly {Memory,Time,Identity,Geometry,Physics}` (6.5), Kollapsphasen `P1..P5` (6.6).
- **`[EXT]`-Datentypen (Vorschlag):** `RegionState` (7.3), `NpcState` (11.2), `enum EPhysicsField` (die 9 Felder), `enum ERegionArche` (die 6 Biome).
- **Namenskonvention (`[EXT]`):** Kanon-Konstanten `CONST_*`, Universe-IDs `REGION_*`, Enums `E*`; deutsche Kanonbegriffe im Code als englische Symbolnamen mit Kommentar-Gloss (z. B. `MemoryBearer` // Erinnerungsträger).
---
 
## 27. Anhang C — Initiale Tuning-Tabellen `[TUNE]`
 
Alle Werte sind Startpunkte fürs Playtesting, keine finalen Konstanten.
 
| Parameter | Startwert | Notiz |
|---|---|---|
| Weltzeit gesamt | 100 reale Tage | Kanon-Fakt; Realzeitfaktor/Vorlauf tunebar (R1) |
| Konsistenzband-Grenzen | 0.20 / 0.50 / 0.80 | Kanon-Bänder (6.2) |
| Fracture `TimeOffset` | 1 h – mehrere Jahre | Kanon-Spanne; Verteilung tunebar |
| Anomaliedichte am Ursprung vs. Rand | ~5–10× | Gradient-Steilheit für Kompass-Lesbarkeit |
| Kollaps-Ausbreitung | 1 Graphkante / X Weltzeit-Einheiten | X tunebar; „Geschichte wartet nicht" |
| Memory-Shift-Reichweite | 0–3 Graphknoten | wie weit Neu-Einordnung streut |
| Traglast (physisches Inventar) | klein, sichtbar | Diegese vor Bequemlichkeit |
| Koop-Spielerzahl | 1–4 | Kanon |
| Vertical-Slice-Biome | 2–3 | Scope-Gate (23.3) |
 
---
 
## Änderungsprotokoll (Changelog)
 
| Version | Datum | Änderung |
|---|---|---|
| v1.0 | (Repo) | Ursprüngliches, knappes GDD (Kanon-Skelett). |
| v2.0 | 2026-07-20 | Vollständige, entwicklerfertige Konsolidierung des gesamten Repo-Kanons (MDD, FULL_MDD, Universe Bible, CLEAR/CLEAR_DEVELOPER, Snapshots, old/). Ergänzt Simulationsmodell (UniverseState/Konsistenz/Rekonstruktion/Anomalie/Kollaps), 9 Physikfelder, 6 Biom-Archetypen, Dissonanz-Ausarbeitung, Zeit-/Tod-/Koop-/Ende-Design, Art/Audio/UX/Tech/Produktion, Risiken und kanonische offene Fragen. CANON/EXT/TUNE/OFFEN durchgängig markiert. |
 
> **Kanon-Disziplin:** Bei jeder künftigen Änderung gilt — `[KANON]` nur mit ausdrücklicher Kanon-Revision ändern; `[EXT]` wird durch die finalen Bibles ersetzt; nach jeder Implementierungsänderung Doku synchronisieren (Director-Vorgabe). Der `requirements/`-Ordner bleibt unverändert.
 
*Ende des Dokuments.*
