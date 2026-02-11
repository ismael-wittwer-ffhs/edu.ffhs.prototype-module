# [Modulname] — FFHS

> **Prototyp-Modul-Repository**
> Dies ist das Template-Repository für die Erstellung neuer FFHS-Kursmodule. Ersetzen Sie die Platzhalter in eckigen Klammern durch Ihre tatsächlichen Modulinformationen, bevor Sie das Template verwenden.

## Modulzusammenfassung

`[Modulzusammenfassung hier einfügen.]`

## Modulübersicht

| Feld             | Wert                           |
|------------------|--------------------------------|
| Modulkürzel      | `[z. B. PCG]`                  |
| Modulname        | `[z. B. Programming in C# for Games]` |
| ECTS             | `[z. B. 5]`                    |
| Semester         | `[z. B. HS 2026]`             |
| Verantwortlich   | `[Name]`                       |

## Ordnerstruktur

```
├── src/
│   ├── input/          # Rohes Quellmaterial (PDFs, Textdateien usw.)
│   └── output/         # Verarbeitetes Markdown aus dem Quellmaterial
├── content/
│   ├── block-1/        # Kursinhalt Block 1
│   ├── block-2/        # Kursinhalt Block 2
│   ├── block-3/        # Kursinhalt Block 3
│   ├── block-4/        # Kursinhalt Block 4
│   ├── block-5/        # Kursinhalt Block 5
│   └── exams/          # Prüfungsmaterial
├── scripts/                # Hilfsskripte (Moodle-Transformer, Markdown-zu-PDF usw.)
```

### `src/input/`
Hier kommt das gesamte Rohquellmaterial hin — PDFs, Word-Dokumente, Textdateien oder andere Eingaben, die verarbeitet werden müssen. Dieser Ordner ist von der Cursor-Indexierung ausgeschlossen (via `.cursorignore`).

### `src/output/`
Enthält die verarbeiteten Markdown-Versionen der Eingabequellen. Diese dienen als Zwischenformat für die Erstellung der finalen Kursinhalte.

### `content/block-[1-5]/`
Die fünf Blöcke des Kurses. Jeder Unterordner enthält den finalen, strukturierten Inhalt für den jeweiligen Block (Lernziele, Übungen, Leistungsnachweise usw.).

## Anleitung zur Anpassung dieses Templates

1. **Alle `[Platzhalter]`** in dieser README durch die tatsächlichen Modulangaben ersetzen.
2. **Block-Ordner umbenennen**, falls Ihr Kurs eine andere Benennung verwendet (z. B. `week-1`, `unit-1`). Die obige Struktur entsprechend anpassen.
3. **Blöcke hinzufügen oder entfernen**, falls Ihr Kurs mehr oder weniger als fünf hat.
4. **Quellmaterial** in `src/input/` ablegen und die verarbeitete Ausgabe in `src/output/` platzieren.
5. **Jeden `content/block-*/`**-Ordner mit dem finalen Lehrmaterial für den jeweiligen Block befüllen.
6. **Diesen Abschnitt löschen** («Anleitung zur Anpassung dieses Templates»), sobald das Modul eingerichtet ist.
