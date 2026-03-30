---
name: learnings-deploy
description: Generates and maintains the GitHub Actions workflow that auto-deploys the learnings monorepo (jbryancondor/learnings) to GitHub Pages on every push to main. Use this skill when: "set up deployment", "create the github actions workflow", "deploy to github pages", "why isn't my page live", "regenerate the workflow", "the deploy is broken", "update the CI", "how do I publish my site", or any time the .github/workflows/deploy.yml file needs to be created or fixed.
---

# Learnings Deploy — GitHub Actions + GitHub Pages

## Overview

The deployment is fully automatic: push to `main` → GitHub Actions runs → site is live at `https://jbryancondor.github.io/learnings/`.

The workflow file lives at `.github/workflows/deploy.yml`.

---

## Workflow file

The canonical content of `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v5

      # Full repo deploy — deploys every folder on every push to main.
      # TODO (implement later): switch to path-filtered deploys so only
      # changed folders trigger a new deployment, reducing noise and build time.
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: "."

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

---

## What each part does

| Part | Purpose |
|------|---------|
| `on: push: branches: [main]` | Only deploys from `main` — other branches never deploy |
| `workflow_dispatch` | Lets you trigger a deploy manually from the GitHub Actions UI |
| `permissions` | Required by GitHub's OIDC-based Pages deployment (no tokens needed) |
| `concurrency` | Prevents two deploys running at once; queued runs wait, not cancel |
| `configure-pages` | Sets correct base URL and metadata for GitHub Pages |
| `upload-pages-artifact path: "."` | Uploads the entire repo as the deploy artifact |
| `deploy-pages` | Publishes to GitHub Pages and outputs the live URL |

---

## First-time setup

The workflow file alone is not enough — GitHub Pages must be enabled in the repo settings. See `SETUP.md` for the one-time steps (takes ~2 minutes).

---

## Troubleshooting

**Workflow not triggering:**
- Confirm you pushed to `main`, not another branch
- Check `.github/workflows/deploy.yml` is committed (not just created locally)

**Permissions error in the workflow run:**
- Go to repo Settings → Actions → General → Workflow permissions
- Set to "Read and write permissions"

**404 on the live URL after deploy:**
- Go to Settings → Pages and confirm Source is set to "GitHub Actions"
- Wait 2–3 minutes for DNS propagation on first deploy

**Site shows stale content:**
- Hard refresh: Cmd+Shift+R (Mac) / Ctrl+Shift+R (Windows/Linux)
- Check the Actions tab to confirm the latest run succeeded

---

## Future improvement (TODO)

The current workflow deploys the full repo on every push. For larger repos, consider path-filtered deploys:

```yaml
on:
  push:
    branches: [main]
    paths:
      - 'home/**'
      - 'sdd-research/**'
      # add each topic folder here
```

This reduces unnecessary deploys when only unrelated files change (e.g., README.md edits).
