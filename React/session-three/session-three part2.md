# 🔷 React Course – Session 3.2: React Router & Navigation

---

## 📑 Table of Contents

1. [Installation](#-installation)
2. [What is Routing in React?](#-what-is-routing-in-react)
3. [BrowserRouter, Routes & Route](#-react-router-basics-what-are-the-key-parts)
4. [Link vs NavLink (with design example)](#-link-vs-navlink--whats-the-difference)
5. [Dynamic Routing with useParams](#-dynamic-routing-with-useparams)
6. [Navigation with useNavigate](#-programmatic-navigation-with-usenavigate)

## 📦 Installation

Before using React Router, you need to install it in your project:

```bash
npm install react-router-dom
```

Or if you're using yarn:

```bash
yarn add react-router-dom
```

This installs the latest version of React Router

---

## 🧭 What is Routing in React?

In a traditional website, navigating to a new page reloads the entire browser window. But in **React**, which is a single-page application (SPA) framework, we simulate page navigation **without reloading** using a library called **React Router**.

Routing helps you:

* Change views without reloading the page.
* Preserve app state.
* Load content based on URL.

---

## 🔧 React Router Basics: What Are the Key Parts?

### 🔹 `BrowserRouter`

This is the **main component** that wraps your entire app. It enables routing using the browser's address bar.

> 🧠 Think of it like a container that tells React: "Hey, I want to enable routing here."

**Where to write it:** In `index.js`:

```jsx
import { BrowserRouter } from 'react-router-dom';

ReactDOM.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>,
  document.getElementById('root')
);
```

---

### 🔹 `Routes` and `Route`

* `<Routes>`: A container for all the routes.
* `<Route>`: Defines a path and the component to show.

```jsx
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
</Routes>
```

> 📍 `path` is the URL path.
> 🧩 `element` is the component to display when that path is visited.

🧠 **Difference Between `Routes` and `Route`:**

* `Routes` holds multiple `Route` components.
* `Route` maps a specific path to a specific component.

---

## 🔗 Link vs NavLink – What’s the Difference?

### 🔸 `Link`

* Used to navigate **without refreshing the page**.
* Replaces traditional `<a>` tags.

```jsx
<Link to="/about">About</Link>
```

### 🔸 `NavLink`

* Works like `Link` **but also tells you if the link is active**.
* Good for navigation menus (e.g., highlight the current tab).

```jsx
<NavLink
  to="/about"
  className={({ isActive }) => isActive ? 'active-link' : ''}
>
  About
</NavLink>
```

🧠 **Key Difference:** `NavLink` adds styling when the link matches the current route.

**Design Example (CSS):**

```css
.active-link {
  font-weight: bold;
  color: blue;
  border-bottom: 2px solid blue;
}
```

```jsx
<NavLink to="/home">Home</NavLink>
<NavLink to="/about">About</NavLink>
```

When you're on `/about`, the "About" link is highlighted automatically.

---

## 🔢 Dynamic Routing with `useParams()`

Used when the path has variables (e.g., `/user/123`).

### Step-by-step:

1. In `App.jsx`:

```jsx
<Route path="/user/:id" element={<User />} />
```

2. In `User.jsx`:

```jsx
import { useParams } from 'react-router-dom';

function User() {
  const { id } = useParams();
  return <h2>User ID: {id}</h2>;
}
```

📌 `:id` is a placeholder that React Router understands.

---

## 🚀 Programmatic Navigation with `useNavigate()`

Sometimes, you need to navigate after something happens (e.g., login).

```jsx
import { useNavigate } from 'react-router-dom';

function Login() {
  const navigate = useNavigate();

  function handleLogin() {
    // Login logic here
    navigate('/dashboard'); // Redirect to dashboard
  }

  return <button onClick={handleLogin}>Login</button>;
}
```

### 🔁 Go Back or Forward

```jsx
navigate(-1); // Go back
navigate(1);  // Go forward
```

-----------------------------------------------------------