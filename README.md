# Transformator – virtuelle Untersuchung

Kleine, eigenständige HTML/JavaScript-Simulation für Lilas

Das Projekt ist als konkrete Unterrichtshilfe für Lilas Transformator-Thema gedacht. Deshalb ist der Code ohne Framework, ohne Build-System und ohne externe Bibliotheken gehalten: Datei öffnen, ändern, speichern, done

## Elemente

- Switch AC/DC
- Switch Modell
- Switch Last
- Primärspannung U₁ Regler
- Primärwindungszahl N₁ Regler
- Sekundärwindungszahl N₂ Regler
- Modellsimulation
- virtuelle Messreihe
- Untersuchungsaufträge A–F

## Dateien

### `index.html`

Die komplette Schülerseite

- HTML = Inhalt und Struktur
- CSS im `<style>)-Block = Aussehen
- JavaScript im `<script>)-Block = Interaktion und Modell

Die Datei ist absichtlich monolithisch. Lila muss also nicht erst irgendein Framework verstehen.

### `teacher.html`

Loginseite für den Lehrkraftbereich.

Der eigentliche Lehrkraftinhalt liegt verschlüsselt im `DATA)-Objekt.

Das ist bei einem öffentlichen GitHub-Pages-Projekt kein echter serverseitiger Schutz. Der Browser bekommt den verschlüsselten Inhalt und den Code zur Entschlüsselung. Außerdem bleiben alte Git-Commits grundsätzlich in der Repository-Historie.

### `README.md`

Diese Erklärung. Also ungefähr die Gebrauchsanweisung für das Ding, falls Marv irgendwann vergessen hat, was er hier eigentlich gebaut hat

## Wo Lila zuerst suchen sollte

- **Startwerte der Regler:** im HTML-Abschnitt bei `value=`
- **Physikalisches Modell:** `function values()`
- **Anzeige aktualisieren:** `function update()`
- **Transformatorzeichnung:** `function draw()`
- **Messreihe:** `function renderRows()`
- **Animation:** `function animate()`
- **Lehrkraft-Login:** `function openTeacher()`

## Zugriff

GitHub Pages:

`https://23ke74e6r347.github.io/transfomator_sim/`

Lehrkraftbereich:

`https://23ke74e6r347.github.io/transfomator_sim/teacher.html`
