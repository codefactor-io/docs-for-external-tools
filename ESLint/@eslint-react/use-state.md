Pattern: Incorrect use of `useState`

Issue: -

## Description

Destructure the result of `useState` into a state value and setter. Name the setter `set` followed by the capitalized state name, such as `count` and `setCount`, so their relationship is clear. The state value must be a plain variable, not another destructuring pattern.

When computing initial state with a function call, wrap it in a lazy initializer to avoid repeating that computation on every render. Returning the `useState` result directly from a custom Hook and omitting an unused setter are allowed.

## Examples

Example of **incorrect** code:

```jsx
import { useState } from "react";

function Counter() {
  const [count, updateCount] = useState(0);
  return <div>{count}</div>;
}
```

Example of **correct** code:

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);
  return <div>{count}</div>;
}
```

## Further Reading

* [ESLint React - use-state](https://eslint-react.xyz/docs/rules/use-state)
