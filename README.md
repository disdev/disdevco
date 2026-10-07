# Distance Development

Static site for https://disdev.co. Plain HTML/CSS, no build step.

## Preview
Open `index.html` in a browser, or run `python3 -m http.server 8000` and visit http://localhost:8000.

## Edit
- Content: `index.html`
- Styling and colors: `styles.css` (tokens at the top)
- When Rumbo or Signup Builder launches, replace its `<span class="badge">Coming soon</span>` with `<a href="URL">Visit Rumbo</a>`.

## Hosting
Deploy the repo root as a static site (GitHub Pages, Netlify or Cloudflare Pages) and point the disdev.co DNS at it.
