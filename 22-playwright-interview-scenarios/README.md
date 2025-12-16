
## 1. Locator Strategy in a Large Application

### Scenario
You are automating a large e-commerce application.
The UI changes frequently and tests break often.

### Solution
- Prefer `data-test-id` attributes
- Avoid XPath and deeply nested CSS selectors
- Use role-based locators (`getByRole`)
- Define a locator priority strategy for the team

### Why This Works
- Locators remain stable despite UI changes
- Tests become easier to maintain
- Reduces flaky failures

---

## 2. Parallel Execution Failures in CI

### Scenario
Tests pass locally but fail randomly in CI when executed in parallel.

### Debugging Approach
- Check for shared state across tests
- Ensure each test uses its own browser context
- Reduce workers temporarily to isolate failures
- Use Playwright traces and videos

### Real-World Insight
Most CI flakiness is caused by poor test isolation, not Playwright itself.

---

## 3. Authentication Handling in Enterprise Applications

### Scenario
Login involves MFA and takes significant time.
Logging in before every test slows execution.

### Best Practice
- Perform login once
- Save authenticated storage state
- Reuse it across tests
- Avoid repeated UI logins

### Benefit
- Faster test execution
- More stable tests
- Reduced dependency on external systems

---

## 4. Backend API Instability Affecting UI Tests

### Scenario
UI tests fail because backend APIs are unreliable.

### Strategy
- Mock API responses where possible
- Intercept network requests
- Validate UI behavior independently

### Key Principle
UI tests should validate UI behavior, not backend reliability.

--
