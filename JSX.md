# Chapter 2: Understanding JSX

What is JSX?

JSX (JavaScript XML) is a syntax extension for JavaScript used in React. It allows developers to write UI elements using a syntax that closely resembles HTML. JSX makes it easier to describe the structure of a React component within JavaScript code.

Why Use JSX?

Improves Readability: JSX allows developers to visualize the UI structure directly within JavaScript code.

Prevents Injection Attacks: React automatically escapes expressions in JSX to prevent XSS (Cross-Site Scripting) attacks.

Boosts Performance: JSX is compiled into efficient JavaScript code before execution.

Writing JSX

A basic JSX expression looks like HTML but is written inside JavaScript:

const element = <h1>Hello, World!</h1>;

This JSX syntax gets converted into JavaScript behind the scenes:

const element = React.createElement("h1", null, "Hello, World!");

JSX Rules and Best Practices

Only One Parent Element: JSX must be wrapped in a single parent element.

return (
    <div>
        <h1>Hello</h1>
        <p>Welcome to React!</p>
    </div>
);

Embedding JavaScript Expressions: Use {} to insert JavaScript expressions inside JSX.

const name = "Alice";
const element = <h1>Hello, {name}!</h1>;

Using ClassName Instead of Class: Since class is a reserved keyword in JavaScript, use className instead.

<div className="container">Welcome</div>

Self-Closing Tags: Elements without children should be self-closed.

<img src="logo.png" alt="Logo" />

JavaScript Functions in JSX: You can use JavaScript functions inside JSX expressions.

function getGreeting(user) {
    return <h1>Hello, {user.name}!</h1>;
}

Summary

JSX is a syntax extension that allows writing HTML-like elements inside JavaScript.

It enhances readability and prevents security vulnerabilities.

JSX expressions must have a single parent element and use {} for embedding JavaScript.

React automatically converts JSX into JavaScript before rendering.

In the next chapter, we will dive deeper into Props, which allow components to receive and use dynamic data.
