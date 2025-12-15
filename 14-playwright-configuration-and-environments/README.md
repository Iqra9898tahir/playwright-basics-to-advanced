# Playwright Configuration & Environment Management

## What is playwright.config.js?
`playwright.config.js` is the central configuration file in Playwright.

It controls:
- Test execution behavior
- Browser settings
- Environment configuration
- Reporting and retries

---

## Why Configuration is Important
- Avoids hardcoding values
- Enables environment-based testing
- Centralizes framework behavior
- Improves maintainability

---

## Common Configuration Options
```js
module.exports = {
  timeout: 30000,
  retries: 1,
  use: {
    baseURL: 'https://example.com',
    headless: true
  }
};
```
---

## baseURL
`baseURL` allows you to avoid repeating URLs in tests.

Instead of:
```js
await page.goto('https://example.com/login');
```
```js
await page.goto('/login');
```
---

## Environment Management
Real projects have multiple environments:
- Dev
- QA
- Staging
- Production

Environment values should NOT be hardcoded.

---

## Using Environment Variables
Environment variables help control behavior without changing code.

Examples:
- Base URL
- Credentials
- Feature flags

---

## Running Tests in Different Environments
```js
BASE_URL=https://qa.example.com npx playwright test
```
---

## Browser Configuration
Playwright allows running tests on:
- Chromium
- Firefox
- WebKit

This ensures cross-browser coverage.

---

## Retries
Retries rerun failed tests automatically.

Useful for:
- Flaky tests
- Network instability

---

## Common Interview Questions & Answers

**Q: Why use baseURL?**  
A: To avoid duplication and make environment switching easier.

**Q: Where should environment-specific values live?**  
A: In environment variables, not in test code.

**Q: Does Playwright support multi-browser testing?**  
A: Yes, out of the box.

---

## Common Mistakes
- Hardcoding URLs
- Ignoring environment separation
- Overusing retries

---

## Key Takeaways
- Configuration centralizes behavior
- baseURL simplifies navigation
- Environment variables enable flexibility
- Good config = scalable framework
