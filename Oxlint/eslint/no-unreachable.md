Pattern: Code after flow control statement

Issue: -

## Description

Code that appears after return, throw, break, or continue statements can never be executed and indicates a logic error. Such unreachable code should be removed or the flow control statements should be moved.

## Examples

Example of **incorrect** code:
```javascript
function foo() {
  return true;
  console.log("never executed");
}

function bar() {
  throw new Error("error");
  doSomething();
}

while (true) {
  break;
  console.log("never runs");
}

for (let i = 0; i < 10; i++) {
  continue;
  i++;  // never reached
}
```

Example of **correct** code:
```javascript
function foo() {
  console.log("executed");
  return true;
}

function bar() {
  doSomething();
  throw new Error("error");
}

while (true) {
  if (condition) {
    break;
  }
  console.log("might run");
}

for (let i = 0; i < 10; i++) {
  if (i === 5) continue;
  console.log(i);
}
```