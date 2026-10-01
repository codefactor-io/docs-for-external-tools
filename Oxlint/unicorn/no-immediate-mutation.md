Pattern: Mutation immediately after initialization

Issue: -

## Description

When you initialize a variable and immediately mutate it, it's cleaner to include
the mutation in the initialization. This makes the code more readable and reduces
the number of statements.

## Examples

Example of **incorrect** code:
```javascript
const array = [1, 2];
array.push(3);

const object = { foo: 1 };
object.bar = 2;

const set = new Set([1, 2]);
set.add(3);

const map = new Map([["foo", 1]]);
map.set("bar", 2);
```

Example of **correct** code:
```javascript
const array = [1, 2, 3];

const object = { foo: 1, bar: 2 };

const set = new Set([1, 2, 3]);

const map = new Map([
  ["foo", 1],
  ["bar", 2],
]);
```
