# Distance Development Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a static one-page site for Distance Development at disdev.co listing Rumbo and Signup Builder with contact info.

**Architecture:** Hand-written `index.html` + `styles.css` in the repo root, no build step or JS. Light/dark via `prefers-color-scheme`. Hosted as plain files.

**Tech Stack:** HTML5, CSS3 (custom properties, grid), SVG favicon.

**Spec:** `docs/superpowers/specs/2026-10-07-disdev-website-design.md`

## Global Constraints

- Static HTML/CSS only; no JavaScript, build step, backend or contact form.
- Canonical URL `https://disdev.co/`.
- Contact email `dustin@disdev.co` via `mailto:`; LinkedIn `https://www.linkedin.com/in/dustin-speer/`.
- Products: **Rumbo** (online learning platform) and **Signup Builder** (volunteer signup form service); both show a "Coming soon" state, no outbound link.
- Automatic light/dark mode; responsive phone to desktop; semantic HTML; accessible contrast and focus states.
- Footer: © Distance Development.

## Review Focus

- Very narrow phone width (320px): no horizontal scroll, cards stack.
- Dark mode: text and "Coming soon" badge keep readable contrast.
- Keyboard navigation: header and contact links show a visible focus ring; skip-to-content works.
- "Coming soon" cards must not render as dead links (no `<a href="#">`).
- Link previews: Open Graph/meta description present so sharing the URL shows a title and description.

---

### Task 1: Page content and styling

**Files:**
- Create: `index.html`
- Create: `styles.css`
- Create: `favicon.svg`

**Interfaces:**
- Produces: `index.html` with section ids `#products`, `#about`, `#contact`; `styles.css` with tokens `--bg --fg --muted --accent --card --border`.

- [ ] **Step 1: Create `favicon.svg`**

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64"><rect width="64" height="64" rx="14" fill="#4f46e5"/><text x="32" y="44" text-anchor="middle" font-family="system-ui,sans-serif" font-size="34" font-weight="700" fill="#fff">D</text></svg>
```

- [ ] **Step 2: Create `index.html`**

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Distance Development</title>
  <meta name="description" content="Distance Development builds products and services with software and AI expertise. Home of Rumbo and Signup Builder.">
  <link rel="canonical" href="https://disdev.co/">
  <link rel="icon" href="favicon.svg" type="image/svg+xml">
  <meta property="og:type" content="website">
  <meta property="og:title" content="Distance Development">
  <meta property="og:description" content="Products and services built with software and AI expertise.">
  <meta property="og:url" content="https://disdev.co/">
  <meta name="color-scheme" content="light dark">
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <a class="skip" href="#main">Skip to content</a>
  <header class="site-header">
    <div class="wrap bar">
      <a class="brand" href="#top">Distance Development</a>
      <nav aria-label="Primary">
        <a href="#products">Products</a>
        <a href="#contact">Contact</a>
      </nav>
    </div>
  </header>

  <main id="main">
    <section class="hero wrap" id="top">
      <h1>We build products that put software and AI to work.</h1>
      <p class="lead">Distance Development is a product development business creating focused tools and services, from idea to launch.</p>
    </section>

    <section class="wrap" id="products" aria-labelledby="products-h">
      <h2 id="products-h">Products</h2>
      <div class="cards">
        <article class="card">
          <h3>Rumbo</h3>
          <p>An online learning platform for creating and delivering courses. Built to make teaching and learning simple.</p>
          <span class="badge">Coming soon</span>
        </article>
        <article class="card">
          <h3>Signup Builder</h3>
          <p>A volunteer signup form service. Create a signup, share a link, and let people claim the spots that work for them.</p>
          <span class="badge">Coming soon</span>
        </article>
      </div>
    </section>

    <section class="wrap" id="about" aria-labelledby="about-h">
      <h2 id="about-h">About</h2>
      <p>Distance Development is led by Dustin Speer, a software developer focused on practical applications of AI. We design, build and run products and services that solve real problems.</p>
    </section>

    <section class="wrap" id="contact" aria-labelledby="contact-h">
      <h2 id="contact-h">Contact</h2>
      <ul class="contact">
        <li><a href="mailto:dustin@disdev.co">dustin@disdev.co</a></li>
        <li><a href="https://www.linkedin.com/in/dustin-speer/" rel="noopener">LinkedIn</a></li>
      </ul>
    </section>
  </main>

  <footer class="site-footer">
    <div class="wrap">&copy; Distance Development</div>
  </footer>
</body>
</html>
```

