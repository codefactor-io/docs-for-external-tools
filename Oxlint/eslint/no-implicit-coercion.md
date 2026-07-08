Pattern: Use of implicit type coercion

Issue: -

## Description

Implicit type coercions using operators can be less clear than using explicit
type conversion functions like `Boolean()`, `Number()`, and `String()`.
Using explicit conversions makes the intent clearer and the code more readable.

## Examples

Example of **incorrect** code:
```javascript
var b = !!foo;
var n = +foo;
var s = "" + foo;
```

Example of **correct** code:
```javascript
var b = Boolean(foo);
var n = Number(foo);
var s = String(foo);
```
