Pattern: Multiple escape characters in string

Issue: -

## Description

Using `String.raw` allows you to write paths and regular expressions without escaping backslashes, making the code more readable. This is particularly useful for Windows paths and regular expressions that contain many backslashes.

## Examples

Example of **incorrect** code:
```javascript
const file = "C:\\windows\\style\\path\\to\\file.js";
const regexp = new RegExp("foo\\.bar");
```

Example of **correct** code:
```javascript
const file = String.raw`C:\windows\style\path\to\file.js`;
const regexp = new RegExp(String.raw`foo\.bar`);
```