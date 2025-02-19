Pattern: Direct call of Object.prototype methods

Issue: -

## Description

Calling Object.prototype methods (like hasOwnProperty, isPrototypeOf) directly on objects can fail when the object is created with null prototype (Object.create(null)) or when properties shadow the built-in methods. Always use these methods from Object.prototype through call() or apply().

## Examples

Example of **incorrect** code:
```javascript
const obj = { hasOwnProperty: false };
console.log(obj.hasOwnProperty("foo"));  // TypeError

const data = JSON.parse('{"isPrototypeOf": 1}');
data.isPrototypeOf(obj);  // TypeError

foo.propertyIsEnumerable("bar");
```

Example of **correct** code:
```javascript
const obj = { hasOwnProperty: false };
console.log(Object.prototype.hasOwnProperty.call(obj, "foo"));

const data = JSON.parse('{"isPrototypeOf": 1}');
Object.prototype.isPrototypeOf.call(data, obj);

Object.prototype.propertyIsEnumerable.call(foo, "bar");
```