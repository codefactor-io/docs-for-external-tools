Pattern: Bitwise operator misuse

Issue: -

## Description

Using bitwise operators (& |) where logical operators (&& ||) are expected can cause bugs. Bitwise operators don't short-circuit and operate on individual bits rather than boolean values.

## Examples

Example of **incorrect** code:
```javascript
if (obj & obj.property) {
  console.log(obj.property);
}

const value = input | defaultValue;
```

Example of **correct** code:
```javascript
if (obj && obj.property) {
  console.log(obj.property);
}

const value = input || defaultValue;
```