# Distance Development Website — Design

## Purpose
A static, one-page marketing site for Distance Development (disdev.co), a product development business building products and services with software and AI expertise. Audience is mixed (prospective clients, people following the products, collaborators), so the page is simple and credible without pushing a single call to action.

## Scope
- Static HTML/CSS only. No build step, no JavaScript framework, no backend, no contact form.
- Hosted as plain files (GitHub Pages / Netlify / Cloudflare Pages) at https://disdev.co.

## Files
- `index.html` — the page
- `styles.css` — all styling
- `favicon.svg` — simple monogram icon
- `README.md` — how to preview and host

## Page structure
1. **Header** — "Distance Development" wordmark; anchor links to Products and Contact.
2. **Hero** — one-line statement (product development with software and AI expertise) plus a short supporting sentence.
3. **Products** — two cards, each with name, two-sentence description, and link button:
   - **Rumbo** — online learning platform.
   - **Signup Builder** — volunteer signup form service.
4. **About** — short paragraph on background and approach (optional; may be cut).
5. **Contact** — email via `mailto:dustin@disdev.co` link and LinkedIn: https://www.linkedin.com/in/dustin-speer/
6. **Footer** — © Distance Development.

## Visual design
Typography-led, system font stack, generous whitespace, a single accent color, automatic light/dark mode via `prefers-color-scheme`, responsive from phone to desktop.

## Quality
Semantic HTML, accessible contrast and focus states, `<title>`, meta description, Open Graph tags, canonical URL `https://disdev.co/`. Verified in a browser at phone and desktop widths before completion.

## Open items
- Product URLs for Rumbo and Signup Builder; until provided, cards show a "Coming soon" state instead of a link.
- Tagline / accent color: neutral defaults unless specified.
