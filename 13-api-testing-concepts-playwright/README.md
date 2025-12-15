# API Testing Concepts with Playwright

## What is API Testing?
API testing validates the backend logic of an application by testing endpoints directly without using the UI.

It ensures that:
- Business logic works correctly
- Data is returned accurately
- Errors are handled properly

---

## Why API Testing is Important
- Faster than UI tests
- More reliable
- Catches backend bugs early
- Reduces dependency on UI

---

## UI Testing vs API Testing
| UI Testing | API Testing |
|----------|------------|
| Slow | Fast |
| UI dependent | UI independent |
| More flaky | More stable |
| End-to-end validation | Business logic validation |

---

## Can Playwright Do API Testing?
Yes. Playwright provides built-in support for API testing using `APIRequestContext`.

This allows:
- Sending HTTP requests
- Validating responses
- Combining API + UI tests

---

## Common API Methods
- GET → Fetch data
- POST → Create data
- PUT → Update data
- DELETE → Remove data

---

## API Request Components
An API request consists of:
- URL
- Method
- Headers
- Body (for POST/PUT)
- Authentication (if required)

---

## API Response Components
An API response contains:
- Status code
- Response body
- Headers
- Response time

---
```js
## Common API Assertions (Conceptual)
expect(response.status()).toBe(200);
expect(responseBody.name).toBe('Iqra');
```
---

## Why Use Playwright for API Testing?
- Same tool for UI and API
- Shared test runner
- Shared configuration
- Easier integration testing

---

## Common Interview Questions & Answers

**Q: Why not test everything using UI?**  
A: UI tests are slow and flaky; API tests are faster and more reliable.

**Q: Can API tests replace UI tests?**  
A: No, both serve different purposes and should be combined.

**Q: What is APIRequestContext?**  
A: It is Playwright’s way to send HTTP requests for API testing.

---

## Common Mistakes
- Relying only on UI tests
- Not validating response data
- Ignoring status codes

---

## Key Takeaways
- API testing validates backend logic
- Playwright supports API testing
- Combine API + UI for strong automation
