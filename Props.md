# Chapter 3: Understanding Props

What are Props?

Props (short for properties) are a mechanism in React that allows components to receive data from their parent components. They enable components to be dynamic and reusable by passing different values.

Why Use Props?

Reusability: The same component can be used with different data.

Data Flow: Props allow parent components to pass data to child components.

Customization: Components can be customized based on prop values.

How to Use Props

Props are passed as attributes to components and accessed inside the component using the props object.

Example 1: Passing Props to a Functional Component

function Greeting(props) {
    return <h1>Hello, {props.name}!</h1>;
}

function App() {
    return (
        <div>
            <Greeting name="Alice" />
            <Greeting name="Bob" />
        </div>
    );
}

Greeting component receives name as a prop.

It dynamically renders a personalized greeting based on the name prop.

Example 2: Using Props with Default Values

Props can have default values using default parameters or defaultProps.

function Greeting({ name = "Guest" }) {
    return <h1>Hello, {name}!</h1>;
}

OR

Greeting.defaultProps = {
    name: "Guest"
};

If no name prop is provided, it defaults to "Guest".

Example 3: Passing Multiple Props

Props can contain multiple values, including strings, numbers, and objects.

function UserCard({ name, age }) {
    return <p>{name} is {age} years old.</p>;
}

function App() {
    return <UserCard name="Alice" age={25} />;
}

Example 4: Passing Functions as Props

Props can also pass functions to handle events.

function Button({ onClick }) {
    return <button onClick={onClick}>Click Me</button>;
}

function App() {
    const handleClick = () => alert("Button Clicked!");
    return <Button onClick={handleClick} />;
}

The Button component receives an onClick function as a prop.

The App component passes a function to handle the click event.

Summary

Props allow components to receive dynamic data from parent components.

They help create reusable and customizable components.

Props can pass strings, numbers, objects, functions, and even components.

They are read-only (components should not modify their props).

