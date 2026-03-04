# CHAPTER 7: Conditional Rendering

---

## What is Conditional Rendering?

Conditional Rendering means:

Showing different UI based on a condition.

Just like in JavaScript:

```js
if (age > 18) {
  console.log("Adult");
}
```

In React:
We render different JSX based on conditions.

---

## Why It Is Important?

Real applications constantly change UI based on:

* User login status
* Data loading state
* Error messages
* Role-based access
* Theme toggle
* Button visibility

Without conditional rendering → UI would be static.

---

## Method 1: if/else Statement

Best for larger logic.

```jsx
function UserStatus({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome Back</h1>;
  } else {
    return <h1>Please Login</h1>;
  }
}
```

Here:

* If true → one UI
* If false → another UI

---

## Method 2: Ternary Operator (Most Common)

**Syntax:**

```js
condition ? trueValue : falseValue
```

Example:

```jsx
function UserStatus({ isLoggedIn }) {
  return (
    <h1>
      {isLoggedIn ? "Welcome Back" : "Please Login"}
    </h1>
  );
}
```

This is most commonly used in real projects.

---

## Method 3: Logical AND (&&)

Used when you want to render something only if condition is true.

```jsx
function Notification({ hasMessage }) {
  return (
    <div>
      {hasMessage && <p>You have new messages</p>}
    </div>
  );
}
```

If `hasMessage` is true → paragraph renders.

If false → nothing renders.

---

## Combining with State (Important)

```jsx
import { useState } from "react";

function Toggle() {
  const [isVisible, setIsVisible] = useState(false);

  return (
    <div>
      <button onClick={() => setIsVisible(!isVisible)}>
        Toggle
      </button>
      {isVisible && <h1>Hello World</h1>}
    </div>
  );
}
```

**Flow:**

Click → State changes → Condition changes → UI updates.

---

## Loading Example (Real MERN Example)

```jsx
import { useState } from "react";

function DataComponent() {
  const [loading, setLoading] = useState(true);

  return (
    <div>
      {loading ? <p>Loading...</p> : <p>Data Loaded</p>}
    </div>
  );
}
```

In real apps:

* While API call running → show spinner
* After data comes → show content

**Flow:**

State/Props → Condition Check → JSX Selected → Rendered

---

## Switch Statement Rendering

For multiple conditions:

```jsx
function Status({ role }) {
  switch (role) {
    case "admin":
      return <h1>Admin Panel</h1>;
    case "user":
      return <h1>User Dashboard</h1>;
    default:
      return <h1>Guest</h1>;
  }
}
```

Used in role-based UI (very important in MERN).

---

## Best Practice

✔ Use ternary for small conditions

✔ Use if/else for complex logic

✔ Use && for simple show/hide

✔ Avoid nested ternaries (hard to read)

Bad example:

```js
condition1 ? condition2 ? "A" : "B" : "C";
```

This becomes confusing.

---

# SUMMARY

* Used to show/hide UI
* Based on state or props
* Use if/else, ternary, &&
* Important for login, loading, roles
* Uses normal JavaScript inside JSX

---

# QUESTIONS

1. What is conditional rendering?
   
2. Name three ways to implement conditional rendering.
   
3. When should you use ternary vs if/else?
   
4. What happens when condition in && is false?
   
5. Why is nested ternary bad practice?
   
6. Create a login message component that shows:

   * "Welcome" if logged in
   * "Please Login" if not
     
7. Create a toggle component that shows/hides text.
   
8. Create a component that shows "Loading…" if loading is true.
   
9. Create role-based rendering using switch statement.
    
10. Create a component that conditionally renders a button only if user is admin.
<br>

[← Back to Home](../README.md)
