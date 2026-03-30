---
name: learnings-architecture
description: Architecture and conventions guide for the learnings monorepo (jbryancondor/learnings). Use this skill whenever you are working in this repository — creating a new learning folder, adding an index.html, naming a topic, asking how to structure something, or checking what files are required. Also trigger on: "add a new page", "new topic", "create a learning page", "how should I name this folder", "what do I need in this folder", "create a new deep dive", "add a section", "start a new research page".
---

# Learnings Monorepo — Architecture Guide

## What this repo is

A monorepo of independent, self-contained learning pages. Each folder is a standalone web page (a deep dive into a concept, tool, or research area). The repo deploys to GitHub Pages: `https://jbryancondor.github.io/learnings/`.

---

## Folder and file rules

### One folder = one learning topic

- Folder name must be **kebab-case** (e.g., `css-grid-deep-dive`, `sdd-research`, `react-server-components`)
- The folder name becomes the URL: `https://jbryancondor.github.io/learnings/<folder-name>/`

### Required files

| File | Purpose | Required? |
|------|---------|-----------|
| `index.html` | The landing page — this IS the page that gets deployed | **Yes, always** |

### Optional files

Anything else is allowed but optional. Common patterns:

- `*.md` files — freeform research notes, no naming convention required
- `assets/` subfolder — images, icons, local CSS/JS files
- Any other supporting files

The `.md` files are personal notes; they are not rendered or linked from `index.html` unless you explicitly choose to do so.

---

## `index.html` requirements

Every `index.html` must:

1. Be **fully standalone** — all styles and scripts inline or from CDN. No build step, no bundler.
2. Include a **back-to-home link** pointing to `../home/`. Example:
   ```html
   <a href="../home/">← Home</a>
   ```
   Style it however you want, but it must be there so users can navigate back.
3. Have a meaningful `<title>` tag — the index updater skill reads this to generate the home page listing.
4. Implement **both light and dark themes** — use the **learnings-ui-guidelines** skill for the exact CSS variables, toggle button, and JavaScript pattern.

---

## Root structure

```
learnings/
├── index.html          ← Redirect only: <meta refresh> → home/
├── home/
│   └── index.html      ← Master index listing all learning pages (maintained by learnings-index-updater skill)
├── <topic-name>/
│   ├── index.html      ← Required: the standalone landing page
│   └── *.md            ← Optional: companion notes
├── .github/
│   └── workflows/
│       └── deploy.yml  ← CI/CD: auto-deploy to GitHub Pages on push to main
├── README.md
└── SETUP.md
```

### The `home/` folder

`home/index.html` is the master index — it lists all learning topics with links. It is a real page in the same pattern as other learning pages, not just a utility file. It lives at `https://jbryancondor.github.io/learnings/home/`.

The repo root `index.html` only redirects to `home/` — do not add content there.

### The `home/index.html` marker comments

The home page uses HTML comment markers so the index updater skill can find and replace the cards section:

```html
<!-- PAGES_START -->
  ... card entries ...
<!-- PAGES_END -->
```

Do not remove or rename these comments.

---

## How to add a new learning topic

1. Create a new kebab-case folder: `mkdir my-topic`
2. Create `my-topic/index.html` — standalone, with `← Home` link and both light/dark themes
3. Use the **learnings-ui-guidelines** skill for the theme implementation
4. Run the **learnings-index-updater** skill to register it in `home/index.html`
5. Commit and push to `main`

---

## Deployment

- Only `main` branch deploys
- Every push to `main` triggers a full deploy via GitHub Actions
- See `SETUP.md` for one-time GitHub Pages configuration
- Use the **learnings-deploy** skill if you need to regenerate or inspect the workflow file
