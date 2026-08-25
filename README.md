# AcreetionOS Docs

Official documentation site for [AcreetionOS](https://acreetionos.org) — live at **https://docs.acreetionos.org**.

Built with [Antora](https://antora.org) from AsciiDoc sources. Theme matches acreetionos.org (dark `#121212`, green `#2ecc71`).

## Components

| Component | Pages | Focus |
|---|---|---|
| wiki | 39 | Task-oriented guides for daily use |
| install-guide | 12 | Download → USB → Calamares → desktop |
| admin-guide | 21 | systemd, storage, boot chain, tuning |
| release-notes | 5 | ISO contents, update highlights, known issues |
| editions | 6 | Standard / Immutable / Lightweight / Mobile |
| contributor | 10 | Bugs, testing, packaging, governance |

**91 content pages** total, plus client-side search (@antora/lunr-extension) and per-page SEO meta (description, OG tags, canonical, sitemap).

## Build locally

```bash
npm install
npx antora antora-playbook.yml   # output in public/
```

The UI bundle (`ui-bundle.zip`) is derived from the Antora default UI with an appended AcreetionOS theme layer; regenerate via `ui-src/` if needed.

## Deploy

`public/` (plus `CNAME`, `.nojekyll`, `_img/og-image.png`) publishes to the `gh-pages` branch → GitHub Pages → `docs.acreetionos.org`.

A self-contained landing page lives at `landing/index.html`; it is mirrored to `/var/www/docs.acreetionos.org/` on the us.iso server (nginx vhost `docs.acreetionos.org`) as the origin fallback.

## Editing

Pages are plain AsciiDoc under `components/<component>/modules/ROOT/pages/`. Every page needs a `:description:` attribute (feeds `<meta name=description>`). Cross-component links use `xref:component::page.adoc[Label]`. See `contributor::docs-style.adoc`.
