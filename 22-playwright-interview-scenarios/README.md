1. Locator Strategy in a Large Application
Scenario

You are automating a large e-commerce application.
The UI changes frequently and tests break often.

What would you do?

Prefer data-test-id attributes for all critical elements

Avoid XPath and deeply nested CSS selectors

Use role-based locators for accessibility and stability

Define a locator strategy guideline for the team

Why this works in real projects

Locators become independent of UI changes

Tests remain stable even when layouts change

Collaboration with developers improves automation quality

2. Parallel Execution Failures in CI
Scenario

Tests pass locally but fail randomly in CI when run in parallel.

How would you debug and fix this?

Check for shared state (global variables, reused contexts)

Ensure each test runs in its own browser context

Reduce workers temporarily to isolate the issue

Use Playwright traces and videos for debugging

Real-world insight

Most CI flakiness is caused by poor test isolation, not Playwright itself.

3. Authentication Handling in Enterprise Applications
Scenario

The application uses MFA and login is slow.
Logging in before every test increases execution time.

Best approach

Perform login once

Save authenticated storage state

Reuse it across tests

Avoid repeated UI logins

Why this is important

Faster execution

More stable tests

Less dependency on external authentication systems

4. Backend API Instability Affecting UI Tests
Scenario

UI tests fail because backend APIs are unstable.

What strategy would you use?

Mock API responses where possible

Intercept network calls

Validate UI behavior independently

Key principle

UI tests should validate UI behavior, not backend reliability.

5. Handling Dynamic Elements in Modern SPAs
Scenario

Elements appear after API calls, causing flaky tests.

Correct approach

Avoid waitForTimeout()

Rely on Playwright’s auto-waiting

Wait for specific UI conditions

Use expect() assertions with retries

Why this works

Reduces flakiness

Makes tests more deterministic

6. Optimizing Test Execution for Large Suites
Scenario

Your project has over 1,000 Playwright tests.

How do you optimize execution?

Split tests using projects

Separate smoke tests from regression tests

Enable retries only in CI

Use parallel execution wisely

7. Debugging Tests That Fail Only in Headless Mode
Scenario

A test passes locally but fails in headless execution.

Debugging steps

Run tests in headed mode locally

Enable Playwright trace viewer

Capture screenshots and videos

Check viewport and timing differences

8. Page Object Model (POM) Design Issues
Scenario

Page Objects are growing very large and hard to maintain.

How would you refactor?

Split pages into components

Keep Page Objects action-focused

Avoid assertions inside Page Objects

Move validations to test files

9. CI/CD Pipeline Failures
Scenario

Playwright tests are flaky and slow in CI pipelines.

How would you improve reliability?

Run in headless mode

Reduce unnecessary browser launches

Enable retries only in CI

Analyze HTML reports and traces
