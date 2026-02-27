# CHAPTER 2: JSX (JavaScript XML)

---

## What is JSX?

JSX stands for: **JavaScript XML**

It allows us to write HTML-like code inside JavaScript.

### Example:

```javascript```

``` *const element = <h1>Hello World</h1>;* ```

This looks like HTML, but it is actually JavaScript.

---

## Why JSX is Needed?

**Without JSX, React code looks like this:**

``` React.createElement("h1", null, "Hello World"); ```

**With JSX:**

``` <h1>Hello World</h1>```

-Much cleaner.

-Much readable.

-Much maintainable.

---

## How JSX Works Internally (Important)

JSX is NOT understood by the browser.

It is converted into JavaScript by: Babel

**Actual Flow**

JSX → Converted by Babel → React.createElement() → Virtual DOM → Real DOM

---

## JSX Rules (Very Important)

JSX follows strict rules.

*Rule 1: Return only ONE parent element*
```
 return (
  <div>
    <h1>Hello</h1>
    <p>World</p>
  </div>
); 
```
Or using Fragment:
```
 return (
  <>
    <h1>Hello</h1>
    <p>World</p>
  </>
);
```
<> </> is called a Fragment.



*Rule 2: Close all tags*

``` <img src="image.png" /> ```


*Rule 3: Use className instead of class*

Because class is a reserved JavaScript keyword.

``` <div className="container"></div> ```



*Rule 4: JavaScript inside {} (Curly Braces)*

```
const name = "Alice";

<h1>Hello {name}</h1>

```

Anything inside {} is JavaScript.

---

## Embedding JavaScript in JSX

You can use:

-Variables

-Expressions

-Functions

-Ternary operators

-map()

*Example*
```
const age = 20;
<h1>{age > 18 ? "Adult" : "Minor"}</h1>

```

React evaluates the expression and renders the result.

---

## JSX is Expression-Based

JSX is not a string. It is an expression that returns an object.

*Example*
``` const element = <h1>Hello</h1>; ```

*Behind the scenes:*

``` const element = React.createElement("h1", null, "Hello"); ```

So JSX produces JavaScript objects.

---

## Why JSX is Powerful?

Because:

-UI and logic stay together

-Makes components readable

-Easy to manage dynamic content

-Helps in conditional rendering

---

## Real Example to Understand JSX Deeply

Let’s create a small component:
```
function Welcome() {
  const name = "Vaishnavi";
  const isLoggedIn = true;

  return (
    <div>
      <h1>Hello {name}</h1>
      <p>{isLoggedIn ? "Welcome Back!" : "Please Login"}</p>
    </div>
  );
}
```
*What is happening?*

-JSX written inside return

-Curly braces allow JS expressions

-Conditional rendering using ternary

-Everything wrapped inside single parent <div>

-React converts this into JS objects → Virtual DOM → Real DOM.

---

## Technical Deep Dive (Beginner Friendly)

*When React sees:*

``` <h1>Hello</h1> ```

*It creates an object like:*
```
{
  type: "h1",
  props: {
    children: "Hello"
  }
}
```
That object becomes part of Virtual DOM.

This is why JSX must return a single parent.

Because internally, React is building a tree structure.

---

## SUMMARY

-JSX = JavaScript XML

-Converted by Babel

-Must return single parent

-Use {} for JavaScript

-class → className

-JSX creates objects (Virtual DOM elements)

---

## QUESTIONS

1. What is JSX and why is it used?

2. How does JSX get converted into JavaScript?

3. Why must JSX return only one parent element?

4. Why do we use className instead of class?

5. What is the purpose of {} in JSX?

6. Fix the error:
```
return (
  <h1>Hello</h1>
  <p>World</p>
);

```

7. Convert this JSX into React.createElement form:
   
``` <h1>Hello React</h1> ```


8. Write a component that displays:

   -Your name

   -Your age

   -A message using ternary operator inside JSX


9.  What will this output?
```
*const name = "Vaishnavi";* 
*<h1>{name.toUpperCase()}</h1>*

```

10. What happens if you forget to close a tag in JSX?

`` <br> ``

⬅ [Back to Home](../README.md)

