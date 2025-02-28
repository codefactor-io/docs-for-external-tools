Pattern: Excessive callback nesting

Issue: -

## Description

Deeply nested callbacks create code that is difficult to read and maintain. This pattern is known as "callback hell" and makes understanding the flow of asynchronous operations challenging. Limiting callback nesting improves code readability.

## Examples

Example of **incorrect** code:
```js
// With { "max": 3 }
foo1(function () {
  foo2(function () {
    foo3(function () {
      foo4(function () {
        // ...
      });
    });
  });
});
```

Example of **correct** code:
```js
// With { "max": 3 }
foo1(handleFoo1);

function handleFoo1() {
  foo2(handleFoo2);
}

function handleFoo2() {
  foo3(handleFoo3);
}

function handleFoo3() {
  foo4(handleFoo4);
}

function handleFoo4() {
  foo5();
}
```