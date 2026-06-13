# Wise World AI Studio

Source for [wiseworldai.com](https://wiseworldai.com) — a portfolio site for the Wise World AI product stack.

## Stack

Single-file static site: HTML + inline CSS + vanilla canvas animations. No build step, no framework, no JS dependencies. Designed to be readable end-to-end and deployable as a folder.

- **Entrypoint:** `site/index.html`
- **Assets:** `site/assets/`

## Deploy

```sh
# Anything that serves static files works.
cd site && python3 -m http.server 8765
# → http://localhost:8765
```

Production is on Netlify (drop the `site/` folder, or point Netlify at this repo with publish directory `site`).

## Animations

Every product showcase has 4 inline canvas animations (hero / problem / architecture / features). They share a small runtime defined inside `site/index.html`:

- `makeAnimation(canvas, drawFn, opts)` — `requestAnimationFrame` loop with DPR scaling and `ResizeObserver`
- `mountAnimations()` — wires `IntersectionObserver` so each animation only renders when in view
- `ANIMS[name]` registry — one `draw(ctx, p, w, h, state)` per slot

Adding a product means appending one entry to the `PRODUCTS` array and four entries to `ANIMS`.
