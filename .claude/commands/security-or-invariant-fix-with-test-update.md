---
name: security-or-invariant-fix-with-test-update
description: Workflow command scaffold for security-or-invariant-fix-with-test-update in memory-lancedb-pro.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /security-or-invariant-fix-with-test-update

Use this workflow when working on **security-or-invariant-fix-with-test-update** in `memory-lancedb-pro`.

## Goal

Fixes a security or data invariance bug, adds or updates regression tests to cover the edge cases, and ensures encoding/formatting consistency in source and test files.

## Common Files

- `index.ts`
- `src/*.ts`
- `test/*.test.mjs`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Implement fix in core logic (e.g., index.ts, src/*.ts)
- Update or add test cases in test/*.test.mjs to cover new edge cases
- Ensure source and test files use consistent encoding/formatting (e.g., UTF-8, LF)
- Document reviewer feedback and address must-fix items

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.