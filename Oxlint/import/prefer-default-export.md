Pattern: Missing default export

Issue: -

## Description

When a module has only one export, using a default export instead of named exports improves readability and maintainability. This standardizes module exports and makes the primary export more obvious to consumers.

## Examples

Example of **incorrect** code:

```javascript
// With { target: "single" }
export const foo = "foo";

// With { target: "any" }  
export const foo = "foo";
export const baz = "baz";
```

Example of **correct** code:

```javascript
// With { target: "single" }
export const foo = "foo";
const bar = "bar";
export default bar;

// With { target: "any" }
export default function bar() {}
```