### 1.What is the difference between var, let, and const in JavaScript?
 These 3 are Keywords used for variable declartion.They have distinct differences in terms of scope, hoisting, and mutability.
# LET
* Scope: let is block-scoped. It means that it is only accessible within the block where it is defined.

* You can re-declare a variable using var without any issues.

 Eg:
```jsx

let a = 5;
console.log(a)

function Letfunction() {
  let b = 10;
  if (b) {
    let b = 20
    console.log(b)
  }
  console.log(b)
}

Letfunction();

```
# VAR
* Scope: var is function-scoped. It means that if a var is defined within a function, it is only accessible within that function. If defined outside any function, it has a global scope.

* You can re-declare a variable using var without any issues.

 Eg:
``` jsx
var a = 5;
console.log(a)

function Varfunction() {
  var b = 10;
  if (b) {
    var b = 20
    console.log(b)
  }
  console.log(b)
}

Varfunction();
```
# CONST
* Scope: const is block-scoped, similar to let.
* You cannot re-declare a variable using const within the same scope.

### 2. How do you create a new React component?
* There are 2 types to declare react components
# Functional Component
Example:

```jsx
import React from 'react';
function MyComponent() {
  return (
    <div>
      <h1>Hello, World!</h1>
      <p>This is a functional component.</p>
    </div>
  );
}
export default MyComponent;
```
# Using Class Component
```jsx
import React, { Component } from 'react';

class MyClassComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      message: 'Hello from class component!'
    };
  }

  handleClick = () => {
    this.setState({ message: 'State updated!' });
  };

  render() {
    return (
      <div>
        <p>{this.state.message}</p>
        <button onClick={this.handleClick}>Update Message</button>
      </div>
    );
  }
}

export default MyClassComponent;
```
### 3. What is the purpose of the render() method in a React component?

* The render() method is a crucial part of a class-based React component. It is responsible for describing the UI of the component by returning a React element, which can be a single element or a tree of elements created using JSX.

* Whenever the component's state or props change, the render() method is called again to update the UI accordingly.

* render() method outputs the React elements that make up the component's UI. These elements are then converted into DOM nodes by React.

### 4. How do you handle state changes in a React component?

```jsx
import React, { useState } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default MyComponent;
```
### 5. What is the difference between a controlled and uncontrolled component in React?
 Controled Component
* State Management: Form data is handled by React state.
* Value: The value of the input is controlled by the component's state.
* Updates: Changes to the input update the state, which then updates the input value.

UnControled Component

* State Management: Form data is handled by the DOM.
* Value: The value of the input is managed by the DOM, not by React state.
* Access: Use ref to access the input value directly from the DOM.

### 6.How do you pass props to a React component?

React components use props to communicate and share data with each other. Every parent component can pass some information to its child components by giving them props.
* Props are arguments passed into React components.
* Props are known as properties in React, which are used to pass data and event handlers from one component to another.
 
 ### Passing props to a React component: 
1.Define the Child Component to Receive Props:
* First, create a child component that expects to receive props.

2.Pass Props from the Parent Component:
* In the parent component, you pass the props to the child component by adding attributes to the child component element.

3.Use Props in Child:
* Access and use the props inside the child component to render or perform actions based on the props.

```jsx
import React from 'react';

function Func(props) {
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return <Greeting name="Bharani" />;
}

export default App;
```

### 7. What is the purpose of the key prop in a React component?
* The key prop is a unique identifier that React uses to efficiently manage and update elements within a list.
* The key prop helps React identify which items in a list have changed, been added, or removed. It is crucial for optimizing rendering performance and ensuring that components maintain their state correctly.

* Uniqueness: Each key must be unique among siblings to help React distinguish between elements.

* Performance: Helps React quickly determine which items need to be updated by comparing keys.

* State Preservation: Ensures that components maintain their state correctly when items are reordered or modified.

```jsx
 <ul>
    {items.map((item, index) => (
    <ListItem key={index} item={item} />
    ))}
</ul>
```

### 8. How do you handle events in a React component?
Events are actions or occurrences that happen in the browser and can be handled using JavaScript. 

### Handling Events in React:
1.Define an Event Handler:
 * Create a function that specifies what should happen when the event occurs.

2.Attach the Event Handler:
 * Use JSX to attach the event handler function to an element via an event attribute (e.g., onClick, onChange).

3.Manage state to reflect changes triggered by events.

```jsx
import React, { useState } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
}

export default MyComponent;
```

### 9. What is the difference between a functional component and a class component in React?
Functional Components:

* These are simpler and are written as JavaScript functions.
* They take props as an argument and return JSX.
* Before Hooks, they were considered stateless and hence were slightly more performant due to less overhead.
* Syntax: Simpler and less verbose.
* Performance: Generally more performant due to less overhead compared to class components.

