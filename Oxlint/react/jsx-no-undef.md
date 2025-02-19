Pattern: Undeclared variable in JSX

Issue: -

## Description

Using undefined variables in JSX likely indicates a misspelling or a missing import, which will cause a `ReferenceError` at runtime. All components used in JSX must be declared or imported before use.

## Examples

Example of **incorrect** code:
```jsx
const C = <B />; // B is not defined
```

Example of **correct** code:
```jsx
import B from './B';
const C = <B />;
```