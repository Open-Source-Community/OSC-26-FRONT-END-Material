# 🔷 React Course – Session 4: React Router & Navigation

---

## 📑 Table of Contents


1. [URL Parameters with useSearchParams](#-working-with-url-search-params-usesearchparams)
2. [Nested Routes with Outlet](#-nested-routes-with-outlet)
3. [Default Redirects (Index Routes)](#-default-redirects-index-routes)
4. [404 Page Handling](#-handling-404-not-found-routes)
5. [Full Navbar Example with Login](#-full-navbar-example-with-login)
6. [Common Mistakes](#-common-mistakes)

---


## 🔍 Working with URL Search Params (`useSearchParams()`)

If the URL is: `/products?category=shoes&sort=price`, we can extract the info.

### Read Params:

```jsx
import { useSearchParams } from 'react-router-dom';

function Products() {
  const [searchParams] = useSearchParams();
  const category = searchParams.get('category');
  const sort = searchParams.get('sort');

  return (
    <>
      <p>Category: {category}</p>
      <p>Sort: {sort}</p>
    </>
  );
}
```

### Set Params:

```jsx
const [_, setSearchParams] = useSearchParams();
setSearchParams({ category: 'books', sort: 'rating' });
```

📌 **Why it's useful**:

* Filter/search/sort pages (e.g., e-commerce, blogs).
* Share links with the same filter applied.
* Keeps URL clean and user-friendly.

---

## 📂 Nested Routes with `Outlet`

You can show subpages under a layout.

### In App.jsx:

```jsx
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="profile" element={<Profile />} />
  <Route path="settings" element={<Settings />} />
</Route>
```

### In Dashboard.jsx:

```jsx
import { Outlet } from 'react-router-dom';

function Dashboard() {
  return (
    <div>
      <h1>Dashboard</h1>
      <Outlet /> {/* This is where child components show */}
    </div>
  );
}
```

---

## 🔀 Default Redirects (Index Routes)

Set a default component to render when a parent route's path is matched exactly.

### ✅ Basic Index Route

```jsx
<Route path="/dashboard" element={<Dashboard />}>
  <Route index element={<DashboardHome />} /> {/* Default child */}
  <Route path="profile" element={<Profile />} />
  <Route path="settings" element={<Settings />} />
</Route>
```

When visiting `/dashboard`, `<DashboardHome />` will render in the `<Outlet />`.

### ✅ Redirect from Index Route

```jsx
import { Navigate } from 'react-router-dom';

<Route path="/admin" element={<AdminLayout />}>
  <Route index element={<Navigate to="dashboard" />} />
  <Route path="dashboard" element={<AdminDashboard />} />
  <Route path="users" element={<UserManagement />} />
</Route>
```

Now visiting `/admin` will redirect to `/admin/dashboard`.

---

## ❌ Handling 404 (Not Found) Routes

To catch all unknown paths:

```jsx
<Route path="*" element={<NotFound />} />
```

**Where to write:**
Put this at the **end of all your routes** inside `Routes` in `App.jsx`. This way, if no route matches, this one catches it.

### Example:

```jsx
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="*" element={<NotFound />} />
</Routes>
```

### Why?

To show a nice error page instead of a blank screen.

---

## 🧩 Full Navbar Example with Login

Here's a complete implementation of a responsive navbar with login functionality:

```jsx
// App.jsx
import { BrowserRouter, Routes, Route, Navigate } from 'react-router-dom';
import Navbar from './components/Navbar';
import Home from './pages/Home';
import About from './pages/About';
import Login from './pages/Login'; // Added Login page
import Users from './pages/Users';
import Products from './pages/Products';
import Dashboard from './pages/Dashboard';
import DashboardHome from './pages/DashboardHome';
import Profile from './pages/Profile';
import Settings from './pages/Settings';
import NotFound from './pages/NotFound';

function App() {
  return (
    <BrowserRouter>
      <Navbar />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/login" element={<Login />} />
        <Route path="/users" element={<Users />} />
        <Route path="/users/:id" element={<UserDetail />} />
        <Route path="/products" element={<Products />} />
        
        {/* Dashboard with default redirect */}
        <Route path="/dashboard" element={<Dashboard />}>
          <Route index element={<Navigate to="home" replace />} />
          <Route path="home" element={<DashboardHome />} />
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
        
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

```jsx
// components/Navbar.jsx
import { NavLink, useNavigate } from 'react-router-dom';

function Navbar() {
  const navigate = useNavigate();
  
  return (
    <nav className="navbar">
      <div className="logo">MyApp</div>
      
      <div className="nav-links">
        <NavLink to="/" className={({isActive}) => isActive ? 'active' : ''}>
          Home
        </NavLink>
        
        <NavLink to="/about" className={({isActive}) => isActive ? 'active' : ''}>
          About
        </NavLink>
        
        <NavLink to="/users" className={({isActive}) => isActive ? 'active' : ''}>
          Users
        </NavLink>
        
        <NavLink to="/products" className={({isActive}) => isActive ? 'active' : ''}>
          Products
        </NavLink>
        
        <NavLink to="/dashboard" className={({isActive}) => isActive ? 'active' : ''}>
          Dashboard
        </NavLink>
      </div>
      
      <div className="nav-actions">
        <button onClick={() => navigate('/login')}>Login</button>
        <button onClick={() => navigate(-1)}>Back</button>
      </div>
    </nav>
  );
}

export default Navbar;
```


---

## ⚠️ Common Mistakes

### ❌ Forgetting to wrap app in BrowserRouter

```jsx
// ❌ Missing BrowserRouter
<Routes>
  <Route path="/" element={<Home />} />
</Routes>

// ✅ Correct
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
  </Routes>
</BrowserRouter>
```

### ❌ Using <a> tags instead of Link

```jsx
// ❌ Causes full page reload
<a href="/about">About</a>

// ✅ Correct - no page reload
<Link to="/about">About</Link>
```

### ❌ Missing key prop in route lists

```jsx
// ❌ Causes performance issues
{users.map(user => (
  <Link to={`/user/${user.id}`}>{user.name}</Link>
))}

// ✅ Correct - unique key required
{users.map(user => (
  <Link key={user.id} to={`/user/${user.id}`}>{user.name}</Link>
))}
```

### ❌ Forgetting Outlet in nested routes

```jsx
// ❌ Child routes won't render
function Dashboard() {
  return <h1>Dashboard</h1>;
}

// ✅ Correct - include Outlet
function Dashboard() {
  return (
    <div>
      <h1>Dashboard</h1>
      <Outlet /> {/* Renders child routes */}
    </div>
  );
}
```

### ❌ Misplacing the 404 route

```jsx
// ❌ 404 catches too early
<Routes>
  <Route path="*" element={<NotFound />} />
  <Route path="/about" element={<About />} />
</Routes>

// ✅ Correct - 404 route last
<Routes>
  <Route path="/about" element={<About />} />
  <Route path="*" element={<NotFound />} />
</Routes>
```

### ❌ Incorrect use of useParams

```jsx
// ❌ Won't work - missing colon in path
<Route path="/user/id" element={<User />} />

// ✅ Correct - colon indicates parameter
<Route path="/user/:id" element={<User />} />
```

### ❌ Not handling URL parameters safely

```jsx
// ❌ May crash if param missing
function User() {
  const { id } = useParams();
  return <h2>User ID: {id}</h2>;
}

// ✅ Safer - handle missing case
function User() {
  const { id } = useParams();
  
  if (!id) return <div>User ID missing!</div>;
  
  return <h2>User ID: {id}</h2>;
}
```

### ❌ Confusing useParams and useSearchParams

```jsx
// ❌ Incorrect - useParams for query params
const { category } = useParams(); // Won't work for /products?category=shoes

// ✅ Correct - useSearchParams for query params
const [searchParams] = useSearchParams();
const category = searchParams.get('category');
```

### ❌ Forgetting replace in redirects

```jsx
// ❌ Adds unnecessary history entry
<Route index element={<Navigate to="dashboard" />} />

// ✅ Correct - replace current history entry
<Route index element={<Navigate to="dashboard" replace />} />
```
