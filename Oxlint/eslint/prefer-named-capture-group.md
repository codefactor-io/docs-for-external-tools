Pattern: Unnamed regular expression capture group

Issue: -

## Description

Unnamed capturing groups (`(...)`) are referenced only by position, which
makes the regex harder to read and maintain. When the pattern changes, index-based
references silently break. Named groups (`(?<name>...)`) make the intent explicit
and allow references by name (e.g. `match.groups.year`), which is more robust.

## Examples

Example of **incorrect** code:
```javascript
const re = /([0-9]{4})-([0-9]{2})/;
const match = re.exec(str);
const year = match[1]; // fragile index
```

Example of **correct** code:
```javascript
const re = /(?<year>[0-9]{4})-(?<month>[0-9]{2})/;
const match = re.exec(str);
const year = match.groups.year; // explicit name

// Non-capturing groups are always fine
const parts = /(?:[0-9]{4})/;
```
