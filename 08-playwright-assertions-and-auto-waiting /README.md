# Playwright Assertions & Auto-Waiting

## What is an Assertion?
An assertion is a validation step that checks whether the application behaves as expected.

Assertions decide whether a test:
- Passes
- Fails

Without assertions, tests have no value.

---

## Why Assertions Are Important
- Validate UI behavior
- Catch bugs automatically
- Provide confidence in test results
- Required for meaningful automation

---

## Assertions in Playwright
Playwright uses the `expect()` library for assertions.

Assertions in Playwright are:
- Auto-waiting
- Reliable
- Built into the test runner

---

## What is Auto-Waiting?
Auto-waiting means Playwright automatically waits for a condition to become true before failing the test.

This removes the need for manual waits.

---

## Why Auto-Waiting is Powerful
- Reduces flaky tests
- Improves test stability
- Simplifies test code
- Saves execution time

---
```
## Common Playwright Assertions
await expect(page).toHaveTitle('Dashboard');
await expect(page).toHaveURL(/dashboard/);
await expect(locator).toBeVisible();
await expect(locator).toHaveText('Welcome');
await expect(locator).toBeEnabled();
```
---

## Assertion vs Wait (INTERVIEW QUESTION)

- **Assertion** checks a condition and fails if it is not met
- **Wait** pauses execution without validation

Playwright assertions already include smart waiting.

---

## Good Practice
- Use assertions instead of manual waits
- Validate what the user sees
- Keep assertions meaningful

---

## Bad Practice
- Using hard waits (setTimeout, sleep)
- Asserting internal implementation details
- Overusing assertions unnecessarily

---

## Common Mistakes
- Forgetting to use `await` with expect
- Adding extra waits before assertions
- Asserting unstable text

---

## Interview Questions & Answers

**Q: What makes Playwright assertions different?**  
A: They include built-in auto-waiting and retry mechanism.

**Q: Do we need explicit waits in Playwright?**  
A: No, Playwright handles waiting automatically through assertions and actions.

**Q: What happens if an assertion fails?**  
A: The test fails immediately with a detailed error.

---

## Key Takeaways
- Assertions validate application behavior
- Playwright assertions auto-wait
- Avoid manual waits
- Strong assertions = stable automation

