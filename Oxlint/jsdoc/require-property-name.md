Pattern: Unnamed property

Issue: -

## Description

Each @property tag must include the name of the property being documented. A type alone is not sufficient for proper documentation.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @typedef {Object} UserConfig
 * @property {string}
 * @property {number}
 */
```

Example of **correct** code:
```javascript
/**
 * @typedef {Object} UserConfig
 * @property {string} username
 * @property {number} age
 */
```