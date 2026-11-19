# Datenschutzerklärung - Wardogs Tracker Discord-Bot

Stand: 19.11.2026

Der Discord-Bot gehört zum Wardogs Tracker, einem privaten, kostenlosen Hobbyprojekt
(GitHub: [Klayment](https://github.com/Klayment)). Er ist kein offizielles Produkt der Entwickler
von Wardogs.

## Welche Daten gespeichert werden

Nur wenn du deinen Tracker mit `/link` verknüpfst:

- deine Discord-Nutzer-ID
- ein Hash (keine Klartextkopie) des Schlüssels, mit dem dein Tracker hochlädt, und wann du verknüpft hast
- eine Zusammenfassung deiner Stats, die dein Tracker hochlädt: Kills, Tode, K/D, Headshot-Quote,
  Matches, Spielzeit, Geld, Kontostand und die Namen deiner meistgenutzten Waffen, jeweils für
  heute, diese Woche, die Season und gesamt, dazu der Zeitpunkt des letzten Uploads
- vorübergehend der Verknüpfungscode aus `/link`, höchstens 10 Minuten

## Was nicht gespeichert wird

- keine Nachrichten: der Bot liest keine Chatnachrichten, er bekommt nur die Slash-Befehle
- keine Namen anderer Spieler, kein Steam-Name, keine Screenshots, keine Rohdaten aus dem Spiel
- keine IP-Adressen durch den Bot selbst

## Wozu

Ausschließlich, um deine Befehle (`/stats`, `/geld`, `/heute`, `/waffen`) zu beantworten. Die
Daten werden nicht verkauft, nicht weitergegeben und nicht für Werbung genutzt.

## Wer sie sieht

Die Antwort auf einen Befehl sieht jeder, der den Channel lesen kann, in dem du den Befehl
eingibst. Andere können deine Stats nicht abrufen, es gibt keinen Befehl dafür.

## Wo die Daten liegen

Bei Cloudflare (Cloudflare Workers und Cloudflare D1), das den Bot betreibt. Für die Verarbeitung
durch Cloudflare gilt zusätzlich dessen Datenschutzerklärung: https://www.cloudflare.com/privacypolicy/

## Wie lange

Bis du die Verknüpfung löst. Jeder neue Upload ersetzt den vorigen Stand, ältere Stände werden
nicht aufbewahrt.

## Löschen

`/unlink` im Discord oder "Trennen" im Tracker-Dashboard löscht deine Verknüpfung und deine
gespeicherten Stats sofort.

## Kontakt

Fragen über die Issues dieses Repositorys:
https://github.com/Klayment/wardogs-tracker-releases/issues
