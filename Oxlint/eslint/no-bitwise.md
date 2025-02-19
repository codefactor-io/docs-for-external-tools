Pattern: Use of bitwise operator

Issue: -

## Description

Bitwise operators in JavaScript are rarely needed and often indicate a mistake where logical operators (`&&`, `||`) were intended. Their use can lead to unexpected behavior and reduced code clarity.

## Examples

Example of **incorrect** code:
```javascript
var x = y | z;
var m = n & o;
var a = b ^ c;
x |= y;
```

Example of **correct** code:
```javascript
var x = y || z;
var m = n && o;
var a = Math.pow(b, c);
x = y;
```