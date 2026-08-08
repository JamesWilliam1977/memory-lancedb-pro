---
name: bugfix-with-tdd-and-ci-manifest-update
description: Workflow command scaffold for bugfix-with-tdd-and-ci-manifest-update in memory-lancedb-pro.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /bugfix-with-tdd-and-ci-manifest-update

Use this workflow when working on **bugfix-with-tdd-and-ci-manifest-update** in `memory-lancedb-pro`.

## Goal

Implements a bugfix using test-driven development (TDD), adds/updates regression tests, and ensures new tests are included in the CI manifest for continuous integration.

## Common Files

- `index.ts`
- `src/*.ts`
- `test/*.test.mjs`
- `scripts/ci-test-manifest.mjs`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Write failing test(s) for the bug (TDD) in test/*.test.mjs
- Implement the bugfix in relevant source files (e.g., index.ts, src/*.ts)
- Update or add type/interface definitions if needed (e.g., src/*.ts)
- Update scripts/ci-test-manifest.mjs to include new/updated tests
- Verify all tests pass and CI covers the new cases

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.