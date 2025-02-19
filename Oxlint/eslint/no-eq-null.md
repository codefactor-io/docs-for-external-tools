Pattern: Loose equality comparison with `null`

Issue: -

## Description

Using loose equality operators (`==`, `!=`) when comparing with `null` can produce unexpected results because the comparison will match both `null` and `undefined`. Use strict equality operators (`===`, `!==`) for explicit null checks.

## Examples

Example of **incorrect** code:
```javascript
if (foo == null) {
  handleNull();
}

if (foo != null) {
  handleNotNull();
}

while (value == null) {
  waitForValue();
}
```

Example of **correct** code:
```javascript
if (foo === null) {
  handleNull();
}

if (foo !== null) {
  handleNotNull();
}

// Check for both null and undefined explicitly
if (foo == null && foo === undefined) {
  handleNullOrUndefined();
}
```