Pattern: Unnecessary assignment of constructor property parameter

Issue: -

## Description

TypeScript's parameter properties allow creating and initializing a member in one place. Therefore, in most cases, it is not necessary to assign parameter properties of the same name to members within a constructor.

## Examples

Example of **incorrect** code:

```javascript
class Foo {
  constructor(public bar: string) {
    this.bar = bar;
  }
}
```

Example of **correct** code:

```javascript
class Foo {
  constructor(public bar: string) {}
}
```