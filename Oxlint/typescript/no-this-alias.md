Pattern: Creating alias for `this`

Issue: -

## Description

Creating variables that alias `this` can lead to unexpected behavior and make code harder to maintain. Instead, use arrow functions to preserve the correct `this` context, or destructure specific properties needed from `this`.

## Examples

Example of **incorrect** code:
```ts
function example() {
  const self = this;
  const that = this;
  const _this = this;
}
```

Example of **correct** code:
```ts
function example() {
  doSomething(() => {
    this.value = 42;
  });
  
  const { value } = this;
}
```