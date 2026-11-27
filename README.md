# Wardogs Tracker

Stat-Tracker für Wardogs. Läuft im Hintergrund (Tray-Symbol), liest den Bildschirm aus und zeigt
alles in einem Dashboard im Browser: K/D, Kills, Tode, Headshot-Rate, Geld je Session und je
Match, Waffen samt Gunsmith-Werten, Maps, Opfer, Nemesis, Entfernungen, Belohnungen, EP und
Level je Klasse. Filter nach gesamter Spielzeit, Season, Woche, Tag, Session, Match oder eigenem
Zeitraum.

Getrackt wird auf jedem Server, nur die Firing Range nicht.

Aktuelle Version: **0.1.41** (frühe Fassung, Fehler sind möglich).

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
3. Beim ersten Start öffnet sich das Dashboard mit den Nutzungsbedingungen (Deutsch oder
   Englisch). Erst nach **Akzeptieren** zählt der Tracker, **Ablehnen** beendet ihn.
   Danach in den **Einstellungen** den eigenen
   **Spielernamen** eintragen, genau wie im Spiel. Ohne Namen kann der Tracker Kills und Tode nicht
   zuordnen.
4. Spielen. Gezählt wird, solange Wardogs im Vordergrund oder unverdeckt sichtbar ist, etwa wenn der
   Fokus auf einem zweiten Monitor liegt.

Wer die Datei prüfen will: zu jeder exe liegt `WardogsTracker.exe.sha256` im Release, in
PowerShell vergleichen mit `Get-FileHash WardogsTracker.exe`.

## Bedienung

Das Tray-Symbol (Fadenkreuz) hat ein Menü: Dashboard öffnen, Pausieren, Datenordner öffnen,
Beenden. Das Dashboard läuft unter <http://127.0.0.1:8765/>, nur auf dem eigenen Rechner.

Waffen erkennt der Tracker am Killfeed-Symbol. In der Waffentabelle ordnet man jedem Symbol eine
Waffe oder Fahrzeuggruppe zu, gleiche Zuordnung fasst Symbole zusammen.

Die Seite **Klassen** zeigt EP und Level je Klasse, gelesen vom Endbildschirm (Tab PROGRESSION),
dazu Schnitt und Prognose bis zum nächsten oder einem gewählten Level. Den Startstand trägt man
einmal von Hand aus Tab > Progression ein, danach zählt der Tracker selbst weiter.

Seasons trägt man in den Einstellungen als `Name;JJJJ-MM-TT` ein, eine pro Zeile.

## Discord-Bot

Die eigenen Stats lassen sich im Discord abrufen, auch wenn der PC aus ist: `/stats` (wahlweise
für heute, Woche, Season oder gesamt), `/geld`, `/heute`, `/waffen`, `/match` (letztes Match),
`/rekorde` und `/vergleich` (gegen Vortag, Vorwoche oder die Season davor). Jeder sieht nur seine
eigenen Zahlen.

1. Den Bot auf den Server holen (Admin, einmal):
   <https://discord.com/oauth2/authorize?client_id=1572914410547183696&scope=bot+applications.commands&permissions=0>
2. Im Discord `/link` tippen, der Code ist nur für dich sichtbar und 10 Minuten gültig.
3. Im Dashboard unter **Einstellungen > Discord** den Code eintragen und **Verknüpfen** klicken.

Hochgeladen werden nach jedem Match nur deine Zahlen, Waffennamen und dein Kontostand, keine
Spielernamen. **Trennen** im Dashboard oder `/unlink` löscht die Daten beim Bot.
[Datenschutz](PRIVACY.md) · [Nutzungsbedingungen](TERMS.md)

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
- `config.json` - die Einstellungen; der Discord-Schlüssel darin ist mit Windows verschlüsselt
  und nur auf diesem Rechner unter diesem Konto lesbar
- `tracker.log` - Protokoll für die Fehlersuche

Erkennt der Tracker nichts, hilft **Einstellungen > Diagnose speichern**: eine zip mit Logs,
Einstellungen und ein paar Kennwerten, ohne die eigenen Namen und ohne die Datenbank.

Ins Netz geht nur die Update-Abfrage an GitHub und, beim Laden der Waffendaten, die Abfrage an
MetaForge.

## Quellen

Waffen-, Gunsmith- und Aufsatzdaten stammen von MetaForge. Wardogs Tracker ist ein privates
Fan-Projekt und steht in keiner Verbindung zu den Entwicklern von Wardogs.

## Lizenz

Wardogs Tracker (c) 2026 Klayment, alle Rechte vorbehalten. Kostenlos für den privaten Gebrauch;
weitergeben bitte nur als Link auf diese Release-Seite. Entpacken, Dekompilieren und das
Nachbauen der Erkennung sind nicht erlaubt. Die genauen Bedingungen stehen in
`LICENSE`, die Lizenzen der enthaltenen Bibliotheken in `THIRD-PARTY-NOTICES.txt`. Beides liegt
jedem Release bei und ist im Tracker unter Einstellungen > Lizenz und Hinweise abrufbar.

Spielbilder, Waffen- und Fahrzeugnamen gehören den Rechteinhabern von Wardogs und sind von dieser
Lizenz nicht erfasst.

## English

Stat tracker for Wardogs. It runs in the background, reads the screen like recording software and
shows your stats in a local dashboard at <http://127.0.0.1:8765/>. It never touches the game
process, but Wardogs uses anti-cheat: **use at your own risk**.

1. Download `WardogsTracker.exe` from [Releases](../../releases/latest) and put it in a folder of
   its own. SmartScreen warns on first start because the exe is not signed: **More info > Run
   anyway**.
2. On first start the dashboard shows the terms of use. The tracker only starts counting after
   you click **Accept**; **Decline** quits it.
3. Enter your in-game player name under **Einstellungen** (settings). Game language must be
   English.

All data stays on your PC in `%LOCALAPPDATA%\WardogsTracker`. The tracker only contacts GitHub
(updates), MetaForge (weapon data) and, if you link it, the Discord bot. Free for private,
non-commercial use; share it only by linking to this page. Unpacking, decompiling or copying its
detection logic is not permitted. Full terms in `LICENSE` (German version prevails), third-party
licenses in `THIRD-PARTY-NOTICES.txt`.
