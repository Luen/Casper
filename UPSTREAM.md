# Syncing with TryGhost/Casper

This repo is a fork of [TryGhost/Casper](https://github.com/TryGhost/Casper) customised as **casper-ws** for Wanderstories.

## Remotes

| Remote     | URL                              | Purpose                    |
|------------|----------------------------------|----------------------------|
| `upstream` | `https://github.com/TryGhost/Casper.git` | Official Casper theme |
| `origin`   | Your GitHub fork                 | Push your work here        |

## Pull latest Casper changes

```bash
git fetch upstream
git merge upstream/main
```

Resolve any conflicts, then rebuild and commit:

```bash
pnpm install
pnpm zip
git add -A
git commit -m "Merge upstream Casper and rebuild assets"
```

Push to your fork:

```bash
git push origin main
```

## Files most likely to conflict

When merging upstream, watch these Wanderstories customisations:

- `index.hbs` — homepage banners, map, random articles
- `default.hbs` — member access script, Rocket Loader attributes
- `assets/css/screen.css` — Wanderstories / map / author styles
- `assets/js/infinite-scroll.js` — homepage infinite-scroll skip + semicolon fix
- `package.json` — theme name `casper-ws`, custom settings
- `page-*.hbs` — custom page templates
- `partials/content-cta.hbs` — paywall copy (not in upstream)

## Rebase alternative

If you prefer a linear history:

```bash
git fetch upstream
git rebase upstream/main
pnpm zip
git push origin main --force-with-lease
```

Use `--force-with-lease` only on your fork, never on TryGhost/Casper.
