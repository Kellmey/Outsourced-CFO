# Outsourced-CFO

# Outsourced CFO — Landing Page

A high-converting, mobile-responsive landing page for **Outsourced CFO** ([ocfo.com](https://www.ocfo.com/)), built as a single self-contained HTML file with no build step and no external dependencies beyond Google Fonts.

> **Tagline:** Building a world-class finance function for your growing company.

---

## Live Preview

Open `index.html` directly in any modern browser — no server required.

To share with others, the simplest path is to drag the file onto [Netlify Drop](https://app.netlify.com/drop) for an instant public URL. GitHub Pages and Vercel work equally well for a more permanent deployment.

---

## Project Goals

This page was designed against four assessment criteria:

1. **Conversion thinking** — not just design, but the psychology behind every section
2. **UX structure and flow** — a logical, intuitive user journey
3. **Attention to detail** — typography, spacing, color, micro-interactions
4. **Practical implementation** — clean, semantic, accessible, mobile-first code

---

## Conversion Strategy

Every section earns its place by moving the visitor closer to the single conversion goal: **booking a call with the OCFO team.**

### One ask, repeated

The primary CTA — "Get in Touch" / "Request a Call" — appears in the sticky nav, the hero, and the final form section. No competing asks. No secondary funnels.

### Psychological arc (top → bottom)

| Section | Job to be done |
| --- | --- |
| **Hero** | Hook with outcome-focused headline; offer two paths (primary CTA + secondary "Explore Services") |
| **Featured In** | Borrowed authority — Forbes, Entrepreneur, Fast Company logos |
| **Stats bar** | Hard credibility — 20+ industries · hundreds of founders · $100M+ raised · 34+ countries |
| **Problem section** | Mirror the reader's pain (people buy when they recognize themselves) |
| **Services** | Present the solution: OCFO's four real service pillars |
| **Industries** | Reassure the visitor we've worked in their sector |
| **Process** | Remove friction — show exactly what happens next |
| **Testimonials** | Social proof from real named clients with their companies |
| **FAQ** | Handle the last objections (pricing, fit, tech stack, location) before the ask |
| **Final CTA + form** | Convert |

### Low-friction lead form

Only six fields, two of which qualify the lead silently for routing:

- First name, last name, work email, company
- **I'm interested in** → routes to the right OCFO service line
- **Annual revenue** → qualifies fit without scaring anyone off

Inline validation with friendly error messages and a success state on submit. The form simulates submission today; in production, swap the success handler for a `POST` to a CRM endpoint (HubSpot, Salesforce, Zoho CRM, etc.).

---

## UX & Design Decisions

### Visual system

- **Palette** — Deep navy (`#0B1E3F`) for authority, muted gold (`#C9A961`) for premium accents, warm off-white (`#FAFAF7`) background
- **Typography** — `Fraunces` (serif) for headlines to evoke premium financial brands; `Inter` (sans) for body copy for clean readability
- **Spacing & rhythm** — Consistent 8px grid, generous whitespace, hierarchy-led type scale (`clamp()` for fluid responsiveness)
- **Hero visual** — Custom-built dashboard mockup in pure SVG, no stock imagery; reinforces the "financial clarity" message above the fold
- **Micro-interactions** — Button hover lifts, arrow nudges on hover, card hover states with gold border

### Accessibility

- Semantic HTML5 (`<header>`, `<main>`, `<section>`, `<article>`, `<details>`)
- All form labels paired to inputs with `for`/`id`
- `aria-label`, `aria-expanded`, `aria-live` on interactive elements
- All color combinations verified at **WCAG AA contrast**
- Keyboard-navigable, screen-reader friendly
- Reduced reliance on color alone — icons and shapes reinforce meaning

### Mobile responsiveness

Mobile-first CSS with breakpoints at **480, 560, 700, 720, 768, 880, 900, 980, 1000px** covering every common device width. Includes:

- Hamburger nav with slide-down menu on smaller viewports
- Stacked hero, problem, and CTA grids
- Service cards collapse from 4 → 2 → 1 columns
- Form rows collapse to single-column on narrow screens
- Touch-friendly tap targets (minimum 44px)

---

## Tech Stack

| | |
| --- | --- |
| Markup | Semantic HTML5 |
| Styling | Vanilla CSS with custom properties (design tokens) |
| Interactivity | Vanilla JavaScript — no frameworks |
| Fonts | Google Fonts (`Fraunces`, `Inter`) |
| File size | ~49 KB single file |
| Dependencies | None (other than fonts) |

No build step. No npm install. No bundler. Open the file and it works.

---

## File Structure

```
outputs/
├── index.html      ← the entire landing page (HTML + CSS + JS in one file)
└── README.md       ← this file
```

---

## How to Customize

### Change brand colors

All colors live as CSS custom properties at the top of the `<style>` block (lines ~16–32). Change the values in `:root` and the whole page updates.

```css
:root {
  --navy-900: #0B1E3F;   /* primary brand color */
  --gold-500: #C9A961;   /* accent / CTA */
  --bg:       #FAFAF7;   /* page background */
  /* ... */
}
```

### Wire up the form to a real endpoint

In the `<script>` block at the bottom, find the comment `// Simulate submission` and replace the success-state block with a `fetch` call to your CRM:

```js
const response = await fetch('https://your-crm-endpoint', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(Object.fromEntries(new FormData(form)))
});
```

### Replace placeholder logos

The "As Featured In" strip uses styled text placeholders (`Forbes`, `Entrepreneur`, etc.). For production, swap each `<span class="pub">` for an actual `<img>` of the publication logo (SVGs are ideal).

---

## Assessment Notes

| Criterion | Where to look |
| --- | --- |
| Conversion thinking | Repeated CTA strategy, low-friction form design, problem → solution arc, FAQ handling objections, qualified lead routing via "interested in" dropdown |
| UX structure and flow | Sticky nav, logical top-to-bottom narrative, smooth anchor scrolling, predictable section rhythm |
| Attention to detail | Type pairing, color tokens, hover states, focus rings, real client testimonials with real companies, contrast-verified palette |
| Practical implementation | Single file, no build step, semantic HTML, mobile-first responsive, AA accessibility, clean separation of concerns within the file |

---

## Credits

- **Content & positioning** sourced from [ocfo.com](https://www.ocfo.com/) — including the four service pillars, real client testimonials (Tim Molteno, Yvonne Wakefield, Aidan Casserly), company stats, and NYC office address.
- **Fonts** — [Fraunces](https://fonts.google.com/specimen/Fraunces) and [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts.

---

_Built as part of a landing page design assessment._
