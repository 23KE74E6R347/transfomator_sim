# Transformator – virtuelle Untersuchung

Interaktive HTML/JavaScript-Simulation für den Physikunterricht am Beruflichen Gymnasium.

## Zweck

Die Simulation ersetzt bzw. ergänzt einen nicht ausreichend funktionierenden Realversuch. Sie ermöglicht eine kontrollierte Untersuchung von Abhängigkeiten eines idealen und eines bewusst vereinfachten realen Transformators.

Der didaktische Arbeitsweg lautet:

**Vorhersage → Parameter gezielt verändern → beobachten → Messwerte aufnehmen → Zusammenhang erklären → Modellgrenzen reflektieren**

Die Simulation soll damit nicht nur eine Animation sein, sondern eine virtuelle experimentelle Situation schaffen.

## Funktionen

- Wechselspannung / Gleichspannung
- Primärspannung U₁
- Primärwindungszahl N₁
- Sekundärwindungszahl N₂
- Leerlauf / Belastung
- Lastwiderstand R
- Idealmodell
- vereinfachtes Realmodell
- Anzeige von U₁, U₂, I₁, I₂, P₁, P₂ und Wirkungsgrad η
- animierte Darstellung des zeitlich wechselnden magnetischen Flusses
- virtuelle Messreihe
- Untersuchungsaufträge
- separate Lehrkraftseite mit Erwartungsbild und Bewertungsraster

## Physikalisches Modell

### Idealmodell

Für Wechselspannung gilt:

`U₂ / U₁ = N₂ / N₁`

Unter Belastung gilt im idealen Modell:

`P₁ = P₂`

Daraus folgt:

`I₂ / I₁ = N₁ / N₂`

Im Leerlauf ist die Sekundärseite offen. Daher wird I₂ = 0 gesetzt, während U₂ weiterhin durch das Übersetzungsverhältnis bestimmt wird.

### Vereinfachtes Realmodell

Das Realmodell verwendet einen kleinen äquivalenten Sekundär-Innenwiderstand:

`r_int = 0,08 Ω`

Unter Last gilt im Modell:

`I₂ = U₂₀ / (R + r_int)`

`U₂ = I₂ · R`

Die Verlustleistung des äquivalenten Innenwiderstands ist:

`P_V = I₂² · r_int`

und:

`P₁ = P₂ + P_V`

Das Modell bildet ausdrücklich keinen vollständigen realen Transformator ab. Insbesondere werden Kernverluste, Streuinduktivität, magnetische Sättigung, Frequenzabhängigkeiten und ein detailliertes Wicklungsmodell nicht separat simuliert.

### Gleichspannung

Bei Gleichspannung wird im eingeschwungenen Zustand U₂ = 0 gesetzt. Ein möglicher kurzer Einschalttransient wird nicht simuliert.

## Messung

Mit **„Messwert aufnehmen“** wird der aktuelle Zustand als Messpunkt gespeichert. Gespeichert werden unter anderem:

- Versorgung: AC/DC
- Modell: ideal/real
- Lastzustand
- U₁
- N₁
- N₂
- R
- U₂
- I₂
- P₂
- η

Die Messwerte bleiben erhalten, wenn anschließend die Einstellungen verändert werden.

Für sinnvolle Messreihen sollte möglichst jeweils nur eine unabhängige Größe verändert werden.

## Lehrkraftseite

Die Lehrkraftfassung liegt unter `teacher.html`.

Sie enthält:

- fachliches Kernmodell
- Erwartungsbild für die Untersuchungsaufträge
- konkrete Erwartungswerte
- typische Schülerantworten
- Bewertungshinweise
- Modellgrenzen
- typische Fehlvorstellungen
- technisches Validierungsmodell

### Zugriffsschutz

Die aktuelle `teacher.html` verwendet einen **Client-seitigen Passwort-Gate mit AES-GCM-Verschlüsselung**:

- Lehrkraftinhalt liegt in der aktuellen Datei nicht im Klartext.
- Schlüsselableitung: PBKDF2 mit SHA-256 und 600.000 Iterationen.
- Verschlüsselung: AES-256-GCM.
- Salt und Initialisierungsvektor sind zufällig.
- Das Passwort wird nicht im Repository gespeichert.
- Die Seite ist zusätzlich mit `noindex,nofollow,noarchive` gekennzeichnet.

**Wichtige Sicherheitsgrenze:** Das ist bei einem öffentlichen GitHub-Pages-Repository kein vollwertiger serverseitiger Zugriffsschutz. Der Browser erhält den verschlüsselten Inhalt und führt die Entschlüsselung lokal aus. Außerdem enthalten frühere öffentliche Git-Commits die Lehrkraftseite noch im Klartext. Deshalb darf das Repository weiterhin nicht als Ort für hochvertrauliche Informationen betrachtet werden.

Für echten Zugriffsschutz sind weiterhin ein privates GitHub-Pages-Setup mit geeigneter GitHub-Enterprise-Konfiguration oder ein Authentifizierungs-Proxy wie Cloudflare Access die bessere Lösung.

Das aktuelle Passwort wird absichtlich **nicht** dokumentiert und muss separat an die berechtigte Lehrkraft übermittelt werden.

## Nutzung

Die öffentliche Simulation kann über GitHub Pages aufgerufen werden:

`https://23ke74e6r347.github.io/transfomator_sim/`

Die Lehrkraftseite liegt unter:

`https://23ke74e6r347.github.io/transfomator_sim/teacher.html`

## Entwicklung

- `index.html` – Schüler-/Simulationsseite
- `teacher.html` – Lehrkraft-/Erwartungsbild
- `README.md` – Projektdokumentation

Es werden keine externen JavaScript-Bibliotheken benötigt.

## Qualitäts- und Modellgrenzen

Die Simulation ist ein didaktisches Modell und kein technisches Simulationsprogramm für reale Transformatoren.

Vor dem Einsatz im Unterricht sollte insbesondere geprüft werden:

- Passung zur konkreten Unterrichtssequenz
- vorhandenes Vorwissen der Lerngruppe
- gewünschte Lernziele
- Modellannahmen
- konkrete Aufgabenstellung
- Funktionsfähigkeit auf den tatsächlich verwendeten Geräten
- Browser-/Displaydarstellung
- Rückbindung an den Realversuch

Die Lehrkraft bleibt für die endgültige fachliche und didaktische Verwendung verantwortlich.

## Lizenz / Nutzung

Für dieses Repository ist derzeit keine separate Open-Source-Lizenz festgelegt. Ohne LICENSE-Datei sollte der Code nicht automatisch als frei zur Weiterverwendung lizenziert betrachtet werden.

## Status

**Prototyp / Unterrichtsentwicklung**

Der Schwerpunkt liegt auf fachlicher und didaktischer Validierung, nicht auf einer vollständigen technischen Modellierung realer Transformatoren.