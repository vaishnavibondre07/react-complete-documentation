# CHAPTER 13: CONTEXT API

---

## 🔹 What Problem Does Context API Solve?

In React, data flows from parent → child using props.

This works for small apps, but in large apps it creates a problem:

👉 **Props Drilling**

---

## 🔹 Props Drilling Explained

```
App
 └── Layout
      └── Sidebar
           └── Menu
                └── Profile
```

If `Profile` needs data:

* App → Layout

* Layout → Sidebar

* Sidebar → Menu

* Menu → Profile

❌ Even components that don’t need data still pass it

### Problems:

* Tight coupling
  
* Hard to maintain

* Unnecessary re-renders

* Difficult debugging

---

## 🔹 What is Context API?

👉 Context API allows sharing data globally without passing props manually.

> It creates a **global data layer** in React.

---

## 🔹 Core Concepts

* `createContext()`
* Provider
* Consumer (old)
* `useContext`
* Multiple contexts

---

## 🔹 Step-by-Step Implementation

### 1. Create Context

```jsx id="a9d2k3"
import { createContext } from "react";

export const AuthContext = createContext();
```

---

### 2. Provider

```jsx id="b2k9s1"
<AuthContext.Provider value={{ user: "John" }}>
  <App />
</AuthContext.Provider>
```

👉 `value` is important

👉 When value changes → re-render

---

### 3. Consume Context

```jsx id="c7m2d1"
import { useContext } from "react";
import { AuthContext } from "./AuthContext";

function Dashboard() {
  const auth = useContext(AuthContext);
  return <h1>{auth.user}</h1>;
}
```

---

## 🔹 Internal Working

React stores:

* Provider value reference
  
* List of subscribed components

When value changes:

* React compares reference
  
* If changed → all consumers re-render

---

## 🔹 Performance Issue (Important)

```jsx id="d8k1p2"
<AuthContext.Provider value={{ user }}>
```

❌ New object every render → re-render

---

## 🔹 Optimization

```jsx id="e1m9d4"
const value = useMemo(() => ({ user }), [user]);

<AuthContext.Provider value={value}>
```

✔ Prevents unnecessary re-renders

---

## 🔹 Multiple Contexts

```jsx id="f7k3d2"
<AuthProvider>
  <ThemeProvider>
    <App />
  </ThemeProvider>
</AuthProvider>
```

---

## 🔹 Context + useReducer (Advanced)

```jsx id="g2d9k1"
const AuthContext = createContext();

function authReducer(state, action) {
  switch (action.type) {
    case "LOGIN":
      return { user: action.payload };
    case "LOGOUT":
      return { user: null };
    default:
      return state;
  }
}
```

```jsx id="h8k2d3"
function AuthProvider({ children }) {
  const [state, dispatch] = useReducer(authReducer, { user: null });

  return (
    <AuthContext.Provider value={{ state, dispatch }}>
      {children}
    </AuthContext.Provider>
  );
}
```

---

## 🔹 Folder Structure (Best Practice)

```
src/
├── context/
│   ├── AuthContext.js
│   ├── ThemeContext.js
│   └── index.js
├── components/
├── pages/
```

---

## 🔹 Real Example: Theme Toggle

```jsx id="i2k9d3"
const ThemeContext = createContext();
```

```jsx id="j3k8d1"
function ThemeProvider({ children }) {
  const [theme, setTheme] = useState("light");

  function toggleTheme() {
    setTheme(prev => prev === "light" ? "dark" : "light");
  }

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}
```

```jsx id="k4d2m1"
function Header() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <div className={theme}>
      <button onClick={toggleTheme}>Toggle</button>
    </div>
  );
}
```

---

## 🔹 Real MERN Example: Auth Context

Stores:

* user
* token
* login()
* logout()

```jsx 
function login(userData) {
  dispatch({ type: "LOGIN", payload: userData });
  localStorage.setItem("token", userData.token);
}
```

---

## 🔹 When NOT to Use Context

❌ Frequently changing data

❌ Large dynamic lists

❌ Performance-critical state

👉 Use Redux / Zustand instead

---

## 🔹 SUMMARY

* Context solves props drilling
* Provider gives global data
* Consumers subscribe to updates
* Reference change triggers re-render
* Combine with useReducer for scalability
* Use memoization for performance

---

## 📝 QUESTIONS

1. What is props drilling?

2. How does Context trigger re-render?

3. Why object reference causes re-render?

4. When should Context be avoided?

5. Why combine Context with useReducer?

6. Build ThemeContext

7. Create AuthContext

8. Optimize with useMemo

9. Use multiple contexts

10. Role-based UI using context

[⬅ Back to Home](../README.md)
