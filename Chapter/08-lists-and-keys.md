# CHAPTER 8: Lists and Keys

---

## Why Lists Are Important?

In real applications, data usually comes in arrays.

Examples:
- List of users
- List of products
- List of posts
- List of comments

React must render these dynamically.

That’s where **Lists & Keys** come in.

---

## Rendering Lists Using `map()`

In JavaScript:

```js```

const numbers = [1, 2, 3];


To display each number in React:

```
function NumberList() {
  const numbers = [1, 2, 3];

  return (
    <ul>
      {numbers.map((num) => (
        <li>{num}</li>
      ))}
    </ul>
  );
}
```
### 🔍 What is Happening?

  - map() loops over the array

  - For each element → returns JSX

  - React renders each item

### Important:

- map() returns a new array

- That array contains JSX elements

---

## The Key Problem ⚠️

If you run the previous code, React shows a warning:

  Each child in a list should have a unique "key" prop.

Why?

  Because React needs a way to identify each item uniquely.

---

What is a Key?

A **key** is a special prop used by React to:

  - Identify list items

  - Track changes

  - Optimize re-rendering

*Correct example:*

```
function NumberList() {
  const numbers = [1, 2, 3];

  return (
    <ul>
      {numbers.map((num) => (
        <li key={num}>{num}</li>
      ))}
    </ul>
  );
}
```

Now each `` <li> `` has a unique key.

---

## Why Keys Are Important? (Deep Concept)

When state changes:

React compares old list vs new list.

Without keys:

  - React gets confused

  - May re-render entire list

  - Performance issues

With keys:

  - React knows exactly which item changed

This process is part of the:

## 👉 Reconciliation Algorithm

---

### Flow:

Old List → New List → Compare using Keys → Update only changed item

---

## Best Source for Keys

Best keys:

  - ✅ Unique ID from database (MongoDB _id)

  - ✅ UUID
  
  - ✅ Unique stable value

# Example (MERN style):

```
function UserList({ users }) {
  return (
    <div>
      {users.map((user) => (
        <p key={user._id}>{user.name}</p>
      ))}
    </div>
  );
}
```

Perfect key = _id

---

Why Index as Key is Bad Practice

You might see:

key={index}

This is not recommended if:

  - Items can be deleted

  - Items can be reordered

  - Items can be inserted in the middle

Because:

 Indexes change → React misidentifies items.

Use index only when:

  - List is static

  - No reordering

---

## Real MERN Example (Products List)

```
function ProductList() {
  const products = [
    { id: 1, name: "Laptop", price: 50000 },
    { id: 2, name: "Phone", price: 20000 }
  ];

  return (
    <div>
      {products.map((product) => (
        <div key={product.id}>
          <h2>{product.name}</h2>
          <p>₹ {product.price}</p>
        </div>
      ))}
    </div>
  );
}
```

---

## Rendering Components Inside map()

Very common pattern:

```
function Product({ name, price }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>₹ {price}</p>
    </div>
  );
}

function ProductList({ products }) {
  return (
    <>
      {products.map((product) => (
        <Product
          key={product.id}
          name={product.name}
          price={product.price}
        />
      ))}
    </>
  );
}
```

This is an industry-level pattern.

---

## Common Mistakes

❌ Forgetting key

❌ Using random key every render

❌ Using array index incorrectly

❌ Mutating array instead of creating new array

---

## 🧠 Deep Understanding

Keys help React:

  - Identify elements

  - Prevent unnecessary re-renders

  - Improve performance

  - Maintain correct UI state

Without keys → React loses track of identity.

---

## SUMMARY

  - Use map() to render lists

  - Each element must have a unique key

  - Keys help React optimize updates

  - Avoid index as key when possible

  - Use database IDs in MERN apps

---

## QUESTIONS

1. Why are lists important in React?

2. What does map() do when rendering lists?

3. What is a key in React?

4. Why does React require unique keys?

5. What problems occur if keys are missing?

6. Why is using array index as key not recommended?

7. Write a React component that renders a list of numbers using map().

8. Create a component that displays a list of users with their names.

9. Render a Product component inside map().

10.Explain how keys help React's Reconciliation Algorithm.
<br>

[⬅ Back to home ](../README.md) 




