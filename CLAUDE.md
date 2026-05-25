# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

ComeShine is a personal/business profile site for 麓絵里 (Eli Fumoto), owner of ComeShine — a dining hall and inn opening in Nagato Yumoto Onsen, Yamaguchi, Japan in Summer 2026.

## Architecture

The entire site is a single self-contained file: **`index.html`**. There is no build step, no package manager, and no external dependencies beyond Google Fonts (loaded via CDN).

All CSS is in a `<style>` block in the `<head>`. All JavaScript is in a `<script>` block at the bottom of `<body>`.

### Bilingual System (JA/EN)

Language switching is handled purely with CSS class toggling on `<body>`:

- `body.ja` — shows elements with class `lang-jp`, hides `lang-en`
- `body.en` — shows elements with class `lang-en`, hides `lang-jp`
- `setLang(lang)` in the script block switches the active class and updates the toggle buttons

Every piece of user-facing text must have two versions: one wrapped in `class="lang-jp"` and one in `class="lang-en"`.

### Scroll Animations

Scroll-reveal animations use `IntersectionObserver`. Elements start at `opacity: 0; transform: translateY(2rem)` and gain class `visible` when they enter the viewport, which transitions them to full opacity. Affected element types: `.story-block`, `.pull-quote`, `.fact-item`, `.philosophy h2`, `.philosophy p`.

### Design Tokens (CSS custom properties)

```
--ink:   #1a1208  (dark brown, primary text/backgrounds)
--warm:  #8B5E3C  (medium brown, accents)
--gold:  #C9A84C  (gold, highlights)
--cream: #F7F2EA  (off-white, light backgrounds)
--mist:  #E8E0D0  (light warm grey, secondary backgrounds)
--sage:  #7A8C6E  (defined but unused currently)
```

### Fonts

- `Cormorant Garamond` — headings, quotes, decorative numbers (elegant serif)
- `Noto Serif JP` — Japanese text
- `Lato` — body copy, labels (sans-serif)

## Development

No build or install step. Open `index.html` directly in a browser, or serve with any static file server:

```bash
python3 -m http.server 8000
```

No linting, no tests, no CI configuration.
