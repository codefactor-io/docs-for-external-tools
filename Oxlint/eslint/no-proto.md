Pattern: Use of `__proto__` property

Issue: -

## Description

The `__proto__` property is deprecated since ECMAScript 3.1. Modern code should use `Object.getPrototypeOf()` and `Object.setPrototypeOf()` instead for accessing and setting an object's prototype.

## Examples

Example of **incorrect** code:
```javascript
const parent = {};
const child = {};

const proto = obj.__proto__;
obj.__proto__ = parent;

const otherProto = obj["__proto__"];
obj["__proto__"] = child;
```

Example of **correct** code:
```javascript
const parent = {};
const child = {};

const proto = Object.getPrototypeOf(obj);
Object.setPrototypeOf(obj, parent);

// Create object with specific prototype
const newObj = Object.create(parent);
```