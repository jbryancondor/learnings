---
name: learnings-index-updater
description: Updates the home/index.html master index page of the learnings monorepo (jbryancondor/learnings) to reflect all current learning folders. Use this skill when: "update the home page", "register my new page", "I added a new folder and want it listed", "sync the index", "add my new topic to the home page", "the home page is missing a page", "refresh the index", or any time home/index.html needs to reflect the current state of the repo.
---

# Learnings Index Updater

## What this skill does

Scans all folders in the repo for `index.html`, then updates `home/index.html` so every learning topic is listed with a card linking to it.

---

## Step-by-step process

### 1. Discover all learning folders

Scan the repo root for **subdirectories that contain an `index.html`**, excluding:
- `home/` itself
- Any hidden folder (starting with `.`)
- Any folder without an `index.html`

For each discovered folder, read its `index.html` and extract:
- **Title** — from the `<title>` tag (strip any trailing ` — ` suffixes if you want a short title, but keeping the full title is fine)
- **Description** — look for a `<meta name="description" content="...">` tag; if absent, leave the description empty or write a short generic one based on the folder name

### 2. Build the cards HTML

For each discovered folder, generate a card entry:

```html
<a class="card" href="../<folder-name>/">
  <div class="card-title"><TITLE></div>
  <div class="card-desc"><DESCRIPTION></div>
  <div class="card-meta">
    <span class="tag"><INFERRED_TAG></span>
  </div>
</a>
```

For tags, infer 1–2 short tags from the folder name or title (e.g., `sdd-research` → `research`). Keep tags lowercase.

### 3. Replace the cards section in home/index.html

Find the marker comments and replace everything between them:

```html
<!-- PAGES_START -->
  <GENERATED CARDS HERE>
<!-- PAGES_END -->
```

Use the Edit tool to do a targeted replacement — do not rewrite the entire file.

### 4. Update README.md table

The `README.md` contains a Pages table:

```markdown
| Folder | Title | Description |
```

Update this table to match the current set of pages. Find the table by its header row and replace the full table.

---

## Important rules

- **Never remove a folder's card** unless the folder itself no longer exists — do not delete entries just because a folder is missing `index.html` or looks incomplete. If unsure, ask the user.
- **Preserve card order** — add new pages at the end of the list by default. If the user wants a different order, ask them.
- **Do not touch anything else** in `home/index.html` — only the content between `<!-- PAGES_START -->` and `<!-- PAGES_END -->`.
- If a folder's `index.html` has no `<title>` tag, use the folder name formatted as Title Case as a fallback (e.g., `css-grid` → `Css Grid`).

---

## Verification

After updating, confirm:
1. `home/index.html` has one card per learning folder
2. Each card's `href` points to the correct relative path (`../folder-name/`)
3. The `README.md` table is in sync
4. Tell the user which folders were added, which were already there, and if any were missing `index.html`
