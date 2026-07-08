Pattern: Use of `Array#reverse()`

Issue: -

## Description

`Array#reverse()` modifies the original array in place, which can lead to unintended side effects—especially
when the original array is used elsewhere in the code.

## Examples

Example of **incorrect** code:
```javascript
const reversed = [...array].reverse();
```

Example of **correct** code:
```javascript
const reversed = [...array].toReversed();
```
