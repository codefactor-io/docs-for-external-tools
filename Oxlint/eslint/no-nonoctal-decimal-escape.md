Pattern: Legacy escape sequence in string

Issue: -

## Description

The escape sequences `\8` and `\9` in string literals are legacy features that produce different results in different JavaScript engines. These sequences should be avoided in favor of literal digits or proper escape sequences.

## Examples

Example of **incorrect** code:
```javascript
const str1 = "Some text \8";
const str2 = "\9 is invalid";
const regex = /\8/;
const str3 = `Template with \8 escape`;
```

Example of **correct** code:
```javascript
const str1 = "Some text 8";
const str2 = "9 is invalid";
const str3 = "Use \\8 for backslash eight";
const regex = /8/;
const str4 = `Template with 8`;
```