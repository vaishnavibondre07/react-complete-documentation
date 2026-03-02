# CHAPTER 5: STATE

---

## What is State?

State is a built-in React object that stores data that can change over time.

In simple words:

State is data that controls how a component behaves and renders.

---

## Why State is Needed?

Without state, your UI is static.

### Example:

```jsx```

```

function Counter() {

  return <h1>0</h1>;
}

```
No matter what happens → it always shows 0.

But real apps need:

  - Counter increase

  - Show/hide elements

  - Toggle themes

  - Update forms

  - Display API data

That requires *State*.

---

# Introducing useState (First Hook)

React provides a Hook called:

*👉 useState*

This allows functional components to store and update state.

---

# Basic Syntax of useState

```
import { useState } from "react";

const [state, setState] = useState(initialValue);
```

Explanation:

  - state → current value

  - setState → function to update value

  - initialValue → starting value

---

# Basic Counter Example

```
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>
        Increase
      </button>
    </div>
  );
}
```

## Understanding This Example Deeply

Step by step:

 1. useState(0) → initial value is 0

 2. count stores current value

 3. setCount updates value

 4. When button clicked → setCount(count + 1)

 5. React re-renders component

 6. UI updates automatically

That re-render happens because state changed.

---

## How State Triggers Re-render

Flow: User Click → setState → State Changes → Component Re-renders → UI Updates

---

# Important Rule: Never Update State Directly

❌ Wrong:

`` count = count + 1; ``

This will NOT re-render component.

✅ Correct:

`` setCount(count + 1); ``

Because React tracks updates only through the setter function.

---

# Multiple State Variables

You can have multiple states:

```
const [name, setName] = useState("");

const [age, setAge] = useState(0);
```
Each state is independent.

---

# Functional Update (Very Important)

Sometimes you must use previous value safely.

Correct way: 

`` setCount(prevCount => prevCount + 1);``

Why?

Because state updates are asynchronous.

If you do:

```
setCount(count + 1);

setCount(count + 1);
```

It might not increase twice.

Using functional update guarantees correct result.

---

Updating Objects in State

❌ Wrong:

``` 
const [user, setUser] = useState({ name: "Alice", age: 20 });

user.age = 21;

```


✅ Correct:

`` setUser({ ...user, age: 21 });``


We use the spread operator to copy previous state.

Because React state must be immutable.

---

# Updating Arrays in State

Example:

```
const [items, setItems] = useState([]);

setItems([...items, "New Item"]);
```

Never use:

``` items.push("New Item"); ❌```


Because push() mutates the original array.

React needs a new reference to detect change.

---

# State vs Props (Deep Understanding)

```
     Props	                    State

Comes from parent	     Managed inside component

    Read-only	              Can be updated

   External data	           Internal data

```
Props → Input
State → Internal memory

---

# Real MERN Example

Login Form

```
function Login() {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  return (
    <div>
      <input
        value={email}
        onChange={(e) => setEmail(e.target.value)}
      />
      <input
        type="password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
      />
    </div>
  );
}
```

Here:

  - State stores input values

  - UI reflects state

  - React controls input

This is called:

*👉 Controlled Component* 

---

# Deep Concept: Why State Causes Re-render?

When state changes, React:

  - Creates new Virtual DOM

  - Compares with old Virtual DOM

  - Updates only changed parts

That’s why UI updates automatically.

---

# SUMMARY

- State stores dynamic data

- useState is used to create state

- Never update state directly

- State updates cause re-render

- Objects & arrays must be updated immutably

---

# QUESTIONS

1. What is state in React?

2. What is the difference between props and state?

3. Why should state not be updated directly?

4. What happens when state changes?

5. What is immutability in React?

6. Create a counter using useState.
   
7. Create a toggle button (Show/Hide text).
   
8. Create a component that stores an object in state and updates one property.
   
9. Create a component that stores an array in state and adds items to it.
    
10. Why might this not work correctly?
    ```
     setCount(count + 1);
     setCount(count + 1);
    ```
    Explain and fix it.


[⬅ Back to Home](../README.md)


---
