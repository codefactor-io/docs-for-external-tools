Pattern: Explicit `true` value for boolean JSX attribute

Issue: -

## Description

In JSX, boolean attributes can be written using shorthand syntax by omitting the value. Using explicit `true` values creates unnecessary verbosity and inconsistency in the codebase.

## Examples

Example of **incorrect** code:
```jsx
const Hello = <Hello personal={true} />;
```

Example of **correct** code:
```jsx
const Hello = <Hello personal />;
```