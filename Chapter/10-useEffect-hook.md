# CHAPTER 10: useEffect HOOK

## (Side Effects, Lifecycle & Real-World Data Flow)

---

## 🔹 What is useEffect?

React components have two phases:

* **Render phase** → React calculates UI
* **Commit phase** → React updates DOM

But real apps need more than UI rendering.

### Examples of Side Effects:

* Fetch data from backend
* Set up event listeners
* Start timers
* Update document title
* Subscribe to WebSocket

👉 These are called **Side Effects**

> A side effect is anything that affects something outside the component.

To handle this, React provides:
👉 **useEffect**

---

## 🔹 Basic Syntax

```jsx
import { useEffect } from "react";

useEffect(() => {
  // side effect
});
```

### Full Syntax

```jsx
useEffect(() => {
  // effect logic

  return () => {
    // cleanup logic
  };
}, [dependencies]);
```

---

## 🔹 Execution Flow

👉 **Render → DOM Update → useEffect runs**

---

## 🔹 Dependency Array (Most Important)

### 1. No Dependency Array

```jsx
useEffect(() => {
  console.log("Runs every render");
});
```

Runs:

* On mount
* On every update

⚠️ Can cause infinite loops

---

### 2. Empty Dependency Array []

```jsx
useEffect(() => {
  console.log("Runs once");
}, []);
```

Runs:

* Only on first render

Used for:

* API calls
* Initial setup

---

### 3. With Dependencies

```jsx
useEffect(() => {
  console.log("Runs when count changes");
}, [count]);
```

Runs:

* On mount
* When `count` changes

---

## 🔹 Real Example – API Call

```jsx
import { useState, useEffect } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

---

## 🔹 Infinite Loop Problem

```jsx
useEffect(() => {
  setCount(count + 1);
}, [count]);
```

⚠️ This causes infinite loop:

* Effect runs
* State updates
* Re-render
* Effect runs again

---

## 🔹 Cleanup Function

```jsx
useEffect(() => {
  const interval = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => {
    clearInterval(interval);
  };
}, []);
```

Runs:

* Before unmount
* Before next effect

👉 Prevents memory leaks

---

## 🔹 Lifecycle Understanding

### Mount

* Component loads
* Effect runs

### Update

* State/props change
* Effect runs if dependency changes

### Unmount

* Component removed
* Cleanup runs

---

## 🧠 Mental Model

👉 **R → D → C**

* Render
* Dependency
* Cleanup

---

## 🔹 Best Practices

✔ Always use dependency array
✔ Avoid unnecessary state updates
✔ Split multiple effects
✔ Don’t use async directly

### ❌ Wrong

```jsx
useEffect(async () => {});
```

### ✅ Correct

```jsx
useEffect(() => {
  async function fetchData() {}
  fetchData();
}, []);
```

---

## 🔹 Deep Concept

React uses **shallow comparison**

```jsx
useEffect(() => {}, [{}]);
```

⚠️ Runs every render (new object reference)

---

## 🔹 Real MERN Scenario

```jsx
useEffect(() => {
  fetch(`/api/products?category=${category}`)
    .then(res => res.json())
    .then(data => setProducts(data));
}, [category]);
```

---

## 🔹 SUMMARY

* useEffect handles side effects
* Runs after render
* Dependency controls execution
* Cleanup prevents memory leaks
* Wrong dependencies → infinite loops

---
## 📝 QUESTIONS

1. What is a side effect in React?
   
2. When does useEffect execute?
   
3. What happens without dependency array?
   
4. Why is cleanup important?
   
5. Why avoid async directly?
    
6. Update document title using useEffect
    
7. Build timer with cleanup
    
8. API fetch with dependency
    
9. Infinite loop example + fix
    
10. Dependency as object – what happens?

[⬅ Back to Home](../README.md)
