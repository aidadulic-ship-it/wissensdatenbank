# Wissen bleibt

Klickbarer, deutschsprachiger Prototyp, der Wissensmanagement, Exit-Prozess und Onboarding verbindet. Von Aida Dulic.

Der Ablauf: **Exit erfassen → Wissen priorisieren → Übergabe planen → Wissen erfassen → Übernahme prüfen → Onboarding erstellen.** Jede abgeschlossene Übergabe aktualisiert zusätzlich ein **Wissensregister** mit Stellenbeschreibungen, Projekten und einer Auswertung zur Prozessverbesserung.

> **Hinweis:** Alle Personen, Firmen und Daten sind erfunden (Beispielfall Anna Berger, Learning Specialist). Der Prototyp hat keine Anmeldung und keine Zugriffskontrolle. Bitte keine echten personenbezogenen Daten eintragen.

## Schnellstart

Die App ist eine einzige Datei ohne Build-Schritt und ohne Abhängigkeiten.

1. Repository herunterladen oder klonen.
2. `index.html` im Browser öffnen.

### Auf GitHub Pages veröffentlichen

1. Repository auf GitHub anlegen und den Inhalt dieses Ordners hochladen.
2. Unter **Settings → Pages** als Quelle den Branch `main` und den Ordner `/ (root)` wählen.
3. Nach kurzer Zeit ist die App unter `https://<benutzername>.github.io/<repository>/` erreichbar.

## Funktionen

- Dashboard mit sechs klickbaren Kennzahlen, „nächster Schritt“ je Rolle und Mini-Kalender
- Exit-Fall anlegen (mit Prüfung der Eingaben und simuliertem HR-Ereignis), Detailansicht mit sechs Schritten
- Rückwärts berechneter Zeitplan, inklusive Vorschau bei Datumsänderung
- Aufgaben und Projekte mit Prioritäten A, B und C und passenden Übergabeschritten
- Wissenserfassung beginnt mit den drei kritischsten Aufgaben (Quellen verknüpfen, Fehlendes, Erfahrungswissen, Interviewnotiz); optional 14 vertiefende Fragen in 7 Abschnitten
- Simulierte Vorschläge (regelbasiert, keine KI): Antwort → Vorschlag → Quelle → Korrektur → Bestätigung → Wissenseintrag
- Termine als Monatskalender und Liste, simulierte Einladungen
- Sechs getrennte Prüfstufen je Aufgabe (Dokumentation, fachliche Prüfung, Zugänge, erklärt, selbstständig durchgeführt, abgenommen) mit Nachweis, Nacharbeit und Wiederholung
- Zwei berechnete Kennzahlen: „Vorbereitung abgeschlossen“ und „Selbstständige Übernahme bestätigt“, dazu Zähler für kritische Aufgaben
- Terminplanung nach Verfügbarkeit: Vertretung vor Eintritt der Nachfolge, Status „blockiert“, Zeitbudget, Vorschlag zur Neuplanung
- Pilotauswertung mit „Noch keine Daten“, wenn Daten fehlen
- Demo-Datum in der Seitenleiste, um spätere Schritte (z. B. Leas Eintritt am 16.11.) durchzuspielen
- Onboarding-Plan: weiterführen, verbessern oder einstellen
- Verkürzter Übergabeprozess für Sonderfälle
- **Wissensregister:** Stellenbeschreibungen, Projekte, Auswertung mit Hinweisen
- **Weiterentwicklung (Ausblick) – „Produktionsreife & Umsetzung“:** interaktiver Planungsbereich (Code-Befunde, Zielarchitektur, Datenmodell und Fachregeln, Outlook/Graph-Plan, Workflows, Sicherheit & Datenschutz, Fahrplan M0–M5) mit Status, Verantwortlichen, Zieltermin, Nachweisen, Filtern und Markdown-Export. Reine Planung: Datenbank, Outlook und Automatisierungen sind weiterhin simuliert; es gibt kein Backend, keine echte Anmeldung und keine Graph-Anbindung. Die Planungsdaten liegen getrennt im Browser (`wissen-bleibt-plan-v1`).
- Demo-Rollenwechsel (austretende Person, Führungskraft, übernehmende Person, HR)
- Befehlspalette (Strg/Cmd + K), Hilfe, Hell- und Dunkelmodus, Bedienung am Handy

## Datenspeicherung

- Fälle, Aufgaben, Termine und Eingaben liegen im `localStorage` des Browsers (Schlüssel `wissen-bleibt-demo-v2`).
- Das Wissensregister liegt unter `wissen-bleibt-register-v1`, ebenfalls lokal im Browser.
- „Demo zurücksetzen“ in der Seitenleiste lädt die Beispieldaten neu.
- Wenn die App auf claude.ai als Artifact läuft, nutzt das Register stattdessen die gemeinsame Datenbank dieser Seite und es gibt eine Bearbeitungsleiste für Kommentare. Auf GitHub Pages sind diese beiden Funktionen nicht aktiv.

## Projektstruktur

```
index.html                  fertige App (wird aus src/ gebaut)
src/                        Quellen: Stile, Markup und Skripte in Modulen
  build.sh                  baut index.html (benötigt Node nur für die Syntaxprüfung)
design/
  design-system/            Farben, Schrift und Regeln (tokens.json, README)
  screens-canvas/           Entwürfe: Dashboard und Seitenleiste
  ux-konzept-canvas/        UX-Konzept: Ablauf und Mobil-Screens
```

### Weiterentwickeln

```bash
bash src/build.sh
```

Die Module in `src/` werden in dieser Reihenfolge zusammengesetzt: Daten, Kern (Zustand, Navigation), Ansichten, Aktionen, Befehlspalette, Wissensregister, Bearbeitungsleiste, Start.

## Gestaltung

- Marineblau für Struktur, Magenta für Aktionen, Rot nur für kritische Zustände
- Schriften: Bricolage Grotesque (Überschriften), Hanken Grotesk (Text), IBM Plex Mono (Daten) über Google Fonts
- Kontrast für Text mindestens 4,5:1, bedienbar per Tastatur, Zielgrößen ab 44 px
- Die Entwürfe unter `design/` sind Design-Canvas-Dateien (`.dc.html`) und brauchen ihren Editor, um angezeigt zu werden. Die Farbwerte stehen in `design/design-system/tokens.json`.

## Lizenz

Noch nicht festgelegt. Bitte vor der Veröffentlichung eine `LICENSE`-Datei ergänzen (zum Beispiel MIT).

## Was simuliert ist

HR-Ereignis, Kalendereinladungen, Wissensquellen (kein SharePoint), automatische Vorschläge (Regeln, keine KI) und alle Personen und Daten. Es gibt keine Zeitersparnis-Aussage, weil Vergleichsdaten fehlen.

## Startseite
Beim Öffnen erscheint eine Startseite mit Start-Knopf, der in die Datenbank führt (`index.html#app` überspringt sie; Klick auf das Logo links oben öffnet sie wieder). Der Avatar ist als KI-generiert gekennzeichnet. Ein Avatar-Video (z. B. HeyGen-Export) lässt sich über `LANDING_VIDEO` in `src/13-landing.js` eintragen; ebenso `LANDING_EMAIL` und `LANDING_LINKEDIN` für den Kontaktblock (leer = Block bleibt unsichtbar). Der Abschnitt „So könnte die Zusammenarbeit aussehen“ ist ein Entwurf und gehört in `src/2b-landing.html`.
