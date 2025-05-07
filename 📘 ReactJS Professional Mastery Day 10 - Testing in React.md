
## 🌟 Part 1: Why Testing Matters

---

### ✅ Benefits:

- Prevent bugs before shipping
- Make refactoring safe
- Ensure component behavior stays consistent
- Improve confidence in codebase

---

## 🌟 Part 2: Types of Tests in React

---

|Type|Focus|Tools|
|---|---|---|
|✅ Unit Test|Tests single functions/components|`Jest`, `RTL`|
|✅ Integration Test|Tests multiple units together|`React Testing Library`|
|✅ E2E Test|Tests full app flow|`Cypress`, `Playwright`|

---

## 🌟 Part 3: React Testing Tools Overview

---

### 🔧 Jest

- JavaScript testing framework by Meta
- Works with React out of the box
- Snapshot testing support

### 🔧 React Testing Library (RTL)

- Focuses on **testing components as users use them**
- Encourages best practices (no testing implementation details)

---

## 🌟 Part 4: Installing Jest + RTL

---

```bash
bash
CopyEdit
npm install --save-dev jest @testing-library/react @testing-library/jest-dom

```

👉 Add to `package.json`:

```json
json
CopyEdit
"scripts": {
  "test": "jest"
}

```

---

## 🌟 Part 5: Writing Your First Unit Test

---

### 🧪 Component: `Greeting.js`

```jsx
jsx
CopyEdit
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

```

### 🧪 Test: `Greeting.test.js`

```jsx
jsx
CopyEdit
import { render, screen } from "@testing-library/react";
import Greeting from "./Greeting";

test("renders the greeting with name", () => {
  render(<Greeting name="Rohan" />);
  const text = screen.getByText("Hello, Rohan!");
  expect(text).toBeInTheDocument();
});

```

---

## 🌟 Part 6: Simulating Events

---

### 🧪 `Button.js`

```jsx
jsx
CopyEdit
export default function Button({ onClick }) {
  return <button onClick={onClick}>Click Me</button>;
}

```

### 🧪 `Button.test.js`

```jsx
jsx
CopyEdit
import { render, fireEvent } from "@testing-library/react";
import Button from "./Button";

test("calls onClick handler", () => {
  const mockClick = jest.fn();
  const { getByText } = render(<Button onClick={mockClick} />);
  fireEvent.click(getByText("Click Me"));
  expect(mockClick).toHaveBeenCalledTimes(1);
});

```

---

## 🌟 Part 7: Test Selectors: Best Practices

---

✅ Prefer `getByRole`, `getByText`, `getByPlaceholderText`

❌ Avoid `getByTestId` unless necessary

```jsx
jsx
CopyEdit
getByRole("button", { name: /submit/i })

```

---

## 🌟 Part 8: Snapshot Testing

---

```jsx
jsx
CopyEdit
import { render } from "@testing-library/react";
import renderer from "react-test-renderer";
import Greeting from "./Greeting";

test("matches snapshot", () => {
  const tree = renderer.create(<Greeting name="Rohan" />).toJSON();
  expect(tree).toMatchSnapshot();
});

```

📌 Creates a JSON representation of the component → easy regression testing

---

## 🌟 Part 9: Mocking API Calls

---

```jsx
jsx
CopyEdit
global.fetch = jest.fn(() =>
  Promise.resolve({
    json: () => Promise.resolve({ message: "Hello" }),
  })
);

```

Useful for testing components that use `useEffect` + `fetch`.

---

## 🌟 Part 10: Coverage Report

---

Run this to get code coverage:

```bash
bash
CopyEdit
npm test -- --coverage

```

✅ See which parts of your app are tested

✅ Aim for **80–100% coverage**

---

## 🌟 Part 11: Interview Questions (Day 10)

---

✅ Why use `React Testing Library` over `Enzyme`?

✅ How do you simulate a button click in tests?

✅ What's the difference between unit and integration testing?

✅ What does snapshot testing do?

✅ How do you mock fetch API in tests?

---

### Sample Answer:

**Q:** Why prefer React Testing Library?

> Because it tests components the way users interact with them — not the implementation — leading to more robust, maintainable tests.

---

## 🌟 Part 12: Practice Tasks

---

✅ Write unit test for a simple login form

✅ Simulate form input and submission

✅ Write integration test for login + redirect

✅ Mock API data and render response

✅ Add snapshot test for a UI component

---

## 🌟 Part 13: Tools to Explore Further

---

✅ `Cypress` – E2E browser automation

✅ `Playwright` – Fast E2E framework by Microsoft

✅ `msw` – Mock Service Worker for realistic API mocks

✅ `Vitest` – Lightning-fast test runner (especially with Vite)

---

## 🌟 Part 14: Summary

---

- Testing ensures code stability, maintainability, and confidence
- RTL + Jest are gold standards for React unit/integration testing
- Write user-focused tests (simulate real usage)
- Mock APIs for deterministic behavior
- Use `coverage` to improve test quality