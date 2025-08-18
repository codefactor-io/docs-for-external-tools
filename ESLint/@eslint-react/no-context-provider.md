Pattern: Use of `<Context.Provider>`

Issue: -

## Description

Replaces usages of `<Context.Provider>` with `<Context>`.

In React 19, you can render `<Context>` as a provider instead of `<Context.Provider>`.

Example of **incorrect** code:

```js
import React from "react";
import ThemeContext from "./ThemeContext";

function App({ children }) {
  return (
    <ThemeContext.Provider value="light">
      {children}
    </ThemeContext.Provider>
  );
}
```

Example of **correct** code:

```js
import React from "react";
import ThemeContext from "./ThemeContext";

function App({ children }) {
  return (
    <ThemeContext value="dark">
      {children}
    </ThemeContext>
  );
}
```

## Further Reading

* [GitHub - no-context-provider](https://eslint-react.xyz/docs/rules/no-context-provider)