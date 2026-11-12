# Wardogs Tracker

Stat-Tracker für Wardogs. Läuft im Hintergrund (Tray-Symbol), liest den Bildschirm aus und zeigt
alles in einem Dashboard im Browser: K/D, Kills, Tode, Headshot-Rate, Geld je Session und je
Match, Waffen samt Gunsmith-Werten, Maps, Opfer, Nemesis, Entfernungen, Belohnungen. Filter nach
gesamter Spielzeit, Season, Woche, Tag, Session, Match oder eigenem Zeitraum.

Getrackt wird auf jedem Server, nur die Firing Range nicht.

Aktuelle Version: **0.1.0** (frühe Fassung, Fehler sind möglich).

## Wichtig: Anti-Cheat

Der Tracker liest **nur den Bildschirm** aus, wie eine Aufnahme-Software (OBS, Shadowplay). Er
öffnet den Spielprozess nicht, liest keinen Speicher, fasst keinen Netzverkehr an und schreibt
nichts ins Spiel. Das Spielfenster wird nur über die Prozessliste gefunden.

Trotzdem: Wardogs nutzt Anti-Cheat. **Nutzung auf eigene Gefahr.**

## Download und Start

1. Unter [Releases](../../releases/latest) `WardogsTracker.exe` herunterladen und in einen
   eigenen Ordner legen, zum Beispiel `%LOCALAPPDATA%\Programs\Wardogs Tracker`.
2. Starten. Die exe ist nicht signiert, deshalb warnt Windows SmartScreen beim ersten Start:
   **Weitere Informationen > Trotzdem ausführen**.
3. Beim ersten Start öffnet sich das Dashboard. In den **Einstellungen** den eigenen
   **Spielernamen** eintragen, genau wie im Spiel. Ohne Namen kann der Tracker Kills und Tode nicht
   zuordnen.
4. Spielen. Gezählt wird nur, solange Wardogs im Vordergrund ist.

Wer die Datei prüfen will: zu jeder exe liegt `WardogsTracker.exe.sha256` im Release, in
PowerShell vergleichen mit `Get-FileHash WardogsTracker.exe`.

## Bedienung

Das Tray-Symbol (Fadenkreuz) hat ein Menü: Dashboard öffnen, Pausieren, Datenordner öffnen,
Beenden. Das Dashboard läuft unter <http://127.0.0.1:8765/>, nur auf dem eigenen Rechner.

Waffen erkennt der Tracker am Killfeed-Symbol. In der Waffentabelle ordnet man jedem Symbol eine
Waffe oder Fahrzeuggruppe zu, gleiche Zuordnung fasst Symbole zusammen.

Seasons trägt man in den Einstellungen als `Name;JJJJ-MM-TT` ein, eine pro Zeile.

## Updates

Der Tracker fragt beim Start einmal am Tag hier nach einer neuen Version. Gibt es eine, erscheint
im Dashboard ein Hinweis. In den Einstellungen unter **Updates** lädt **Jetzt aktualisieren** die
neue exe, prüft die Prüfsumme, tauscht die Datei und startet den Tracker neu. Die Statistik bleibt
erhalten. Von Hand geht es auch: Tracker beenden, neue exe über die alte kopieren.

## Voraussetzungen

- Windows 10 oder 11, Spiel im Fenster- oder randlosen Modus. Exklusives Vollbild ist ungetestet.
- Die Bildbereiche skalieren mit der Auflösung. **Getestet bisher nur auf 2560 x 1440**, bei
  anderen Auflösungen bitte melden, was nicht erkannt wird.
- Spielsprache Englisch. Die Texterkennung nutzt Windows-OCR mit `en-US`; fehlt das englische
  Sprachpaket, unter Windows-Einstellungen > Zeit und Sprache Englisch (USA) hinzufügen.

## Daten

Alles bleibt auf dem eigenen Rechner, in `%LOCALAPPDATA%\WardogsTracker`:

- `tracker.db` - die Statistik (SQLite)
- `config.json` - die Einstellungen
- `tracker.log` - Protokoll für die Fehlersuche

Ins Netz geht nur die Update-Abfrage an GitHub und, beim Laden der Waffendaten, die Abfrage an
MetaForge.

## Quellen

Waffen-, Gunsmith- und Aufsatzdaten stammen von MetaForge. Wardogs Tracker ist ein privates
Fan-Projekt und steht in keiner Verbindung zu den Entwicklern von Wardogs.
