Pattern: Invalid regular expression in RegExp constructor

Issue: -

## Description

Using an invalid pattern in RegExp constructor causes a runtime SyntaxError when the code is executed, unlike regexp literals which fail at parse time. Invalid patterns include incorrect syntax or invalid flags.

## Examples

Example of **incorrect** code:
```javascript
RegExp('[');
RegExp('.', 'z');
new RegExp('\\');
new RegExp('[a-z', 'g');
RegExp('foo', 'bar');
```

Example of **correct** code:
```javascript
RegExp('.');
new RegExp('[a-z]');
RegExp(pattern, 'g');
new RegExp(/foo/g);
this.RegExp('[');  // Not creating RegExp
```