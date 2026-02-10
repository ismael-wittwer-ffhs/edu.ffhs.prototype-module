---
alwaysApply: true
---

# Moodle-Kurs erstellen

Erzeuge den Moodle-Kurs für dieses Modul basierend auf dem Modulplan in `content/modulplan.md` und den Quellinhalten in `src/output/`.

## Modulstruktur

Jedes Modul besteht aus **5 Blöcken**. Jeder Block hat einen **Gesamtaufwand von 30 Stunden** und gliedert sich in drei Phasen:

| Phase                | Beschreibung |
|----------------------|--------------|
| **Vorbereitungsphase** | Selbststudium vor der Präsenz — Leseaufträge, Forumsdiskussionen, Quizzes, Abgaben |
| **Präsenzphase**       | 4 Unterrichtseinheiten à 45 min = **3 h** — Vertiefung, Anwendung, Klärung offener Fragen |
| **Nachbereitungsphase**| Nachbearbeitung, Reflexion, ergänzende Aufgaben |

**Zeitbudget pro Block:**
Die Summe der geschätzten Zeiten aller Aufgaben (Vorbereitung + Präsenz + Nachbereitung) muss **ca. 30 h** ergeben. Die Präsenzphase ist fix bei 3 h; die restlichen ~27 h verteilen sich auf Vor- und Nachbereitung.

## Aufgabentypen in der Vorbereitungsphase

Hinter **jeder** Aufgabe steht die geschätzte Bearbeitungszeit in Klammern.

### 1. Leseauftrag

Reines Lesen eines Textes oder Kapitels.

```markdown
### Leseauftrag: [Titel des Textes]
Lesen Sie [Quelle / Kapitel / Seitenangabe]. *(geschätzte Zeit: X h)*
```

### 2. Leseauftrag + Forumsdiskussion

Kombination aus Lesen und aktivem Austausch im Forum.

```markdown
### Leseauftrag & Forum: [Titel des Textes]
1. Lesen Sie [Quelle / Kapitel / Seitenangabe]. *(geschätzte Zeit: X h)*
2. Posten Sie im Forum **[Forumname]**:
   - Mindestens **eine eigene Frage oder Beobachtung** zum Text.
   - Kommentieren Sie mindestens **einen Beitrag** einer/s Mitstudierenden.
   *(geschätzte Zeit: X min)*
```

### 3. Quiz

Multiple-Choice- und/oder offene Fragen. Zu jeder Frage wird die **Musterlösung** mitgeliefert.

```markdown
### Quiz: [Thema]
*(geschätzte Zeit: X min)*

**Frage 1 (Multiple Choice):**
Welche Aussage zu [Thema] ist korrekt?
- [ ] A) …
- [x] B) … ← *korrekt*
- [ ] C) …
- [ ] D) …

> **Musterlösung:** B ist korrekt, weil …

**Frage 2 (Offen):**
Erklären Sie …

> **Musterlösung:** …
```

### 4. Abgabe

Einreichung einer Aufgabe, eines Entwurfs, Codes usw.

```markdown
### Abgabe: [Titel]
[Aufgabenstellung …]
**Abgabeformat:** [z. B. PDF, ZIP, Link]
*(geschätzte Zeit: X h)*
```

## Ausgabeformat

Erzeuge pro Block eine Markdown-Datei unter `content/block-N/block-N.md` mit folgender Struktur:

```markdown
# Block N: [Titel]

## Lernziele
- …

## Vorbereitungsphase (~X h)

### Leseauftrag: …
…

### Quiz: …
…

(weitere Aufgaben)

## Präsenzphase (3 h)

### Unterrichtseinheit 1 (45 min): [Thema]
- …

### Unterrichtseinheit 2 (45 min): [Thema]
- …

### Unterrichtseinheit 3 (45 min): [Thema]
- …

### Unterrichtseinheit 4 (45 min): [Thema]
- …

## Nachbereitungsphase (~X h)

### [Aufgabentyp]: …
…

---
**Gesamtaufwand Block N:** ~30 h
```

## Ablauf

1. **Lies `content/modulplan.md`** — dort stehen die Themen und die Zuordnung zu den Blöcken.
2. **Lies die Quellinhalte in `src/output/`** — diese liefern den Fachstoff für die Aufgaben.
3. **Erzeuge für jeden Block** die Datei `content/block-N/block-N.md` nach obiger Struktur.
4. Stelle sicher, dass die **Zeitsumme pro Block ≈ 30 h** beträgt (Vorbereitung + 3 h Präsenz + Nachbereitung).
5. Jede Aufgabe hat eine **realistische Zeitschätzung** in Klammern.
6. Quizfragen enthalten immer die **Musterlösung**.
7. **Erfinde keine Fachinhalte** — leite alle Aufgaben aus dem Modulplan und den Quelltexten ab. Verwende Platzhalter `[…]`, wenn konkreter Stoff noch fehlt.
8. Gib am Ende eine Zusammenfassung mit der Zeitverteilung aller 5 Blöcke aus.
