Pattern: Implicit length or size check

Issue: -

## Description

Use explicit comparisons when checking array length or collection size for better code clarity. Avoid implicit checks like `!array.length` or indirect comparisons like `array.length < 1`.

## Examples

Example of **incorrect** code:
```javascript
const isEmpty = foo.length == 0;
const isEmpty = foo.length < 1;
const isEmpty = !foo.length;
const isEmpty = !(foo.length > 0);
const isEmptySet = !foo.size;
```

Example of **correct** code:
```javascript
const isEmpty = foo.length === 0;
```