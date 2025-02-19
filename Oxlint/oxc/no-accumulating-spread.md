Pattern: Spread operator in accumulator

Issue: -

## Description

Using spread operators in `reduce()` accumulators or loops creates a new object/array on each iteration, leading to O(n²) complexity. Use direct mutation methods like push or property assignment instead.

## Examples

Example of **incorrect** code:
```javascript
const result = items.reduce((acc, item) => ({
  ...acc,
  [item.id]: item
}), {});

let array = [];
for (const x of items) {
  array = [...array, x];
}
```

Example of **correct** code:
```javascript
const result = items.reduce((acc, item) => {
  acc[item.id] = item;
  return acc;
}, {});

let array = [];
for (const x of items) {
  array.push(x);
}
```