Pattern: Parameter only used in recursive call

Issue: -

## Description

Function parameters that are only used in recursive calls without any other purpose likely indicate a mistake. These parameters increase complexity without adding value since they're just passed through unchanged.

## Examples

Example of **incorrect** code:
```javascript
function process(data, unused) {
  if (data.length === 0) return;
  return process(data.slice(1), unused);
}

const calc = (x, extra) => {
  return x > 0 ? calc(x - 1, extra) : 0;
};
```

Example of **correct** code:
```javascript
function process(data) {
  if (data.length === 0) return;
  return process(data.slice(1));
}

const calc = (x) => {
  return x > 0 ? calc(x - 1) : 0;
};
```