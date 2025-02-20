Pattern: Use of `substr()` or `substring()`

Issue: -

## Description

The `slice()` method provides a more consistent way to extract a portion of a string compared to legacy methods like `substr()` and `substring()`. It has clearer behavior and matches the behavior of `Array.prototype.slice()`.

## Examples

Example of **incorrect** code:
```javascript
"foo".substr(1, 2);
"foo".substring(1, 2);
```

Example of **correct** code:
```javascript
"foo".slice(1, 2);
```