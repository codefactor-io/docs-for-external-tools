Pattern: Trailing zero in decimal number

Issue: -

## Description

In JavaScript, numbers like `1.0`, `1.` and `1` are exactly the same. Using trailing zeros in decimal numbers adds unnecessary verbosity without any functional difference.

## Examples

Example of **incorrect** code:
```javascript
const foo = 1.0;
const foo = -1.0;
const foo = 123_456.000_000;
```

Example of **correct** code:
```javascript
const foo = 1;
const foo = -1;
const foo = 123456;
const foo = 1.1;
```