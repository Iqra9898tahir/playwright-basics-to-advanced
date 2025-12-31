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
