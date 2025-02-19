Pattern: Existence check using `find`, `findIndex`, or `filter`

Issue: -

## Description

Using `Array#some()` is more idiomatic for checking if elements exist in an array that match a condition, compared to `find`, `findIndex`, `findLast`, `findLastIndex` or checking `filter` length.

## Examples

Example of **incorrect** code:
```javascript
const foo = array.find(fn) ? bar : baz;
const foo = array.findLast((elem) => hasRole(elem)) !== null;
foo.findIndex(bar) < 0;
foo.findIndex((element) => element.bar === 1) !== -1;
array.filter(fn).length === 0;
```

Example of **correct** code:
```javascript
const foo = array.some(fn) ? bar : baz;
foo.some((element) => element.bar === 1);
!array.some(fn);
```