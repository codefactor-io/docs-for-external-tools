Pattern: Use of `parseInt` for numeric literals

Issue: -

## Description

ES6 supports binary, octal, and hexadecimal literals, making `parseInt()` and `Number.parseInt()` unnecessary for converting string representations of these numbers. Using numeric literals directly is more concise and clearer.

## Examples

Example of **incorrect** code:
```javascript
parseInt("111110111", 2);
parseInt("767", 8);
parseInt("1F7", 16);

Number.parseInt("111110111", 2);
Number.parseInt("0767", 8);
Number.parseInt("1F7", 16);

parseInt(`111110111`, 2);
parseInt("0xFF", 16);
```

Example of **correct** code:
```javascript
0b111110111;   // binary
0o767;         // octal
0x1F7;         // hexadecimal

// ParseInt is ok for non-literal strings
parseInt(someVariable, 10);
Number.parseInt(value, 2);

// Parsing strings that aren't literals
parseInt("12.5", 10);
Number.parseInt(getUserInput(), 16);
```