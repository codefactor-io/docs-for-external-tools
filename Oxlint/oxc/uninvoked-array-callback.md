Pattern: Callback on empty array slots

Issue: -

## Description

Using array methods with callbacks on arrays created with `new Array(n)` won't work as expected. Such arrays contain empty slots rather than actual values, so the callback is never invoked.

## Examples

Example of **incorrect** code:
```javascript
const items = new Array(3).map(i => i + 1);
const filled = new Array(5).forEach(console.log);
```

Example of **correct** code:
```javascript
const items = Array(3).fill().map(i => i + 1);
const filled = [...Array(5)].forEach(console.log);
const numbers = Array.from({length: 3}, (_, i) => i + 1);
```