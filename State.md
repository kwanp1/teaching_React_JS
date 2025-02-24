# Chapter 5: Understanding State and Lifecycle

## What is State in React?
State is a built-in feature in React that allows components to store and manage dynamic data. Unlike props, which are passed down from parent components, state is **local** to a component and can change over time, causing the component to re-render with updated data.
When I say “State is a built-in feature in React”, I mean that state management is a core capability provided by React. It allows components to store and update data dynamically, enabling interactive user interfaces.

### Why Use State?
- **Stores Dynamic Data**: Helps manage values that change over time (e.g., user input, API responses, etc.).
- **Triggers Re-Renders**: React updates the UI whenever state changes.
- **Encapsulated in Components**: State is maintained within the component itself, ensuring modularity.

## What is `useState` in React?
`useState` is a **React Hook** that allows functional components to maintain and update state.

useState is a function: In functional components, React provides the useState Hook, which returns an array containing:
	1.	State value (which can be any data type).
	2.	A function to update the state.


### Is `useState` a JavaScript Keyword?
No, `useState` is **not** a JavaScript keyword. It is a **function** provided by React as part of the Hooks API. Since it is a named export from React, we need to import it explicitly:

```jsx
import { useState } from "react";
```

Since `useState` is a function, you can verify this by checking its type:
```js
console.log(typeof useState); // Output: "function"
```

## Can We Have Multiple `useState` Hooks?
Yes! There is **no limit** to the number of `useState` hooks in a React component. Each call to `useState` manages a separate state variable.

```jsx
const [count, setCount] = useState(0); // First useState
const [name, setName] = useState("Alice"); // Second useState
```

Each `useState` is independent, meaning updating one state does **not** affect the others.

## How to Use `useState`
### 1️⃣ Basic Syntax:
```jsx
const [state, setState] = useState(initialValue);
```
- **`state`**: Stores the current value.
- **`setState`**: Function to update the state.
- **`initialValue`**: Initial value of the state.

### 2️⃣ Example: Counter Component
```jsx
import React, { useState } from "react";

function Counter() {
    const [count, setCount] = useState(0); // Defining state

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}

export default Counter;
```


### 3️⃣ Example: Using `useState` with Objects
```jsx
const [user, setUser] = useState({ name: "Alice", age: 25 });

function updateAge() {
    setUser(prevUser => ({
        ...prevUser, // Keep existing properties
        age: prevUser.age + 1 // Update age
    }));
}
```
In functional components, state itself is not a function, but useState is.
What Are React’s Functional Components?

Functional components in React are JavaScript functions that return JSX (UI elements). They are the modern way to create React components, replacing class components in most cases.

## Understanding Component Lifecycle
In React, every component follows a **lifecycle** that determines how and when it should be rendered or updated. React components go through three main lifecycle phases:

### **1️⃣ Mounting (Component is Created)**
- The component **is added to the DOM**.
- **Common use case**: Fetching data when the component loads.
- Hook: `useEffect(() => {...}, [])`

### **2️⃣ Updating (Component Re-renders)**
- Happens when **state or props change**.
- **Common use case**: Updating the UI when the user interacts with the component.
- Hook: `useEffect(() => {...}, [state])`

### **3️⃣ Unmounting (Component is Removed)**
- The component **is removed from the DOM**.
- **Common use case**: Cleaning up event listeners or timers.
- Hook: `useEffect(() => { return () => {...} }, [])`

## Using Lifecycle with `useEffect`
The `useEffect` Hook allows functional components to handle **side effects** like API calls, timers, or event listeners.

### Example: Timer Component
```jsx
import React, { useState, useEffect } from "react";

function Timer() {
    const [seconds, setSeconds] = useState(0);

    useEffect(() => {
        console.log("Component Mounted");
        
        const interval = setInterval(() => {
            setSeconds(prev => prev + 1);
        }, 1000);

        return () => {
            console.log("Component Unmounted");
            clearInterval(interval); // Cleanup function
        };
    }, []); // Runs once when the component mounts

    return <p>Time: {seconds}s</p>;
}

export default Timer;
```
✅ **What Happens?**
- `useEffect` runs **once** when the component mounts (`[]` dependency array).
- The `setInterval` function **updates state every second**, causing re-renders.
- When the component **unmounts**, the cleanup function (`clearInterval`) stops the timer.

## Props vs. State
| Feature      | Props | State |
|-------------|-------|-------|
| **Definition** | Passed from parent to child component | Managed inside the component |
| **Mutability** | Immutable – cannot be modified by the child component | Mutable – can be updated using `setState` |
| **Who Controls It?** | Controlled by the parent component | Controlled by the component itself |
| **Use Case** | Used to pass static or dynamic data to child components | Used to store and update dynamic values |
| **Re-Renders?** | Changing props will re-render the component | Updating state will re-render the component |

## Summary
- **State** stores **dynamic data** and triggers re-renders when updated.
- **`useState` is a React Hook**, not a JavaScript keyword, and allows **functional components** to have state.
- **There is no limit** to how many `useState` hooks can be used in a component.
- **Lifecycle phases**: Mounting, Updating, Unmounting.
- **`useEffect`** is used to handle **side effects** like API calls and event listeners.
- **Props are immutable**, while **state is mutable and managed inside a component**.

In the next chapter, we will explore **Hooks**, which provide more power to functional components beyond state management.

