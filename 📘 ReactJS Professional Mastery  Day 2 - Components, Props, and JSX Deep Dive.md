
---

# 🌟 Part 1: What are Components?

---

## 🚀 Definition:

- **Components** are the **building blocks** of a React application’s UI.
    
- Think of components like **custom HTML tags** — each with its own logic and appearance.
    
- **Small, reusable, independent** pieces that work together to build complex UIs.
    

---

## 🛠️ Two Main Types of Components:

|Functional Components|Class Components|
|---|---|
|Simple functions returning JSX|JavaScript ES6 Classes|
|Stateless (but now with Hooks can manage state)|Can manage state traditionally|
|Shorter, cleaner, easier|Verbose, more boilerplate|
|Introduced Hooks after React 16.8 making them powerful|Mostly used before Hooks|

---

## 🎯 Example 1 — Functional Component:

javascript

CopyEdit

`function Welcome() {   return <h1>Hello, React Learner!</h1>; }  export default Welcome;`

Usage:

javascript

CopyEdit

`import Welcome from './Welcome';  function App() {   return <Welcome />; }`

---

## 🎯 Example 2 — Class Component:

javascript

CopyEdit

`import React, { Component } from 'react';  class Welcome extends Component {   render() {     return <h1>Hello from Class Component!</h1>;   } }  export default Welcome;`

> 🔥 **Best Practice Today:** Always prefer **Functional Components + Hooks** unless specifically needed.

---

# 🌟 Part 2: Understanding JSX (JavaScript XML)

---

## 🚀 What is JSX?

- **JSX** = **JavaScript + XML**.
    
- Allows us to write **HTML-like syntax** inside JavaScript.
    
- JSX is **syntactic sugar** for `React.createElement` behind the scenes.
    

---

## 🎯 JSX Example:

javascript

CopyEdit

`const element = <h1>Welcome to React!</h1>;`

Behind the scenes, this is translated into:

javascript

CopyEdit

`const element = React.createElement('h1', null, 'Welcome to React!');`

---

## 🌟 JSX Syntax Rules

- JSX must have **one parent element**.
    
- Use **camelCase** for attributes (`className` instead of `class`).
    
- Dynamic values are inserted with **curly braces `{}`**.
    

Example:

javascript

CopyEdit

`const name = "Alex"; return <h2>Hello, {name.toUpperCase()}!</h2>;`

---

# 🌟 Part 3: Props (Passing Data between Components)

---

## 🚀 What are Props?

- **Props** = **Properties** passed to components, similar to HTML attributes.
    
- Allow **communication from parent ➔ child**.
    
- Props are **read-only** inside child components.
    

---

## 🎯 Basic Example of Props:

**Parent Component (App.js)**

javascript

CopyEdit

`import Greeting from './Greeting';  function App() {   return <Greeting name="John" age={25} />; }`

**Child Component (Greeting.js)**

javascript

CopyEdit

`function Greeting(props) {   return (     <div>       <h1>Hello, {props.name}!</h1>       <p>You are {props.age} years old.</p>     </div>   ); }`

---

## 🌟 Props Destructuring (Cleaner Code)

Instead of `props.name` and `props.age`, you can destructure:

javascript

CopyEdit

`function Greeting({ name, age }) {   return (     <div>       <h1>Hello, {name}!</h1>       <p>You are {age} years old.</p>     </div>   ); }`

---

# 🌟 Part 4: Fragments — Grouping without Extra Nodes

---

## 🚀 Why Use Fragments?

- JSX must return one root element.
    
- But we often want to group multiple elements **without extra div**s cluttering the DOM.
    

---

## 🎯 Example using Fragment:

javascript

CopyEdit

`function Info() {   return (     <>       <h1>React is Awesome!</h1>       <p>Let's learn it properly.</p>     </>   ); }`

or

javascript

CopyEdit

`import React from 'react';  function Info() {   return (     <React.Fragment>       <h1>React is Awesome!</h1>       <p>Let's learn it properly.</p>     </React.Fragment>   ); }`

> 🔥 Using Fragments keeps the DOM clean and avoids unnecessary nesting.

---

# 🌟 Part 5: React.StrictMode — Safety Net for Developers

---

## 🚀 What is React.StrictMode?

- Special component used to **highlight potential problems**.
    
- Only runs in **development mode**.
    
- Doesn’t affect production build.
    

Wrap your app inside `StrictMode` in `index.js`:

javascript

CopyEdit

`import React from 'react'; import ReactDOM from 'react-dom'; import App from './App';  ReactDOM.createRoot(document.getElementById('root')).render(   <React.StrictMode>     <App />   </React.StrictMode> );`

Strict Mode checks:

- Unsafe lifecycle methods
    
- Usage of deprecated APIs
    
- Unexpected side-effects
    

---

# 🌟 Part 6: Mini Hands-On Practice

---

✅ Create a **ProfileCard** component that accepts props:

- `name`
    
- `bio`
    
- `location`
    

✅ Display this information inside a simple card layout.

Example:

javascript

CopyEdit

`function ProfileCard({ name, bio, location }) {   return (     <div>       <h2>{name}</h2>       <p>{bio}</p>       <h4>{location}</h4>     </div>   ); }`

---

# 🌟 Part 7: Common Interview Questions from Day 2

---

✅ What are Components in React?  
✅ Difference between Functional and Class Components?  
✅ What are Props? Why are they immutable?  
✅ How does JSX work behind the scenes?  
✅ Why use Fragments in React?  
✅ What is React.StrictMode and why should you use it?

---

### Sample Interview Answer:

**Q:** _What are Props in React?_

> "Props (short for properties) are read-only attributes that allow data to be passed from a parent component to a child component. They help create dynamic and reusable components by customizing behavior or appearance based on the data provided."