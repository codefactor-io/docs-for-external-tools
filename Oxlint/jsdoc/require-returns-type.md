Pattern: Untyped return tag

Issue: -

## Description

The @returns tag must include a type specification in curly braces. Without a type, other developers won't know what kind of value to expect from the function.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @returns The processed data
 */
function processData(input) {
  return input.trim();
}
```

Example of **correct** code:
```javascript
/**
 * @returns {string} The processed data
 */
function processData(input) {
  return input.trim();
}
```