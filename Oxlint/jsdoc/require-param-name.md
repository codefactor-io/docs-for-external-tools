Pattern: Missing parameter name

Issue: -

## Description

Each @param tag must include the parameter name that it documents. A type alone is not sufficient for proper documentation.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @param {string}
 * @param {number}
 */
function updateUser(name, age) {}
```

Example of **correct** code:
```javascript
/**
 * @param {string} name
 * @param {number} age
 */
function updateUser(name, age) {}
```