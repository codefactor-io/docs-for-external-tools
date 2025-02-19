Pattern: Use of `@ts-ignore` comment

Issue: -

## Description

Using `@ts-ignore` can lead to missed errors as it continues to suppress errors even after the original issue is fixed. `@ts-expect-error` is safer because it causes an error if used on a line that no longer has type errors.

## Examples

Example of **incorrect** code:
```ts
// @ts-ignore
const str: string = 1;

/**
 * Some explanation
 * @ts-ignore
 */
const num: number = "value";
```

Example of **correct** code:
```ts
// @ts-expect-error
const str: string = 1;

/**
 * Some explanation
 * @ts-expect-error
 */
const num: number = "value";
```