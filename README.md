# Training Hub — source

Everything needed to run and deploy the GFF/SOS Training Hub.

## Files
- `Training Hub.dc.html` — the main hub (entry point)
- `Training Hub Login.dc.html` — login screen
- `support.js` — required runtime (loaded by both pages)
- `hub-data.js` — all content (departments, courses, lessons, career ladder)
- `hub-images.js` — inlined images (career photos, logos, examples)
- `image-slot.js` — image-slot web component
- `assets/` — logos, murals, avatars, career photos
- `Training Hub (standalone single-file).html` — one fully self-contained copy
  with everything inlined; open directly, no server needed (offline-friendly).

## Run locally
The `.dc.html` pages load `support.js` + data/image scripts as separate files,
so serve over HTTP (not `file://`):

    python3 -m http.server 8000
    # or:  npx serve .

Then open http://localhost:8000/Training%20Hub.dc.html

## Deploy to the live subdomain
Serve these files as static files behind training-hub.getfoundfirst.com.
Any static host works (Netlify, Vercel, Cloudflare Pages, GitHub Pages, S3, nginx).
The entry point is `Training Hub.dc.html`.

To publish updates: replace these files with the latest versions from this repo
and redeploy. The single-file standalone is optional — the deployed site uses
the multi-file version.

## Notes for the dev (Rasel)
- No build step. These are plain static files.
- If you want a clean URL, alias `Training Hub.dc.html` to `/` (index) at the host.
- `.dc.html` is just HTML — the extension can be renamed to `.html` if the host
  prefers, as long as the internal links between hub and login are updated to match.
