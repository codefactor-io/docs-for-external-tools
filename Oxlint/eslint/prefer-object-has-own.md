Pattern: Use of `hasOwnProperty` call

Issue: -

## Description

Using `Object.prototype.hasOwnProperty.call()` is a common but verbose way to safely check for object properties. The ES2022 `Object.hasOwn()` method provides a shorter, clearer alternative that achieves the same goal.

## Examples

Example of **incorrect** code:
```javascript
Object.prototype.hasOwnProperty.call(obj, "prop");
Object.hasOwnProperty.call(obj, "key");
({}).hasOwnProperty.call(object, "foo");

const hasProp = Object.prototype.hasOwnProperty.call(obj, prop);
if (Object.prototype.hasOwnProperty.call(data, "id")) {}
```

Example of **correct** code:
```javascript
Object.hasOwn(obj, "prop");
Object.hasOwn(object, "foo");

const hasProp = Object.hasOwn(obj, prop);
if (Object.hasOwn(data, "id")) {}

// Direct calls on objects are checked by no-prototype-builtins
if (obj.hasOwnProperty("id")) {}
```