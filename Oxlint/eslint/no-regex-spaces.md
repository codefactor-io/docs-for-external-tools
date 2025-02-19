Pattern: Multiple spaces in regular expression

Issue: -

## Description

Using multiple consecutive spaces in regular expressions makes it hard to visually count the intended number of spaces to match. Using a quantifier with a single space is clearer and less error-prone.

## Examples

Example of **incorrect** code:
```javascript
var re = /foo   bar/;
var re = new RegExp('foo   bar');
var re = /bar    baz/g;
var re = RegExp('this    spacing');
```

Example of **correct** code:
```javascript
var re = /foo {3}bar/;
var re = new RegExp('foo {3}bar');
var re = /bar\s{4}baz/g;
var re = RegExp('this {4}spacing');

// Single space is fine
var re = /foo bar/;
```