# CHAPTER 3: COMPONENTS

---

## What is a Component?

A Component is a reusable piece of UI.

Think of it like: A building block of your application.

Instead of writing one big HTML file, React says:  
Break your UI into small, reusable pieces.

---

## Real Life Analogy

Imagine a website like Instagram:

- Navbar  
- Sidebar  
- Post  
- Comment  
- Footer  

Each of these is a component.

---

## Why Components Are Important?

Without components:

- Code becomes messy  
- Hard to maintain  
- Hard to reuse  

With components:

- Clean structure  
- Reusable UI  
- Easy to manage  

This is called: **Component-Based Architecture**

---

## Types of Components in React

Earlier React had:

- Class Components  
- Functional Components  

Now in modern React:

✅ We use **Functional Components**

---

## Functional Component (Modern Way)

A functional component is just a JavaScript function that returns JSX.

### Example:

```jsx```
```
function Welcome() {
  return <h1>Hello World</h1>;
}
```

Or arrow function:

```
const Welcome = () => {
  return <h1>Hello World</h1>;
};
```

## How to Use a Component?

If you create:
```
function Welcome() {
  return <h1>Hello World</h1>;
}
```
You use it like:

``` <Welcome /> ```

*Important Rule*

Component names must start with *Capital Letter*.

❌ <welcome />
✅ <Welcome />

Because:

-Lowercase = HTML tag

-Capital = React component

---

## How React Sees Components Internally

When you write:

`` <Welcome /> ``

React converts it into:

``` React.createElement(Welcome) ```

React calls the function → gets JSX → creates Virtual DOM → updates UI.

---

## Component Tree (Very Important Concept)

React apps are built as a tree of components.

*Example Structure:*
```
App
├── Navbar
├── Sidebar
├── Content
│    ├── Post
│    ├── Post
│    └── Post
└── Footer
```
---

## Reusable Components (Very Important)

Instead of writing:

```
<h1>User 1</h1>
<h1>User 2</h1>
<h1>User 3</h1>
```

We create:

```
function User() {
  return <h1>User</h1>;
}
```

Then use it multiple times:
```
<User />
<User />
<User />
```
Same structure, reused.

Later we’ll customize it using Props (next chapter 🔥).

---

## Small Practical Example

Let’s build a mini app:

```
function Navbar() {
  return <h2>My Website</h2>;
}

function Footer() {
  return <p>Copyright 2026</p>;
}

function App() {
  return (
    <div>
      <Navbar />
      <h1>Welcome</h1>
      <Footer />
    </div>
  );
}

```

# What is happening?

- App is root component

- Navbar and Footer are child components

- UI is divided into logical sections

- Clean and maintainable

---

## Folder Structure (Beginner Friendly + Industry Style)

*Basic structure:*
```
src/
├── components/
│     ├── Navbar.jsx
│     ├── Footer.jsx
│     └── User.jsx
├── App.jsx
└── main.jsx
```

*Why*

- Keeps code organized

- Easy to scale

- Industry standard practice

---

## Deep Concept: Composition Over Inheritance

React prefers:

👉 Composition (combining components)

Instead of:

❌ Inheritance (like OOP classes)

You combine components to build bigger UI.

Example:
```
<Card>
  <Profile />
</Card>
```

## SUMMARY

- Component = reusable UI block

- Functional components are modern standard

- Must start with capital letter

- React apps are component trees

- Use composition to build UI

---

## QUESTIONS

1. What is a functional component?

2. Why must component names start with a capital letter?

3. Explain component-based architecture.

4. What is component composition?

5. What is a component tree?

6. Create a component called *Header* that displays a website title.

7. Create a component called *Footer* and use it inside App.
   
8. Create three components:

     - Navbar

     - Sidebar

     - Content

     Combine them inside App.

9. What will happen if you write ``` <header /> ``` instead of ``` <Header /> ```?
    
10. Create a reusable *Card* component.


[⬅ Back to Home](../)
