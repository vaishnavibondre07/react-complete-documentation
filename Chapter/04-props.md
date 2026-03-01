# CHAPTER 4: PROPS

---

## What are Props?

Props stands for: **Properties**

Props are used to pass data from one component to another.

Usually:

👉 Parent → Child  

Think of props like function parameters.

---

## Why Props Are Needed?

Without props, components are static.

### Example:

```jsx ```

```
function User() {
  return <h1>Hello User</h1>;
}
```
No matter how many times you use it, output is same.

But real apps need dynamic data:

   - Different user names

   - Different products

   - Different prices

That’s where props come in.

---

# Basic Example of Props

*Step 1: Create Component*

```
function User(props) {
  return <h1>Hello {props.name}</h1>;
}
```

*Step 2: Pass Data*

```
<User name="Alice" />
<User name="John" />
```

Output:

*Hello Alice*

*Hello John*

---

# How It Works Internally

When you write:

``` <User name="Alice" /> ```

React converts it into:

``` User({ name: "Alice" }); ```

So props is just an object:

``` 
props = {
  name: "Vaishnavi"
}
```

That’s why we access: ``` props.name ```

---

# Destructuring Props (Modern Way)

Instead of:
```
function User(props) {
  return <h1>Hello {props.name}</h1>;
}
```

We use:

```
function User({ name }) {
  return <h1>Hello {name}</h1>;
}
```

- Cleaner.

- More readable.
  
- Industry standard.

---

# Passing Multiple Props

```
function User({ name, age }) {
  return (
    <div>
      <h1>{name}</h1>
      <p>Age: {age}</p>
    </div>
  );
}
```

Usage: ``` <User name="Alice" age={20} /> ```

Notice:

- Strings → "text"

- Numbers → {20}

Because curly braces allow JavaScript expressions.

---

# Props are Read-Only (Very Important)

Props cannot be changed inside child component.

❌ Wrong:

`` props.name = "New Name"; ``

React will not allow this.

Why?

*Because props follow one-way data flow.*

Parent controls data.

Child receives data.

---

# One-Way Data Flow (Core React Principle)

Flow: *Parent → Child → Child → Child*

Data flows downward only.

This makes debugging easier and applications more predictable.

---

# Children Prop (Very Important Concept)

React has a special prop called: children

```
Example:
function Card({ children }) {
  return <div className="card">{children}</div>;
}
```
Usage:

```
<Card>
  <h1>Hello</h1>
  <p>This is inside card</p>
</Card>
```
Everything inside *<Card>* becomes *children.*

This is powerful for reusable layouts.

---

# Props vs State (Basic Idea)

```     
        Props	                       State                
      
  Passed from parent	       Managed inside component        

      Read-only	                 Can be changed              

     External data	             Internal data


 ```

We’ll deeply understand state in the next chapter.

---

# Real Example (MERN Style)

Imagine a product list:

```
function Product({ title, price }) {
  return (
    <div>
      <h2>{title}</h2>
      <p>₹ {price}</p>
    </div>
  );
}
```

Usage:

```
<Product title="Laptop" price={50000} />
<Product title="Phone" price={20000} />
```

Same component → different data → dynamic UI.

This is real-world usage in e-commerce apps.

---

# Deep Understanding

Props make components:

  - Reusable

  - Dynamic

  - Modular

  - Scalable

Without props, React apps would be static.

---

# SUMMARY

Props pass data

Parent → Child

Props are objects

Props are read-only

Supports children prop

Follows one-way data flow

---

# QUESTIONS

1. What are props?

2. Why are props read-only?

3. Explain one-way data flow.

4. What is destructuring in props?

5. What is the *children* prop?

6. Create a *User* component that accepts *name* and *age* as props.
   
7. Pass multiple props to a component.
   
8. Create a Button component that receives text as prop.
   
9. Create a Card component that uses children.
    
10. What will happen if you try to modify props inside a component?



[⬅ Back to Home](../README.md)
