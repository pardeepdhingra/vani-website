# वाणी Vani — Website

Single-page marketing site for **Vani**, a free AAC communication app for children.
100% static (HTML + CSS + a little JS) — hosts anywhere, including **GitHub Pages**.

## Structure

```
index.html        # the whole page
styles.css        # all styling (palette taken from the app logo)
assets/           # logo, app icon, family photo, real simulator screenshots
  screens/        # iPhone + iPad screenshots used across the page
```

## Before you launch — edit the config

At the **bottom of `index.html`**, in the `VANI_CONFIG` block:

```js
const VANI_CONFIG = {
  iosUrl:     "https://apps.apple.com/app/idXXXXXXXXXX",                 // App Store / TestFlight link
  androidUrl: "https://play.google.com/store/apps/details?id=com...",    // Play Store link
  email:      "contact@galasar.com"                                      // feedback / fallback address
};
```

Until `iosUrl` / `androidUrl` are real URLs, those buttons just scroll to the download section.

## Contact form (mailto — no backend, no third-party service)

The form opens the visitor's own email app with the message pre-filled and addressed
to `VANI_CONFIG.email` (contact@galasar.com). No server, no API key, no external service
to ever go down — it just works, including on GitHub Pages.

- On submit, JS builds a `mailto:` link from the name / email / type / message fields and
  opens the visitor's mail client; they press send.
- A small “Prefer email? Write to us directly…” link is shown as a fallback.

> Want submissions to arrive silently (no mail app opening)? Switch to a form service like
> **Web3Forms** or **Formspree**, or host on a platform with serverless functions (e.g.
> Vercel) and POST to an API route. The mailto approach trades that for zero dependencies.

## Run locally

It's static, so any static server works:

```bash
python3 -m http.server 8087
# open http://localhost:8087
```

## Deploy to GitHub Pages

1. Push this folder to a GitHub repo.
2. Repo → **Settings → Pages** → Source: *Deploy from a branch* → branch `main`, folder `/ (root)`.
3. Your site goes live at `https://<username>.github.io/<repo>/`.

(Any static host also works: Netlify, Cloudflare Pages, Vercel, etc.)

## Assets

All images are real: the app logo, icon, the founder's family photo, and live
iPhone + iPad simulator screenshots of Vani. The raw, unprocessed captures live in
`raw-shots/` (git-ignored).
