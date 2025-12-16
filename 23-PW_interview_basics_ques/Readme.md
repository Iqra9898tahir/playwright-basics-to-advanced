# Automation Framework Explanation (Playwright)

This document explains how I describe my automation framework
during interviews, using clear and practical language.

---

## How would you explain your automation framework?

### Spoken Interview Answer

> My automation framework is built using Playwright and follows the Page Object Model design pattern.

> I separate all locators and reusable actions into page classes inside a dedicated `pages` folder.  
> This way, when the UI changes, I only update the locators in one place instead of modifying multiple tests.

> I use stable locator strategies such as `getByRole`, `getByText`, and `getByPlaceholder`, and I avoid fragile locators like XPath or dynamic IDs.

> There is a clear separation of responsibilities in the framework:
> - Test files contain only test logic and assertions
> - Page Objects contain element locators and user actions
> - Utilities contain reusable helpers
> - Test data is managed separately

> I also use Playwright fixtures for things like browser context creation and login setup.
> For authenticated flows, I store logged-in sessions using `storageState` so tests don’t need to log in repeatedly.

> For reliability, I rely on Playwright’s built-in auto-waiting and assertions such as `toBeVisible()` and `toHaveText()` instead of adding hard waits or sleeps.

> The framework supports parallel execution, multiple environments like dev, stage, and prod,
> and generates detailed reports with screenshots, videos, and trace logs.

> Overall, this structure makes the framework clean, scalable, and easy to maintain.

---

## Why this framework works well in real projects

- Minimal duplication of locators
- Stable and readable tests
- Easy maintenance when UI changes
- Faster execution using session reuse
- Strong debugging support

---

## Interview Tip

> When explaining a framework, focus on **why you made design decisions**, not just what tools you used.
# Handling Flaky Tests in Playwright (Interview Answer)

This document explains how I answer questions about
flaky tests based on real-world Playwright experience.

---

## What will you do if a test is flaky and fails randomly?

### Spoken Interview Answer

> When a test becomes flaky, I never assume it’s just a locator issue.

> First, I open the Playwright trace viewer to see exactly where and why the test is failing.
> Traces help me understand timing, UI state, and network behavior during failure.

> After that, I systematically check four key areas.

---

## 1. Locator Stability

> I verify whether the locator is stable or dynamic.
> If needed, I replace it with more reliable locators like `getByRole`, `getByText`, or `getByPlaceholder`.

- Avoid XPath
- Avoid dynamic IDs
- Prefer semantic and accessibility-based locators

---

## 2. Synchronization Issues

> Many flaky tests fail because of incorrect timing assumptions.

> I remove manual waits and replace them with Playwright assertions such as:
> - `toBeVisible()`
> - `toHaveText()`
> - `toBeEnabled()`

This ensures the test waits for the actual UI condition.

---

## 3. Network or API Delays

> If the UI depends on backend APIs, I make sure the test waits for the required network response.
> Sometimes I wait for network idle or specific API responses before validating the UI.

---

## 4. Animations and Rendering Delays

> Some applications have animations or slow rendering.
> In such cases, I either disable animations or wait for the element to become stable before interacting.

---

## Handling CI Environment Issues

> If the flakiness occurs only in CI due to slower execution,
> I enable retry logic specifically for CI environments.

> I also avoid unnecessary UI validations to make the test more resilient.

---

## Final Thought (Interview Favorite)

> My goal is to remove all timing assumptions from the test
> and ensure locators and waits are fully stable and deterministic.

---

## Key Takeaways for Interviews

- Flaky tests are usually caused by timing, not tools
- Trace viewer is the first debugging step
- Stable locators and proper waits solve most issues
- CI slowness needs resilience, not hacks

# Playwright Interview Questions & Answers (Spoken + Real Scenarios)

This README contains **spoken-style interview answers** for Playwright,
covering both **conceptual questions** and **real-world scenarios**
based on actual automation challenges.

