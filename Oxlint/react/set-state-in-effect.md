Pattern: Synchronous state update inside effect

Issue: -

## Description

Calling `setState` synchronously in an effect triggers an immediate
extra render pass and usually indicates non-local derived data, a
derived-event pattern, or improper external-data synchronization.
Values that can be computed from props and state should be computed
during render instead.

## Examples

Example of **incorrect** code:
```jsx
import { useEffect, useState } from "react";
function Component() {
  const [state, setState] = useState(0);
  useEffect(() => {
    setState((s) => s + 1);
  });
  return state;
}
```

Example of **correct** code:
```jsx
function Component({ value }) {
  const doubled = value * 2;
  return <div>{doubled}</div>;
}
```
