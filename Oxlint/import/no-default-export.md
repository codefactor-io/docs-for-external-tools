Pattern: Use of default export

Issue: -

## Description

Default exports can make refactoring and auto-imports less reliable since the name of the imported value can vary based on how it's imported. Named exports provide more explicit and predictable imports.

## Examples

Example of **incorrect** code:
```javascript
export default 'bar';

const foo = 'foo';
export { foo as default };
```

Example of **correct** code:
```javascript
export const foo = "foo";
export const bar = "bar";
```