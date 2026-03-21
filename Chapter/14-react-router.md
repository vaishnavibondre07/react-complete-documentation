# CHAPTER 14: REACT ROUTER

---

## 🔹 What is Routing?

Routing allows users to navigate between different pages in an application.

### 🆚 Traditional vs React Routing

* Traditional:

  * New HTML page loads
  * Full page refresh

* React (SPA):

  * Single HTML file
  * UI updates dynamically
  * No page reload

👉 Faster and smoother experience

---

## 🔹 How Routing Works in SPA

When URL changes:

* React Router intercepts
* Matches path
* Renders component
* Updates UI without reload

---

## 🔹 Installation

```bash id="q2k9d1"
npm install react-router-dom
```

---

## 🔹 Core Components

* BrowserRouter
* Routes
* Route
* Link
* useParams
* useNavigate

---

## 🔹 BrowserRouter

```jsx id="a8k2d1"
import { BrowserRouter } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Main />
    </BrowserRouter>
  );
}
```

👉 Enables routing using history API

---

## 🔹 Routes & Route

```jsx id="b3k9d2"
import { Routes, Route } from "react-router-dom";

function Main() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="/login" element={<Login />} />
    </Routes>
  );
}
```

---

## 🔹 Link (No Reload Navigation)

```jsx id="c4k2d3"
import { Link } from "react-router-dom";

<Link to="/about">About</Link>
```

❌ Avoid `<a>`
✔ Use `Link`

---

## 🔹 useParams (Dynamic Routing)

```jsx id="d7k1p3"
<Route path="/users/:id" element={<UserDetails />} />
```

```jsx id="e8k2d4"
import { useParams } from "react-router-dom";

function UserDetails() {
  const { id } = useParams();
  return <h1>User ID: {id}</h1>;
}
```

---

## 🔹 useNavigate (Programmatic Navigation)

```jsx id="f1k9d2"
import { useNavigate } from "react-router-dom";

function Login() {
  const navigate = useNavigate();

  function handleLogin() {
    navigate("/dashboard");
  }
}
```

---

## 🔹 Nested Routes

```jsx id="g9k2d1"
<Route path="/dashboard" element={<DashboardLayout />}>
  <Route path="profile" element={<Profile />} />
  <Route path="settings" element={<Settings />} />
</Route>
```

```jsx id="h2k8d3"
import { Outlet } from "react-router-dom";

function DashboardLayout() {
  return (
    <>
      <h1>Dashboard</h1>
      <Outlet />
    </>
  );
}
```

---

## 🔹 Protected Routes

```jsx id="i3k9d1"
function ProtectedRoute({ children }) {
  const { user } = useContext(AuthContext);

  if (!user) {
    return <Navigate to="/login" />;
  }

  return children;
}
```

---

## 🔹 Role-Based Protection

```jsx id="j2k8d4"
if (user.role !== "admin") {
  return <Navigate to="/" />;
}
```

---

## 🔹 Real MERN Flow

Login:

* Submit form
* Get token
* Store token
* Update context
* Navigate to dashboard

Logout:

* Remove token
* Clear state
* Redirect

---

## 🔹 Best Practices

✔ Wrap app with BrowserRouter

✔ Use ProtectedRoute

✔ Keep routes separate

✔ Use Link instead of `<a>`

---

## 🔹 Common Mistakes

❌ Using `<a>`

❌ Forgetting Outlet

❌ No auth handling

❌ Hardcoding routes

---

## 🔹 SUMMARY

* Routing enables SPA navigation
* BrowserRouter syncs URL
* Routes map components
* Link avoids reload
* useParams → dynamic routes
* useNavigate → navigation
* Nested routes → layouts
* Protected routes → security
---

## 📝 QUESTIONS

1. Difference between SPA and traditional routing?

2. Why use Link instead of `<a>`?

3. How BrowserRouter works?

4. Purpose of Outlet?

5. Why protected routes?

6. Create basic routing

7. Dynamic product route

8. Nested dashboard routes

9. ProtectedRoute using context

10. Role-based routing


[⬅ Back to Home](../README.md)
