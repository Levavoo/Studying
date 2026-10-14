# ML Atlas — Offline-Lernroadmap

Selbstbestimmtes ML-Curriculum mit 56 Kompetenzen, davon 46 Kernthemen, in Machine Learning, Python, SQL, linearer Algebra, Statistik und Analysis. Ohne Zeitziele oder Prüfungsvorbereitung.

## Öffnen

Im vorhandenen Repository-Ordner:

```bash
git pull --ff-only origin main
```

Danach `index.html` per Doppelklick im Browser öffnen. Unter Windows alternativ:

```powershell
Start-Process .\index.html
```

Es ist keine Installation, kein Python-/Node-Server und keine Internetverbindung für die Roadmap erforderlich. Nur der Git-Abgleich sowie das bewusste Öffnen externer Bücher, Kurse und Dokumentationen benötigen Internet. Externe Lernmaterialien sind verlinkt, nicht heruntergeladen.

Beim ersten Herunterladen:

```bash
git clone https://github.com/Levavoo/Studying.git
cd Studying
```

## Funktionen

- Themen nach Fach, Wichtigkeit, Status und Voraussetzungen filtern.
- Erforderliche Voraussetzungen von optionaler Vertiefung unterscheiden.
- Lernziele, praktische Selbstchecks und aufklappbare Antwortkriterien verwenden.
- Passende Lernmaterialien direkt bei der jeweiligen Kompetenz öffnen.
- Lernstatus und eigenes Sicherheitsgefühl getrennt dokumentieren.
- Notizen, Nachweise und Material-Lesezeichen speichern.
- Lernfortschritt als JSON exportieren und nach einer Vorschau importieren.

Die Aufgaben werden nicht automatisch ausgeführt oder benotet.

## Fortschritt sichern

Der Browser speichert den Fortschritt lokal. Die HTML-Datei und Git enthalten diese persönlichen Einträge nicht automatisch. Bei lokalen Dateien kann sich das Speicherverhalten zwischen Browsern unterscheiden. Den Dateipfad möglichst beibehalten und regelmäßig **Export progress** verwenden. Vor Umbenennen, Verschieben, Browserwechsel oder Löschen von Browserdaten exportieren.

Einen Export aus der früheren Version kannst du über **Import progress** übernehmen. Die Kompetenz-IDs bleiben gleich. Beim Import ersetzen erkannte Einträge die entsprechenden lokalen Datensätze; andere Einträge bleiben erhalten.

Exportierte `ml-atlas-progress*.json`-Dateien und der Ordner `progress-backups/` werden von Git ignoriert. Für den Gerätewechsel diese Dateien separat übertragen und importieren.

## Aufbau

`index.html` enthält Oberfläche, Styling, Curriculum und JavaScript vollständig. Keine externen Fonts, Skripte, Bibliotheken, Telemetrie oder automatischen Netzwerkanfragen. Eine Content Security Policy blockiert Netzwerkanfragen aus der Anwendung.

Der Inhalt ist bewusst eine ausbaufähige Kernstruktur. Spezialisierungen und optionale Vertiefungen zählen nicht zum Kernfortschritt.

Die vorherigen Repository-Inhalte wurden auf Wunsch ersetzt. Frühere Versionen sind weiterhin in der Git-Historie vorhanden.
