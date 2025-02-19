Pattern: Use of `with` statement

Issue: -

## Description

The `with` statement adds all properties of an object to the current scope, making it impossible to determine whether a variable inside the block refers to a property of the object or a variable in an outer scope. This leads to confusing code and potential bugs.

## Examples

Example of **incorrect** code:
```javascript
with (math) {
  x = cos(angle);
}

with (object) {
  property = 42;
}

with (point) {
  r = Math.sqrt(x * x + y * y);  // Unclear if r is from point
}
```

Example of **correct** code:
```javascript
const x = math.cos(angle);

object.property = 42;

const r = Math.sqrt(
  point.x * point.x + 
  point.y * point.y
);

// Or use destructuring
const { x, y } = point;
const r = Math.sqrt(x * x + y * y);
```