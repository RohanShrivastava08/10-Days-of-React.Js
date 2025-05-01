

---

# 🌟 Part 1: What is State in React?

---

## 🚀 Definition:

- **State** is a **built-in object** that stores **dynamic data** and allows a component to respond to user actions or internal events.
    
- Unlike props, **state is local** to the component.
    
- When **state changes**, the component **re-renders** automatically.
    

---

## 🧠 Props vs State

|Props|State|
|---|---|
|Passed from parent to child|Managed inside the component|
|Immutable (read-only)|Mutable using setState/useState|
|Static data|Dynamic/interactive data|

---

# 🌟 Part 2: useState Hook (React 16.8+)

---

## 🚀 What is a Hook?

- Hooks are **special functions** that let you **“hook into” React features** like state or lifecycle in functional components.
    

---

## 🎯 Syntax of useState:

javascript

CopyEdit

`const [stateVariable, setStateFunction] = useState(initialValue);`

### 🔄 How it works:

- `useState()` returns an **array with two elements**:
    
    - Current state value
        
    - Function to update it
        

---

## 🎯 Basic Counter Example:

javascript

CopyEdit

`import React, { useState } from 'react';  function Counter() {   const [count, setCount] = useState(0); // Initial value is 0    return (     <div>       <h1>{count}</h1>       <button onClick={() => setCount(count + 1)}>Increment</button>     </div>   ); }`

> 🔥 Updating state **automatically triggers re-render** of that component.

---

# 🌟 Part 3: Event Handling in React

---

## 🚀 React Event System:

- Uses **synthetic events** (cross-browser wrappers).
    
- Uses **camelCase** syntax: `onClick`, `onChange`, `onSubmit`, etc.
    

---

## 🎯 Button Click Example:

javascript

CopyEdit

`function Greet() {   const sayHello = () => alert("Hello!");   return <button onClick={sayHello}>Say Hello</button>; }`

---

## 🎯 Input Event Example (Controlled Component):

javascript

CopyEdit

`function NameInput() {   const [name, setName] = useState("");    return (     <div>       <input         type="text"         value={name}         onChange={(e) => setName(e.target.value)}       />       <p>Your name is: {name}</p>     </div>   ); }`

> 🔥 Controlled components keep UI in sync with state.

---

# 🌟 Part 4: Updating State — Key Rules

---

## 🔐 React State Rules:

1. **Do NOT mutate state directly** (e.g., `count++ ❌`).
    
2. Use `setState()` or `setX()` returned by `useState`.
    
3. React may **batch updates** — don’t depend on immediate value.
    

---

## 🎯 Functional Update Example:

javascript

CopyEdit

`setCount(prevCount => prevCount + 1);`

Why? Safer when state update depends on previous state.

---

# 🌟 Part 5: Mini Project — Counter App (With Reset)

---

javascript

CopyEdit

`function CounterApp() {   const [count, setCount] = useState(0);    return (     <div>       <h1>Count: {count}</h1>       <button onClick={() => setCount(prev => prev + 1)}>+</button>       <button onClick={() => setCount(prev => prev - 1)}>-</button>       <button onClick={() => setCount(0)}>Reset</button>     </div>   ); }`

---

# 🌟 Part 6: Common Interview Questions

---

✅ What is the difference between props and state?  
✅ What does the `useState` hook do?  
✅ Can you update state directly? Why not?  
✅ What are synthetic events in React?  
✅ Explain controlled vs uncontrolled components.  
✅ What happens when state changes in a component?

---

### Sample Answer:

**Q:** What is useState in React?

> `useState` is a Hook that allows you to manage local state in functional components. It returns a state variable and a setter function. Updating the state causes the component to re-render with the new data.