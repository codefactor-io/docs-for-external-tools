Pattern: Use of `Array#sort()`

Issue: -

## Description

`Array#sort()` modifies the original array in place, which can lead to unintended side effects—especially when the original array is used elsewhere in the code.

## Examples

Example of **incorrect** code:

```javascript
const sorted = [...array].sort();
```

Example of **correct** code:

```javascript
const sorted = [...array].toSorted();
```