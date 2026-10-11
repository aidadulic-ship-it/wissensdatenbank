# Wissen bleibt

Klickbarer, deutschsprachiger Prototyp, der Wissensmanagement, Exit-Prozess und Onboarding verbindet. Von Aida Dulic (HR Content, Employer Branding, AI Enablement).

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
- Geführte Wissenserfassung mit 14 Fragen, Zwischenspeichern und Fortsetzen
- Termine als Monatskalender und Liste, simulierte Einladungen
- Übernahmeprüfung (Praxisprüfung, Nacharbeit, Abnahme)
- Onboarding-Plan: weiterführen, verbessern oder einstellen
- Verkürzter Übergabeprozess für Sonderfälle
- **Wissensregister:** Stellenbeschreibungen, Projekte, Auswertung mit Hinweisen
- Demo-Rollenwechsel (austretende Person, Führungskraft, übernehmende Person, HR)
- Befehlspalette (Strg/Cmd + K), Hilfe, Hell- und Dunkelmodus, Bedienung am Handy

## Datenspeicherung

- Fälle, Aufgaben, Termine und Eingaben liegen im `localStorage` des Browsers (Schlüssel `wissen-bleibt-demo-v1`).
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
