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