---

## Part 1: Core Playwright Concepts

---

## 1. What is Playwright and why do you use it?

### Spoken Interview Answer
> Playwright is a modern automation framework developed by Microsoft.
> I use it because it supports multiple browsers, has built-in auto-waits,
> handles iframes, new tabs, file uploads, and provides fast and reliable tests.
> It also comes with tracing and debugging features out of the box.

---

## 2. Difference between Playwright and Selenium?

### Spoken Interview Answer
> Selenium is WebDriver-based and relatively slower.
> Playwright works at the browser level, so it’s faster and more stable.
> Playwright has built-in auto-waiting, parallel execution, network mocking,
> file upload/download handling, and does not require external drivers.

---

## 3. How do you handle dynamic dropdowns?

### Spoken Interview Answer
> I never rely on index because it can change.
> I type into the input, wait for the dropdown options to appear,
> and select the option using visible text.
> This keeps the test stable even if the order changes.

---

## 4. How do you handle tables?

### Spoken Interview Answer
> I locate all rows, loop through them, find the matching cell value,
> and then perform actions like Edit or Delete inside the same row.
> I always use row-column logic instead of relying on row index.

---

## 5. Have you used Page Object Model (POM)?

### Spoken Interview Answer
> Yes. I keep locators and reusable actions in page classes
> and keep test logic and assertions inside spec files.
> This makes the framework cleaner, easier to maintain,
> and changes can be handled in one place.

---

## 6. How do you handle alerts in Playwright?

### Spoken Interview Answer
> Playwright uses dialog event listeners.
> I listen for the dialog event, read the message,
> and then accept or dismiss it.
> There’s no need for switchTo like Selenium.

---

## 7. How do you handle file upload?

### Spoken Interview Answer
> For HTML file inputs, I use setInputFiles.
> For OS-level dialogs, I wait for the fileChooser event
> and attach the file.
> Playwright handles both cases easily.

---

## 8. How do you handle file downloads?

### Spoken Interview Answer
> I wait for the download event using page.waitForEvent('download'),
> trigger the download, get the suggested filename,
> and then save or validate the file.

---

## 9. How do you handle new tabs or windows?

### Spoken Interview Answer
> I use context.waitForEvent('page') to capture the new tab.
> Then I interact with that page object directly.
> There’s no window-handle switching like Selenium.

---

## 10. What are auto-waits in Playwright?

### Spoken Interview Answer
> Playwright automatically waits for elements to be visible,
> stable, and ready before interacting.
> This removes the need for manual sleeps
> and significantly reduces flakiness.

---

## 11. What is a test fixture in Playwright?

### Spoken Interview Answer
> Fixtures provide reusable setup like login,
> test data, or environment configuration.
> They run before and after tests
> and help avoid repeating setup logic.

---

## 12. What is storageState?

### Spoken Interview Answer
> storageState stores cookies and localStorage after login.
> I use it to avoid logging in again and again,
> which makes tests much faster and more stable.

---

## 13. How do you handle network mocking?

### Spoken Interview Answer
> I intercept API calls using route(),
> mock responses, delay APIs, or simulate errors.
> This allows me to test frontend behavior
> without depending on backend stability.

---

## 14. What is trace viewer?

### Spoken Interview Answer
> Playwright records test execution including steps,
> DOM snapshots, network calls, and screenshots.
> When a test fails, I open the trace viewer
> to replay the test and find the root cause.

---

## 15. How do you ensure test stability?

### Spoken Interview Answer
> I use auto-waits, stable locators,
> avoid hard sleeps, and interact only with
> visible and attached elements.

---

## 16. Difference between HTML modal and browser alert?

### Spoken Interview Answer
> Browser alerts are JavaScript dialogs and block the UI.
> HTML modals are normal DOM elements.
> Playwright handles HTML modals with locators
> and browser alerts using dialog events.

---

