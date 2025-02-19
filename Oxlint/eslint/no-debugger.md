Pattern: Use of `debugger` statement

Issue: -

## Description

The `debugger` statement is typically used during development to trigger debugging functionality. When left in production code, it has no effect unless a debugger is attached and can indicate forgotten debugging code.

## Examples

Example of **incorrect** code:
```javascript
function calc(data) {
  debugger;
  return data.reduce((sum, val) => sum + val, 0);
}

async function main() {
  const data = await getData();
  debugger;  // Forgotten debugging statement
  process(data);
}
```

Example of **correct** code:
```javascript
function calc(data) {
  return data.reduce((sum, val) => sum + val, 0);
}

async function main() {
  const data = await getData();
  process(data);
}
```