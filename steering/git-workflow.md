# Git and branching

GitHub is the single source of truth for code. Laptop clones and production checkouts
are working copies of it. Containers mount the laptop clone; they do not hold their own
copy.

## Branches

    main      = what production runs. Protected. Changes only through a PR.
    develop   = integration / staging. Protected. Changes only through a PR.
    feature/<ticket>-<short-name>   = one branch per task, cut from develop.
    hotfix/<ticket>-<short-name>    = cut from main, PR to main, then merge back to develop.

Flow: `feature/*` -> PR -> `develop` -> validate on staging -> PR -> `main` -> deploy.

## Rules

- Never push directly to `main` or `develop`. Never force-push either.
- Never delete `main` or `develop`. Never rewrite published history.
- Create commits only when asked. Prefer specific `git add <file>` over `git add .`.
- Commit messages: imperative, reference the ticket key (for example `PROJ-123: Fix invoice rounding`).
- One concern per PR. The PR description states: what changed, why, how it was tested.
- Do not merge `develop` into `main` yourself. That PR is the human approval gate.
- Before deleting any branch, show that it has no commits missing from `main`.
- Run git on the host, not inside containers.

## Protection

- `main` and `develop` require a pull request. No approvals are required for a solo
  maintainer, because authors cannot approve their own PRs. The gate is that the PR
  exists, conversations are resolved and (once CI exists) checks pass.
- Block force pushes and deletions on both branches.
- Do not allow admins to bypass `main` protection.
- Private repositories need a paid GitHub plan for branch protection to be enforced.
