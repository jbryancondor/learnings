---
name: learnings-security
description: Security review skill for the learnings monorepo. All pages are public — nothing sensitive should ever be exposed. Use this skill when: building a new page, reviewing existing pages before committing, adding external scripts or stylesheets, "security review", "is this safe to publish", "check for secrets", "add a CDN script", "SRI hash", "what should I not expose", or any time security concerns come up in this repo.
---

# Learnings Security Guidelines

All pages in this repo are **public** at `https://jbryancondor.github.io/learnings/`. Treat every file as fully visible to anyone on the internet.

---

## Automated scanning

A GitHub Actions workflow (`.github/workflows/security.yml`) runs **gitleaks** on every push to `main` and on every pull request. It scans the full git history for accidentally committed secrets.

If the workflow fails, do not merge or push until the secret is removed from history (not just deleted from the file — git history must be cleaned with `git filter-repo` or similar).

---

## Security checklist — run before every commit

### Secrets and credentials

- [ ] No API keys, tokens, or passwords anywhere in the code
- [ ] No `.env` values copy-pasted into HTML/JS
- [ ] No internal URLs (staging, admin, internal tools)
- [ ] No personal email addresses, phone numbers, or private identifiers
- [ ] No auth headers, bearer tokens, or session IDs in fetch() calls or comments
- [ ] No database connection strings or service account credentials

### JavaScript

- [ ] No `eval()` or `new Function()` with user-controlled input
- [ ] No `innerHTML` assignments using data that could come from external sources
- [ ] `fetch()` calls only hit public, intentional endpoints
- [ ] No `postMessage` listeners without origin validation (if used)

### External resources (CDN scripts and stylesheets)

If a page loads any script or stylesheet from a CDN, it **must** use Subresource Integrity (SRI):

```html
<!-- Without SRI — NOT allowed -->
<script src="https://cdn.example.com/lib.min.js"></script>

<!-- With SRI — required -->
<script
  src="https://cdn.example.com/lib.min.js"
  integrity="sha384-<hash>"
  crossorigin="anonymous">
</script>
```

Generate SRI hashes at https://www.srihash.org or with:
```bash
curl -s https://cdn.example.com/lib.min.js | openssl dgst -sha384 -binary | openssl base64 -A
```

Then prefix the output with `sha384-`.

Currently no pages use CDN resources — all styles and scripts are inline, which is the safest approach. Keep this as the default and only use CDN when there is a clear reason.

### HTML meta / information exposure

- [ ] No `<meta>` tags exposing internal tooling, CMS, or generator info beyond what's intentional
- [ ] No HTML comments left in production that reference internal systems, staging URLs, or credentials
- [ ] `<title>` and `<meta name="description">` contain only public-facing content

---

## What is safe to include

These are fine for public pages:

- GitHub username and repo links
- Public CDN resources (with SRI)
- Inline CSS and JS with no sensitive logic
- Public API calls to services that require no auth
- Analytics snippets (if desired in the future) from reputable providers

---

## If gitleaks flags a false positive

Add a `.gitleaks.toml` at the repo root to allowlist it:

```toml
[allowlist]
  description = "Allowlisted patterns"
  regexes = [
    '''<the-false-positive-pattern>''',
  ]
```

Only do this if you are certain the flagged string is not a real secret.
