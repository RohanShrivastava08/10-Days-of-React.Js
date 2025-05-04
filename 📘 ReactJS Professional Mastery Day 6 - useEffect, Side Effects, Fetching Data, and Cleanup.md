
## 🌟 Part 1: What is a Side Effect?

---

### 🧠 Definition:

In React, a **side effect** is _any operation that affects something outside the component_, like:

- Fetching data
    
- Subscribing to events
    
- Updating the DOM manually
    
- Setting timers
    
- Logging
    
- Modifying external states
    

---

## 🌟 Part 2: Introducing the `useEffect` Hook

---

### 🔧 Syntax:

jsx

CopyEdit

`useEffect(() => {   // Side effect logic here }, [dependencies]);`

---

### ✅ Where it's used:

- API calls
    
- DOM event listeners
    
- Updating document titles
    
- Animations
    
- Cleanup logic (like unsubscribing)
    

---

## 🌟 Part 3: Basic `useEffect` Example

---

jsx

CopyEdit

``import { useState, useEffect } from "react";  function Hello() {   const [name, setName] = useState("Rohan");    useEffect(() => {     console.log(`Welcome ${name}!`);   }, [name]); // Runs when 'name' changes    return <input value={name} onChange={(e) => setName(e.target.value)} />; }``

---

## 🌟 Part 4: useEffect Dependency Array

---

### 🎯 Three behaviors:

1. **No Dependency Array** → runs **after every render**
    

jsx

CopyEdit

`useEffect(() => {   console.log("Runs every render"); });`

2. **Empty Dependency `[]`** → runs **once on mount**
    

jsx

CopyEdit

`useEffect(() => {   console.log("Runs once on mount"); }, []);`

3. **Specific Dependencies** → runs when dependencies **change**
    

jsx

CopyEdit

`useEffect(() => {   console.log("Runs when count changes"); }, [count]);`

---

## 🌟 Part 5: Fetching API Data with useEffect

---

### 🎯 Example using `fetch`:

jsx

CopyEdit

`function PostList() {   const [posts, setPosts] = useState([]);    useEffect(() => {     fetch("https://jsonplaceholder.typicode.com/posts")       .then((res) => res.json())       .then((data) => setPosts(data.slice(0, 5))); // First 5 posts   }, []);    return (     <ul>       {posts.map((post) => <li key={post.id}>{post.title}</li>)}     </ul>   ); }`

---

### 🛠 Best Practice: Handle Loading/Error States

jsx

CopyEdit

`useEffect(() => {   async function loadPosts() {     try {       const res = await fetch(url);       const data = await res.json();       setPosts(data);     } catch (error) {       console.error("Error loading posts:", error);     }   }   loadPosts(); }, []);`

---

## 🌟 Part 6: Cleanup in useEffect

---

### 🔄 Why Cleanup?

To **avoid memory leaks**, especially with:

- Event listeners
    
- Subscriptions
    
- Timers
    

---

### 🎯 Example: `setInterval` Cleanup

jsx

CopyEdit

`useEffect(() => {   const interval = setInterval(() => {     console.log("Tick");   }, 1000);    return () => clearInterval(interval); // cleanup }, []);`

---

### 🎯 Example: Cleanup for Event Listeners

jsx

CopyEdit

`useEffect(() => {   function handleResize() {     console.log("Resized!");   }    window.addEventListener("resize", handleResize);    return () => {     window.removeEventListener("resize", handleResize);   }; }, []);`

---

## 🌟 Part 7: Common Interview Questions (Day 6)

---

✅ What is the purpose of `useEffect` in React?  
✅ How does the dependency array in `useEffect` work?  
✅ What happens if you forget the cleanup function?  
✅ How would you fetch API data in a React component?  
✅ Can you have multiple `useEffect` hooks in one component?

---

### Sample Answer:

**Q:** Why do we need a cleanup function in `useEffect`?

> To prevent memory leaks. For example, if you start an interval or subscribe to an event, React needs to clean it up when the component unmounts. Otherwise, it will run even after the component is gone.

---

## 🌟 Part 8: Mini Project — Weather App (Basic)

---

### 🎯 Fetch Weather by City (pseudo code)

jsx

CopyEdit

``const [weather, setWeather] = useState(null); const [city, setCity] = useState("Delhi");  useEffect(() => {   fetch(`https://api.weatherapi.com/v1/current.json?key=KEY&q=${city}`)     .then(res => res.json())     .then(data => setWeather(data)); }, [city]);``

> Add a text input to change city and show weather details dynamically.

---

## 🌟 Part 9: Hands-On Practice Tasks

---

✅ Fetch and display a list of users from an API  
✅ Build a timer component with `setInterval` and cleanup  
✅ Add event listener for window resize, and remove on unmount  
✅ Practice changing document title dynamically  
✅ Create a simple API-driven product list

---

## 🌟 Part 10: Summary

---

- `useEffect` runs side effects in functional components
    
- Dependency array controls when effect runs
    
- Cleanup avoids memory leaks
    
- It’s essential for **fetching data, syncing states, and handling async logic**