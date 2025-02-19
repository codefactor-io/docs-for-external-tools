Pattern: Redundant array length check with `every/some`

Issue: -

## Description

Using array length checks with `array.every()` or `array.some()` is unnecessary since these methods already handle empty arrays appropriately - `every()` returns `true` and `some()` returns `false` for empty arrays.

## Examples

Example of **incorrect** code:
```javascript
if (array.length === 0 || array.every(Boolean)) {
  // do something
}

if (array.length > 0 && array.some(Boolean)) {
  // do something  
}
```

Example of **correct** code:
```javascript
if (array.every(Boolean)) {
  // do something
}

if (array.some(Boolean)) {
  // do something
}
```