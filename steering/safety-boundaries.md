# Safety boundaries

Principle: more freedom in local, less in staging, least in production. Humans own business
priorities, acceptance criteria and production approval. Deterministic tooling does
repeatable operations. The agent does not improvise production commands.

## Production is off limits unless explicitly approved per action

- No SSH to production, no framework CLI commands against production, no database access.
- Read-only inspection is allowed ONLY through an approved, least-privilege mechanism
  (for example a read-only role with a fixed set of allowed commands). If none exists,
  ask the user to run the command and paste the output.
- Never run deployments, migrations, restarts, restores, or backups on production.
  Deploys happen through a scripted, human-approved process.

## Always ask before

- Deleting or overwriting data, volumes, branches, or more than one file.
- Removing volumes, pruning container systems, dropping a database.
- Force pushes, history rewrites, changing branch protection, changing the default branch.
- Anything that sends data off this machine, or could message real customers or staff.
- Changing auth, permissions, roles, or security settings.

## Secrets and sensitive data

- Do not open, read, copy or print key material. Reference it by path only.
- Files holding passwords, tokens or encryption keys: refer to values by key name; never
  echo them into chat, commits, or docs.
- Real business data (backups, exports, restored databases) is never committed, never
  uploaded, and never pasted into tickets, PRs or chat unless the user asks.
- Do not put secrets or production hostnames/IPs into steering, specs or docs.
- Scrub temporary files that held secrets once the task is done.

## Local environment

- Before any command that mutates a local database (restore, migrate, bulk update),
  say what it will do. Prefer a snapshot or a fresh test environment when practical.
- Bind local services to loopback only.
- Keep schedulers and background workers that can contact the outside world paused until
  integrations are neutralized and the user approves.
