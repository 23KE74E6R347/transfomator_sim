# Transformator – virtuelle Untersuchung

Kleine, eigenständige HTML/JavaScript-Simulation für Lila.

Das Projekt ist nicht als allgemeines Softwareprojekt gedacht, sondern als konkrete Unterrichtshilfe für Lilas Transformator-Thema. Deshalb ist der Code absichtlich ohne Framework, ohne Build-System und ohne externe Bibliotheken gehalten: Datei öffnen, ändern, speichern, fertig. ^^

## Worum es geht

Die Simulation ersetzt bzw. ergänzt den misslungenen Realversuch. Sie soll nicht einfach einen hübschen Transformator anzeigen, sondern eine virtuelle Untersuchung ermöglichen:

**Vorhersagen → einstellen → beobachten → Messwert aufnehmen → Zusammenhang erklären → Modellgrenzen reflektieren**

Untersucht werden:

- Wechselspannung / Gleichspannung
- Primärspannung U₁
- Primärwindungszahl N₁
- Sekundärwindungszahl N₂
- unbelasteter / belasteter Transformator
- Lastwiderstand R
- Idealmodell / vereinfachtes Realmodell
- U₁, U₂, I₁, I₂, P₁, P₂ und η
- virtuelle Messreihe
- Untersuchungsaufträge A–F
- separater Lehrkraftbereich

## Dateien

### `index.html`

Die komplette Schüler-/Simulationsseite.

- HTML = Inhalt und Struktur
- CSS im `<style>)-Block = Aussehen
- JavaScript im `<script>)-Block = Interaktion und Modell

Die Datei ist absichtlich monolithisch. Lila muss also nicht erst irgendein Framework verstehen.

### `teacher.html`

Loginseite für den Lehrkraftbereich.

Der eigentliche Lehrkraftinhalt liegt verschlüsselt im `DATA)-Objekt.

Wichtig: Das ist bei einem öffentlichen GitHub-Pages-Projekt kein echter serverseitiger Geheimschutz. Der Browser bekommt den verschlüsselten Inhalt und den Code zur Entschlüsselung. Außerdem bleiben alte Git-Commits grundsätzlich in der Repository-Historie.

### `README.md`

Diese Erklärung. Also ungefähr die Gebrauchsanweisung für das Ding, falls Marv irgendwann vergessen hat, was er hier eigentlich gebaut hat. 😭

## Wie der Code kommentiert ist

Die Kommentare sind absichtlich eher so geschrieben, wie Marv technische Dinge direkt an Lila erklären würde: kurz, konkret, ein bisschen locker und mit gelegentlichem „warum ist das hier so?“.

Nicht:

> `// Initialisiert den Zustand der Anwendung.`

Sondern eher:

> `// Hier passiert die eigentliche Physik. Der Rest ist größtenteils Oberfläche.`

Die Idee dahinter: Lila soll Änderungen selbst vornehmen können, ohne dass der Code wie eine fremde Softwarebibliothek wirkt.

Ein paar harmlose Tippfehler in Kommentaren sind absichtlich eingebaut. Das sind keine Syntax- oder Logikfehler und ändern nichts an der Funktion. 😅

## Wo Lila zuerst suchen sollte

- **Startwerte der Regler:** im HTML-Abschnitt bei `value=`
- **Physikalisches Modell:** `function values()`
- **Anzeige aktualisieren:** `function update()`
- **Transformatorzeichnung:** `function draw()`
- **Messreihe:** `function renderRows()`
- **Animation:** `function animate()`
- **Lehrkraft-Login:** `function openTeacher()`

Wenn ein Button anders reagieren soll, zuerst bei den `.onclick`-Zeilen schauen.

## Physikalisches Modell

### Idealmodell

Für Wechselspannung:

`U₂ / U₁ = N₂ / N₁`

Unter Belastung:

`P₁ = P₂`

Daraus:

`I₂ / I₁ = N₁ / N₂`

Im Leerlauf ist die Sekundärseite offen. Deshalb wird `I₂ = 0` gesetzt, während `U₂` weiterhin über das Übersetzungsverhältnis bestimmt wird.

### Vereinfachtes Realmodell

Das Realmodell besitzt einen kleinen äquivalenten Sekundär-Innenwiderstand:

`r_int = 0,08 Ω`

Unter Last:

`I₂ = U₂₀ / (R + r_int)`

`U₂ = I₂ · R`

`P_V = I₂² · r_int`

`P₁ = P₂ + P_V`

Das ist ausdrücklich kein vollständiges Modell eines realen Transformators. Kernverluste, Streuinduktivität, magnetische Sättigung, Frequenzabhängigkeiten und ein detailliertes Wicklungsmodell werden nicht separat simuliert.

### Gleichspannung

Bei Gleichspannung wird im eingeschwungenen Zustand `U₂ = 0` gesetzt. Ein kurzer Einschalttransient wird nicht simuliert.

## Entwicklung

Keine externen JavaScript-Bibliotheken, kein Framework, kein Build-Schritt.

Für Änderungen:

1. Datei öffnen.
2. Änderung machen.
3. Im Browser testen.
4. Auf GitHub committen.

Bei Änderungen an der Physik bitte nicht nur den angezeigten Wert ändern: Das Modell in `values()`, die Hinweise und die Lehrkraftfassung müssen zusammenpassen.

## Zugriff

GitHub Pages:

`https://23ke74e6r347.github.io/transfomator_sim/`

Lehrkraftbereich:

`https://23ke74e6r347.github.io/transfomator_sim/teacher.html`

## Qualitätscheck vor dem Unterricht

- Passt die Simulation zur konkreten Unterrichtssequenz?
- Sind Vorwissen und verwendete Begriffe klar?
- Ist sichtbar, was idealisiert wird?
- Wird „belastet“ so eingeführt, wie es im Unterricht gebraucht wird?
- Passen Untersuchungsaufträge und Erwartungsbild zusammen?
- Funktioniert die Darstellung auf den tatsächlich verwendeten Geräten?
- Kann die Simulation sinnvoll auf den Realversuch zurückbezogen werden?

Die Simulation soll den Realversuch nicht ersetzen, weil Simulationen „besser“ wären, sondern weil die kontrollierte Variation der relevanten Größen mit dem vorhandenen Aufbau nicht zuverlässig gelingt.

## Status

**Unterrichtsentwicklung / Lila**

Schwerpunkt: fachliche und didaktische Verwendbarkeit, nicht vollständige technische Modellierung realer Transformatoren.
