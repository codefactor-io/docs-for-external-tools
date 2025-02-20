Pattern: Use of `.apply()` method call

Issue: -

## Description

Using `Reflect.apply()` is clearer and safer than the `.apply()` method, which might be overridden or not exist. `Reflect.apply()` provides a more reliable way to call functions with a given this value and arguments.

## Examples

Example of **incorrect** code:
```javascript
foo.apply(null, [42]);
```

Example of **correct** code:
```javascript
Reflect.apply(foo, null, [42]);
```