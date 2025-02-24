
# Chapter 4: Understanding Renders

What Does "Renders" Mean in React.js?

In React, "renders" refers to the process of converting React components into actual DOM elements that appear on the screen.

How Rendering Works

- React Components Return JSXEvery React component returns JSX, which describes what the UI should look like.

- React Converts JSX into JavaScriptJSX is transformed into React.createElement() calls.

- React Updates the Virtual DOMReact first updates the Virtual DOM (an in-memory representation of the real DOM).

- React Compares the Virtual DOM with the Previous VersionIt checks what has changed using a process called Reconciliation.

- React Updates the Real DOM EfficientlyInstead of updating everything, React updates only the necessary parts.

When Does React Re-Render Components?

React re-renders a component when:

- State Changes (useState updates)

- Props Change (Parent component passes new props)

- Context Changes (if using useContext)

- Force Re-Rendering (forceUpdate() in class components)

Example of Re-Rendering with State

```javascript
function Counter() {
    const [count, setCount] = React.useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}

```


Summary

Rendering is the process of React converting components into DOM elements.

React updates the Virtual DOM first, then efficiently updates the actual DOM.

Re-renders happen when state or props change.

React minimizes unnecessary DOM updates to improve performance.


