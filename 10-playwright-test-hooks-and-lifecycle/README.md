# Playwright Test Hooks & Test Lifecycle

## What are Test Hooks?
Test hooks are special functions that run before or after tests.

They are used to:
- Set up test data
- Initialize test state
- Clean up after tests

---

## Why Test Hooks Are Important
- Avoid code duplication
- Improve test readability
- Maintain clean test execution
- Essential for framework design

---
```
## Playwright Test Lifecycle
The order in which Playwright executes tests and hooks:

beforeAll  → runs once before all tests
beforeEach → runs before each test
test       → actual test execution
afterEach  → runs after each test
afterAll   → runs once after all tests
```
---
```
## beforeAll Hook
Runs once before all tests in a file.

Used for:
- Global setup
- Expensive operations
```
```
test.beforeAll(async () => {
  // setup logic
});

```
```
---

## beforeEach Hook
Runs before each test.

Used for:
- Navigating to pages
- Login setup
- Resetting state


```
```
test.beforeEach(async ({ page }) => {
  await page.goto('https://example.com');
});

```
```
---
```
## afterEach Hook
Runs after each test.

Used for:
- Cleanup
- Logging
- Screenshots on failure
```
test.afterEach(async () => {
  // cleanup logic
});
```
```
---

## afterAll Hook
Runs once after all tests.

Used for:
- Closing resources
- Final cleanup

```

---

## beforeEach vs beforeAll (INTERVIEW)
| Hook | Runs | Use Case |
|-----|-----|----------|
| beforeAll | Once | Heavy setup |
| beforeEach | Every test | Clean state |

---

## Common Use Cases
- Login in beforeEach
- Environment setup in beforeAll
- Cleanup in afterEach

---

## Common Mistakes
- Putting assertions in hooks
- Heavy logic in beforeEach
- Sharing state between tests

---

## Interview Questions & Answers

**Q: Where do you put login logic?**  
A: In beforeEach to ensure clean test state.

**Q: Can hooks access page object?**  
A: Yes, via test context.

**Q: Are hooks mandatory?**  
A: No, but recommended for clean framework design.

---

## Key Takeaways
- Hooks control test lifecycle
- Reduce duplication
- Improve maintainability
- Essential for scalable frameworks


