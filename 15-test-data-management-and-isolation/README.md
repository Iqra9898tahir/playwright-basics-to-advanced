# Test Data Management & Test Isolation

## What is Test Data?
Test data is the input information used to execute test cases.

Examples:
- User credentials
- Orders
- Products
- API payloads

---

## Why Test Data Management Matters
Poor test data strategy leads to:
- Flaky tests
- Data conflicts
- Tests failing in parallel execution
- Unreliable CI pipelines

Good test data management ensures:
- Stable tests
- Independent execution
- Scalability

---

## What is Test Isolation?
Test isolation means:
Each test should run independently and not depend on other tests.

A test should:
- Create its own data
- Clean up after itself
- Not rely on shared state

---

## Problems Without Test Isolation
- One test breaks another
- Order-dependent failures
- Parallel execution issues

---

## Common Test Data Strategies

### 1️⃣ Hardcoded Data (NOT Recommended)
```js
const username = 'testuser';
Problems:

Data conflicts

Not scalable

Breaks in parallel runs
2️⃣ Static Test Data Files
users.json

Used when:

Data is read-only

No mutation happens
 3️⃣ Dynamic Test Data (BEST PRACTICE)

Create data at runtime using:

API calls

Randomized values

Factories
Data Creation via API (Conceptual)

### 🔹 START CODE BLOCK (```js)

```
---

## Data Cleanup Strategies
- Delete data after test
- Use disposable test environments
- Reset database (in lower envs)

---

## Test Data in Parallel Execution
Parallel tests require:
- Unique data per test
- No shared accounts
- Isolated sessions

---

## Environment-Specific Data
- Dev / QA / Staging data should differ
- Never use production data
- Use environment variables

---

## Common Interview Questions & Answers

**Q: How do you avoid test data conflicts?**  
A: By creating unique test data per test and ensuring test isolation.

**Q: Can tests share data?**  
A: No, shared data causes flaky tests, especially in parallel execution.

**Q: How does API testing help with test data?**  
A: APIs allow fast and reliable test data setup and cleanup.

---

## Common Mistakes
- Reusing the same user across tests
- Hardcoding credentials
- Not cleaning up test data

---

## Key Takeaways
- Test data strategy is critical for stability
- Test isolation enables parallel execution
- Dynamic data is the best practice
