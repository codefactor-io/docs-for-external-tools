Pattern: Self-assignment of variable

Issue: -

## Description

Self-assignments don't have any effect and usually indicate a mistake, such as an incomplete refactoring or a typo. These assignments can be safely removed or need to be replaced with the intended assignment target.

## Examples

Example of **incorrect** code:
```javascript
foo = foo;
[a, b] = [a, b];
obj.prop = obj.prop;

[a, b, c] = [a, b, c];
a.b.c = a.b.c;

const {x, y} = {x: x, y: y};
```

Example of **correct** code:
```javascript
foo = bar;
[a, b] = [b, a];  // Swapping values
obj.prop = obj.other;

[a, b, c] = [c, a, b];  // Rotating values
a.b.c = x.y.z;

const {x, y} = coords;
```