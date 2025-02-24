# Chapter 10: Understanding React Context API

## What is the React Context API?
The **React Context API** is a built-in feature in React that allows **state and data to be shared across multiple components** without the need for **prop drilling**.

### **Why Use Context API?**
- **Avoids Prop Drilling**: No need to pass props manually through multiple nested components.
- **Global State Management**: Easily manage global data like themes, authentication, and user preferences.
- **Better Code Organization**: Centralized state improves maintainability.
- **Works with Hooks**: Can be combined with `useState` and `useReducer` for better state management.

## **How Context API Works**
The Context API has three main parts:
1. **`React.createContext()`** → Creates a new context.
2. **`Provider`** → Supplies the state/data to components.
3. **`Consumer` or `useContext()`** → Accesses the context data in components.

### **Step-by-Step Example of Context API**
#### **1️⃣ Creating a Context**
```jsx
import React, { createContext, useState } from "react";

// Create a new context
const ThemeContext = createContext();

function ThemeProvider({ children }) {
    const [theme, setTheme] = useState("light");

    return (
        <ThemeContext.Provider value={{ theme, setTheme }}>
            {children}
        </ThemeContext.Provider>
    );
}

export { ThemeContext, ThemeProvider };
```
✅ **`ThemeContext`** holds the context data.  
✅ **`ThemeProvider`** wraps components that need access to the theme.

#### **2️⃣ Using the Context in Components**
```jsx
import React, { useContext } from "react";
import { ThemeContext } from "./ThemeContext";

function ThemeToggler() {
    const { theme, setTheme } = useContext(ThemeContext);

    return (
        <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>
            Toggle Theme (Current: {theme})
        </button>
    );
}
```
✅ **`useContext(ThemeContext)`** allows access to the theme value and function.
✅ Clicking the button toggles the theme between `"light"` and `"dark"`.

#### **3️⃣ Wrapping the Application with the Provider**
```jsx
import React from "react";
import { ThemeProvider } from "./ThemeContext";
import ThemeToggler from "./ThemeToggler";

function App() {
    return (
        <ThemeProvider>
            <ThemeToggler />
        </ThemeProvider>
    );
}

export default App;
```
✅ **`ThemeProvider`** wraps the entire app so all components can access the theme.

## **When to Use Context API?**
- **For Global State**: Managing authentication, user preferences, and themes.
- **When Avoiding Prop Drilling**: No need to pass props manually through multiple nested components.
- **When Data is Needed Across Multiple Components**: Centralized state is more efficient.

## **Context API vs. Other State Management Solutions**
| Feature | Context API | Redux | useState/useReducer |
|---------|------------|--------|------------------|
| **Best For** | Small to Medium State | Large-Scale Apps | Local Component State |
| **Prop Drilling Solution** | ✅ Yes | ✅ Yes | ❌ No |
| **Performance Overhead** | Low | High | Low |
| **Setup Complexity** | Easy | Complex | Easy |

## **Summary**
- **Context API provides a way to manage global state in React.**
- **It avoids prop drilling by making data available globally.**
- **It consists of `createContext()`, `Provider`, and `useContext()`.**
- **Useful for themes, authentication, and shared global state.**

In the next chapter, we will explore **React Performance Optimization**, including techniques like memoization and lazy loading.

