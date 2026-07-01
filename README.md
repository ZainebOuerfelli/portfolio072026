# Zaineb Ouerfelli — One-Page Portfolio

A single-page personal site for **Zaineb Ouerfelli**, Senior Business Transformation Consultant.
Built with semantic HTML + Tailwind CSS, expressing Zaineb's brand to Third Node's craft standard.

## Stack
- **HTML + Tailwind CSS** via the **Tailwind Play CDN** (prototype mode — no build step).
- **DM Sans** (Google Fonts).
- Self-contained: open `index.html` in any browser. No dependencies to install.

## Preview
From this folder:
```
python3 -m http.server 8080
```
Then open <http://localhost:8080>. (Or just double-click `index.html`.)

## Brand tokens (single source of truth)
Defined once in the inline `tailwind.config` at the top of `index.html` — never hardcode values in markup:

| Token | Hex | Role |
|-------|-----|------|
| `bg` | `#eeeeee` | dominant neutral background (~60%) |
| `surface` | `#ffffff` | cards / lift sections |
| `ink` | `#0a0a0a` | body text (black) |
| `muted` | `#565656` | secondary text (AA-safe on bg & surface) |
| `line` | `#d6d6d6` | hairline borders |
| `accent` | `#6fcf97` | primary green (~30%) — philosophy section, chips, case-study numbers |
| `accent-deep` | `#2fa084` | hover / active detail |
| `green-ink` | `#1f6f5f` | deepest emphasis + dark sections/footer; **the only green that carries white text** (white-on-`#6fcf97` fails AA, so light green always uses dark text) |

Type: DM Sans, weights 400 / 500 (`font-medium`) / 700 (`font-bold`). Spacing on an 8pt system.

## Sections
Nav → Hero → The Thinking (philosophy) → About → Selected Work (7-role timeline + 3 case studies) → Toolkit → Contact → Footer.

## Assets (in place)
Both real assets are installed:

1. **Headshot** → `assets/img/zaineb.jpg` ✅ (1254×1254 square; displayed in a 4:5 portrait frame via `object-cover object-top`, so ~12% is trimmed off each side — the centered subject stays safe). To swap, replace this file (a portrait ~4:5 crop will display with no side-trim).
2. **CV PDF** → `assets/Zaineb-Ouerfelli-Resume-2026.pdf` ✅ — wired to both "Download CV" links (hero + contact).

The hero markup still keeps a labeled fallback box behind the image, so if the file is ever removed the layout degrades gracefully instead of showing a broken image.

## Content notes
- "**6+ years**" is used consistently (consulting/transformation career). The agriculture origin is narrative background, not counted in the total.
- Client/program names are used only where already public (Visit Saudi, Ministry of Sports, SDAIA). Other roles are described by sector + country.
- All content traces to the CV and content skeleton — no fabricated metrics, logos, or testimonials.

## Going to production (optional)
The Play CDN is for prototyping. For a production deploy, compile Tailwind with the CLI:
1. `npm install -D tailwindcss`
2. Move the inline `tailwind.config` object into `tailwind.config.js` and add a `content: ["./index.html"]` key.
3. Add an `input.css` with `@tailwind base; @tailwind components; @tailwind utilities;`.
4. `npx tailwindcss -i input.css -o assets/style.css --minify`, then replace the `cdn.tailwindcss.com` script tag with `<link rel="stylesheet" href="assets/style.css">`.
5. Self-host DM Sans or keep the Google Fonts link.

Deploy the folder to any static host (Netlify, Vercel, GitHub Pages, Cloudflare Pages) — it's just static files. The structure also rebuilds cleanly in Framer/Webflow if a no-code platform is preferred later.
