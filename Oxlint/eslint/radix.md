Pattern: Missing radix in `parseInt`

Issue: -

## Description

Using `parseInt()` without specifying the radix can lead to unexpected results, especially when parsing strings with leading zeros. Always specify base 10 or the intended base to ensure consistent number parsing.

## Examples

Example of **incorrect** code:
```javascript
parseInt("071");      // 57 (interpreted as octal in some browsers)
parseInt("08");       // 0 (invalid in octal)
parseInt("0x16");     // 22 (interpreted as hex)
parseInt("15.5");     // 15

const str = userInput();
parseInt(str);
```

Example of **correct** code:
```javascript
parseInt("071", 10);  // 71
parseInt("08", 10);   // 8
parseInt("0x16", 16); // 22 (explicitly hex)
parseInt("15.5", 10); // 15

const str = userInput();
parseInt(str, 10);
```