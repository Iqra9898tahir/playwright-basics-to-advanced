# Parallel Execution in Playwright

## What is Parallel Execution?
Parallel execution means running multiple tests at the same time instead of one after another.

This reduces:
- Execution time
- CI pipeline duration

---

## Does Playwright Support Parallel Execution?
Yes.  
Playwright runs tests in parallel **by default** using workers.

---

## What is a Worker?
A worker is a separate process that executes tests.

Key points:
- Each worker runs independently
- Each worker has its own browser instance
- Workers do not share state

---

## How Parallel Execution Works
1. Playwright starts the test runner
2. Number of workers is determined
3. Test files are distributed across workers
4. Tests run simultaneously
5. Results are merged into one report

---

## Workers vs Test Files
- Playwright runs **test files** in parallel
- Tests inside the same file run sequentially by default

---

## Controlling Number of Workers
```js
module.exports = {
  workers: 4
};
```
---

## When Parallel Execution Fails
Parallel execution often fails due to:
- Shared test data
- Shared user accounts
- Order-dependent tests
- Global state usage

---

## Role of Test Data Management
Parallel execution requires:
- Unique test data per test
- No shared users
- Isolated environments

(This connects directly to Topic 15)

---

## Serial Execution (When Needed)
Sometimes tests must run sequentially.

Examples:
- Dependent workflows
- Stateful scenarios
```js
test.describe.serial('Sequential Tests', () => {
  // tests here run one after another
});
```
---

## Parallel vs Serial Execution
| Parallel | Serial |
|-------|-------|
| Faster | Slower |
| Needs isolation | Allows dependency |
| Best practice | Use only when required |

---

## Parallel Execution in CI/CD
- Reduces pipeline time
- Improves feedback speed
- Requires stable test design

---

## Common Interview Questions & Answers

**Q: Does Playwright run tests in parallel by default?**  
A: Yes, Playwright uses workers to run tests in parallel.

**Q: Why do tests fail only in parallel?**  
A: Due to shared data, shared users, or improper test isolation.

**Q: How do you limit parallel execution?**  
A: By controlling the number of workers or using serial execution.

---

## Common Mistakes
- Using the same user in all tests
- Depending on test order
- Disabling parallelism instead of fixing data issues

---

## Key Takeaways
- Parallel execution is default in Playwright
- Workers enable concurrency
- Test isolation is mandatory
- Proper data strategy ensures stability
