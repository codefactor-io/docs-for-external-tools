Pattern: Duplicate code in conditional branches

Issue: -

## Description

Duplicate code is less maintainable. Extracting common code from branches makes the code more DRY (Don't Repeat Yourself)
and easier to maintain.

## Examples

Example of **incorrect** code:
```javascript
if (condition) {
  console.log("Hello");
  return 13;
} else {
  console.log("Hello");
  return 42;
}

if (condition) {
  doSomething();
  cleanup();
} else {
  doSomethingElse();
  cleanup();
}
```

Example of **correct** code:
```javascript
console.log("Hello");
if (condition) {
  return 13;
} else {
  return 42;
}

if (condition) {
  doSomething();
} else {
  doSomethingElse();
}
cleanup();
```
