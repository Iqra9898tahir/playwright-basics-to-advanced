1️⃣ Locator Strategy (Real App Scenario)
❓ Question

You are automating a large e-commerce application.
The UI changes frequently, and your tests break often.
How would you design a stable locator strategy?

✅ Answer

Prefer data-test-id attributes added specifically for automation

Avoid XPath and deep CSS selectors

Use role-based locators for accessibility-driven stability

Establish a locator priority guideline across the team

Example Explanation:

“I ask developers to add data-test-id attributes. This keeps locators independent of UI changes and improves test stability.”

2️⃣ Parallel Execution Issue (Real CI Scenario)
❓ Question

Your Playwright tests run fine locally but fail randomly in CI when executed in parallel.
How do you debug and fix this?

✅ Answer

Check for shared state between tests (global variables, reused contexts)

Ensure each test uses its own browser context

Reduce workers temporarily to isolate failures

Use Playwright traces and videos to analyze flaky behavior

Key Explanation:

“Most CI flakiness comes from poor test isolation, not Playwright itself.”

3️⃣ Authentication Handling (Enterprise App)
❓ Question

In a real enterprise app, login takes time and MFA is enabled.
How would you handle authentication efficiently in Playwright?

✅ Answer

Perform login once

Save authenticated storage state

Reuse it across tests

Avoid UI login for every test

Why:

Faster execution

More stable tests

Less dependency on external auth systems

4️⃣ Network Dependency Failure
❓ Question

Your test depends on a backend API that sometimes fails.
What strategy would you use to keep UI tests stable?

✅ Answer

Use API mocking where possible

Intercept network calls

Validate UI independently from backend instability

Real-World Justification:

“UI tests should validate UI behavior, not backend reliability.”

5️⃣ Handling Dynamic Elements (Modern SPA)
❓ Question

Elements load dynamically after API responses.
How do you avoid flaky waits?

✅ Answer

Avoid waitForTimeout

Use auto-waiting in Playwright

Wait for specific UI conditions (visibility, enabled state)

Leverage expect() assertions with retries

6️⃣ Test Runner Configuration (Large Project)
❓ Question

Your project has 1,000+ tests.
How would you optimize Playwright execution?

✅ Answer

Split tests using projects

Run smoke tests separately

Configure retries only in CI

Use parallel execution wisely

7️⃣ Debugging a Failing Test (Real Scenario)
❓ Question

A test passes locally but fails only in headless mode.
How do you debug it?

✅ Answer

Run in headed mode locally

Enable Playwright trace viewer

Capture screenshots & videos

Compare viewport and timing differences

8️⃣ Page Object Model Design
❓ Question

Your POMs are growing very large and hard to maintain.
What refactoring would you do?

✅ Answer

Split pages into components

Avoid assertions inside page objects

Keep POMs action-focused

Move validations to test layer

9️⃣ CI/CD Integration Failure
❓ Question

Playwright tests are slow and flaky in CI.
What steps would you take?

✅ Answer

Run in headless mode

Reduce browser launches

Use retries only in CI

Analyze reports & traces

🔥 How Interviewers Judge You

They don’t want:
❌ “Playwright is a testing tool”
❌ “Locators are used to find elements”

They want:
✅ Decision making
✅ Trade-offs
✅ Real-world reasoning
