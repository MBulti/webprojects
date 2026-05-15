# Hebamme Landingpage

Statische Hugo-Landingpage für eine Hebamme. Die Seite benötigt kein Backend, keine Datenbank und kein Kontaktformular.

## Voraussetzungen

- Hugo Extended installieren: <https://gohugo.io/installation/>
- Dieses Projekt im Terminal öffnen:

```bash
cd hebamme-landingpage
```

## Lokal entwickeln

```bash
hugo server
```

Danach die angezeigte lokale URL im Browser öffnen, meistens `http://localhost:1313/`.

## Inhalte ändern

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
logoAlt = "Hebamme Anna Beispiel"
```

Das Hero-Bild wird aktuell als `/images/mock-photo.svg` ausgeliefert. Ersetze für die echte Website `static/images/mock-photo.svg` durch ein passendes Foto oder lege z. B. `static/images/hero.jpg` ab und passe `heroImage` und `ogImage` in `hugo.toml` an.

## Kontaktangaben

Telefon und E-Mail werden in `hugo.toml` gepflegt:

```toml
phone = "+49 123 4567890"
phoneHref = "+491234567890"
email = "kontakt@hebamme-beispiel.de"
```

Wenn WhatsApp genutzt werden soll, kann `whatsappHref` gesetzt werden, zum Beispiel:

```toml
whatsappHref = "https://wa.me/491234567890"
```

## Build für IONOS

```bash
hugo --minify
```

Der fertige Website-Build liegt danach im Ordner `public/`.

## Veröffentlichung über GitHub Pages

Dieses Repository enthält einen GitHub-Actions-Workflow unter `.github/workflows/github-pages.yml`.
Nach einem Push auf `main` wird diese Landingpage automatisch nach GitHub Pages gebaut:

```text
https://mbulti.github.io/webprojects/
```

In GitHub muss unter `Settings > Pages > Build and deployment` als Source `GitHub Actions` ausgewählt sein.

## Upload zu IONOS

Nur den Inhalt von `public/` hochladen, nicht den ganzen Projektordner.

Mögliche Wege:

- SFTP-Zugang von IONOS verwenden.
- IONOS-Dateimanager verwenden.

Nach dem Upload im IONOS-Konto SSL für die Domain aktivieren.

## Docker

Die Seite kann auch als Docker-Container gebaut und lokal getestet werden.

Build aus dem Workspace-Root:

```bash
cd ..
docker build -f hebamme-landingpage/Dockerfile -t hebamme-landingpage .
```

Start:

```bash
docker run --rm -p 8080:80 hebamme-landingpage
```

Danach ist die Seite unter `http://localhost:8080/` erreichbar.

Alternativ mit Docker Compose:

```bash
docker compose up --build
```

Der Container baut die Website mit Hugo, kopiert das gemeinsame Theme aus `../themes/shared-landing/` und serviert die fertigen statischen Dateien mit Nginx.

Beide Landingpages gemeinsam starten:

```bash
cd ..
docker compose -f compose.yml up --build
```

## Veröffentlichung prüfen

- Startseite öffnet korrekt.
- Impressum ist unter `/impressum/` erreichbar.
- Datenschutz ist unter `/datenschutz/` erreichbar.
- Telefonlink funktioniert auf dem Smartphone.
- E-Mail-Link öffnet das Mailprogramm.
- Mobile Ansicht wirkt sauber und lesbar.

## Hinweise

- `public/` nicht manuell bearbeiten. Der Ordner wird bei jedem Build neu erzeugt.
- Bei GitHub Pages wird `baseURL` im Workflow gesetzt, nicht in `hugo.toml`.
- Rechtstexte sind Platzhalter und müssen vor der Veröffentlichung geprüft werden.
- Keine unnötigen Tracking- oder Drittanbieter-Skripte einbauen, wenn sie nicht wirklich gebraucht werden.
