Pattern: Explicit `undefined` assignment

Issue: -

## Description

Variables, parameters, and return statements are `undefined` by default, making explicit assignments of `undefined` unnecessary and verbose.

## Examples

Example of **incorrect** code:
```javascript
let foo = undefined;
const bar = (x = undefined) => {};
return undefined;
```

Example of **correct** code:
```javascript
let foo;
const bar = (x) => {};
return;
```