# Chapter 6: Understanding Hooks

## What are Hooks?
Hooks are a feature in React that allow functional components to use state and lifecycle methods without needing to write class components. Introduced in React 16.8, hooks provide a cleaner and more reusable way to manage component behavior.

A React Hook is a special function that allows functional components to use React features like state and lifecycle methods without needing class components.

### Why Use Hooks?
- **Simplifies Code**: Hooks reduce the need for class components and make logic reusable.
- **Better Code Organization**: Encourages separation of concerns in functional components.
- **Easier State Management**: Hooks allow stateful logic to be used in function components.

### Why is useState a React Hook?
What is useState in React?
useState is not a keyword in JavaScript or React. It is a function that comes from the React library.


## Commonly Used Hooks
React provides several built-in hooks, including:

### 1. `useState`: Managing State in Functional Components
The `useState` hook allows components to store and update local state.

#### Example:
```jsx
import React, { useState } from "react";

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}
```
- `useState(0)` initializes state with a value of `0`.
- `setCount` updates the state when the button is clicked.

### 2. `useEffect`: Handling Side Effects
The `useEffect` hook allows functional components to perform side effects such as data fetching, subscriptions, or manual DOM manipulations.

#### Example:
```jsx
import React, { useState, useEffect } from "react";

function Timer() {
    const [seconds, setSeconds] = useState(0);

    useEffect(() => {
        const interval = setInterval(() => {
            setSeconds((prev) => prev + 1);
        }, 1000);

        return () => clearInterval(interval); // Cleanup function
    }, []);

    return <p>Time: {seconds}s</p>;
}
```
- `useEffect` runs once when the component mounts (due to `[]` dependency array).
- The cleanup function prevents memory leaks by clearing the interval.

### 3. `useContext`: Managing Global State
The `useContext` hook allows components to access global state without prop drilling.

#### Example:
```jsx
import React, { useContext } from "react";
const ThemeContext = React.createContext("light");

function ThemedComponent() {
    const theme = useContext(ThemeContext);
    return <p>Current Theme: {theme}</p>;
}
```
- `useContext(ThemeContext)` provides access to the nearest `ThemeContext.Provider` value.

## Summary
- **Hooks enable state and side effects in functional components.**
- **`useState`** manages component-level state.
- **`useEffect`** handles side effects like API calls and event listeners.
- **`useContext`** allows for global state management without prop drilling.

