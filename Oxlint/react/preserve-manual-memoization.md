Pattern: Manual memoization not preserved

Issue: -

## Description

When the compiler cannot prove that existing manual memoization is
preserved, it skips optimizing that code.

## Examples

Example of **incorrect** code:
```jsx
import { useCallback } from "react";
function useFoo(props) {
  const values = [];
  values.push(props);
  return useCallback(() => values, [values]);
}
```

Example of **correct** code:
```jsx
import { useMemo } from "react";
function Component({ propA }) {
  return useMemo(() => propA.x, [propA]);
}
```
