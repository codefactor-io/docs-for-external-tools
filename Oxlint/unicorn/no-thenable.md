Pattern: Object with `then` method creating thenable

Issue: -

## Description

Objects with a `then` method can be mistakenly treated as promises when used with `await`, causing unexpected behavior like code after the `await` never executing.

## Examples

Example of **incorrect** code:
```javascript
async function example() {
  const foo = {
    unicorn: 1,
    then() {},
  };

  const { unicorn } = await foo;

  console.log("after"); // Never executes
}
```

Example of **correct** code:
```javascript
async function example() {
  const foo = {
    unicorn: 1
  };

  const { unicorn } = foo;
  console.log("after");
}
```