Pattern: Missing separator in `Array#join()`

Issue: -

## Description

When using `Array#join()`, explicitly specifying the separator makes the code's intent clearer rather than relying on the default comma separator. This improves code readability and maintainability.

## Examples

Example of **incorrect** code:
```javascript
foo.join();
```

Example of **correct** code:
```javascript
foo.join(",");
```