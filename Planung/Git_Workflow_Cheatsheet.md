# Git-Cheatsheet — Studying
Für VS Code + PowerShell. Alle täglichen Befehle im lokalen Ordner **Studying** ausführen. Befehle einzeln ausführen; bei Fehlern stoppen.

## Einmalig: Repository herunterladen
Nur wenn du noch keine lokale Kopie hast. Im gewünschten übergeordneten Ordner:
```powershell
git clone https://github.com/Levavoo/Studying.git
cd Studying
code .
```
Ist der Ordner schon vorhanden: in VS Code öffnen, nicht erneut klonen. Falls `code` nicht erkannt wird: Datei → Ordner öffnen.
Git-Version prüfen: `git --version`.
Falls Git beim Commit nach deiner Identität fragt, einmal im Repository setzen (Platzhalter ersetzen):
```powershell
git config user.name "Dein Name"
git config user.email "Deine GitHub-Commit-Adresse"
```
Die E-Mail wird Teil der Commits. Du kannst deine GitHub-noreply-Adresse verwenden. Bei der Anmeldung den angebotenen GitHub-Anmeldevorgang nutzen.

## Dein täglicher Ablauf
### 1. Vor dem Lernen: Stand prüfen und neue Materialien holen
```powershell
git status
git branch --show-current
git pull --ff-only origin main
```
Voraussetzung: Du bist auf **main**, und `git status` zeigt keine offenen Änderungen. Falls ein anderer Branch angezeigt wird, zuerst offene Arbeit sichern; erst dann `git switch main`.
`--ff-only` aktualisiert ohne Merge-Commit und stoppt bei auseinanderlaufender Historie.

### 2. Lernen und bearbeiten
Notebook oder Markdown öffnen, Antworten ergänzen, mit **Strg+S speichern**.
Bei Notebooks: vor der Abgabe Kernel neu starten und alle Zellen der Reihe nach ausführen; danach nochmals speichern.

### 3. Genau deine Abgabe vormerken
Beispiel ML-001; für andere Abgaben Dateipfad ersetzen:
```powershell
git status
git diff --stat
git add ML/Abgaben/ML-001.ipynb
git diff --cached --stat
```
Mit `git diff` siehst du nicht vorgemerkte Änderungen an bereits erfassten Dateien; neue Dateien stehen zunächst in `git status`.
Mit `git diff --cached` siehst du die vorgemerkten Änderungen. Bei Notebooks ist die VS-Code-Differenzansicht oft übersichtlicher als JSON im Terminal.
IHK-Beispiel:
```powershell
git add IHK/AP1/Abgaben/AP1-D01.md
```
Für den Probelauf gezielt Dateien hinzufügen, damit keine ungewollten Dateien mitkommen.

### 4. Lokal versionieren und hochladen
```powershell
git commit -m "Bearbeite ML-001: Datenqualitaet pruefen"
git push origin main
git status
```
Anschließend Datei auf GitHub prüfen. **Erst nach erfolgreichem Push kann der Mentor deine lokale Arbeit sehen.**
Ein sauberer Arbeitsordner allein beweist nicht, dass deine Commits hochgeladen wurden.

## Die Begriffe
| Befehl / Aktion | Bedeutung |
|---|---|
| Strg+S | Datei auf deinem Rechner speichern |
| git status | Branch, offene Änderungen und gegebenenfalls Synchronisationsstand anzeigen |
| git add DATEI | Aktuellen Dateiinhalt für den nächsten Commit vormerken |
| git commit -m "Text" | Vorgemerkten Stand lokal versionieren |
| git push origin main | Lokale main-Commits nach GitHub übertragen |
| git pull --ff-only origin main | Remote-main holen und aktuellen Branch nur per Fast-forward aktualisieren |
| git log --oneline -5 | Letzte fünf lokale Commits zeigen |
| git remote -v | Hinterlegte Remote-Adressen anzeigen |

## Typische Situationen
**Nach git add weitergeschrieben?** Speichern und dieselbe Datei erneut mit `git add` vormerken. Sonst wird der zuvor vorgemerkte Inhalt committed.

**Falsche Datei vorgemerkt?** Aus der Auswahl nehmen; die bearbeitete Datei bleibt erhalten:
```powershell
git restore --staged ML/Abgaben/ML-001.ipynb
```

**Offene Änderungen vor dem Pull?** Zuerst speichern, gezielt hinzufügen und als Zwischenstand committen. Beispiel:
```powershell
git add ML/Abgaben/ML-001.ipynb
git commit -m "Zwischenstand ML-001"
```
Auch alle anderen offenen Änderungen bewusst behandeln; danach `git status` prüfen.

**Push abgelehnt oder Fast-forward nicht möglich?** Wenn dein Arbeitsordner sauber ist und deine lokalen Commits noch nicht veröffentlicht wurden:
```powershell
git pull --rebase origin main
```
Nur bei erfolgreichem Abschluss:
```powershell
git push origin main
```
Damit werden neue Remote-Commits geholt und deine noch lokalen Commits darauf erneut angewendet. Bei Konflikten stoppen und `git status` lesen. Besonders bei .ipynb nicht blind „ours/theirs“ wählen. Fehlermeldung und betroffenen Pfad im Chat senden. Um den laufenden Rebase abzubrechen:
```powershell
git rebase --abort
```
Für diesen Lernworkflow brauchst du weder `push --force` noch `reset --hard`.

## Zusammenarbeit
- Wir arbeiten im Probelauf auf **main**; Zusatzbranches sind nicht nötig.
- Vor einer Lerneinheit neue Materialien und Korrekturen holen.
- Antworten in deinen Abgabeabschnitten ergänzen; Mentorfeedback erhalten.
- Kleine nachvollziehbare Commits, z. B. „Ergaenze AP2-D01“.
- Erst nach erfolgreichem Push ist die Abgabe eingereicht; optional im Chat die Nummer nennen.

## Offizielle Referenzen
- https://git-scm.com/docs/git-pull
- https://git-scm.com/docs/git-restore
- https://git-scm.com/docs/git-add
- https://git-scm.com/docs/git-commit

**Merksatz: Pull → bearbeiten → speichern → Add → Commit → Push.**
