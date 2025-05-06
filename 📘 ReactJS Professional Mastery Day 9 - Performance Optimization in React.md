
## 🌟 Part 1: Why Optimize Performance in React?

---

React apps can slow down when:

- Large re-renders occur unnecessarily
    
- Components re-render too often
    
- Expensive operations (loops, sorting) are not memoized
    
- Props and state updates trigger child re-renders
    

### ✅ Goal:

🚀 Minimize re-renders  
🧠 Memorize expensive computations  
🎯 Prevent unnecessary executions

---

## 🌟 Part 2: React `memo` — Prevent Unnecessary Component Renders

---

### 📌 What is it?

`memo` is a **higher-order component** that prevents re-rendering if **props haven't changed**.

### 🧪 Usage:

jsx

CopyEdit

`import React from "react";  const MyComponent = React.memo(function MyComponent({ title }) {   console.log("Rendering:", title);   return <h1>{title}</h1>; });`

### 🧠 Behind the scenes:

It shallowly compares the props → if unchanged, skips render.

---

## 🌟 Part 3: `useCallback` — Memoize Functions

---

Every time a parent renders, **inline functions** are re-created → causes child components to re-render.

### 🔄 Problem:

jsx

CopyEdit

`<Child onClick={() => doSomething()} />`

### ✅ Solution with `useCallback`:

jsx

CopyEdit

`const handleClick = useCallback(() => doSomething(), []); <Child onClick={handleClick} />`

> `useCallback` memoizes the function reference.

---

## 🌟 Part 4: `useMemo` — Memoize Expensive Calculations

---

Used to **cache computed values** so React doesn't re-calculate unless dependencies change.

### ⚡ Example:

jsx

CopyEdit

`const expensiveResult = useMemo(() => {   return computeHeavy(value); }, [value]);`

Only re-calculates when `value` changes.

---

## 🌟 Part 5: React DevTools for Performance

---

Install **React Developer Tools** extension:

- Highlights components that re-render
    
- Shows state/prop changes
    
- Shows memoization issues
    

---

## 🌟 Part 6: Avoiding Unnecessary Re-renders

---

✅ Keep component trees shallow  
✅ Break components into smaller ones  
✅ Lift state only when necessary  
✅ Use `key` props correctly  
✅ Don't pass new objects/arrays as props directly

---

## 🌟 Part 7: Example — Without vs With Memoization

---

### ❌ Without Optimization:

jsx

CopyEdit

`function App() {   const [count, setCount] = useState(0);   const user = { name: "Rohan" };    return <Child user={user} />; }`

- `Child` will always re-render because `user` is a new object each time.
    

---

### ✅ With Optimization:

jsx

CopyEdit

`const user = useMemo(() => ({ name: "Rohan" }), []);`

Now `user` is memoized and `Child` will only re-render if `user` changes.

---

## 🌟 Part 8: Throttling and Debouncing

---

Use when handling:

- Search input
    
- Scroll/resize events
    
- Button clicks
    

### 🔁 Throttling: Fires at intervals

### 🛑 Debouncing: Fires after pause

Use libraries like **lodash**:

js

CopyEdit

`const handleChange = debounce(() => { ... }, 300);`

---

## 🌟 Part 9: Lazy Loading Components

---

jsx

CopyEdit

`const About = React.lazy(() => import("./About"));  <Suspense fallback={<Spinner />}>   <About /> </Suspense>`

✅ Reduces initial bundle size  
✅ Improves perceived load time

---

## 🌟 Part 10: Code Splitting with Dynamic Imports

---

Split routes/components to load only when needed.

jsx

CopyEdit

`const Product = React.lazy(() => import("./Product"));`

---

## 🌟 Part 11: Interview Questions (Day 9)

---

✅ How does React optimize re-rendering?  
✅ What is the difference between `useMemo` and `useCallback`?  
✅ What does React.memo() do?  
✅ When should you NOT use memoization?  
✅ What is lazy loading in React?

---

### Sample Answer:

**Q:** Why use `useCallback` in React?

> To prevent unnecessary re-renders of child components that depend on function props, especially when the parent re-renders frequently.

---

## 🌟 Part 12: Mini Project Tasks (Performance Practice)

---

✅ Build a component with expensive calculation — optimize using `useMemo`  
✅ Memoize callback handlers in a form using `useCallback`  
✅ Lazy load routes using `React.lazy`  
✅ Split components using `React.Suspense`  
✅ Compare performance before and after using memoization

---

## 🌟 Part 13: Summary

---

- `React.memo()` avoids unnecessary component re-renders
    
- `useCallback()` memoizes function references
    
- `useMemo()` memoizes expensive calculations
    
- Lazy loading helps reduce initial bundle size
    
- Throttling/debouncing helps with performance in events