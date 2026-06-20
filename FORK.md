# FORK.md — golem15com/wn-location-plugin

This repository is a golem15 fork of WinterCMS Location plugin. It keeps the
upstream composer package name `winter/wn-location-plugin` so downstream
consumers need no rename — the git *source* is overridden by re-pointing the
superproject submodule at this fork; the only divergence is a widened
`winter/wn-backend-module` constraint so the plugin resolves against the
Laravel 12 / Winter 1.3 core forks.

- **Upstream:** wintercms/wn-location-plugin (tag `v2.2.0`)
- **Base SHA:** `46398fa7d4321342d59bee624cdddb1285b6fca7`
- **Base tag:** `golem15-base` (immutable re-convergence anchor at the fork point)
- **Working branch:** `laravel12`
- **upstream remote:** `git@github.com:wintercms/wn-location-plugin.git`

## Delta commits (cherry-pickable, beyond upstream `v2.2.0`)

- `chore(fork): widen wn-backend-module ^1.2.8 for L12/1.3 resolve + FORK.md`
  — widens `winter/wn-backend-module` from `~1.2.8|dev-develop` to
  `^1.2.8|dev-develop` so `1.3.x-dev` (the golem15com backend-module fork's
  Laravel 12 line) satisfies the constraint. No behavioral source change.

## Re-convergence

```bash
git fetch upstream
git merge upstream/main               # branch laravel12 ≠ main → unambiguous
# or rebase the minimal golem15 delta onto a finalized upstream:
git rebase --onto upstream/main golem15-base laravel12
```

If upstream ships a Laravel 12 / Winter 1.3 compatible release, the cleanest
re-converge is to re-point the superproject submodule back at
`wintercms/wn-location-plugin` — the widened constraint is the only divergence.
