Pattern: Redundant assignment of parameter property

Issue: -

## Description

Constructor parameters with visibility modifiers (`public`, `private`, `protected`, or `readonly`) are automatically initialized as class properties. Explicitly assigning these parameters to their corresponding properties is redundant and unnecessary.

## Examples

Example of **incorrect** code:
```typescript
class Foo {
  constructor(public name: unknown) {
    this.name = name; // Unnecessary assignment
  }
}
```

Example of **correct** code:
```typescript
class Foo {
  constructor(public name: unknown) {
    // No assignment needed
  }
}
```