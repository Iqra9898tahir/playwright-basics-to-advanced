# JavaScript Promises

## What is a Promise?
A Promise is an object that represents the eventual completion or failure of an asynchronous operation.

In simple terms, a Promise is a placeholder for a value that will be available in the future.

---

## Why Promises Exist?
Promises help JavaScript handle asynchronous operations such as:
- API requests
- Page loading
- File operations

They prevent callback hell and make async code manageable.

---

## Promise States
A Promise can be in one of three states:

- **Pending** – Initial state, operation not completed
- **Fulfilled** – Operation completed successfully
- **Rejected** – Operation failed

---

## Simple Promise Example
```js
const myPromise = new Promise((resolve, reject) => {
  let success = true;

  if (success) {
    resolve("Operation successful");
  } else {
    reject("Operation failed");
  }
});
Consuming a Promise using .then() and .catch()
myPromise
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.log(error);
  });
async / await with Promise

async / await is a cleaner way to work with Promises.
async function runExample() {
  try {
    const result = await myPromise;
    console.log(result);
  } catch (error) {
    console.log(error);
  }
}
``` 
How Playwright Uses Promises

Every Playwright action returns a Promise.

Examples:
``` 
await page.goto("https://example.com");
await page.click("#login");
await page.fill("#username", "Iqra");
``` 

await ensures that each action completes before the next one starts.

Common Mistakes

Forgetting to use await

Not handling rejected Promises

Mixing .then() with async/await

Interview Notes

Promises represent future values

async/await is built on top of Promises

Playwright actions return Promises
