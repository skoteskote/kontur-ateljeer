# konturateljeer.com

Static site for KONTUR Ateljéer, rebuilt from the old Wix site. No build step,
no framework, no JavaScript — just HTML, one stylesheet and images.

## Layout

```
index.html              Startsida (AKTUELLT)
kreatorer/index.html    Presentationer av kreatörerna
kontakt/index.html      Kontaktuppgifter
konstnärer/index.html   Redirect till /kreatorer/ (gamla Wix-URL:en)
404.html
assets/css/style.css
assets/fonts/           Nunito Sans (self-hosted fallback för Avenir)
assets/img/             Logotyp, affisch, entrébild, ikoner
assets/img/kreatorer/   Porträtt
```

## Editing

Everything is plain HTML. The pieces you'll touch most often:

- **New event on the front page** — edit the `<article class="event">` block in
  `index.html`: title, times, body text and the poster image.
- **Adding or changing a person** — copy an `<article class="person">` block in
  `kreatorer/index.html`. Photo goes in `assets/img/kreatorer/`, roughly 600px
  wide. Keep the `width`/`height` attributes matching the real pixel size so the
  page doesn't jump while images load.
- **Contact details** — `kontakt/index.html`.

The nav is repeated in each file; if you add a page, update it in all of them
and mark the current one with `aria-current="page"`.

## Local preview

```sh
python3 -m http.server 8000
# → http://localhost:8000
```

## Deploying to GitHub Pages

Push to GitHub, then Settings → Pages → *Deploy from a branch* → `main` / `/`
(root). `CNAME` already points at `www.konturateljeer.com`; DNS for that name
needs to move off Wix to GitHub Pages before the domain will resolve here.

## Fonts

The Wix site used Avenir (body) and Helvetica (headings, nav, addresses) via
Wix's licensed web fonts. Those licences don't transfer, so:

- Headings use `Helvetica Neue / Helvetica / Arial` — present on essentially
  every device.
- Body text asks for Avenir first (installed on macOS and iOS) and falls back to
  self-hosted **Nunito Sans**, a free geometric sans close to Avenir, elsewhere.

So Apple visitors see real Avenir and everyone else sees a near match. Drop in
licensed Avenir web fonts later and the fallback stops being used.
