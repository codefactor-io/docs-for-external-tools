Pattern: Dynamic property deletion

Issue: -

## Description

Using the `delete` operator with computed key expressions can be dangerous and poorly optimized. If you need a key-value collection with frequent deletions, consider using `Map` or `Set` instead of an object.

## Examples

Example of **incorrect** code:
```ts
const container: { [i: string]: number } = {};
delete container["key" + index];
delete container[`prefix_${id}`];
```

Example of **correct** code:
```ts
const container: { [i: string]: number } = {};
delete container.staticKey;
delete container["literal-key"];

// Better approach
const map = new Map<string, number>();
map.delete(`prefix_${id}`);
```