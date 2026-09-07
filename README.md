# Tata's Batters — Website

The landing page for [Tata's Batters](https://instagram.com/tatasbatters), a Palestinian catering and bakery in the Bay Area. It's a pre-launch "coming soon" page: a look at the menu and the kitchen, plus an email list to sign up for the launch.

One file, `index.html`. No build step, no framework, no dependencies to install. Fonts load from Google Fonts; everything else is inline or in `/media`.

## What's on the page

- **Hero** — logo, tagline, and two calls to action (join the list, follow on Instagram)
- **What we'll be baking** — a menu tease with English and Arabic names, grouped into Savory, Bread, and Sweets. No prices, nothing orderable yet.
- **From the kitchen** — a four-tile gallery, one of which is a short syrup-pour video
- **Join the list** — an email capture form (see below)
- **Footer** — Instagram, phone `(408) 658-9079`, email `tatasbatters@gmail.com`

Design is a cream, olive, and gold palette with arched-dome and olive-branch motifs, set in Fraunces, Work Sans, Space Mono, and Noto Naskh Arabic. It respects `prefers-reduced-motion`: the hero animation and the gallery video only play if the visitor hasn't asked motion off.

## The waitlist form

Right now the form has no backend. On submit it opens the visitor's mail app with a pre-filled message to `tatasbatters@gmail.com`, and they still have to press send. That works with zero setup but loses anyone who doesn't finish.

**To switch to a real form** (recommended once signups start coming in), edit `index.html`:

1. On the `<form id="waitlist-form">`, set `action="https://formspree.io/f/YOUR_ID"` and `method="post"` (or a Tally / Google Form endpoint).
2. Delete the `data-mailto` attribute on that same `<form>`.

The script at the bottom of the file checks for `data-mailto`. Once it's gone, the browser just posts the form normally and the script stays out of the way.

## Media

`index.html` references these files in a `media/` folder. They are not committed to this repo yet. Add them before deploying:

```
media/hero.jpg          media/hero.webp
media/manoushe.jpg      media/manoushe.webp
media/fatayer.jpg       media/fatayer.webp
media/atayef.jpg        media/atayef.webp
media/hilbeh-poster.jpg media/hilbeh-syrup.mp4
media/og-cover.jpg      (link-preview image, 1200x630)
media/favicon.ico  media/icon-32.png  media/apple-touch-icon.png
```

Every image tag has a fallback, so a missing file degrades to a solid tile rather than a broken image, but the page is meant to be seen with all of them.

## Deploying

It's a static site. Any static host works (Vercel, Netlify, GitHub Pages, Cloudflare Pages). Drop `index.html` and the `media/` folder at the root.

### Before it goes live

- [ ] Replace `https://tatasbatters.vercel.app` with the real domain in the three Open Graph / Twitter URLs near the top of `index.html`. Facebook, WhatsApp, and Instagram need absolute URLs or the preview image won't render.
- [ ] Add the `media/` assets listed above
- [ ] Point the waitlist form at a real backend (see above)
- [ ] Connect the custom domain
- [ ] Confirm the favicon files are in place
- [ ] Add a Privacy Policy page
- [ ] Add a Terms & Conditions page

(The last four are the standing pre-launch checklist for any Tata's Batters site.)

## Files

```
index.html   the entire page
media/        images and video (add before deploy — not in the repo yet)
```
