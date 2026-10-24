# Motivify-site

The website for Motivify, the Stoic passages, practices and habits app for Android: a landing page, the privacy policy and the terms of use. Plain HTML and one `style.css` in the Stoa design system, served by GitHub Pages from `main` at https://mykhailonester.github.io/Motivify-site/. No build step, no scripts, and nothing is loaded from another site.

## Preview

```
python3 -m http.server 8000
```

Run it from the repo root and open http://localhost:8000/. Every link and asset path is relative, so the site works both at the root and under `/Motivify-site/`.

## Layout

- `index.html`, `privacy/index.html`, `terms/index.html`: the three pages, all styled by `style.css`
- `assets/img/`: app captures as webp, icons, the video poster and `og.png`
- `assets/video/`: the vertical promo video (no audio)
- `assets/fonts/`: Newsreader and Instrument Sans, subset to Latin as woff2, with their SIL OFL licences
- `assets/og/og.html`: the source of `og.png`
- `sitemap.xml`, `robots.txt`, `.nojekyll`

## Assets

The captures, icon and promo video come from the app repo's 2.1.0 store-listing graphics, so the site tells the same story as the Google Play listing. When the listing changes, update the captures and the numbers on the landing page with it.

`og.png` (1200×630) is rendered from `assets/og/og.html` with headless Chrome at 2x and scaled down:

```
chrome --headless=new --hide-scrollbars --force-device-scale-factor=2 --allow-file-access-from-files \
  --window-size=1200,630 --screenshot=og-2x.png assets/og/og.html
sips -z 630 1200 og-2x.png --out assets/img/og.png
```

## Contact

The contact address is the app's own support address, written with its `@` as the HTML entity `&#64;` in every page so simple scrapers miss it; keep it that way when editing. Never put a personal address in this public repo.
