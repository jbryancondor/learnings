# Bryan's Learning Lab

A monorepo of independent learning pages — each folder is a standalone deep dive into a concept, tool, or research area, deployed via GitHub Pages.

Live site: **https://jbryancondor.github.io/learnings/**

---

## How this repo works

### Structure

```
learnings/
├── index.html              ← Root redirect → home/
├── home/
│   └── index.html          ← Master index listing all learning pages
├── <topic-name>/           ← One folder per learning topic (kebab-case)
│   ├── index.html          ← The landing page (required)
│   └── *.md                ← Optional research/notes files
├── .github/
│   └── workflows/
│       └── deploy.yml      ← GitHub Actions: auto-deploy on push to main
└── README.md
```

### Conventions

- Every topic lives in its own **kebab-case** folder (e.g., `sdd-research`, `css-grid-deep-dive`)
- **`index.html` is the only required file** per folder — it is the page
- `.md` files are optional companion notes; they are not rendered or deployed separately
- Every `index.html` must include a **back-to-home link** pointing to `../home/`
- The `home/` page lists all topics and links to them

### Adding a new topic

1. Create a new kebab-case folder: `mkdir my-topic`
2. Add `my-topic/index.html` with a back-to-home link (`<a href="../home/">← Home</a>`)
3. Run the **learnings-index-updater** skill to register the new page in `home/index.html`
4. Commit and push to `main` — the site auto-deploys

### Deployment

Every push to `main` triggers GitHub Actions and deploys the full repo to GitHub Pages.
See `SETUP.md` for the one-time GitHub configuration needed.

---

## Pages

| Folder | Title | Description |
|--------|-------|-------------|
| [sdd-research](./sdd-research/) | SDD Tools Benchmark — 2026 | Comparative analysis of Spec-Driven Development tools |