Class Components:
* These are more complex and are written as ES6 classes.
* They extend from React.Component and must have a render method that returns JSX.
* Historically used for stateful components before the advent of Hooks.
* Syntax: More verbose, requiring constructor for state initialization and binding methods if necessary.
* Performance: May have slightly more overhead compared to functional components.


 ### 10. How do you use React Hooks?
React Hooks are functions that let you use state and other React features in functional components. 

These functions enable you to use state and side effects in functional components. 
 ### 1. useState:
It Manages the state in a functional component.
Eg:
```jsx
import React, { useState } from 'react';
function Example() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```
### 2. useEffect:
Perform side effects in your component, like fetching data, directly manipulating the DOM.
Eg:
```jsx
import React, { useState, useEffect } from 'react';
function Example() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    console.log(`You clicked ${count} times`);
    return () => {
      console.log('Cleanup');
    };
  }, [count]); 

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```
### useContext : 
Accesses context values without needing a context consumer.
```jsx
import React, { useContext } from 'react';

const ThemeContext = React.createContext('light');

function ThemedComponent() {
  const theme = useContext(ThemeContext);

  return <div>The current theme is {theme}</div>;
}
```
### 11. What is the purpose of the useEffect() hook in React? 
The useEffect hook in React is used to perform side effects in functional components.

The useEffect takes two arguments:

1.A function that contains the side effect logic.

2.An optional array of dependencies.

### Purposes of useEffect:
- 1.Data Fetching
- 2.Subscribing and Unsubscribing
- 3.Updating the DOM

```jsx
import React, { useState, useEffect } from 'react';

function Example() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, [])

  return <div>{data ? `Data: ${data}` : 'Loading...'}</div>;
}

```

### 12. How do you fetch data from an API in a React component?
Fetching data from an API in a React component can be done using the useEffect hook along with the fetch API.

**1.Set up State:**
Use useState() is to manage the state where the fetched data will be stored.

**2.Use useEffect:**
Use the useEffect() hook to fetch data when the component mounts.

**3.Fetch Data:**
Use the fetch API to get data from the server.
Update the state with the fetched data.
Handle any potential errors.

```jsx
import React, { useState, useEffect } from 'react';

function FetchData() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://dummyjson.com/quotes/random')
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json();
      })
      .then(data => {
        setData(data);
        setLoading(false);
      })
      .catch(error => {
        setError(error);
        setLoading(false);
      });
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <div>
      <h1>Data:</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

export default FetchData;
```

# 13. What is the purpose of the useContext() hook in React?
A)The useContext hook in React is used to access the context values provided by a Context.Provider in a functional component.
- useContext : Accesses context values without needing a context consumer.

The useContext() hook in React allows you to consume values from a React context. 

```jsx
import React, { useContext } from 'react';

const ThemeContext = React.createContext('light');

function ThemedComponent() {
  const theme = useContext(ThemeContext);

  return <div>The current theme is {theme}</div>;
}
```

### Purpose of useContext():
**1.Avoid Prop Drilling:** It allows developers to easily share data across multiple components without the need for prop drilling.

**2.Improve Component Reusability**:By using context, you can create components that are more self-contained and reusable.

**3.Share Global State**:Context is often used to share data that needs to be accessible across multiple components.

## 14. How do you use React Router for client-side routing?
A)React Router is a popular library for handling client-side routing in React applications.
 It allows you to create single-page applications with navigation without having to refresh the page.

### Steps to Implement React Router
Step 1: Create a react app by using the following command.

```jsx
npx create-react-app routing
cd routing
```
Step 2: Install the required dependencies.

```jsx
npm install react-router-dom
```
3.Set Up the Router:

Use the BrowserRouter component to wrap your application. This component will keep your UI in sync with the URL.

4. Create Route Components:

Create separate component files for each route (e.g., Home, About, Contact).

```jsx
import React from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';

function Home() {
  return <h2>Home Page</h2>;
}

function About() {
  return <h2>About Page</h2>;
}

function Contact() {
  return <h2>Contact Page</h2>;
}

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/contact">Contact</a></li>
          </ul>
        </nav>

        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;
```



### 15. What is the difference between useState() and useReducer() in React?
In React, useState and useReducer are both hooks that help manage state in functional components,
 but they are used in different scenarios and have distinct differences.


**useState:**

- To manage simple state logic.
- we can directly update the state value using the setter function returned by useState.
- Suitable for most basic state management needs.

