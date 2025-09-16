Pattern: Unused assignment

Issue: -

## Description

Dead stores refer to assignments made to local variables that are subsequently never used or immediately overwritten. Such assignments are unnecessary and don’t contribute to the functionality or clarity of the code. They may even negatively impact performance. Removing them enhances code cleanliness and readability. Even if the unnecessary operations do not do any harm in terms of the program’s correctness, they are - at best - a waste of computing resources.


Example of **incorrect** code:

```ts
function foo(y) {
  let x = 100; // Noncompliant: dead store
  x = 150;     // Noncompliant: dead store
  x = 200;
  return x + y;
}
```

Example of **correct** code:

```ts
function foo(y) {
  let x = 200; // Compliant: no unnecessary assignment
  return x + y;
}
```

## Further Reading

* [S1854](https://sonarsource.github.io/rspec/#/rspec/S1854/javascript)