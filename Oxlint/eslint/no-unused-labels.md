Pattern: Label declaration without usage

Issue: -

## Description

Labels that are declared but never referenced in a break or continue statement are likely leftover from refactoring. They add visual noise and can be safely removed to improve code clarity.

## Examples

Example of **incorrect** code:
```javascript
outer: for (let i = 0; i < 10; i++) {
  inner: for (let j = 0; j < 10; j++) {
    break;  // breaks inner loop without using label
  }
}

unused: {
  doSomething();
  break;  // unlabeled break
}

loop: while (condition) {
  if (x) return;  // no labeled break/continue
}
```

Example of **correct** code:
```javascript
outer: for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    if (condition) break outer;  // label is used
  }
}

block: {
  doSomething();
  break block;  // label is used
}

// No label when unnecessary
while (condition) {
  if (x) break;
}
```