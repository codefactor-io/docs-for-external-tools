Pattern: Ref access during render

Issue: -

## Description

React may not have attached the ref yet during render, and reading it
does not subscribe the component to updates — the UI silently goes
stale.

## Examples

Example of **incorrect** code:
```jsx
import { useRef } from "react";
function Component() {
  const ref = useRef(null);
  const value = ref.current; // read during render
  return <div>{value}</div>;
}
```

Example of **correct** code:
```jsx
import { useEffect, useRef } from "react";
function Component() {
  const ref = useRef(null);
  useEffect(() => {
    ref.current.focus();
  }, []);
  return <input ref={ref} />;
}
```
