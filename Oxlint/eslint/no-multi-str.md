Pattern: String with backslash line continuation

Issue: -

## Description

Using backslash line continuation in strings is an undocumented legacy feature that can lead to unexpected whitespace issues. Use template literals or string concatenation instead for multiline strings.

## Examples

Example of **incorrect** code:
```javascript
var str = "Line 1 \
    Line 2";

var message = "Hello \
world";

var x = "Multiple \
        lines \
        here";
```

Example of **correct** code:
```javascript
var str = `Line 1
    Line 2`;

var message = "Hello " +
    "world";

var x = "Multiple " +
    "lines " +
    "here";
```