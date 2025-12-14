# Functions and Arrow Functions in JavaScript

## What is a Function?
A function is a reusable block of code designed to perform a specific task.
Functions help avoid code repetition and make programs easier to maintain.

---

## Why Functions are Important in Automation?
- Automation scripts repeat actions (click, fill, validate)
- Functions help reuse logic
- Playwright actions are function-based
- Page Object Model heavily uses functions

---

## Normal Function Example
```js
function greetUser(name) {
  console.log("Hello " + name);
}
```
Arrow Functions

Arrow functions are a shorter syntax for writing functions in JavaScript.

Example:
```
const greetUser = (name) => {
  console.log("Hello " + name);
};
```
Why Playwright Uses Arrow Functions

Cleaner syntax

Better readability

Works well with async/await

Common in modern JavaScript frameworks

Functions in Playwright Tests

Playwright test structure uses arrow functions:
```
test('sample test', async ({ page }) => {
  await page.goto('https://example.com');
});
```
Interview Notes

Functions help reuse code

Arrow functions provide shorter syntax

Playwright tests commonly use arrow functions with async/await
