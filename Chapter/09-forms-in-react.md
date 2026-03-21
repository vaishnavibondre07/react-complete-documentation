# CHAPTER 9: FORMS IN REACT

## (Controlled & Uncontrolled Components)

---

## 🔹 Why Forms Are Important?

Forms are used to collect user data like:

* Email
* Password
* Name
* Address
* Search queries

### 🆚 Traditional HTML vs React

| Traditional HTML          | React                   |
| ------------------------- | ----------------------- |
| Browser handles form data | React handles form data |
| Less control              | Full control            |
| Page reload               | SPA (no reload)         |

👉 React gives:

* Better validation
* Dynamic behavior
* Real-time updates

---

## 🔹 Controlled Components (Most Important Concept)

A **Controlled Component** is:

> A form element whose value is controlled by React state.

👉 **State = Single Source of Truth**

---

## 🔹 Example: Controlled Input

```jsx
import { useState } from "react";

function Login() {
  const [email, setEmail] = useState("");

  return (
    <input
      type="email"
      value={email}
      onChange={(e) => setEmail(e.target.value)}
    />
  );
}
```

### 🔍 Flow:

```
User types → onChange → State updates → Re-render → Input updates
```

---

## 🔹 Handling Multiple Inputs

```jsx
import { useState } from "react";

function Login() {
  const [formData, setFormData] = useState({
    email: "",
    password: ""
  });

  function handleChange(e) {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  }

  return (
    <>
      <input
        name="email"
        value={formData.email}
        onChange={handleChange}
      />

      <input
        name="password"
        type="password"
        value={formData.password}
        onChange={handleChange}
      />
    </>
  );
}
```

### ⭐ Key Concept:

```js
[e.target.name]
```

👉 Dynamically updates the correct field
👉 Industry-level pattern

---

## 🔹 Form Submission

```jsx
function handleSubmit(e) {
  e.preventDefault();
  console.log("Form Submitted");
}
```

```jsx
<form onSubmit={handleSubmit}>
  <button type="submit">Login</button>
</form>
```

### ❗ Why use `preventDefault()`?

* Prevents page reload
* Keeps SPA behavior

---

## 🔹 Uncontrolled Components

👉 DOM handles form state instead of React

### Example:

```jsx
import { useRef } from "react";

function Login() {
  const emailRef = useRef();

  function handleSubmit() {
    console.log(emailRef.current.value);
  }

  return (
    <>
      <input ref={emailRef} />
      <button onClick={handleSubmit}>Submit</button>
    </>
  );
}
```

### 🔍 Key Points:

* No state used
* Direct DOM access
* Less control

---

## 🔹 Controlled vs Uncontrolled

| Controlled           | Uncontrolled       |
| -------------------- | ------------------ |
| State controls value | DOM controls value |
| Uses `useState`      | Uses `useRef`      |
| More common          | Rarely used        |
| Easy validation      | Less control       |

👉 In real MERN apps:
**95% Controlled Components**

---

## 🔹 Real MERN Example (Register Form)

```jsx
import { useState } from "react";

function Register() {
  const [user, setUser] = useState({
    name: "",
    email: "",
    password: ""
  });

  function handleChange(e) {
    setUser({
      ...user,
      [e.target.name]: e.target.value
    });
  }

  function handleSubmit(e) {
    e.preventDefault();
    console.log(user);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input name="name" onChange={handleChange} />
      <input name="email" onChange={handleChange} />
      <input name="password" onChange={handleChange} />
      <button type="submit">Register</button>
    </form>
  );
}
```

---

## ❌ Common Mistakes

* Forgetting `value` attribute
* Forgetting `onChange`
* Mutating state directly
* Not using `preventDefault()`
* Not using spread operator

---

## 🧠 Deep Understanding

Controlled components:

* Give React full control
* Make validation easy
* Enable real-time updates
* Keep data consistent

👉 React becomes the **Single Source of Truth**

---

## 📌 SUMMARY

* Controlled components use **state**
* Uncontrolled components use **ref**
* Use `preventDefault()` for form submit
* Use spread operator for multiple inputs
* Controlled components = industry standard

---

## 📝 QUESTIONS

1. What is a controlled component?

2. Why is state called the "single source of truth" in forms?

3. What is the difference between controlled and uncontrolled components?

4. Why do we use e.preventDefault()?

5. Why do we use spread operator when updating form state?

6. Create a login form with email and password using controlled inputs.

7. Create a form that stores name, age, and city in a single state object.

8. Build a small search input that displays typed text below it.

9. Convert a controlled input into uncontrolled using useRef.

10. What will happen if you remove value from a controlled input?

[⬅ Back to Home](../README.md)


