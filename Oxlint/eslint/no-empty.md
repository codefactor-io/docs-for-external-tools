Pattern: Empty block statement

Issue: -

## Description

Empty block statements usually indicate incomplete refactoring or code that was removed without cleaning up the containing block. While not technically errors, they can cause confusion and should either be removed or documented with a comment explaining their purpose.

## Examples

Example of **incorrect** code:
```javascript
if (condition) {
}

while (condition) {
}

try {
  doSomething();
} catch(e) {
}

function foo() {
}
```

Example of **correct** code:
```javascript
if (condition) {
  // Handle special case later
}

while (condition) {
  break;
}

try {
  doSomething();
} catch(e) {
  // Errors can be safely ignored
}

function foo() {
  return;
}
```