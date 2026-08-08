```markdown
# memory-lancedb-pro Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches the core development practices and workflows used in the `memory-lancedb-pro` TypeScript codebase. You'll learn the project's coding conventions, how to structure bugfixes and security patches using test-driven development (TDD), and how to ensure your changes are properly tested and integrated with CI.

## Coding Conventions

- **Language:** TypeScript
- **Framework:** None detected
- **File Naming:** Use kebab-case for all files.
  - Example: `memory-store.ts`, `vector-utils.ts`
- **Import Style:** Use relative imports.
  - Example:
    ```typescript
    import { VectorStore } from './vector-store';
    ```
- **Export Style:** Use named exports.
  - Example:
    ```typescript
    export function connectDB() { /* ... */ }
    export type MemoryRecord = { /* ... */ };
    ```
- **Commit Messages:** Follow conventional commit style, using prefixes like `fix`.
  - Example: `fix: handle null vectors in similarity search`

## Workflows

### Bugfix with TDD and CI Manifest Update
**Trigger:** When you need to fix a bug and ensure it is covered by automated tests and CI.  
**Command:** `/bugfix-tdd-ci`

1. **Write a Failing Test:**  
   Create or update a test in `test/*.test.mjs` that reproduces the bug.
   ```typescript
   // test/vector-utils.test.mjs
   import { faultyFunction } from '../src/vector-utils';

   test('handles null input gracefully', () => {
     expect(() => faultyFunction(null)).toThrow();
   });
   ```
2. **Implement the Bugfix:**  
   Fix the bug in the relevant source file (e.g., `src/vector-utils.ts`).
   ```typescript
   export function faultyFunction(input: number[] | null) {
     if (!input) throw new Error('Input cannot be null');
     // ...rest of logic
   }
   ```
3. **Update Types/Interfaces (if needed):**  
   Adjust type definitions in `src/*.ts` as required.
4. **Update CI Test Manifest:**  
   Add or update the test entry in `scripts/ci-test-manifest.mjs` to ensure CI runs the new/updated test.
   ```javascript
   // scripts/ci-test-manifest.mjs
   export default [
     'test/vector-utils.test.mjs',
     // ...other tests
   ];
   ```
5. **Verify All Tests Pass:**  
   Run the test suite and ensure CI covers the new cases.

### Security or Invariant Fix with Test Update
**Trigger:** When you discover a security or data integrity issue that requires both code and test updates.  
**Command:** `/security-fix-test`

1. **Implement the Fix:**  
   Update core logic in `index.ts` or `src/*.ts` to resolve the issue.
   ```typescript
   export function sanitizeInput(data: string) {
     return data.replace(/[^\w\s]/gi, '');
   }
   ```
2. **Update/Add Test Cases:**  
   Add or update tests in `test/*.test.mjs` to cover new edge cases.
   ```typescript
   test('sanitizes malicious input', () => {
     expect(sanitizeInput('hello<script>')).toBe('hello');
   });
   ```
3. **Ensure Consistent Encoding/Formatting:**  
   Make sure all source and test files use UTF-8 encoding and LF line endings.
4. **Document Reviewer Feedback:**  
   Address any must-fix items raised during code review.

## Testing Patterns

- **Test Files:** Located in `test/` directory, using the pattern `*.test.ts` or `*.test.mjs`.
- **Framework:** Not explicitly detected; tests are written in standard TypeScript/JavaScript style.
- **Test Example:**
  ```typescript
  import { addMemory } from '../src/memory-store';

  test('adds a memory record', () => {
    const result = addMemory({ id: '1', value: 'foo' });
    expect(result).toBeTruthy();
  });
  ```

## Commands

| Command           | Purpose                                                        |
|-------------------|----------------------------------------------------------------|
| /bugfix-tdd-ci    | Start a bugfix using TDD and update the CI test manifest       |
| /security-fix-test| Fix a security/invariant bug and update/add relevant tests     |
```
