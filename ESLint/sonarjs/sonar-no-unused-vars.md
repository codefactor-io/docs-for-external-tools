Pattern: Unused variable

Issue: -

## Description

Unused variables are a common source of bugs and confusion. Removing them can make your code cleaner and easier to understand.


Example of **incorrect** code:

```js
function numberOfMinutes(hours) {
  var seconds = 0;   // seconds is never used
  return hours * 60;
}
```

Example of **correct** code:

```js
function numberOfMinutes(hours) {
  return hours * 60;
}
```

## Further Reading

* [no-unused-vars](https://sonarsource.github.io/rspec/#/rspec/S1481/javascript)