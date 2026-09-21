Pattern: Filtered array element access

Issue: -

## Description

Using `filter(...)[0]` or array destructuring to get the first match is less
efficient and more verbose than using `find(...)`. `find` and `findLast`
short-circuit when a match is found, whereas `filter` evaluates the entire array.

## Examples

Example of **incorrect** code:
```javascript
const match = users.filter((u) => u.id === id)[0];
const match = users.filter(fn).shift();
const [match] = users.filter(fn);

const match = users.filter(fn).at(-1);
const match = users.filter(fn).pop();
```

Example of **correct** code:
```javascript
const match = users.find((u) => u.id === id);
const match = users.find(fn);

const match = users.findLast(fn);
```
