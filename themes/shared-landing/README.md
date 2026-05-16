# Shared Landing Theme

Wiederverwendbares Hugo-Theme für statische Business-Landingpages.

Das Theme enthält:

- Startseitenlayout mit Hero, Leistungen, optionalen Inhaltssektionen und Kontakt.
- Layouts für Impressum und Datenschutz.
- Varianten-Styling über `siteVariant`, aktuell `midwife-premium` und `trade-premium`.
- Relative Asset-URLs für GitHub Pages und Unterpfad-Deployments.

## Projektkonfiguration

In `hugo.toml` werden globale Daten und Design-Tokens gepflegt:

```toml
theme = "shared-landing"
themesDir = "../themes"

[params]
  siteVariant = "midwife-premium"
  businessName = "Name"
  profession = "Beruf oder Angebot"
  location = "Ort und Umgebung"
  phone = "+49 123 4567890"
  phoneHref = "+491234567890"
  email = "kontakt@example.de"
  whatsappHref = ""
  instagramUrl = ""
  logoImage = "/images/logo.png"
  logoAlt = "Name"
  heroImage = "/images/portrait.jpg"
  ogImage = "/images/portrait.jpg"
  primaryColor = "#936863"
  accentColor = "#e7b8aa"
  darkColor = "#2d2522"
  lightColor = "#fff7f3"
  seoDescription = "Kurzbeschreibung für Suchmaschinen."
```

## Startseiten-Parameter

Die Inhalte der Startseite liegen in `content/_index.md`.

### Hero

```yaml
hero:
  eyebrow: "Kurzer Kontext"
  title: "Hauptüberschrift"
  text: "Ein kurzer Einführungstext."
  primaryCta: "Kontakt aufnehmen"
  secondaryCta: "Leistungen ansehen"
  mediaBadge: ""
```

`mediaBadge` ist optional. Wenn es leer ist oder fehlt, wird kein Badge angezeigt.

### Leistungen

```yaml
servicesHeading: "Leistungen im Überblick"
showServiceExamples: false
services:
  - title: "Leistung"
    iconImage: "/images/service.png"
    text: "Kurzbeschreibung"
    examples:
      - "Optionaler Chip"
```

`iconImage` ist optional. Alternativ kann `icon` für ein Textsymbol genutzt werden.
`showServiceExamples: false` blendet die `examples`-Chips aus.

### Trust-Bereich

```yaml
showTrust: false
trustHeading: "Klar, persönlich und verlässlich"
trust:
  - "Aussage"
```

Der Bereich wird nur angezeigt, wenn `showTrust` nicht `false` ist und `trust` Einträge enthält.

### Über Mich

```yaml
about:
  title: "Über mich"
  image: "/images/about.jpg"
  imageAlt: "Portrait"
  text: "Persönlicher Text."
```

`image` und `imageAlt` sind optional.

### Erfahrung

```yaml
experienceHeading: "Erfahrung und Schwerpunkte"
experience:
  - title: "Station oder Schwerpunkt"
    image: "/images/example.jpg"
    imageAlt: "Beschreibung des Bildes"
    text: "Kurzbeschreibung."
```

Der Bereich wird nur angezeigt, wenn `experience` Einträge enthält. Bilder sind optional.

### Ablauf

```yaml
showProcess: false
processHeading: "So läuft die Zusammenarbeit ab"
process:
  - title: "Anfrage"
    text: "Beschreibung"
```

`showProcess: false` blendet den Bereich und den Navigationslink aus.

### Einsatzgebiet

```yaml
showArea: false
area:
  title: "Einsatzgebiet"
  text: "Beschreibung"
```

`showArea: false` blendet den Bereich aus.

### Kontakt

```yaml
contact:
  title: "Kontaktaufnahme"
  text: "Kontakttext inklusive Erreichbarkeit."
```

Telefon, E-Mail und WhatsApp kommen aus `hugo.toml`. Buttons werden nur gerendert, wenn die jeweiligen Werte gesetzt sind.

## Lokaler Build

Aus einem Projektordner:

```bash
hugo server
hugo --minify
```

Aus einem Monorepo-Root:

```bash
hugo --source hebamme-landingpage --destination /tmp/hebamme-public --baseURL http://localhost:1313/
```
