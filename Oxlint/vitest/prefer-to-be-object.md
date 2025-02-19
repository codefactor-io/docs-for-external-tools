Pattern: Indirect `Object` type checking in tests

Issue: -

## Description

Using `toBeInstanceOf(Object)` or `instanceof Object` for type checking is less explicit than the dedicated `toBeObject()` method. Using `toBeObject()` makes the test's intention clearer and improves code readability.

## Examples

Example of **incorrect** code:
```js
expectTypeOf({}).toBeInstanceOf(Object);
expectTypeOf({} instanceof Object).toBeTruthy();
```

Example of **correct** code:
```js
expectTypeOf({}).toBeObject();
expectTypeOf({}).toBeObject();
```