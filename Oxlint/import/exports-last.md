Pattern: Misplaced `export`

Issue: -

## Description

Exports scattered throughout the file can lead to poor code readability
and increase the cost of locating the export quickly

## Examples

Example of **incorrect** code:
```javascript
const bool = true;
export const foo = "bar";
const str = "foo";
```

Example of **correct** code:
```javascript
const arr = ["bar"];
export const bool = true;
export const str = "foo";
export function func() {
  console.log("Hello World");
}
```
