Pattern: Unnecessary length argument in `slice()`

Issue: -

## Description

Using `length` as the end argument in `slice()` is redundant since `slice()` will automatically go to the end of the array or string when no end index is provided.

## Examples

Example of **incorrect** code:
```javascript
foo.slice(1, foo.length);
```

Example of **correct** code:
```javascript
foo.slice(1);
```