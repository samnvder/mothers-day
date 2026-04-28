# Mother’s Day RSVP landing (standalone Firebase site)

This folder is meant to be the **root of its own Git repository** (or copy these files into a new repo root). It does **not** depend on the South End monorepo, Pickleball, or the parent `Website/` tree.

## What you need

| File | Purpose |
|------|---------|
| `index.html` | Public site (Hosting serves this) |
| `firebase.json` | `public: "."` — ignores draft/embed/docs so only `index.html` is published |
| `.firebaserc` | Firebase **project id** |
| `package.json` | `npm run deploy` / `npm run deploy:preview` |
| `Mothers Day HTML.html` | Optional Thrive/WP embed (not uploaded to Hosting) |
| `south_end_mothers_day_rsvp_cursor_brief.md` | Build spec (not uploaded) |
| `README.md` | This file (not uploaded) |

You **do not** need: parent `package.json`, pickleball `firebase.json`, or a monorepo path like `Website/mothers-day/`.

## One-time Firebase setup

1. Create a project (e.g. id in `.firebaserc` or change it).
2. Enable **Hosting**.
3. `npx firebase-tools login`

## Deploy

```bash
npm run deploy
```

Preview channel (7 days):

```bash
npm run deploy:preview
```

## CI (optional, new repo)

Add `.github/workflows/deploy.yml`:

```yaml
name: Deploy Hosting
on:
  push:
    branches: [main, master]
  workflow_dispatch:
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm install -g firebase-tools
      - run: firebase deploy --non-interactive
        env:
          FIREBASE_TOKEN: ${{ secrets.FIREBASE_TOKEN }}
```

(Set `FIREBASE_TOKEN` in repo secrets; run from repo root where `firebase.json` lives.)
