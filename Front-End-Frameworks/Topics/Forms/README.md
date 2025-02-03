# React Forms and User Input

Forms are a crucial part of web applications, enabling users to input and submit data. In React, form handling differs from traditional DOM-based handling, offering more control and easier synchronization with the component's state. This chapter explores how to create and manage forms in React, work with controlled and uncontrolled components, and implement best practices for handling user input.

![React Forms](React-Forms.webp)

Source: Dall-E by OpenAI

- [React Forms and User Input](#react-forms-and-user-input)
  - [Learning Outcomes](#learning-outcomes)
  - [Controlled and Uncontrolled Components](#controlled-and-uncontrolled-components)
    - [Controlled Components](#controlled-components)
    - [Uncontrolled Components](#uncontrolled-components)
  - [Basics of Form Handling](#basics-of-form-handling)
    - [Event Handling](#event-handling)
    - [Forms with Multiple Inputs](#forms-with-multiple-inputs)
    - [Form Validation](#form-validation)
  - [Best Practices for Form Management](#best-practices-for-form-management)
  - [Practical Example: Complete Form](#practical-example-complete-form)
  - [Sources](#sources)
  - [Questions and Exercises](#questions-and-exercises)
  - [Exercise](#exercise)

---

## Learning Outcomes

By the end of this chapter, you should be able to:

- Create and manage forms in React.
- Work with controlled and uncontrolled components for handling user input.
- Implement event handlers for form and input management.
- Apply best practices for user input handling in React.

---

## Controlled and Uncontrolled Components

### Controlled Components

Controlled components use React state to manage form input values. The form elements' values are stored in the component's state and updated through event handlers.

#### Example: Controlled Component

```javascript
import React, { useState } from 'react';

function ControlledForm() {
  const [name, setName] = useState('');

  function handleChange(event) {
    setName(event.target.value);
  }

  function handleSubmit(event) {
    event.preventDefault();
    alert(`Submitted name: ${name}`);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default ControlledForm;
```

### Uncontrolled Components

Uncontrolled components handle form elements directly in the DOM, using refs to access their values.

#### Example: Uncontrolled Component

```javascript
import React, { useRef } from 'react';

function UncontrolledForm() {
  const nameInput = useRef(null);

  function handleSubmit(event) {
    event.preventDefault();
    alert(`Submitted name: ${nameInput.current.value}`);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" ref={nameInput} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default UncontrolledForm;
```

## Basics of Form Handling

### Event Handling

Event handling involves managing actions like form submission (`onSubmit`) and input changes (`onChange`).

#### Example: Form Event Handling

```javascript
import React, { useState } from 'react';

function FormHandling() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  function handleEmailChange(event) {
    setEmail(event.target.value);
  }

  function handlePasswordChange(event) {
    setPassword(event.target.value);
  }

  function handleSubmit(event) {
    event.preventDefault();
    console.log(`Email: ${email}, Password: ${password}`);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Email:
        <input type="email" value={email} onChange={handleEmailChange} />
      </label>
      <label>
        Password:
        <input type="password" value={password} onChange={handlePasswordChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default FormHandling;
```

### Forms with Multiple Inputs

When handling multiple inputs, use a single event handler and store inputs in the state as an object.

#### Example: Form with Multiple Inputs

```javascript
import React, { useState } from 'react';

function MultiInputForm() {
  const [formData, setFormData] = useState({
    username: '',
    email: '',
    password: ''
  });

  function handleChange(event) {
    const { name, value } = event.target;
    setFormData({
      ...formData,
      [name]: value
    });
  }

  function handleSubmit(event) {
    event.preventDefault();
    console.log(formData);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Username:
        <input type="text" name="username" value={formData.username} onChange={handleChange} />
      </label>
      <label>
        Email:
        <input type="email" name="email" value={formData.email} onChange={handleChange} />
      </label>
      <label>
        Password:
        <input type="password" name="password" value={formData.password} onChange={handleChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default MultiInputForm;
```

### Form Validation

Form validation ensures user input meets certain criteria before submission.

#### Example: Client-Side Validation

```javascript
import React, { useState } from 'react';

function ValidatedForm() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [errors, setErrors] = useState({});

  function handleEmailChange(event) {
    setEmail(event.target.value);
  }

  function handlePasswordChange(event) {
    setPassword(event.target.value);
  }

  function validate() {
    const errors = {};
    if (!email) {
      errors.email = 'Email is required';
    } else if (!/\S+@\S+\.\S+/.test(email)) {
      errors.email = 'Email is invalid';
    }
    if (!password) {
      errors.password = 'Password is required';
    } else if (password.length < 6) {
      errors.password = 'Password must be at least 6 characters';
    }
    return errors;
  }

  function handleSubmit(event) {
    event.preventDefault();
    const validationErrors = validate();
    if (Object.keys(validationErrors).length > 0) {
      setErrors(validationErrors);
    } else {
      console.log(`Email: ${email}, Password: ${password}`);
    }
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Email:
        <input type="email" value={email} onChange={handleEmailChange} />
        {errors.email && <p>{errors.email}</p>}
      </label>
      <label>
        Password:
        <input type="password" value={password} onChange={handlePasswordChange} />
        {errors.password && <p>{errors.password}</p>}
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default ValidatedForm;
```

## Best Practices for Form Management

- **Use controlled components:** for better control and validation.
- **Leverage refs:** for direct DOM manipulation with uncontrolled components.
- **Implement event handlers:** for managing input changes and form submissions.
- **Validate user input:**  to ensure data integrity.

## Practical Example: Complete Form

### Combine controlled components with validation for a robust form implementation.

```javascript
import React, { useState } from 'react';

function CompleteForm() {
  const [formData, setFormData] = useState({
    username: '',
    email: '',
    password: ''
  });

  const [errors, setErrors] = useState({});

  function handleChange(event) {
    const { name, value } = event.target;
    setFormData({
      ...formData,
      [name]: value
    });
  }

  function validate() {
    const errors = {};
    if (!formData.username) {
      errors.username = 'Username is required';
    }
    if (!formData.email) {
      errors.email = 'Email is required';
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      errors.email = 'Email is invalid';
    }
    if (!formData.password) {
      errors.password = 'Password is required';
    } else if (formData.password.length < 6) {
      errors.password = 'Password must be at least 6 characters';
    }
    return errors;
  }

  function handleSubmit(event) {
    event.prevent

Default();
    const validationErrors = validate();
    if (Object.keys(validationErrors).length > 0) {
      setErrors(validationErrors);
    } else {
      console.log(formData);
    }
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Username:
        <input type="text" name="username" value={formData.username} onChange={handleChange} />
        {errors.username && <p>{errors.username}</p>}
      </label>
      <label>
        Email:
        <input type="email" name="email" value={formData.email} onChange={handleChange} />
        {errors.email && <p>{errors.email}</p>}
      </label>
      <label>
        Password:
        <input type="password" name="password" value={formData.password} onChange={handleChange} />
        {errors.password && <p>{errors.password}</p>}
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default CompleteForm;
```

## Sources

- [React Official Documentation](https://react.dev)
- [JavaScript Front-End Frameworks and Libraries](https://www.javascriptstuff.com/)
- [MDN Web Docs - Form Data Validation](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation)

## Questions and Exercises

- What are controlled and uncontrolled components, and how do they differ?
- How do you handle form events in React?
- How can you manage a form with multiple inputs in React?
- Describe how to implement client-side form validation.


## Harjutus

- Create a controlled form that handles multiple inputs and validates them before submission.
- Use refs to create an uncontrolled form for a simple input field.
