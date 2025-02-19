Pattern: Use of `new` with primitive wrapper objects

Issue: -

## Description

Creating primitive wrapper objects with `new String()`, `new Number()`, or `new Boolean()` leads to unexpected behavior. The resulting objects have different `typeof` results than primitives and boolean objects are always truthy, even when wrapping `false`.

## Examples

Example of **incorrect** code:
```javascript
const str = new String("hello");
const num = new Number(123);
const bool = new Boolean(false);

if (str === "hello") {  // false, because str is an object
  console.log("never reached");
}

if (new Boolean(false)) {  // always true!
  console.log("always reached");
}
```

Example of **correct** code:
```javascript
const str = String("hello");
const num = Number(123);
const bool = Boolean(false);

// Or use literals
const str2 = "hello";
const num2 = 123;
const bool2 = false;
```