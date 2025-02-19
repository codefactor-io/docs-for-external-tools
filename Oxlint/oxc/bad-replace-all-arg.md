Pattern: Non-global regex in `replaceAll`

Issue: -

## Description

When using `replaceAll` with a regular expression, the regex must include the global flag (g). Without it, `replaceAll` will throw a `TypeError` since non-global regexes can only replace the first match.

## Examples

Example of **incorrect** code:
```javascript
text.replaceAll(/\s+/, "-");
text.replaceAll(/[aeiou]/, "*");
```

Example of **correct** code:
```javascript
text.replaceAll(/\s+/g, "-");
text.replaceAll(/[aeiou]/g, "*");
text.replaceAll(" ", "-"); // String literal is ok
```