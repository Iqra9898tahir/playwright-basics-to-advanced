# Playwright Folder Structure

---
```
## 📁 Folder Structure

Playwright_automation
├── .github
│ └── workflows
│ └── playwright.yml
├── tests
│ └── example.spec.js
├── playwright.config.js
├── package.json
├── package-lock.json
└── node_modules
```

### 🔹 Explanation of Each Folder/File

1. **`.github/workflows/playwright.yml`**
   - Contains GitHub Actions workflow for **CI/CD**.
   - Automatically runs Playwright tests on **push or pull requests**.
   - Helps maintain **stable builds** and **code quality**.
   - **Interview explanation:**  
     *"This folder contains GitHub Actions workflow. The `playwright.yml` file is used for CI/CD to automatically run Playwright tests in a clean environment whenever code is pushed or a pull request is created."*

2. **`tests/` folder**
   - Contains all Playwright test files (`.spec.js`).
   - Organized by **feature or functionality**.

3. **`tests/example.spec.js`**
   - **This is a Playwright test file where test cases are written using Playwright Test Runner. It contains browser actions and assertions.**
   - Uses `test()`, `page.goto()`, and `expect()` for browser automation and assertions.
   - **Interview explanation:**  
     *"Each `.spec.js` file represents a test suite and contains scenarios for end-to-end testing of the application."*

4. **`playwright.config.js`**
   - **Playwright.config.js is the central configuration file that controls how Playwright tests run across different browsers, environments, timeouts, retries, and reporting.**
   - Controls:
     - Browsers (Chromium, Firefox, WebKit)
     - Base URL
     - Timeouts
     - Headless or headed execution
     - Test retries, screenshots, and videos
   - **Interview explanation:**  
     *"This file controls how Playwright tests run in different environments and provides global configurations for test execution."*

5. **`package.json`**
   - **Manages project dependencies and provides npm scripts to run Playwright tests.**
   - Node.js metadata and dependency file.
   - Key script example:
     ```json
     "scripts": {
       "test": "npx playwright test"
     }
     ```
   - **Interview explanation:**  
     *"package.json manages dependencies and scripts for running Playwright tests in this project."*

6. **`package-lock.json`**
   - **Locks dependency versions to ensure consistency across environments.**
   - Ensures all developers and CI/CD pipelines use the exact same package versions.
   - **Interview explanation:**  
     *"package-lock.json ensures consistent builds and prevents unexpected issues due to version mismatches."*

7. **`node_modules/`**
   - Contains all installed npm packages required by Playwright.
   - Should **not** be committed to GitHub.
   - **Interview explanation:**  
     *"node_modules contains all installed dependencies required for Playwright to function correctly."*

---

## ⚡ Why Node.js and npm for Playwright

- **Node.js**
  - Provides the runtime to execute JavaScript-based Playwright tests **outside the browser**.
  - Controls browsers, handles async operations, and runs test scripts.
  - **Interview explanation:**  
    *"Node.js provides the execution environment for Playwright tests, allowing JavaScript-based test scripts to run outside the browser and control browser instances."*

- **npm**
  - Node Package Manager used to install Playwright and dependencies.
  - Runs commands like `npx playwright test`.
  - **Interview explanation:**  
    *"npm is used to manage Playwright as a dependency and to execute Playwright-related commands."*

---

## ✅ How to Run Tests

1. Install dependencies (if not already done):
   ```bash
   npm install
   npx playwright install

   ## fixtures
   Fixtures manage test lifecycle by providing isolated, reusable, auto-cleaned resources like browser, context, and page, improving test reliability and maintainability.
   Fixtures are Playwright’s way of managing test setup and teardown automatically, ensuring isolation and reusability.