## Part 2: Real-Time Scenario-Based Questions

---

## Scenario 1: Login required for every test

### Spoken Interview Answer
> Instead of logging in repeatedly,
> I generate a login state once using storageState
> and reuse it across tests.
> This improves speed and stability.

---

## Scenario 2: Page loads slow and element is not available

### Spoken Interview Answer
> I avoid manual waits.
> I rely on Playwright auto-waiting
> or add expectations like toBeVisible or toHaveText.
> This ensures the test waits for the correct UI state.

---

## Scenario 3: Table with hundreds of rows

### Spoken Interview Answer
> I loop through rows, match the target cell value,
> and perform the action inside the same row.
> This works even if row positions change.

---

## Scenario 4: Tests fail randomly in CI

### Spoken Interview Answer
> I check locator stability, synchronization issues,
> network delays, animations, and environment differences.
> I add proper waits, retries in CI,
> and remove unnecessary UI validations.

---

## Scenario 5: Dynamic dropdown based on typing

### Spoken Interview Answer
> I type into the input,
> wait for options to appear,
> and select using visible text instead of index.

---

## Scenario 6: File upload and download validation

### Spoken Interview Answer
> For uploads, I use setInputFiles or fileChooser.
> For downloads, I use page.waitForEvent('download')
> and validate the downloaded file.

---

## Scenario 7: Popup blocks the page

### Spoken Interview Answer
> If it’s an HTML modal, I treat it as a DOM element.
> If it’s a JS alert, I handle it using dialog events.

---

## Scenario 8: New tab opens after clicking a link

### Spoken Interview Answer
> I use context.waitForEvent('page')
> to capture and interact with the new tab.

---

## Scenario 9: Validate API before UI interaction

### Spoken Interview Answer
> I use Playwright’s request fixture
> to validate the API response first,
> then continue with UI validation.

---

## Scenario 10: Validate product price in e-commerce app

### Spoken Interview Answer
> I search for the product,
> loop through product cards,
> match the product name,
> and extract the price from the same container.

---

## Scenario 11: Parallel tests overwrite data

### Spoken Interview Answer
> I make sure tests are independent,
> use separate users or data,
> and isolate state using worker-based fixtures.

---

## Scenario 12: Infinite scroll page

### Spoken Interview Answer
> I scroll using page.evaluate
> until the target item appears,
> then interact with it.

---

## Scenario 13: Mock API error (500)

### Spoken Interview Answer
> I mock the API using route()
> to return a 500 response
> and validate the UI error handling.

---

## Scenario 14: Disabled button until form is valid

### Spoken Interview Answer
> I fill required fields
> and assert that the button becomes enabled
> using toBeEnabled().

---

## Scenario 15: Running Playwright in CI

### Spoken Interview Answer
> I install browsers,
> run tests in headless mode,
> configure environment variables,
> and upload traces, videos, and reports
> as CI artifacts.

---

## Final Interview Tip

> Interviewers care more about **how you think**
> than about syntax.
> Always explain problem → approach → reasoning.
# Playwright Advanced Interview Questions (Missing/High-Priority)

This README covers **advanced Playwright concepts**, **scenario-based questions**, and **framework-level understanding** that are often asked in interviews but were not covered in previous notes.

---

## Part 1: Core Advanced Concepts

---

### 1️⃣ Browser vs Context vs Page

**Spoken Interview Answer:**  
> Browser is the actual browser instance.  
> Context is an isolated session (cookies, storage) — each test runs in its own context.  
> Page is a single tab in that context.  
> Using separate contexts ensures test isolation and allows parallel execution safely.

---

### 2️⃣ How does Playwright ensure test isolation?

**Spoken Interview Answer:**  
> Each test runs in its own **browser context**, so cookies, localStorage, and cache do not leak between tests.  
> This allows reliable parallel execution and prevents flaky results.

---

### 3️⃣ How do retries work in Playwright?

