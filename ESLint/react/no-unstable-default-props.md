Pattern: Unstable default props

Issue: -

## Description

Prevents using referential-type values as default props in object destructuring.

When using object destructuring syntax, you can set the default value for a given property if it does not exist. If you set the default value to one of the values that is compared by identity, then each time the destructuring is evaluated, the JS engine will create a new, distinct value in the destructured variable.

This harms performance, as it means that React will have to re-evaluate hooks and re-render memoized components more often than necessary.

To fix the violations, the easiest way is to use a referencing variable in module scope instead of using the literal values.

Examples of **incorrect** code for this rule:

```js
import React from "react";

interface MyComponentProps {
  items: string[];
}

function MyComponent({ items = [] }: MyComponentProps) {
  //                           ^^
  //                           - An 'Array literal' as a default prop. This could lead to a potential infinite render loop in React. Use a variable instead of 'Array literal'.
  return null;
}
```

Examples of **correct** code for this rule:

```js
import React from "react";

const emptyArray: string[] = [];

interface MyComponentProps {
  items: string[];
}

function MyComponent({ items = emptyArray }: MyComponentProps) {
  return null;
}
```