Pattern: Use of named export

Issue: -

## Description

Named exports require strict identifier matching and can lead to fragile imports,
while default exports enforce a single, consistent module entry point.

## Examples

Example of **incorrect** code:
```javascript
export const foo = "foo";

const bar = "bar";
export { bar };
```

Example of **correct** code:
```javascript
export default 'bar';

const foo = 'foo';
export { foo as default }
```
