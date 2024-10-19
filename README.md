# usePrevious custom hook for React 

A lightweight and simple custom React hook that helps you track the **previous value** of a state or prop in your functional components.

## Features

- **Track Previous State**: Easily keep track of the previous value of any piece of state or props in React.
- **No Re-renders**: Uses `useRef` to persist values across renders without triggering re-renders.
- **Simple API**: Provides an intuitive, easy-to-use API that seamlessly integrates with your existing React components.
- **Lightweight**: Minimal code that adds functionality without bloat.

## Installation

Install the hook via npm:

```bash
npm install @gk3000/use-previous
```
or via yarn:
```
yarn add @gk3000/use-previous
```

##U sage

### Basic Example
This hook is perfect for tracking the previous value of a piece of state or a prop in your component. Here's an example of how to use it in a functional component:
```
import React, { useState } from 'react';
import usePrevious from '@gk3000/use-previous';

function Counter() {
  const [count, setCount] = useState(0);
  
  // Track the previous value of the count state
  const previousCount = usePrevious(count);

  return (
    <div>
      <h1>Current Count: {count}</h1>
      <h2>Previous Count: {previousCount}</h2>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
}

export default Counter;
```
## Parameters
```
const previousValue = usePrevious(value);
```
`value` (`any`): The state or prop value you want to track.

## Returns
- `previousValue`: The previous value of the state or prop before the last update. On the initial render, it will return `undefined`.

### Advanced Example

This hook can also track previous values of more complex data types, such as objects or arrays:
```
import React, { useState } from 'react';
import usePrevious from '@gk3000/use-previous';

function UserInfo() {
  const [user, setUser] = useState({ name: 'John', age: 30 });

  const previousUser = usePrevious(user);

  return (
    <div>
      <h1>Current User: {user.name}, Age: {user.age}</h1>
      <h2>Previous User: {previousUser?.name}, Age: {previousUser?.age}</h2>
      <button onClick={() => setUser({ name: 'Jane', age: 25 })}>
        Change User
      </button>
    </div>
  );
}

export default UserInfo;
```

## Why Use usePrevious?

- Useful for Comparing State Changes: It helps in situations where you need to know the previous value to perform comparisons, animations, or transitions based on changes.
- Simple & Flexible: The hook is easy to use and works with any data type (primitives, arrays, objects).
- Optimized: Since usePrevious uses useRef, it stores the previous value without causing unnecessary re-renders, making it efficient for performance-sensitive components.

## License

This project is licensed under the MIT License.
