# Playwright Locators – Complete Guide (0 to Hero)

## What is a Locator?
A locator is a way to identify and interact with an element on a web page.

Playwright uses locators to perform actions like:
- Click
- Fill
- Read text
- Validate visibility

---

## Why Locators Are Critical in Automation
- Locators are the backbone of UI automation
- Poor locators cause flaky tests
- Interviewers judge your experience based on locator choices

---

## Playwright Locator Strategy (MOST IMPORTANT)

Playwright recommends locating elements **the same way users interact with them**.

---

## Locator Preference Order (Interview GOLD)

1. **getByRole** ⭐⭐⭐⭐⭐ (BEST)
2. **getByLabel**
3. **getByPlaceholder**
4. **getByText**
5. **getByTestId**
6. **CSS / XPath** ❌ (LAST OPTION)

---

## 1️⃣ getByRole (BEST PRACTICE)
Uses accessibility roles (how screen readers see elements).

```js
await page.getByRole('button', { name: 'Login' }).click();
```
Why this is best:

Stable
User-centric
Accessible
Recommended by Playwright

2️⃣ getByLabel

Used for form inputs associated with labels.
```
await page.getByLabel('Username').fill('iqra');
```
Why good:
Clean
Stable
Easy to read

3️⃣ getByPlaceholder

Used when input has a placeholder.
```
await page.getByPlaceholder('Enter email').fill('test@email.com');
```
4️⃣ getByText

Finds elements based on visible text.
```
await page.getByText('Submit').click();
```

⚠️ Risk:

Text may change

Not ideal for dynamic UIs

5️⃣ getByTestId

Uses custom test attributes.
```
await page.getByTestId('login-button').click();
```

Used when:

No good role or label exists

App supports test IDs

6️⃣ CSS and XPath (LAST RESORT)
```
await page.locator('#loginBtn').click();
await page.locator("//button[@id='loginBtn']").click();
```
Why avoid:

Fragile

Tightly coupled to UI structure

Break easily

Chained Locators

Used to narrow down search scope.
```
await page.locator('form').getByRole('button', { name: 'Login' }).click();
```
Locator Auto-Waiting (Playwright Superpower)

Playwright automatically waits for:

Element to appear

Element to be visible

Element to be actionable

No manual waits needed.

Common Locator Mistakes (INTERVIEW)

Using XPath everywhere

Relying on index-based locators

Hardcoding dynamic text

Ignoring accessibility roles

Interview Questions & Answers

Q: Which locator is most preferred in Playwright?
A: getByRole because it aligns with accessibility and user behavior.

Q: When do you use getByTestId?
A: When user-facing locators are unavailable or unstable.

Q: Why avoid XPath?
A: It is brittle and tightly coupled to DOM structure.
