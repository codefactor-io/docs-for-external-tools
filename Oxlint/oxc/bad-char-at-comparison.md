Pattern: Invalid charAt comparison

Issue: -

## Description

The charAt method always returns a single character string. Comparing its result with a string longer than one character will always evaluate to false and indicates a logic error.

## Examples

Example of **incorrect** code:
```javascript
if (str.charAt(0) === "ab") {
  // Will never be true
}
str.charAt(5) === "\r\n";
```

Example of **correct** code:
```javascript
if (str.charAt(0) === "a") {
  // Can be true
}
str.charAt(5) === "\n";
```