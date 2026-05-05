Pattern: Unnecessary assignment

Issue: -

## Description

Dead stores add noise and can hide real bugs (e.g., you meant to use that value or wrote to the wrong variable). Removing them improves clarity and performance.

## Examples

Example of **incorrect** code:

```ts
/* eslint no-useless-assignment: "error" */

function fn1() {
  let v = "used";
  doSomething(v);
  v = "unused"; // assigned but never read
}

function fn2() {
  let v = "used";
  if (condition) {
    v = "unused"; // early return; this write is never observed
    return;
  }
  doSomething(v);
}

function fn3() {
  let v = "used";
  if (condition) {
    doSomething(v);
  } else {
    v = "unused"; // value not used later in this branch
  }
}
```

Example of **correct** code:

```ts
function fn1() {
  let v = "used";
  doSomething(v);
  v = "used-2";
  doSomething(v); // the reassigned value is read
}

function fn2() {
  let v = "used";
  if (condition) {
    v = "used-2";
    doSomething(v); // reassignment is observed before returning
    return;
  }
  doSomething(v);
}

function fn3() {
  let v = "used";
  for (let i = 0; i < 10; i++) {
    doSomething(v);
    v = "used in next iteration"; // used on the next loop pass
  }
}
```