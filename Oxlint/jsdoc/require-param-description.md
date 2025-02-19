Pattern: Missing parameter description

Issue: -

## Description

Each @param tag should include a description explaining the parameter's purpose. Descriptions help other developers understand how to use the function correctly.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @param {string} name
 * @param {number} age
 */
function createUser(name, age) {}
```

Example of **correct** code:
```javascript
/**
 * @param {string} name The user's full name
 * @param {number} age The user's age in years
 */
function createUser(name, age) {}
```