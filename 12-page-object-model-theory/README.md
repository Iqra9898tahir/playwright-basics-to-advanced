# Page Object Model (POM) – Theory & Interview Guide

## What is Page Object Model?
Page Object Model (POM) is a design pattern used in test automation where each page of the application is represented as a separate class or file.

The page object contains:
- Locators
- Page-specific actions

Tests interact with pages, not directly with locators.

---

## Why Use Page Object Model?
POM helps in:
- Reducing code duplication
- Improving maintainability
- Separating test logic from UI logic
- Making tests readable and scalable

---

## Problem Without POM
Without POM:
- Locators are scattered in tests
- UI changes break multiple tests
- Maintenance becomes difficult

---

## How POM Solves These Problems
- Locators live in one place
- UI changes require updates in only one file
- Tests become clean and readable

---

## POM Conceptual Structure
tests
├── login.spec.js
pages
├── login.page.js
├── dashboard.page.js
---

## What Goes Inside a Page Object?
A page object should contain:
- Locators
- Actions (methods)

It should NOT contain:
- Assertions
- Test logic

---

## Example (Conceptual)
```js
class LoginPage {
  constructor(page) {
    this.page = page;
    this.usernameInput = page.getByLabel('Username');
    this.passwordInput = page.getByLabel('Password');
    this.loginButton = page.getByRole('button', { name: 'Login' });
  }

  async login(username, password) {
    await this.usernameInput.fill(username);
    await this.passwordInput.fill(password);
    await this.loginButton.click();
  }
}


## How Tests Look With POM

test('user can login successfully', async ({ page }) => {
  const loginPage = new LoginPage(page);
  await loginPage.login('user', 'pass');
});

---

## Benefits of POM (INTERVIEW)
- Cleaner tests
- Easier maintenance
- Better reusability
- Scalable framework design

---

## Common Mistakes in POM
- Adding assertions inside page objects
- Creating very large page classes
- Mixing test logic with page logic

---

## Interview Questions & Answers

**Q: What is Page Object Model?**  
A: A design pattern that separates page logic from test logic.

**Q: Where should assertions go?**  
A: In test files, not in page objects.

**Q: Does POM reduce code?**  
A: It reduces duplication and improves maintainability.

---

## Key Takeaways
- POM is a design pattern, not a tool
- Tests should be readable
- Page objects encapsulate UI behavior
