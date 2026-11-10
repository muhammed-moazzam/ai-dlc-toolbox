# <Project name> project rules

Copy to `.kiro/steering/<project>-rules.md` in the project workspace. Keep it to facts
that only apply to this project. Generic lifecycle, safety, git and TDD rules come from
the toolbox. Do not repeat them here and do not put feature requirements here.

## Stack

<Frameworks, versions, language runtime, anything that affects how code behaves.>

## Hard rules

- <What must never be modified (vendored or upstream code).>
- <Native features to prefer before custom code.>
- <Where custom code must live, and the extension points to use.>

## Where things live

| What | Path |
|---|---|
| <App or service> | `<path>` |
| <Read-only reference source> | `<path>` |
| <Environment files> | `<path>` |

## Local environment

<How to start and stop it. How to run the framework CLI. Which data is real.>

## Testing

<Runner, base classes, where tests live, how to create the throwaway test environment.>

## Project safety

<Which folders hold keys or real data. What is production here and how it may be inspected.>

## Known open items

<Things that are not done yet and affect safety or correctness. Update when resolved.>
