Pattern: Use of TypeScript directive comments

Issue: -

## Description

TypeScript directive comments like `@ts-ignore` suppress compiler errors, which reduces the effectiveness of TypeScript's type checking. Instead of suppressing errors, it's better to fix the underlying type issues.

## Examples

Example of **incorrect** code:
```ts
if (false) {
  // @ts-ignore: Unreachable code error
  console.log("hello");
}
```

Example of **correct** code:
```ts
if (true) {
  console.log("hello");
}
```