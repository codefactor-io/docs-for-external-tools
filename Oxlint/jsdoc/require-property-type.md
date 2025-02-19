Pattern: Untyped property

Issue: -

## Description

Each @property tag must include a type specification in curly braces. Types provide important information about the expected values for the property.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @typedef {Object} UserConfig
 * @property username
 * @property age
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