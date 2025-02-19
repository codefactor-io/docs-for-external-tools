Pattern: Use of `tslint` directive comments

Issue: -

## Description

TSLint directive comments are obsolete when migrating to ESLint. These comments should be removed after the migration is complete to maintain clean code and prevent confusion.

## Examples

Example of **incorrect** code:
```ts
// tslint:disable-next-line
someCode();
```

Example of **correct** code:
```ts
someCode();
```