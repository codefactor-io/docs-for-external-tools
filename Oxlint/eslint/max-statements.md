Pattern: Too many statements

Issue: -

## Description

Some people consider large functions a code smell. Large functions tend to do a lot of things and can make it hard to follow what's going on. This rule can help avoid large functions.

## Examples

Example of **incorrect** code for `{ "max": 10 }`:

```js
function foo() {
  const foo1 = 1;
  const foo2 = 2;
  const foo3 = 3;
  const foo4 = 4;
  const foo5 = 5;
  const foo6 = 6;
  const foo7 = 7;
  const foo8 = 8;
  const foo9 = 9;
  const foo10 = 10;

  const foo11 = 11; // Too many.
}

const bar = () => {
  const foo1 = 1;
  const foo2 = 2;
  const foo3 = 3;
  const foo4 = 4;
  const foo5 = 5;
  const foo6 = 6;
  const foo7 = 7;
  const foo8 = 8;
  const foo9 = 9;
  const foo10 = 10;

  const foo11 = 11; // Too many.
};
```

Example of **correct** code:

```js
function foo() {
  const foo1 = 1;
  const foo2 = 2;
  const foo3 = 3;
  const foo4 = 4;
  const foo5 = 5;
  const foo6 = 6;
  const foo7 = 7;
  const foo8 = 8;
  const foo9 = 9;
  return function () {
    // 10

    // The number of statements in the inner function does not count toward the
    // statement maximum.

    let bar;
    let baz;
    return 42;
  };
}

const bar = () => {
  const foo1 = 1;
  const foo2 = 2;
  const foo3 = 3;
  const foo4 = 4;
  const foo5 = 5;
  const foo6 = 6;
  const foo7 = 7;
  const foo8 = 8;
  const foo9 = 9;
  return function () {
    // 10

    // The number of statements in the inner function does not count toward the
    // statement maximum.

    let bar;
    let baz;
    return 42;
  };
};
```