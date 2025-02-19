Pattern: Interface with single call signature

Issue: -

## Description

Using an interface or object type with a single call signature is more verbose than using an equivalent function type. Function types are more concise and easier to read for simple function definitions.

## Examples

Example of **incorrect** code:
```ts
interface Processor {
  (): string;
}

type Handler = {
  (): number;
};
```

Example of **correct** code:
```ts
type Processor = () => string;

type Handler = () => number;

// OK: Multiple call signatures or additional properties
interface Overloaded {
  (data: string): number;
  (id: number): string;
}

interface WithProperties {
  (): void;
  prop: string;
}
```