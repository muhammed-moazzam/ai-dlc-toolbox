# AI-assisted development lifecycle (AI-DLC)

AI agents are used where they add the most value. Humans keep control at the points
that carry business or production risk. Deterministic tooling does anything repeatable.
The agent does not run the lifecycle on its own authority.

## Lifecycle

    Business requirement / user story
    -> Requirements analysis
    -> Technical design / architecture
    -> HUMAN APPROVAL
    -> Development
    -> Automated testing / TDD
    -> AI-assisted code review
    -> Pull request
    -> CI/CD validation
    -> Staging deployment
    -> HUMAN APPROVAL
    -> Production deployment
    -> Monitoring / feedback
    -> New requirements

## Who does what

| Owner | Responsibilities |
|---|---|
| AI agent | Analyze requirements and flag ambiguities. Produce designs and implementation plans. Break features into tasks. Implement approved tasks. Write and update tests (TDD). Debug failures. Review code against requirements and standards. Generate documentation. Analyze logs and incidents. Suggest improvements. |
| Human | Business priorities and acceptance criteria. Approval of requirements before development. Approval of significant architecture decisions. Review of high-risk or security-sensitive changes. Production deployment approval. Destructive database or infrastructure operations. Final judgment when AI output is uncertain. |
| Deterministic tooling | Source control and PRs (Git/GitHub). Test runs and validation (CI). Deployments (scripts or infrastructure tooling). Backups and restores. Anything that must behave identically every time. |

If a step is repeatable, it belongs in a script or pipeline, not in an agent's judgment.
Agents never improvise production commands.

## Environments

More freedom locally, less in staging, least in production.

| Environment | Agent autonomy |
|---|---|
| Local / throwaway | Broad. Read, edit, run, test, debug. |
| Staging | Moderate. Deploys through the pipeline, human-approved. |
| Production | Minimal. Read-only inspection through an approved mechanism. Changes only via the scripted, human-approved deploy. |

## Requirements vs steering

- Permanent steering holds reusable knowledge: standards, architecture constraints,
  safety rules, how this lifecycle works.
- Feature requirements come from tracked work items (tickets, user stories), never from
  steering. Do not paste a feature's requirements into a steering file.
- Each project adds one project-specific steering file (stack, paths, commands, rules
  that only apply there). Use `templates/project-steering.md`.

## Working rules for the agent

- Do not start development until requirements are approved and the design is approved.
- State assumptions and open questions instead of guessing. Ambiguity goes back to the
  human before code is written.
- Prefer the platform's native features before custom code. Say what was considered.
- Work test-first. See `testing-tdd.md`.
- Report what was verified and what was not. Do not claim a result that was not checked.
- One concern per branch and per pull request.

## Maturity

Each stage is proven manually, with a human driving, before it is delegated to a
specialized agent (planning, development, testing/review, operations). Do not add an
agent for a stage that has not been run by hand successfully.
