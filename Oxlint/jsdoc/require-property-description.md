Pattern: Missing property description

Issue: -

## Description

Each @property tag should include a description explaining the property's purpose. Descriptions help other developers understand how to use the property correctly.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @typedef {Object} UserConfig
 * @property {string} username
 * @property {number} age
 */
```

Example of **correct** code:
```javascript
/**
 * @typedef {Object} UserConfig
 * @property {string} username The user's login name
 * @property {number} age The user's age in years
 */
```