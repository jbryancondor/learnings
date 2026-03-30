# Learnings Monorepo — Agent Guidelines

This file is the source of truth for any AI agent or LLM working in this repository.
Read this before making any changes.

---

## What this repo is

A monorepo of independent, self-contained static learning pages. Each folder is a standalone deep-dive into a concept, tool, or research area. The repo deploys automatically to GitHub Pages: `https://jbryancondor.github.io/learnings/`.

**Owner:** Bryan Condor (`jbryancondor`)
**Stack:** Pure HTML/CSS/JS — no build step, no bundler, no framework required.

---

## Architecture rules

### One folder = one learning topic

- Folder name must be **kebab-case** (e.g., `css-grid-deep-dive`, `sdd-research`)
- The folder name becomes the URL path: `https://jbryancondor.github.io/learnings/<folder-name>/`
- **Never** put topic content directly in the repo root

### Required files per topic folder

| File | Purpose |
|------|---------|
| `index.html` | The page — standalone, self-contained, no build step |

Everything else is optional: `.md` research notes, `assets/` subfolder, etc.

### Every `index.html` must

1. Be **fully standalone** — inline styles/scripts or CDN only
2. Include a **back-to-home link** pointing to `../home/`:
   ```html
   <a href="../home/">← Home</a>
   ```
3. Have a meaningful `<title>` tag (used by the index updater)
4. Implement **light and dark theme** — see the UI Guidelines section below

### Root structure

```
learnings/
├── index.html              ← Redirect only → home/
├── home/
│   └── index.html          ← Master index listing all pages
├── <topic-name>/
│   ├── index.html          ← Required: the standalone page
│   └── *.md                ← Optional: companion notes (no naming convention)
├── .claude/
│   └── skills/             ← Project skills (Claude Code)
├── .github/
│   └── workflows/
│       └── deploy.yml      ← Auto-deploy on push to main
├── AGENTS.md               ← This file
├── CLAUDE.md               ← Claude Code specific instructions
├── README.md
└── SETUP.md                ← One-time GitHub Pages setup guide
```

### The `home/` folder

`home/index.html` is the master index — a real page listing all topics. It uses marker comments for automated updates:

```html
<!-- PAGES_START -->
  ... card entries here ...
<!-- PAGES_END -->
```

Do not remove or rename these markers.

### How to add a new topic

1. Create a kebab-case folder
2. Create `index.html` inside it — must include `← Home` link and both themes
3. Update `home/index.html` to add a card for the new page (update the section between the `PAGES_START`/`PAGES_END` markers)
4. Update the `README.md` pages table
5. Commit and push to `main`

---

## UI Guidelines

### Every page must support light and dark themes

Both themes are required — no exceptions. Pages that only implement one theme are incomplete.

### Theme priority order

1. User's stored preference (`localStorage` key `theme`)
2. OS-level preference (`prefers-color-scheme` media query)
3. Default fallback: dark

### CSS pattern — use `data-theme` on `<html>`

Define all color tokens as CSS variables in two blocks:

```css
/* Dark theme — default */
:root {
  --bg: #0d1117;
  --bg-card: #161b22;
  --border: #30363d;
  --text: #e6edf3;
  --text-muted: #7d8590;
  --accent: #58a6ff;
  --accent-2: #3fb950;
}

/* Light theme */
[data-theme="light"] {
  --bg: #ffffff;
  --bg-card: #f6f8fa;
  --border: #d0d7de;
  --text: #1f2328;
  --text-muted: #636c76;
  --accent: #0969da;
  --accent-2: #1a7f37;
}
```

Use only `var(--token)` references in the rest of your CSS — never hardcode colors.

### Toggle button

Place a theme toggle button in a visible, consistent location (top-right corner recommended):

```html
<button id="theme-toggle" aria-label="Toggle light/dark theme" title="Toggle theme">
  <span id="theme-icon">🌙</span>
</button>
```

### JavaScript — canonical implementation

```js
(function() {
  const root = document.documentElement;
  const btn = document.getElementById('theme-toggle');
  const icon = document.getElementById('theme-icon');
  const mq = window.matchMedia('(prefers-color-scheme: dark)');

  function applyTheme(theme) {
    root.setAttribute('data-theme', theme);
    icon.textContent = theme === 'dark' ? '🌙' : '☀️';
    localStorage.setItem('theme', theme);
  }

  // Init: stored > OS > dark
  const stored = localStorage.getItem('theme');
  applyTheme(stored || (mq.matches ? 'dark' : 'light'));

  // Respond to OS preference changes (only if no stored preference)
  mq.addEventListener('change', e => {
    if (!localStorage.getItem('theme')) applyTheme(e.matches ? 'dark' : 'light');
  });

  // Toggle on click
  btn.addEventListener('click', () => {
    applyTheme(root.getAttribute('data-theme') === 'dark' ? 'light' : 'dark');
  });
})();
```

---

## Deployment rules

- Only the **`main` branch** deploys to GitHub Pages
- Every push to `main` triggers a **full repo deploy** (all folders)
- Other branches never deploy — use them freely for development
- See `SETUP.md` for one-time GitHub Pages setup

---

## Security

All pages are **publicly accessible**. Never commit anything sensitive.

- No API keys, tokens, passwords, or credentials anywhere in the code or comments
- No internal URLs, staging endpoints, or private identifiers
- All CDN scripts/stylesheets must use **Subresource Integrity (SRI)** — prefer inline code over CDN when possible
- No `eval()` or `innerHTML` with uncontrolled input

Automated secret scanning runs on every push and pull request via `.github/workflows/security.yml` (gitleaks). See the **learnings-security** skill for the full checklist and SRI guidance.

---

## What NOT to do

- Do not add build steps, package.json, or bundlers
- Do not hardcode colors — use CSS variables
- Do not create a topic folder without `index.html`
- Do not edit the root `index.html` content (it is a redirect only)
- Do not remove the `<!-- PAGES_START -->` / `<!-- PAGES_END -->` markers in `home/index.html`
- Do not commit secrets, credentials, or internal URLs — gitleaks will catch it but prevention is better