- [ ] **Step 3: Create `styles.css`**

```css
:root {
  --bg: #ffffff; --fg: #14151a; --muted: #565b6b;
  --accent: #4338ca; --card: #f6f6fa; --border: #e2e3ec;
  --max: 64rem;
}
@media (prefers-color-scheme: dark) {
  :root {
    --bg: #0f1015; --fg: #ececf2; --muted: #a2a6b8;
    --accent: #a5b4fc; --card: #181a22; --border: #2a2d3a;
  }
}
* { box-sizing: border-box; }
html { scroll-behavior: smooth; }
body {
  margin: 0; background: var(--bg); color: var(--fg);
  font: 1rem/1.6 system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
}
a { color: var(--accent); }
a:focus-visible { outline: 3px solid var(--accent); outline-offset: 3px; border-radius: 4px; }
.wrap { max-width: var(--max); margin: 0 auto; padding: 0 1rem; }
.skip { position: absolute; left: -999px; top: 0; background: var(--bg); padding: .5rem 1rem; z-index: 10; }
.skip:focus { left: 1rem; top: 1rem; }

.site-header { border-bottom: 1px solid var(--border); }
.bar { display: flex; justify-content: space-between; align-items: center; padding-top: 1rem; padding-bottom: 1rem; gap: 1rem; flex-wrap: wrap; }
.brand { font-weight: 700; color: var(--fg); text-decoration: none; }
nav a { margin-left: 1.25rem; text-decoration: none; }
nav a:hover { text-decoration: underline; }

section { padding-top: 3rem; padding-bottom: 1rem; }
.hero { padding-top: 5rem; padding-bottom: 2rem; }
h1 { font-size: clamp(2rem, 6vw, 3.25rem); line-height: 1.15; margin: 0 0 1rem; max-width: 18ch; }
h2 { font-size: 1.5rem; margin: 0 0 1rem; }
h3 { margin: 0 0 .5rem; font-size: 1.25rem; }
.lead { font-size: 1.2rem; color: var(--muted); max-width: 40rem; margin: 0; }

.cards { display: grid; gap: 1rem; grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr)); }
.card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 1.5rem; }
.card p { color: var(--muted); margin: 0 0 1rem; }
.badge { display: inline-block; font-size: .8rem; font-weight: 600; padding: .2rem .65rem; border-radius: 999px; border: 1px solid var(--accent); color: var(--accent); }

.contact { list-style: none; padding: 0; margin: 0; display: flex; gap: 1.5rem; flex-wrap: wrap; }
.site-footer { margin-top: 4rem; padding: 1.5rem 0; border-top: 1px solid var(--border); color: var(--muted); font-size: .9rem; }
```

- [ ] **Step 4: Verify in a browser**

Run: `open index.html`
Expected: hero, two "Coming soon" cards, About, Contact (mailto and LinkedIn links), footer. Check 320px width (no horizontal scroll), dark mode (toggle macOS appearance), Tab key shows focus rings and skip link.

- [ ] **Step 5: Verify no dead links**

Run: `grep -n 'href="#"' index.html; grep -c 'href="#' index.html`
Expected: first command prints nothing; only anchors are `#main`, `#top`, `#products`, `#contact`.

- [ ] **Step 6: Commit**

```bash
git add index.html styles.css favicon.svg
git commit -m "feat: add Distance Development one-page site"
```

### Task 2: README and hosting notes

**Files:**
- Create: `README.md`

- [ ] **Step 1: Create `README.md`**

```markdown
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
```

- [ ] **Step 2: Commit**

```bash
git add README.md
git commit -m "docs: add README with preview and hosting notes"
```

---

## Self-review
- Spec coverage: header, hero, products, about, contact, footer, favicon, meta/OG/canonical, light/dark, responsive, README all covered.
- Placeholders: none; product cards intentionally show "Coming soon" per spec.
- Review Focus items are exercised by Task 1 Steps 4-5.
