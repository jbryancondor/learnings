---
name: learnings-ui-guidelines
description: UI implementation guide for pages in the learnings monorepo. Provides the canonical light/dark theme pattern with OS auto-detection, localStorage persistence, and a toggle button. Use this skill whenever building or editing any index.html in this repo — adding a theme toggle, implementing dark mode, fixing theme switching, asking what colors to use, or starting a new page from scratch. Also trigger on: "add dark mode", "theme toggle", "light and dark", "what CSS variables should I use", "the theme isn't switching", "auto-detect theme".
---

# Learnings UI Guidelines

## The one hard rule

Every `index.html` in this repo must support both **light and dark themes**. A page with only one theme is incomplete. This is not optional.

---

## Color tokens

Define all colors as CSS variables. Copy this block into every new page:

```css
/* ── Dark theme (default) ── */
:root {
  --bg: #0d1117;
  --bg-card: #161b22;
  --bg-code: #0d1117;
  --border: #30363d;
  --text: #e6edf3;
  --text-muted: #7d8590;
  --text-dim: #484f58;
  --accent: #58a6ff;
  --accent-2: #3fb950;
  --accent-3: #d2a8ff;
  --accent-warn: #d29922;
  --accent-danger: #f85149;
  --tag-bg: #1f2937;
  --shadow: 0 2px 8px rgba(0,0,0,0.4);
}

/* ── Light theme ── */
[data-theme="light"] {
  --bg: #ffffff;
  --bg-card: #f6f8fa;
  --bg-code: #f0f2f4;
  --border: #d0d7de;
  --text: #1f2328;
  --text-muted: #636c76;
  --text-dim: #8c959f;
  --accent: #0969da;
  --accent-2: #1a7f37;
  --accent-3: #8250df;
  --accent-warn: #9a6700;
  --accent-danger: #cf222e;
  --tag-bg: #eaeef2;
  --shadow: 0 2px 8px rgba(0,0,0,0.1);
}
```

Never hardcode a color value outside these two blocks. Always use `var(--token)`.

---

## Theme toggle button

Place this in a fixed position, top-right corner:

```html
<button id="theme-toggle" aria-label="Toggle light/dark theme" title="Toggle theme">
  <span id="theme-icon">🌙</span>
</button>
```

Suggested button CSS (add to your stylesheet):

```css
#theme-toggle {
  position: fixed;
  top: 16px;
  right: 16px;
  z-index: 200;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 6px 10px;
  cursor: pointer;
  font-size: 16px;
  color: var(--text);
  transition: background 0.15s, border-color 0.15s;
}
#theme-toggle:hover {
  border-color: var(--accent);
}
```

---

## Theme JavaScript

Drop this script at the end of `<body>`, after all other scripts:

```html
<script>
(function() {
  const root = document.documentElement;
  const btn  = document.getElementById('theme-toggle');
  const icon = document.getElementById('theme-icon');
  const mq   = window.matchMedia('(prefers-color-scheme: dark)');

  function applyTheme(theme) {
    root.setAttribute('data-theme', theme);
    icon.textContent = theme === 'dark' ? '🌙' : '☀️';
    localStorage.setItem('theme', theme);
  }

  // Priority: stored preference > OS preference > dark fallback
  const stored = localStorage.getItem('theme');
  applyTheme(stored || (mq.matches ? 'dark' : 'light'));

  // Follow OS changes only when the user hasn't made an explicit choice
  mq.addEventListener('change', e => {
    if (!localStorage.getItem('theme')) applyTheme(e.matches ? 'dark' : 'light');
  });

  btn.addEventListener('click', () => {
    applyTheme(root.getAttribute('data-theme') === 'dark' ? 'light' : 'dark');
  });
})();
</script>
```

---

## How theming works

- `data-theme` attribute on `<html>` controls which CSS variable block is active
- On first load: check `localStorage` → if empty, check `prefers-color-scheme` → default to dark
- On OS theme change: only auto-switch if the user has never clicked the toggle
- On toggle click: flip theme and persist to `localStorage` so the choice survives page reloads and navigation

---

## Checklist for a new page

- [ ] CSS variables block includes both `:root` (dark) and `[data-theme="light"]`
- [ ] All color values use `var(--token)` — no hardcoded hex
- [ ] `#theme-toggle` button exists in the HTML
- [ ] Theme JS script is included at end of `<body>`
- [ ] Test: toggle works, page survives refresh in both themes, OS preference respected on first load

---

## Existing page: `sdd-research/index.html`

This page was created before the theme convention was established. It only has a dark theme. When updating it, add the `[data-theme="light"]` block and the toggle button/script following the patterns above.
