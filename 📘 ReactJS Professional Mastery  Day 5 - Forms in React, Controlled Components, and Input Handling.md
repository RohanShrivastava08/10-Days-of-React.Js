

## 🌟 Part 1: Introduction to Forms in React

---

### 🚀 Forms in HTML vs React:

- In plain HTML, forms manage their own state (uncontrolled).
    
- In React, we typically use **controlled components**, meaning:
    
    - Input fields derive their value from **state**
        
    - Every keystroke updates the state using `useState`
        

---

## 🌟 Part 2: Controlled vs Uncontrolled Components

---

### ✅ Controlled Components:

- The input field is **bound to component state**.
    
- React has **full control** over the form data.
    

jsx

CopyEdit

`const [name, setName] = useState(""); <input value={name} onChange={(e) => setName(e.target.value)} />`

---

### ❌ Uncontrolled Components:

- Uses a **ref** to get data after submission.
    
- Not recommended for modern React unless necessary.
    

jsx

CopyEdit

`const inputRef = useRef(); <input ref={inputRef} />`

---

## 🌟 Part 3: useState for Form Inputs

---

### 🎯 Example: Single Input

jsx

CopyEdit

`function NameForm() {   const [name, setName] = useState("");    return (     <form>       <input         type="text"         value={name}         onChange={(e) => setName(e.target.value)}       />       <p>Your name: {name}</p>     </form>   ); }`

---

### 🎯 Multiple Inputs (Best Practice):

jsx

CopyEdit

`function SignupForm() {   const [form, setForm] = useState({ email: "", password: "" });    function handleChange(e) {     const { name, value } = e.target;     setForm(prev => ({ ...prev, [name]: value }));   }    return (     <form>       <input name="email" value={form.email} onChange={handleChange} />       <input name="password" value={form.password} onChange={handleChange} />     </form>   ); }`

---

## 🌟 Part 4: Handling Form Submission

---

### 🎯 Preventing Default Behavior

jsx

CopyEdit

``function ContactForm() {   const [msg, setMsg] = useState("");    function handleSubmit(e) {     e.preventDefault(); // Prevents page reload     alert(`Message Sent: ${msg}`);   }    return (     <form onSubmit={handleSubmit}>       <textarea value={msg} onChange={(e) => setMsg(e.target.value)} />       <button type="submit">Send</button>     </form>   ); }``

---

## 🌟 Part 5: Input Types & Handling

---

- ✅ Text, Email, Password
    
- ✅ Textarea
    
- ✅ Radio Buttons
    
- ✅ Checkboxes
    
- ✅ Select Dropdown
    

---

### 🎯 Checkbox Handling

jsx

CopyEdit

`const [agree, setAgree] = useState(false); <input type="checkbox" checked={agree} onChange={() => setAgree(!agree)} />`

---

### 🎯 Select Dropdown Handling

jsx

CopyEdit

`const [fruit, setFruit] = useState("apple");  <select value={fruit} onChange={(e) => setFruit(e.target.value)}>   <option value="apple">Apple</option>   <option value="banana">Banana</option> </select>`

---

## 🌟 Part 6: Basic Form Validation (Optional)

---

### 🎯 Simple Required Field Check

jsx

CopyEdit

`function Login() {   const [email, setEmail] = useState("");    const handleSubmit = (e) => {     e.preventDefault();     if (!email) {       alert("Email is required!");     }   };    return (     <form onSubmit={handleSubmit}>       <input value={email} onChange={(e) => setEmail(e.target.value)} />       <button>Submit</button>     </form>   ); }`

---

## 🌟 Part 7: Mini Project — Signup Form

---

jsx

CopyEdit

`function SignupForm() {   const [form, setForm] = useState({ name: "", email: "", password: "" });    const handleChange = (e) => {     const { name, value } = e.target;     setForm((prev) => ({ ...prev, [name]: value }));   };    const handleSubmit = (e) => {     e.preventDefault();     console.log("Signup data:", form);   };    return (     <form onSubmit={handleSubmit}>       <input name="name" placeholder="Name" value={form.name} onChange={handleChange} />       <input name="email" placeholder="Email" value={form.email} onChange={handleChange} />       <input name="password" type="password" placeholder="Password" value={form.password} onChange={handleChange} />       <button>Sign Up</button>     </form>   ); }`

---

## 🌟 Part 8: Common Interview Questions

---

✅ What is a controlled component in React?  
✅ How do you manage form input fields in React?  
✅ What's the difference between controlled and uncontrolled inputs?  
✅ How do you handle multiple inputs with one handler?  
✅ How is form submission handled in React?

---

### Sample Answer:

**Q:** What are controlled components?

> A controlled component is a form element whose value is controlled by React through component state. Every change in the input updates the state, and the state determines what’s shown in the input.