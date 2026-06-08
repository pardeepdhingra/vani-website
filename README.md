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

## Contact form (FormSubmit.co — no backend)

The form posts directly to **FormSubmit.co**, which forwards messages to
`contact@galasar.com`. No server, no API key — works on static hosting.

- The form `action` is `https://formsubmit.co/contact@galasar.com`.
- JavaScript submits it via FormSubmit's AJAX endpoint so the visitor stays on the page
  with an inline “thank you”. If JS is off or fetch fails, it falls back to a normal submit.
- **One-time activation:** the *first* submission triggers a confirmation email to
  `contact@galasar.com`. Click the link in that email once, and all future messages arrive.
- A hidden `_honey` field blocks spam bots.

> Want to hide the email address in the HTML? After activation, FormSubmit gives you a
> hashed endpoint like `https://formsubmit.co/abcdef123…`. Swap it into the form's `action`.

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
