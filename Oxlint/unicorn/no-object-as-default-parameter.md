Pattern: Object literal as default parameter

Issue: -

## Description

Using an object literal as a default parameter value can lead to unexpected behavior when passing partial options. When only some properties are provided, the entire default object is replaced. Use object destructuring with individual defaults instead.

## Examples

Example of **incorrect** code:
```javascript
function foo(foo = { a: false }) {}
function bar(options = { x: 1, y: 2 }) {}
```

Example of **correct** code:
```javascript
function foo({ a = false } = {}) {}
function bar({ x = 1, y = 2 } = {}) {}
```