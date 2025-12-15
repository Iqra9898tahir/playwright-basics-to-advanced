# Wait Strategies in Playwright

## What is a Wait?
A wait is a pause in test execution until a certain condition is met or time passes.

Waiting is needed because web applications are asynchronous.

---

## Playwright’s Philosophy on Waiting
Playwright is designed to avoid manual waiting as much as possible.

It provides:
- Auto-waiting actions
- Auto-waiting assertions

---

## Types of Waiting in Automation
1. Auto-Waiting (Recommended)
2. Explicit Waits (Rare cases)
3. Hard Waits (Not Recommended)
---

## 1️⃣ Auto-Waiting (BEST PRACTICE)
Playwright automatically waits for:
- Elements to appear in DOM
- Elements to be visible
- Elements to be actionable

This happens during:
- page actions (click, fill)
- assertions (expect)

No extra code is required.

---

## 2️⃣ Explicit Waits (Use Carefully)
Explicit waits are used when you must wait for a specific event.

Examples:
- Waiting for network response
- Waiting for navigation
- Waiting for API completion

```js
await page.waitForURL('/dashboard');
await page.waitForResponse(resp => resp.status() === 200);
```js
---

## 3️⃣ Hard Waits (AVOID)
Hard waits pause execution for a fixed time.
```
await page.waitForTimeout(5000);
```
---

## Why Hard Waits Are Bad
- Slow down tests
- Cause flaky behavior
- Do not validate conditions
- Fail in slow or fast environments

---

## Assertion vs Wait (IMPORTANT)
- Assertions validate conditions
- Waits only delay execution

Playwright assertions already include waiting logic.

---

## Common Interview Traps
- “Do you use Thread.sleep?” ❌
- “Do you add waits before every click?” ❌
- “Do you rely on time-based waits?” ❌

Correct answer:
> “Playwright handles waiting automatically through actions and assertions.”

---

## Best Practices
- Trust Playwright auto-waiting
- Use assertions instead of waits
- Use explicit waits only when required
- Avoid hard waits

---

## Interview Questions & Answers

**Q: How does Playwright handle waits?**  
A: Through built-in auto-waiting for actions and assertions.

**Q: When do you use explicit waits?**  
A: Only for specific events like navigation or API responses.

**Q: Why avoid hard waits?**  
A: They are unreliable and slow.

---

## Key Takeaways
- Auto-waiting is Playwright’s strength
- Explicit waits are rare
- Hard waits should be avoided
- Assertions are better than waits

