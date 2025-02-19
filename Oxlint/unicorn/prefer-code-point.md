Pattern: Character code manipulation without Unicode support

Issue: -

## Description

The `String#codePointAt()` and `String.fromCodePoint()` methods provide better Unicode support compared to their older counterparts `charCodeAt()` and `fromCharCode()`, especially for characters outside the BMP (Basic Multilingual Plane).

## Examples

Example of **incorrect** code:
```javascript
"🦄".charCodeAt(0);
String.fromCharCode(0x1f984);
```

Example of **correct** code:
```javascript
"🦄".codePointAt(0);
String.fromCodePoint(0x1f984);
```