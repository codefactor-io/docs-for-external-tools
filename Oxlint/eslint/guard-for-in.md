Pattern: Unguarded for-in loop

Issue: -

## Description

A for-in loop iterates over all enumerable properties of an object, including those inherited through the prototype chain. Without filtering the results with an if statement, unexpected behavior can arise from inherited properties.

## Examples

Example of **incorrect** code:
```javascript
for (key in foo) {
  doSomething(key);
}
```

Example of **correct** code:
```javascript
for (key in foo) {
  if (Object.hasOwn(foo, key)) {
    doSomething(key);
  }
}
```