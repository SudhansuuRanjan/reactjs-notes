---
tags: [ReactJs]
title: Timers and Counters in React
created: '2023-07-06T16:29:58.397Z'
modified: '2023-07-06T16:30:23.716Z'
---

# Timers and Counters in React

In React, you can perform async operations like `setInterval` and `setTimeout` using various techniques. Here are two common approaches:

1. Using `useEffect` Hook:
   You can utilize the `useEffect` Hook to manage async operations like `setInterval` and `setTimeout`. Here's an example:

   ```js
   import React, { useEffect, useState } from 'react';

   function MyComponent() {
     const [count, setCount] = useState(0);

     useEffect(() => {
       const interval = setInterval(() => {
         // Perform desired operation
         setCount((prevCount) => prevCount + 1);
       }, 1000);

       // Clean up the interval on component unmount
       return () => {
         clearInterval(interval);
       };
     }, []);

     return <div>Count: {count}</div>;
   }
   ```

   In this example, `useEffect` is used to start a timer using `setInterval` when the component mounts. The interval increments the `count` state every second. The interval is cleared using `clearInterval` when the component unmounts.

2. Custom Hook:
   You can create a custom hook to encapsulate the logic of async operations. Here's an example:

   ```js
   import React, { useEffect, useState } from 'react';

   function useInterval(callback, delay) {
     useEffect(() => {
       const interval = setInterval(callback, delay);

       return () => {
         clearInterval(interval);
       };
     }, [callback, delay]);
   }

   function MyComponent() {
     const [count, setCount] = useState(0);

     useInterval(() => {
       // Perform desired operation
       setCount((prevCount) => prevCount + 1);
     }, 1000);

     return <div>Count: {count}</div>;
   }
   ```

   In this approach, a custom hook called `useInterval` is created to encapsulate the logic of `setInterval`. The custom hook is then used within the component to handle the async operation.

Both approaches ensure that async operations like `setInterval` or `setTimeout` are properly managed and cleaned up to avoid memory leaks or unexpected behavior. Remember to clean up any async operations in the `useEffect` cleanup function to prevent side effects after the component unmounts.
