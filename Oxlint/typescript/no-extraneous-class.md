Pattern: Unnecessary class wrapper

Issue: -

## Description

Classes that only contain static members or just a constructor are generally unnecessary in TypeScript/JavaScript. Module-level functions and constants provide better organization without the additional complexity of class syntax.

## Examples

Example of **incorrect** code:
```ts
class StaticConstants {
  static readonly version = 42;
  static isProduction() {
    return process.env.NODE_ENV === "production";
  }
}

class HelloWorldLogger {
  constructor() {
    console.log("Hello, world!");
  }
}
```

Example of **correct** code:
```ts
export const version = 42;
export function isProduction() {
  return process.env.NODE_ENV === "production";
}

export function logHelloWorld() {
  console.log("Hello, world!");
}
```