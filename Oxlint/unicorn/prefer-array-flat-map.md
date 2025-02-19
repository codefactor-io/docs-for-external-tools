Pattern: Chained `map().flat()` calls

Issue: -

## Description

Using `flatMap()` is more efficient than chaining `map()` and `flat()` methods, as it avoids creating an intermediate array.

## Examples

Example of **incorrect** code:
```javascript
const bar = [1, 2, 3].map((i) => [i]).flat();
```

Example of **correct** code:
```javascript
const bar = [1, 2, 3].flatMap((i) => [i]);
```