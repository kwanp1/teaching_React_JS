# Chapter 9: Understanding React Router

## What is a Single Page Application (SPA)?
A **Single Page Application (SPA)** is a web application that loads a **single HTML page** and dynamically updates the content as the user interacts with it, **without refreshing the entire page**. React applications are commonly built as SPAs.

### **Why Use an SPA?**
- **Faster Performance**: Only necessary content is loaded instead of reloading the entire page.
- **Smooth User Experience**: Users don't experience full-page reloads, making the app feel more like a native application.
- **Better Caching**: Data can be fetched once and stored, reducing server load.
- **Easier Frontend Development**: React components manage different sections of the page dynamically.

### **How React Router Enables SPAs**
- React Router allows **changing the URL** without triggering a full-page reload.
- It **updates the displayed component dynamically** while keeping the same HTML page in use.
- With **client-side routing**, React manages navigation entirely in the browser, reducing server requests.

## What is React Router?
React Router is a **library for handling navigation** in React applications. It allows users to navigate between different pages or views **without reloading the page** by using a concept called **client-side routing**.

### Why Use React Router?
- **Single Page Application (SPA) Support**: Helps manage multiple views in SPAs without full-page reloads.
- **Dynamic Routing**: Routes update dynamically based on the application state.
- **Declarative Routing**: Routes are defined as part of the component structure, making them easier to manage.
- **URL Synchronization**: Keeps the UI in sync with the browser’s URL.

## Installing React Router
To use React Router, install it using npm or yarn:
```sh
npm install react-router-dom
```
OR
```sh
yarn add react-router-dom
```

## Setting Up React Router
To use React Router, wrap your application inside a `BrowserRouter` component.

### Example: Basic Routing
```jsx
import React from "react";
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";

function Home() {
    return <h1>Home Page</h1>;
}

function About() {
    return <h1>About Page</h1>;
}

function App() {
    return (
        <Router>
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/about" element={<About />} />
            </Routes>
        </Router>
    );
}

export default App;
```
✅ **Key Points:**
- **`BrowserRouter`** provides routing capabilities.
- **`Routes`** acts as a container for multiple routes.
- **`Route`** maps a URL path to a component.

## Navigating Between Pages
To navigate between pages without a full refresh, use the `Link` component instead of `<a>` tags.

### Example: Navigation with `Link`
```jsx
import { Link } from "react-router-dom";

function Navbar() {
    return (
        <nav>
            <Link to="/">Home</Link>
            <Link to="/about">About</Link>
        </nav>
    );
}
```
✅ **Why Use `Link` Instead of `<a>`?**
- `<a>` reloads the page, breaking the SPA behavior.
- `Link` enables navigation **without refreshing the browser**.

## Dynamic Routing with URL Parameters
Sometimes, we need to pass dynamic values through the URL. React Router allows this using **URL parameters**.

### Example: Using URL Parameters
```jsx
import { useParams } from "react-router-dom";

function UserProfile() {
    let { username } = useParams();
    return <h1>Profile of {username}</h1>;
}
```
```jsx
<Routes>
    <Route path="/user/:username" element={<UserProfile />} />
</Routes>
```
✅ **How It Works:**
- `:username` is a **dynamic route parameter**.
- `useParams()` extracts the value from the URL.

## Redirecting Users
You can redirect users to another page using `Navigate`.

```jsx
import { Navigate } from "react-router-dom";

function NotFound() {
    return <Navigate to="/" />; // Redirect to home page
}
```

## Summary
- **React Router enables client-side navigation** in SPAs.
- **`BrowserRouter` wraps the app** to provide routing capabilities.
- **`Routes` and `Route` define paths** that map to components.
- **`Link` allows navigation** without page refresh.
- **URL parameters** (`useParams`) make routes dynamic.
- **`Navigate` helps in redirection**.

In the next chapter, we will explore **React Context API**, which allows state management across multiple components.

