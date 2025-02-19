Pattern: Nested ternary expression

Issue: -

## Description

Nesting ternary expressions creates code that is hard to read and understand at a glance. Using if statements or splitting into multiple simple ternaries improves readability and maintainability.

## Examples

Example of **incorrect** code:
```javascript
const value = condition1 ? condition2 ? value1 : value2 : value3;

const result = a ? b ? c : d : e ? f : g;

const text = count ? count === 1 ? 'one' : 'many' : 'none';
```

Example of **correct** code:
```javascript
let value;
if (condition1) {
  value = condition2 ? value1 : value2;
} else {
  value = value3;
}

const result = condition 
  ? valueIfTrue 
  : valueIfFalse;

// Split into multiple simple ternaries
const hasCount = count ? 'has' : 'no';
const countText = count === 1 ? 'item' : 'items';
```