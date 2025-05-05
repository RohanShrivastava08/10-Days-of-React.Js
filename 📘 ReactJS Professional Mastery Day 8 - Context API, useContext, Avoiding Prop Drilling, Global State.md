
## 🌟 Part 1: What is Prop Drilling? Why is it Bad?

---

### 📦 Prop Drilling:

Passing props **through many layers** of components just to reach a deeply nested component.

**Problem:** Too many intermediary components passing data unnecessarily → messy, harder to maintain.

### ✅ Example:

jsx

CopyEdit

`<Parent>   <Child>     <GrandChild user={user} />   </Child> </Parent>`

👎 Inefficient → even if only `GrandChild` needs `user`.

---

## 🌟 Part 2: Enter React Context API 🚀

---

### 🎯 Use Case:

When **multiple components at different levels** need access to the same **global data** (e.g., user info, theme, auth status, language).

---

### ✅ Benefits:

- Eliminates prop drilling
    
- Provides global state access
    
- Works with functional components via `useContext`
    

---

## 🌟 Part 3: Steps to Use Context API

---

### 1️⃣ Create Context

jsx

CopyEdit

`import { createContext } from "react";  const UserContext = createContext();`

---

### 2️⃣ Create a Provider Component

jsx

CopyEdit

`function UserProvider({ children }) {   const user = { name: "Rohan", isLoggedIn: true };    return (     <UserContext.Provider value={user}>       {children}     </UserContext.Provider>   ); }`

---

### 3️⃣ Wrap App with Provider

jsx

CopyEdit

`<UserProvider>   <App /> </UserProvider>`

---

### 4️⃣ Access Context with `useContext`

jsx

CopyEdit

`import { useContext } from "react"; import { UserContext } from "./UserContext";  function Profile() {   const user = useContext(UserContext);   return <h1>Welcome {user.name}</h1>; }`

---

## 🌟 Part 4: Example – Theme Context Switcher 🎨

---

### ✅ ThemeContext.js

jsx

CopyEdit

`import { createContext, useState } from "react";  export const ThemeContext = createContext();  export function ThemeProvider({ children }) {   const [darkMode, setDarkMode] = useState(false);   const toggleTheme = () => setDarkMode(!darkMode);    return (     <ThemeContext.Provider value={{ darkMode, toggleTheme }}>       {children}     </ThemeContext.Provider>   ); }`

---

### ✅ App.js

jsx

CopyEdit

`<ThemeProvider>   <App /> </ThemeProvider>`

---

### ✅ Any Component:

jsx

CopyEdit

`const { darkMode, toggleTheme } = useContext(ThemeContext);  <button onClick={toggleTheme}>   Switch to {darkMode ? "Light" : "Dark"} Mode </button>`

---

## 🌟 Part 5: Nesting Multiple Contexts

---

You can combine multiple contexts:

jsx

CopyEdit

`<AuthProvider>   <ThemeProvider>     <LanguageProvider>       <App />     </LanguageProvider>   </ThemeProvider> </AuthProvider>`

Use in any component via:

jsx

CopyEdit

`const { user } = useContext(AuthContext); const { darkMode } = useContext(ThemeContext);`

---

## 🌟 Part 6: Custom Hook for Context (Best Practice)

---

jsx

CopyEdit

`// useAuth.js export const useAuth = () => useContext(AuthContext);`

Then use it like:

jsx

CopyEdit

`const { isLoggedIn } = useAuth();`

Cleaner and reusable!

---

## 🌟 Part 7: Interview Questions (Day 8)

---

✅ What is Context API and when should you use it?  
✅ Difference between `useContext` and `useState`?  
✅ How does Context API help avoid prop drilling?  
✅ How can you switch themes globally using Context?  
✅ Can you have multiple contexts in one app?

---

### Sample Answer:

**Q:** When would you avoid using Context API?

> For deeply nested state that changes frequently (like input values), it’s better to use `useState` or libraries like Redux or Zustand to avoid unnecessary re-renders.

---

## 🌟 Part 8: Mini Project Ideas

---

### ✅ 1. Theme Switcher

- Toggle dark/light mode across the app using Context
    

### ✅ 2. Auth Context

- Simulate login/logout and show user info conditionally
    

### ✅ 3. Language Context

- Toggle between EN / FR with `useContext`
    

---

## 🌟 Part 9: Hands-On Practice Tasks

---

✅ Create a context to manage user authentication  
✅ Build a theme toggler with a toggle button  
✅ Show/hide navbar items based on context login state  
✅ Combine multiple contexts in one app  
✅ Use `useContext` + `useEffect` to sync data

---

## 🌟 Part 10: Summary

---

- Context API provides **global state** to avoid **prop drilling**
    
- `createContext`, `Provider`, and `useContext` are the core parts
    
- It simplifies **state management** across large apps
    
- Can be combined with custom hooks
    
- Great for auth, theme, language, cart, and more