# Conditional Rendering in React

Conditional rendering is a technique used to display or hide components or parts of a component based on specific conditions. It allows dynamic changes to the user interface based on state or props. This material explores various ways to implement conditional rendering in React, focusing on functional components.

![React Conditional Rendering](React-Conditional.webp)

Image Source: Dall-E by OpenAI

- [Conditional Rendering in React](#conditional-rendering-in-react)
  - [Learning Outcomes](#learning-outcomes)
  - [Techniques for Conditional Rendering](#techniques-for-conditional-rendering)
    - [`if` Statement](#if-statement)
      - [Example: `if` Statement](#example-if-statement)
    - [Logical `&&` Operator](#logical--operator)
      - [Example: Logical `&&` Operator](#example-logical--operator)
    - [Ternary Operator](#ternary-operator)
      - [Example: Ternary Operator](#example-ternary-operator)
    - [Direct Return with Conditions](#direct-return-with-conditions)
      - [Example: Conditional Return](#example-conditional-return)
  - [Additional Examples](#additional-examples)
    - [Example: Conditional Rendering with State](#example-conditional-rendering-with-state)
      - [Example: `LoginControl.js`](#example-logincontroljs)
    - [Example: Checking Multiple Conditions](#example-checking-multiple-conditions)
      - [Example: Handling Multiple Conditions](#example-handling-multiple-conditions)
    - [Example: Hiding Elements](#example-hiding-elements)
      - [Example: Hiding Elements](#example-hiding-elements-1)

## Learning Outcomes

By the end of this material, learners should be able to:

- Explain what conditional rendering is and why it is used.
- Use various techniques for conditional rendering, such as `if` statements, logical `&&` operators, and ternary operators.
- Implement conditional rendering in practical examples using functional components.

## Techniques for Conditional Rendering

### `if` Statement

The classic way to achieve conditional rendering is to use an `if` statement. This is typically used within the render function.

#### Example: `if` Statement

```javascript
import React from 'react';

function UserGreeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign up.</h1>;
}

export default UserGreeting;
```

### Logical  `&&` Operator

The logical  `&&` operator can be used when you want to render a component only if a condition is true. If the condition is false, nothing is rendered.

#### Example: Logicale `&&` Operator

```javascript
import React from 'react';

function Mailbox({ unreadMessages }) {
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>You have {unreadMessages.length} unread messages.</h2>
      }
    </div>
  );
}

export default Mailbox;
```

### Ternary Operator

The ternary operator (`? :`)  is a compact way to perform conditional rendering, allowing you to render one of two components depending on a condition.

#### Example: Ternary Operator

```javascript
import React from 'react';

function Greeting({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? (
        <h1>Welcome back!</h1>
      ) : (
        <h1>Please sign up.</h1>
      )}
    </div>
  );
}

export default Greeting;
```

### Direct Return with Conditions

If you want to render components directly in a function, you can use conditional logic for immediate returns.

#### Example: Conditional Return

```javascript
import React from 'react';

function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign up.</h1>;
}

export default Greeting;
```

## Additional Examples

### Example: Conditional Rendering with State

Using React state, you can control whether a user is logged in or not and display appropriate greeting messages.

#### Example: `LoginControl.js`

```javascript
import React, { useState } from 'react';

function LoginControl() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  const handleLoginClick = () => {
    setIsLoggedIn(true);
  };

  const handleLogoutClick = () => {
    setIsLoggedIn(false);
  };

  return (
    <div>
      <Greeting isLoggedIn={isLoggedIn} />
      {isLoggedIn ? (
        <button onClick={handleLogoutClick}>Logout</button>
      ) : (
        <button onClick={handleLoginClick}>Login</button>
      )}
    </div>
  );
}

function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign up.</h1>;
}

export default LoginControl;
```

### Example: Checking Multiple Conditions

When you need to check multiple conditions, you can combine different conditional rendering techniques.

#### Example: Handling Multiple Conditions

```javascript
import React from 'react';

function StatusMessage({ isOnline, hasMessages }) {
  if (!isOnline) {
    return <p>User is offline.</p>;
  }

  return (
    <div>
      <p>User is online.</p>
      {hasMessages ? (
        <p>You have new messages.</p>
      ) : (
        <p>No new messages.</p>
      )}
    </div>
  );
}

export default StatusMessage;
```

### Example: Hiding Elements

Conditional rendering can also be used to hide elements by excluding them from the DOM.

#### Example: Hiding Elements

```javascript
import React, { useState } from 'react';

function WarningBanner({ warn }) {
  if (!warn) {
    return null;
  }

  return (
    <div className="warning">
      Warning!
    </div>
  );
}

function Page() {
  const [showWarning, setShowWarning] = useState(true);

  const handleToggleClick = () => {
    setShowWarning(prevShowWarning => !prevShowWarning);
  };

  return (
    <div>
      <WarningBanner warn={showWarning} />
      <button onClick={handleToggleClick}>
        {showWarning ? 'Hide' : 'Show'} Warning
      </button>
    </div>
  );
}

export default Page;
```
