# Asynchronous JavaScript (async / await)

## What is Asynchronous Programming?
Asynchronous programming allows JavaScript to start a task and continue executing other code without waiting for the task to finish.

This is useful for time-consuming operations like page loading, API calls, and file handling.

---

## Why Asynchronous Programming is Needed?
JavaScript is single-threaded, meaning it can execute only one task at a time.
If JavaScript waited for slow operations synchronously, applications would freeze.

Asynchronous programming helps JavaScript stay responsive.

---

## Synchronous vs Asynchronous Execution

### Synchronous
- Code runs line by line
- Each task waits for the previous task to finish
- Can cause blocking

Example:
```js
console.log("Step 1");
console.log("Step 2");
```

### Asynchronous
- Long-running tasks start
- JavaScript continues execution
- Task result is handled later

Example:
```
startTask();
console.log("Next step");

Example:

loadPageAsync();
clickButton();
```
🔹 Async/Await Keywords
async

Marks a function as asynchronous

Allows use of await inside it

await

Pauses execution inside the async function

Waits until the asynchronous task completes
```
🔹 Simple Example
async function example() {
  await loadPage();
  console.log("Page loaded");
}
```

Here:

loadPage() takes time

await waits for it

Next line runs only after completion

🔹 Why Async/Await is Mandatory in Playwright

Playwright actions are asynchronous:

page.goto() waits for navigation

page.click() waits for element readiness

page.fill() waits for input action

API requests wait for server response

Without await, tests become flaky and unreliable.

Example:

await page.goto("https://example.com");
await page.click("#login");

🔹 Interview Tip

Q: Why do we use async/await in Playwright?
A: Because browser interactions and network operations are asynchronous, and async/await ensures proper execution order and stable test execution.


