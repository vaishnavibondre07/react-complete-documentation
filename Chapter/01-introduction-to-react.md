# CHAPTER 1: Introduction to React

---

## What is React?

React is a **JavaScript library** used to build **User Interfaces (UI)**.

👉 It helps us build interactive applications like:

- Dashboards  
- E-commerce apps  
- Social media apps  
- Admin panels  

React was created by **Meta (formerly Facebook)**.

It is used in:

- Facebook  
- Instagram  
- Netflix  

---

## Why React Was Created?

Before React, websites were built using:

- HTML  
- CSS  
- JavaScript (Direct DOM manipulation)

### Problems in Traditional Approach

When the UI became large and dynamic:

- Code became messy  
- DOM updates were slow  
- State management became difficult  

### React Solved This By Introducing:

- ✅ Component-based architecture  
- ✅ Virtual DOM  
- ✅ Declarative UI  

---

## Library vs Framework

### Library

A library is a tool that helps you perform specific tasks.

React is called a **library** because:

- It focuses only on UI  
- You choose routing, state management, and other tools  

### Framework

A framework controls the entire structure of the application.

Example:

- Angular is a framework  

**Difference:**

- React → You control the structure  
- Angular → Framework controls the structure  

---

## What is SPA (Single Page Application)?

### Traditional Website (MPA – Multi Page Application)

- Entire page reloads when clicking a link  
- Example: News websites  

### SPA (Single Page Application)

In React:

- Only the required part of the page updates  
- No full page reload  

Examples:

- Gmail  
- Twitter  

That smooth user experience = SPA

---

## What is Virtual DOM?

### Normal DOM

Browser DOM is slow because:

- Every change updates the real DOM  
- Real DOM operations are expensive  

### Virtual DOM

React creates a **copy of the real DOM in memory**.

### Process:

1. Create virtual copy  
2. Compare old vs new (Diffing)  
3. Update only the changed part  
4. Apply minimal changes to real DOM  

This process is called **Reconciliation**.

---

## Example to Understand Virtual DOM

Imagine you change only a button text.

### Normal JavaScript:

- Browser may re-render the full section  

### React:

- Detects only the button changed  
- Updates only that button  

⚡ Result: Faster performance

---

## How React Works (Basic Flow)

1. You write JSX  
2. JSX converts into JavaScript  
3. React creates Virtual DOM  
4. React compares changes  
5. React updates the real DOM efficiently  

---

## React Core Philosophy

React follows **Declarative Programming**.

Instead of saying:

> "Change this element manually"

You say:

> "UI should look like this"

React handles updates automatically.

---

## Declarative vs Imperative Example

### ❌ Imperative (Normal JavaScript)

``` javascript ```

document.getElementById("btn").innerText = "Clicked";

You manually update the DOM.



### ✅ Declarative (React)

<button>{clicked ? "Clicked" : "Click Me"}</button>

You describe the UI based on state.
React handles the update.

---

### Summary

- React is a UI library

- It uses component-based structure

- Uses Virtual DOM for performance

- Follows declarative approach

- Helps build SPAs


---


### Important Questions

1. What is React and why is it called a JavaScript library instead of a framework?

2. Explain the difference between SPA and MPA.

3. What is Virtual DOM? Why is it faster than Real DOM?

4. What is Reconciliation in React?

5. What does declarative programming mean in React?

6. Explain step-by-step what happens when a state changes in React.

7. Write the flow of JSX to Real DOM in correct order.

8. Why does React improve performance in large applications?

9. What problem did React solve compared to traditional DOM manipulation?

10. If React did not use Virtual DOM, what issues could arise?


[⬅ Back to Home](../README.md)
