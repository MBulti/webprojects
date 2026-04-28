# Shared Landing Theme

Gemeinsames Hugo-Theme fuer die Landingpages.

Dieses Theme enthaelt:

- Layouts fuer Startseite, Impressum und Datenschutz.
- Gemeinsames CSS.
- Gemeinsame Navigation, Hero, Leistungsbereich, Ablauf, Kontakt und Footer.

Die einzelnen Projekte definieren nur:

- Texte in `content/_index.md`.
- Rechtstexte in `content/impressum.md` und `content/datenschutz.md`.
- Farben, Kontaktangaben, SEO-Daten und Bildpfade in `hugo.toml`.
- Bilder in `static/images/`.

Lokaler Build aus einem Projektordner:

```bash
hugo --minify
```

Das funktioniert, weil die Projekte `themesDir = "../themes"` verwenden.
