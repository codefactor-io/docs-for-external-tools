Pattern: Error constructor without `new` keyword

Issue: -

## Description

While errors can be created without the `new` keyword, using it makes the constructor call explicit and clearer. Always use `new` when throwing error objects.

## Examples

Example of **incorrect** code:
```javascript
throw Error("🦄");
throw TypeError("unicorn");
throw lib.TypeError("unicorn");
```

Example of **correct** code:
```javascript
throw new Error("🦄");
throw new TypeError("unicorn");
throw new lib.TypeError("unicorn");
```