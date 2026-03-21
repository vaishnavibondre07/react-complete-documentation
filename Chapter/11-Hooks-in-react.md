# CHAPTER 11: HOOKS INTRODUCTION

## (Deep Foundation Chapter)

---

## 🔹 What Are Hooks?

Hooks are special functions introduced in React 16.8 that allow functional components to:

* Use state
* Use lifecycle features
* Access context
* Manage side effects
* Share logic between components

### 🔍 Simple Definition

> Hooks let functional components “hook into” React features.

---

## 🔹 Why Hooks Were Introduced?

### ❌ Problem 1: Class Components Were Complex

Classes required:

* constructor
* this keyword
* binding methods
* lifecycle methods
* verbose syntax

```jsx id="k3v8pz"
class Counter extends React.Component {
  constructor() {
    super();
    this.state = { count: 0 };
  }

  render() {
    return <h1>{this.state.count}</h1>;
  }
}
```

---

### ❌ Problem 2: Logic Reuse Was Hard

Used:

* Higher Order Components (HOC)
* Render Props

Problems:

* Deep nesting
* Wrapper hell

---

### ❌ Problem 3: Lifecycle Methods Were Confusing

* componentDidMount
* componentDidUpdate
* componentWillUnmount

👉 Logic scattered across methods

---

## 🔹 How Hooks Changed Everything

Hooks:

* Removed need for classes
* Made logic reusable
* Simplified lifecycle
* Improved readability
* Encouraged functional programming

👉 Modern React = Functional Components + Hooks

---

## 🔹 Rules of Hooks (CRITICAL)

### Rule 1: Only Call Hooks at Top Level

❌ Wrong:

```jsx id="g1p9tk"
if (condition) {
  useState(0);
}
```

✔ Correct:

```jsx id="8fj3dl"
const [count, setCount] = useState(0);
```

👉 React depends on hook order

---

### Rule 2: Only Call Hooks Inside React Functions

✔ Allowed:

* Functional components
* Custom hooks

❌ Not allowed:

* Normal JS functions
* Loops / conditions
* Class components

---

## 🔹 How Hooks Work Internally

```jsx id="2n8h0l"
const [count, setCount] = useState(0);
const [name, setName] = useState("");
```

👉 Internally stored as:

```
[0, ""]
```

👉 React tracks using order
👉 If order changes → wrong mapping

---

## 🔹 Hooks vs Lifecycle Mapping

| Class Lifecycle      | Hook Equivalent  |
| -------------------- | ---------------- |
| constructor          | useState         |
| componentDidMount    | useEffect([])    |
| componentDidUpdate   | useEffect([dep]) |
| componentWillUnmount | cleanup function |

👉 useEffect replaces lifecycle methods

---

## 🔹 Benefits of Hooks

✔ Cleaner code
✔ Smaller components
✔ Better separation of concerns
✔ Easy testing
✔ Reusable logic (custom hooks)
✔ Better performance

---

## 🧠 Mental Model

👉 Hooks = State + Side Effects + Shared Logic

👉 Think: **Functional Power Upgrade**

---

## 🔹 Real MERN Importance

Hooks used everywhere:

* useState → forms & UI
* useEffect → API calls
* useContext → authentication
* useReducer → complex state
* useRef → DOM access

👉 Without hooks → no modern React

---

## 🔹 SUMMARY

* Hooks enable state & lifecycle in functional components
* Replace class components
* Simplify logic reuse
* Follow 2 strict rules
* Hook order matters
* Core of modern React

---

## 🔹 Back to Home Button

```jsx id="y3zv8m"
import { Link } from "react-router-dom";

function BackHome() {
  return <Link to="/">⬅ Back to Home</Link>;
}
```

---

## 📝 QUESTIONS

1. Why were Hooks introduced in React?

2. What problems did class components create?

3. What are the two rules of Hooks?

4. Why must hooks be called at top level?

5. How does React track hooks internally?

6. Convert class counter → functional with hooks

7. Example of breaking hook order

8. Component with two useState

9. Create custom hook (useCounter)

10. How useEffect replaces lifecycle methods

[⬅ Back to Home](../README.md)
