Pattern: Incorrect use of `new` with built-in objects

Issue: -

## Description

Some built-in objects require `new` for consistency (e.g., `Array`, `Map`, `Set`), while others should not use `new` to avoid creating object wrappers for primitives (e.g., `String`, `Number`, `Boolean`).

## Examples

Example of **incorrect** code:
```javascript
const foo = new String("hello world");
const bar = Array(1, 2, 3);
```

Example of **correct** code:
```javascript
const foo = String("hello world");
const bar = new Array(1, 2, 3);
```