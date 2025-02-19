Pattern: Content in void tag

Issue: -

## Description

Certain JSDoc tags like @async, @private, @readonly should not contain any content. These tags are meant to be used as markers or flags without additional description.

## Examples

Example of **incorrect** code:
```javascript
/**
 * @async with some content
 * @private this is private
 * @readonly add description
 */
function getData() {}
```

Example of **correct** code:
```javascript
/**
 * @async
 * @private
 * @readonly
 */
function getData() {}
```