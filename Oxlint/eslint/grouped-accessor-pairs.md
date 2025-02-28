Pattern: Separated accessor pairs in objects

Issue: -

## Description

Accessor pairs (getters and setters) for the same property should be defined next to each other in objects or classes. This improves code readability by keeping related functionality together.

## Examples

Example of **incorrect** code:
```js
const foo = {
  get a() {
    return this.val;
  },
  b: 1,
  set a(value) {
    this.val = value;
  },
};
```

Example of **correct** code:
```js
const foo = {
  get a() {
    return this.val;
  },
  set a(value) {
    this.val = value;
  },
  b: 1,
};
```