Pattern: Date clone through timestamp conversion

Issue: -

## Description

Using `.getTime()` to convert a `Date` object to a timestamp and then back to a
`Date` is redundant and unnecessary. Simply passing the `Date` object to the
`Date` constructor is cleaner and more efficient.

## Examples

Example of **incorrect** code:
```javascript
new Date(date.getTime());
```

Example of **correct** code:
```javascript
new Date(date);
```
