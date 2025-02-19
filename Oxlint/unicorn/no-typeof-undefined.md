Pattern: Use of `typeof` for `undefined` check

Issue: -

## Description

Using `typeof value === 'undefined'` is unnecessarily verbose. Direct comparison with `undefined` is clearer and preferred. Only use `typeof` when checking if a global variable exists, where `globalThis.value === undefined` may be more appropriate.

## Examples

Example of **incorrect** code:
```javascript
typeof foo === "undefined";
```

Example of **correct** code:
```javascript
foo === undefined;
```