```jsx
import React, { useState } from 'react';

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

**useReducer:**

- To manage more complex state logic and interactions.

- You have to dispatch actions to update the state, and a reducer function handles how the state should change based on the action type.

- Makes it easier to see how state transitions happen in response to actions.

### 16. How do you optimize the performance of a React application?

Optimizing the performance of a React application involves various strategies and best practices to ensure your app runs efficiently and smoothly.

**1. Use React.memo():**

Prevents unnecessary re-renders of functional components by memoizing them.

**2. Use useCallback and useMemo:**

Prevents the creation of new function and object instances on every render.

**3. Code Splitting:**

Splits your code into smaller chunks, loading only the necessary code for the current page.

**4.List visualization:**

List visualization, or windowing, involves rendering only the items currently visible on the screen.

**5. Optimize Images**

Reduce the load time and improve rendering speed by optimizing images.

**6. Minimize and Bundle Assets:**

Reduce the size of your JavaScript, CSS, and other assets.

### 17. What is the purpose of the shouldComponentUpdate() method in a React component?###
- The shouldComponentUpdate() method in a React class component is used to control whether a component should re-render when its props or state change.

- If a component's output is not affected by the current change in state or props.

- Usage: Useful for optimizing performance in scenarios where rendering is expensive and updates are frequent.

### Purpose of shouldComponentUpdate()
**1.Optimize Performance:**

It will optimizes the performance of your React apps.

**2.Conditional Rendering:**

We can implement custom logic to decide if the component should re-render based on changes to props or state.


### 18. Using React DevTools for Debugging

React DevTools is a powerful tool for inspecting and debugging React applications. It provides a way to inspect the component tree, analyze component props and state, and debug performance issues.

### Installation

1. Browser Extension:
 Install React DevTools as a browser extension for Chrome or Firefox.

 -  Chrome Extension
 -  Firefox Add-on

2.Standalone Application: Alternatively, you can install it as a standalone application via npm for use with any browser.

```jsx
npm install -g react-devtools
```

# Key Features
### 1. Component Tree Inspection

- View Component Hierarchy: Inspect the hierarchical structure of your React components.
- Select Components: Click on any component in the tree to see its props, state, and context.

### 2. Props and State Analysis

- Inspect Props: View the current props of a selected component.
- Inspect State: View the local state of a selected component.
- Edit State and Props: Temporarily modify props and state to test changes in real-time.

### 3. Profiler

- Record Performance: Use the Profiler tab to record and analyze component rendering performance.
- View Rendering Time: Identify which components are re-rendering and how long they take.

### 4. Highlight Updates
- Visualize Updates: Enable highlighting to see which components are updating on each render.

### Example Workflow

- Open DevTools: Open the React DevTools from your browser's DevTools panel or as a standalone application.
- Inspect Components: Navigate the component tree to select components and inspect their props, state, and context.
- Analyze Performance: Use the Profiler to record and analyze rendering performance to optimize slow components.
- Edit and Test: Modify props and state in the DevTools to test how changes affect your application.

### 19. Difference Between Higher-Order Components (HOCs) and Render Props Pattern in React

Both Higher-Order Components (HOCs) and the Render Props pattern are techniques in React used to share logic between components. They serve similar purposes but have different implementations and use cases.

### Higher-Order Components (HOCs)
- Definition: A Higher-Order Component is a function that takes a component and returns a new component with additional props or behavior. It's a pattern used for code reuse.
- Usage: HOCs are used to inject additional functionality into components without modifying the original component.
# Example

```jsx
import React from 'react';
function withEnhancement(WrappedComponent) {
  return class extends React.Component {
    render() {
      const newProps = { extraProp: 'value' };
      return <WrappedComponent {...this.props} {...newProps} />;
    }
  };
}
function MyComponent(props) {
  return <div>{props.extraProp}</div>;
}
const EnhancedComponent = withEnhancement(MyComponent);

export default EnhancedComponent;
```

### 20. Using React with TypeScript

TypeScript adds static type checking to JavaScript, which can improve development efficiency and code quality in React applications. Here's how you can use React with TypeScript.

## Setup

### 1. Create a TypeScript React Project
 You can create a new React project with TypeScript using Create React App:

```jsx
npx create-react-app my-app --template typescript
```
Alternatively, if you’re adding TypeScript to an existing project, install TypeScript and its type definitions:

```jsx
npm install typescript @types/react @types/react-dom
```

### 2. Configure TypeScript
Add a tsconfig.json file to configure TypeScript. Create React App sets this up automatically, but you can customize it if needed.

### 3. Rename Files
Rename your .js files to .tsx (for files containing JSX) or .ts (for files without JSX).
```jsk
import React from 'react';

interface Props {
  title: string;
  count?: number; 
}

const MyComponent: React.FC<Props> = ({ title, count = 0 }) => {
  return (
    <div>
      <h1>{title}</h1>
      <p>Count: {count}</p>
    </div>
  );
};

export default MyComponent;
```