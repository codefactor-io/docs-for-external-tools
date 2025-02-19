Pattern: Use of non-strict equality operator

Issue: -

## Description

Using non-strict equality operators (== and !=) can lead to hard-to-track bugs due to type coercion. Strict equality operators (=== and !==) are safer as they check both value and type.

## Examples

Example of **incorrect** code:
```javascript
let a = [];
let b = false;
a == b;  // evaluates to true due to type coercion

if (x != null) {
  // ...
}
```

Example of **correct** code:
```javascript
let a = [];
let b = false;
a === b;  // evaluates to false as expected

if (x !== null) {
  // ...
}
```