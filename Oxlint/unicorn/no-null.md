Pattern: Use of `null` literal

Issue: -

## Description

Using `undefined` instead of `null` simplifies input validation and makes TypeScript types less verbose. Most developers use `null` and `undefined` interchangeably, so standardizing on `undefined` improves consistency.

## Examples

Example of **incorrect** code:
```javascript
let foo = null;
function bar(baz = null) {}
```

Example of **correct** code:
```javascript
let foo;
function bar(baz) {}
```