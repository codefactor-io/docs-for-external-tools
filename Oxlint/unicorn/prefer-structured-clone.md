Pattern: Non-native deep clone implementation

Issue: -

## Description

The `structuredClone()` function provides a native way to create deep clones of objects, which is more efficient and reliable than using `JSON.parse(JSON.stringify())` or utility libraries like Lodash's `cloneDeep`.

## Examples

Example of **incorrect** code:
```js
const clone = JSON.parse(JSON.stringify(foo));
const clone = _.cloneDeep(foo);
```

Example of **correct** code:
```js
const clone = structuredClone(foo);
```