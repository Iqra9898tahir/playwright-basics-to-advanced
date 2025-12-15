# Playwright Test Structure & Naming Conventions

## Why Test Structure Matters
Good test structure:
- Improves readability
- Makes debugging easier
- Helps teams collaborate
- Scales well in large projects

Poor structure leads to:
- Confusing tests
- Hard maintenance
- Duplicate logic

---
```js
## Recommended Folder Structure
tests
├── auth
│   └── login.spec.js
├── dashboard
│   └── dashboard.spec.js
├── settings
│   └── settings.spec.js
---
```js
## Test File Naming Convention
- Use `.spec.js` suffix
- Name files based on feature
- Avoid generic names

Good examples:
- login.spec.js
- checkout.spec.js

Bad examples:
- test1.js
- sample.js

---

## Test Description Naming (VERY IMPORTANT)
Test names should describe **user behavior**, not implementation.

```js
test('user can login with valid credentials', async ({ page }) => {
  // test steps
});
```js
---

## Bad Test Names (AVOID)
- "login test"
- "verify page"
- "test case 1"

These give no context.

---

## Good Test Names (INTERVIEW GOLD)
- user can logout successfully
- error message is shown for invalid password
- dashboard loads with correct user data

---

## Arrange–Act–Assert Pattern
A clean way to structure tests:

1. Arrange → setup
2. Act → perform action
3. Assert → validate result


```js
test('user sees error on invalid login', async ({ page }) => {
  // Arrange
  await page.goto('/login');

  // Act
  await page.fill('#username', 'wrong');
  await page.click('#submit');

  // Assert
  await expect(page.getByText('Invalid credentials')).toBeVisible();
});

```js


## One Assertion vs Multiple Assertions
- Prefer **focused assertions**
- Avoid validating too many things in one test
- One test = one scenario

---

## Avoid Hardcoding Test Data
- Use constants
- Use config files
- Use environment variables

---

## Common Interview Questions & Answers

**Q: How do you name your tests?**  
A: Based on user behavior and expected outcome.

**Q: How do you structure large test suites?**  
A: By feature/module folders.

**Q: Why is readability important in tests?**  
A: Tests act as documentation and are maintained long-term.

---

## Key Takeaways
- Structure tests by feature
- Use meaningful names
- Follow Arrange–Act–Assert
- Clean tests reflect strong automation skills
