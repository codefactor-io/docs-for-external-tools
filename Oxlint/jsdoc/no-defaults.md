Pattern: Default value in JSDoc

Issue: -

## Description

Specifying default values in JSDoc is redundant when using ES6 default parameters. Default values should be specified in the function parameters rather than in the documentation.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @param {number} [count=10] Number of items
 */
function getItems(count) {}
```

Example of **correct** code:
```javascript
/**
 * @param {number} count Number of items
 */
function getItems(count = 10) {}
```