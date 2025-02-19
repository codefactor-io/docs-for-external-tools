Pattern: Invalid access declaration

Issue: -

## Description

Access levels in JSDoc must use valid values (private, protected, public, package) and should not mix @access tag with direct access tags (@private, etc.) in the same block.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @access private
 * @public
 */
function example() {}

/**
 * @access invalid
 */
function another() {}
```

Example of **correct** code:
```javascript
/**
 * @access private
 */
function example() {}

/**
 * @protected
 */
function another() {}
```