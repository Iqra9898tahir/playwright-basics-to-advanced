# CI/CD with GitHub Actions for Playwright

## What is GitHub Actions?
GitHub Actions is a CI/CD tool provided by GitHub that runs workflows automatically.

Workflows are defined using YAML files.

---

## Why Use GitHub Actions with Playwright?
- Automatically run tests on every push
- Catch bugs early
- No manual execution
- Free for public repositories

---

## Where CI Configuration Lives
```
.github/workflows/playwright.yml
```
---

## When Does CI Run?
CI runs when:
- Code is pushed
- Pull request is created

---

## Basic GitHub Actions Workflow Steps
1. Checkout code
2. Setup Node.js
3. Install dependencies
4. Install Playwright browsers
5. Run Playwright tests
6. Upload test reports

---

## Sample Playwright GitHub Actions Workflow
```
name: Playwright Tests

on:
  push:
    branches: [ main ]
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Install Playwright Browsers
        run: npx playwright install --with-deps

      - name: Run Playwright Tests
        run: npx playwright test

      - name: Upload Playwright Report
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: playwright-report
          path: playwright-report

```

---

## Headless Execution in CI
Playwright runs in headless mode by default in CI environments.

---

## Handling Secrets in CI
Secrets should be stored in:
- GitHub Repository → Settings → Secrets

Never hardcode credentials.

---

## Common Interview Questions

**Q: How do you integrate Playwright with CI/CD?**  
A: By configuring GitHub Actions to run Playwright tests on code push.

**Q: Where do you see test results in CI?**  
A: In GitHub Actions logs and uploaded artifacts.

---

## Key Takeaways
- CI runs automatically on push
- GitHub Actions uses YAML
- Playwright fits naturally in CI
- Reports help debug failures
