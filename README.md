# Mugunda Vocational Training Centre — Website

Static website for Mugunda VTC (formerly Mugunda Adult Learning Centre).

**Stack:** Plain HTML, CSS, JavaScript. No build step, no framework.
**Deploy target:** Netlify (currently at `mugunda.netlify.app` — will be updated).

---

## Local development

Serve the folder with any static server. Some options:

```bash
# Python
python -m http.server 8000

# Node (if you have it)
npx serve .

# VS Code
Install "Live Server" extension, right-click index.html → Open with Live Server
```

Then open `http://localhost:8000`.

---

## Structure

```
mugunda/
├── index.html              Homepage
├── about/                  About Us (history, facilities, leadership)
├── courses/                Courses + Downloads
├── admissions/             Apply Now target
├── contact/                Contact info + map
├── support-us/             Donor-facing page
└── assets/
    ├── css/                Global CSS, imported via main.css
    ├── js/                 Vanilla JS (nav toggle, WhatsApp button)
    └── images/             All photos + logo
```

## Editing CSS

All CSS is global. Every page loads `/assets/css/main.css`, which `@import`s every other stylesheet.

- Change brand colors → `assets/css/base/variables.css`
- Change nav appearance → `assets/css/layout/nav.css`
- Change button styles → `assets/css/components/buttons.css`
- Homepage-specific styles → `assets/css/pages/home.css`

## Editing HTML

The `<nav>` and `<footer>` are duplicated in each page. If you change one, sync across all six.

---

## Brand

- **Navy:** `#1a2b5c` (primary)
- **Gold:** `#f4b840` (accent, CTAs)
- **Cream:** `#faf7f0` (page background)
- **Display font:** Fraunces (serif)
- **Body font:** DM Sans (sans-serif)
