Pattern: Use of `useContext`

Issue: -

## Description

Replaces usages of `useContext` with `use`.

In React 19, `use` is preferred over `useContext` because it is more flexible.

In addition, it is recommended to enable the naming-convention/context-name rule to enforce consistent naming conventions for contexts.

Example of **incorrect** code:

```js
import { useContext } from "react";

function Button() {
  const theme = useContext(ThemeContext);
  // ...
}
```

Example of **correct** code:

```js
import { use } from "react";

function Button() {
  const theme = use(ThemeContext);
  // ...
}
```

## Further Reading

* [GitHub - no-use-context](https://eslint-react.xyz/docs/rules/no-use-context)