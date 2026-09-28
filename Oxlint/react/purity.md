Pattern: Impure function call during render

Issue: -

## Description

Impure renders return different output for the same props and state,
breaking memoization, concurrent rendering, and replayability.

## Examples

Example of **incorrect** code:
```jsx
function Component() {
  const rand = Math.random();
  return <div>{rand}</div>;
}
```

Example of **correct** code:
```jsx
import { useState } from "react";
function Component() {
  const [rand, setRand] = useState(0);
  return <button onClick={() => setRand(Math.random())}>{rand}</button>;
}
```
