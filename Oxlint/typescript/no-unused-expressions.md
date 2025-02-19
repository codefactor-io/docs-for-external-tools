Pattern: Standalone type or assertion expression

Issue: -

## Description

Unused expressions that don't have any effect on the program are likely mistakes. These include standalone type references and type assertions that aren't assigned or used in any way.

## Examples

Example of **incorrect** code:
```ts
Set<number>;
1 as number;
window!;
obj?.prop;  // result unused
```

Example of **correct** code:
```ts
const set = new Set<number>();
const num = 1 as number;
console.log(window);
const value = obj?.prop;
```