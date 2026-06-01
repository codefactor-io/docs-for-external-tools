Pattern: Unnecessary computed key

Issue: -

## Description

It’s unnecessary to use computed properties with literal.

## Examples

Example of **incorrect** code:

```javascript
const a = { ["0"]: 0 };
const b = { ["0+1,234"]: 0 };
const c = { [0]: 0 };
const e = { ["x"]() {} };

class Foo {
  ["foo"] = "bar";
  [0]() {}
  static ["foo"] = "bar";
  get ["b"]() {}
  set ["c"](value) {}
}
```

Example of **correct** code:

```javascript
const a = { a: 0 };
const b = { 0: 0 };
const c = { x() {} };
const e = { "0+1,234": 0 };

class Foo {
  foo = "bar";
  0() {}
  a() {}
  static foo = "bar";
}
```