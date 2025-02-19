Pattern: Use of restricted global variable

Issue: -

## Description

Some global variables should be avoided either because they're deprecated (like the global `event` object), environment-specific, or conflict with better alternatives. Using these globals can lead to maintainability issues or bugs.

## Examples

Example of **incorrect** code:
```javascript
function handleClick() {
  console.log(event);  // Using global event object
}

if (isFinite(value)) {  // Using global isFinite
  process(value);
}

if (isNaN(x)) {  // Using global isNaN
  handleInvalid();
}
```

Example of **correct** code:
```javascript
function handleClick(event) {  // Use event parameter
  console.log(event);
}

if (Number.isFinite(value)) {  // Use Number method
  process(value);
}

if (Number.isNaN(x)) {  // Use Number method
  handleInvalid();
}
```