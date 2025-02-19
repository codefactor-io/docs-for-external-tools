Pattern: Number literal exceeding precision

Issue: -

## Description

JavaScript numbers are stored as 64-bit floating-point values, which cannot accurately represent all numbers. Using literals that exceed this precision leads to unexpected results in calculations and comparisons.

## Examples

Example of **incorrect** code:
```javascript
const x = 9007199254740993;  // Exceeds Number.MAX_SAFE_INTEGER
const binary = 0b100000000000000000000000000000000000000000000000000001;
const octal = 0o400000000000000000001;
const hex = 0x20000000000001;
const scientific = 2e999;
```

Example of **correct** code:
```javascript
const x = 9007199254740991;  // Number.MAX_SAFE_INTEGER
const binary = 0b1111111111111111111111111111111111111111111111111111111;
const scientific = 2e308;
const precise = BigInt("9007199254740993");
```