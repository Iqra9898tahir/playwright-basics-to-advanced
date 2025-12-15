# Reporting & Debugging in Playwright

## Why Reporting is Important
Test reports help:
- Understand test results
- Identify failed scenarios
- Debug issues quickly
- Share results with the team

---

## Built-in Reporting in Playwright
Playwright provides built-in reporters without extra configuration.

Common reporters:
- HTML Report
- List Reporter
- JSON Reporter
- JUnit Reporter

---

## HTML Report
The HTML report is the most commonly used report.

Features:
- Test pass/fail status
- Execution time
- Error messages
- Screenshots and traces (if enabled)

---

## Generating HTML Report
```
npx playwright test
npx playwright show-report
```
---

## Debugging Failed Tests
Playwright provides multiple debugging tools:
- Trace Viewer
- Screenshots
- Videos
- Debug mode

---

## Trace Viewer
Trace viewer records everything that happens during test execution.

It captures:
- Actions
- Network calls
- DOM snapshots
- Screenshots

---

## When to Use Trace Viewer
- Flaky tests
- CI failures
- Hard-to-reproduce bugs

---

## Screenshots
Screenshots help visually understand failures.

They are usually captured:
- On test failure
- On demand for debugging

---

## Videos
Videos record the entire test execution.

Useful for:
- CI debugging
- Understanding timing issues

---

## Debug Mode
Debug mode pauses execution step-by-step.

```bash
npx playwright test --debug
```
---

## Common Interview Questions & Answers

**Q: How do you debug a failing Playwright test?**  
A: Using trace viewer, screenshots, videos, and debug mode.

**Q: What is Playwright trace?**  
A: A detailed execution recording that helps analyze failures.

**Q: Do you need third-party tools for reporting?**  
A: No, Playwright provides built-in reporters.

---

## Common Mistakes
- Ignoring trace files
- Not enabling debugging tools in CI
- Relying only on console logs

---

## Key Takeaways
- Reports help analyze test results
- Trace viewer is a powerful debugging tool
- Screenshots and videos improve visibility
- Debug mode helps step-by-step analysis
