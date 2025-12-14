# JavaScript Basics for Automation Testing

## What is JavaScript?
JavaScript is a programming language used to create dynamic and interactive behavior in web applications.
In automation testing, JavaScript is used to write test scripts that interact with web browsers.

---

## Why JavaScript for Automation?
- Playwright is built primarily for JavaScript/TypeScript
- Strong community support
- Modern automation tools use JavaScript
- Faster execution and better tooling

---

## JavaScript Execution Basics
- JavaScript is single-threaded
- Executes code line by line
- By default, JavaScript is synchronous

---

## Synchronous Execution
Synchronous means each line of code waits for the previous line to finish before executing.

Example:
```js
console.log("Step 1");
console.log("Step 2");

Arrow Functions

Arrow functions are a shorter syntax for writing functions in JavaScript.

Example:

const greetUser = (name) => {
  console.log("Hello " + name);
};

Why Playwright Uses Arrow Functions

Cleaner syntax

Better readability

Works well with async/await

Common in modern JavaScript frameworks

Functions in Playwright Tests

Playwright test structure uses arrow functions:

test('sample test', async ({ page }) => {
  await page.goto('https://example.com');
});

Interview Notes

Functions help reuse code

Arrow functions provide shorter syntax

Playwright tests commonly use arrow functions with async/await
