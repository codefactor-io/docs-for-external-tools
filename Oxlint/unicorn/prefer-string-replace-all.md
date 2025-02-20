Pattern: Global string replacement with `replace()`

Issue: -

## Description

The `replaceAll()` method provides a safer and more efficient way to replace all occurrences of a pattern compared to using `replace()` with a global regex. It's clearer in intent and doesn't require regex escape handling for string patterns.

## Examples

Example of **incorrect** code:
```javascript
string.replace(/foo/g, 'bar');
string.replace(new RegExp(pattern, 'g'), 'bar');
```

Example of **correct** code:
```javascript
string.replaceAll('foo', 'bar');
string.replaceAll(/foo/, 'bar');
```