Pattern: Timestamp creation via `new Date()`

Issue: -

## Description

Using `Date.now()` is more concise and efficient than `new Date().getTime()` or `new Date().valueOf()` as it avoids creating unnecessary `Date` objects.

## Examples

Example of **incorrect** code:
```javascript
const ts = new Date().getTime();
const ts = new Date().valueOf();
```

Example of **correct** code:
```javascript
const ts = Date.now();
```