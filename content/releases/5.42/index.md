---
menu:
  main:
    name: "5.42"
    identifier: "5.42"
    parent: "releases"
    weight: -542
---

> * Dieses Update erfordert einen Re-Index, planen Sie entsprechende Downtime / Updatezeit ein.
> * Durch eine Fehlerbehebung bei der Interpretion von `Standard` in Mehrfachfeldern kann es bei Feldern mit demselben Namen (z.B. "titel" und "zusaetzliche__titel.titel") zu Problemen kommen. Überprüfen Sie die Maskeneinstellungen für `Standard`.
> * Dieses Release hat aktuell ein Problem mit Download + Export bei aktivierten Connector-Instanzen. Für Download + Export deaktivieren Sie die Connector-Instanzen (auf Ebene des Benutzers).

# Version 5.42.1

*Veröffentlicht am 01.11.2018*

### Webfrontend

*Behoben*

* Das Speichern von neuen Objekten nach dem Hochladen wurde behoben.

# Version 5.42.0

*Veröffentlicht am 31.10.2018*

### Webfrontend

*Neu*

* Hochladen-Menü bei Rechtsklick und als Favorit für Mappen.
* Exporter: Eine neue Funktion ermöglicht das Auswählen eigener Masken je exportiertem Objekttyp. Bei Exporten kann dadurch die easydb-seitige Auswahl der besten Maske überschrieben werden.

*Verbessert*

* Anzeige von Mehrsprachigkeit: Im Editor und Detail werden grundsätzlich alle gesetzten Sprachen angezeigt. Die Einstellung des Benutzers zur Datensprache bestimmen die Eingabesprachen der Editoren die mindestens sichtbar sind.
* Exporter: Dialog öffnet sich schneller, in einigen Fällen wurden viel zu viel Daten vom Server geladen.
* Entwickler: Im Debug-Modus werden keine Session-Cookies vom Server gesetzt und überprüft. Das vereinfacht in Chrome den Request komplett im CURL-Format zu kopieren.
* Datenmodell: Das Laden von defekten Datenmodellen führt nicht mehr zu einem Absturz, sondern erlaubt es das wenigstens das defekte Datenmodell zu verwerfen.
* Datenmodell: Vergrößerte und informativere Anzeige von Informationen in der Übersicht.
* CUI: Korrektes Berechnen von Anzeige-Positionen auch wenn `margin` und ` border` für den `BODY` verwendet werden. Das betrifft die Verwendung von easydb mit eigenem CSS.
* Kleine Suchen und Editoren haben eine Vollbild-Funktion.
* Verbessertes Design von Ausdrucken.
* Pools: Anzeige im Administrationsbereich wurde dadurch beschleunigt, dass wir nur noch die erste Kinderebene automatisch öffnen.
* CSV-Importer: Mehr Informationen in der Log-Datei.

*Behoben*

* Suche: Verbessertes Setzen des Cursor beim Filtern in der Schnellanzeige.
* Basis-Konfiguration: Korrektes setzen der minimalen Anzeige von Listenelementen (wie beispielweise Sprachen).
* Suche: Korrigierte Anzeige von verlinkten Bildern aus anderen Objekttypen in der Text-Ansicht.
* CSV-Importer: Fehlerhaftes Importieren von verlinkten Objekten wurde behoben.
* Präsentation: Export von PPTX von ungespeicherten Änderungen wurde behoben.
* Anzeige eines Menüs für Dateien in Reverse-Nested-Objekten wurde behoben.
* Die Anzeige von mehr als 1000 Mappen eines Benutzers ist jetzt möglich.
* Datenmodell: Unterstützung von UNIQUE für Custom-Data-Types wurde behoben.


### Server

*Neu*

* Anmelden an einen normalen Benutzeraccount mit den Zugangsdaten eines admistrativen Accounts ermöglicht.
* Suche nach Asset-Status ermöglicht.
* Sprachen für den Suggest-Index sind nun in der Basiskonfiguration auswählbar.

*Verbessert*

* Aggregationen für Mehrfachfelder ermöglicht, die "Nested Index" in den Maskeneinstellungen aktiviert haben.
* Verbesserung für `/api/suggest`, keine mehrfachen Vorschläge.
* Verwendung von Custom-Data-Type-Feldern im Gruppeneditor ermöglicht.

*Behoben*

* Fehler beim Ändern von aus easydb-4 migrierten Passwörtern behoben.
* Fehler bei Erzeugung von `_standard` korrigiert, wenn Felder auf verschiedenen Ebenen den selben Namen hatten.
* Indizierung von `message`-Objekten wird vorgezogen, um Nutzerbenachrichtigung bei Neuindizierung zu verbessern.
* Verbesserte Fehlerbehandlung (Collections, gespeicherte Suchen).

### Fylr

*Verbessert*

* Zip: Überprüfung von URLs vor der Komprimierung, um die Fehlerbehandlung zu verbessern.
* Design der Fehlerseite verbessert.
