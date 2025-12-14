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

### Asynchronous
- Long-running tasks start
- JavaScript continues execution
- Task result is handled later

Example:

startTask();
console.log("Next step");

What is async?

async is a keyword used before a function to indicate that the function will perform asynchronous operations.

An async function always returns a Promise.

Example:

async function runTest() {
  console.log("Test started");
}

What is await?

await is used inside an async function.
It pauses execution until the asynchronous operation completes.

Example:

await loadPage();

Simple async/await Example
async function example() {
  console.log("Start");
  await waitForAction();
  console.log("End");
}


Execution order:

Start

waitForAction completes

End

Why async/await is Mandatory in Playwright

All Playwright actions are asynchronous:

Page navigation

Element interactions

Waiting for elements

API requests

Using async/await ensures:

Correct execution order

Stable tests

Reduced flakiness

Example:

test('login test', async ({ page }) => {
  await page.goto('https://example.com');
  await page.click('#login');
});

Common Mistakes

Forgetting to use await

Calling async functions without waiting

Mixing synchronous and asynchronous logic incorrectly

Interview Notes

JavaScript is single-threaded but supports async operations

async/await simplifies promise-based code

Playwright relies heavily on async/await for browser interactions
