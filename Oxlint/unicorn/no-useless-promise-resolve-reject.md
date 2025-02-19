Pattern: Redundant `Promise.resolve/reject` in async context

Issue: -

## Description

In async functions or promise callbacks, wrapping return values in `Promise.resolve` or errors in `Promise.reject` is unnecessary since these contexts automatically wrap returns in promises and handle thrown errors appropriately.

## Examples

Example of **incorrect** code:
```javascript
async () => Promise.resolve(bar);
```

Example of **correct** code:
```javascript
async () => bar;
```