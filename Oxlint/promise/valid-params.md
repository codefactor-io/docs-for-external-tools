Pattern: Invalid number of arguments in `Promise` methods

Issue: -

## Description

Calling `Promise` methods with an incorrect number of arguments can lead to unexpected behavior or bugs that are difficult to detect. Each `Promise` method has a specific number of expected parameters that should be followed.

## Examples

Example of **incorrect** code:
```javascript
Promise.resolve(1, 2);
```

Example of **correct** code:
```javascript
Promise.resolve(1);
```