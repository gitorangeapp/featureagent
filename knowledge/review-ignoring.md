# What the auto-merge review ignores

Conventions for `.orangeignore` and lockfile handling in `worker/src/review/`:

- A lockfile is never sent to a model, whatever `.orangeignore` says. Lockfile ignoring is a hard guarantee on
  purpose: a `!`-negation rule in `.orangeignore` re-including a lockfile is not a bug and not a docs/code
  contradiction. Do not flag it.
- `.orangeignore` (read from the target branch) replaced the old hardcoded GENERATED ignore list. It is a
  deliberate, documented design that repositories choose per path what to ignore: a path (for example `*.snap`)
  that the old hardcoded list ignored but the new list omits is a configuration choice, not a removed feature.
  Only flag a gap if the pull request's own description or docs promise the path is ignored and the list doesn't
  match it.
