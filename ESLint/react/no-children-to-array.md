Pattern: Use of `Children.toArray`

Issue: -

## Description

Using `Children.toArray` is uncommon and can lead to fragile code.

Example of **incorrect** code:

```js
import React, { Children } from "react";

interface MyComponentProps {
  children: React.ReactNode;
}

function MyComponent({ children }: MyComponentProps) {
  const result = Children.toArray(children);
  result.reverse();
  // ...
}
```

Alternatives: https://react.dev/reference/react/Children#alternatives


## Further Reading

* [GitHub - no-children-to-array](https://eslint-react.xyz/docs/rules/no-children-to-array)