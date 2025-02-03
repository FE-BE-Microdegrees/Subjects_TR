# React Components

## Introduction

React is a popular JavaScript library used for building user interfaces. The fundamental concept and building block of React is the component. Components allow developers to divide the user interface into small, reusable pieces, making development and maintenance easier.

## Learning Outcomes

By the end of this material, learners should be able to:

- Explain what a React component is and why it is important.
- Create and use different types of components (functional and class-based).
- Use props and state for communication and dynamic data management between components.

## What is a React Component?

A component is an independent and reusable piece of code that defines part of the user interface. Each component can include HTML, JavaScript, and CSS. There are two types of components in React: functional and class-based components.

### Functional Components

Functional components are JavaScript functions that take props as input and return React elements.

#### Example: Functional Component

```javascript
import React from 'react';

function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}

export default Welcome;
```

### Class-Based Components
Class-based components are JavaScript classes that extend the `React.Component` class. These components can have their own state and lifecycle methods.

#### Example: Class-Based Component

```javascript
import React, { Component } from 'react';

class Welcome extends Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

export default Welcome;
```

## Props

Props (short for "properties") are data passed to components. Props allow components to receive data from their parent components and display it.

### Example: Using Props

```javascript
import React from 'react';
import Welcome from './Welcome';

function App() {
  return (
    <div>
      <Welcome name="Alice" />
      <Welcome name="Bob" />
      <Welcome name="Charlie" />
    </div>
  );
}

export default App;
```

In this example, the `Welcome` component receives the `name` prop, which is used to display a greeting message.

## State

State is the internal data model of components that can change over time. Changing the state triggers a re-render of the component to reflect the changes in the user interface.

### Example: Using State in a Class-Based Component

```javascript
import React, { Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}

export default Counter;
```

### Example: Using State in a Functional Component (Hooks)

React hooks (`useState`, `useEffect` etc) enable functional components to use state and other React features.

```javascript
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

export default Counter;
```

## Component Composition

Component composition means combining smaller components to create larger, more complex components. This approach promotes reusability and simplifies code maintenance.


### Example: Component Composition

```javascript
import React from 'react';

function Header() {
  return <header><h1>My App</h1></header>;
}

function Footer() {
  return <footer><p>© 2024 My App</p></footer>;
}

function Main() {
  return <main><p>Welcome to my app!</p></main>;
}

function App() {
  return (
    <div>
      <Header />
      <Main />
      <Footer />
    </div>
  );
}

export default App;
```

## Lifecycle Methods

Lifecycle methods are special methods that allow components to perform actions at specific points during their lifetime. These are mainly used in class-based components.

### Key Lifecycle Methods

1. **componentDidMount**: Invoked after the component is mounted for the first time.
2. **componentDidUpdate**: Invoked after the component's state or props have changed.
3. **componentWillUnmount**: Invoked right before the component is removed from the DOM.

#### Example: Using Lifecycle Methods

```javascript
import React, { Component } from 'react';

class LifecycleDemo extends Component {
  componentDidMount() {
    console.log('Component mounted');
  }

  componentDidUpdate(prevProps, prevState) {
    console.log('Component updated');
  }

  componentWillUnmount() {
    console.log('Component will unmount');
  }

  render() {
    return <div>Lifecycle Demo</div>;
  }
}

export default LifecycleDemo;
```
