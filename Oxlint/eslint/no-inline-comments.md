Pattern: Comment on same line as code

Issue: -

## Description

Comments placed at the end of a line of code can make code harder to read.
They can easily be missed when scanning vertically, and they make lines longer.
Moving comments to their own lines makes them more prominent and reduces line length.

## Examples

Example of **incorrect** code:
```javascript
var a = 1; // inline comment
var b = 2; /* another inline comment */
```

Example of **correct** code:
```javascript
// comment on its own line
var a = 1;

/* block comment on its own line */
var b = 2;
```
