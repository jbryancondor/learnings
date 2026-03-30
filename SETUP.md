# GitHub Pages Setup Guide

One-time steps to enable automatic deployment for this repo.

---

## 1. Push the workflow to GitHub

Make sure the `.github/workflows/deploy.yml` file is committed and pushed to `main`:

```bash
git add .github/workflows/deploy.yml
git commit -m "ci: add GitHub Pages deployment workflow"
git push origin main
```

---

## 2. Enable GitHub Pages in the repo settings

1. Go to your repo on GitHub: https://github.com/jbryancondor/learnings
2. Click **Settings** (top navigation bar)
3. In the left sidebar, click **Pages** (under "Code and automation")
4. Under **Source**, select **GitHub Actions**
5. Click **Save**

> If you see "Deploy from a branch" selected instead, change it to "GitHub Actions".

---

## 3. Trigger the first deploy

The workflow triggers automatically on every push to `main`. After completing step 2, push any small change (e.g., update README) to kick off the first deployment:

```bash
git add README.md
git commit -m "chore: trigger initial pages deploy"
git push origin main
```

---

## 4. Verify the deployment

1. Go to the **Actions** tab on GitHub: https://github.com/jbryancondor/learnings/actions
2. You should see a workflow run called "Deploy to GitHub Pages" in progress or completed
3. Once it passes (green checkmark), your site is live at:

   **https://jbryancondor.github.io/learnings/**

---

## Ongoing workflow

After setup, you never need to do this again. Just:

```bash
git add .
git commit -m "your message"
git push origin main
```

GitHub Actions picks it up and deploys automatically. Deployment usually takes 1–2 minutes.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Workflow fails with "Pages not found" | Make sure you set Source → GitHub Actions in step 2 |
| 404 on the site URL | Wait 2–3 minutes after first deploy; GitHub sometimes has propagation delay |
| Workflow not triggering | Check that you pushed to `main` (not another branch) |
| Site shows old content | Hard refresh the browser (Cmd+Shift+R / Ctrl+Shift+R) |
