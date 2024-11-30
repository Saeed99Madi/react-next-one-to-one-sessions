# React Component Lifecycle: Mounting, Updating, and Unmounting

React, a popular JavaScript library for building user interfaces, revolves around the concept of components. These components have a lifecycle that can be divided into three primary phases: Mounting, Updating, and Unmounting. In this blog, we’ll explore these phases and the lifecycle methods associated with them using examples of both Class and Functional Components in React.
![HTML Conversion Exercise](https://miro.medium.com/v2/resize:fit:720/format:webp/1*WjIdhcGpij-66kNtBu5ZiQ.jpeg)

## 3 Phases of a Component Lifecycle

### 1. Mounting

The Mounting phase signifies the time when a component is first created and inserted into the Document Object Model (DOM). It involves setting up the initial state, rendering the component, and performing any side-effects related to the component’s mounting.

### 2. Updating

The Updating phase occurs when a component receives new props or its state changes. This phase is responsible for rendering updates, re-evaluating the component’s UI, and handling any side-effects associated with these updates.

### 3. Unmounting

The Unmounting phase happens when a component is removed from the DOM. This is where you can clean up any resources or subscriptions to prevent memory leaks.

## Class Component Lifecycle

Let’s explore the Class Component lifecycle methods and their role in these phases.

### `constructor` Method

The constructor method is rarely used in modern React. It is used to initialize the component's state and bind methods. State initialization is now typically done outside the constructor using class properties.

### `componentDidMount` Method

`componentDidMount` is called after the component is inserted into the DOM. It's a suitable place to perform tasks like data fetching, setting up event listeners, or initializing third-party libraries.

### `componentDidUpdate` Method

`componentDidUpdate` is called after a render update. It's useful for performing actions based on changes to props or state, such as updating the UI or making additional data requests.

### `componentWillUnmount` Method

`componentWillUnmount` is called before the component is removed from the DOM. Here, you should clean up any resources like event listeners or subscriptions to avoid memory leaks.

### `render` Method

The `render` method defines the component's UI and is called every time the component mounts or updates. It returns the JSX that will be rendered to the DOM.

### Example: Simple Counter using Class Component

```jsx
import React from "react";

class CounterClass extends React.Component {
  constructor(props) {
    super(props);
    // Initialize state
    this.state = { count: 0 };
  }

  // componentDidMount is called after the component is inserted into the DOM
  componentDidMount() {
    console.log("Component mounted");
  }

  // componentDidUpdate is called after a render update
  componentDidUpdate() {
    console.log("Component updated");
  }

  // componentWillUnmount is called before the component is removed from the DOM
  componentWillUnmount() {
    console.log("Component unmounted");
  }

  // Function to increment the count
  increment = () => {
    this.setState((prevState) => ({ count: prevState.count + 1 }));
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}

export default CounterClass;
```

## Functional Component Lifecycle

Functional Components, introduced with React Hooks, also have their lifecycle management using hooks. Let’s look at how these hooks correspond to the lifecycle phases.

### `useState` Hook

The `useState` hook is used to initialize and manage state in Functional Components. It's equivalent to the constructor in Class Components, where you set the initial state.

### `useEffect` Hook

`useEffect` is the swiss army knife of Functional Component lifecycle management. It handles component lifecycle events, including rendering (updating) and cleanup (unmounting).

### Example: Simple Counter using Functional Component

```jsx
import React, { useState, useEffect } from "react";

function CounterFunctional() {
  // Initialize state using the useState hook (equivalent to constructor)
  const [count, setCount] = useState(0);

  // useEffect hook for component lifecycle
  useEffect(() => {
    // Effect runs after every render (equivalent to componentDidUpdate)
    console.log("Component rendered");

    // Cleanup effect (equivalent to componentWillUnmount)
    return () => {
      console.log("Component unmounted");
    };
  }, []);

  // Function to increment the count
  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

export default CounterFunctional;
```

## Conclusion

Understanding the component lifecycle is crucial for building robust React applications. Whether you prefer Class Components or Functional Components with hooks, React provides powerful tools to manage the lifecycles of your components effectively. Choose the approach that fits your project’s needs and keep these lifecycle phases and methods in mind as you build your next React application. Happy coding!

---

React offers two types of components, and understanding both is key to mastering the library:

- [**Class vs Functional Components**](https://www.freecodecamp.org/news/react-functional-components-vs-class-components/)  
  An article explaining the difference between class and functional components, and when to use each.

- [**React Components Docs**](https://reactjs.org/docs/react-component.html)  
  Official React documentation covering both class and functional components.

---
