# React and Axios: Data Fetching and Displaying

React is a popular JavaScript library for building user interfaces, while Axios is a promise-based HTTP client used for fetching and sending data. Together, they allow developers to build dynamic and data-driven web applications. This tutorial will cover how to install and set up Axios in a React project, how to fetch data from an external API, and how to display the fetched data.

![React and Axios](React-Axios.webp)

Image Source: Dall-E by OpenAI

- [React and Axios: Data Fetching and Displaying](#react-and-axios-data-fetching-and-displaying)
  - [Learning Outcomes](#learning-outcomes)
  - [Prerequisites](#prerequisites)
  - [Step 1: Setting Up the Project](#step-1-setting-up-the-project)
    - [1.1. Creating a React Project](#11-creating-a-react-project)
    - [1.2. Installing the Axios Module](#12-installing-the-axios-module)
  - [Step 2: Fetching Data Using Axios](#step-2-fetching-data-using-axios)
    - [2.1. Creating the Component](#21-creating-the-component)
      - [Example: `UserList.js`](#example-userlistjs)
    - [Explanation](#explanation)
    - [2.2. Adding the Component to the App](#22-adding-the-component-to-the-app)
      - [Example: `App.js`](#example-appjs)
  - [Step 3: Error Handling and Best Practices](#step-3-error-handling-and-best-practices)
    - [3.1. Error Handling](#31-error-handling)
    - [3.2. Loading State](#32-loading-state)
    - [3.3. Best Practices](#33-best-practices)
  - [Additional Example: Parameterized Query](#additional-example-parameterized-query)
    - [4.1. Creating the Component](#41-creating-the-component)
      - [Example: `UserDetail.js`](#example-userdetailjs)
    - [4.2. Using the Component](#42-using-the-component)
      - [Example: `App.js`](#example-appjs-1)
      - [Example: `UserList.js` (modified)](#example-userlistjs-modified)

## Learning Outcomes

By the end of this tutorial, learners should be able to:

- Install and set up the Axios module in a React project;
- Fetch data from an external API using Axios;
- Display the fetched data in React components;
- Handle potential errors when fetching and displaying data.

## Prerequisites

- Node.js and npm are installed on your computer.
- Basic knowledge of React components and state management.

## Step 1: Setting Up the Project

### 1.1. Creating a React Project

If you do not already have a React project, create a new project using the Create React App tool.

```bash
npx create-react-app myapp
cd myapp
```

### 1.2. Installing the Axios Module

Install the Axios module to handle HTTP requests.

```bash
npm install axios
```

## Step 2: Fetching Data Using Axios

### 2.1. Creating the Component

Create a new component to fetch and display the data.

#### Example: `UserList.js`

```javascript
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function UserList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        setUsers(response.data);
        setLoading(false);
      })
      .catch(error => {
        setError(error);
        setLoading(false);
      });
  }, []);

  if (loading) {
    return <p>Loading...</p>;
  }

  if (error) {
    return <p>Error: {error.message}</p>;
  }

  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map(user => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;

```

### Explanation

- **useState**: We use state to manage the user data, loading state, and errors.
- **useEffect**: We fetch the data from the API when the component is mounted.
- **axios.get**: Makes an HTTP request to the external API  `https://jsonplaceholder.typicode.com/users`.
- **setUsers**: Updates the state with the fetched user data.
- **setLoading**: Updates the state with the fetched user data.
- **setError**: Updates the state with the fetched user data.

### 2.2. Adding the Component to the App

Modify the  `App.js` file to render the `UserList` component.

#### Example: `App.js`

```javascript
import React from 'react';
import UserList from './UserList';

function App() {
  return (
    <div className="App">
      <UserList />
    </div>
  );
}

export default App;
```

## Step 3: Error Handling and Best Practices

### 3.1. Error Handling

The code already shows how to handle errors when fetching data. If the request fails, the error state is updated, and an error message is displayed.

```javascript
if (error) {
  return <p>Error: {error.message}</p>;
}
```

### 3.2. Loading State

It is important to handle the loading state to inform the user that data is still being fetched.

```javascript
if (loading) {
  return <p>Loading...</p>;
}
```

### 3.3. Best Practices

- **Use `useEffect` Hook**: Data fetching should be done using the useEffect hook so that the request is made when the component is mounted.
- **Error Boundaries**: Use error boundary components to catch errors in components.
- **Abstraction**:  Abstract API calls into separate files or services to keep the code clean and reusable.
- 
## Additional Example: Parameterized Query

Here’s an additional example where we fetch data with a parameter.

### 4.1. Creating the Component

Create a component that fetches data for a specific user based on the user ID.

#### Example: `UserDetail.js`

```javascript
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function UserDetail({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get(`https://jsonplaceholder.typicode.com/users/${userId}`)
      .then(response => {
        setUser(response.data);
        setLoading(false);
      })
      .catch(error => {
        setError(error);
        setLoading(false);
      });
  }, [userId]);

  if (loading) {
    return <p>Loading...</p>;
  }

  if (error) {
    return <p>Error: {error.message}</p>;
  }

  return (
    <div>
      <h1>{user.name}</h1>
      <p>Email: {user.email}</p>
      <p>Phone: {user.phone}</p>
    </div>
  );
}

export default UserDetail;
```

### 4.2. Using the Component

Modify the `App.js` file to display the `UserDetail` component when a user is selected.

#### Example: `App.js`

```javascript
import React, { useState } from 'react';
import UserList from './UserList';
import UserDetail from './UserDetail';

function App() {
  const [selectedUserId, setSelectedUserId] = useState(null);

  return (
    <div className="App">
      <UserList onSelectUser={setSelectedUserId} />
      {selectedUserId && <UserDetail userId={selectedUserId} />}
    </div>
  );
}

export default App;
```

#### Example: `UserList.js` (modified)

```jsx
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function UserList({ onSelectUser }) {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        setUsers(response.data);
        setLoading(false);
      })
      .catch(error => {
        setError(error);
        setLoading(false);
      });
  }, []);

  if (loading) {
    return <p>Loading...</p>;
  }

  if (error) {
    return <p>Error: {error.message}</p>;
  }

  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map(user => (
          <li key={user.id} onClick={() => onSelectUser(user.id)}>
            {user.name}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;
```