**Spoken Interview Answer:**  
> Retries can be configured per test or globally in `playwright.config`.  
> Usually enabled in CI to handle transient issues.  
> Retries are not a fix for flaky tests — they only mask temporary failures.

---

### 4️⃣ How do you run specific tests / tags / grep?

**Spoken Interview Answer:**  
> Use `test.only` to run a single test, `test.describe` to group tests, or `--grep` to run tests matching a pattern.  
> This is useful for smoke tests, regression suites, or CI pipelines.

---

### 5️⃣ Difference between `page.locator()` and `page.$()`

**Spoken Interview Answer:**  
> `page.locator()` returns a **Locator**, which supports **auto-waiting** and retries.  
> `page.$()` returns an **ElementHandle**, which does **not** auto-wait.  
> Using Locator is recommended for stable tests.

---

## Part 2: Fixtures & Test Data

---

### 6️⃣ Global Setup vs Fixtures – when to use what?

**Spoken Interview Answer:**  
> Global setup runs once per test run — e.g., login, environment setup.  
> Fixtures run per test or per worker — e.g., browser page, test data injection.  
> Both help avoid repeating setup code.

---

### 7️⃣ How do you handle test data management?

**Spoken Interview Answer:**  
> I use static test data for predictable scenarios.  
> For dynamic tests, I generate data using libraries like Faker.  
> Environment-specific test data is managed using config or `.env` files.

---

## Part 3: Debugging & Flaky Tests

---

### 8️⃣ How do you debug flaky tests using Trace Viewer?

**Spoken Interview Answer:**  
> Open the trace, replay the steps, check locator resolution, network calls, and timing issues.  
> This helps identify whether flakiness comes from locators, waits, or environment issues.

---

### 9️⃣ What happens if one worker crashes?

**Spoken Interview Answer:**  
> Only that worker’s tests fail.  
> Other workers continue independently.  
> Retried tests and isolation prevent cascading failures.

---

### 🔟 How do you combine API and UI testing in Playwright?

**Spoken Interview Answer:**  
> I create test data using APIs, validate via UI, then clean up via API.  
> This ensures UI tests do not fail due to unstable backend data.

---

### 1️⃣1️⃣ How do you validate API schema or response structure?

**Spoken Interview Answer:**  
> I validate status codes, response keys, and data types using assertions.  
> Can also mock API responses to simulate backend scenarios.

---

## Part 4: Trick / Follow-up Questions

---

### 1️⃣2️⃣ Why not use `waitForTimeout()`?

**Spoken Interview Answer:**  
> Fixed waits are prone to flakiness.  
> Always use **auto-waits** or explicit expectations like `toBeVisible()` or `toHaveText()`.

---

### 1️⃣3️⃣ What do you do if auto-wait is not enough?

**Spoken Interview Answer:**  
> Use explicit locators with conditions, or wait for network calls and DOM stability.  
> Avoid adding arbitrary sleep times.

---

### 1️⃣4️⃣ Can Playwright test mobile?

**Spoken Interview Answer:**  
> Yes, by emulating devices with viewport and user-agent settings.  
> Supports mobile web testing, but not real devices.

---

### 1️⃣5️⃣ When would you NOT automate a test?

**Spoken Interview Answer:**  
> One-time flows, highly unstable UI, or tests with low ROI.  
> Always focus on stable, repeatable, and critical scenarios.

---

## Part 5: Framework Design / Scalability

---

### 1️⃣6️⃣ How do you design a scalable Playwright framework?

**Spoken Interview Answer:**  
> I use **Page Object Model** for locators and reusable actions.  
> Maintain separation of **tests, pages, utilities, and test data**.  
> Use **fixtures** for login, environment setup, and context creation.  
> Configure **parallel execution, retries, and reporting**.  
> Use **storageState** for login reuse.  
> This makes the framework **clean, maintainable, and scalable**.

---

