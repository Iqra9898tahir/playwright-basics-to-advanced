# 📘 Automation Terminal Errors – Playwright Real-World Guide

This README is a **personal automation handbook** for understanding **generic terminal errors**, why they occur, and how **Playwright Trace** helps identify the real root cause.

---

## 🧠 Core Principle (MOST IMPORTANT)

> **Terminal errors tell WHAT failed**  
> **Trace tells WHY it failed**

Never change locators, add waits, or refactor tests **before checking trace**.

---

## 🧪 Tools Context

- Automation Tool: **Playwright**
- Scope: **UI / End-to-End Automation**
- Environment: Local & CI
- Debugging Tools:
  - Terminal logs
  - Trace Viewer
  - HTML Report
  - Screenshots

---

## 1️⃣ Timeout Exceeded

### Terminal Error
Timeout 30000ms exceeded while waiting for locator


### What terminal tells
- Action waited too long

### Real-world reasons
- Element never rendered
- API failed
- Wrong page
- Loader/overlay blocking UI

### Trace reveals
- DOM snapshot
- Network failures
- Pending loaders

---

## 2️⃣ Element Not Found

### Terminal
Error: locator('#submit') not found


### Possible causes
- Wrong page
- Conditional rendering
- Element appears later
- Shadow DOM

### Trace helps
- Check if element ever existed
- Verify page state

---

## 3️⃣ Element Not Visible

### Terminal
Element is not visible


### Real reasons
- display: none
- Element off-screen
- Covered by modal/loader
- Animation not finished

### Trace shows
- CSS visibility
- Overlapping elements

---

## 4️⃣ Element Detached From DOM

### Terminal
ElementHandle is detached from DOM


### Why it happens
- React/Vue re-render
- DOM replaced after action

### Trace shows
- DOM refresh timing

---

## 5️⃣ Navigation Timeout

### Terminal
page.goto: Navigation timeout exceeded

### Possible reasons
- Backend slow
- Redirect loop
- Environment down

### Trace shows
- Network requests
- Redirect chain

---

## 6️⃣ Strict Mode Violation

### Terminal
Strict mode violation: locator resolved to multiple elements


### Meaning
- Locator too generic

### Trace helps
- Shows all matched elements
- Helps refine locator strategy

---

## 7️⃣ Target Page / Context Closed

### Terminal
Target page, context or browser has been closed

### Real causes
- App crash
- Unexpected redirect
- Test ended early

### Trace shows
- When page closed
- Console errors

---

## 8️⃣ Execution Context Destroyed

### Terminal
Execution context was destroyed

### Happens when
- Page navigates during interaction
- SPA route change

### Trace shows
- Navigation timing issue

---

## 9️⃣ Assertion Failed

### Terminal
Expected string to contain "Success"
Received ""


### What terminal lacks
- Why text empty?
- Element hidden?
- API delay?

### Trace reveals
- UI state at assertion time

---

## 🔟 Network Request Failed

### Terminal
net::ERR_FAILED

### Possible causes
- Backend issue
- CORS
- Test environment unstable

### Trace gives
- Request/response status
- Failed API endpoints

---

## 1️⃣1️⃣ Child Window / Popup Not Found

### Terminal
waiting for event "page" timed out

### Real reasons
- Click didn’t open new tab
- Wrong locator
- Popup blocked

### Trace shows
- Click action execution
- Whether new page opened

---

## 1️⃣2️⃣ Flaky Tests (CI Only Failures)

### Terminal
Timeout exceeded (fails only in CI)

### Almost always due to
- Timing issues
- Slow network
- Test data dependency

### Trace is mandatory
- CI behavior replay
- Root cause identification

---

## 🔍 How Professionals Debug Failures

1. Read terminal error → identify failed step
2. Open trace → go to failed action
3. Inspect previous step DOM
4. Check network & console
5. Decide:
   - Test issue?
   - App bug?
   - Environment issue?

---

## 🚦 Trace Best Practices

### Recommended configuration
```js
use: {
  trace: 'retain-on-failure'
}
