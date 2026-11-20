Pattern: Leaked timeout

Issue: -

## Description

A timeout scheduled in a component or custom Hook is not canceled when it is no longer needed. Its callback can run after the component unmounts or after an Effect's dependencies change, using values from an outdated render.

Save the ID returned by `setTimeout` and call `clearTimeout` in the Effect's cleanup function.

## Examples

Example of **incorrect** code:

```jsx
import { useEffect } from "react";

function Notification({ message }) {
  useEffect(() => {
    const timeoutId = setTimeout(() => console.log(message), 1000);
  }, [message]);

  return null;
}
```

Example of **correct** code:

```jsx
import { useEffect } from "react";

function Notification({ message }) {
  useEffect(() => {
    const timeoutId = setTimeout(() => console.log(message), 1000);
    return () => clearTimeout(timeoutId);
  }, [message]);

  return null;
}
```

## Further Reading

* [ESLint React - no-leaked-timeout](https://eslint-react.xyz/docs/rules/web-api-no-leaked-timeout)
