Pattern: Length-based array indexing

Issue: -

## Description

Using negative indices provides a more concise and readable way to access elements from the end of an array, compared to using length-based calculations like `array.length - n`.

## Examples

Example of **incorrect** code:
```js
foo.slice(foo.length - 2, foo.length - 1);
foo.at(foo.length - 1);
```

Example of **correct** code:
```js
foo.slice(-2, -1);
foo.at(-1);
```