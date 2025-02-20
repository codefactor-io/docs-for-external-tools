Pattern: Custom wrapper for type coercion function

Issue: -

## Description

Creating custom functions that simply wrap built-in coercion functions like `String()`, `Number()`, `BigInt()`, `Boolean()`, or `Symbol()` is unnecessary. Using the built-in functions directly provides the same functionality with better clarity.

## Examples

Example of **incorrect** code:
```javascript
const foo = (v) => String(v);
foo(1);
const foo = (v) => Number(v);
array.some((v) => /* comment */ v);
```

Example of **correct** code:
```javascript
String(1);
Number(1);
array.some(Boolean);
```