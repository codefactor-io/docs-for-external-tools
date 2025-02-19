Pattern: Deeply nested ternary expression 

Issue: -

## Description

Deeply nested ternary expressions make code difficult to understand. Only one level of nesting is allowed, and nested expressions must be wrapped in parentheses for clarity.

## Examples

Example of **incorrect** code:
```javascript
const foo = i > 5 ? (i < 100 ? true : false) : true;
const foo = i > 5 ? true : i < 100 ? true : i < 1000 ? true : false;
```

Example of **correct** code:
```javascript
const foo = i > 5 ? (i < 100 ? true : false) : true;
const foo = i > 5 ? (i < 100 ? true : false) : i < 100 ? true : false;
```