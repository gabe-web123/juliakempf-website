# Julia Kempf — Site

Six-page static site for Julia Kempf (soprano &amp; voice teacher).
No build step. Plain HTML + CSS, deployed via GitHub → Vercel.

## Files

```
julia-site/
├── index.html        Home
├── about.html        About / bio
├── repertoire.html   Genre catalog (resume style)
├── demos.html        Sample demos
├── teaching.html     Voice teaching
├── contact.html      Contact form (Formspree-wired)
├── thanks.html       Form success page
├── styles.css        Shared stylesheet
├── vercel.json       Vercel config (clean URLs)
├── copy.md           Editable copy template
└── README.md         This file
```

## Deploy to Vercel

This site uses the same GitHub → Vercel pipeline as your other projects.

### First-time setup

1. Make sure the repo is on GitHub (already pushed by the deploy script — see below).
2. Go to <https://vercel.com/new>
3. Click **Import** next to the `juliakempf-website` repo
4. Framework preset: **Other** (Vercel will auto-detect static HTML)
5. Build command: *(leave blank)*
6. Output directory: *(leave blank — it's the root)*
7. Click **Deploy**

You'll get a URL like `juliakempf-website.vercel.app` immediately.

### Connecting a custom domain

In Vercel dashboard → Project → **Settings → Domains**, add `juliakempf.com` (or whichever domain) and follow the DNS instructions.

### Updates

Every `git push` to `main` triggers a new Vercel deploy automatically. No manual step needed.

## Clean URLs

`vercel.json` has `cleanUrls: true`, so visitors see `/about` instead of `/about.html`. The HTML files keep their `.html` names locally for easy preview — Vercel rewrites them on the deployed site.

## Contact form — Formspree

The contact form posts to [Formspree](https://formspree.io) (free tier covers 50 submissions/month, with built-in spam filtering).

### Setup (one-time, ~60 seconds)

1. Sign up at <https://formspree.io> with `juliaekempf@gmail.com`
2. Create a new form (call it whatever — "Julia Kempf Site Contact" or similar)
3. Copy the form ID (looks like `xyzabcde`)
4. Open `contact.html`, find this line near the top of the `<form>`:

   ```html
   <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST">
   ```

5. Replace `YOUR_FORMSPREE_ID` with your real ID
6. Commit + push — done.

Every submission will be emailed to the Formspree-registered address, and a dashboard shows all entries.

## Editing content

All copy lives in `copy.md` — it's a labeled template that maps to every text field on the site. Edit there, then ask Claude:

> apply copy.md updates to the site

…and the HTML files will be updated automatically.

Color, typography, spacing all live in `styles.css` — edit once, all pages update.

## Local preview

Just open any `.html` file in a browser. Internet required for Google Fonts (Cormorant Garamond + Cormorant SC + Jost).

For local clean-URL preview:

```bash
npx vercel dev
```

(Or just `npx serve .` for plain static serving.)
