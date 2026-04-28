# Trockenbau Landingpage

Statische Hugo-Landingpage fuer einen Trockenbau- und Innenausbau-Betrieb. Die Seite benoetigt kein Backend, keine Datenbank und kein Kontaktformular.

## Voraussetzungen

- Hugo Extended installieren: <https://gohugo.io/installation/>
- Dieses Projekt im Terminal oeffnen:

```bash
cd trockenbau-landingpage
```

## Lokal entwickeln

```bash
hugo server
```

Danach die angezeigte lokale URL im Browser oeffnen, meistens `http://localhost:1313/`.

## Inhalte aendern

- Haupttexte der Landingpage: `content/_index.md`
- Impressum: `content/impressum.md`
- Datenschutz: `content/datenschutz.md`
- Name, Ort, Telefon, E-Mail, Farben und SEO-Daten: `hugo.toml`
- Bilder: `static/images/`
- Gemeinsames Layout und CSS: `../themes/shared-landing/`

Optionaler Instagram-Link in der Navigation:

```toml
instagramUrl = "https://www.instagram.com/deinprofil/"
```

Wenn `instagramUrl` leer bleibt, wird kein Instagram-Link angezeigt.

Logo oben links:

```toml
logoImage = "/images/logo.svg"
logoAlt = "Trockenbau Beispiel"
```

Das Hero-Bild wird aktuell als `/images/mock-photo.svg` ausgeliefert. Ersetze fuer die echte Website `static/images/mock-photo.svg` durch ein passendes Foto oder lege z. B. `static/images/hero.jpg` ab und passe `heroImage` und `ogImage` in `hugo.toml` an.

## Kontaktangaben

Telefon und E-Mail werden in `hugo.toml` gepflegt:

```toml
phone = "+49 123 4567890"
phoneHref = "+491234567890"
email = "angebot@trockenbau-beispiel.de"
```

Wenn WhatsApp genutzt werden soll, kann `whatsappHref` gesetzt werden, zum Beispiel:

```toml
whatsappHref = "https://wa.me/491234567890"
```

## Build fuer IONOS

```bash
hugo --minify
```

Der fertige Website-Build liegt danach im Ordner `public/`.

## Upload zu IONOS

Nur den Inhalt von `public/` hochladen, nicht den ganzen Projektordner.

Moegliche Wege:

- SFTP-Zugang von IONOS verwenden.
- IONOS-Dateimanager verwenden.

Nach dem Upload im IONOS-Konto SSL fuer die Domain aktivieren.

## Docker

Die Seite kann auch als Docker-Container gebaut und lokal getestet werden.

Build aus dem Workspace-Root:

```bash
cd ..
docker build -f trockenbau-landingpage/Dockerfile -t trockenbau-landingpage .
```

Start:

```bash
docker run --rm -p 8085:80 trockenbau-landingpage
```

Danach ist die Seite unter `http://localhost:8085/` erreichbar.

Alternativ mit Docker Compose:

```bash
docker compose up --build
```

Der Container baut die Website mit Hugo, kopiert das gemeinsame Theme aus `../themes/shared-landing/` und serviert die fertigen statischen Dateien mit Nginx.

## Veroeffentlichung pruefen

- Startseite oeffnet korrekt.
- Impressum ist unter `/impressum/` erreichbar.
- Datenschutz ist unter `/datenschutz/` erreichbar.
- Telefonlink funktioniert auf dem Smartphone.
- E-Mail-Link oeffnet das Mailprogramm.
- Mobile Ansicht wirkt sauber und lesbar.

## Hinweise

- `public/` nicht manuell bearbeiten. Der Ordner wird bei jedem Build neu erzeugt.
- Rechtstexte sind Platzhalter und muessen vor der Veroeffentlichung geprueft werden.
- Keine unnoetigen Tracking- oder Drittanbieter-Skripte einbauen, wenn sie nicht wirklich gebraucht werden.
