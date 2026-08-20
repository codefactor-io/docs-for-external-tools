Pattern: Long-form object property or method syntax

Issue: -

## Description

Stylistic preference

## Examples

Example of **incorrect** code:
```javascript
var properties = { x: x, y: y, z: z };
var methods = { a: function () {}, b: function () {} };
```

Example of **correct** code:
```javascript
var properties = { x, y, z };
var methods = { a() {}, b() {} };
```
