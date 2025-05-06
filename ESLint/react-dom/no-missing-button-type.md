Pattern: Missing `type` attribute for `button`

Issue: -

## Description

Enforces explicit `type` attribute for `button` elements.

The default `type` of a button is `submit`, which causes the submission of a form when placed inside a `form` element. This is likely not the behaviour that you want inside a React application.

Allowed button types are: `submit`, `button` or `reset`.

Example of **incorrect** code:

```tsx
import React from "react";

function MyComponent() {
  return <button>Click me</button>;
  //     ^^^^^^^^^^^^^^^^^^^^^^^^^
  //     - Missing 'type' attribute on button component.
}
```

Example of **correct** code:

```tsx
import React from "react";

function MyComponent() {
  return <button>Click me</button>;
  //     ^^^^^^^^^^^^^^^^^^^^^^^^^
  //     - Missing 'type' attribute on button component.
}
```