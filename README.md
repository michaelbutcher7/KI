# KI-Magie · Fortbildung Künstliche Intelligenz

Zentrale Plattform für die Fortbildungsreihe **KI-Magie - Vom Prompt zur Praxis**: Theorie, Praxis und niveaudifferenzierte Lernideen für Lehrende und Lernende der Grundschule, Sekundarstufe I und Sekundarstufe II.

> Statisches HTML/CSS/JS - keine Build-Tools, kein Framework. Sofort GitHub-Pages-tauglich.

## Inhalte

- **11 Workshops** mit Theorie, eingebetteten Tools (KI-Blick, Miro) und Ressourcen
- **5 Zielgruppen-Tabs** pro Workshop (Lehrende GS / Sek I / Sek II, Lernende Sek I / Sek II)
- **Niveaudifferenzierte Lernideen** mit kopierbaren Prompts
- **Brand-Design** in den Farben `#283676` (Blau), `#3f77bb` (Hellblau), `#c0ce3a` (Grün)

## Projektstruktur

```
website/
├── index.html                  Landing Page
├── 404.html                    Fehlerseite
├── .nojekyll                   Bypass Jekyll auf GitHub Pages
├── robots.txt                  SEO
├── sitemap.xml                 SEO
├── README.md                   diese Datei
├── css/
│   └── style.css               Komplettes Design-System
├── js/
│   └── main.js                 Tabs, Mobile-Nav, Prompt-Copy, TOC-Scrollspy
├── assets/
│   ├── favicon.svg             Tab-Icon
│   └── og-image.svg            Social-Media-Vorschaubild
└── pages/
    ├── 01-ki-im-alltag.html
    ├── 02-ai-literacy-lehrende.html
    ├── 03-ai-literacy-lernende.html
    ├── 04-technologiewissen.html
    ├── 05-praktische-anwendung.html
    ├── 06-potenziale-bildung.html
    ├── 07-potenziale-alltag.html
    ├── 08-ethik-zukunft.html
    ├── 09-didaktischer-einsatz.html
    ├── 10-einfuehrung-unterricht.html
    └── 11-datenschutz.html
```

## Auf GitHub Pages veröffentlichen

### Variante A · Repo-Root (empfohlen für Project Pages)

1. Neues Repo erstellen, z. B. `ki-magie`.
2. Die Inhalte aus `website/` ins Repo-Root kopieren (nicht den Ordner selbst).
3. Push:
   ```bash
   git init
   git add .
   git commit -m "Initial: KI-Magie"
   git branch -M main
   git remote add origin https://github.com/USER/ki-magie.git
   git push -u origin main
   ```
4. **Repository → Settings → Pages**
   - *Source*: `Deploy from a branch`
   - *Branch*: `main`, Folder: `/ (root)`
   - *Save*
5. Nach ~1 Minute ist die Seite unter `https://USER.github.io/ki-magie/` live.

### Variante B · `/docs`-Ordner

Wer das Projekt zusammen mit anderen Dateien in einem Repo hat:

1. `website/` in `docs/` umbenennen.
2. **Settings → Pages → Branch**: `main`, Folder: `/docs`.

### Variante C · GitHub Actions Workflow

Für mehr Kontrolle (z. B. zukünftige Build-Schritte):

```yaml
# .github/workflows/deploy.yml
name: Deploy KI-Magie
on:
  push:
    branches: [main]
permissions:
  contents: read
  pages: write
  id-token: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v5
      - uses: actions/upload-pages-artifact@v3
        with:
          path: ./website     # bzw. ./
      - id: deployment
        uses: actions/deploy-pages@v4
```

In *Settings → Pages → Source* auf **GitHub Actions** umstellen.

## Vor dem Deploy anpassen

- `robots.txt` - Sitemap-URL eintragen: `https://USER.github.io/REPO/sitemap.xml`
- `sitemap.xml` - URLs absolut machen, sobald Domain bekannt
- Optional: `CNAME`-Datei mit Custom-Domain (`ki-magie.de`) anlegen

## Lokal testen

```bash
cd website
python3 -m http.server 8000
# http://localhost:8000 öffnen
```

> ⚠️ Direktes Öffnen über `file://` funktioniert nur eingeschränkt - Iframes (KI-Blick, Miro) und einige Browser laden nur über HTTP.

## Erweitern

### Neue Lernidee hinzufügen
Im jeweiligen `pages/0X-...html` innerhalb des Tab-Panels einen weiteren `<div class="idea">`-Block ergänzen. Muster:

```html
<div class="idea">
  <h4>🎯 Titel</h4>
  <div class="idea-meta">
    <span class="badge level-1">Niveau 1</span>
    <span class="badge time">⏱ 45 Min</span>
    <span class="badge tool">🛠 ChatGPT</span>
  </div>
  <p>Beschreibung …</p>
  <div class="prompt-box">
    <button class="copy-btn">Kopieren</button>
    <span class="prompt-content">Hier der Prompt …</span>
  </div>
  <div class="idea-reflect"><strong>Reflexion:</strong> …</div>
</div>
```

### Neuen Workshop hinzufügen
1. Neue Datei `pages/12-NAME.html` (an einer bestehenden orientieren).
2. In `index.html` Topic-Card ergänzen.
3. Sitemap-Eintrag in `sitemap.xml` ergänzen.

## Eingebettete Tools

- [KI-Blick](https://www.ki-blick.kmz-es.de/) - KMZ Esslingen
- [Miro Board KI-Magie](https://miro.com/) - Themenmap

## Referenz-Quellen

- [DigCompEdu](https://joint-research-centre.ec.europa.eu/system/files/2018-09/digcompedu_leaflet_de_2018-01.pdf)
- [klicksafe: KI &amp; Me](https://www.klicksafe.de/news/ab-sofort-verfuegbar-ki-and-me-wie-kuenstliche-intelligenz-unser-leben-praegt)
- [Sendung mit der Maus: Wie schreibt eine KI Texte?](https://kinder.wdr.de/tv/die-sendung-mit-der-maus/av/wie-schreibt-eine-ki-texte-100.html)
- [Schokoroboter und Deepfakes (PDF)](https://schokofakes.ai/fileadmin/user_upload/Download/Schokoroboter-und-Deepfakes-2024.pdf)
- [3sat: Kann ich mit KI](https://www.3sat.de/wissen/kann-ich-mit-ki)

## Lizenz

CC BY-SA 4.0 - frei nutzbar mit Namensnennung. Inhalte und Konzept: **Michael Fleischer** · Regioberatender Landesmedienzentrum Baden-Württemberg, Lehrer und freier Referent (DigitalEduLab).
