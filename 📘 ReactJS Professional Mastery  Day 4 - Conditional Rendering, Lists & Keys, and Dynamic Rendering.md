
## 🌟 Part 1: Conditional Rendering in React

---

### 🚀 What is it?

- The ability to **render different UI elements** based on **conditions** (like `if/else`, `true/false`, etc.).
    
- Achieved using **JavaScript logic inside JSX**.
    

---

### 🎯 Method 1: `if-else` Outside JSX

jsx

CopyEdit

`function Greeting({ isLoggedIn }) 
{   if (isLoggedIn)
{     return <h1>Welcome back!</h1>;   }   return <h1>Please sign in.</h1>; }`

---

### 🎯 Method 2: Ternary Operator

jsx

CopyEdit

`<p>{isLoggedIn ? "Logged In ✅" : "Guest ❌"}</p>`

---

### 🎯 Method 3: Logical AND (`&&`)

jsx

CopyEdit

`{showWelcome && <h1>Welcome to React!</h1>}`

> If `showWelcome` is `true`, the message renders.

---

### 🎯 Method 4: Using Variables to Store JSX

jsx

CopyEdit

`let message; if (isAdmin) {   message = <AdminDashboard />; } else {   message = <UserDashboard />; } return <div>{message}</div>;`

---

## 💡 Tip:

Never use traditional `if-else` _inside JSX_. Instead, use ternary or logical operators.

---

## 🌟 Part 2: Rendering Lists using `.map()`

---

### 🚀 What is List Rendering?

- You can **dynamically generate components** from arrays using `.map()`.
    

---

### 🎯 Basic Example:

jsx

CopyEdit

`const fruits = ["Apple", "Banana", "Cherry"];  function FruitList() {   return (     <ul>       {fruits.map((fruit, index) => (         <li key={index}>{fruit}</li>       ))}     </ul>   ); }`

---

## 🌟 Part 3: The Importance of `key` Prop

---

### 🔑 Why are `keys` important?

- Helps React **identify which items changed, added, or removed**.
    
- Speeds up rendering using **efficient diffing algorithm**.
    

---

### ✅ Good `key`: Unique, stable ID (like `user.id`)

jsx

CopyEdit

`users.map(user => <li key={user.id}>{user.name}</li>)`

### ❌ Bad `key`: Array index (can lead to UI bugs if list updates dynamically)

---

## 🌟 Part 4: Dynamic Rendering with Props + State + Lists

---

### 🎯 Example: User Card List

jsx

CopyEdit

`const users = [   { id: 1, name: "Rohan", role: "Developer" },   { id: 2, name: "Ayesha", role: "Designer" } ];  function UserCard({ name, role }) {   return (     <div>       <h3>{name}</h3>       <p>{role}</p>     </div>   ); }  function UserList() {   return (     <>       {users.map(user => (         <UserCard key={user.id} name={user.name} role={user.role} />       ))}     </>   ); }`

---

## 🌟 Part 5: Mini Project — Todo List App (Without Hooks)

---

jsx

CopyEdit

`const todos = ["Learn React", "Build a Project", "Crack Interviews"];  function TodoList() {   return (     <ul>       {todos.map((todo, i) => (         <li key={i}>{todo}</li>       ))}     </ul>   ); }`

> Tomorrow we’ll add **state** and **user input** to make it dynamic!

---

## 🌟 Part 6: Interview Questions from Day 4

---

✅ How does conditional rendering work in React?  
✅ What are the different ways to conditionally render content?  
✅ What is the purpose of the `key` prop in lists?  
✅ Why is using array index as a key considered bad?  
✅ How does React handle list diffing behind the scenes?

---

### Sample Answer:

**Q:** What is the role of `key` in list rendering?

> "The `key` prop helps React identify which elements have changed or been removed. It improves performance by enabling React to minimize DOM operations when re-rendering lists."