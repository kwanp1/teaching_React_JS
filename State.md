# Chapter 5: Understanding State

## What is State?
State is a built-in React feature that allows components to manage and store dynamic data. Unlike props, state is **mutable** and can change over time, making it essential for interactive and dynamic applications.

### Why Use State?
- **Stores Dynamic Data**: Keeps track of user inputs, UI changes, and data updates.
- **Triggers Re-Renders**: When state updates, React automatically re-renders the component.
- **Encapsulated in Components**: Each component can manage its own state independently.

## Using `useState`
React provides the `useState` hook to manage state in functional components.

### Example:
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

## Props vs. State
Both **props** and **state** are essential for managing data in React, but they serve different purposes.

| Feature      | Props | State |
|-------------|-------|-------|
| **Definition** | Props (short for properties) are passed from a parent component to a child component. | State is managed within a component and can change over time. |
| **Mutability** | Immutable – cannot be modified by the child component. | Mutable – can be updated using `useState` or `setState`. |
| **Who Controls It?** | Controlled by the parent component. | Controlled by the component itself. |
| **Use Case** | Used to pass static or dynamic data to child components. | Used to store and update dynamic values like user inputs and component changes. |
| **Re-Renders?** | Changing props will re-render the component. | Updating state will re-render the component. |

### Example: Props vs. State
```jsx
import React, { useState } from "react";

function ChildComponent({ message }) {
    return <p>Message from Parent: {message}</p>;
}

function ParentComponent() {
    const [text, setText] = useState("Hello, World!");

    return (
        <div>
            <ChildComponent message={text} />
            <button onClick={() => setText("Hello, React!")}>Change Text</button>
        </div>
    );
}
```


## When to Use Props vs. State?
- **Use Props** when passing data **from a parent component** to a child component.
- **Use State** when data **belongs to a component** and changes over time.

## Summary
- **State stores mutable data in a component.**
- **The `useState` hook is used to declare and update state.**
- **Props are immutable, while state is mutable.**
- **Props are controlled by parent components, while state is controlled by the component itself.**
- **State updates trigger re-renders of the component.**


