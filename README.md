# Surface Finish Sampler

A lightweight web UI for previewing metal finishes on a part before committing to
fabrication. Start from a CAD line drawing, then apply a fully rendered die-cast
finish from a dropdown, or compare two finishes side by side.

## What's here

- `index.html` — the entire app, self-contained. All preview images are embedded as
  data URIs, so it runs offline with no build step and no external assets.

## Run locally

Just open the file:

```bash
open index.html      # macOS
# or double-click index.html in your file browser
```

Or serve it (optional):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Features (V1)

- **Line drawing as the starting point** — the app opens on the original CAD linework.
- **Finish dropdown** — apply any of 8 states (line drawing, copper, chem film,
  chromate, clear chromate, copper-nickel-tin, cobalt-tin, electroless nickel) with
  a soft crossfade.
- **Compare mode** — split the view into two panels, each with its own finish.
- **Upload** — drop in another drawing to view it in the stage. (Automatically
  *rendering* finishes onto a new upload is a backend step, not included in this shell.)

## Deploy a live link with GitHub Pages

After pushing this repo to GitHub (see below), enable Pages:

1. Repo **Settings → Pages**.
2. Under **Build and deployment**, set **Source = Deploy from a branch**.
3. Choose branch **main** and folder **/ (root)**, then **Save**.
4. Your live URL appears within a minute or two at:
   `https://<your-username>.github.io/<repo-name>/`

## Roadmap

- Draggable before/after slider (requires pose-matched renders).
- Finish swatches as clickable chips; dropdown grouped by family
  (bright / satin / black / colored).
- Real upload → finish-render pipeline via a 3D renderer (Three.js) or Adobe Firefly.
- Expand from 8 finishes toward the full surface-finish menu.

## Notes

- The copper render uses a slightly different camera angle than the other six
  renders, so it won't register pixel-for-pixel in compare mode. The other six share
  the line drawing's exact pose.
