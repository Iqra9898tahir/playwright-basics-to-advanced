# Playwright Test Anatomy

## What is Playwright?
Playwright is an end-to-end automation framework used to test web applications across different browsers.

It allows automation of UI interactions and API testing.

---

## What is a Playwright Test?
A Playwright test is a function that contains steps to validate application behavior in a browser.

Each test represents one scenario or user flow.

---

## What is `test()`?
`test()` is a function provided by Playwright’s test runner.

It is used to define a test case.

---

## Basic Playwright Test Structure
```js
test('basic test', async ({ page }) => {
  await page.goto('https://example.com');
});
```
---

## Why is the Test Function `async`?
Browser interactions take time (page load, clicks, API calls).

Playwright actions are asynchronous, so the test function must be marked as `async`.

---

## What is `page`?
`page` represents a single browser tab.

Using `page`, we can:
- Open URLs
- Click elements
- Fill input fields
- Read text
- Validate UI behavior

---

## Why do we use `await` with `page` actions?
Each Playwright action returns a Promise.

Using `await` ensures:
- Correct execution order
- Stable test execution
- No flaky tests

---

## Example with Multiple Actions
```
test('login flow', async ({ page }) => {
  await page.goto('https://example.com');
  await page.click('#login');
  await page.fill('#username', 'testuser');
});
```
---

## Key Points to Remember
- Every Playwright test uses `test()`
- Test functions are async
- `page` is the browser context
- `await` is mandatory for Playwright actions

---

## Interview Notes
- Playwright uses an async test runner
- `page` represents a browser tab
- Missing `await` can cause test failures
