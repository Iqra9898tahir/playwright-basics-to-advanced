# Playwright Test Runner – Architecture & Execution Flow

## What is Playwright Test Runner?
Playwright Test Runner is the built-in test execution engine provided by Playwright.

It is responsible for:
- Discovering test files
- Executing tests
- Managing parallelism
- Handling retries and reporting

---

## Why Use Playwright’s Test Runner?
- Built-in support (no external tools needed)
- Fast execution
- Parallel by default
- Integrated reporting and debugging

---

## Test File Structure
Playwright identifies test files using:
- `.spec.js`
- `.test.js`

Example:
```text
tests/
 ├── login.spec.js
 ├── dashboard.spec.js
```
---

## Test Discovery Process
1. Playwright scans the `tests` directory
2. Identifies test files
3. Loads test definitions
4. Prepares workers for execution

---

## What is a Worker?
A worker is an isolated process that runs tests.

Key points:
- Each worker has its own browser context
- Workers enable parallel execution
- Workers do not share state

---

## Test Execution Flow
1. Test runner starts
2. Workers are created
3. Tests are assigned to workers
4. Hooks are executed
5. Tests run
6. Results are collected
7. Reports are generated

---

## Hooks in Execution Flow
Hooks allow setup and teardown logic.

Common hooks:
- beforeAll
- beforeEach
- afterEach
- afterAll

---

## Isolation by Default
Playwright ensures:
- New browser context per test
- No shared cookies or storage
- Clean state for each test

---

## Retries Handling
If enabled:
- Failed tests are retried
- Only failing tests rerun
- Helps reduce flaky failures

---

## Common Interview Questions & Answers

**Q: Is Playwright test runner parallel by default?**  
A: Yes, Playwright runs tests in parallel using workers.

**Q: What is the difference between a worker and a browser context?**  
A: Worker is a process; context is an isolated browser session.

**Q: Does Playwright share state between tests?**  
A: No, tests are isolated by default.

---

## Common Mistakes
- Assuming tests run sequentially
- Sharing test data between tests
- Misusing beforeAll for data setup

---

## Key Takeaways
- Test runner controls execution
- Workers enable parallelism
- Isolation ensures stability
- Understanding runner = better framework design
