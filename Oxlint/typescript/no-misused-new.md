Pattern: Incorrect usage of `new` and `constructor`

Issue: -

## Description

Classes use `constructor` methods for initialization, while interfaces describing static class objects may define a `new()` method. Using these incorrectly can lead to confusing and invalid type definitions.

## Examples

Example of **incorrect** code:
```typescript
declare class C {
  new(): C;
}

interface I {
  new(): I;
  constructor(): void;
}
```

Example of **correct** code:
```typescript
declare class C {
  constructor();
}

interface IStatic {
  new(): IInstance;
}
interface IInstance {
  method(): void;
}
```