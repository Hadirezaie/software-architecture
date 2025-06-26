# Testing Types

- Unit Testing
- Integration Testing
- System Testing
  - Functional Testing
  - Performance Testing
- Usability Testing
- Acceptance Testing
- Regression Testing

Sure! Here's a concise and clear definition for each testing type, including how and when to use them:

---

### **Unit Testing**

- **Definition:** Tests individual components or functions (e.g. a method or class) in isolation.
- **How/When to Use:**

  - Use during development.
  - Ideal for testing logic-heavy components.
  - Tools: JUnit (Java), pytest (Python), etc.

---

### **Integration Testing**

- **Definition:** Tests how multiple units/components work together (e.g. service + database).
- **How/When to Use:**

  - After unit testing.
  - Useful for detecting interface/communication issues.
  - Tools: Spring Boot Test, Postman (for API), etc.

---

### **System Testing**

- **Definition:** Tests the entire application as a whole to ensure it meets requirements.
- **How/When to Use:**

  - After integration testing.
  - Covers end-to-end scenarios.

#### **Functional Testing**

- **Definition:** Verifies that each feature works according to functional requirements.
- **Use:** For validating user-facing features (e.g. login, search).

#### **Performance Testing**

- **Definition:** Checks how the system performs under load, stress, or high concurrency.
- **Use:** To ensure scalability and speed.

  - Tools: JMeter, Gatling.

---

### **Usability Testing**

- **Definition:** Evaluates the app's user experience, interface, and ease of use.
- **How/When to Use:**

  - During UI/UX design and beta testing.
  - Involves real users or usability experts.

---

### **Acceptance Testing**

- **Definition:** Confirms that the system meets business requirements and is ready for release.
- **How/When to Use:**

  - Done at the end of development, often by the client or QA.
  - Includes **User Acceptance Testing (UAT)**.

---

### **Regression Testing**

- **Definition:** Ensures that new code changes haven’t broken existing functionality.
- **How/When to Use:**

  - After bug fixes, feature additions, or code refactoring.
  - Often automated in CI/CD pipelines.

---

### **Test-Driven Development (TDD):**

**Definition:**
A development approach where you **write the tests first**, then write the **minimum code** needed to pass those tests, and finally **refactor** the code if needed.

---

### Typical TDD Cycle (Red → Green → Refactor):

1. **Red:** Write a failing test (because the functionality doesn’t exist yet).
2. **Green:** Write just enough code to make the test pass.
3. **Refactor:** Clean up the code while keeping the tests green.

---

### Why Write Tests Before Code?

- Helps you **clearly define requirements and behavior**.
- Leads to **simpler, more focused code**.
- Encourages writing **testable** and **modular** code.
- Gives you **immediate feedback** if something breaks.

---

### When Not to Use It?

- In early prototyping (where requirements change rapidly).
- When you're doing exploratory or UI-heavy development with unclear specs.

---

### Summary:

> **Yes, writing tests before code is a valid and powerful approach, especially in TDD.** It improves code quality, maintainability, and developer confidence.

### **Test Coverage** – Explained Simply

**Test Coverage** is a **measure** of how much of your code is **executed (covered)** when your test suite runs.

---

### What It Tells You:

- How much of your **code is being tested**.
- Which parts of the code are **not tested** at all.
- Helps identify **uncovered logic**, potential bugs, or **dead code**.

---

### Common Types of Test Coverage:

1. **Line Coverage:**
   What percentage of **lines of code** are executed by tests?

2. **Branch Coverage:**
   Are all **if/else conditions** or decision branches tested?

3. **Function/Method Coverage:**
   Are all functions or methods in the codebase being tested?

4. **Path Coverage:**
   Are all possible execution **paths** through a program tested?

---

### Example:

If your app has 100 lines of code and your tests execute 80 of them, your **line coverage** is **80%**.

---

### Tools for Measuring Coverage:

- **Java:** JaCoCo, Cobertura
- **Python:** Coverage.py
- **JavaScript:** Istanbul (nyc)
- **.NET:** Coverlet

---

### Important Note:

> **High test coverage ≠ good tests.**
> You can have 100% coverage with poor-quality tests that don’t catch bugs.

---

### Best Practice:

Use test coverage as a **tool to guide testing**, not as the only quality metric. Aim for **meaningful tests**, not just numbers.

---

Great question! Understanding **Fast Tests** vs **Slow Tests** helps you design better, more efficient test suites — especially in CI/CD environments.

---

## **Fast Tests**

### What Are They?

Tests that run **quickly**, often in **milliseconds or seconds**.

### Characteristics:

- Do **not** rely on external systems (DBs, APIs, etc.)
- Run **in-memory**
- Are usually **Unit Tests**
- Very reliable and easy to debug

### Examples:

- Testing a `MathUtils.add(a, b)` method
- Verifying logic like string manipulation or validation

### Typical Time:

**< 1 second per test**

### Use them:

- Frequently during development
- In every commit (CI/CD)
- For **core logic**, helpers, business rules

---

## **Slow Tests**

### What Are They?

Tests that take **more time** to run due to reliance on **external resources** or complex setups.

### Characteristics:

- Interact with real databases, APIs, filesystems, browsers, etc.
- May be **Integration**, **System**, or **UI** tests
- Slower and more brittle than fast tests

### Examples:

- Testing a REST API with a real HTTP call
- Checking how a web app behaves in a browser using Selenium
- Verifying file upload to cloud storage

### Typical Time:

**Several seconds to minutes per test**

### Use them:

- Before releases
- In nightly test suites
- For **real-world behavior** validation

---

## Best Practice:

> "Run fast tests often, run slow tests wisely."

- Keep **most tests fast**.
- Isolate slow tests and maybe tag them (`@SlowTest`) so you can run them conditionally.
- Automate both types — just with different schedules.

---

## BeforeEach

## AfterEach

## BeforeAll

## AfterAll

## Arrange-Act-Assert (AAA) Pattern

- Set up test resources with a @BeforeEach method.
- Execute test method
- Verify expected outcomes using assertions

DELETE FROM sold_sim_queue where iccid in('8993017100289380492','8993017100279311036');
