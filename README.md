# LOST ATLAS 1.0 — Anleitung für Einsteiger

Eine **funktionierende, installierbare Progressive Web App (PWA)** ohne Build-Schritt und ohne Kostenpflicht für eine Datenbank.

## Funktionen

- Interaktive Leaflet/OpenStreetMap-Karte, eigene Orte und Koordinaten
- Historische Steckbriefe, eigene Bilder, freie Quellen-URLs
- Expeditionstagebuch mit Datum, Text und eigenen Bildern
- Routenliste mit Sortierung und Übergabe an Google Maps **nur für Anfahrt zwischen öffentlichen Zielpunkten**
- Vier Zugangskategorien (öffentlich, Führung/Erlaubnis, ungeklärt, nicht betreten)
- Speichern über IndexedDB auf dem aktuellen Gerät/Browser, JSON-Export und -Import
- PWA-App-Symbol und Service Worker für App-Dateien (Kartenkacheln offline **nicht** garantiert)

### Wichtige Grenzen

1. **Kein Onlinekonto und keine Synchronisation.** Notizen/Fotos liegen im jeweiligen Browser auf dem Gerät und können beim Löschen von Websitedaten verschwinden. Regelmäßig `Mehr > JSON-Backup exportieren` verwenden und die Datei in der Dateien-App/iCloud Drive speichern. Browserdaten sind kein verschlüsselter Tresor. Wer Zugriff auf dein entsperrtes Gerät/Browserprofil hat, kann sie ggf. lesen.
2. **Kein Sicherheits- oder Zugangsnachweis.** Demostatus sind redaktionelle Kategorien, müssen vor Besuch beim Betreiber aktuell kontrolliert werden. Die Kartenroute zeigt keine legalen Fußwege durch Gelände an.
3. **Keine echten historischen Fotos ab Werk.** Lade eigene Bilder hoch oder ergänze die Quellen. Bilder und Ortsangaben aus fremden Quellen nur mit Nutzungsrecht übernehmen.
4. **Kartennutzung benötigt online Kartenkacheln** und Leaflet wird beim ersten Besuch über einen CDN geladen. Die Basis-App kann nach dem ersten Onlinebesuch offline starten, aber die Karte braucht i.d.R. Internet.
5. OpenStreetMap benötigt sichtbar eingeblendete Attribution; bei stärkerer Nutzung ggf. geeigneten Kartenanbieter einsetzen und Nutzungsbedingungen beachten.
6. Die Startkoordinaten sind ungefähre Kartenpositionen für öffentliche Ausgangspunkte, keine Zugangs- oder Grenzangaben.

## Am einfachsten: Veröffentlichung via GitHub Pages

GitHub Pages ist ein statisches Website-Hosting; für diese Version wird **kein eigener Server** benötigt.

1. GitHub-Konto unter https://github.com registrieren/anmelden.
2. Neues Repository erstellen: `lost-atlas` (für kostenlose Pages-Nutzung am einfachsten **Public**). **ACHTUNG:** Alle Dateien eines öffentlichen Repositories sind öffentlich. Keine privaten Notizen oder Fotos in das Repository hochladen; diese werden nur in der laufenden App lokal erzeugt.
3. Das ZIP entpacken und **den INHALT des Ordners** `lost-atlas-1.0` hochladen: `index.html`, `app.js`, `styles.css`, `sw.js`, `manifest.webmanifest`, Verzeichnis `icons/`, `README.md`. Auf GitHub: `Add file` > `Upload files` > `Commit changes`. Falls dein iPhone das Hochladen eines ganzen Ordners erschwert, nutze einmal einen PC/Mac oder die GitHub-Desktop-Alternative.
4. Im Repository `Settings` > `Pages` > `Build and deployment`: `Deploy from a branch`, Branch `main`, Ordner `/(root)`, anschließend `Save`.
5. Nach Veröffentlichung erscheint die Adresse gewöhnlich unter `https://DEIN-NAME.github.io/lost-atlas/`. Verwende die in `Pages` tatsächlich angezeigte URL.
6. In Safari am iPhone URL öffnen > Teilen > `Zum Home-Bildschirm` > `Hinzufügen`.
7. Neuen Beispielort anlegen, ein Journal-Foto speichern, App schließen und wieder öffnen, dann Backup exportieren.

Alternative ohne GitHub: Ein Webhoster mit statischem Hosting und **HTTPS**; alle Projektdateien unverändert in einen Webordner hochladen.

## Entwicklung am Rechner

Mit Python (falls installiert) im Projektordner: `python -m http.server 8080`. Dann am Rechner `http://localhost:8080` öffnen. **Nicht direkt per Doppelklick auf index.html starten**, da PWA-Service-Worker und Browser-Speicher dabei anders funktionieren können.

## Mit Codex erweitern

1. Repository mit Codex verbinden bzw. Projekt in Codex öffnen.
2. Beispiel-Auftrag: „Erweitere Lost Atlas um eine Galerie mit mehreren Fotos pro Ort, Datenvalidierung und Tests. Bewahre vorhandene Datensätze/Exportformat und den PWA-Offline-Start. Ändere nur nötige Dateien. Erkläre jede Änderung laienverständlich und teste die App.“
3. Änderungen prüfen und in `main` übernehmen. Pages veröffentlicht die neue Version.
4. Vor jeder größeren Erweiterung ein JSON-Backup anlegen. Bei Änderungen am Service Worker die CACHE-Version anheben.

## Aufbau

- `index.html`: Seitenstruktur
- `styles.css`: Design
- `app.js`: Karten-, Orts-, Journal-, Tour- und Speicherfunktionen
- `sw.js`: PWA-Offline-App-Shell
- `manifest.webmanifest` und `icons/`: Homescreen-App

## Datenschutz bei Veröffentlichung

Die App sendet Ortskoordinaten an externe Kartendienste zur Darstellung der Karte; die Routenübergabe öffnet Google Maps. IP-Adresse und Nutzungsdaten können diesen Diensten zugänglich sein. Es gibt keine eigene Analytics-/Tracking-Integration. Bei **öffentlicher Bereitstellung** sind Datenschutzhinweise und ggf. rechtliche Pflichtangaben je nach Nutzung zu prüfen. Verwende zur Entwicklung nur nicht vertrauliche Daten.
