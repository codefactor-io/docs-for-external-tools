Pattern: Unnecessary `.call()` or `.apply()`

Issue: -

## Description

Using `Function.prototype.call()` or `Function.prototype.apply()` is unnecessary when the context object (this) is undefined, null, or the same as the function's own context. These calls are slower than direct invocation.

## Examples

Example of **incorrect** code:
```javascript
foo.call(undefined, 1, 2, 3);
foo.apply(null, [1, 2, 3]);

obj.method.call(obj, x, y);
obj.method.apply(obj, [x, y]);

// Same as the object's context
object.method.call(object, x, y);
```

Example of **correct** code:
```javascript
foo(1, 2, 3);  // Instead of foo.call(undefined, 1, 2, 3)
obj.method(x, y);  // Instead of obj.method.call(obj, x, y)

// Different context is fine
foo.call(obj, 1, 2, 3);
obj.method.apply(otherObj, [x, y]);

// Variable arguments are fine
foo.apply(null, args);
obj.method.apply(obj, arguments);
```