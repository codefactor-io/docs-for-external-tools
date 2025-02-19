Pattern: Explicit use of `any` type

Issue: -

## Description

The `any` type disables TypeScript's type checking, acting as an escape hatch from the type system. While useful for prototyping, explicit `any` types should be avoided in production code as they can hide potential errors.

## Examples

Example of **incorrect** code:
```typescript
const age: any = "seventeen";
const ages: any[] = ["seventeen"];
function greet(): any {}
function greet(param: Array<any>): string {}
```

Example of **correct** code:
```typescript
const age: number = 17;
const ages: string[] = ["seventeen"];
function greet(): string {}
function greet(param: Array<string>): string {}
```