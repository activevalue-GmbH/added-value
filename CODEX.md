# Codex-Briefing: added value KI-Pitch

## Was ist das?

Ein strategisches Positionierungsdokument für die KI-Marke **added value**.
Einzelne HTML-Datei, kein Framework, kein Build-Prozess.
Deployment via GitHub Pages (`main` Branch, `/root`).

---

## Dateistruktur

```
/
├── index.html        ← die einzige Datei, die zählt
├── CODEX.md          ← dieses Briefing
└── README.md         ← kurze Projektbeschreibung
```

---

## Design-System (nicht verändern ohne Freigabe)

### Farben (CSS Custom Properties in :root)

```css
--brand: #171412;          /* Fast-Schwarz, warm — Primärfarbe für Highlights, Nav-Header */
--brand-mid: #8B6914;      /* Amber/Gold, mittel — Subtext auf dunklem Grund */
--brand-pale: #F0EAE0;     /* Sehr helles Warm-Beige — Hintergrund für Highlight-Blöcke */
--cream: #F6F1EA;           /* Seitenhintergrund */
--warm-white: #FDFAF6;     /* Card-Hintergrund */
--ink: #171412;             /* Primärer Fließtext */
--ink-muted: #5c5850;      /* Sekundärer Text */
--ink-faint: #9a918c;      /* Metadaten, Labels */
--rule: #D8D2C8;            /* Trennlinien */
--accent: #C4862A;          /* Goldener Akzent — Headlines auf dunklem Grund, CTA */
```

### Typografie

```
Display / Headlines:  Playfair Display (Google Fonts) — Serif, 700
Body / Labels:        DM Sans (Google Fonts) — Sans-serif, 300 / 400 / 500
```

### Grundprinzipien

- Keine em-Dashes (—) im Text
- Kein Fett-Missbrauch: `font-weight: 500` für Betonung, nie 600/700 im Fließtext
- Sentence case überall, kein ALL CAPS außer Labels (11px, letter-spacing)
- Kein Boxen-Overkill: Editorial, nicht Dashboard
- Warme Ästhetik: kein kalter Tech-Look, kein Corporate-Blau

---

## Aufgaben für Codex

### Priorität 1: Typografie-Verfeinerung

Die Typografie-Skala soll konsistenter werden:

- Hero-Headline: `font-size: 52px` auf Desktop, `36px` auf Mobile
- Section-Headlines (`h2`): `font-size: 34px`
- Sub-Headlines innerhalb Sektionen: `font-size: 22px`
- Body: `font-size: 16px`, `line-height: 1.75`
- Labels (EYEBROW): `font-size: 11px`, `letter-spacing: 0.15em`, uppercase

### Priorität 2: Sektionsnummern als Margin-Notes

Die Sektionsnummern (01 · Marktlage etc.) sollen auf Desktop als linke Marginalie erscheinen:

```css
/* Ziel-Verhalten auf Desktop (>900px) */
.section-label {
  position: relative;
  /* Zahl links rausragen lassen, Inhalt beginnt bei 0 */
}
```

Auf Mobile: inline bleiben wie jetzt.

### Priorität 3: Tier-Farben der Produktleiter schärfen

Die drei Ebenen (Starten / Vertiefen / Umsetzen) sollen farblich klarer differenziert sein:

- Ebene 1 (Starten): `background: #171412` (fast schwarz)
- Ebene 2 (Vertiefen): `background: #2A2220` (etwas heller)
- Ebene 3 (Umsetzen): `background: #C4862A` (Amber/Gold — stärkste Ebene, Umsetzung)

Header-Text jeweils auf hellem Ton.

### Priorität 4: Mobile Responsive

- Alle 2-Spalten-Grids (`grid-template-columns: 1fr 1fr`) auf `1fr` bei < 640px
- Stat-Row: 1 Spalte auf Mobile
- Paradox-Box: 1 Spalte auf Mobile
- Team-Karten: `grid-template-columns: 1fr` (Name über Text)

### Priorität 5: Closing-Block

Der letzte Block (dunkelgrauer Hintergrund mit goldener Headline) soll stärker wirken:

- Hintergrund: `#171412`
- Headline-Größe erhöhen auf `48px`
- Die italic Zeile ("Machen Sie es offiziell.") in `--accent` (#C4862A) setzen
- Mehr vertikaler Raum: `padding: 72px 56px`

---

## Was Codex NICHT anfassen soll

- Den Inhalt / Texte — nur auf explizite Anfrage
- Die Grundstruktur der Sektionen (Reihenfolge, Anzahl)
- Die Google Fonts Imports
- Die Logik der Produktleiter (drei Tiers + Ecosystem-Block)

---

## GitHub Pages Deployment

1. Repository anlegen (public oder private mit Pages aktiviert)
2. `main` branch, root-Verzeichnis
3. Settings > Pages > Source: `main` / `/(root)`
4. `index.html` muss im Root liegen

URL-Pattern: `https://[username].github.io/[repo-name]/`

---

## Bekannte Baustellen (für spätere Iteration)

- Kein aktives Navigations-Highlighting beim Scrollen (IntersectionObserver fehlt noch)
- Kein Print-Stylesheet
- Fonts werden von Google Fonts geladen — bei Offline-Nutzung ggf. self-hosten
