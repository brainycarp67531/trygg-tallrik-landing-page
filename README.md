Trygg Tallrik — project notes

Front-end structure

- `index.html` — main markup
- `css/` — split into:
  - `tokens.css` — design tokens (variables)
  - `base.css` — resets and base layout
  - `buttons.css` — button styles
  - `hero.css`, `features.css`, `how.css`, `reviews.css`, `cta.css` — per-section styles
  - `responsive.css` — media queries and motion preferences
- `assets/icons/` — SVG icons used inline via `<img>`

Quick asset optimization

Install dev dependencies and optimize SVGs:

```bash
npm install
npm run optimize:icons
```
