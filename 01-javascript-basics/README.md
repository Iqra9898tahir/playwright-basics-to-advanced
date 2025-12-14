# JavaScript Basics for Automation Testing

## What is it?
JavaScript is a programming language used to create dynamic and interactive behavior in web applications.  
In automation testing, JavaScript is used to write test scripts that control and interact with web browsers.

---

## Why do we need it?
Playwright automation is written using JavaScript/TypeScript.  
Understanding JavaScript is mandatory to:
- Write reliable test scripts
- Handle asynchronous browser actions
- Debug automation failures effectively

---

## How it works?
JavaScript has the following core characteristics:
- It is **single-threaded**
- Code is executed **line by line**
- By default, execution is **synchronous**

However, real-world operations like browser actions and API calls are handled asynchronously to avoid blocking execution.

---

## Simple Example

### Synchronous Execution
```js
console.log("Step 1");
console.log("Step 2");

```
Asynchronous Concept (Introduction)

Some operations take time, such as:

Page loading

Network requests (API calls)

File system operations

JavaScript uses asynchronous mechanisms so that long-running tasks do not freeze the program.

Detailed async concepts are covered in later sections.

Playwright Relevance

In Playwright:

Browser interactions are asynchronous

Page loads and element actions take time

Tests must wait correctly for actions to complete

Because of this, Playwright relies heavily on:

async

await

Without understanding JavaScript basics, Playwright scripts become unreliable.

Interview Questions (with Answers)
1. Is JavaScript synchronous or asynchronous?

Answer:
JavaScript is synchronous by default but supports asynchronous operations using callbacks, promises, and async/await.

2. Why is JavaScript called single-threaded?

Answer:
JavaScript executes code on a single main thread, meaning it processes one task at a time. Asynchronous operations are handled using the event loop.

3. Why is async/await important in Playwright?

Answer:
Browser actions take time. Async/await ensures Playwright waits for actions like page load, element visibility, and network responses before continuing execution.
