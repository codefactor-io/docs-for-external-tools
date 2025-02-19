Pattern: Irregular numeric separator grouping

Issue: -

## Description

Long numbers should use numeric separators (`_`) in consistent group sizes to improve readability. Different number types have different preferred grouping sizes: decimal numbers use groups of three, hexadecimal use groups of two, and binary numbers use groups of four.

## Examples

Example of **incorrect** code:
```javascript
const invalid = [
  1_23_4444,
  1_234.56789,
  0xab_c_d_ef,
  0b10_00_1111,
  0o1_0_44_21,
  1_294_28771_2n
];
```

Example of **correct** code:
```javascript
const valid = [
  1_234_567,
  1_234.567_89,
  0xab_cd_ef,
  0b1000_1111,
  0o10_4421,
  1_294_287_712n
];
```