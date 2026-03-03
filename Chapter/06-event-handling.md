# CHAPTER 6: EVENT HANDLING

---

## What is Event Handling?

An event is an action performed by the user.

#### Examples:

- Clicking a button  
- Typing in input  
- Submitting a form  
- Hovering over element  

Event handling in React means:

Responding to user actions and executing code.

---

## React vs Normal JavaScript Events

#### In Normal JavaScript

```javascript```
```
document.getElementById("btn").addEventListener("click", function () {
  console.log("Clicked");
});
```
In React

``` <button onClick={handleClick}>Click</button> ```

React uses:

  - camelCase event names

  - JSX syntax

  - Functions instead of strings

---

## Basic Event Example

```
function Button() {
  function handleClick() {
    alert("Button Clicked!");
  }

  return <button onClick={handleClick}>Click Me</button>;
}
```

Explanation:

  - onClick is the event

  - handleClick is the function

  - Function runs when button is clicked

---

## Arrow Function in Events

You can also write:

```
<button onClick={() => alert("Clicked")}>
  Click Me
</button>
```

⚠ Avoid writing heavy logic inside JSX.

#### Better practice: Define function separately.

---

## Event Object (Very Important)

React automatically passes an *event object*.

```
function handleChange(event) {
  console.log(event.target.value);
}
```
Usage: 

`` <input onChange={handleChange} /> ``

The event object contains:

  - event.target

  - event.type

  - event.preventDefault()

  - many more properties

---

## Synthetic Events (Important Technical Concept)

React does not use native browser events directly.

Instead, React creates:

#### 👉 SyntheticEvent

It is a wrapper around the browser's native event.

*Why?*

  - Better cross-browser compatibility

  - Same behavior everywhere

So when you use: *onClick*

You are using React’s SyntheticEvent system.

---

## Passing Arguments to Event Handler

Sometimes you need to pass custom values.

```
function handleClick(name) {
  alert(name);
}
```

Correct way:

```
 <button onClick={() => handleClick("Vaishnavi")}> 
  Click
 </button>
```
Wrong way:

`` <button onClick={handleClick("Vaishnavi")}> ``

Because this will execute immediately instead of waiting for click.

---

## Combining Events + State (Very Important)

Let’s build a counter again:

```
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  function increase() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increase}>Increase</button>
    </div>
  );
}

```

#### Flow:

User Click → Event triggers → State updates → Re-render → UI updated

- Events are entry points to change state.

---

## Form Submission Example

```
function Form() {
  function handleSubmit(event) {
    event.preventDefault();
    alert("Form Submitted");
  }

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}

```

## Why preventDefault()?

Because:

  - By default, form reloads the page

  - React apps should not reload page (SPA concept)

---

## Common React Events

```
  Event	                   Usage

 onClick	              Button click

 onChange	              Input change

 onSubmit	              Form submit

 onMouseOver	             Hover

 onKeyDown	            Keyboard press

```

All events are written in *camelCase*.

---

## Deep Understanding

Events connect: *User → State → UI*

Without events:

  - No interaction

  - No dynamic behavior

Events are entry points to update state and trigger re-renders.

---

## SUMMARY

  - React events use camelCase

  - Pass function reference

  - Uses SyntheticEvent wrapper

  - Combine events + state

  - Use preventDefault for forms

---

## QUESTIONS


1. What is a SyntheticEvent?

2. Why are React event names written in camelCase?

3. What is the difference between onClick={handleClick} and onClick={handleClick()}?

4. Why do we use event.preventDefault()?

5. How do events connect to state updates?

6. Create a button that shows alert when clicked.
   
7. Create an input field that logs value on every change.
   
8. Create a form that prevents page reload on submit.
   
9. Pass custom argument to event handler.
    
10. Build a small counter using events + state.
<br>

[⬅ Back to Home](../README.md)


