# AGENTS.md

This repo is a **single-file interactive sales presentation** (pitch deck) built with vanilla HTML/CSS/JS.

## Core facts

- **All code** lives in `index.html` — CSS in `<style>`, JS in `<script>`. No external files.
- **No build tools** — open directly in browser or serve via static server. No `npm`, bundlers, or dependencies.
- **Deployment** — GitHub Pages auto-deploys on push to `main` via `.github/workflows/deploy.yml`. The workflow uploads the **entire root directory**.
- **No tests** — none configured.
- **No package.json** — zero tooling, zero frameworks.

## Editing guidelines

- This is an **interactive slide deck**, not a static landing page. Navigation uses `data-slide` attributes and JS controls (`.slide` / `.active`).
- **Slide structure**: Each `<div class="slide" data-slide="N">` is one screen. Add/remove slides by editing these blocks and updating navigation logic.
- **Theme system**: CSS variables in `:root` (dark default). Light theme via `.light-theme` class on `<body>`. Toggle persists to `localStorage.theme`.
- **Keep single-file**: Do NOT split into `.css` or `.js` files unless explicitly requested. Inline styles live in the `<head>`.
- **Key JS functions**: `nextSlide()`, `prevSlide()`, `updateSlide()`, `openModal()`, `closeModal()` — use these to wire new interactive elements.
- **Progress bar** and slide counter auto-update via JS — `data-slide` numbering, `totalSlides` var, and the counter span must stay in sync.
- If adding icons/emojis, use the same visual language (Bebas Neue for headers, Playfair Display for headings, Poppins for body).
- **Business-focused language**: avoid technical jargon — the audience is barbers, not developers.

## Commands

```bash
# Quick local preview
python -m http.server 8000
# Open http://localhost:8000

# Deploy
git add index.html
git commit -m "Update pitch deck"
git push origin main  # GitHub Pages deploys automatically
```

## Gotchas

- **Do not add build tools or split files** — this project's philosophy is zero-dependency single-file.
- **Don't move static assets** — none exist currently. If you add images, keep them inline (base64) or hosted; don't create `img/` folders.
- **Deploy workflow** uploads the root — never relocate `index.html`.
- **Form/Buy buttons** in the final slide call `openModal()` — don't replace with external links unless user confirms.
- Preserve the **comparison table** (ahorro vs apps) and **senior showcase** sections — those are the key differentiators for Legado Barber.
- Use **mentoría empresarial**, not "asesoría legal" — avoid liability language.
- Keep **numbers complete** (`$350.000`, not `$350k`) — clearer for business audiences.
