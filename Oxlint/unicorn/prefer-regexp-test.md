Pattern: `String#match()` or `RegExp#exec()` for boolean check

Issue: -

## Description

When checking if a pattern exists in a string, `RegExp#test()` is more efficient than `String#match()` or `RegExp#exec()` as it only returns a boolean instead of creating a new array of matches.

## Examples

Example of **incorrect** code:
```javascript
if (string.match(/unicorn/)) {
}
if (/unicorn/.exec(string)) {
}
```

Example of **correct** code:
```javascript
if (/unicorn/.test(string)) {
}
Boolean(string.match(/unicorn/));
```