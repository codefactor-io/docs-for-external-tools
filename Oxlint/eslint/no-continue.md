Pattern: Use of `continue` statement

Issue: -

## Description

The `continue` statement skips the rest of the current loop iteration and can make code harder to understand and maintain. Using structured control flow with if statements leads to clearer and more testable code.

## Examples

Example of **incorrect** code:
```javascript
let sum = 0;
for (let i = 0; i < 10; i++) {
  if (i >= 5) {
    continue;
  }
  sum += i;
}

for (const user of users) {
  if (!user.active) {
    continue;
  }
  processUser(user);
}
```

Example of **correct** code:
```javascript
let sum = 0;
for (let i = 0; i < 10; i++) {
  if (i < 5) {
    sum += i;
  }
}

for (const user of users) {
  if (user.active) {
    processUser(user);
  }
}
```