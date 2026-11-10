# AI-DLC Toolbox

A reusable, AI-assisted software development lifecycle. AI agents do the work they are
good at (analysis, design, implementation, tests, review, documentation). Humans keep
control of business priorities and production risk. Deterministic tooling (Git, CI/CD,
deploy scripts) handles anything repeatable.

It is built for the Kiro IDE: the rules are steering files that load into every session.

**Status:** work in progress. The lifecycle is defined here. Stages are being proven
manually on a real ERPNext/Frappe project before any stage is delegated to a specialized
agent. Nothing below claims a stage is proven until it has been run end to end.

## Lifecycle

    Requirement -> Requirements analysis -> Design -> HUMAN APPROVAL
    -> Development -> Automated testing (TDD) -> AI-assisted review -> Pull request
    -> CI/CD validation -> Staging -> HUMAN APPROVAL -> Production
    -> Monitoring / feedback -> New requirements

Details, ownership of each step, and the environment autonomy model are in
`steering/ai-dlc-lifecycle.md`.

## Contents

| Path | Purpose |
|---|---|
| `steering/ai-dlc-lifecycle.md` | The lifecycle, who owns each step, environment autonomy, maturity rule |
| `steering/safety-boundaries.md` | Production access, actions that need approval, secrets handling |
| `steering/git-workflow.md` | Branch model, PR gates, branch protection |
| `steering/testing-tdd.md` | Red, green, refactor, and testing safety rules |
| `templates/project-steering.md` | Starting point for the one project-specific steering file |

## Using it in a project

1. Make the four `steering/` files available to the project's Kiro workspace. Either
   link or copy them into the workspace's `.kiro/steering/`, or into `~/.kiro/steering/`
   to apply to every workspace.
2. Copy `templates/project-steering.md` into the project and fill it in.
3. Put feature requirements in your work tracker, not in steering.

## Design principles

- Generic rules live here. Project facts live in one project file.
- Deterministic tools over agent improvisation for anything repeatable.
- More agent freedom locally, least in production.
- Prove each stage by hand before automating it with an agent.
