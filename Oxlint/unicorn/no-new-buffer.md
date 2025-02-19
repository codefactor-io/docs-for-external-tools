Pattern: Use of deprecated `new Buffer()` constructor

Issue: -

## Description

The `new Buffer()` constructor has been deprecated since Node.js 4. Use `Buffer.from()` for creating a buffer from existing data or `Buffer.alloc()` for creating a new buffer with allocated memory.

## Examples

Example of **incorrect** code:
```javascript
const buffer = new Buffer(10);
```

Example of **correct** code:
```javascript
const buffer = Buffer.alloc(10);
```