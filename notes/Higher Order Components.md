---
tags: [ReactJs]
title: Higher Order Components
created: '2023-07-06T16:25:19.047Z'
modified: '2023-07-06T16:27:15.523Z'
---

# Higher Order Components

Higher Order Components (HOCs) are a pattern in React that enables component composition by taking a component and returning a new component with enhanced functionality. HOCs are functions that accept a component as an argument and return a new component.

Here's an example of creating a Higher Order Component:

```js
import React from 'react';

// Higher Order Component
function withLogging(WrappedComponent) {
  return function WithLogging(props) {
    // Additional logic or functionality can be added here

    // Render the wrapped component with any additional props
    return <WrappedComponent {...props} />;
  };
}

// Component to be wrapped
function MyComponent(props) {
  return <div>Hello, {props.name}!</div>;
}

// Use the HOC to enhance the functionality of MyComponent
const EnhancedComponent = withLogging(MyComponent);

// Usage of the enhanced component
function App() {
  return <EnhancedComponent name="React" />;
}
```

In this example, the `withLogging` function is a Higher Order Component that accepts a `WrappedComponent` as an argument. It returns a new component (`WithLogging`) that wraps the `WrappedComponent` and provides additional functionality.

The `WithLogging` component can add logic or functionality before or after rendering the `WrappedComponent`. You can modify the props, add state, or perform other operations as needed.

The `EnhancedComponent` is created by passing `MyComponent` to the `withLogging` Higher Order Component. The enhanced component now has the additional functionality provided by the HOC.

Higher Order Components are a powerful pattern in React that enables reusability and composability of components. They allow you to enhance and modify component behavior without directly modifying the original component's code.

In React, you can create a wrapper component using a functional component. Here's an example of creating a wrapper component using a functional component and React hooks:

```js
import React from 'react';

// Wrapper component
function WrapperComponent(WrappedComponent) {
  return function EnhancedComponent(props) {
    // Additional logic or state can be added here

    return <WrappedComponent {...props} />;
  };
}

// Component to be wrapped
function MyComponent(props) {
  return <div>Hello, {props.name}!</div>;
}

// Use the wrapper component to enhance the functionality of MyComponent
const EnhancedComponent = WrapperComponent(MyComponent);

// Usage of the enhanced component
function App() {
  return <EnhancedComponent name="React" />;
}
```

In this example, the `WrapperComponent` is a wrapper component created using a functional component. It takes the `WrappedComponent` as an argument and returns a new functional component that wraps it. The enhanced component can have additional logic, state, or props.

The `EnhancedComponent` is created by passing `MyComponent` to `WrapperComponent`. The enhanced component now has the additional functionality provided by the wrapper.

You can customize the wrapper component by adding hooks, state, or any other functionality within the body of the `EnhancedComponent` functional component. This allows you to apply reusable logic or modifications to multiple components in a concise and readable manner using functional components.


If you want to create a wrapper component that passes the child component as a prop, you can modify the example as follows:

```js
import React from 'react';

// Wrapper component
function WrapperComponent({ children }) {
  // Additional logic or state can be added here

  return <div>{children}</div>;
}

// Component to be wrapped
function MyComponent(props) {
  return <div>Hello, {props.name}!</div>;
}

// Use the wrapper component to enhance the functionality of MyComponent
function App() {
  return (
    <WrapperComponent>
      <MyComponent name="React" />
    </WrapperComponent>
  );
}
```

In this example, the `WrapperComponent` receives the child components through the `children` prop. It can perform additional logic or modifications before rendering the children.

The `MyComponent` is wrapped by the `WrapperComponent` by placing it as a child within the `WrapperComponent` tags in the `App` component.

This approach allows you to wrap any component(s) within the `WrapperComponent` and pass them as children. The wrapped component(s) can receive additional props or utilize the wrapper's logic or state as needed.



