# 📘 CHAPTER 12: COMMONLY USED HOOKS

## (Core Production Hooks)

---

## 🔵 useRef — Persistent Mutable Reference

### 🔹 What is useRef?

useRef is a React Hook that returns a mutable object:

```js 
const refObject = useRef(initialValue);
```

👉 Structure:

```js id="7s2mfd"
{ current: initialValue }
```

  ✔ Same object persists across re-renders
  
  ✔ Updating `.current` does NOT trigger re-render

---

### 🔹 Why use useRef?

1. Access DOM directly
2. Store values without re-render

---

### 🔹 Example: DOM Access

```jsx id="a1k8dl"
import { useRef } from "react";

function InputFocus() {
  const inputRef = useRef(null);

  function handleFocus() {
    inputRef.current.focus();
  }

  return (
    <>
      <input ref={inputRef} />
      <button onClick={handleFocus}>Focus Input</button>
    </>
  );
}
```

---

### 🔹 Persisting Values

```jsx id="k2d9sj"
function RenderTracker() {
  const renderCount = useRef(0);

  renderCount.current++;

  return <h2>Render Count: {renderCount.current}</h2>;
}
```

---

### 🔹 useRef vs useState

| Feature    | useState | useRef |
| ---------- | -------- | ------ |
| Re-render  | Yes      | No     |
| Mutable    | No       | Yes    |
| UI state   | Yes      | No     |
| DOM access | No       | Yes    |

---

### 🔹 When NOT to Use useRef

❌ Replace state

❌ Store UI data

❌ Break React flow

---

## 🟣 useContext — Global Data Access

### 🔹 What is useContext?

Allows components to access global data without props drilling.

---

### 🔹 Props Drilling Problem

App → Layout → Sidebar → Menu → Profile

👉 Data passed unnecessarily through layers

---

### 🔹 Example

```jsx id="m9s2jd"
const AuthContext = React.createContext();
```

```jsx id="9v2jks"
<AuthContext.Provider value={{ user: "John" }}>
  <Dashboard />
</AuthContext.Provider>
```

```jsx id="p4k3dl"
const auth = useContext(AuthContext);
```

---

### 🔹 Key Concept

✔ Components subscribe to context

✔ Value change → re-render

---

## 🟡 useMemo — Performance Optimization

### 🔹 What is useMemo?

Memoizes computed values:

```jsx id="d8sk21"
const value = useMemo(() => compute(), [deps]);
```

---

### 🔹 Example

```jsx id="z9d3ls"
function Calculator({ number }) {
  const squared = useMemo(() => {
    return number * number;
  }, [number]);

  return <h1>{squared}</h1>;
}
```

---

### 🔹 When to Use

✔ Expensive calculations

✔ Performance issues

---

### ⚠️ Warning

❌ Don’t overuse
👉 Has memory + comparison cost

---

## 🟠 useCallback — Stable Functions

### 🔹 What is useCallback?

Memoizes function reference:

```jsx id="f2k8sl"
const fn = useCallback(() => {}, [deps]);
```

---

### 🔹 Problem Without It

Every render → new function → child re-renders

---

### 🔹 Example

```jsx id="g7s1kd"
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

---

### 🔹 useMemo vs useCallback

| useMemo        | useCallback      |
| -------------- | ---------------- |
| Value          | Function         |
| Returns result | Returns function |

---

## 🔴 useReducer — Complex State

### 🔹 What is useReducer?

```jsx id="t8k2sl"
const [state, dispatch] = useReducer(reducer, initialState);
```

---

### 🔹 Reducer Function

```jsx id="y1d9sk"
function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    default:
      return state;
  }
}
```

---

### 🔹 When to Use

✔ Complex state

✔ Multiple related values

✔ Large apps

---

### 🔹 useReducer vs useState

| useState | useReducer |
| -------- | ---------- |
| Simple   | Complex    |
| Direct   | Dispatch   |

---

## 🔹 SUMMARY

* useRef → mutable values, no re-render
* useContext → global data
* useMemo → optimize calculations
* useCallback → stable functions
* useReducer → complex logic

---

## 📝 QUESTIONS

1. Why ref.current does not re-render?

2. How does useMemo detect changes?

3. Why context causes re-renders?

4. When useReducer over useState?

5. Explain function identity issue

6. Auto-scroll chat using useRef

7. ThemeContext toggle

8. Optimize list with useMemo

9. Prevent re-render with useCallback

10. Build cart using useReducer

[⬅ Back to Home](../README.md)
