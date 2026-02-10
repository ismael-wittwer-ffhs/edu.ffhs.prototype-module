# Anleitung: Arbeiten mit dem FFHS-Modul-Template in Cursor

## Voraussetzungen

- [Cursor](https://cursor.sh/) installiert (aktuelle Version)
- Git installiert und konfiguriert
- Repository geklont oder als Template erstellt

## Schnellstart

1. Repository öffnen: **File → Open Folder** → Projektordner auswählen.
2. `README.md` öffnen und alle `[Platzhalter]` mit den tatsächlichen Modulangaben ersetzen.
3. `content/modulplan.md` mit der Modulstruktur befüllen — dieses Dokument steuert alles Weitere.
4. Quellmaterial in `src/input/` ablegen.
5. Cursor-Commands nutzen, um Quellen zu transformieren und Kursinhalte zu generieren.

---

## Projektstruktur

```
├── .cursor/
│   ├── commands/          # Cursor-Commands (wiederverwendbare Prompts)
│   └── rules/             # Project Rules (KI-Verhaltensregeln)
├── src/
│   ├── input/             # Rohes Quellmaterial (PDFs, DOCX usw.)
│   └── output/            # Verarbeitetes Markdown aus dem Quellmaterial
├── content/
│   ├── block-1/ bis block-5/  # Finale Kursinhalte pro Block
│   ├── exams/             # Prüfungs- und Bewertungsmaterial
│   └── modulplan.md       # Massgebliches Dokument für die Modulstruktur
├── scripts/               # Hilfsskripte
├── README.md              # Modulübersicht
└── ANLEITUNG.md           # Diese Datei
```

### Was gehört wohin?

| Material | Zielordner | Hinweise |
|---|---|---|
| PDFs, DOCX, Rohtexte | `src/input/` | Wird von Cursor nicht indexiert (via `.cursorignore`) |
| Transformierte Markdown-Quellen | `src/output/` | Erzeugt durch den Command *Transform Sources* |
| Modulplan | `content/modulplan.md` | Immer zuerst befüllen — steuert die Blockstruktur |
| Block-Inhalte (Lernziele, Aufgaben) | `content/block-N/block-N.md` | Erzeugt durch den Command *Moodle-Kurs erstellen* |
| Ergänzende Block-Dateien | `content/block-N/01-titel.md` | Kebab-Case, zweistelliges Präfix |
| Prüfungen | `content/exams/` | — |
| Hilfsskripte | `scripts/` | — |

---

## Cursor-Commands ausführen

Commands sind vordefinierte Prompts, die im Ordner `.cursor/commands/` liegen.

### Verfügbare Commands

| Command-Datei | Zweck |
|---|---|
| `transform-sources.md` | Transformiert Rohmaterial aus `src/input/` in Markdown unter `src/output/` |
| `create-course.md` | Erzeugt die Moodle-Kursstruktur (Block-Dateien) basierend auf Modulplan und Quellen |

### So führst du einen Command aus

1. Öffne den Cursor-Chat (Tastenkürzel: `Ctrl+L`).
2. Tippe `/` im Chatfeld — es erscheint eine Liste der verfügbaren Commands.
3. Wähle den gewünschten Command aus (z. B. *Transform Sources*).
4. Der Command-Prompt wird automatisch in den Chat geladen. Bestätige mit Enter.
5. Cursor führt die Anweisungen aus dem Command aus.

### Typischer Workflow

```
1. Quellmaterial in src/input/ ablegen
2. Command "Transform Sources" ausführen     → erzeugt src/output/
3. content/modulplan.md befüllen
4. Command "Moodle-Kurs erstellen" ausführen  → erzeugt content/block-N/block-N.md
5. Inhalte manuell prüfen und verfeinern
```

---

## Project Rules anpassen

Project Rules steuern das Verhalten der KI in diesem Projekt.
Sie liegen unter `.cursor/rules/` als `.mdc`-Dateien.

### Vorhandene Regeln

| Datei | Zweck | Geltungsbereich |
|---|---|---|
| `persona.mdc` | Ton, Stil, Sprachregeln | Immer aktiv |
| `working-mode.mdc` | Arbeitsmodus (Planung, Sicherheit, Kommunikation) | Immer aktiv |
| `project-structure.mdc` | Ordnerstruktur, Dateikonventionen, Transformationsregeln | Immer aktiv |
| `content-authoring.mdc` | Didaktische Grundsätze, Formatierung, Dateinamen | Aktiv bei Dateien unter `content/` |

### Regeln bearbeiten

1. Öffne die gewünschte `.mdc`-Datei unter `.cursor/rules/`.
2. Bearbeite den Inhalt direkt in Cursor.
3. Der YAML-Frontmatter steuert das Verhalten:

```yaml
---
description: Kurzbeschreibung der Regel
alwaysApply: true       # true = immer aktiv, false = nur bei passenden Dateien
globs: content/**       # Optional: Dateimuster, bei denen die Regel gilt
---
```

### Neue Regel erstellen

1. Erstelle eine neue `.mdc`-Datei unter `.cursor/rules/`.
2. Füge den YAML-Frontmatter hinzu (siehe oben).
3. Schreibe die Regelinhalte in Markdown darunter.
4. Die Regel wird ab sofort von Cursor berücksichtigt.

Alternative: **Cursor Settings → Rules** erlaubt ebenfalls das Verwalten von Project Rules über die GUI.

---

## Neue Commands erstellen

1. Erstelle eine neue `.md`-Datei unter `.cursor/commands/`.
2. Der Dateiname wird zum Command-Namen (Kebab-Case empfohlen).
3. Schreibe die Anweisungen in Markdown — diese werden als Prompt an die KI übergeben.
4. Der Command erscheint danach in der `/`-Befehlsliste im Chat.

---

## Git-Workflow

### Konventionen

- **Kebab-Case** für alle Datei- und Ordnernamen.
- `src/input/` wird via `.cursorignore` von der Indexierung ausgeschlossen, ist aber im Git-Repository enthalten.
- `.gitkeep`-Dateien halten leere Ordner im Repository — nicht löschen.

### Änderungen committen (Source-Control-Tab)

Cursor enthält die Git-Integration von VS Code. Alle Git-Operationen lassen sich direkt über die grafische Oberfläche erledigen — ohne Terminal.

1. **Source Control öffnen:** Klicke auf das Branch-Symbol in der linken Seitenleiste oder nutze `Ctrl+Shift+G`.
2. **Änderungen prüfen:** Unter *Changes* siehst du alle geänderten, neuen und gelöschten Dateien. Ein Klick auf eine Datei zeigt den Diff (Vorher/Nachher).
3. **Dateien stagen:**
   - Einzelne Datei stagen: Fahre mit der Maus über die Datei und klicke das `+`-Symbol.
   - Alle Dateien stagen: Klicke das `+`-Symbol neben der Überschrift *Changes*.
   - Gestagete Dateien erscheinen unter *Staged Changes*. Zum Entstagen das `−`-Symbol klicken.
4. **Committen:** Schreibe eine aussagekräftige Nachricht ins Textfeld oberhalb der Dateiliste und klicke den **Commit**-Button (Häkchen-Symbol) oder drücke `Ctrl+Enter`. Alternativ: Klicke den Pfeil neben dem Commit-Button und wähle **Generate Commit Message with AI** — Cursor erstellt dann automatisch eine Commit-Nachricht basierend auf den gestageten Änderungen.
5. **Pushen:** Nach dem Commit erscheint ein **Sync Changes**-Button (oder das Cloud-Symbol in der Statusleiste unten). Damit werden die Commits zum Remote gepusht.

**Weitere nützliche Funktionen im Source-Control-Tab:**

- **Branch wechseln/erstellen:** Klick auf den Branch-Namen in der Statusleiste (unten links).
- **Pull:** Über das Drei-Punkte-Menü (`···`) im Source-Control-Tab → *Pull*.
- **Stash:** Über das Drei-Punkte-Menü → *Stash* — legt aktuelle, nicht committete Änderungen auf einen Stapel und stellt den letzten sauberen Stand wieder her. Nützlich, wenn man z. B. kurz den Branch wechseln muss, ohne die laufende Arbeit zu committen. Über *Pop Stash* lassen sich die Änderungen danach wiederherstellen.
- **Commit History:** Cursor zeigt unter *Timeline* (im Explorer-Tab, unterhalb der Dateiliste) die Commit-Historie der aktuell geöffneten Datei.

### Empfohlene Commit-Struktur

| Änderungstyp | Beispiel-Commit-Nachricht |
|---|---|
| Modulplan erstellt | `Modulplan mit 5 Blöcken definiert` |
| Quellen transformiert | `Quellmaterial Kapitel 1–3 nach src/output transformiert` |
| Block-Inhalte erstellt | `Block 2: Kursstruktur mit Lernzielen und Aufgaben erstellt` |
| Prüfung hinzugefügt | `Schlussprüfung mit 40 MC-Fragen erstellt` |
| Regel angepasst | `Project Rule: Zeitbudget pro Block auf 25h angepasst` |

### Hinweis zu `src/input/`

Die Dateien in `src/input/` sind via `.cursorignore` von der Cursor-Indexierung ausgeschlossen.
Sie werden also von der KI nicht gelesen und nicht in Suchergebnissen berücksichtigt.
Im Git-Repository sind sie aber weiterhin enthalten und werden normal committet.

---

## Tipps für die Arbeit mit Cursor

- **Chat-Kontext einschränken:** Verwende `@`-Referenzen, um Cursor auf bestimmte Dateien oder Ordner zu lenken (z. B. `@content/modulplan.md`).
- **Schrittweise arbeiten:** Erst Modulplan, dann Quellen transformieren, dann Blöcke generieren. Nicht alles auf einmal.
- **Ergebnisse prüfen:** Die KI erfindet keine Inhalte (so konfiguriert), kann aber Formatierungsfehler machen. Immer gegenlesen.
- **Regeln iterativ verfeinern:** Wenn die KI wiederholt etwas falsch macht, eine passende Project Rule ergänzen.
