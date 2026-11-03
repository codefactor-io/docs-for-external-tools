Pattern: Misuse of `useMemo`

Issue: -

## Description

An async or generator callback makes `useMemo` memoize a promise or
iterator instead of the intended value, and misused arguments prevent
memoization from working at all.

## Examples

Example of **incorrect** code:
```jsx
import { useMemo } from "react";
function Component({ a }) {
  const x = useMemo(async () => {
    await a;
  }, [a]);
  return <div>{x}</div>;
}
```

Example of **correct** code:
```jsx
import { useMemo } from "react";
function Component({ a }) {
  const x = useMemo(() => a + 1, [a]);
  return <div>{x}</div>;
}
```
