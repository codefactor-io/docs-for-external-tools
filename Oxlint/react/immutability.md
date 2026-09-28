Pattern: Mutation of immutable React value

Issue: -

## Description

React relies on immutability to know when to re-render; mutating these
values causes stale UI and lost updates.

## Examples

Example of **incorrect** code:
```jsx
import { useState } from "react";
function Component() {
  const [state] = useState({ a: 0 });
  state.a = 1; // mutates state directly
  return <div>{state.a}</div>;
}
```

Example of **correct** code:
```jsx
import { useState } from "react";
function Component() {
  const [state, setState] = useState({ a: 0 });
  return <div onClick={() => setState({ a: state.a + 1 })}>{state.a}</div>;
}
```
