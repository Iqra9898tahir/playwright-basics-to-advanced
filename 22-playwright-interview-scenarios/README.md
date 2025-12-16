
## 1. Locator Strategy in a Large Application

### Scenario
You are automating a large e-commerce application.
The UI changes frequently and tests break often.

### Solution
- Prefer `data-test-id` attributes
- Avoid XPath and deeply nested CSS selectors
- Use role-based locators (`getByRole`)
- Define a locator priority strategy for the team

### Why This Works
- Locators remain stable despite UI changes
- Tests become easier to maintain
- Reduces flaky failures

---

## 2. Parallel Execution Failures in CI

### Scenario
Tests pass locally but fail randomly in CI when executed in parallel.

### Debugging Approach
- Check for shared state across tests
- Ensure each test uses its own browser context
- Reduce workers temporarily to isolate failures
- Use Playwright traces and videos

### Real-World Insight
Most CI flakiness is caused by poor test isolation, not Playwright itself.

---

## 3. Authentication Handling in Enterprise Applications

### Scenario
Login involves MFA and takes significant time.
Logging in before every test slows execution.

### Best Practice
- Perform login once
- Save authenticated storage state
- Reuse it across tests
- Avoid repeated UI logins

### Benefit
- Faster test execution
- More stable tests
- Reduced dependency on external systems

---

## 4. Backend API Instability Affecting UI Tests

### Scenario
UI tests fail because backend APIs are unreliable.

### Strategy
- Mock API responses where possible
- Intercept network requests
- Validate UI behavior independently

### Key Principle
UI tests should validate UI behavior, not backend reliability.

--
# Playwright – Real-Time UI Validation (Spoken Interview Answers)

This document contains **spoken-style interview answers** based on
real Playwright automation experience in production applications.

The focus is on **how I think and approach problems**, not just tools.

---

## 1. How do you validate a mandatory input field?

### Interview Answer (Spoken)
> First, I check whether the field is visible and enabled.
> Then I try submitting the form without entering any value to trigger validation.
> I validate the error message text and its position near the field.
> After that, I enter invalid data and again verify the error behavior.
> Finally, I enter valid data and ensure the error message disappears.
> This way I validate both negative and positive behavior.

---

## 2. How do you validate form-level error messages?

### Interview Answer (Spoken)
> I never validate error messages in isolation.
> I trigger the validation by performing the actual user action, usually form submit.
> Then I verify the error message text, visibility, and that it disappears once the user corrects the input.
> Validation is complete only when error behavior changes correctly with user actions.

---

## 3. How do you find and validate data in a large table?

### Interview Answer (Spoken)
> In real applications, tables are dynamic, so I never rely on row index.
> I first identify the table container, then iterate through rows and locate the row
> based on unique business data like username or order ID.
> Once I find the correct row, I validate related columns inside that row only.
> This approach keeps tests stable even if sorting or pagination changes.

---

## 4. How do you perform actions on a specific table row?

### Interview Answer (Spoken)
> I locate the row using a unique value and scope all actions within that row.
> For example, if I want to click Edit or Delete, I ensure the action happens only
> inside the matched row.
> This avoids accidental operations on the wrong data, which is critical in real systems.

---

## 5. How do you handle tables with pagination?

### Interview Answer (Spoken)
> First, I try to find the data on the current page.
> If it’s not present, I navigate through pages until the record is found.
> I never assume the data is on page one.
> Pagination validation is about data integrity, not just UI navigation.

---

## 6. How do you validate searchable or filterable tables?

### Interview Answer (Spoken)
> I apply the filter or search condition as a user would.
> Then I validate that every visible row matches the search criteria.
> I don’t just check one row — I verify consistency across all displayed results.
> This ensures the filtering logic is working correctly.

---

## 7. How do you validate dynamic dropdowns (API-driven)?

### Interview Answer (Spoken)
> I type into the dropdown to trigger API results.
> I wait for options to appear instead of using static waits.
> Then I select the matching option and validate that the selected value
> is correctly reflected in the UI.
> This mimics real user behavior and avoids flaky timing issues.

---

## 8. How do you validate toast or notification messages?

### Interview Answer (Spoken)
> After triggering the action, I immediately validate the toast message text.
> I also check that it disappears after the expected time.
> Since toasts are temporary, timing and stability are important here.

---

## 9. How do you handle confirmation modals?

### Interview Answer (Spoken)
> I validate that the modal appears with correct title and message.
> Then I test both Cancel and Confirm paths.
> Finally, I validate the expected outcome after the modal action.
> This ensures the user decision flow works correctly.

---

## 10. How do you validate an end-to-end business flow?

### Interview Answer (Spoken)
> I validate every important step, not just the final result.
> For example, if I create a user, I validate success message,
> then verify the user appears in the table,
> and finally validate deletion removes it.
> End-to-end tests should validate business behavior, not just clicks.

---

## How I Avoid Flaky Tests (Interview Favorite)

### Spoken Answer
> I rely on Playwright’s auto-waiting and assertions.
> I avoid hard waits completely.
> I design stable locators and ensure proper test isolation.
> Most flakiness comes from poor synchronization, not tool issues.

---

## Key Interview Takeaways

- Always validate **behavior**, not just UI presence
- Tables should be validated using **data-driven logic**
- Avoid index-based or static assumptions
- Speak in **problem → approach → reasoning** format

---

## Final Interview Tip

> Interviewers don’t test your syntax.
> They test how you think when automation meets real applications.

