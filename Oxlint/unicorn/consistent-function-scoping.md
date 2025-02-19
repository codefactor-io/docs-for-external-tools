Pattern: Unnecessary nested function scope

Issue: -

## Description

Functions that don't capture any variables from their outer scope should be moved to the highest possible scope. This improves readability and allows JavaScript engines to better optimize performance.

## Examples

Example of **incorrect** code:
```js
export function doFoo(foo) {
  // Does not capture anything from the scope, can be moved to the outer scope
  function doBar(bar) {
    return bar === "bar";
  }
  return doBar;
}

function doFoo(foo) {
  const doBar = (bar) => {
    return bar === "bar";
  };
}
```

Example of **correct** code:
```js
function doBar(bar) {
  return bar === "bar";
}

export function doFoo(foo) {
  return doBar;
}

export function doFoo(foo) {
  function doBar(bar) {
    return bar === "bar" && foo.doBar(bar);
  }
  return doBar;
}
```