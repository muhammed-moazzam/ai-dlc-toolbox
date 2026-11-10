# Testing and TDD

## Loop

1. Red: write a failing test that expresses the approved acceptance criterion. Run it
   and show the failure. A test that never failed proves nothing.
2. Green: write the smallest change that makes it pass. Run it and show it passing.
3. Refactor: clean up with the tests still green.

## Rules

- Tests trace back to acceptance criteria on the work item. Name the criterion a test covers.
- One behavior per test. Tests are independent and can run in any order.
- Fix the code, not the test, unless the test itself is wrong. Say so when changing a test.
- Run the relevant tests after every change and report the result. If tests cannot run,
  say so and say why.
- Never run tests against environments holding real data or copies of production data.
  Tests create and delete records. Use a throwaway test environment.
- Debug failures from evidence (logs, tracebacks, reading the framework source), not guesses.
- Framework, runner and base-class details belong in the project steering file.
