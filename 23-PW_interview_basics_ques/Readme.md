1️⃣ What is Playwright and why do you use it?

Perfect Answer:

“Playwright is a modern automation framework by Microsoft. I use it because it supports multiple browsers, handles auto-waits, works with iframes, new tabs, file uploads, and provides fast, reliable tests with built-in tracing and debugging.”

2️⃣ Difference between Playwright and Selenium?

Perfect Answer:

“Selenium is WebDriver-based and slower, while Playwright works at browser-level, so it's faster and more stable. Playwright supports auto-wait, multi-tab, file download/upload, network mocking, and built-in parallel execution. Selenium needs external drivers and extra libraries.”

3️⃣ How do you handle dynamic dropdowns?

Perfect Answer:

“I never rely on index because it changes. I type in the input, wait for the dropdown options to appear, then select the option by visible text. This makes the test stable even if the order changes.”

4️⃣ How do you handle tables?

Perfect Answer:

“I locate all rows, loop through them, find the matching cell value, and then perform actions like Edit/Delete inside the same row. I use row-column logic to interact with dynamic table data.”

5️⃣ Have you used Page Object Model (POM)?

Perfect Answer:

“Yes. I keep locators and reusable functions in page classes and keep test logic in spec files. This makes the code cleaner, maintainable, and changes can be done in one place.”

6️⃣ How do you handle alerts in Playwright?

Perfect Answer:

“Playwright uses dialog event listeners. I wait for the dialog event, read the message, and accept or dismiss. It’s more stable because no switchTo() is required like Selenium.”

7️⃣ How do you handle file upload?

Perfect Answer:

“For HTML file inputs, I use setInputFiles. For OS-level dialogs, I wait for the fileChooser event then attach the file. Playwright handles both easily, unlike Selenium which struggles with system dialogs.”

8️⃣ How do you handle file downloads?

Perfect Answer:

“I wait for the download event using page.waitForEvent('download'), trigger the download, get the suggested filename, and save the file. This is built-in in Playwright.”

9️⃣ How do you handle new tabs or windows?

Perfect Answer:

“I use context.waitForEvent('page') to capture the new tab, then use that page object to interact. No need to switch window handles like Selenium.”

1️⃣0️⃣ What are auto-waits in Playwright?

Perfect Answer:

“Playwright automatically waits for elements to be visible, stable, and ready before interacting. This removes the need for manual sleeps, reduces flakiness, and improves test reliability.”

1️⃣1️⃣ What is test fixture in Playwright?

Perfect Answer:

“Fixtures provide reusable setup like login, test data, or environment configuration. They run before/after tests and help avoid repeating the same setup logic.”

1️⃣2️⃣ What is storageState? (LOGIN REUSE)

Perfect Answer:

“storageState stores cookies and localStorage after a login. I use it to avoid logging in again and again. It makes tests much faster.”

1️⃣3️⃣ How do you handle network mocking in Playwright?

Perfect Answer:

“I intercept API calls using route(), mock responses, delay APIs, or simulate errors. This helps test frontend behavior without depending on backend.”

1️⃣4️⃣ What is trace-viewer?

Perfect Answer:

“Playwright records execution (steps, DOM snapshots, network, screenshots). If a test fails, I open trace-viewer to replay the test and find what went wrong.”

1️⃣5️⃣ How do you ensure test stability?

Perfect Answer:

“I use auto-waits, proper locators (not fragile XPaths), avoid sleeps, use explicit waits only when needed, and interact with visible/attached elements.”

1️⃣6️⃣ How do you handle waits in Playwright?

Perfect Answer:

“I avoid manual waits and rely on auto-wait. But when needed, I use locators like toBeVisible, toHaveText, toBeEnabled, etc.”

1️⃣7️⃣ Tell me the difference between HTML modal and browser alert.

Perfect Answer:

“Browser alerts are JavaScript dialogs and block the UI. HTML modals are just div elements. Playwright handles HTML modals using normal locators and JS alerts using dialog event.”

1️⃣8️⃣ How do you select dropdown (static)?

Perfect Answer:

“I use page.selectOption for standard HTML select tags.”

1️⃣9️⃣ How do you handle environment variables?

Perfect Answer:

“I use config files, .env files, or global setup in Playwright to manage environment-specific URLs, credentials, and test data.”

2️⃣0️⃣ What is the biggest challenge you solved in automation?

Perfect Answer:

“Dynamic elements — especially dynamic dropdowns and tables. I solved it using stable locators, text-based selection, proper waits, and encapsulating the logic in reusable POM functions.”
1️⃣ Scenario: Login is required for every test. How will you optimize your test execution?
Perfect Answer:

“Instead of logging in again and again, I generate a login state once using storageState, save cookies/localStorage, and reuse it for all tests. This reduces execution time and makes tests stable.”

2️⃣ Scenario: A page loads slow, and your test fails because the element is not yet available. What do you do?
Perfect Answer:

“I avoid manual waits. Instead, I rely on Playwright auto-wait or add explicit expectations like toBeVisible() or toHaveText(). This ensures test waits for the correct state instead of using fixed sleeps.”

3️⃣ Scenario: You have a table with hundreds of rows. You need to click Edit on a specific user.
Perfect Answer:

“I locate all rows, loop through them, match the name cell, and perform the action inside the same row. This is dynamic and works even if the row position changes.”

4️⃣ Scenario: Dynamic dropdown where values appear based on typing.
Perfect Answer:

“I type into the input, wait for dropdown options to appear, and click based on visible text — never index. This avoids flakiness when the order changes.”

5️⃣ Scenario: Test cases fail randomly on CI but work fine locally.
Perfect Answer:

“I check for unstable locators, missing waits, network delays, animation timing, or environment differences. I add strict locators, proper waits, retry logic, and check network mocking if backend is unstable.”

6️⃣ Scenario: You need to test file upload and download.
Perfect Answer:

“For upload, I use setInputFiles for HTML input or fileChooser event for OS popups. For downloads, I use page.waitForEvent('download') to capture and verify the file name.”

7️⃣ Scenario: There is a popup (modal) that blocks the page after clicking a button.
Perfect Answer:

“If it’s HTML modal, I treat it as normal DOM element and wait for it to be visible. If it's JS alert, I use Playwright dialog event to accept/dismiss.”

8️⃣ Scenario: After clicking a link, a new tab opens. How do you handle it?
Perfect Answer:

“I use context.waitForEvent('page') to capture the new tab, then interact with that tab while still keeping access to the original page.”

9️⃣ Scenario: You need to verify an API response before UI interaction.
Perfect Answer:

“I use Playwright’s request fixture to send API calls, validate the response, then continue UI actions. This ensures backend is stable before UI testing.”

1️⃣0️⃣ Scenario: You need to search for a product in an e-commerce app and validate the price.
Perfect Answer:

“I type the product name, wait for filtered results, loop through product cards, match product name, and extract the price from the same card/container.”

1️⃣1️⃣ Scenario: A test requires random data (email, username).
Perfect Answer:

“I generate dynamic test data using libraries like faker or custom functions. This prevents conflicts and testing with duplicate data.”

1️⃣2️⃣ Scenario: You must run tests in parallel but they overwrite each other’s data.
Perfect Answer:

“I ensure tests are independent — separate test users, isolated data, and no shared state. I use worker-based fixtures to avoid collisions.”

1️⃣3️⃣ Scenario: You must automate complex mouse actions (drag-drop, hover, right-click).
Perfect Answer:

“I use Playwright’s built-in mouse and keyboard APIs. They support dragTo, hover, and modifiers like Ctrl or Shift for complex interactions.”

1️⃣4️⃣ Scenario: A UI element has dynamic ID that changes every refresh.
Perfect Answer:

“I never use dynamic IDs. Instead, I use stable locators such as getByRole, text(), placeholder, or parent-child relationship.”

1️⃣5️⃣ Scenario: Page has infinite scroll. How do you test it?
Perfect Answer:

“I use page.evaluate to scroll to the bottom repeatedly until all items load or a target item appears. Then I interact with the item.”

1️⃣6️⃣ Scenario: Need to mock an API to test frontend without backend.
Perfect Answer:

“I intercept the API using route(), mock JSON response, and test how UI behaves under various backend conditions like success, error, or delay.”

1️⃣7️⃣ Scenario: Validate error messages when API returns 500.
Perfect Answer:

“I mock the API with route() and force it to return a 500 status. Then I verify that frontend shows the correct error message.”

1️⃣8️⃣ Scenario: Need to screenshot, record video, trace test steps.
Perfect Answer:

“Playwright provides trace viewer, screenshots, and video recording built-in. I enable these in playwright.config for debugging failures.”

1️⃣9️⃣ Scenario: A button is disabled until form is valid.
Perfect Answer:

“I fill required fields, then assert that the button becomes enabled using toBeEnabled(). This validates validation rules.”

2️⃣0️⃣ Scenario: You need to run Playwright in CI (GitHub Actions, Jenkins).
Perfect Answer:

“I install browsers using npx playwright install, run tests headless, set up env variables, and upload trace/videos as pipeline artifacts for debugging.”
