Pattern: Use of `new` with non-constructor globals

Issue: -

## Description

The `Symbol` and `BigInt` functions are not constructors and will throw a TypeError when used with `new`. Though they start with uppercase letters like classes, they are functions that create primitives.

## Examples

Example of **incorrect** code:
```javascript
let sym = new Symbol("foo");
let num = new BigInt(9007199254740991);
let value = new Symbol.for("bar");
```

Example of **correct** code:
```javascript
let sym = Symbol("foo");
let num = BigInt(9007199254740991);
let value = Symbol.for("bar");

// Other constructors are fine
let str = new String("foo");
let obj = new Object();
```