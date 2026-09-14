Trygg Tallrik — project notes

Front-end structure

- `index.html` — main landing page markup
- `privacy.html` — integritetspolicy (draft, needs legal review before publishing)
- `terms.html` — användarvillkor + prenumerationsvillkor (draft, needs legal review before publishing)
- `css/` — split into:
  - `tokens.css` — design tokens (variables)
  - `base.css` — resets and base layout
  - `buttons.css` — button styles
  - `hero.css`, `app-tour.css`, `features.css`, `how.css`, `about.css`, `faq.css`, `reviews.css`, `cta.css` — per-section styles
  - `legal.css` — shared typography for `privacy.html` / `terms.html`
  - `responsive.css` — media queries and motion preferences
- `assets/icons/` — SVG icons used inline via `<img>`, plus `favicon.svg`
- `assets/images/` — app screenshots (`screen-*.png`) used in the hero and "En titt i appen" section, and `og-image.png` for social sharing previews

Known placeholders to update before launch

- Contact email `hej@tryggtallrik.se` in the footer, FAQ and legal pages — swap for the real support address.
- Company name/organisationsnummer in `privacy.html` (§1).
- Legal review of `privacy.html` and `terms.html` — both are drafts.
- Download button links (`href="#"` in the CTA section) once the App Store / Google Play listings are live.

Quick asset optimization

Install dev dependencies and optimize SVGs:

```bash
npm install
npm run optimize:icons
```
