Pattern: Missing use of `useState`

Issue: -

## Description

Enforces correct usage of `useState`, including destructuring, symmetric naming of the value and setter, and wrapping expensive initializers in a lazy initializer function.


Examples of **incorrect** code for this rule:

```js
// Problem: not destructured into a [value, setter] pair
import { useState } from "react";

function Counter() {
  const count = useState(0);
  //    ^^^ useState should be destructured into a value and setter pair, e.g. const [state, setState] = useState(...).
  return <div>{count}</div>;
}
```

Examples of **correct** code for this rule:


```js
// OK: destructure only the value, omitting the setter
import { useState } from "react";

function Component() {
  const [value] = useState(() => expensiveSetup());
  return <div>{value}</div>;
}
```