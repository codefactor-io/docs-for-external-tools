Pattern: Lowercase character in escape sequence

Issue: -

## Description

Using uppercase characters in escape sequences makes them more distinguishable from regular identifiers, improving code readability.

## Examples

Example of **incorrect** code:
```javascript
const foo = "\xa9";
const foo = "\ud834";
const foo = "\u{1d306}";
const foo = "\ca";
```

Example of **correct** code:
```javascript
const foo = "\xA9";
const foo = "\uD834";
const foo = "\u{1D306}";
const foo = "\cA";
```