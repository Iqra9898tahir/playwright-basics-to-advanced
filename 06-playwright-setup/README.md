# Playwright Basics: Architecture, Installation & Setup

## What is it?
Playwright is a Node.js-based end-to-end testing framework that automates browser actions for modern web applications.  
It supports multiple browsers (Chromium, Firefox, WebKit) and languages (JavaScript/TypeScript).

---

## Why do we need it?
- Automates repetitive browser testing tasks  
- Ensures reliability of web applications  
- Works cross-browser and cross-platform  
- Supports modern testing patterns like POM (Page Object Model)  

---

## How it works? (Architecture)
Playwright consists of three main layers:
1. **Test Runner**: Runs tests, handles reporting, retries, parallel execution  
2. **Browser Engine**: Chromium, Firefox, WebKit automation through DevTools / CDP  
3. **Playwright API**: Provides commands for actions like click, type, navigate, screenshot  

**Flow:**
Test Script → Playwright API → Browser Engine → Web Application
```bash
# Initialize Node project
npm init -y

# Install Playwright
npm install -D @playwright/test

# Install browsers
npx playwright install
const { test, expect } = require('@playwright/test');

test('basic test', async ({ page }) => {
  await page.goto('https://example.com');
  await expect(page).toHaveTitle(/Example/);
});
```

Playwright Relevance

Installation sets up browser binaries + test runner

Folder structure organizes tests, configs, and reports

Understanding architecture ensures you write robust, maintainable tests

Folder & File Structure

Typical Playwright project:
```
project-root/
├── tests/             # Test files
├── tests/example.spec.js
├── playwright.config.js  # Main configuration file
├── package.json
└── node_modules/
```
```
tests/: Store test files

playwright.config.js: Test runner config (timeouts, browsers, retries, reporters)

package.json: Node dependencies

node_modules/: Installed packages

Configuration Highlights
// playwright.config.js
import { defineConfig } from '@playwright/test';

export default defineConfig({
  timeout: 30000,
  retries: 1,
  use: {
    headless: true,
    viewport: { width: 1280, height: 720 },
    screenshot: 'only-on-failure',
  },
});
```

Sets timeouts, retries, headless mode, viewport size, screenshots

Can configure parallelism, test match patterns, and reporters

Interview Questions (with Answers)

What is Playwright and why is it used?
Answer: Playwright is an end-to-end testing framework for web applications. It automates browsers to test functionality reliably across multiple browsers and platforms.

What is the typical folder structure of a Playwright project?
Answer:

tests/ – test scripts

playwright.config.js – configuration

package.json – dependencies

node_modules/ – installed packages

How does Playwright architecture work?
Answer: Test scripts use Playwright API → Browser engines (Chromium, Firefox, WebKit) → interact with the web app. The Test Runner manages execution, retries, parallelism, and reporting.

How do you install Playwright and its browsers?
Answer:

npm install -D @playwright/test
npx playwright install


How do you configure Playwright tests?
Answer: Through playwright.config.js, setting timeouts, retries, browsers, headless mode, viewport size, and reporters.
